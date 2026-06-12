---
title: "Windows Ubuntu Dual Boot"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by PixelSmack on 2008-09-06
Ok strange question but i have a ubuntu system that is running only ubuntu, and i could do with doing a dual install with windows, however i am not keen to have to format. I really need the dual boot with windows for performance reasons on this project and am struggling to think of a way to do it without messing up my MBR etc.. does anyone have any ideas, a backup and restore from my current install would be a possibility if anyone has any good ideas for doing that.

Thanks, Andrew.

---

### Post by overdrank on 2008-09-06
> **PixelSmack said:**
> Ok strange question but i have a ubuntu system that is running only ubuntu, and i could do with doing a dual install with windows, however i am not keen to have to format. I really need the dual boot with windows for performance reasons on this project and am struggling to think of a way to do it without messing up my MBR etc.. does anyone have any ideas, a backup and restore from my current install would be a possibility if anyone has any good ideas for doing that.

Thanks, Andrew.

Hi and just a thought but you could try a Virtual Machine.

---

### Post by Herman on 2008-09-06
'windows *for performance reasons' ? *LOL,well,whatever you say.How about installing Windows inside Ubuntu? Have you ever tried that? It's not anywheres near as tricky as one might expect. Here's the link to a good how-to that I used, [HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server")

EDIT: That means you would be running it as a 'virtual machine', as  overdrank just suggested.

---

### Post by PixelSmack on 2008-09-06
I know it sounds silly but i need as little overhead as possible inside a windows environment. Thanks for the ideas.

---

### Post by hubie on 2008-09-06
Partition your system as you want to include Windows.  I've used [GParted]("http://gparted.sourceforge.net/") (download the LiveCD to do it).  For the new partition you create, make sure you format it fat32 or ntfs so that Windows will see it.  I've seen posts that say you should make the Windows partition the first partition on the disk, but I don't know if that is a requirement.

Install Windows onto the new partition (if you formatted the new partition fat32, you can probably have Windows reformat the partition ntfs if you want).

When you are done your install, Windows should boot without a hitch.  The problem, of course, is that Windows will overwrite your MBR.  To recover, you basically boot your system with a recovery or LiveCD and reinstall grub.  One set of directions is [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Another option is to use the Windows boot loader and not reinstall grub.  The few posts I've seen on that are from people who do that because they have trepidation in messing with the Windows MBR.  Personally I don't see what they are worried about and I've never had problems using grub.  Just this morning I installed Ubuntu onto my WinXP laptop (I'm typing from it right now).  I'm using grub, but I installed Ubuntu onto a running Windows system where you want to go the other way.

Unless you accidentally reformat the wrong partition, which is hard to do, data loss should not be a concern.  However, prudence would suggest that you backup anything important on your linux partitions before you start.

---

### Post by Herman on 2008-09-06
> I've seen posts that say you should make the Windows partition the first partition on the disk, but I don't know if that is a requirement.:) Just to be helpful here, I have tried moving Windows XP partitions around a few times and as long as the partition number remains the same I found that it doesn't seem to matter where Windows is located physically on the hard disc at all.  I have even fixed a Windows XP installation that wouldn't boot by moving it to the other end of the hard disk, but I don't know why that worked, it just did. (Later, my freind called me to go over to his place and delete it, they only like Ubuntu.)
I'm not sure about Windows 95 0r 98. I have read that Vista doesn't even care what partition number it has, as long as the 'disc signature' in the MBR doesn't get changed.
If the partition number for Windows XP gets changed, Windows XP won't boot, but you just need to edit boot.ini with the right partition number and that'll fix it. An easier way  is to boot Windows XP installation CD and run the command 'bootcfg /rebuild', and that will replace the old boot.ini file with a new (corrected) one or create a new one of none exists. :)

---

