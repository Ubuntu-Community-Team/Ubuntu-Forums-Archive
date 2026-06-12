---
title: "Several questions about installing"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by rkdeane on 2009-11-21
I own a Lenovo Y530 4G RAM Nvidia graphics ,centrino2 .
 
A couple months ago I installed ubuntu within windows and it worked fine. But I ended up deleting it ebcasue i had some expensive software that i needed that i found difficult to get working on ubuntu. Anyhows I am back!!
 
Since then whenever my computer loads IT GIVES THE OPTION OF uBUNTU OR WINDOWS vista to open up in. However the Ubuntu link does not work and i have to restart to select windows.
I would like to get rid of this screen that comes up so the computer is essentially 100% windows.
 
The reason is lately i have tried to put Ubuntu 9.1 64 bit on my computer and have had a world of difficulty. Can't get CD to boot, eventually got it installed but it basically installed a ubuntu folde within C drive 10 folders and 10 files, and i see the .iso file there not sure why it installed like that.It sai there was an error while installing, and said look at LOG file. Not exactly a computer expert so got lost at the point when i checked the log. 
 
But basically I would like to get ride of everything ubuntu related on my computer so I can start afresh.If someone could advide me hopw to get away from the opening screen I would be grateful.
 
Any other advice would be more than welcome. I am currently downloading 8.04 64 bit to see if I have better luck with that one.
 
I have scanned through the forum but have not found my solutions, so basically going to start from where I was several months ago.
 
Thanks in advance for any help.

---

### Post by presence1960 on 2009-11-21
Follow the instructions for Vista [here]("http://ubuntuforums.org/showthread.php?t=1014708").

You will need to boot from a Vista installation DVD. If you do not have one and your recoverypartition/DVDs do not allow access to Vista Recovery Console you can download the iso for your version of vista [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). Burn it as image to CD and boot from that CD. Then follow the instructions in the first link above.

You get GRUB when you boot because GRUB is in the MBR of your hard disk. Doing what is outlined above will put Vista back on MBR and get rid of GRUB.

---

