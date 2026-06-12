---
title: "How to install ubuntu desktop and win10"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by kougami on 2017-04-21
Hi, I want to know how to install ubuntu on my laptop, but I want to be able to choose between Win10 and Ubuntu when the laptop powers on, I mean, during the ubuntu instalation, if is possible to choose an option that creates a dual boot, or I have to do it manually??

Thaks for helping me and sorry if my english is not accurate enough

---

### Post by ubfan1 on 2017-04-21
What you want is called Dual Boot, see [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) for the instructions, and come back here with questions.

---

### Post by kansasnoob on 2017-04-21
> **ubfan1 said:**
> What you want is called Dual Boot, see [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) for the instructions, and come back here with questions.

That is horribly outdated (last edited 2015-06-29) so I'd avoid what's said there if this is a reasonably new laptop.

---

### Post by kansasnoob on 2017-04-21
> **kougami said:**
> Hi, I want to know how to install ubuntu on my laptop, but I want to be able to choose between Win10 and Ubuntu when the laptop powers on, I mean, during the ubuntu instalation, if is possible to choose an option that creates a dual boot, or I have to do it manually??

Thaks for helping me and sorry if my english is not accurate enough

Step #1: Decide which version and flavor of Ubuntu you want to install and then create either a live DVD or live USB. Then you'll want to boot that live DVD/USB choosing only to "Try Ubuntu without installing". Then from the live desktop open a terminal and post the output of this command:

```
sudo parted -l
```

That changes nothing but provides enough info so we can see if this is a UEFI system or an older MSDOS system as well as the number of partitions.

As far as deciding which version and flavor to install I would always try the "amd64" (64 bit) version, and only use the "i386" (32 bit) version if absolutely needed.

The second consideration is period of support. Most users will want to stick with the LTS versions which have either 3 or 5 years of support from the date of release depending on the flavor, whereas the interim releases are supported for only 9 months:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I also prefer skipping the 2nd, 3rd, and 4th point releases of the LTS versions to avoid HWE-EOL which requires an early kernel and X-stack upgrade:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A16.04.x_Ubuntu_Kernel_Support)

So I'd personally **stick with the 16.04.1 version** of whichever flavor you choose.

You didn't mention any preference of "flavor" but you also need to take into consideration that Ubuntu is switching from the Unity desktop environment to the GNOME Shell DE by 18.04, and Ubuntu GNOME will cease to exist as a separate flavor. Based on that I'm personally using Ubuntu GNOME 16.04.1 amd64 for all of my fresh installs because both Ubuntu and Ubuntu GNOME 16.04 will be able to upgrade directly to Ubuntu 18.04 with the GNOME DE around August 2018.

More about "flavors" here:

[https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

Please feel free to ask as many questions as you wish in deciding which version/flavor you wish to install :)

---

### Post by RobGoss on 2017-04-21
Hello and welcome to the forum, Dual booting is a good way to see how Linux works especially Ubuntu, one thing I do recommend doing is making a complete backup of the Windows installation just in case anything goes wrong

I would also read as much as you to learn what to expect from Ubuntu it's not like Windows so you should understand this right from the start

Like all of us here once you've use Ubuntu for awhile you get to love it

Best of luck with getting started with Ubuntu

---

### Post by oldfred on 2017-04-21
If new system with Windows 10 pre-installed, then it is UEFI.
How you boot install media UEFI or BIOS is then how it installs. And from UEFI boot menu you will get two options to boot Ubuntu installer. One usually is clearly UEFI:flash and other flash which is the BIOS/Legacy/CSM boot option. Flash may be name or label of your flash drive.

Review UEFI Summary install steps in link in my signature if not familiar with UEFI.
Many links to more info if needed.

---

