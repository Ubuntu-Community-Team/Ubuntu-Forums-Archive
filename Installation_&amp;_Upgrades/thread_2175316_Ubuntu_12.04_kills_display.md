---
title: "Ubuntu 12.04 kills display"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by dan-bower88 on 2013-09-18
Hey,

I recently purchased a new PC which I built myself. The specs are as follows:

- Intel i5-4670k (Haswell) overclocked to 4.5GHz
- AMD HD 7870
- Samsung Evo 250GB SSD
- 8GB DDR3 RAM
- Gigabyte Z87-HD3

As soon as I built it I installed Windows which went without a hitch. Since then I've done plenty of gaming on it and there's been absolutely no issues whatsoever. However that all changed when I tried to install Ubuntu...

I tried to install from a 12.04 ISO I downloaded a few months back. The installation did complete but as soon as I attempted to boot into Ubuntu it just killed my display (flickering power LED). After feeling quite frustrated I simply formatted the partition then tried to boot up the LiveCD. This complained about of a lack of video memory then done the same thing as when I tried to boot up from my partition. I assumed a lack of drivers were bundled in the old ISO so today at work I downloaded the latest 12.04 ISO and burnt it to disk. I've just tried to use the LiveCD functionality but I can't even get to that stage in the boot process now (i.e. the bit where it asks if you want to use LiveCD or install).

The haswell chip actually has a video card built into it. I thought Ubuntu might be sending data to that output but when I insert my monitor into the respective DVI slot it doesn't even give a display on boot so I think that's a non-starter. 

Does anyone have *any* ideas what might be causing this? I simply refuse to code in a windows environment and considering how much I spent on the PC I'm pretty gutted I can't get Ubuntu working on it. I'd appreciate any help!

Cheers,

---

### Post by grahammechanical on 2013-09-18
This does not help in the present situation but it may help if you get Ubuntu to install.

[http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html](http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html)

If you do manager to get a working Install Ubuntu session then do not tick to install third party software. That will bring in a proprietary video driver that may not be compatible. The live session uses the Nouveau open source driver. It be best to let Ubuntu install with Nouveau and then install the Intel Haswell driver afterwards.

As for the live session do you get to the first purple screen> The screnn with the two icons at the bottom? If so press enter twice and you will get to a text based screen. Press F6 and in the little menu at the bottom right select nomodeset and press Enter and then Esc to get back to the text based Try - Install screen and select either one and see what happens.

Regards.

---

### Post by dan-bower88 on 2013-09-18
Thanks for the response.

I'm not actually using the video card built into the haswell chip, I'm using an AMD HD 7870. I just brought it up as it might be causing issues.

I do indeed get the purple screen and I just tried the "Try Ubuntu without install" option with nomodeset enable. It failed to boot but it didn't kill my display like last time. 

I'm quite reluctant to actually do the install as last time I selected the "install alongside windows option" but it still messed up the windows boot loader (trying to boot windows from grub just loaded up grub again..some weird loop). I selected "/" as the mount point as it was the recommended option when reading through the forum. That's separate issue though.

---

### Post by dan-bower88 on 2013-09-19
Bump. There must be something I can do. From searching the forums there doesn't seem to be any conflicts with Ubuntu and the HD 7870.

---

### Post by dan-bower88 on 2013-09-20
OK guys I got this resolved.

Essentially the most recent 12.04 ISO is broken for my hardware. There's no way to get it working. I tried booting up the installation with nomodeset enabled and actually noticed it produces an error which is as follows: "Starting load fallback graphics devices [fail]".

I got it working by using my old 12.04 ISO and ensuring that I didn't tick the "install third-party software" checkbox during the installation. This didn't require a nomodeset. 

As polished as Ubuntu is as a whole, this aspect of it is pretty shoddy. Where would be the best place to report this issue?

---

### Post by Quackers on 2013-09-20
The Haswell chips are really quite new and were almost certainly never even heard of when 12-04 was developed.
Generally if you're using brand new hardware it is advisable to use the newest version of Ubuntu as support will be better.
I would suggest trying 13-04.

---

### Post by dan-bower88 on 2013-09-20
I appreciate the thread as a whole is quite confusing due to the various issues but seems you just haven't read all of the posts. The ISO I downloaded months ago eventually resulted in a successful installation whereas the one I downloaded two days ago would kill my display if I booted from CD and just let it run. I can't see how that's related to my CPU.

---

### Post by Quackers on 2013-09-20
Kernels change in different Ubuntu versions. Some may even have regressions in some respects.
It seems strange that the version you originally downloaded now boots without any boot options whereas it didn't seem to earlier.
Occasionally a system will boot a live cd/usb and get to the desktop without a boot option but the actual installed system that results from that cd/usb can require boot options to boot. That may be the case with your original installation, I don't know.

---

### Post by Jonathan Precise on 2013-09-20
> **dan-bower88 said:**
> Essentially the most recent 12.04 ISO is broken for my hardware.

Probably it was a faulty download. Check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows") (scroll to the part "Checksums calculator"). Post it here, or compare with these ones:

[QUOTE=32-bit MD5SUMS]Desktop:
[COLOR=#000000]c4f4c7a0d03945b78e23d3aa4ce127dc
[/COLOR]
Alternate:
[COLOR=#000000]927f06b00821cb4069ce359fe1ec7edb
[/COLOR]
Server:
[COLOR=#000000]e7917ff0543d8248d00ffb166def849e[/COLOR][/QUOTE]

[QUOTE=64-bit MD5SUMS]Desktop:
e2da0d5ac2ab8bedaa246869e30deb71

Alternate:
ca4ecd32f1a4c6917c951f45395901ff

Server:
[COLOR=#000000]2cbe868812a871242cdcdd8f2fd6feb9[/COLOR][/QUOTE]

---

### Post by dan-bower88 on 2013-09-20
> **Quackers said:**
> It seems strange that the version you originally downloaded now boots without any boot options whereas it didn't seem to earlier.

Indeed. The only thing that I done differently was not check "Install third-party software". 

> **Jonathan Precise said:**
> Probably it was a faulty download. Check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows") (scroll to the part "Checksums calculator"). Post it here, or compare with these ones:

I've actually tried with two different ISOs. I initially downloaded and burned it to disk at home. This didn't worked so I downloaded and burned it to disk at work. Both failed to reach the installation stage.

---

### Post by curt2 on 2013-09-24
I am having a similar issue getting "Starting load fallback graphics devices [fail]".
However,  I suspect that it is due to a 3rd party (Nvidia) driver for my VGA  card.  i.e. unlikely to have anything to do with Haswell as mentioned  above.
I put Ubuntu 12.04 (downloaded 22 Sept 2013) on my old PC:
    Asus P5W DH, Some intel dual core proc, ~4GB RAM, and an Nvidia GTS450 - all several years old.
It all ran great at first.  (This is my first Linux venture.  Total noob.)
THEN I got the bright idea of installing the 'latest' graphics card driver  er module, whichI downloaded from NVidia for Linux.
While I could get it downloaded, I couldn't' get it to install.  Kept getting a root error.
So,  after hunting round in system preferences (or the like) I found a cute  little icon of a PCI board that did it all for me.  I forget the name  (and currently can't reboot into Ubuntu) but it was something like  "Install 3rd Party Drivers".
It worked a treat.  Downloaded and installed something from Nvidia and looked successful.  So, I went to bed.

Next day - No boot.  I just get a screen full of Starting this that & other, including "Starting load fallback graphics devices [fail]".

[COLOR=#0000ff]I  suspect I need to uninstall the Nvidia module and reinstall the Nouveau  modules.  (I'd prefer to do this than to reinstall the whole OS again  as I already installed and set up my ROR environment.)
Can anyone direct me to a set of instructions on how to do this??[/COLOR]
I can get to Grub, but that's about it.

I'm posting this tome in case you dan-bower88 *might *have accidentally installed the 3rd party AMD driver and gotten the same result.
Thanks for any help!

---

### Post by dan-bower88 on 2013-09-24
Hey curt2.

Sorry to hear your first venture into linux has been a ballache. It is good but can get frustrating when things like this happen.

Well you're certainly right, this third-party driver was causing my issues. After successfully installing Ubuntu using the old ISO I installed the linux driver for my graphics card that I got from AMD's site. It installed fine, asked for a reset and was fine upon booting back up. After that I installed the 500+ updates Ubuntu prompted me to download. After rebooting, Ubuntu failed to load and prompted me with a box saying "The system is running in low-graphics mode" and asked me to configure my hardware. Luckily I could get to the CLI (you might know this as command prompt in Windows) and just reinstalled the graphics card driver I got from AMD. This sorted my issue.

I recommend you just reinstall Ubuntu. You can probably manage it get it working but I don't feel it's worth the effort if you're new to Linux. When you install the graphics card drivers again just make sure you're logged in as root ("sudo su" to switch to root) and execute the install script from the CLI.

Edit

OK just saw that you'd prefer not to reinstall the OS. I imagine if you  downloaded the driver from another machine, got it on  a USB stick then you could try what I done. One would hope it would handle any conflicts with other drivers all for you. If you keep hitting shift before grub boots you should get a recovery option. I've never actually had to do any of this but something you could look into mate. Hope you get it all sorted.

---

### Post by curt2 on 2013-09-28
Thanks Dan,
I've been working and building computers for over 20 years, so I kinda want to 'fix' this issue for the experience. I'm pretty sure it would take less time to reinstall the OS and other stuff, but hey, I've already done that.

Update:  Nope!  Ended up reinstalling after several hours of not getting Ctrl-Alt-F1 to work.

---

