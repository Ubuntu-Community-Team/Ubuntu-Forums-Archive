---
title: "Problems with installing l/k/xubuntu via wubi"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by Master619 on 2013-01-15
Here is the current disk setup of my computer (running windows 7):
[IMG]http://i.imgur.com/I1Swa.png[/IMG]

Some explanation: I have two physical hard disk: 1TB and 500GB. The D: drive is the whole 1TB one. The 500 GB is initially split into 3 partitions F:, C: (with windows 7 installled) and E: . The free unallocated space was from shrinking the E: partition just now (I'll explain that later).

The current situation:
Like many other windows user, I decided to try out ubuntu today.

After some googling around, I tried with the (seemingly) easiest method: installing via wubi. I downloaded lubuntu and wubi, both v12.10, placed them in the same directory and started installing.

I chose to install it on my E: drive, which at the time still had ~56GB free, and gave wubi 15GB to work with.

Everything was going fine, and the installation finished with the prompt to restart windows. I chose to restart manually, but still restarted right after closing my files.

The system restarted and gave me the lovely boot menu, from which I chose Lubuntu to continue. It gave the (hd0,0) NTFS5: "prefix" is not set error, but still continued the installation.

The lubuntu welcome screen appeared, some final installation steps was carried out, and BAM! There was an error of **"No root file system is defined. Please correct this from the partitioning menu."**

After some searching, the most popular solution was to "click on the drive and choose to mount it as root (/). But **HOW**? I was stuck at that error message and couldn't do anything else! 

I could Ctrl-Alt-F1 to the terminal and sudo parted -l gave me an error of "Error: *Can't have overlapping partitions". *The drive mentioned was /dev/sdb, which seemed to have 1024GB storage, so I assumed it was my 1TB disk.

[LEFT]Tried searching some more, and some one suggested using fixparts. It wasn't included, so I had to sudo apt-get install gpart. Then I ran sudo fixparts /dev/sdb, then p for it to print the table, and then w for it to save the MBR. The saving was completed, but sudo parted -l still gave the same error. Rebooting into lubuntu still gave the same error. 

Tried xubuntu and kubuntu but still the same result.
(There didn't seem to be any problem with root.disk and swap.disk when I checked in windows 7. Those files were still there)

That's when I gave up and decided to take the hard path: installing ubuntu separately on a different partition, but still wanted it to dual-boot with my existing windows 7. So I read some tutorial and started with shrinking some free space from my E: drive, resulted in the state at the beginning of the post.

**Sorry for the long explanation, but now my questions are:**
_ What was wrong with my wubi installations? Is there anything I can do to easily fix it without falling back to installing ubuntu separately?
_ If the latter is a must, then is it ok to install ubuntu on the free unallocated space right now? Is there any problem with the current disk setup?
_ Thanks in advance.
[/LEFT]

---

### Post by Frogs Hair on 2013-01-15
Hello and Welcome

1. Wubi uses the c drive by default and is indented to be used from there but others have been successful using other drives .

2. Windows disk management can't see the Ubuntu root disk because it is inside the Windows partition or what ever drive is chosen.  

There is  a lot material at the link but I think the problem has been dressed before. 

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

