---
title: "Installation Hangs on Load"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by seismic1981 on 2007-03-07
This is my first time trying to install Ubuntu, and I have limited knowledge of operating systems other than the Windows family.

I downloaded and burned the 6.10 release for the x86 processor, and when I boot from the disc, I get the options to load/install ubuntu, start in safe graphics mode, mem test, etc.

When I select that I wish to install/load, or start in safe graphics, the Ubuntu loading progress screen comes up, the one with the Ubuntu logo and the little loading slider. The bar pings back and forth a few times, and then it stops on one side (like it was a normal progress bar that froze at about 2%). I'm not sure what to do besides trying another release, does anyone have any ideas about possible conflicts with my hardware? Does Ubuntu have the ability to start an installation on a SATA drive without any extra files (unlike WinXP)?

I'm running:
Vista Ultimate RC1 on a single NTFS partition
Intel DG965WH Media Series Motherboard
Intel Core 2 Duo E6300
2GB GSkill 800MHz DDR2
WD 160GB SATA HD
ATi Radeon X1800XL
Soundblaster Xfi Xtremegamer
Lite-on DVD/CD combo writer



Thanks!

---

### Post by Kateikyoushi on 2007-03-07
Most likely the videocard is not detected correctly.
Follow these steps [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3") or try the alternate install CD.

---

### Post by sauyeeluo on 2007-03-08
aside from the video card possibly not being detected...

it could also be possible that you burned a coaster. i had a problem a few weeks ago with some live cds that gave me fits. so after trying several live cds in different machines it turned out that my burner was flaking and burning coaster after coaster.  so i'd check the md5sums and possibly reburn another cd.

 in addition, try to start up in vebrose mode and not rely on the ubuntu gui. see if any error messages show up.

---

### Post by seismic1981 on 2007-03-08
> **Kateikyoushi said:**
> Most likely the videocard is not detected correctly.
Follow these steps [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3") or try the alternate install CD.

I followed the directions in that post, and it didn't work for me. It looked as if, when I typed "chroot /root nano /etc/x11/xorg.conf" that the config file didn't exist. I went into the etc directory and it didn't have an x11 directory inside it. It also gave me error messages about "nano", saying that it couldn't execute.

I'll try getting the alternate, thanks for the response!

---

### Post by seismic1981 on 2007-03-08
> **sauyeeluo said:**
> aside from the video card possibly not being detected...

it could also be possible that you burned a coaster. i had a problem a few weeks ago with some live cds that gave me fits. so after trying several live cds in different machines it turned out that my burner was flaking and burning coaster after coaster.  so i'd check the md5sums and possibly reburn another cd.

 in addition, try to start up in vebrose mode and not rely on the ubuntu gui. see if any error messages show up.

How can I check the sum of the CD? I looked at the tutorial, and it said to execute the following:

"md5sum -c md5sum.txt | grep -v 'OK$'"

On my Vista machine it says "grep" is an invalid file. I'm not sure exactly what I'm typing in the command line. I tried just sending the md5 text file on the CD to the md5 program from the tutorial, and it gave a hash, but I don't see a hash that I could compare it to on the hash list. Is it the same hash as the iso?

---

### Post by watson540 on 2007-03-08
no you get the md5sum.txt file from where you downloaded the iso

---

### Post by seismic1981 on 2007-03-08
> **watson540 said:**
> no you get the md5sum.txt file from where you downloaded the iso

Ya, I tried the md5 listed on the website, and compared it to the release iso that I have. It was correct.

On [this page]("https://help.ubuntu.com/community/HowToMD5SUM") they mention how to check the md5 of the cd itself, to see if it burned correctly.

I tried to use the "check cd integrity" option in the ubuntu cd boot screen, and it did the same thing as the safe vga and installation modes.

---

### Post by Kateikyoushi on 2007-03-08
Boot from the cd at the menu press F6 then start with these options, enter one at a time. Not sure that this will help but something on your motherboard can cause the installer to hang.

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by seismic1981 on 2007-03-08
> **Kateikyoushi said:**
> Boot from the cd at the menu press F6 then start with these options, enter one at a time. Not sure that this will help but something on your motherboard can cause the installer to hang.

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

It gives me a single line to enter those commands in, do I just enter them one after another? Like "Boot: linux noapic Boot: linux pci=irqroute..." or do I have to put something in between?

I'm really new as far as linux and commands :)

---

### Post by watson540 on 2007-03-08
no you have to try them one at a time and ignore the word boot and linux, just add them onto the end of the line. noapic first. try to boot, then try to boot with the next, an the next...

---

### Post by seismic1981 on 2007-03-08
> **watson540 said:**
> no you have to try them one at a time and ignore the word boot and linux, just add them onto the end of the line. noapic first. try to boot, then try to boot with the next, an the next...

Awesome, thanks!

---

### Post by seismic1981 on 2007-03-08
Well, I downloaded the 6.06 alternate installation ISO, and burned it. I figured I might as well try a different version, since I was doing the alternate install.

I started up the text-mode installation, and after loading the installer, it told me that there was no cd-rom device detected. I tried to use a few of the drivers listed, with no luck. I'm wondering if that was the problem with the other disc, as well.

---

### Post by watson540 on 2007-03-08
if you boot under expert mode with alternate cd i think it gives you an option to install from an iso somewhere in there in fact i know it does

---

### Post by Kateikyoushi on 2007-03-08
If can not find the drive try to boot with pci=nomsi.

---

### Post by seismic1981 on 2007-03-09
> **Kateikyoushi said:**
> If can not find the drive try to boot with pci=nomsi.

I tried that and it tells me nomsi doesn't exist, or something to that effect.

---

### Post by Kateikyoushi on 2007-03-09
Well I searched for your mobo and it came up with solutions, the problem is the ide controller.
One solution was to install ubuntu on another machine then move the hdd and correct all the the problems which come up.

The other is a nicer solution but no way as comfy as the install cd unfortunately seems curretly these are your choices [LINK]("http://www.chiark.greenend.org.uk/~twomack/DG965WH.txt")

If a 700MB download is no problem try feisty herd5 cd which is the newest of ubuntu and might support your mobo.

---

### Post by seismic1981 on 2007-03-09
> **Kateikyoushi said:**
> Well I searched for your mobo and it came up with solutions, the problem is the ide controller.
One solution was to install ubuntu on another machine then move the hdd and correct all the the problems which come up.

The other is a nicer solution but no way as comfy as the install cd unfortunately seems curretly these are your choices [LINK]("http://www.chiark.greenend.org.uk/~twomack/DG965WH.txt")

If a 700MB download is no problem try feisty herd5 cd which is the newest of ubuntu and might support your mobo.


Great info! Thanks a lot. Since I'm so new to Ubuntu, I think I'm going to hold off on the new download, but I will definitely give the directions in the text file a shot. Or I might just move my HD over to one of my other PCs for a bit. :)

---

### Post by ender1598 on 2007-04-07
> **Kateikyoushi said:**
> Boot from the cd at the menu press F6 then start with these options, enter one at a time. Not sure that this will help but something on your motherboard can cause the installer to hang.

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

I followed these instructions for my Sony Vaio PCV-W30 computer and was about to give up when the last one finally got me to a working desktop.  I was able to install various programs and run various functions.  I went ahead and ran the install on the desktop and it said it was completed successfully.  Now I am getting the same problem when booting up but I don't have the option of doing "irqpoll" like with the livecd.  What can I do to fix this problem?  What does running "irqpoll" do anyways?  I'm running 7.04 by the way.  Thanks for any help.

---

