---
title: "Ubuntu 11.04 falls to BusyBox on boot."
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by reallybadwithlinux on 2011-07-28
I've been having this problem for months, I keep losing interest in fixing it but every now and again I'll pick it back up (I'd really like to use Ubunutu). 
Basically, I've just done a complete ubuntu install alongside windows 7. I partitioned the drive to give Ubuntu 30GB. Everything went smooth. After installation, I boot in GRUB (or GRUB2, I'm really not that well versed in Linux), attempt to boot into my Ubuntu installation and it falls straight to something called busybox, essentially leaving me at a command line.
It also may be worth mentioning that I can't even get WUBI to work correctly. It's quite peculiar. I don't remember the error I keep getting for WUBI, but I think it's strange that ever since I installed Windows 7, I have been unable to get ANY version of Linux to work. I even tried Kubuntu a few months back with no success. 
I've found a couple of similar posts on this site, so I'm sorry about the repost, however as I have such a weak understanding of Linux I was unable to follow any of the advice haha.
If you have any ideas or advice for me, please dumb it down. Thanks very much in advance guys! :)

---

### Post by internetprofiles1 on 2011-11-29
I had the same issue after windows did a chdsk there is a program called boot-repair for ubuntu which some have reported success but i was unable to get it to work. What was My solution? dump windows dual boot.back up the windows personal files to a thumb drive or dvd and Just install ubuntu. The only thing was holding me back was some of my online classes requires internet explorer to work, but the user agent switcher plugin for firefox solved that problem, so as of now i going with ubuntu only.the dual boot seem to cause a lot more problems. Using wubi i.e installing ubuntu inside windows is about option you can choose. In that case the boot file will come from windows instead of the grub boot file eliminating that error, however ubuntu will run slower than normal

---

### Post by internetprofiles1 on 2011-12-03
I redid my attempt at installing only ubuntu 11.10 and I got the same busybox error . A lot of advanced linux users know how to fix it, but hardly anyone describes this as if taking to a child and I feel lost with the instructions. try this, reboot with Live CD select try ubuntu. Then go to the apps gparted and have a look at your partitions, mine was reading that there were no partitions all 80g unallocated..do you get the same error?? Also if you try to reinstall the installer no longer see that you have ubuntu already installed. Search for a post on "missing partitions"  and it has the fix i did not save the link. For my fix, I burnt the iso of 10.04 LTS version and that took care of my partitions and install with no problems booting, and no errors So right now I running that older version, but i will upgrade and see what happens. I think it has something to do with improperly formatting partitions, and unbuntu does not write the new partitions to the master boot record(MBR).

---

### Post by drs305 on 2011-12-03
If  you can boot an Ubuntu LiveCD and download/run the Boot Info Script it can help us see what's happening. The script will generate a file called RESULTS.txt. Open it and include the contents in a new post. 

Once you have pasted it, highlight it and press the # icon. That will generate 'code' tags which make reading it easier.

If your problem is with some aspect of the bootloader (Grub 2) or partitioning, we may be able to help you boot the installation.

You can get to the script download page by clicking the "BIS" link in my signature line.

---

### Post by drs305 on 2011-12-03
If  you can boot an Ubuntu LiveCD and download/run the Boot Info Script it can help us see what's happening. The script will generate a file called RESULTS.txt. Open it and include the contents in a new post. 

Once you have pasted it, highlight it and press the # icon. That will generate 'code' tags which make reading it easier.

If your problem is with some aspect of the bootloader (Grub 2) or partitioning, we may be able to help you boot the installation.

You can get to the script download page by clicking the "BIS" link in my signature line or here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

