---
title: "ubuntu 64bit not booting"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by shteren on 2014-02-24
hi all, i've had ubuntu 32bit 13.10 installed on my laptop which runs core i5-540m and nvidia 330m optimus gpu with 4 gb ram.

recently i needed to install matlab 2012b which only runs on 64 bit linux, so i decided it's time to upgrade my ubuntu to 64 bit as i've heard most problems with 64 bit has been solved.
so i downloaded 13.10 64 bit iso, flashed it on my usb stick using unetbooting (the usb stick is not the problem, my current 32 bit was installed succesfully from it), opened up the live-installer everything went fine and i chose to reinstall on my current installation as to not lose my home folder.
installation went fine, but the system whould stuck after grub... it should say "/sbin/init exec format error" and then kernel panic...

tried to google it but found no solution or similar cases... purging grub and reinstall it using live-cd didn't help...
so i said, ohh hell lets do a clean install, so i wiped clean my ext 4 partition and did a brand new install.

still no go... not the same error as before, just stuck at purple screen... i tried enabling bootlog at /etc/default/bootlogd but it stayed empty...
so i decided i'll try the 12.04 LTS 64 bit, and again excatly the same problem.

i have no idea why it's not booting properly... i don't even get error messages or boot log or anything... just clean installs...

now i'm running 13.10 32bit again which installed and boots flawlessly...

i had 64bit ubuntu 10.4 in the past working fine, but it had lots of 64bit competability issues so i dumped it, my windows 8 runs on 64 bit on the other partition without problems...

can anyone help? or has encountered similar issue?

---

### Post by QIII on 2014-02-25
Hello!

Did you check the md5sum on the iso you downloaded initially?

---

### Post by shteren on 2014-02-25
well i did not, but since i've tried two different iso's (12.04 and 13.10) and both booted up to live cd perfectly fine i suppose it was not the problem.

---

### Post by oldfred on 2014-02-25
If you have an i5, your motherboard probably is both UEFI & BIOS. Which mode did you boot in. Your previous 32 bit had to be in BIOS boot mode as 32 bit does not have any UEFI support.

With nVidia you have to use nomodeset to boot live installer and after install until you install nVidia proprietary driver. I would think you had to do that with 32 bit also?
And some systems need other boot parameters also.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by shteren on 2014-02-25
thanks for your reply! i have an old i5, it's more than 3 years old now, it has no UEFI as it was not present yet when my computer was manufactured. and either way it came without no an os, not with windows 8 preinstalled like UEFI systems.

i don't think the problem is nvidia because the live-cd boots well and if video drivers were my problem i'd be able to go to tty1 using ctrl+alt+1 but nothing happens, the computer just freezes on black screen... and anyhow 32 bit hendles my nvidia optimus card just fine. and it uses the intel video card by default anyway... i can diactivate nvidia through the bios, it's not nvidia....

i'd love to be able to debug it and see what errors comes up but i tried enabling the boot.log and nothing was logged...
the best thing i've had was this screen from when i tried to install 64 bit over my previous 32 bit: [https://copy.com/hnQd8awPA6PF](https://copy.com/hnQd8awPA6PF)

i tried some google and i saw somewhere some people said it might be some ram fault, so i did a ram check and my ram is perfectly fine...

---

### Post by oldfred on 2014-02-25
If you have turned off nVidia, then nomodeset is not required, but Intel sometimes needs boot parameters also.

        Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1


   Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

---

### Post by shteren on 2014-02-25
ok oldfred but i've had video drivers before i could always go to tty1 or tty2 and use terminal to fix this... 

now the omputer boots into blank... i can't do anything. so it doesn't feel like video problem at all... and live cd boots just fine eitherway...

any advice on how i can get a proper log so we can see what the real error it encounters?

> Hello!

Did you check the md5sum on the iso you downloaded initially?
and yes i just did check my md5sums and both iso's match... so no fault there...

BIG EDIT:
i tried reinstalling ubuntu 64 bit again ontop of my new 32bit... 
well i guess it was my mistake all along, my old 13.10 had like 20 different kernel options because i updated it since 11.10 or something.... so i tried a few of them and non worked...

this time around i had only two options, the kernel from 13.10 32bit and the new one that came with the 64bit which was a bit older, 3.11.12 as compared to 3.11.17 with the 32 bit...

anyhow, the 3.11.17 went into panic but the 3.11.12 booted just fine... so it was just a kernel mismatch...

i now have a fully working 64 bit installation... on the other hand it still don't explain why my clean installs didn't boot yestarday... but i'm tired of experimenting so i'll stick to this for now...

---

### Post by oldfred on 2014-02-25
When you did the new install did you reformat / (root). If you did you should not have had any old data. But some use a "dirty" install to preserve data in a /home that is not a separate partition.

You may want to do a though houseclean. Also if new install old kernels in / will not be shown in dpkg and cannot be uninstalled with synaptic or dpkg. You just have to manually remove them.

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

