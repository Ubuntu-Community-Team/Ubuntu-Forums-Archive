---
title: "Probs after upgrading from Karmic to Lucid"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by typos1 on 2010-08-13
Rather than wait for me to back up her home folder and come and upgrade for her, my mum recently upgraded from Karmic to Lucid herself. Not sure what she did, but shes having real problems. She said she was asked if she wanted to keep her current settings at some point and she said yes. Now when her pc boots the screen is mainly black and white,  the processor is at full load, Thunderbird wont work anymore and after 5-10 minutes the screen goes black and the system crashes. Shes got a Pentium 4 about 1.9 Ghz with 2 Gig of RAM. I ve read that Lucid uses an open source drivers for nVidia support, could this be the problem? Shes tried tried pressing F8 or F10 but it doesnt go into the boot menu, just lists a line of about 5 numbers most of them 3s (was going to try to get her to boot from Karmic if it was still in the boot menu, or in safe mode). Any ideas anyone? Thanks

---

### Post by mörgæs on 2010-08-13
First of all: Have you booted with a live CD and rescued the files in /home?

---

### Post by typos1 on 2010-08-13
No need, no files appear to be lost, I just always back up everything first just in case and she didnt. It just dosent work properly anymore, I m going to have a look at it myself tomorrow, just wanted to see if anyone had any ideas. I get occasional bugs on my AMD 64 bit install, but her Intel 32bit install has always been problem free. I asked her to go into system monitor and see what was running, but other than system monitor, nothing else was.

---

### Post by davidmohammed on 2010-08-13
have you tried nomodeset in your grub boot string?

---

### Post by typos1 on 2010-08-13
Um, no. Heard of Grub and a string but cant remember what they are though. How would I do it?

---

### Post by davidmohammed on 2010-08-13
when you boot, press shift and it will display the list of kernels - this is your grub.

press e and then look for the line ending

... quiet splash --

change this to look something like

... nomodeset quiet splash --

CTRL + X to boot

---

### Post by typos1 on 2010-08-13
Ah, thats why I was telling her to try F8 or 10 to get a list of kernels. I ll try that, thanks.

---

### Post by typos1 on 2010-08-13
When she presses shift the screen goes blank-black screen, nothing on it, preocessor makes noise but blank screen.

---

### Post by davidmohammed on 2010-08-13
pressing shift works for grub2 - if the PC is still using grub-legacy then I think you have to either press Escape or space-bar (cant remember which one).

---

### Post by typos1 on 2010-08-17
After its booted the processor is running at 90-100%, but in system monitor/processes, there isnt anything running other than system monitor-no signs of anything hanging, sometimes its might be on for 20 mins then crash, other times it ll be on for 2 or 5 mins then crash. 

Well, I say crash-the screen either goes black, or half goes black and half black with white flashes, or the screen might be yellow when you login or maybe black and white-but the actual pc is running, you just cant do anything with it. 

Something is not right, but if its not in  processes, I cant figure out what it is.

---

### Post by mörgæs on 2010-08-17
If the machine is stable enough to run a command, please post the output of 
```
hwinfo --gfx
```

---

### Post by typos1 on 2010-08-18
It wasnt installed-I installed it and got:-

10: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2562
  Unique ID: _Znp.lKS3NVuOgDF
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel i845"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2562 "i845"
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x2562 
  Revision: 0x03
  Memory Range: 0xd0000000-0xd7ffffff (rw,prefetchable)
  Memory Range: 0xdff80000-0xdfffffff (rw,non-prefetchable)
  IRQ: 16 (167427 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002562sv00001849sd00002562bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #10


The computer has become very slow with Lucid-and it cant do much without crashing. Give it a couple of Firefox windows to run and then open emails and processor goes full tilt, the fan starts whirring away then it crashes. Karmic could do a lot more stuff, without even getting to 50% processor usage.

---

### Post by mörgæs on 2010-08-18
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

If you can not get it to work, the best advice is going to 9.10. This will give you a supported system until april 2011, at which time you can give 10.10 and 11.04 a try.

---

### Post by typos1 on 2010-08-18
Ok, trying some of those fixes, but I cant get into the menu to be able to pick recovery mode-wahtever I do it always boots right into Lucid's login screen.

---

### Post by mörgæs on 2010-08-18
> **typos1 said:**
> Ok, trying some of those fixes, but I cant get into the menu to be able to pick recovery mode-wahtever I do it always boots right into Lucid's login screen.

Try pushing left-shift while booting.

---

### Post by typos1 on 2010-08-21
She installed some updates today from update manager and now it boots to just a blank screen, thats stumped me-doesnt respond to anything.

---

### Post by mörgæs on 2010-08-22
It seems like the machine is so messed up that a clean install of 9.10 is the safest approach.

---

### Post by typos1 on 2010-08-22
Thats what I feared, think the updates might have done something-I didnt think about it, had it been my machine I would have checked what they were before I installed them. Hopefully I ll be able to recover her home folder.

---

### Post by typos1 on 2010-08-23
I ve used a live cd but when I go into the file system it wont let me copy the files and it wont let me change permissions-how can I change peromissions so I can copy the files?

---

### Post by mörgæs on 2010-08-23
Have you tried **sudo chmod...**?

---

### Post by typos1 on 2010-08-23
No, not heard of "mod", take it it stands for modify and it ll let me change the permissions?

Actually is there a list somewhere of all the commands?

---

### Post by davidmohammed on 2010-08-23
try from a terminal session


gksu nautilus

it will launch nautilus but as root.  you should then be able to copy files to where-ever you need to.

---

### Post by typos1 on 2010-08-23
Ok will do, thanks, what does sudo chmod do then? 

Was gonna do that in a terminal too.

---

### Post by mörgæs on 2010-08-24
It is all explained here:
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Though it is a few years old it is a great guide.

---

### Post by typos1 on 2010-08-24
Cool, thanks.

---

### Post by typos1 on 2010-08-24
I ve gone back to Karmic and I managed to save her home folder, but know the syste is only showing 994.5 mb of RAM and not the 1.9 Gb she had before! Any idea where it could have gone!!??

---

### Post by mörgæs on 2010-08-24
Please post the output of 

```
free -m
```

---

### Post by typos1 on 2010-08-26
anna@anna-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           994        616        377          0         18        412
-/+ buffers/cache:        185        809
Swap:         2910          4       2905
anna@anna-desktop:~$ 


Heres the output. Seems to say its got 994mb, but at the beginning of this thread I posted her spec and it was 2Gb, not quite sure how 1Gb could disappear as a result of some software probs.

---

### Post by mörgæs on 2010-08-26
> **typos1 said:**
> 

```
             total       used       free     shared    buffers     cached
Mem:           994        616        377          0         18        412
-/+ buffers/cache:        185        809
Swap:         2910          4       2905

```


[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

CODE-tags makes the output easier to read.

Are you sure about the 2 GB?

---

### Post by typos1 on 2010-08-26
Ah, I see thanks.

Maybe I made a mistake-I m not perfect, but I remember checking in system monitor/system and thinking that she had the same amount of RAM as me. 

I spose the only way to find out for sure is to take the cover off and see.

---

### Post by typos1 on 2010-08-31
Now got probs with the new install of Karmic-wont boot, just get one kernel option (which it WONT boot from) and a few mem test options at boot up. 

Mem test takes 2 hours and reports no probs. 

But wont boot at all to Karmic now. 

Lucid seems to have messed it up totally even ith the drive reformatted and Karmic re installed, which I thought was impossible-cant see how software can break hardware.

---

### Post by mörgæs on 2010-08-31
Did you have wired internet access while installing 9.10, and did you choose 'use entire hard disk for Ubuntu' (or something similar) in the process?

You don't have to reformat manually. It happens automatically during the installation.

---

### Post by typos1 on 2010-08-31
Did have wired internet access, whilst re-installing, but did also when I first installed it in December and never had any probs til upgrade to Lucid. 

I know it reformats automatically, I was just saying that despite reformatting and re-installing Karmic, Lucid seems to have broken the hardware. 

I reformatted the entire disc-didnt want any trace of Lucid left after the probs!

---

### Post by mörgæs on 2010-09-01
Then I am out of ideas, sorry. I don't think that you should be concerned with broken hardware, though.

---

### Post by typos1 on 2010-09-01
Ok, thanks, I just cant understand why a complete new install would suddenly go wrong.

---

### Post by typos1 on 2010-09-01
Its all very strange-I went down there today and it lists 3 Linux kernels, 2 recovery modes and 2 mem tests when you turn it on.

The mem tests take 2 hours with an ok result and the words "on" displaying on the screen, but nothing else and no boot.

The kernels end up with a blank screen and the recovery modes go into a shell. It list various devices and drivers being present and ok, a long number (which I assumed was the hard drive) as "not found". Simply wont boot properly. 

So I tried the live cd and when it boots from that the hard drive doesnt show under places, but it did last week when I rescued all the files and re-installed Karmic.

So I went to re-install Karmic again and the partitioner listed, and this is VERY strange, about 2gb of swap space, 78gb of ext4 formatted hard drive but NO OS at all. 

Basically, after 4 days the entire Karmic install just vanished, how the hell could that happen??!!

---

### Post by mörgæs on 2010-09-04
If the system shows more than one kernel right after a clean installation, something went wrong in the process. 

Have you tried installing 9.10 using the alternate installer?

---

### Post by typos1 on 2010-09-04
It was 4 days after installation from the live cd which came out in October 2009, so I d expect to see several kernels (mine has about 20 listed on start up!) so update manager had showed loads of updates to install, including any updated kernels.

Its a bit strange that it ran fine for 4 days and then the install literally disappeared!

---

