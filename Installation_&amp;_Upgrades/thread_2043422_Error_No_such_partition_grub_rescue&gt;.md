---
title: "Error: No such partition grub rescue&gt;"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by Verm93 on 2012-08-16
I have a laptop runningUbuntu 12.04. I recently added a second hard drive in the optical bay. After installing the second hard drive I attempted to boot up and got "error: no such partition. grub rescue>" prompt. I checked the boot priority in BIOS and made sure it was set to notebook hard drive, which it was. The only way I can get into Ubuntu at the moment is to go to BIOS --> Boot Device Options, and then manually choose to boot into my hard drive with the Ubuntu install. Any insight on this issue?

---

### Post by drs305 on 2012-08-16
Verm93,

Welcome to the Ubuntu Forums.  :-)

Once you boot into Ubuntu, try running "sudo update-grub" just to make sure BIOS and GRUB are seeing the same things. You can also run "sudo grub-install /dev/sda" if sda is your Ubuntu drive.

If that doesn't fix it, I'd recommend installing Boot Repair and clicking the Recommended Repair button. If the boot still is problematic, run the boot info script from Boot Repair and provide the link. It will help us see what's going on. With the varied partitioning schemes available today, the script results is very helpful to get the true picture of your system setup.

Boot Repair link in my signature line.

---

### Post by OM55 on 2012-08-16
Hello Verm93,

Expanding on the previous reply by drs305, here is a detailed step by step description that will help you resolve the issue right away.

Symptom: 
======== 
After boot we get the prompt: 
 
error: file not found. 
Grub rescue>- 
 
 
Problem: 
======== 
The grub information on disk has been corrupted and the system can not boot from the proper partition 
 
Solution: 
========= 
1. Boot with Ubuntu Live CD 
 
2. Open terminal (command prompt) 
 
3. Type: 
```
sudo fdisk -l 
```You will get a list of partitions, similar to the following list: 
 
```
/dev/sda1 13 102400 de Dell Utility 
/dev/sda2 * 13 1926 15360000 7 HPFS/NTFS 
/dev/sda3 1926 30892 232676566 7 HPFS/NTFS 
/dev/sda4 30893 60802 240245761 5 Extended 
/dev/sda5 30893 59584 230467584 83 Linux 
/dev/sda6 59585 60802 9777152 82 Linux swap / Solaris  

```Ubuntu partition is the one with the name "Linux" (not necessarily the one with the star, although could be). 
On this case is on '/dev/sda5' so we have to mount it: 
 
4. 
```
sudo mount /dev/sda5 /mnt 
```(replace 'sda5' with the partition name in your case) 
 
5. And then install grub: 
```
    sudo grub-install --root-directory=/mnt /dev/sda 
 
```6. Reboot and verify that all is working fine.

Hope that helps.

---

### Post by Verm93 on 2012-08-16
Thanks, I'll share my results later after I try it :)

---

### Post by Verm93 on 2012-08-16
I executed the commands and.it said grub was successfully installed, however when booted up I still receive the grub rescue prompt

---

### Post by OM55 on 2012-08-16
So go on and try Boot-Repair.

1. Boot with Ubuntu Live

2. ```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

3. ```
sudo apt-get install -y boot-repair && boot-repair
```

4. (if didn't launch, launch it manually with: 'boot-repair')

You can find more information on Boot-Repair and how to use it at: 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by johnvoisey on 2012-11-09
Hi

Just wanted to say thank you to 'drs' for the info.

I have a system that has not so much evolved as congealed into sentience in a dark corner. XP Professional on what linux calls /dev/sda, an old UBUNTU distro (with some vital mail from an old server) on /dev/sdb and LUBUNTU which I used day-to-day on /dev/sdc (!) 

Despite the unusual (?) config things were all fine and dandy with a grub boot off the /dev/sda mbr until a couple of weeks ago. The LUBUNTU system told em a new release (12.??) was available and like a sucker I fell for it and took the upgrade.

I've had the same error as the OP'er from the moment the system rebooted. "Grub rescue" prompt unless I use the F11 key to bring up the boot meny, then all was ok.

I just tried the advice in drs's first reply in the thread and bingo, all is well again. All I can think of is that the "standard" update script found my config a bit hard to digest. 

Thanks again,

---

### Post by Jorge_Ramirez on 2013-10-08
I've had the same issue as the OP and as this isn't solved I'll post the solution that worked for me:

I recently installed a second hdd in my laptop (replacing the optical bay) and put ubuntu in it.

Just after the ubuntu installation i got that "No such device" message. Typing "ls" in grub rescue command prompt only showed windows partitions and not my second hdd where I installed ubuntu.

So I had to reboot and manually select the boot device, as the op said.

The solution I finally solved this was:

**Go to BIOS menu > change boot mode from "fast" to "normal".**

---

