---
title: "Unable to Install Ubuntu on New Acer E 15 E5-573G-79Jp (Hope that's right)"
date: 2015-10-10
forum: Installation &amp; Upgrades
---

### Post by EclecticEngineer on 2015-10-10
So I got a new laptop and was planning on making it dual boot with Windows 10/Ubuntu 15.

I have done this before to four different machines, and although not a complete newbie I will readily admit not an expert either.  Windows 7 machines all 32 - bit ... all worked like a champ!!

This one however has a different story.

I get the laptop to run the initial program where it asks for whether I want to try ubuntu, install ubuntu, run a disk check, etc.  This is after changing the boot source to either a usb CD-ROM I have or a USB Stick I made of the latest 15 version 64 bit of Ubuntu. If I choose either try Ubuntu or install Ubuntu the screen goes blank and nothing else happens.

I tried messing around with the security settings in the UEFI (Acers version of BIOS), basically every configuration I could dream up and no luck, including disabling the security.  Using 'Legacy' in the security gave me 'table error' as well, at least it was an error and not a blank screen.

Sorry if this is too vague?  Obviously I screwed up and ordered the wrong computer (I thought I had checked the list of Ubuntu Laptops, sigh).

Just wondering if there is any feedback, like yep, doesn't work with the new Acers, thanks!  Or here's the technote saying how to get it to work?  Any feedback would be appreciated.

---

### Post by yancek on 2015-10-10
Do you have windows 10 installed and are now trying to install Ubuntu?
If you are installing Ubuntu and plan to install windows 10, it would probably be easier to reverse that and install windows first.
In any case, windows 10 usually wants to install using UEFI although it isn't necessary.  If you install windows UEFI, then you must install Ubuntu UEFI or you will have problems.

After you downloaded the Ubuntu iso file, did you do an md5 checksum to verify the download was good?

---

### Post by oldfred on 2015-10-10
Have seen many Acer, but if Windows is now UEFI, you need to boot Ubuntu installer in UEFI mode to install in UEFI mode.
You may have to turn on allow USB boot and/or turn off secure boot.

And once installed you have to set a supervisory password & enable "trust" on the Ubuntu/grub efi boot files.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI
[/URL]Screenshots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/
      [/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Windows UEFI & Ubuntu BIOS
[http://ubuntuforums.org/showthread.php?t=2292242](http://ubuntuforums.org/showthread.php?t=2292242)
Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]
[/URL]

---

### Post by EclecticEngineer on 2015-10-10
ok guys thanks for that!  I will check it out tomorrow or Monday.

BTW yes Windows 10 is currently installed.  My apologies if that wasn't clear.

---

### Post by oldfred on 2015-10-10
I missed blank screen issue.
What video card/chip do you have.
Generally nomodeset if nVidia or AMD or different boot parameter if Intel.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Looks like a Skylake? And may be then best to use 15.10 even though only in beta, but will be released soon.
Do you know or can control from UEFI settings which video chip is used to boot?

 Skylake needs this boot parameter if booting with Intel:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)



[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by EclecticEngineer on 2015-10-11
Ok spent a bit more time on this.

First messed around with making the efi files listed as 'secure'.  I got that, but realistically have the same problem.  The system seemed to see the usb drive no problem anyway.  I did get a sexy blue 'boot windows or ubuntu screen' once or twice (cool!), but every time went to the blank screen.

I agree that I think the problem is the video driver when the system leaves grub and moves on to vmlinux?  Does that sound correct?

The driver from the UEFI Setup is Intel GOP version 5.5.1028

I entered grub no problem, pressed e and go to the emacs editor

I tried one at a time,

set i915.modeset=0
set i915.i915_enable_rc6=1
set video=1280x1024-24@60  # but change to your monitor size  not 1280x1024(actually 1920x1080)
set video=VGA-1:1280x1024-24@60  # but change to your monitor size

I assumed set needed to be there from another parameter and the fact that I got an error message with out it.

I also tried the following:

set acpi=0
set acpi_osi=linux
setacpi_backlight=vendor

noalpic I did not try as wasn't sure what to do?  set noalpic=1? nolapic=0, which I found after a bit of a web search?

OK any idea's?

---

### Post by oldfred on 2015-10-11
Are you replacing quiet splash with nomodeset or the Intel parameters? 
And it is not set i915.modeset=0, but just i915.modeset=0 or video=1980x1080-24@60

Line changes from something like this (this is my UUID & partitions)
linux    /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=45de38c8-6748-4634-b207-628d9aa8b42b ro  [COLOR=#ff0000]quiet splash[/COLOR] $vt_handoff

to this:
linux    /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=45de38c8-6748-4634-b207-628d9aa8b42b ro  [COLOR=#ff0000]i915.modeset=0[/COLOR] $vt_handoff

---

### Post by EclecticEngineer on 2015-10-12
Thanks for your patience I will give it a go!

---

### Post by EclecticEngineer on 2015-10-12
eh no luck...I was using the 64-bit Ubuntu version and got grub to work, tried the 32-bit version and got nothing as there are no *.efi to make secure in the UEFI.

I tried the display hardware parameters on the vmlinuz with a 64-bit Ubuntu and no luck.  

I think the problem is the 64 bit Intel chip with the UEFI, this doesn't work with Ubuntu correct?

Anyhow if you have anything else to add I am all ears!

---

### Post by oldfred on 2015-10-12
If anything Intel works very well with UEFI. Intel is one of the sponsors/developers of UEFI. And Intel contributes many updates to kernel, support software & video drivers for its chips to work with Linux.

But you have very new hardware and it takes a bit before the updates to kernels are made, then a while before kernels are in standard Linux distributions.
With you new hardware you may do better with 15.10 as it has newest kernel & support software. It still is beta, but will be released by end of month.

You did not say what Intel chip & video you have?
Only 64 bit Ubuntu fully supports UEFI. 
There now is some support for the crippled 32 bit UEFI systems with 64 bit chips, usually very low cost systems where vendor is trying to make it proprietary.

       Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by EclecticEngineer on 2015-10-14
Thanks old_fred...actually learned quite a bit!!

Anyhow will try this nearer the end of the week.

---

### Post by EclecticEngineer on 2015-10-26
So just an FYI.

I was unable to get anywhere with version Ubuntu 15.10. 

In answer to your questions here we go as best I can...

The system has 4 i7-5500u CPU, a google search revealed the following mother board [SIZE=3]
[/SIZE]**[SIZE=3]Acer Aspire E15 Intel N2830 CPU System Motherboard LA-B511P NBMML11002[/SIZE]**

for the display I have two drivers under Windows an intel HD graphics 5500 and an NVIDIA GeForce 940M...is the NVIDIA unit the problem?

Thanks for your input!

---

### Post by oldfred on 2015-10-26
Do you know which video is in control when booting?
Can you set that in UEFI/BIOS, or is it only auto switching.
It probably boots with Intel in low power mode, so one of the i915 settings should work. With nVidia you need the nomodeset to boot, but need to install the latest nVidia drivers for system to work correctly.
You need to use 15.10, every other version is probably too old, kernel wise and other support software.

Slightly older version:
 Mesa 10.5 vs. 10.7 Git, Linux 4.2 Kernel For Intel Iris Graphics 5100
[http://www.phoronix.com/scan.php?page=news_item&px=Mesa-10.5-10.7-HSW-5100](http://www.phoronix.com/scan.php?page=news_item&px=Mesa-10.5-10.7-HSW-5100)
Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)  Dell 17R
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349)

   [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
 Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

Newest version:
      
 Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by nei2 on 2015-12-07
I had the same problem with installing Ubuntu on my newly purchased Acer Aspire E 15 (E5-573G-57N5) and was just able to figure it out, so figured I'd share -- hopefully this will work for others. Note that I wanted a dual-boot config with a preinstalled Windows 10.

The steps are: 1) Downgrade the Acer BIOS, 2) Install Ubuntu, 3) Fiddle with the UEFI configuration to allow booting into the Ubuntu partition.

1. Downgrade the BIOS.

Based on [http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/td-p/386009](http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/td-p/386009) the new BIOS prevents the Ubuntu installer from running with the same symptoms described here (screen goes blank right after grub). To downgrade, use the instructions from:
 [http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/m-p/386281/highlight/true#M3080](http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/m-p/386281/highlight/true#M3080)

They seem complicated, but it's just a two-character change in the config file. With the downgraded BIOS, you will be able to launch the Ubuntu installer (or just boot from the Live CD without installing).

2. Install Ubuntu.

Same as always. For people who already have Windows 8/10 installed, I suggest backing up and following the process from [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

When this is done, you should have the the system installed on the designated partition. The default setup partitioning options worked for me.

3. Configure UEFI to allow booting into Ubuntu.

This is a little tricky. In your Acer BIOS settings (press F2 to get into the BIOS), you must:
a) Set up a supervisor password to enable some of the UEFI boot options.
b) Set Boot Mode to UEFI and Secure Boot to Enabled -- this should be the default.
c) In the Security tab, pick "Select an UEFI file..." to add the default Ubuntu .efi file as trusted. The file you need to add is \EFI\ubuntu\shimx64.efi -- I need to reset the config for this to work, so if you get a strange error message, select "Restore secure boot to factory default", reboot and try again (but only if you don't have a custom configuration which would get lost). See [http://askubuntu.com/a/519619](http://askubuntu.com/a/519619) for the detailed process.

This might also be helpful:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


After all this, when you press F12 to pick the boot device, you should see the EFI device which will take you into grub and allow booting Ubuntu. At least for me this didn't cause any trouble with the existing Windows 10 install either. Good luck, I'm happy to see you can have as much fun with installing Linux as we had in the 90s!

---

### Post by Ajith_Kumar on 2015-12-08
> **nei2 said:**
> I had the same problem with installing Ubuntu on my newly purchased Acer Aspire E 15 (E5-573G-57N5) and was just able to figure it out, so figured I'd share -- hopefully this will work for others. Note that I wanted a dual-boot config with a preinstalled Windows 10.

The steps are: 1) Downgrade the Acer BIOS, 2) Install Ubuntu, 3) Fiddle with the UEFI configuration to allow booting into the Ubuntu partition.

1. Downgrade the BIOS.

Based on [http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/td-p/386009](http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/td-p/386009) the new BIOS prevents the Ubuntu installer from running with the same symptoms described here (screen goes blank right after grub). To downgrade, use the instructions from:
 [http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/m-p/386281/highlight/true#M3080](http://community.acer.com/t5/E-and-M-Series/Acer-Aspire-e5-573g-You-can-not-install-any-one-Linux/m-p/386281/highlight/true#M3080)

They seem complicated, but it's just a two-character change in the config file. With the downgraded BIOS, you will be able to launch the Ubuntu installer (or just boot from the Live CD without installing).

2. Install Ubuntu.

Same as always. For people who already have Windows 8/10 installed, I suggest backing up and following the process from [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

When this is done, you should have the the system installed on the designated partition. The default setup partitioning options worked for me.

3. Configure UEFI to allow booting into Ubuntu.

This is a little tricky. In your Acer BIOS settings (press F2 to get into the BIOS), you must:
a) Set up a supervisor password to enable some of the UEFI boot options.
b) Set Boot Mode to UEFI and Secure Boot to Enabled -- this should be the default.
c) In the Security tab, pick "Select an UEFI file..." to add the default Ubuntu .efi file as trusted. The file you need to add is \EFI\ubuntu\shimx64.efi -- I need to reset the config for this to work, so if you get a strange error message, select "Restore secure boot to factory default", reboot and try again (but only if you don't have a custom configuration which would get lost). See [http://askubuntu.com/a/519619](http://askubuntu.com/a/519619) for the detailed process.

This might also be helpful:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


After all this, when you press F12 to pick the boot device, you should see the EFI device which will take you into grub and allow booting Ubuntu. At least for me this didn't cause any trouble with the existing Windows 10 install either. Good luck, I'm happy to see you can have as much fun with installing Linux as we had in the 90s!


Thanks a lot for your redirection for installing Ubuntu! :D I had struggled for 5 days continuously to install it.
Thanks a lot man :D Lots of love!

---

### Post by joseph71 on 2016-01-06
Hi Guys, I read this post from the first page because I have the same problems with my new Acer E15 E5-573G-79UB, so you could confirm me that this instructions of downgrading BIOS and so on can solve the booting of Ubuntu or also Debian (that I really need on this machine)???

---

### Post by oldfred on 2016-01-06
I would first confirm that just password & setting trust does not solve issue.
I would also check & maybe complain to Acer if you have to downgrade UEFI/BIOS. That should never be a solution.
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

      
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by spandey on 2016-01-07
Just update to latest BIOS and you will be able to install any linux. I had the same problem at it works now.

---

