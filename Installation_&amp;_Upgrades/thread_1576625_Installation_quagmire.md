---
title: "Installation quagmire"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by paul1149 on 2010-09-17
Hi,

I decided to try Linux again, after a 10 yr hiatus. My first attempt, using another distro, on an external USB hard drive, led me straight into GRUB hell when I opted to place the bootloader on my C drive, not knowing that GRUB would leave most of its data on the remote drive. Now I could not boot into Windows unless the external drive was up.

I ended up reinstalling the distro, this time assigning GRUB to the external drive, and using the Win7 (64 bit) recovery cd's command line to heal the C: MBR. At this point the machine would boot straight into windows if the external drive was off, or it would access GRUB if the external drive was spinning. This was the desired behavior.

Now I decided to try the distro that is said to be best for beginners, ubuntu. I was delighted to find that it had a windows installer, but not so delighted to find that though I installed it out on the external drive, it nonetheless put its bootloader on my C drive. Back to Square One. Now I had to navigate the bootloader every time I booted up. Plus, ubuntu would not boot.

To correct this I then decided to run a native ubuntu install. I burned a cd and ran it, but it inexplicably would not see my external drive. I canceled out.

My priority now became getting at least my C drive correct, which meant healing its MBR once again. But unlike with GRUB, now, two tries later, the command via the Windows recovery disk will not remove the broken ubuntu bootloader.

The saving grace is that the bootloader will load windows; and that I should have a working whole disk image, though I am [COLOR="Red"]loathe[/COLOR] to go to that extreme.

And so, my needs now are these:

[INDENT]1. How do I remove the ubuntu windows installer's bootloader from my C drive?

2. Assuming that is accomplished, how can I get the ubuntu installation CD to see my external USB hard drive?
[/INDENT]
At this point I'm having serious reservations about fooling with Linux at all. But at minimum I would like to restore the C drive to where it was before this fiasco occurred.

Thanks,
Paul

---

### Post by davidmohammed on 2010-09-17
... see this [link]("http://www.ehow.com/how_4836283_repair-mbr-windows.html") on how to restore the mbr for windows 7...

---

### Post by davidmohammed on 2010-09-17
... and have a read of [this]("http://forum.notebookreview.com/linux-compatibility-software/514076-install-linux-external-usb-hdd.html") - this guy is asking a very similar question.

---

### Post by paul1149 on 2010-09-17
That eHow page is exactly where I got my bootsect commands. I've tried four variations so far, to no avail, and now I'm looking at using the /force switch, which I have been reticent to do.

bootsect /nt60 c: /force

I'm not clear on what it means by warning that all file handles will be invalidated (see [http://technet.microsoft.com/en-us/library/cc749177(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc749177(WS.10).aspx) ). Are they healed subsequently? If not the current drive print is useless so why bother with the command rather than reformat/reinstall?

The other thread was interesting, and touched almost exactly on my problem. The boot disk it pointed to, Hiren's, look fabulous.

Thanks, while I debate within myself whether I should use the /force switch.

p.

---

### Post by paul1149 on 2010-09-17
I found the **DREAM **tool for dealing with this aggravation.

[INDENT]**[COLOR="RoyalBlue"]EasyBCD[/COLOR]**: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)[/INDENT]

In ONE MINUTE my MBR problem was solved.

I believe I can also use it to add OS's on the USB drive, but I'll have to read up on it.

Meanwhile, can someone tell me why the ubuntu installation disk did not see my USB hard drive? It's listed in my BIOS to boot after the optical drive and before the C: drive.

Thanks,
p.

---

### Post by paul1149 on 2010-09-17
Ok, I found the USB drive, by first clicking use entire drive, selecting the drive, then clicking select partition.

---

### Post by phillipdhall on 2010-09-18
Good work Paul. I'm new to Linux and interested in learning more about this. If easyBCD was able to fix your windows installation, does that mean Ubuntu's windows installer actually modified the windows BCD instead of installing grub? 
 
You say you have disk imaging software available to you, yes? Now that Windows is working, in theory you could:
 
1) image your windows installation
2) wipe clean (at least the active primary partitions)
3) install Ubuntu as a clean fresh install - IE thinking its the only installed OS
4) move the Ubuntu image (MBR and all) to the external
5) restore the Windows image (MBR and all) to the internal.
 
If your BIOS is actually able to read the external as bootable, any time it is connected, it will automatically boot Ubuntu, which would be nifty! I am tempted to try it myself, but then... I like the performance of my RAID-0 system drive...
 
So, my post may not be very helpful to you, Paul, but it did get me thinking.. which helps me learn linux/grub, so thank you!

---

### Post by paul1149 on 2010-09-18
Phillip, I'm unclear on exactly how ubuntu effected the boot change. It was a textual interface, but that doesn't say much. Either it modified the Windows boot configuration or it replaced it, probably with some variation of GRUB.

BTW, the ubuntu windows installation placed ubuntu *in a file* on the designated partition, which I was unhappy to see. I'm not sure of the reasoning behind that. Evidently it's made for extreme ease of use, whereby one doesn't even need to create a new partition? IAC, that installation would not boot up.

I've never used full image restores, which is why I was loathe to try it here on my main machine, but full disk images should capture the boot configuration. I probably should get a knock-around machine to learn on. But as it stands, I have PCLinux and ubuntu on an external USB hard drive, and Win7 on the C drive. If the USB drive is on, the machine goes to grub there due to my BIOS boot order. In grub I still have set to boot Win7 by default but the other OSes are available. If the USB drive is off, the machine doesn't know about grub and goes straight to Win7 without delay.

At this point, the existing grub was installed by the PCLinux distro, which uses a nice graphical interface. After all these changes I need to verify that ubuntu is still bootable, but I know that PCLinux works.

BTW, EasyBCD operates *from within windows*! It makes everything amazingly easy. I think it would have automatically picked up the other OSes and offered to list them, except they were out on a portable device, which necessitates some intermediary steps. And EasyBCD has its own "NeoGRUB" function (also see [http://en.wikipedia.org/wiki/Easy_BCD](http://en.wikipedia.org/wiki/Easy_BCD)), so I suspect that it can work with existing GRUB arrangements as well as build its own.

The sad thing in all this is that I had been suggesting that a friend try Linux in order to set up a sound studio, but now I'm very reticent because of the hurdles installation throws out. I don't need a long-distance phone call telling me that now her entire computer doesn't boot up. If nowhere else, at least the install process should be carefully guided with loads of contextual help to protect the user from very costly mistakes.

---

### Post by phillipdhall on 2010-09-18
Sound studio, eh? I happen to be a full-time Sound Engineer. I work mostly on live events, but do have a Pro Tools project set-up at home. What DAW is she planning on using with Linux?!?

---

### Post by paul1149 on 2010-09-18
I don't know what a DAW is. And she's not planning on Linux, I just saw [_this_]("http://www.techradar.com/news/software/operating-systems/10-best-linux-distros-for-2010-704584") article, which recommends the ubuntu studio and puredyne distros for media, and I thought of her. If you have any ideas that would help her, I'd be happy to pass them on. So far I've introduced her to Audacity.

---

