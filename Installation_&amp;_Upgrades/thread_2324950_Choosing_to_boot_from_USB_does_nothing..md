---
title: "Choosing to boot from USB does nothing."
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by vlolun.flow on 2016-05-17
Hello. I'm attempting to install Lubuntu 16.04 via USB. I burned the 64bit .iso to my USB using the command:```
dd bs=4M if=/path/to/iso of=/path/to/device && sync
``` I restarted my computer, selected the USB from the list of bootable devices, the screen flashed black for a second and then did nothing, returning to the select screen. I'm sure I've run into this problem before, but I can't for the life of me remember what I did, nor can I think of the correct combination of search terms that will give me something relevant to my situation. (Just to make sure you all know that I really tried to dig up a solution before I came here). I tried changing the boot priority in my BIOS, but it skipped right over the USB and booted from my SSD. I'm sure this implies something, but I'm not sure what. I then found something that looked helpful that suggested enabling CSM support and EFI-Legacy, and disabling secure boot. Only I found that these settings were already in effect. So now I'm pretty unsure of what I need to do. It seems I may need to update my BIOS, but I'm unsure how to do that with Linux already installed. (I'm on a Lenovo ThinkPad, by the way)I found this: [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate) which suggests that I can update my BIOS, but apparently the ThinkVantage page mentioned under Lenovo doesn't exist, and the tidbits the page I linked offers only seem to apply to Windows. I believe I am now sufficiently confused to ask for help here. Thank you!

---

### Post by ubfan1 on 2016-05-17
Which Thinkpad model?  I had pretty good luck with a W520 and 16.04 recently.  Which video in particular.  Maybe turn off discrete video and use intergrated until you get installed.  Did you hashcheck the downloaded ISO?
See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at   [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.

---

### Post by vlolun.flow on 2016-05-19
The L430 model. I hashcheck the iso, came out fine. I don't know how to turn discrete video off. How and why would I go about doing that?

---

### Post by ubfan1 on 2016-05-19
My Thinkpad BIOS settings offer Discrete/Integrated/Optimized video settings.  The Integrated setting uses the Intel video, which is what you might try.

---

### Post by vlolun.flow on 2016-05-20
Hrm. My BIOS doesn't seem to have those options. I'll poke around and see if I can find another way to do that.

---

### Post by ubfan1 on 2016-05-20
which video hardware do you have?   lshw -C video    will tell you.   You may just have a driver issue -- the Nvidia chips typically need "nomodeset" to get booted until the proprietary driver is installed.

---

### Post by vlolun.flow on 2016-05-29
Here's the output of that command:  *-display                      description: VGA compatible controller       product: 3rd Gen Core processor Graphics Controller       vendor: Intel Corporation       physical id: 2       bus info: pci@0000:00:02.0       version: 09       width: 64 bits       clock: 33MHz       capabilities: msi pm vga_controller bus_master cap_list rom       configuration: driver=i915 latency=0       resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:4000(size=64)Okay, I'll try that and let you know how it goes

---

### Post by ubfan1 on 2016-05-29
Looks like you just have the Intel integrated video, using the i915 controller -- should not be any problems with that (I don't see any Nvidia controller, so you probably dont have that).  Did you do the Windows power options to turn off fast boot (if you are dual booting)?  Can you check the USB on another machine?

---

### Post by sudodus on 2016-05-30
Some old and middle-age Intel graphics chips have problems with Lubuntu 16.04 LTS, but if you install a program package, the problems are solved. Maybe it will help in your computer.

```
sudo apt-get install xserver-xorg-video-intel
```

You can also get a tarball with that Intel program package pre-installed via the One Button Installer or a compressed image file via mkusb according to the following links,

[One Button Installer, post #37-38: New Lubuntu tarballs and compressed image files with 'xserver-xorg-video-intel' for Intel graphics](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384)

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by vlolun.flow on 2016-06-04
> **ubfan1 said:**
> Looks like you just have the Intel integrated video, using the i915 controller -- should not be any problems with that (I don't see any Nvidia controller, so you probably dont have that).  Did you do the Windows power options to turn off fast boot (if you are dual booting)?  Can you check the USB on another machine?I am not dual booting, but I can check it on a different Windows machine. Also, sudodus, I ran that line as suggested, and it appears to already be installed: xserver-xorg-video-intel is already the newest version```
xserver-xorg-video-intel is already the newest version. xserver-xorg-video-intel set to manually installed. 0 upgraded, 0 newly installed, 0 to remove and 171 not upgraded.
```

Apologies for double posting, but I've yet to get the edit post button on this site to actually work. The ISO did not work on the other machine I tested it on, which was a Windows machine. I chose to boot from the USB and instead Windows started normally. I can only surmise that there's something wrong with the way I put the ISO on the USB.

---

### Post by sudodus on 2016-06-06
I think we can only guess what is the cause of your problems, and keep trying different things.

- Which version of Lubuntu is it? What is the complete name of the iso file? (i386 corresponds to 32-bits, amd64 corresponds to 64-bits.)

- Have you checked with md5sum that the download was good? See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- Is the computer booting in UEFI mode or BIOS mode?

- Did you install into the whole drive (not into a partition)? mkusb will help you get it right, using dd under the hood. It also helps you write to the correct drive (avoid the mistake to overwrite valuable data in other drives).

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

- It is a good idea to try in several computers in order to find out if the problem is with the USB drive or with the particular computer.

-o-

You may have replied before to one or more of these questions, but there are many posts in the thread and it is a good idea to summarize it in one place.

---

### Post by vlolun.flow on 2016-06-06
Thank you for merging the posts, I'm afraid you may have to do it again. I have, at least, found a workaround. There was something wrong with how I put the ISO on the USB. I instead used the Windows machine and UNetBootin to make it work. That can be found here: [https://unetbootin.github.io/](https://unetbootin.github.io/) . This, I know, is pretty popular software. Figured I'd link to it all the same.

---

### Post by sudodus on 2016-06-06
Congratulations :KS

It is not a workaround, it is a solution, when you use one of the working tools to create a working USB boot drive :-)

If you feel that your problem described in the opening post is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

If/when you have ***another problem*** or item to discuss, please create a ***new thread*** with a good descriptive title. That way you have the best chances to get help from people who know about that problem.

---

### Post by vlolun.flow on 2016-06-06
Done! Thank you so much for your help

---

