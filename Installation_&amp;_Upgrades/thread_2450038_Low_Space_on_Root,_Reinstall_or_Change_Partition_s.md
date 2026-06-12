---
title: "Low Space on Root, Reinstall or Change Partition size"
date: 2020-09-06
forum: Installation &amp; Upgrades
---

### Post by thatsmyboy on 2020-09-06
I've got an old system that keeps on kicking. I made a mistake on my last installation, but I think there's no problem with the SSD that my computer uses. 

Currently my setup is
Root : 15 GB (90.1% full)
Swap : 4 GB
Extended Partition Including:
  Home: ~430 GB
  Boot : 52 GB ( 2.5% full)

I previously had trouble with this rig with a Boot partition of about 2 GB, so I upped the size of that partition and called it a day. I now realize that I probably have the proportions backward between Boot and Root. Should have been ~15 for Boot, ~50 for Root, not the other way around. Suggestions whether to reinstall entirely or if I can get away with resizing partitions?? [ATTACH=CONFIG]286891[/ATTACH][ATTACH=CONFIG]286892[/ATTACH]

---

### Post by SeijiSensei on 2020-09-06
I'd reinstall.  I'm not sure you'll get very far with resizing given the layout of your drive.

---

### Post by oldfred on 2020-09-06
I am also a fan of gpt partitioning, then no extended & logical partitions.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

With BIOS boot, you do need a 1 or 2MB unformatted partition with bios_grub flag for grub to install correctly to gpt's protective MBR. When I still only had BIOS, but was eventually planning on a new UEFI system, I added both an ESP and bios_grub as first two partitions on every new or changed drive.

man fdisk # disk labels section:
"GPT is always a better choice than MBR, especially on modern hardware with a UEFI boot loader."

Also most desktops do not need separate /boot partition, nor swap partition. Some servers may need /boot and a swap partition depending on configuration & use.
Default install of Ubuntu is just / (root) and ESP if UEFI. It creates a swap file by default if no swap partition found.
Many like separate /home and/or data partition(s).

Converting drive from MBR to gpt will totally erase drive if you just reset it in gparted.
But there are tools to convert in place, normally reinstall of grub required and any settings that use UUIDs as they all change. Good backups still required.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by thatsmyboy on 2020-09-06
Thanks guys! Glad you chimed in. I'll check the links - I have never done GPT, so it'll take a little research. Sounds like a reinstall is the painless option . I may have mentioned, but this is NOT modern hardware (more or less same hardware as [this 2014 post]("https://ubuntuforums.org/showthread.php?t=2236871")). so I'll try it out with caution. Always glad to get OldFred's help! SeijiSensei, thanks as well.

---

### Post by Impavidus on 2020-09-06
2 GB should be more than enough for a /boot partition (if you want one at all), assuming you regularly clean old kernels. They've been autoremovable for several years now. About 20 or 30 GB is fine for a root partition, depending on your needs.

The layout of your partitions is such that it's not easy to rearrange things, as your /home partition is in the middle. Probably best to start fresh and restore your /home from your backups.

---

### Post by SeijiSensei on 2020-09-06
Why would he need to restore /home from backups? If you choose manual partitioning, you can leave the home partition alone. I do that all the time. As I see it, he should just reinstall and reverse the assignments of the /boot and root filesystems.

---

### Post by Impavidus on 2020-09-06
That can be done. The partition sizes work, but are a bit weird. Maybe I should have said that a bit more clearly.

So, OP can do a fresh install, keeping the /home partition and just swapping root and /boot, as is OP's original plan. But if OP wants to change the partition sizes to something more sensible, it's better to wipe everything and make a fresh start.

---

### Post by zebra2 on 2020-09-06
If it was me, I would reinstall and choose "other" at the install options screen.  
If it is 20.04 or later I would go with 
35Gig root
the rest as /home
The 35 Gig root allows room for the swapfile that is stored in root and also the fact that the entire OS base is larger than it used to be. I haven't used a 15 Gig root since Puppy Linux. With the advent of Terebyte drives I have used 30Gig for home but now since the swap partition is being moved to root as a file I am using a 35 Gig root. A "full root" equals a crashed computer equals another reinstall. Since I don't do the UEFI thing EXT4 with no extended partition works fine for me.  I have a laptop dual booting 20.10 and Windows 10 in MBR and I don't have an extended partition.

---

### Post by thatsmyboy on 2020-09-28
> do a fresh install, keeping the /home partition and just swapping root and /boot, as is OP's original plan. But if OP wants to change the partition sizes to something more sensible, it's better to wipe everything and make a fresh start. 
  Thanks, Impavidus, that's a nice succinct summary.

---

### Post by hostguycom on 2020-09-28
First, take backup of your machine.
Then, delete the partitions leaving behind /home and after that recreate partitions as per new need and install OS again.
Later you can mount the /home directory.

---

### Post by ActionParsnip on 2020-09-28
Try clearing old kernels

---

### Post by garvinrick4 on 2020-09-28
I agree with some I would just backup Home files if you don't have copy of and since you might want multiple installs partition and all installs can use same Home so can keep installs at 20 to 30 gig or so and wont run out at all. Leave room in extended partition for more installs you
might go nuts. Use gparted to reformat install and make other partionts out of huge Home and use manual to reinstall / . 
You can mount any partition with / and install grub if you want it to boot
first in line after a new install which can put its grub in mbr 'sda' if mbr what you are using. 
READ "old fred" can tell you about anything to do with installations, grub and such. 
Make sure you understand what each line of code does and
make yourself what i call a 'Cheat Sheet' with what the code does will come in handy 
when your memory fails while sitting at the keyboard
 If  old fred didnt give ## the line before his code ask him he will tell you what each line does)
#Basically i just said what post 2 said but in more drawn out way for those who need a bit more info

---

