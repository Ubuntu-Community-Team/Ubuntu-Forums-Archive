---
title: "Partman not recognising partition table"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by tonsofquestions on 2006-06-21
Hi. I've been using linux off-and-on for a while, and decided it was time to try Ubuntu (I needed a reinstall anyway). My system is setup to have a dual-boot with Windows (1 drive, NTFS, EXT3, FAT32, SWAP), and the partition table has been set the way I like it for quite some time. However, when I try to install Ubuntu, the partition manager (I'm assuming partman) doesn't seem to recognise my partition table. I open a shell and check fdisk, which reads it just fine, as do my old linux distro and Windows. My boot manager is currently NTLDR, but I don't see why that should be affecting how the partition manager sees the table.

Is there anything I can do, short of repartitioning (and potentially losing all of my data)? I tried searching the boards, but couldn't find any info. Advice and suggestions would be appreciated. Thanks.

---

### Post by glotz on 2006-06-21
I think the partition editor is Gparted, as in *gnome partition editor application*. I think your boot manager might actually play a role in this as it's written on master boot record (MBR) which contains boot loader **and the partition table**. Maybe if you install GRUB it'd work. What kind of setup did you have in mind? The risk of losing your data is always there. So it's a good idea to backup all mission critical stuff. I've never lost anything though during my exploits...

---

### Post by tonsofquestions on 2006-06-21
Well, I'm pretty sure it's not GParted; I'm using the alternate install CD (so that I can install GRUB somewhere other than the MBR, and am not in Gnome). I can't even install GRUB yet if I wanted to try, since I don't even get to installing - I need to set up paritions and tell it where to install before I get to that stage. I'm not too clear on the differences of the install environment between the two versions, though it does make me curious - anyone know? For that matter, I was browsing through some of the packages on the CD, and was quite surprised to see that it didn't come with some (what I'd call standard) packages, such as emacs, muttm even gcc (that's quite a surprise that it's not there). The last distro I used (fedora) came with a fair number of useful utilities, but I expect I won't realize they're not there until I try. Is there a list somewhere of suggested additional utilities to install? Thanks.

---

### Post by glotz on 2006-06-21
GRUB and Ubuntu have basically very little to do with each others. You can install GRUB totally independently of Ubuntu. [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

I don't know if actually installing GRUB helps though.

---

### Post by tonsofquestions on 2006-06-21
[QUOTE=glotz]GRUB and Ubuntu have basically very little to do with each others. You can install GRUB totally independently of Ubuntu. [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

I don't know if actually installing GRUB helps though.[/QUOTE]

Agreed. It was your suggestion that installing GRUB might help somehow, though it's already installed from my old distro. However, I can't really see how installing it would help, and I don't want to prevent my booting into Windows right now.

---

### Post by glotz on 2006-06-21
Uhm, you can only have one bootloader. Which do you have, GRUB or whatever that was, ntldr? Installing grub won't prevent you from booting windows.

And should it happen, you can easily fix it, if you only have the windows cd.

---

### Post by tonsofquestions on 2006-06-21
[QUOTE=glotz]Uhm, you can only have one bootloader. Which do you have, GRUB or whatever that was, ntldr? [/QUOTE]

Actually, using NTLDR (the windows NT boot LoaDeR) in the MBR does require having GRUB (I've been doing it that way for several years). Windows isn't smart enough to know about linux (and so can't boot it directly), you install GRUB at the beginning of another partition, and point NTLDR to it. GRUB then loads up, though typically the delay is turned down to practically nothing so that it's invisible. In fact, if you do it the other way, you still need NTLDR somewhere for Windows, or else it won't start (it's fussy like that). If you don't believe me, check out some info at [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html).

[QUOTE=glotz]Installing grub won't prevent you from booting windows. And should it happen, you can easily fix it, if you only have the windows cd.[/QUOTE]

Well, using an install CD with an older service pack can cause some issues (it's happened to me in the past; and I don't have a newer CD), not to mention that it can be a hassle, and results in a setup that isn't how I want it. Regardless, can we please get back to my original issue? I'm pretty certain that having GRUB in my MBR instead shouldn't make any difference (what would have happened if I just had an empty pre-partitioned disk that I wanted to use, but didn't want to re-parition)? Which goes back to the original question, does anyone know what's wrong, or what I can do to fix it? I'm also still curious about the list of apps I asked about above (searching the disk further surprises me more and more with what's not there).

---

