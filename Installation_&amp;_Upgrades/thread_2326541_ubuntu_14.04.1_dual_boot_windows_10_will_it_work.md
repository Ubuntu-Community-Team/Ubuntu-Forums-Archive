---
title: "ubuntu 14.04.1 dual boot windows 10 will it work"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by Stu_Monash on 2016-06-02
Hi, will lubuntu-14.04.1-desktop-i386.iso or edubuntu-14.04.1-dvd-i386.iso install on an installed windows 10 desktop and boot afterwards or is 14.04.1 not windows 10 aware?  Thanks

---

### Post by kansasnoob on 2016-06-02
It's good that you asked. There was a huge problem with the installer in 14.04.1:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

The only safe way to install using the 14.04.1 media is to use the advanced partitioning option which is named "Something else".

One more thing of concern. Most Win 10 installs are UEFI and I don't think the i386 version of Ubuntu can be installed in UEFI mode. So please post the output of the following command using the live version of the DVD/USB:

```
sudo parted -l
```

PS: Don't be discouraged by that installer bug, once installed 14.04.1 is rock solid once updated. That's what I'm still using for fresh installs because 16.04 is far too buggy and the later point releases of 14.04 reach HWE EOL too soon:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Stu_Monash on 2016-06-02
Thanks for the great response.  As I have not used Linux before, time to do some research on what you said and find the command line system.

I had a read about the huge problem with the installer in 14.04.1.  The link seems to be some sort of knowledge base about bugs.  Having not seen this web page before and knowing you use it, how did you find this bug out the 1600 odd bugs listed.  Is there some type of search engine linked to it?  Impressive find!

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192"]https://bugs.launchpad.net/ubuntu/+s...y/+bug/1265192

[/URL]

---

### Post by kansasnoob on 2016-06-02
> **Stu_Monash said:**
> I had a read about the huge problem with the installer in 14.04.1.  The link seems to be some sort of knowledge base about bugs.  Having not seen this web page before and knowing you use it, how did you find this bug out the 1600 odd bugs listed.  Is there some type of search engine linked to it?  Impressive find!

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192"]https://bugs.launchpad.net/ubuntu/+s...y/+bug/1265192

[/URL]

I only knew because I do QA testing for Ubuntu GNOME.

---

### Post by Stu_Monash on 2016-06-02
Ok I have had a look into UEFI.  So its a BIOS replacement that is accessed from the boot environment.  I did some research on Windows and if I type Command>run>MSInfo32 and look for the report on BIOS and it says legacy so BIOS I have.

I assume I will install edubuntu-14.04.1-dvd-i386.iso on the BIOS non UEFI boot of Windows in i386,  Of course I will take a backup first!

---

