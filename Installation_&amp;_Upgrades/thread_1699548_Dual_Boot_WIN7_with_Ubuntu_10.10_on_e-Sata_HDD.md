---
title: "Dual Boot WIN7 with Ubuntu 10.10 on e-Sata HDD"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by darkstarsinner on 2011-03-03
I have searched a few pages of threads but none of them actually show how to get this going.

I tried Ubuntu once and had some issues so I uninstalled and went back to W7. But I can't just let it go. I want to work with Ubuntu to try and learn it. while keeping W7 on my system. When I tried to install Ubuntu on an external HDD it screwed everything up and wouldn't even boot windows. So I need your help. Here's my set up:


50GB SSD for W7
320GB e-SATA connected HDD for Ubuntu
4x 500GB HDD's for programs (would consider dedicating at least one to Ubuntu if I can get it running)



Because the system got screwed up I am doing a fresh install all the way through. So my question is how can I install Ubuntu onto the e-SATA HDD with W7 on the SSD and be bale to use GRUB2? Any help would be greatly appreciated!!! 

P.S. Sorry if I'm talking in circles. I'm tired and on Vicoden from getting my tooth pulled.

---

### Post by wilee-nilee on 2011-03-03
If you haven't reinstalled windows it just may need the mbr reloaded.

When dual booting in the manner you want you would use the custom install and make sure grub is pointed at the externals mbr. Or just reload the mbr's

---

### Post by darkstarsinner on 2011-03-03
Well all drives are bare now. I'm using DBAN to clear the 500GB HDD's because I could not get the RAID partitions to clear after I took it down.

I tried the custom install but pointed the loader to the same drive as the Win7 loader thinking that is what it wanted, but apparently that wasn't right. Can anybody walk me through this?

---

### Post by wilee-nilee on 2011-03-03
> **darkstarsinner said:**
> Well all drives are bare now. I'm using DBAN to clear the 500GB HDD's because I could not get the RAID partitions to clear after I took it down.

I tried the custom install but pointed the loader to the same drive as the Win7 loader thinking that is what it wanted, but apparently that wasn't right. Can anybody walk me through this?

Your there already if you used the custom install and recognize the grub dropdown, point it at the HD your installing Ubuntu to. Run fdisk -l when you boot the install disc and confirm the hd sda or sdb...etc, no numbers that would be a actual partition, and not the mbr.

---

### Post by sahilsameerac on 2011-03-03
go to a ubuntu live cd(just boot to a ubuntu cd)
in terminal paste the cmmand
sudo apt-get update grub

---

### Post by darkstarsinner on 2011-03-03
This is gonna be a long bumpy road. Lol I have to re-read everything you guys type to make sure I read it right. What is Sudo?

---

### Post by wilee-nilee on 2011-03-03
> **darkstarsinner said:**
> This is gonna be a long bumpy road. Lol I have to re-read everything you guys type to make sure I read it right. What is Sudo?

First ignore post 5 it is garbage. sudo is what gives you root permission or inMS words; admin permission.

---

### Post by darkstarsinner on 2011-03-03
> **wilee-nilee said:**
> Your there already if you used the custom install and recognize the grub dropdown, point it at the HD your installing Ubuntu to. Run fdisk -l when you boot the install disc and confirm the hd sda or sdb...etc, no numbers that would be a actual partition, and not the mbr.

Okay so using this method what is sda and sdb? And how do you run fdisk -1? I'm sorry for the noob questions, I'm just tired of trying to figure this out on my own.

---

### Post by wilee-nilee on 2011-03-03
> **darkstarsinner said:**
> Okay so using this method what is sda and sdb? And how do you run fdisk -1? I'm sorry for the noob questions, I'm just tired of trying to figure this out on my own.

So a hard drive is identified by 3 letters sda would be one, sdb would be another, sdc, another. If you add a number that is a partition for example sda1, sda2 etc could be a partition in another hard drive sdb1 or any number. Now a partition in letters, in windows, for example the C drive on a single hard drive could be sda1, and D would be sda2 generally. Could be different partitions but this is a cross reference example.

So if you install windows to the internal the drive will probably be sda and the external sdb, this is probably.

The reason for the fdisk -l command is to identify how the system=hd's are reading at that time and the partition numbers. You can also do this from the gparted partitioner and the disc manager. If you use a thumb drive to boot Ubuntu sometimes the thumb is sda, not the internal, so your checking to see what is called what.

Also the fdisk -l 
l=smallcase L

---

### Post by darkstarsinner on 2011-03-03
Okay so when I go to install Ubuntu to the external drive I'm looking for a sba, sbd with no number behind it because that drive is partitioned for an OS. for the boot manager of course. But shouldn't I put the bootloader on the SSD and use that as the primary boot and select the OS from that?

---

### Post by wilee-nilee on 2011-03-03
> **darkstarsinner said:**
> Okay so when I go to install Ubuntu to the external drive I'm looking for a sba, sbd with no number behind it because that drive is partitioned for an OS. for the boot manager of course. But shouldn't I put the bootloader on the SSD and use that as the primary boot and select the OS from that?

If you put the grub bootloader in the internal mbr and have Ubuntu on a external the internal wont boot unless the external is plugged in.

So with grub in the external mbr you will have the choice of Ubuntu or W7, and protect the W7 bootloader to boot W7 with the USB unplugged. So to have this choice the external has to be booted, so you would put it where you want in the bios before or after the main HD. 

You can use a key prompt at powering on to have a choice of HD's to boot from if you decide that is easiest or just put the external ahead of the internal in the bios to default the boot there when plugged in.

Hope this is explained so it is understandable it can be confusing at first,:)

---

### Post by darkstarsinner on 2011-03-04
Would it be best to unhook the SATA cables from all other drives before the install? The side of the case is off so all of the cables are easily accessible.

---

### Post by wilee-nilee on 2011-03-04
> **darkstarsinner said:**
> Would it be best to unhook the SATA cables from all other drives before the install? The side of the case is off so all of the cables are easily accessible.

Yeah if it makes you more comfortable to unplug the SSD and the storage when install Ubuntu and visa verse with the W7 install go for it. 

You main goal is basically getting the OS bootloader in the correct place. But if you don't it is generally a easy fix.

---

### Post by darkstarsinner on 2011-03-04
Okay so I want the OS bootloader on the Ubuntu external and just do a regular install with Win7 on it's own drives. Now, what if my system isn't seeing the E-SATA on load up?

---

### Post by wilee-nilee on 2011-03-04
> **darkstarsinner said:**
> Okay so I want the OS bootloader on the Ubuntu external and just do a regular install with Win7 on it's own drives. Now, what if my system isn't seeing the E-SATA on load up?

When you say not seeing do you mean once everything is installed, can you be more specific.

There is a per-session key prompt like you use to get to the bios that will bring up a boot from menu that lists the HD's, floppy, cd, looks similar to the bios list, it is outside of the bios though. Mine is triggered with a f12 key yours could be esc or another f key.

---

### Post by darkstarsinner on 2011-03-04
Well before I wiped the discs completely I had Ubuntu installed onto the external. But it would boot straight into windows. My Bios key is the delete button. I haven't seen anything about the drive listings for my mobo.

---

### Post by wilee-nilee on 2011-03-04
> **darkstarsinner said:**
> Well before I wiped the discs completely I had Ubuntu installed onto the external. But it would boot straight into windows. My Bios key is the delete button. I haven't seen anything about the drive listings for my mobo.

So with that information it is difficult to tell what happened. From the first post  > When I tried to install Ubuntu on an external HDD it screwed everything up and wouldn't even boot windows.

It is a little difficult to know exactly what you did, the information is convoluted. But installing is not a big deal once you understand what your doing, took me a while to figure it out myself.:)

---

### Post by darkstarsinner on 2011-03-04
The install two posts up was before I screwed up the Windows boot load. I was just using it as an example.

But I thank you greatly for your patience with me asking all of these remedial questions. I'm still working on issues with windows installs too. I used to just install the OS and go but now that I'm digging a bit deeper I'm having issues. Working on installing 7 on the SSD and keeping everything on the HDD's. I had it up but it was still bloating the SSD with crap so it wasn't working the way it should have been.

I will give the install suggestions you gave me a shot and see how everything turns out. Hopefully I will get to the bottom of this.

---

### Post by darkstarsinner on 2011-03-04
Well here's to good advice. I am currently using Ubunut from the external HDD using esata. I did unhook all other sata ports for the install to ensure I didn't screw anything up during the install. It's updating now with no disk in the drive so I believe everything is a go. I will let you know more tomorrow when I install WIN7 on the other drives. Thank you again for all your help!!!

---

