---
title: "dual boot install problem"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by mickeyf on 2007-11-19
First the background, then the question.

Background:

I live in a remote area with only dial-up. I can NOT download an entire rescue CD, or even utility programs if they are too large. On a good day I can get a 10 or maybe a 15 meg file.

I read all the dual boot install how-to's I could find listed or linked to here. I installed 6.10 over win 2k using a CD that I burned when I still lived in high-speed land. The link to NTFS Resizer was dead; I used the re-partitioning facilities that the installer brought up. I shrunk the win 2k partition, and did get a message that the operation 'could not be performed', but the program proceeded and reported success otherwise. I left the resized NTFS partition alone, and put ext3 on the new partitions. Install then reported that the first partition would not be used. Since this presumably meant 'used by Ubuntu', that seemed OK. Ubuntu installed fine, and the boot menu presents me with a choice of Ubuntu or win 2k. Ubuntu boots and runs. Win 2k shows 'starting', then the Windows logo screen, then blue screens with 'Inaccessable boot device'. 

From this I surmise that the MBR is fine, but further downstream there is an issue.

Now the Question:

Can anyone instruct me on how to recover from this without going back to square one and taking an hour and a half to reinstall Windows, then an hour to re-install Ubuntu? (and then possibly repeating the problem?!)

Thanks!

Mickey

---

### Post by monktbd on 2007-11-19
my guess is that the shrinking process did not go well and deleted some of the files windows needed to boot. 
i dont know how much fragmentation occurs on ntfs drives but did you defragment before shrinking?

---

### Post by mickeyf on 2007-11-19
It was a new win 2k install, but I defraged anyway. Twice. Yes, but the question is - if there are missing files, which ones (NTLDR?), and is there a way to replace them if the drive is not ordinarily visible?

thnks

---

### Post by jedopo on 2007-11-19
Hey, I think I had the same problem.  The problem wasn't the bootcode in the MBR but actually the partition table.  (I found this out by poking around with MBRtool)

I was installing 7.10 over XP.  Ubuntu and grub worked fine, but booting to XP from grub yielded the familiar black xp loading status screen, followed quickly by BSOD.  In the end I was able to recover the XP system, by going into fdisk and deleting the new partitions (ext3 and swap) leaving only windows.  Reboot and everything came up fine.  I'm going to reinstall unbuntu now...we'll see how it goes.

---

