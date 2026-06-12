---
title: "Failed Dependencies when installing Java"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by hclaire on 2008-11-06
Hi,

I'm trying to install JRE or JDK any version of java from SUN using terminal. Because I wanna run a program on my machine that requires Java.

So I downloaded the jre-6u10-linux-i586-rpm.bin and tried to install the rpm file. But it says

Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u10-linux-i586.rpm  
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_10-fcs.i586
	/bin/cat is needed by jre-1.6.0_10-fcs.i586
	/bin/cp is needed by jre-1.6.0_10-fcs.i586
	/bin/gawk is needed by jre-1.6.0_10-fcs.i586
	/bin/grep is needed by jre-1.6.0_10-fcs.i586
	/bin/ln is needed by jre-1.6.0_10-fcs.i586
	/bin/ls is needed by jre-1.6.0_10-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_10-fcs.i586
	/bin/mv is needed by jre-1.6.0_10-fcs.i586
	/bin/pwd is needed by jre-1.6.0_10-fcs.i586
	/bin/rm is needed by jre-1.6.0_10-fcs.i586
	/bin/sed is needed by jre-1.6.0_10-fcs.i586
	/bin/sort is needed by jre-1.6.0_10-fcs.i586
	/bin/touch is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_10-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_10-fcs.i586
	/bin/sh is needed by jre-1.6.0_10-fcs.i586
Done

Could anyone tell me what is wrong? Why there are a bunch of file commands that are missing?

Thanks so much!
-Claire

---

### Post by taurus on 2008-11-06
Why not just install it from the repos?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by ww711 on 2008-11-06
> **hclaire said:**
> Hi,

So I downloaded the jre-6u10-linux-i586-rpm.bin and tried to install the rpm file. But it says




rpm - are usually for redhat/centos linux os.

deb - are for ubuntu/debian 

and do what tarus suggested.

---

### Post by IanWood on 2008-11-11
> **taurus said:**
> Why not just install it from the repos?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```


Hi, 

I want to install Java JDK 6u10 in Hardy Heron. 

The Synaptic Package Manager in 8.04 has version Java 6_07 and 8.40 has Java JDK 6_10. How do I install 6_10 in 8.04. I want to keep 8.04 at work as the newer Xorg doesn't work well with the Matrox card in my PC. 

Cheers

Ian

---

### Post by taurus on 2008-11-11
> **IanWood said:**
> Hi, 

I want to install Java JDK 6u10 in Hardy Heron. 

The Synaptic Package Manager in 8.04 has version Java 6_07 and 8.40 has Java JDK 6_10. How do I install 6_10 in 8.04. I want to keep 8.04 at work as the newer Xorg doesn't work well with the Matrox card in my PC. 

Cheers

Ian

If you want to install java and it is not available from the repos, you can download the .bin, NOT the .rpm.bin version.  Then, you can move it to /opt with the sudo and unpack it there.

```
cd ~/Desktop
sudo mv java_filename.bin /opt
cd /opt
sudo chmod 755 java_filename.bin
sudo ./java_filename.bin
```
That would unpack it in /opt.  Now, you just have to configure it so your system would use the new version.

```
sudo update-alternatives --config java
```
And make sure you pick the new version from the list.  Now, you can check to see if your system is using the new version with

```
java -version
```

---

### Post by IanWood on 2008-11-12
Thanks Taurus,

Is there a way to get Ubuntu 8.04 to be able to "see" the same version of the jdk as Ubuntu 8.10? The reason I ask is that my machine at home with 8.10 has version JDK 6u10 installed by default, so it must be possible for Ubuntu to manage this. Is this due to each Ubuntu version using different repos?

If this isn't possible I will follow your instructions, but I would rather have Synaptic manage packages. 

Thanks again for your help,

Ian

---

