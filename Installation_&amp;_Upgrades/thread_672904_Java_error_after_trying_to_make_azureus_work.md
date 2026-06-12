---
title: "Java error after trying to make azureus work"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Harish TM on 2008-01-20
I recently had a problem with Azureus after an update. 

This seems to have been a problem with a recent update of  xserver-xorg-core which broke Java aps. 

Unfortunately I tried to fix this myselfbefore finding: [This]("http://ubuntuforums.org/showthread.php?p=4158788")  

The error I get:
> 

~$ azureus 
WARNING: Error loading security provider gnu.javax.crypto.jce.GnuCrypto: java.lang.ClassNotFoundException: gnu.javax.crypto.jce.GnuCrypto
WARNING: Error loading security provider gnu.javax.crypto.jce.GnuSasl: java.lang.ClassNotFoundException: gnu.javax.crypto.jce.GnuSasl
WARNING: Error loading security provider gnu.javax.net.ssl.provider.Jessie: java.lang.ClassNotFoundException: gnu.javax.net.ssl.provider.Jessie
WARNING: Error loading security provider gnu.javax.security.auth.callback.GnuCallbacks: java.lang.ClassNotFoundException: gnu.javax.security.auth.callback.GnuCallbacks
WARNING: Error loading security provider org.bouncycastle.jce.provider.BouncyCastleProvider: java.lang.ClassNotFoundException: org.bouncycastle.jce.provider.BouncyCastleProvider
WARNING: Error loading security provider gnu.crypto.jce.GnuCrypto: java.lang.ClassNotFoundException: gnu.crypto.jce.GnuCrypto
DEBUG::Sun Jan 20 15:36:07 GMT+05:30 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
  -- and so on

<Hangs Here>



Here are a list of things I tried (from my .bash_history)

> sudo apt-get install sun-java-sdk
sudo apt-get install free-java-sdk
sudo aptitude install xserver-xorg-core=2:1.2.0-3ubuntu8
azureus
sudo apt-get remove free-java-sdk
sudo apt-get -f install
azureus
sudo aptitude install xserver-xorg-core=2:1.2.
sudo apt-get remove free-java-sdk
sudo apt-get remove  classpath-tools fastjar
azureus
sudo apt-get -f install
azureus
sudo apt-get remove sun-java-sdk
sudo apt-get -f install
azureus
sudo apt-get remove azureus
sudo apt-get -f install
sudo apt-get remove libgnucrypto-java liblog4j1.2-java libswt3.2-gtk-java libseda-java libcommons-cli-java libgtk-jni libcairo-java libbcprov-java libglib-j\
ava libgtk-java
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get --foce install
sudo apt-get --f install
sudo apt-get -f install
sudo apt-get install azureus

Now I am unable to run any Java applications. 

Could someone please help?

My system details:

ubuntu feisty

> 

$uname -a
Linux <computer-Name> 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686 GNU/Linux



> 
$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu     : yes
fpu_exception   : yes
cpuid level     : 1
wp      : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 1611.14
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu     : yes
fpu_exception   : yes
cpuid level     : 1
wp      : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 1611.14
clflush size    : 64



---

### Post by ajgreeny on 2008-01-20
```
sudo apt-get update && sudo apt-get install xserver-xorg-core
```The package was broken and is now fixed.  Make sure it is the version 2:1.3.0.0.dfsg-12ubuntu8.3 and you should be OK.

---

### Post by Harish TM on 2008-01-20
ajgreeny, 

        Thanks for the reply. However I have already updated xserver-xorg-core ( ran your command again just to make sure) 

Here is what I get:

> 

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.




I have tried everything at:  [http://ubuntuforums.org/showthread.php?p=4158788](http://ubuntuforums.org/showthread.php?p=4158788)

I maybe wrong but I think its the other stuff I did that broke Java somehow.

Anything else I can try?

---

