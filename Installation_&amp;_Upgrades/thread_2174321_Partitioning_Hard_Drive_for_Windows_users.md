---
title: "Partitioning Hard Drive for Windows users"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by Nelson_Batista on 2013-09-13
Hello, everyone! I started trying Ubuntu a few days ago, and have decided to fully switch over from Windows 7.  I tried a bit of (admittedly) poorly-informed repartitioning of my hard drive so that I could make Ubuntu my primary OS in order to avoid having all of my files permanently erased. However, I am quite worried that I got way ahead of myself and have decided to stop and ask someone for help before I go any further. Thus far I have created a new partition of size 9265 MB (9.2 GB) and type ext3. I have included a screenshot of the installation window and was hoping that anyone would be able to tell me what to do next. I am particularly concerned about which partitions should have which mount points, as well as how to access the files that I (hopefully) haven't modified or damaged in any way during my little experimentation, though any information you're willing to provide would be greatly appreciated.  Screenshot: [http://i.imgur.com/t2sb5vp.png](http://i.imgur.com/t2sb5vp.png)

---

### Post by nerdtron on 2013-09-13
Good thing you have a screenshot.
So I assume you have file on both the ntfs partitions?
Looks OK to me. The mount point / is where Ubuntu will be installed. Choose "ext4" instead of "ext3". 
Also, fully switch to Ubuntu with only 9.2GB? It's like 9.2GB of Drive  C:/ partition in windows, even though your files/data will be on the  ntfs partitions, you'll run out of space when you install a lot of  programs.

You can click "install now" and it will continue but you sure you don't want to create a swap partition?

When Ubuntu boots you'll see 2 partitions in nautilus for your two ntfs partitions.

---

### Post by Nelson_Batista on 2013-09-13
I'm fairly certain I have files on both NTFS partitions. Most definitely some important ones on the 480GB one. What size would you recommend for the Ubuntu partition? And should I specify any mount points for the others? Also what is a swap partition and should I have one?

---

### Post by nerdtron on 2013-09-13
If you can still boot into Windows 7, it is safer to adjust the Ubuntu partition there since you can immediately check if your data is good after you have created/shrink/extend your partitions. On the disk management in windows 7, shink your ntfs partition a little bit and add it to Ubuntu partition.
I say 15BG to 20 GB is good for Ubuntu / partition.
You won't need a swap if you have a lot of RAM say 4GB and up. And the size should depend on weather you are going to use "hibernate". In this case the swap partition can be the same as the amount of ram on your computer.

You don't have to set mount points for the NTFS partitions. When you boots Ubuntu, you can see these partitions in the side pane of nautilus. Just click them and you'll have access to those partitions.

---

### Post by oldfred on 2013-09-13
Only use Windows to shrink NTFS partitions and immediately reboot so it can run chkdsk and fix itself for its new size. Also never make Windows too small as it needs 30% free space to work well. At 10% free it becomes very slow.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Mephisto Pheles on 2013-09-14
If you really are considering moving to ubuntu permanently, I suggest you keep your windows installed as fall back, you never know.

 First of all do some Win housekeeping: 

1. If there is anything of any importance to you on your windows partitions, photos, documents, home movies, passwords etc etc please back it up before you start! It's probably not necessary but it is always Better to be safe than sorry.
 
 2. get the free CCleaner (piriform.com), and take your time to go through it's advanced settings. Let it also delete all Windows Updates Installers, that's easily a few gigabytes depending on how old your Win is. This wll not delete the updates, these are just the installers. ( Don't use the registry cleaner!)

 3. use the system Disk Cleanup and let it also delete all but the last system restore points. (Turn off disk indexing as well)

    4. uninstall all programs you don't need / won't use anymore. Think about it first, assume you might have to fall back on Win 7 for a couple days if anything happens with your ubuntu. Depending on what you use your computer for keep your options open. (Allows you to download/burn updated linux iso's for example. Or even google for solutions or ask for help here.)

  5. If you're not going to use Win 7 regularly anymore, and have enough RAM, turn off the pagefile, but leave enough free space for it to be reactivated when you resize later on, in case you need it again later. (Remember to turn it back on if you're going back to Win for more than maintenance use). If the 10 Gb partition on your graphic is your system partition, you can skip this step. Leave the pagefile. 

   6. defragment all your NTFS partitions using a decent Win defragmenter that allows you to move all the files to the beginning of the partition. (Perfect Disk for example, I think even the demo will let you do it, it's called pre-shrink defrag. For your 10 Gb partition use Smart Placement instead. No need to resize that one.)

  7. use a windows partitioning tool to resize your NTFS partitions, (in your case the 450Gb one, I'd leave the 10 Gb one alone), remember to leave enough free space in case you need to reactivate your pagefile. (assuming that you're sure you want to stay on linux, if not leave enough free space, you can use ntfs drives/space under linux. You can always reclaim the ext 4/3 partition later should you want to go back to Win permanently. See 8 below first before you decide on the size of your ntfs partitions)
 
  8. Resize the ext 4/3 / partition to something comfortable (15-30 gig), depending on how much you'll be installing, programs and software that is.  Always keep your options open, you have plenty of space, so. (You already have 9365Mb in the graphic you posted so you really only need an extra 10-20 Gb from your largest ntfs partition and a swap partition the size of your RAM).

    9. As for space you'll need for your Data (documents, photos, mp3s, movies, pdfs etc etc), purists might/will disagree but I use my NTFS partitions I had under Win XP for all my data. Since ubuntu allows you to use them out of the box it's safer for me, in case my linux fails (or rather : if I screw up again wanting to have the very latest kernel!) I can access them over Win XP that I miminimized and kept, and eventually recover them via my home Win network. In your case you'll be able to use the large 450 GB NTFS partition for your data. If you want to you can have it mounted on boot. If you want to keep things separate, make a "Linux Data" folder on it . (Or if you're comfortable enough with resizing partitions, split it up in 2 NTFS partitions, depending on how much free space you have available on that large partition after extending your ext 4 and creating a swap partition. This is definitely optional. That's what I would do. No requirement.)

   
    Although it is unlikely I will ever go back to Win, I do appreciate that I can fall back to it in case of a disaster. Formatting everything to ext 4, for my data too, would reduce my options and it would have been way to much work in my case, so I didn't want to do it. One consequence you'll have to accept, you better defragment your NTFS partitions regularly, once every couple of months or even twice a year should be enough, since it doesn't make that big a difference for most data anyway. Depending on what you use your computer for of course. (If it's loaded with 4+ gigabyte sized movies defragment regularly as you rip or downloaded a couple of them if you have playback problems.)

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Installation & Upgrades**.*

Why not simply set up a rock solid LTS release as the 'fallback' and create some spare partitions for playthings (Ubuntu installs you can experiment with, break and learn by fixing)? I personally don't see any point in having Windows as the default 'fallback' position or OS. Not sure why that's any better or worse than anything else.

I always use an LTS partition as my main squeeze set up the way I like and have four partitions for diddling about. The other option is to set up an install how you like then clone it. Anything breaks, just reinstall the working version to the / partition. This would presume you have all personal data on another partition (/home perhaps). 

If want to run Linux only, I don't see *any* reason at all to have Windows on your machine as a safety blanket. ;)

---

### Post by Nelson_Batista on 2013-09-14
EDIT: Thank you all so much for your help. Much appreciated. :)

After a day of some headaches and much googling, I've managed to come up with this: [http://i.imgur.com/b5Y8Ls6.png](http://i.imgur.com/b5Y8Ls6.png)

I'm fairly certain something is horribly wrong somewhere. /dev/sda1 looks pretty off. I've also backed up all the stuff I care about on what was the large NTFS partition so formatting is no longer an issue. I tried installing Ubuntu using the other method, which involves formatting the entire drive, only to have it give me "error: file '/grub/i386-pc/normal.mod' not found" followed by the line "grub rescue>" which, while it sounds adorable, means I can't boot into Ubuntu unless I use "Try Ubuntu" from the USB drive. I figured it had something to do with lack of proper partitioning so I decided to try my hand at manual partitioning once again, under the assumption that the worst that could happen is that I format a hard drive that no longer has anything important to me.

EDIT: I also would like to point out that I have 4 GB of RAM, but only 2 GB for the swap partition. Was wondering if that would be an issue. Also, sorry for all the questions; I'm VERY new to all this. :/

---

### Post by nerdtron on 2013-09-14
All is correct! Except for the "Device for boot loader installation". You should choose /dev/sda for the bootloader. I think this is the reason you are getting a "grub rescue>" error.

---

### Post by Nelson_Batista on 2013-09-14
Followed Nerdtron's instructions and it installed and booted with no errors of any sort. Everything seems to be working perfectly fine. Thank you all so much for your help. :)

---

