---
title: "xubuntu &amp; Debian jessie, everything else doesn't work.why?"
date: 2014-06-30
forum: Installation &amp; Upgrades
---

### Post by keiner1234 on 2014-06-30
Hi,
i just bought the new Acer Aspire E3-111-C6LG. 
It seems like Windows 7 - 8.1 don't make any problems, but the only Linux distributions anyone get's to work are Xubuntu 14.04 64 bit and Debian Jessie.
Ubuntu 14.04, Linux Mint (Ubuntu & Debian) don't work.
Those who do work are installed with UEFI. All other versions that don't work boot on a live Stick only with legacy Bios aktivated. You can install it from there, but then it won't boot. The live Versions are also not able to use ACPI i guess, if you shut down the computer you have to press the Power Button to turn it off.
Xubuntu und Jessie with uefi don't have that Problem.

Has anyone an idea what might be the reason? Xubuntu and Linux Mint 17 (ubuntu version) should both use Ubuntu 14.04 or not?

Thank you

---

### Post by grahammechanical on 2014-06-30
Xubuntu 14.04 is much closer to Ubuntu 14.04 then Linux Mint is, otherwise it would be called Ubuntu Mint. If Xubuntu 14.04 can be installed, then there is no logical reason why Ubuntu 14.04 does not install since Xubuntu is built on Ubuntu. The same instructions for installing Ubuntu on Windows 8 machines should work with Xubuntu. And the other way around unless we, the user, are doing something different.

As for why this does not happen, it is impossible to say because "does not work" does not provide any information that can be used to diagnose the problem.

Regards.

---

### Post by patricio3 on 2014-07-05
Same Here!!!! I have the Acer Aspire E3-111-C9SD and I have the same problem. 
Win8.1 works perfectly, but the only distribution that work was the old Ubuntu 13.04 and Linpus Linux (with some instabilities). I can run in Live mode the 14.04 but when i try to install it it crashes. I try to install Debian 7.5 (the stable release) and Linux Mint, but it just get stuck on the logo when they try to load. I install with Legacy and works for a while, but the 13.04 works very slowed in the graphic interfase.

What kind of information can I get to diagnose this issue?

Thank you!! :p

---

### Post by ikunat33 on 2014-07-09
I have the exact same issue. I have tried several different bios configurations. I was only able to install mint 17 after writing the ISO to USB using "dd if=mint-distro.iso of=/dev/sdx" and putting the bios to legacy. then it allowed me to install from the live system, which ran perfectly, but would not shut down afterwards and locks up every time i try to restart. It will not even run the live system anymore. :-(

---

### Post by Yves_Archambault on 2014-08-05
Hi, I am very new to Linux.
I have install Ubuntu 14.04 and also tested Kubuntu 14.04 on my Acer E3-111-C32T that was pre-install with w8.1
I have completly remove the Windows partition, disabled UEFI and after setting Quiet boot to disabled all have install ok.

Both version do the same, I unplugged it and close the lid and when I have reopen it, nothing has happen.
It is like it is freeze there. I did not find any key to wake it up.
After pressing the on/off for quiet a long time, 10 sec. I hearded some sound that make me think that now it was really stop.
I press again on on/off, it start to boot, the Kubuntu logo was there and it seems to froze there.

I have done some other tests.
I am trying to re-install with the UBS key but I am unable. It try to look for a CD, I don't understand why.
In bios, I could see the USB key and it is the first in the list followed by the HD.

[IMG]https://dl.dropboxusercontent.com/u/7622838/20140804_194627.jpg[/IMG]

This is what I get when I boot. The Kubuntu logo stay there.
Any body have an clue.

Yves

---

### Post by ffuentese on 2014-08-25
Does anyone else has more information about it? I tried Elementary OS Luna (which didn't even pass the "E" logo at best) and Ubuntu 14.04 64 bits. The last one reached the Live CD and it seems way faster than Windows 8.1 however, when it gets stuck it's over (for example I tried to install Netbeans while I browsed the web with only one tab open in a light webpage) and it got frozen. So I thought it would freeze in the middle of a full installation.

It's a bummer cause it seems to run pretty well.

---

### Post by icebuntu on 2014-09-19
In case anybody cares Slackware64-current with the huge kernel works*. (it fails to boot sometimes, shutdown hangs and sleep doesn't work) but other than that works fine

---

### Post by icebuntu on 2014-11-29
> **icebuntu said:**
> In case anybody cares Slackware64-current with the huge kernel works*. (it fails to boot sometimes, shutdown hangs and sleep doesn't work) but other than that works fine

In case the issue is still of interest I posted on my blog a few issues I had (and fixed) with this laptop: [http://www.sgvulcan.com/linux-on-the-acer-e3-111-aspire-e3-111-c5fn/](http://www.sgvulcan.com/linux-on-the-acer-e3-111-aspire-e3-111-c5fn/)

---

### Post by Rico_Law on 2015-05-26
I have a similar problem with Ubuntu 14.04 LTS and pretty much anything else.  I run Ubuntu on an SSD drive, and it works beautifully and is very fast.  I have several other drives I wanted to test with other OS's, but no matter what they all fail and error out, or just totally freak out.

I tried:
1. openSUSE on an SSD, then again on a normal SATA HDD.  Both times the install would finish, and after connecting it to my network it seemed stable.  The SSD would then never boot it again (stops and crashes at boot), and the HDD is having nightmarish video glitches and updaters that won't ever finish.  I also have an issue where random services will try to start, and then crash my video driver.  The only option is to reboot.  Neither installation is acceptable, or reliable.
2. Fedora on the SSD, and HDD.  I was really looking forward to this one, because I used RedHat back in the day and thought it was great.  First install on the SSD, never able to boot.  Got stuck on loading splash and bonked with errors about missing directories.  The HDD will boot, but when any changes are made to the video driver (I have a Nvidia GTX660), or any muti-tasking is attempted, it freaks out and goes 80's Nintendo on me.  Colors and blocks, like someone unplugged a Coleco cartridge while playing it.  Clearly the video card driver needs some massaging, as I discovered on another forum, and a slew of terminal commands that may or may not fix it.  
3. Slax on the SSD. This was my last effort at making this easy.  It actually does work, with the right drivers, and seems stable...but is very bare-bones.  How robust is it really?  Can it serve as a primary, with the right tweaks?
4. Full Monte.  Full of Fail.  Spends an eternity installing onto a HDD, then will not boot.  Gets to GUI and crashes.  

At each failure, all I would have to do is pop the Ubuntu SSD back in and I was booted and running in 20 seconds flat.  I just hate the Unity desktop, was trying to make it look like SUSE (my favorite style), and then got lost when a bunch of themes in my Unity Config just flat out didn't work, or worked wrong.  I'm no novice, and really don't care about a few sudo commands to shore something up...but working with 12-15 commands and files all over the place can get tedious.  Nothing has worked as simply and as reliably as Ubuntu, so kudos for that, but can we get the themes to work without learning cuneiform?  

Just want the close on the right, and the taskbar on the bottom.  I'm not itching for WIndows, I just think it is a better layout.  

If anyone has any insight, I know there are hundreds of variables that I haven't mentioned, I would be grateful.  I would really like to use openSUSE, but that video card crashes so often it makes it unusable.  At first I thought it was the SSD, but loading each one onto the normal HDD should have worked if the SSD was to blame.

I am going to have to learn sanskrit to be a Linux user, huh?  Thanks everyone.

---

