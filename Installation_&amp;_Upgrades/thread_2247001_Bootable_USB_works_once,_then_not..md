---
title: "Bootable USB works once, then not."
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by MrKimi on 2014-10-04
What I want to get to is a bootable USB containing Xubuntu. Should be easy enough, I had exactly this on my previous (32 bit) machine. I've upgraded and I need to install a 64 bit OS on my USB. Here's my proceedure:

1) Installed Xubuntu 14.04.1 on the HD on my 64 bit machine (details below) . This is working prefectly and it is my day to day machine.
2) pulled the HD from the machine, booted off the LiveDVD, plugged in the target USB and installed Xubuntu 14.04.1 on it.
3) booted off the USB, works fine
4) replaced the hard drive and rebooted off the USB, still fine.
5) booted off the HD: fine
6) tried to boot off the USB: it ignored the USB and booted off the HD
7) pulled the HD from the machine and attempted to boot from the USB: no bootable device.

I've been around this twice now. I can get the USB back if I boot off the LiveDVD, install the boot repairer, and use that to fix the USB, which is all very time consuming. And that only puts me back to step 3 anyway. It seems like booting off the HD manages to corrupt the USB drive *even if it isn't plugged in* (which is, of course, nonsense). It boots the LiveDVD no problem when I ask it to. It also reliably boots a LiveDVD copy I made to a USB (actually the same USB, I've since overwritten it). But it won't consistently boot my target OS on that USB.

Is this anything todo with the UEFI (previous machine did not have that). I have secure boot turned off. Both the HD and the USB have a fat32 partition on the front which I think is the boot files. They aren't there on my 32 bit HD and USB (which still boot on my old machine).

Machine details:
Toshiba Satellite P70-A (PSPLPA)
USB is a SanDisk (14.91GB)

---

### Post by oldfred on 2014-10-05
Only 64 bit versions of Ubuntu support UEFI, and will boot in either UEFI or BIOS from UEFI menu. 
The 32 bit version will only boot in BIOS/CSM/Legacy boot mode.

You do not have to make a flash drive both UEFI and BIOS, but show both.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
Howto help USB boot drives - sudodus
A tool that helps boot some computers from [other] USB boot drives - Chainloader
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

Sometimes the renumber of the drive from the install to the working boot causes issues. It should not as UUID do not change. But boot drive in grub is always hd0, but when you install to a flash drive it may be hd1 or hd2 etc. I sometimes have had to go into grub menu and manually change to hd0 when directly booting a full install on a flash drive the first time. Then run sudo update-grub to fix it permanently.

---

### Post by sudodus on 2014-10-05
1. I have found that sometimes an installed system in a USB HDD is not shut down properly (even when done via the shutdown button), and the file system is corrupted. After repair with

```
sudo e2fsck -f /dev/sdx
```

it has worked again except in one case. It seems to help to flush the buffers to disk before shutdown.

```
sync
```

But this should happen automatically. I've had this problem happen with more than one distro. I don't know if the drive is failing physically, there is no definite signs of that.The S.M.A.R.T. information indicates a good disk (tested with smartctl). Maybe the USB system is shutting down before the buffers are flushed (that would be a bad bug).

2. My flash drive to boot in UEFI or BIOS has been rather reliable, but I have tried to make it up to date using update/dist-upgrade. After that it did not work. I think something happened to the UEFI system, and I must admit, that I do not understand the UEFI system.

*. Maybe the safest way to have a portable system, that works with UEFI, is a persistent live system (based on an Ubuntu family desktop iso file).

Anyway, I will read the posts in this thread will great interest. Good luck :-)

---

### Post by MrKimi on 2014-10-28
Sorry for taking so long to get back. I thought I had posted an update but I see it isn't here so I must have done something silly. I hope I do better this time.
But I have been working on this one, and at least refining the question better.
Before I describe what I've been doing, thanks for the replies. My initial query was horribly vague and I appreciate the time you took to answer.

Since then I have isolated the following:
a) my hard drive in the machine. Always works when I'm in UEFI boot mode, never works in CSM, but that's no problem.
b)  an old USB drive with Ubuntu installed (14.04 IIRC, I can't look at it  while I'm typing...) and that boots in CSM mode. Interestingly that's 32  bits. I didn't think that would work at all on a 64 bit machine so I  didn't try it until now. Also worth noting, when the machine comes up  with boot options (hard drive, optical, LAN, USB...) it fills in the  type of USB drive (Sandisk) if it is in CSM, like it recognises it.  Otherwise it leaves that blank. The other options (HDD, LAN, optical)  also have their types filled in.
c) a newer USB drive  with Ubuntu 14.04 installed 64bit. Doesn't boot in either CSM or UEFI  but in CSM it tells me 'no operating system' which suggests it at least  tried. I'm not sure of the state of that USB so it might be right
d)  (yep still going...) an external HDD which plugs into a USB port. Now,  this has a copy of Lubuntu 14.04 on it. I can open up my machine and  pull the usual HDD out and replace it with this and and it boots no  problem. When I try and boot with it as external in UEFI mode it doesn't  give me a type and doesn't boot. In CSM mode it gives me a type and  when I try and boot it waits there with its cursor flashing for ages  until I give up. I'm quite sure it wasn't doing anything useful in that  time.

So I think switching to CSM to  boot one USB does work for (b), but not the (c), or not yet. I have to  check if it boots when my hard drive is removed 'cos that was the only  way I got it to boot earlier.
Then there's the external drive (d) which I know is valid, but doesn't boot in either mode.

In fact I can live with (c) not booting now that I have (b) working. What I would really like to get working is (d) which is a known valid UEFI system ('cos it boots when it is installed internally). It looks like my machine doesn't like UEFI over USB, but will boot CSM systems. So I need to find a way to make that drive boot with either I think (or just CSM would be fine)

In light of that I think I'm safe in assuming that I don't have the shut down problem (or not yet anyway) but the info in [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) looks promising. I don't have either of the non-functioning drives with me right now but I'll be trying that tonight.

---

### Post by sudodus on 2014-10-29
> **MrKimi said:**
> Sorry for taking so long to get back. I thought I had posted an update but I see it isn't here so I must have done something silly. I hope I do better this time.
But I have been working on this one, and at least refining the question better.
Before I describe what I've been doing, thanks for the replies. My initial query was horribly vague and I appreciate the time you took to answer.

Since then I have isolated the following:
a) my hard drive in the machine. Always works when I'm in UEFI boot mode, never works in CSM, but that's no problem.

:-)
> 
b)  an old USB drive with Ubuntu installed (14.04 IIRC, I can't look at it  while I'm typing...) and that boots in CSM mode. Interestingly that's 32  bits. I didn't think that would work at all on a 64 bit machine so I  didn't try it until now. Also worth noting, when the machine comes up  with boot options (hard drive, optical, LAN, USB...) it fills in the  type of USB drive (Sandisk) if it is in CSM, like it recognises it.  Otherwise it leaves that blank. The other options (HDD, LAN, optical)  also have their types filled in.

32-bit systems do not work in UEFI mode, but otherwise (in BIOS alias CSM mode) 32-bit systems work in 64-bit computers. It seems your system does not 'want to' boot from USB in UEFI mode. Can you unset secure boot?
> 
c) a newer USB drive  with Ubuntu 14.04 installed 64bit. Doesn't boot in either CSM or UEFI  but in CSM it tells me 'no operating system' which suggests it at least  tried. I'm not sure of the state of that USB so it might be right

Some pendrives are no good booters. Other pendrives cooperate with some, but not all motherboards. My experience is that Sandisk and Transcend are good booters. See this link for more details:
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
> 
d)  (yep still going...) an external HDD which plugs into a USB port. Now,  this has a copy of Lubuntu 14.04 on it. I can open up my machine and  pull the usual HDD out and replace it with this and and it boots no  problem. When I try and boot with it as external in UEFI mode it doesn't  give me a type and doesn't boot. In CSM mode it gives me a type and  when I try and boot it waits there with its cursor flashing for ages  until I give up. I'm quite sure it wasn't doing anything useful in that  time.

Maybe the problem is that the computer won't let you boot from USB in UEFI mode, and since the Lubuntu system is installed in UEFI mode, it won't boot in CSM mode.
> 
So I think switching to CSM to  boot one USB does work for (b), but not the (c), or not yet. I have to  check if it boots when my hard drive is removed 'cos that was the only  way I got it to boot earlier.
Then there's the external drive (d) which I know is valid, but doesn't boot in either mode.

In fact I can live with (c) not booting now that I have (b) working. What I would really like to get working is (d) which is a known valid UEFI system ('cos it boots when it is installed internally). It looks like my machine doesn't like UEFI over USB, but will boot CSM systems. So I need to find a way to make that drive boot with either I think (or just CSM would be fine)

In light of that I think I'm safe in assuming that I don't have the shut down problem (or not yet anyway) but the info in [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) looks promising. I don't have either of the non-functioning drives with me right now but I'll be trying that tonight.

You could try to reinstall Lubuntu into the USB HDD (d), this time

1. Set the computer in CSM mode

2. Run the installer. It should work with both of Lubuntu 14.04.1 LTS ***64-bit and 32-bit*** desktop systems.

---

### Post by MrKimi on 2015-01-01
Well I finally got back to this. Obviously it hasn't been keeping me  awake but it was still on my nag list and I finally got back to taking a  look again.
First thanks for the reply and sorry (again) for not getting back sooner.
I think you nailed it with:
* Maybe the problem is that the computer won't let you boot from USB in  UEFI mode, and since the Lubuntu system is installed in UEFI mode, it  won't boot in CSM mode.*

So what I have done is just run boot repair on the USB I had installed with Xubuntu but did not boot (c). This fixed up the grub loader. I think I did this earlier actually but this time I installed grub on both partitions whereas I only did one last time and that was the UEFI partition. So, with that done, I switched to CMS and booted from the USB drive successfully. The extra step of switching to/from CMS is not a problem 'cos I'm rebooting anyway.

As for the (d) drive not working that turns out to be less important than I thought. The (d) drive is what I use as my emergency clone disk if my main disk goes bad. As long as I can copy to it from time to time to refresh the clone it doesn't need to boot off the USB interface, it only needs to boot when I put it inside the machine, and it does. So all is well.

Thanks for the help
Roger

---

### Post by sudodus on 2015-01-02
Congratulations, and thanks for sharing your results :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

