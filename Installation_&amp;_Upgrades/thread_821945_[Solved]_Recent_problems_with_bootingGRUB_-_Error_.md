---
title: "[Solved] Recent problems with booting/GRUB - Error 17"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by FireboltFred on 2008-06-07
Hello. I recently had a few problems booting up my system, and even though I was able to eventually solve it myself, i wanted to post my solution in case it can help someone in the future.

So, first some background. I have a triple-boot setup on my PC, with XP, Vista, and Ubuntu 8.04. These were all running fine, with GRUB coming up first, and then the Windows bootloader afterward if i select "Windows." Anyway, I was running out of space for my windows partitions and I wanted to expand them with some free space on the rest of that hard drive. I couldn't do this in either XP's or Vista's drive manager, so I installed Partition Magic 8 on XP.

When I first started PM, however, it gave me some message saying that the numbering of my drives was off (or something similar), and so the program could go ahead and fix that right up for me, which I [foolishly] let it do. And then, to top it all of, PM couldn't even shrink or expand any of my partitions. Gay. After closing PM, for some reason it remounted my secondary drive to E: (it had been Z:).

I was getting a little suspicious of this program, so I decided to reboot to make sure that I was still able to.

Lo and behold, i was not. Before even getting to the GRUB menu, it would say "Loading GRUB..." and then give me an Error 17.

I booted to an Ubuntu 7.10 Live CD that I had so that I could look up the issue on this site, and I found a number of useful topics. [This]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub") was the first topic I found, and it still seems to be the most helpful. I also found a topic that links to a site that has directions for various numbered GRUB errors, but I can't find it anymore. [This]("http://ubuntuforums.org/showthread.php?t=819326&highlight=grub+18") also helped, but it's for error 15.

Anyway, I will sum up what I found out. Many of the GRUB errors are caused by GRUB looking for the wrong partition when it goes to load the menu, or when it goes to load a particular OS. In this case, it was screwed up by Partition Magic, but other times people have gotten it when they reinstall Linux or install Windows, etc. Some topics say to change boot order in the BIOS, but that was not applicable here. Anyway, bottom line(s):

1. If you get an error (including 15, 17, 18) BEFORE Grub loads the menu, do this:
- Boot to an Ubuntu Live CD.
- Open the Terminal
- Reinstall GRUB (refer to [This]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+18") topic for directions)
- When you do that, take note of the partition that Linux is installed on (in the format hd(#,#)).
- You can restart now and see if that fixed the problem. For me, I was then able to get into Windows, but it gave another error when I tried to boot into Linux. For that, read on...

2. If you receive an error AFTER trying to boot an OS from the GRUB menu:
- On the GRUB menu, hit "e" to edit the boot command. Since the problem is most likely that it's looking on the wrong partition, edit that first line to a different set of numbers (i.e. hd(#,#)). If you already went through step 1, try using the set you got when you ran the commands in the terminal. If that doesn't work or you don't know the correct partition, you can either:
* Try various number combinations, such as hd(0,0), hd(0,1), hd(1,0), etc.
* Boot to a Live CD and run the commands:

sudo grub
find /boot/grub/stage1
quit

And take note of the partition.

- Now, if you successfully booted into Ubuntu this time from the GRUB menu, or you are running from the Live CD, the next step is the same - you have to edit the Grub menu.lst file. It can be found in the /boot/grub/ folder. To edit it, i just use "sudo gedit /boot/grub/menu.lst" and it seems to work fine.
- There are a number of options to change in this file, such as default entry to load, colors, etc. I had to edit this file before to add a Windows entry. To fix the problem, though, you will need to change the partition that GRUB is accessing so it will load it correctly.
- Using the partition hd(#,#) that you know is the default Ubuntu boot partition, change the "root" of each entry to the correct partition.
- Save the menu.lst file and reboot

Hopefully, you did all of this correctly and it works now, but if it's still not working, you can just repeat these steps. Some people say you can also fix some of this with a Super Grub CD, but I have not looked into this method. Everything worked for me at this point, so that's pretty much all I can help you with for now. Hopefully it helps.

---

### Post by Unix_Slayer on 2008-06-07
[http://www.supergrubdisk.org]("http://www.supergrubdisk.org")

---

