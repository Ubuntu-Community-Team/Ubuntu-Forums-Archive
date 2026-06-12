---
title: "HP desktop won't run Ubuntu 10.04"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by jcolyn on 2010-08-05
I have a HP model a6019h desktop with 2GB ram 320GB drive and dual core 3.20GHZ. I downloaded the live CD and booted on it. It ran for maybe a minute then the computer froze up and would not respond. I had to restart the computer by pressing the on/off button. I then installed and had the same problems. Never could get to the error logs to see if I could determine the problem.

I then installed Kubuntu 10.04 and it runs fine with no problems whatsoever.

My Dell Inspiron 600m runs Ubuntu fine.

Anybody have any ideas what the problem might be?

---

### Post by tommcd on 2010-08-06
> **jcolyn said:**
> 
I then installed Kubuntu 10.04 and it runs fine with no problems whatsoever.
Anybody have any ideas what the problem might be?
There is no valid reason why Kubuntu would work where Ubuntu did not.
When you booted the *buntu CDs, did you run the option: *Check CD for defects*??????
This is most important. It will verify that the CD you are trying to use to install *buntu is good.

---

### Post by jcolyn on 2010-08-06
> **tommcd said:**
> There is no valid reason why Kubuntu would work where Ubuntu did not.
When you booted the *buntu CDs, did you run the option: *Check CD for defects*??????
This is most important. It will verify that the CD you are trying to use to install *buntu is good.

Yes I did check the CD. In fact I downloaded a new ISO, burned it to disk and tried it too with the same results.

HP support seems to think it could be my old bios version(5.04 new one is 5.12)  so I borrowed a drive from work today and an installing windows on it since the bios update for this computer has to be run from within windows. Once updated I'm going to give it another try..

I'll be up till midnight since the Vista install takes 2 hours.

---

### Post by jcolyn on 2010-08-07
The bios update failed to fix the problem. It still freezes up completely When running Ubuntu live CD. I can install Ubuntu but it freezes up once installed so I am back to Kubuntu on the machine.

I'm now back to thinking the problem could be an issue between the graphics card and Gnome since the only difference is the desktop installed. Gnome v KDE..

Ant suggestions??

---

### Post by tommcd on 2010-08-07
What graphics card does the computer have?
You could try installing Ubuntu from the alternate CD. This is a text based install CD that should bypass any graphics related problems.
If you really want the Gnome desktop, you could just install the **ubuntu-desktop** packages onto your Kubuntu system. This should give you the choice to run Gnome or KDE when booting the computer. 
(Note: This will add a lot of extra stuff to your system since it includes the whole Ubuntu Gnome desktop).
If you later want to remove Gnome and get back to a pure KDE, just follow this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
If you decide you like Gnome and want to get rid of KDE, follow this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
If it were me though, if Kubuntu was running ok I would probably just as well stick with that. It is your choice.

---

### Post by jcolyn on 2010-08-07
> **tommcd said:**
> What graphics card does the computer have?
You could try installing Ubuntu from the alternate CD. This is a text based install CD that should bypass any graphics related problems.
If you really want the Gnome desktop, you could just install the **ubuntu-desktop** packages onto your Kubuntu system. This should give you the choice to run Gnome or KDE when booting the computer. 
(Note: This will add a lot of extra stuff to your system since it includes the whole Ubuntu Gnome desktop).
If you later want to remove Gnome and get back to a pure KDE, just follow this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
If you decide you like Gnome and want to get rid of KDE, follow this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
If it were me though, if Kubuntu was running ok I would probably just as well stick with that. It is your choice.

This is what I come up with by running the 2 commands.

I may try disabling the onboard graphics card and installing a new one to see what happens.

I did try the alternate CD..

colyn@Kubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
colyn@Kubuntu:~$ sudo lshw -C video
[sudo] password for colyn: 
  *-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fe980000-fe9fffff ioport:cc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe940000-fe97ffff
colyn@Kubuntu:~$

---

### Post by jcolyn on 2010-08-08
After much work I have determined my problem is not the graphics card afterall.

I had to jumper the hard drive to drop SATA speed from 3Gb/s to 1.5Gb/s

After doing this I ran Ubuntu live CD for over 2 hours without a single issue. I now have it installed and updated and working like it should..

---

### Post by tommcd on 2010-08-08
> **jcolyn said:**
> 
colyn@Kubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

The intel 8xx series graphics cards have been known to be problematic on Ubuntu Lucid:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
This is due to the Kernel Mode Setting (KMS) feature in the newer linux kernels. There have been some "growing pains" during the transition to KMS, particularly with intel cards.
Several possible workarounds are listed there.
If you want to try installing a new graphics card I would recommend a cheap nvidia card if you can. Then just install the nvidia driver.
> **jcolyn said:**
> 
I had to jumper the hard drive to drop SATA speed from 3Gb/s to 1.5Gb/s
It seems unusual that this would fix your problem. Your hard drive settings should not affect running the live CD, since the live CD loads off the CD into RAM. You can even remove your hard drive(s) and the live CD should run ok. I suppose this could affect *installing* Ubuntu though if the live CD had trouble seeing the hard drives.
Perhaps check the sata settings in the BIOS? There may be new options there since you upgraded the BIOS.
Again, if it were me and everything was running ok, I would probably just leave it alone. 
Glad you got this sorted out.

---

### Post by jcolyn on 2010-08-08
> **tommcd said:**
> The intel 8xx series graphics cards have been known to be problematic on Ubuntu Lucid:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
This is due to the Kernel Mode Setting (KMS) feature in the newer linux kernels. There have been some "growing pains" during the transition to KMS, particularly with intel cards.
Several possible workarounds are listed there.
If you want to try installing a new graphics card I would recommend a cheap nvidia card if you can. Then just install the nvidia driver.

The above site is what first made me wonder if that was the problem so I tried the fixes which did not work.

I wonder if there will be a fix in the next release of Ubuntu?

> **tommcd said:**
> It seems unusual that this would fix your problem. Your hard drive settings should not affect running the live CD, since the live CD loads off the CD into RAM. You can even remove your hard drive(s) and the live CD should run ok. I suppose this could affect *installing* Ubuntu though if the live CD had trouble seeing the hard drives.
Perhaps check the sata settings in the BIOS? There may be new options there since you upgraded the BIOS.
Again, if it were me and everything was running ok, I would probably just leave it alone. 
Glad you got this sorted out.

I was talking to a local computer tech who told me some will work if SATA speed is set to 1.5Gb/s instead of 3Gb/s so I gave it a try. The computer has been running non-stop since around 11:00pm last night without a single freeze up so I'll keep it this way till the next release of Ubuntu.

Since the computer was running fine with Kubuntu 10.04 at 3Gb/s SATA speed does this mean the issue as in the above url is a Gnome related issue?

Thanks

---

### Post by tommcd on 2010-08-10
> **jcolyn said:**
> 
I was talking to a local computer tech who told me some will work if SATA speed is set to 1.5Gb/s instead of 3Gb/s so I gave it a try. 
I can understand how that might affect running K/Ubuntu off the hard drive. The hard drive settings should not matter when just running the live CD though.
> **jcolyn said:**
> 
Since the computer was running fine with Kubuntu 10.04 at 3Gb/s SATA speed does this mean the issue as in the above url is a Gnome related issue?

What url are you talking about? If you mean this: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) That is caused by the drivers that ship with the Ubuntu kernel. Both Ubuntu and Kubuntu use the same kernel, so intel graphics performance should be the same in each. So should the ability to run on SATA 1.5 and SATA 3.0 for that matter. 
Unless there are some patches or configuration specific specific to Kubuntu that affects this some how. I really don't know.

---

