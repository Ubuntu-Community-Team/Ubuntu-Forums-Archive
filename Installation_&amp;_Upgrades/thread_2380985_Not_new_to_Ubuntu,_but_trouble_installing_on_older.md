---
title: "Not new to Ubuntu, but trouble installing on older hardware"
date: 2017-12-24
forum: Installation &amp; Upgrades
---

### Post by carnivorousdonut on 2017-12-24
Ok, It's ancient hardware, gimme a break.
I use Ubuntu on a semi-regular basis for my neural network, so I'm somewhat familiar with how things work. Having said that, here is the issue, in great detail:
I was given a very old server, A Compaq ML530 G1.
Lengthy detailed specs are here: [https://www.harddrivesdirect.com/quickspecs_proliant_ML530.php](https://www.harddrivesdirect.com/quickspecs_proliant_ML530.php)

Initially, I had the devil's own time dealing with the Cirrus Logic add-in PCI card, but dumped it in for the built-in ATI Rage IIc, which is at least supported from an 32bit ubuntu-based distro.
So far, so good. I can boot to any live DVD, but cannot install, because it doesn't see the drives.
Yes, they are SCSI, using an HP card, which is built in. I have the Compaq SmartStart CD, if need be (system is config'd for RAID 10) but without a driver for the SCSI card, I'm dead in the water.
Suggestions? I'm certainly open to them.

---

### Post by mörgæs on 2017-12-25
Hi, welcome to the fora.

Could it be a problem with [Fake-RAID]("http://skrypuch.com/raid/")?

---

### Post by Autodave on 2017-12-25
Not that it has anything to do with the RAID issue, but what version are you trying to install?

---

### Post by carnivorousdonut on 2017-12-25
It's real hardware RAID, this was an old server, and I'm currently (attempting) to install Lubuntu which is based on 17.10 IIRC.
I'm open to suggestions, I run 16.04 LTS on my RNN rig.

---

### Post by sudodus on 2017-12-25
Can you boot that computer from a USB drive? In that case you can use either a persistent live system or an installed system (installed into a USB drive) and maybe it will be easier to find a driver that can manage the SCSI drive(s), when the system is running.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If you cannot boot from USB, maybe you can use a Plop CD to boot and chainload to USB.

[help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

---

### Post by carnivorousdonut on 2017-12-25
The system predates USB. Hence why I put the exhausting detail link in my original thread.
I can boot from a live DVD just fine, and use the system just fine from the DVD. What I wish to do, is install the OS onto the hard drive, which is in a RAID configuration.
No Debian-based Distro that I have tried, sees the RAID card.
If you could point me to the driver (if it exists) and how to install it, that'd be great.
I am somewhat surprised, that if a driver exists, that it was pulled from the Distro, or never included in the 1st place. Native drivers have been around (i.e. built in to the OS) for Win2k on up, and given the age of the server, I would think *nix would have no issue with this, but perhaps I am wrong...

---

### Post by mörgæs on 2017-12-26
Some old posts show that people have successfully installed an old server image. 

[https://ubuntuforums.org/showthread.php?t=1000486](https://ubuntuforums.org/showthread.php?t=1000486)
[https://blog.jigsawpieces.me/2006/06/03/ubuntu-on-proliant-ml530/](https://blog.jigsawpieces.me/2006/06/03/ubuntu-on-proliant-ml530/)

Old software should of course not be used for production but it's interesting to see if it behaves differently. 

Have you tried that?

---

### Post by carnivorousdonut on 2017-12-26
I have not, but I'm going to try it shortly, and let you know how it goes. Thank you for finding those links

---

### Post by carnivorousdonut on 2017-12-26
Two steps forward, 8 back.9.04 LTS Server installs fine, but I can't do any updates or install any packages (through the command line, no GUI installed by default) because it's too old apparently (lots of 404 messages when I try sudo apt-get updates)
But it did see my drive, so there was that.
So I had the brilliant idea of going up to 14.04 LTS Server....
...except they yanked the driver out, so it doesn't see my RAID controller (how dumb is that to pull out drivers?)
So back into 9.04 and the lshw - short gives me this as far as RAID/SCSI hardware:

storage - Smart-2/P RAID Controller (which, I suspect, is where the drives are attached)
storage - 53C896/897
storage - 53C896/897

So, is it possible to extract the driver from the 9.04 .ISO, and when installing the 14.04 version, point it to a floppy or something (I have a PCI USB card on the way) to load the old driver, so it sees my RAID controller?

---

### Post by mörgæs on 2017-12-28
> **carnivorousdonut said:**
> 
...except they yanked the driver out, so it doesn't see my RAID controller 

Links, please.


9.04 was not LTS and I don't know if it's possible to move a driver to another release. 

As a long shot and without any guarantee I suggest that you do the following:

From the 9.04 install change sources.list to point to 14.04 using the commmand

```
sudo sed -i s/jaunty/trusty/ /etc/apt/sources.list

```
After that ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade

```
Might work, might wreck the operative system.

---

### Post by carnivorousdonut on 2017-12-28
It sort of worked, but threw me into dependency hell, but it gave me an idea, so I'm starting fresh, sans the compaq RAID card, and going with a spare adaptec 29160 I have, which ubuntu has no issue with.
Thank you for all your help.

---

### Post by mörgæs on 2017-12-28
You're welcome.
If you consider the problem solved please mark the thread so.

---

