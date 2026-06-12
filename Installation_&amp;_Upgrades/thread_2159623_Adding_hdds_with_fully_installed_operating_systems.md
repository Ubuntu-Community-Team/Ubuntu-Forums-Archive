---
title: "Adding hdds with fully installed operating systems to GRUB"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by pikeminnow on 2013-07-03
Hi. I've been using linux since about 2010, but up until now I've sort of been able to ignore GRUB problems by reinstalling the OS and keeping /home and therefore all my files. This means I am a grub nub and cannot solve my problem now.

I was recently approached with a summer job offer to learn how to install and use Apache Hadoop for this guy, and doing that required me to switch from Fedora 18 (I've been using Fedora for the entire time until now) to Ubuntu. My first couple times installing Ubuntu.... didn't go very well. I have Precise working beautifully now, but, and here is the problem, I have a hdd with Windows 7 and a hdd with Fedora 18.** I want to know how I can plug them in and make the Ubuntu GRUB recognize them and provide them as options to boot into**. 

The Windows bootloader has always been a little skeezy. I broke it the first time I tried installing linux (pretty close to day of unboxing the machine), but it was fine because Fedora came with its own bootloader. However, when I was trying to install Ubuntu off a flash drive, the Fedora bootloader broke and the new Ubuntu one failed to install. It's part of a long history of having trouble generating new bootloaders. I can only get it to reliably work off an optical disk. In any case, I've spent a couple days googling but I'm not really sure how to articulate the problem to the search engine- I'm certain there is a way of doing this without reinstalling Ubuntu. I can even replace GRUB if necessary- if I'm told how to do it. 

TL/DR: **GRUB nub wants to know how to add new (old) disks with preinstalled OSs to GRUB by any means but reinstalling Ubuntu and keeping the new (old) disks' file data intact.**

Relevant info:

3 SATA HDDs
64 bit Ubuntu Precise Pangolin
64 bit Fedora 18 Spherical Cow
64 bit Windows 7 Ultimate
BIOS, not UEFI

I have an entire CD wallet of various livecds. One of them is GParted. I also have the LiveCD I installed Precise from.

---

### Post by arpanaut on 2013-07-03
Seems to me the easiest way would be... 
If Ubuntu will boot properly, just set that HDD in the bios as the first in the boot order.
boot into Ubuntu with the other disks connected to the machine,
Once logged into Ubuntu open a terminal and run:
```
sudo update-grub
```
enter your password and this process should detect the other OS and upon rebooting 
they will be offered in the grub menu that appears after post.

p.s. if windows was not initially installed on that particular machine you will probably encounter issues booting windows.
due to licensing matters. 

Hope that gets you rolling.

---

### Post by pikeminnow on 2013-07-03
> **arpanaut said:**
> Seems to me the easiest way would be... 
If Ubuntu will boot properly, just set that HDD in the bios as the first in the boot order.
boot into Ubuntu with the other disks connected to the machine,
Once logged into Ubuntu open a terminal and run:
```
sudo update-grub
```
enter your password and this process should detect the other OS and upon rebooting 
they will be offered in the grub menu that appears after post.

p.s. if windows was not initially installed on that particular machine you will probably encounter issues booting windows.
due to licensing matters. 

Hope that gets you rolling.

Yeah! This pretty much works. I see an option for Windows 7 now- both of these drives were in the machine prior to Ubuntu and the licensing has been sorted out since 2011, which is a big reason to not wreck it. I don't want to have to call Microsoft over it. It doesn't seem to have detected the Fedora, though, which is a bit of a shame since I had some files still left on it that I wanted to move to my external hard drive before the F19 Shrodingers Cat release. Is there a way to figure that bit out? I think it sort of recognized it, there was a whole bunch of "detected linux" going on, which looked about right because this was an "especially old" Fedora install by my standards, it's from about a week after Spherical Cow landed so there were a lot of old kernel stuff left on the GRUB screen.

The GRUB screen I have had Ubuntu, another Ubuntu, another entry which I believe said something along the lines of "older linux", a couple of memtests and the Windows 7.

---

### Post by arpanaut on 2013-07-03
Don't know didly about Fedora... sorry
You should be able to access your files on that drive from Ubuntu file manager.

---

### Post by pikeminnow on 2013-07-04
> **arpanaut said:**
> Don't know didly about Fedora... sorry
You should be able to access your files on that drive from Ubuntu file manager.

Yeah, maybe. It doesn't seem like that drive is even mounting though, which is a separate matter. Seeing as the original question has been answered, though, I'm going to mark this as "solved" and go figure out how to mount an encrypted drive.

---

