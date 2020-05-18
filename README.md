# oci-java-sdk-demo

Make sure you have an OCI config located at `~/.oci/config` and a `DEFAULT` profile configured.

!!! note
Run the following code under an Oracle Java JDK (11+)

Run:

```bash
$ ./gradlew assemble && java -jar build/libs/oci-java-sdk-demo-1.0-SNAPSHOT-all.jar  
```

Observe the stack trace:

```bash
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
Exception in thread "main" com.oracle.bmc.http.signing.internal.PEMFileRSAPrivateKeySupplier$PEMFileRSAPrivateKeySupplierException: org.bouncycastle.openssl.PEMException: exception processing key pair: JCE cannot authenticate the provider BC
        at com.oracle.bmc.http.signing.internal.PEMFileRSAPrivateKeySupplier.<init>(PEMFileRSAPrivateKeySupplier.java:120)
        at com.oracle.bmc.http.signing.internal.DefaultRequestSignerFactory.createKeySupplier(DefaultRequestSignerFactory.java:111)
        at com.oracle.bmc.http.signing.internal.DefaultRequestSignerFactory.createRequestSigner(DefaultRequestSignerFactory.java:54)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:268)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:217)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:180)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:145)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:117)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:92)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:69)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:55)
        at com.oracle.bmc.objectstorage.ObjectStorageClient.<init>(ObjectStorageClient.java:44)
        at codes.recursive.Test.main(Test.java:22)
Caused by: org.bouncycastle.openssl.PEMException: exception processing key pair: JCE cannot authenticate the provider BC
        at org.bouncycastle.openssl.PEMEncryptedKeyPair.decryptKeyPair(Unknown Source)
        at com.oracle.bmc.http.signing.internal.PEMFileRSAPrivateKeySupplier.<init>(PEMFileRSAPrivateKeySupplier.java:94)
        ... 12 more
Caused by: java.lang.SecurityException: JCE cannot authenticate the provider BC
        at java.base/javax.crypto.JceSecurity.getInstance(JceSecurity.java:145)
        at java.base/javax.crypto.SecretKeyFactory.getInstance(SecretKeyFactory.java:252)
        at org.bouncycastle.jcajce.util.ProviderJcaJceHelper.createSecretKeyFactory(Unknown Source)
        at org.bouncycastle.openssl.jcajce.PEMUtilities.getKey(Unknown Source)
        at org.bouncycastle.openssl.jcajce.PEMUtilities.getKey(Unknown Source)
        at org.bouncycastle.openssl.jcajce.PEMUtilities.crypt(Unknown Source)
        at org.bouncycastle.openssl.jcajce.JcePEMDecryptorProviderBuilder$1$1.decrypt(Unknown Source)
        ... 14 more
Caused by: java.util.jar.JarException: file:/Users/trsharp/Projects/sdk/oci-java-sdk-demo/build/libs/oci-java-sdk-demo-1.0-SNAPSHOT-all.jar has unsigned entries - codes/recursive/Test.class
        at java.base/javax.crypto.JarVerifier.verifySingleJar(JarVerifier.java:459)
        at java.base/javax.crypto.JarVerifier.verifyJars(JarVerifier.java:314)
        at java.base/javax.crypto.JarVerifier.verify(JarVerifier.java:257)
        at java.base/javax.crypto.ProviderVerifier.verify(ProviderVerifier.java:129)
        at java.base/javax.crypto.JceSecurity.verifyProvider(JceSecurity.java:191)
        at java.base/javax.crypto.JceSecurity.getVerificationResult(JceSecurity.java:217)
        at java.base/javax.crypto.JceSecurity.getInstance(JceSecurity.java:141)
        ... 20 more
```