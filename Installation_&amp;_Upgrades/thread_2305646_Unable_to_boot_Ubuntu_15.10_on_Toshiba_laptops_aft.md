---
title: "Unable to boot Ubuntu 15.10 on Toshiba laptops after several trials and tests"
date: 2015-12-07
forum: Installation &amp; Upgrades
---

### Post by david474 on 2015-12-07
Hello Ubuntu community. I happend to get 2 different toshiba satellite laptops  (2007 and 2012) which have exactly the same boot system and bios (no choice between bios en UEFI...). I used a 16Gb pendrive to try Ubuntu and they both work very well when working from the USB drive. I installed Ubuntu 15.10 on both laptops: one with a 250Gb old HDD and the newest one with a Sandisk 120Gb SSD. I tried installing besides Windows and also from a custom install. No luck, after 3 days of searching and trying different ways, I get the same results on both systems: boot hangs with the black screen with the message saying "Gave up waiting for root device... Busybox...(initramsfs)". I tried the Boot-Repair, it did repair different files, but no luck, neither laptop can boot by itself, but the GRUB file boots ok, I have the choice of OS on the old one (I want to keep Windows Vista on that one in another partition on the same disk). But on the newest one, I only have Ubuntu installed and I still see the GRUB file. Here is the result of the repair report on the newest system: 

[http://paste2.org/n80mJcK5](http://paste2.org/n80mJcK5)

What did I overlooked ?

Thank you
David - new to Ubuntu
Montreal

---

### Post by oldfred on 2015-12-08
Some Intel chips need a boot parameter. The nomodeset is for nVidia & AMD, but you add the Intel one the same way. And some laptops need other boot parameters in addition, like the acpi examples below.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions
[/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

---

### Post by david474 on 2015-12-08
Thanks for you reply [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), when doing this command, here is what I get:
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-prob: error: failed to get canonical path of '/cow.
ubuntu@ubuntu:~$
[URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B][URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B][URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B][URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B][URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B][URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B]
[/B][/COLOR][/B][/URL][/B][/COLOR][/B][/URL][/B][/COLOR][/B][/URL][/B][/COLOR][/B][/URL][/B][/COLOR][/B][/URL][/B][/COLOR][/B][/URL]

---

### Post by oldfred on 2015-12-08
You are trying to update grub on the live installer, you want to do that on your install.
You can chroot into your install, or use Boot-Repair which semi-automates it.
       
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by david474 on 2015-12-09
Since the beginning, I installed 15.10 on the SSD and because it does not boot, I boot from the USB key with 15.10 installed. 
I then make my changes to grub using the xterm with the gedit command. Is that the good way ? (of course its kind of slow I have to reboot everytime on the SSD to check if the changes take effect ...).
This is now the content of my grub:

```
[COLOR=#d3d3d3]
[/COLOR][COLOR=#0000ff][FONT=arial]# If you change this file, run 'update-grub' afterwards to update[/FONT]
[FONT=arial]# /boot/grub/grub.cfg.[/FONT]
[FONT=arial]# For full documentation of the options in this file, see:[/FONT]
[FONT=arial]#   info -f grub -n 'Simple configuration'[/FONT]

[FONT=arial]GRUB_DEFAULT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT=0[/FONT]
[FONT=arial]GRUB_HIDDEN_TIMEOUT_QUIET=true[/FONT]
[FONT=arial]GRUB_TIMEOUT=10[/FONT]
[FONT=arial]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX_DEFAULT="[/FONT][FONT=arial]quiet splash nomodeset"[/FONT]
[FONT=arial]GRUB_CMDLINE_LINUX=""[/FONT]

[FONT=arial]# Usually Intel works with one of these:[/FONT]
[FONT=arial]i915.modeset=0[/FONT]
[FONT=arial]i915.i915_enable_rc6=1[/FONT]
[FONT=arial]video=1366X768-24@60 # but change to your monitor size not 1280x1024 : [/FONT][/COLOR][COLOR=#800080][FONT=arial]1280X1024 is not a choice on that laptop...[/FONT]
[/COLOR][COLOR=#0000ff][FONT=arial]video=VGA-1:1366X768-24@60 # but change to your monitor size[/FONT]
[FONT=arial]# Other settings in addition to above for other hardware related issues[/FONT]
[FONT=arial]acpi=0[/FONT]
[FONT=arial]acpi_osi=linux[/FONT]
[FONT=arial]acpi_backlight=vendor[/FONT]
[FONT=arial]noalpic[/FONT]

[FONT=arial]# Uncomment to enable BadRAM filtering, modify to suit your needs[/FONT]
[FONT=arial]# This works with Linux (no patch required) and with any kernel that obtains[/FONT]
[FONT=arial]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/FONT]
[FONT=arial]#GRUB_BADRAM="0x01234567,[/FONT][FONT=arial]0xfefefefe,0x89abcdef,[/FONT][FONT=arial]0xefefefef"[/FONT]

[FONT=arial]# Uncomment to disable graphical terminal (grub-pc only)[/FONT]
[FONT=arial]#GRUB_TERMINAL=console[/FONT]

[FONT=arial]# The resolution used on graphical terminal[/FONT]
[FONT=arial]# note that you can use only modes which your graphic card supports via VBE[/FONT]
[FONT=arial]# you can see them in real GRUB with the command `vbeinfo'[/FONT]
[FONT=arial]#GRUB_GFXMODE=640x480[/FONT]

[FONT=arial]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux[/FONT]
[FONT=arial]#GRUB_DISABLE_LINUX_UUID=true[/FONT]

[FONT=arial]# Uncomment to disable generation of recovery mode menu entries[/FONT]
[FONT=arial]#GRUB_DISABLE_RECOVERY="true"[/FONT]

[FONT=arial]# Uncomment to get a beep at grub start[/FONT]
[FONT=arial]GRUB_INIT_TUNE="480 440 1"[/FONT][/COLOR][COLOR=#d3d3d3][/COLOR]

I cannot update-grub, I still receive an error message: 
[COLOR=#000000]ubuntu@ubuntu:~$ sudo update-grub[/COLOR]
[COLOR=#000000]/usr/sbin/grub-prob: error: failed to get canonical path of '/cow.[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$
```

[/COLOR]because of that message, I do a "boot-repair" and then I reboot.

What happens now when I reboot from the SSD is that after the GRUB menu, I select Ubuntu, I see a black screen, I see a purple screen (15.10) with the logo Ubuntu for 1-2 seconds, the cursor appears (bigger than normal) and it ends up with the purple background of 15.10. I can move the cursor and see it moving, but there is nothing on screen. It hangs there...

Thank you for your follow-up oldfred

---

### Post by oldfred on 2015-12-09
Do not add the lines I posted to /etc/default/grub.
You need to convert it back to its default.

And you cannot run sudo update-grub from the live installer. The error on /cow is because the command is running on the live installer which it cannot update and not on your install.

Please go back to post #2 and how to add nomodeset. Review the links.
You add nomodeset or one of the Intel boot parameters when booting and you get the grub menu. It is not saved and has to be added each time, but usually nomodeset is not required once you install a proprietary video driver. Only if you have to add one of the other optional boot parameters may after you have booted may you want to add it to grub.

Do you get grub menu when you boot, or do you have to hold shift key from BIOS until menu appears when you reboot.

---

### Post by david474 on 2015-12-14
Dear oldfred,
I got it !
Although I spent 15hours trying to make my 2 laptops working, when I found how, it took me 5min to make both work.

SUMMARY OF SOLUTION:
I installed unbuntu 15.10 from a USB pendrive on 2 toshiba laptops (2007 with HDD and 2011 with SSD)
Still running from the USB drive, I installed Boot-repair and run it from the USB drive
In boot repair, I went into the advanced menu and there was an option (can't remember exactly) to choose NOMODESET 
I executed boot-repair and said yes to make the proposed corrections to the boot files
I removed the USB drive and reboot
It went correctly to the Grub menu where I could choose to boot Ubuntu and it did it ok.

No more black screen, it is very fine and I am discovering with amusement the wonders you guys did in the last 15 years with that OS. Thank you to the Linux/Ubuntu active community. I will probably install it on other computers also in the next few months (mine and others...)

---

