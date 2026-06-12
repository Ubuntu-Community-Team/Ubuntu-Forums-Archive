---
title: "Cant get Ubuntu to install at all!"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by thegreatwildbeast666 on 2011-02-27
Hi, I am completely new to Linux and have a very old Sony PCG-9201 that I am trying to install Ubuntu 10.10 on. I created a boot cd from the downloaded ISO from the main site. Sometimes I get to the loader screen and sometimes it hangs. I installed a new 80g hard drive and I am almost sure that the DVD player is good. I can load Hiren's tools and get to mini linux and mini XP BUT the install for Ubuntu fails. Is it possible that the write speeds I am using to create the disk are to high? If so can you recommend a app to use to create the boot cd from a win7 OS. The stock  win7 ISO tool doesn't let me choose a speed. I took a few pictures of the screens maybe you can give me some advice. I have been loading to the live environment and then running the install because it seems to get farther along in the process. But it fails nonetheless. I can not boot to usb on this machine so CD is the only option. Also there is no current install on the hard drive. I have formated and checked for errors to make sure its not the HD and it all checks out. I REALLY want to learn linux and to try my hand in development but I need to start from somewhere. One other thing, I tried to install from the ISO directly off my removable HD by mounting it in mini XP. It seemed to get through the install ok but I dont think it created a boot partition so I was never able to get back after reboot. Sorry this is so long but I am very eager to get started.

---

### Post by Quackers on 2011-02-27
Welcome to UF.
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, boot from the live cd and at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language, then on the next screen choose the option to check the cd for errors. If any errors are found in the cd, but the md5sum is ok you will need to burn the iso image to cd at a lower speed.

A couple more things. What graphics card is in use in the laptop and how much ram is installed?

---

### Post by kansasnoob on 2011-02-27
> **Quackers said:**
> Welcome to UF.
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, boot from the live cd and at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language, then on the next screen choose the option to check the cd for errors. If any errors are found in the cd, but the md5sum is ok you will need to burn the iso image to cd at a lower speed.

A couple more things. What graphics card is in use in the laptop and how much ram is installed?

+1!

I was also going to ask what Windows software was being used to burn the CD/DVD? This may be helpful:

[https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

Regarding hardware, if you can get any Linux live media to run on that machine please post the output of the following commands:

```
lspci | grep VGA
```

&#65279;```
cat /proc/cpuinfo|head -8
```

```
free -m
```

---

### Post by dino99 on 2011-02-27
burn at the slowest speed (always) or better use unetbootin

---

### Post by thegreatwildbeast666 on 2011-02-27
I am using this right? Does this mean I need to DL a new copy? As for my video card I have no idea but the ram is 384m.

---

### Post by thegreatwildbeast666 on 2011-02-27
VGA compatible controller : Neomagic NM2380 256XL rev 10

proc : 0
vendor : GenuineIntel
cpu fam : 6
model : 8
model name : Pentium III
stepping : 3
MHz : 744.474
cache : 256 KB

mem Total : 370 used 178 free 192 shared 0 buffers 0 cached 144

---

### Post by thegreatwildbeast666 on 2011-02-28
So any advice guys?  I tried booting to live xp mini and running the tool unetbootin but when I try to select the HD to install it on it only gives me the virtual drive letter. Under USB I can select the drive but it wont boot that way. Also I can't seem to get the tool to work in Linux live. I copied the program into the bin director and set it to execute but it doesn't run. O and I ran the disk check and the CD had one bad file. So I am guessing the write speed is to high. I dled a new copy of the ISO and can get to it in to live environments but no idea how to get a full install from there. Thank you for your help!

---

### Post by Hakunka-Matata on 2011-02-28
[http://releases.ubuntu.com/10.10/MD5SUMS]("http://releases.ubuntu.com/10.10/MD5SUMS")

That site lists the MD5SUMS of all the different Ubuntu 10.10 versions

Those are the checksum value your downloaded & burned .iso CD should produce
If they are equal, you've downloaded and burned a good CD/USB

---

### Post by Hakunka-Matata on 2011-02-28
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

There, that's a more official site that will sort your MD5Sums

---

### Post by Hakunka-Matata on 2011-02-28
You might want to try the Linux distro Puppy.  It has especially low minimum hardware requirements.  It could be a stepping-stone to getting your Ubuntu USB LiveCD burned and booting.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

And you might even end up liking it, for your hardware that is.  It was my first experience with Linux, but I use Ubuntu almost exclusively now.

Good Luck

---

