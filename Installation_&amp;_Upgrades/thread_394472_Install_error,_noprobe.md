---
title: "Install error, noprobe?"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by ascendant on 2007-03-26
I try to install Feisty, install stops with this "screenshot":
[SIZE="5"]```
udevd-event[2093]: run_program: '/sbin/modprobe' abnormal exit
BusyBox v1.1.3 (Debian 1:1.1.3-3ubunut3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/ash: can't access tty: job control turned off
(initramfs) _
```[/SIZE]

The best I can guess is that it gave up looking for hardware.

I have all sorts of problems getting linux CDs even to boot on my poor computer.  The sad thing is, it's quite new and built by me.
[COLOR="Blue"][DSL]("http://www.damnsmalllinux.org")[/COLOR] does not work, nor [COLOR="Blue"][Knoppix]("http://www.knopper.net/knoppix/index-en.html")[/COLOR].  [COLOR="Blue"][SuSE]("http://en.opensuse.org/Welcome_to_openSUSE.org")[/COLOR] worked grandly until I couldn't perform even the most basic of operations like setting the default gateway.  [COLOR="Blue"][Fedora Core 6]("http://fedoraproject.org/wiki/")[/COLOR] was able to detect my hdds with linux -noprobe, but i have to give it up because i can't get it to recognise any of my other hardware (LAN, default video card, such).  IDK if this is because I used noprobe when installing.

Back to Ubuntu: the terminal works well enough.  I noticed that it found a USB drive when I plugged my camera in (screenshot) although IDK how to mount them.  /dev/disk/by-name/NO_NAME failed to CD.

I'm a Windows power user, and I'm trying so hard to switch, I know Linux is better, but I just can't get anything besides [COLOR="Red"]WinXP[/COLOR] to work on this blasted box.

[COLOR="Blue"][Here]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=681&CategoryID=1&DetailName=Feature&MenuID=44&LanID=9")[/COLOR] is my mobo.  The HDD I intend to install to are on the southbridge SATA (Intel ICH8, driver "ata_piix")
Sorry, I can't get the links to be blue.

So, basically what I'm asking is: 
am I right in assuming this is driver-related, most likely the southbridge? and 
where's the noprobe option go? and 
if I choose noprobe, will Ubuntu not recognise any drivers except the ones I expliciitly tell it to load? If so, how do I find out what driers I need?  Device Manager anyone?

---

### Post by tommcd on 2007-03-27
The p965/ICH8 chipset has been problematic. 
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
I hope the final version of fiesty has support for it. Do a search for "jmicon" and "ICH8". You are not alone.
And welcome to the forums.
Also, you might try zenwalk:
[http://zenwalk.org/](http://zenwalk.org/)
I uses 2.6.2 kernel. Sorry I don't have better advice.

---

### Post by tommcd on 2007-03-27
Also, you might try posting here:
[http://www.phoronix.net/forums/](http://www.phoronix.net/forums/)
Forum admin Michael is very knowledgeable about new hardware and linux, and he answers many threads.

---

### Post by ascendant on 2007-03-27
Thank you very much for your reply.  That core 2 Duo support page looks extremely interesting.  On three forums, this has been the best info I have gotten.  Thanks very much.  

I am also gald to learn I am not alone with the errors i have with my wonderful ICH8 southbridge.  It might even mean someone knows how to deal with it!

---

### Post by ascendant on 2007-03-27
I searched through the phoronix forums and found pretty nothing relating to my problem.  It also has a very annoyingly restrictive search, so it's probabble that I missed something.
I am hesitant to create an account there.

Some extra info:
When it boots from the CD, I have removed the silent and splash options from the line.
It spits a lot of errors about trying to read fd0.  Naturally, the floppy drive is freaking out, and when I put a blank floppy in there, the errors stop, but the system still stops at with the same prompt as first post.

Later, I set up a usb drive and got it working as bootable.
It no longer had errors trying to deal with the floppy but instead ropped to prompt with this output:
```
Done.
check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules is /dev
ALERT! does not exist. Dropping to shell

[and the busybox printout and command prompt from the ram FS)
```

I tried all-generic-ide from the core 2 duo support as well.  
[LIST]
[*]It asks for the driver CD.  
[*]I don't have it, I press enter.  
[*]It reads from the fdd, gives up and tells me to reinsert te install cd.  
[*]It's already in there, I press enter.
[*]it reads from the floppy some more and dies.
[/LIST]

I am thinking I need to set up some links to lead it back to my cdrom (or usb key)  how would I set them up?

in /dev there is /sda and /sda1 (i think they are my zip drive.  the size is right during the boot output) and there is /sdb and /sdb4.  For the same reasons these are my USB drive.
i have tried mount /dev/sd** /dev/* (not with *s but with different names) and mount /dev/* /dev/sd** but IDK the syntax for mount.  Both times it complains that the device does not exist.

Do i need this drivers cd that it speaks of?  I am afraid of using it because it looks like it will cause the system to forget where the installation CD is.

I have noticed that there are plenty of errors with my southbridge due to a bug in the kernel.  There are several posts explaining that the bug has been fixed in latest/beta or w/e builds/updates (I know little about this stuff) Is it possible (on the USB drive) to replace the kernel it loads with one of these?  If so< I'm thinking it is this vmlinuz file.  If anyone has this fixed kernel, can they post the file? My processor is E6600 and I am using the 64-bit Feisty cd.

---

### Post by ascendant on 2007-03-28
So it pretty much looks like I'm getting nowhere with Ubuntu.  I tries your Zen (Live CD though, not the whole OS) and it didn't boot.  It complained about missing LiveData.  Oh well.

I will download 64-bit openSuSE 10.2 and see where I get with that.

openSuSE x86 has been the best working so far.  It recognized pretty much all of my hardware.  I hope it will be the same in the x64 case.

---

### Post by tommcd on 2007-03-29
Glad you got something to work. It is disappointing that Suse 10.2 works and Ubuntu fiesty did not. Perhaps the final version of fiesty will be better? I was really hoping to see solid core 2 duo support in fiesty.

---

### Post by blazerte on 2007-04-18
Same problem here with Feisty Beta 3. 
Debian's Etch (network install) seems to be working well though so far.
Maybe the final release of Feisty will work. Until then it's Debian.

---

### Post by blazerte on 2007-04-28
Got it working on P5B-VM

Necessary to disable the JMicron sata/pata chip in bios. See this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

Since my DVD R/W is SATA and I'm not using RAID, this is OK for me.

---

### Post by ascendant on 2007-04-28
Yeah, I figured that might do the trick, but both my CD burner and DVD burner are ATA.  I have SATA adapters for both, but they're more meant for harddrives.  OpenSUSE does not see my CD drive (currently).  This may be because it tries to access it in DMA mode.
Windows can see it and use it in PIO, but that is a very inefficient mode.  In PIO, I can burn at ~20x and one of the CPU cores (2.7 GHz)  maxes out (non-multithreaded kernel interrupts).

Currently I have one HDD on one of the adapters, DMA works for it.  The DVD drive is on the JMicron, and the CD is on another adapter.  OpenSUSE sees the DVD drive and DMA's it.  I can't find an IDE cable long enough to reach for both.

Does anyone know if Linux supports PIO, and if it's PIO implementation is better than Windows's?

---

### Post by blazerte on 2007-04-29
Yes, the Enhanced IDE driver in 2.6 supports PIO, whether it's better than windows, I know not. 
It can be tuned by kernel command line options. For example from source code Documentation/ide.txt:

"hdx=autotune"         : driver will attempt to tune interface speed
                          to the fastest PIO mode supported,
                          if possible for this drive only.
                          Not fully supported by all chipset types,
                          and quite likely to cause trouble with
                          older/odd IDE drives.

There's other stuff in ide.txt too.

---

