---
title: "How do install windows after installing ubunt u 11.10 first?"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by leel05 on 2011-11-04
how do you install windows xp sp2 64bit after installing ubuntu 11.10 64bit first?  i would like to try dual boot but when i try to install xp(having ubuntu installed first) with the cd i always get the blue screen of death? is this fixable? if so how do i go about this? if not is it possible to remove ubuntu 11.10 and fixing the hard drive so xp will correctly install?

please help been looking for answers for a month now and none has help regarding ubuntu to ubuntu+xp...its always xp to ubuntu+xp

i love ubuntu on how fast/secure it runs, but i need windows for piratical reasons with school work

---

### Post by kurt18947 on 2011-11-04
Can you do it the other way around?  Install Windows first then Ubuntu?  GRUB should see and add Windows.  I don't know how to get Windows' boot manager to see Ubuntu and add it.  I use a separate boot manager but that's an additional expense and something else to potentially cause problems.

---

### Post by Hedgehog1 on 2011-11-04
Windows want to run in the first partition (if XP) or the first two partitions (Vista and Windows 7).

To install XP after any other OS, the XP installer has to be helped along.

First, AFTER BACKING UP YOUR IMPORTANT DATA, you would shrink the current 1st partition to make space for the XP one.

Then, you would install XP in that new area you just created.

Lastly, you need to update GRUB to get the dual boot between XP and Ubuntu working.

Other option: Run XP in virtual box as a guest OS of Ubuntu.

***The Hedge***

:KS

---

### Post by leel05 on 2011-11-04
i have tried resizing the ubuntu partition so i could make the extra space used for XP partition and i do have grub installed/updated for dualboot...but unfortunately i get the blue screen of death when trying to install XP (with resized ubuntu partition+grub)...i have a feeling when i installed ubuntu (using all the space in my hard drive) it erased/rewrote the MBR and is messing up the boot for windows xp disk (which i have tried fixing using lilo, but no luck)


so...
1) i dont know why i can't install xp even with a resized ubuntu partition+grub
1a) is it the mbr(being corrupted) that is the problem? 1b)if yes, can it be fixed?
2) is it something to do with grub 3.0 that is messing up the boot of windows xp disk?
3) if there really is no answer how do i go in removing ubuntu os completely? so i can do a fresh installation of XP

---

### Post by Hedgehog1 on 2011-11-04
If all else fails (and it appears it has) and you need to install XP from scratch, Use gparted from the live CD to remove all partitions, and then create a new, empty 'mbr' partition map.

This will leave the drive in a clean state that XP can install on.

Once XP is installed and you have run the windows updates (there will be a ton), you can install Ubuntu again as a dual boot.

***The Hedge***

:KS

---

### Post by Mark Phelps on 2011-11-04
When you boot from CD, the MBR of the hard drive isn't read -- so no matter what is there, it won't affect booting from CD.

If you're getting a bluescreen when booting the XP CD, you have worse problems -- and formatting your drive is not going to do anything to solve those.

---

### Post by amjjawad on 2011-11-04
> **leel05 said:**
> how do you install windows xp sp2 64bit after installing ubuntu 11.10 64bit first?  i would like to try dual boot but when i try to install xp(having ubuntu installed first) with the cd i always get the blue screen of death? is this fixable? if so how do i go about this? if not is it possible to remove ubuntu 11.10 and fixing the hard drive so xp will correctly install?

please help been looking for answers for a month now and none has help regarding ubuntu to ubuntu+xp...its always xp to ubuntu+xp

i love ubuntu on how fast/secure it runs, but i need windows for piratical reasons with school work

It's old but concept should be the same.
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

---

### Post by amjjawad on 2011-11-04
> **leel05 said:**
> how do you install windows xp sp2 64bit after installing ubuntu 11.10 64bit first?  i would like to try dual boot but when i try to install xp(having ubuntu installed first) with the cd i always get the blue screen of death? is this fixable? if so how do i go about this? if not is it possible to remove ubuntu 11.10 and fixing the hard drive so xp will correctly install?

please help been looking for answers for a month now and none has help regarding ubuntu to ubuntu+xp...its always xp to ubuntu+xp

i love ubuntu on how fast/secure it runs, but i need windows for piratical reasons with school work

Off-Topic hence removed.

---

### Post by leel05 on 2011-11-08
okay so if im getting the blue screen, should i even try to repartition my HD (to wipe it clean) and try installing xp....or am i just screwed and should just go buy a cheap HD and install what ever windows os on it? because its getting pretty annoying having to use the campus computers (which are slow/outdated/so many users = no bandwidth)

---

### Post by oldfred on 2011-11-09
You have to have a primary (sda1 thru sda4) partition formated to NTFS with the boot flag.

Then you have to have a full XP install disk not one of the service pack update releases.

---

### Post by leel05 on 2011-11-09
no everything is though sda1...my laptop originally had windows 7 os but apparently crashed somehow (through updates or something and didnt make any software backup because i never in my life would thought windows would do a update and crash...i do back up my docs and stuff regularly) so it couldnt start or anything...then i installed ubuntu(which worked and is using up the whole HD now) but would like to install my windows xp (full installation disk)....i have tried repartitioning for ntfs with ubuntu partitions (dual boot)(only gets the blue screen after the cd boots)....have tried removing all partitions and installing xp on clean HD (blue screen shows up)....also have done a virtual machine of xp which does install and works (so i know the disk does work still) but would want dual boot or just fully xp until i buy windows 7 os again =(

---

### Post by mohamedtoma73 on 2011-11-09
i can figure a solution.install xp and then install ubuntu inside windows using wubi.in the boot menu of wubi  ubuntu installation you will see entry of the previosly installed ubuntu(installed before windows installation).if you do not see the entry boot into wubi installation and run **sudo update-grub** in a terminal and you are done.you will see the entry of ubuntu installation (the one before windows ) in the boot screen of wubi ubuntu installation

---

### Post by amjjawad on 2011-11-09
> **mohamedtoma73 said:**
> i can figure a solution.install xp and then install ubuntu inside windows using wubi.

Then what am I suppose to do with this: [SIZE=1][HOW TO Avoid Wubi & Install Ubuntu on USB Drive]("http://ubuntuforums.org/showthread.php?t=1650699")

:)
[/SIZE]

---

### Post by mohamedtoma73 on 2011-11-09
i can figure a solution.install xp and then install ubuntu inside  windows using wubi.in the boot menu of wubi  ubuntu installation you  will see entry of the previosly installed ubuntu(installed before  windows installation).if you do not see the entry boot into wubi  installation and run **sudo update-grub** in a terminal and you are  done.you will see the entry of ubuntu installation (the one before  windows ) in the boot screen of wubi ubuntu installation

---

### Post by mohamedtoma73 on 2011-11-10
sorry if i didnt understand the guestion.blue screen of death mean there is a driver problem mostly to be sata driver
(please read carefully the blue screen and report it) not included in the windows installation.there multiple solutions:
1-try changing ahci mode into ide mode in bios(if fail go to step 2)
2-slipstreaming your sata ahci driver in the windows installation cd (google  how to)
3-change the installation cd into windows xp sp3 or windows 7

---

### Post by Mark Phelps on 2011-11-10
> **mohamedtoma73 said:**
> i can figure a solution.install xp and then install ubuntu inside  windows using wubi.in the boot menu of wubi  ubuntu installation you  will see entry of the previosly installed ubuntu(installed before  windows installation).if you do not see the entry boot into wubi  installation and run **sudo update-grub** in a terminal and you are  done.you will see the entry of ubuntu installation (the one before  windows ) in the boot screen of wubi ubuntu installation

Did you not READ what the OP said? He said he can NOT install XP.  So why provide an answer that that starts out with "install xp"?

Please stop posting this same text over and over in different threads.

---

### Post by Mark Phelps on 2011-11-10
> **leel05 said:**
> my laptop originally had windows 7 os ...

then i installed ubuntu(which worked and is using up the whole HD now) but would like to install my windows xp (full installation disk) ...

i have tried repartitioning for ntfs with ubuntu partitions (dual boot)(only gets the blue screen after the cd boots)

OK, my guess is that the XP CD is of an early version of XP, and you're getting a blue screen because, a laptop with Win7 preloaded (if yours came this way) almost certainly uses SATA controller, not PATA, and the early XP CD does not have (the right?) SATA drivers.  So, after it boots, when it tries to search the hard drives, if fails due to driver errors.

If your PC does have SATA drive, the only way you will be able to install XP will be to obtain a disk that already has the drivers -- since it apparently will not get far enough into the installation process to open the windows that allows you to press F6 and load the drivers.

---

### Post by leel05 on 2011-11-10
> **Mark Phelps said:**
> OK, my guess is that the XP CD is of an early version of XP, and you're getting a blue screen because, a laptop with Win7 preloaded (if yours came this way) almost certainly uses SATA controller, not PATA, and the early XP CD does not have (the right?) SATA drivers.  So, after it boots, when it tries to search the hard drives, if fails due to driver errors.

If your PC does have SATA drive, the only way you will be able to install XP will be to obtain a disk that already has the drivers -- since it apparently will not get far enough into the installation process to open the windows that allows you to press F6 and load the drivers.



thank you this was the most help answer...that just means i need to get windows 7 os now =( but thanks for eveyones help =D:KS

---

