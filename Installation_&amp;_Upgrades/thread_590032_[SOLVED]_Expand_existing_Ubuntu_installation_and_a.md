---
title: "[SOLVED] Expand existing Ubuntu installation and add separate /home partition"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-10-24
Ok, after some searching through the forums I have found a guide to create a new /home partition to replace the default one installed under / . However, before I proceed I have a few questions:

1. I am not familiar with partitioning, how do I figure out which partitions on the drive Gutsy is on/using?
2. I have a 40GB Western Digital Caviar HDD, most of it (not sure how much) is used for Gutsy but I have a smaller partition that has Wolvix on it. I don't want to erase any part of the Wolvix install, but I would like to resize it (I think it is 10GB and I want to resize it to 3 or 4GB). How do I figure out which partitions Wolvix is using and resize them accordingly?
3. If I am making my Wolvix install smaller, do I also need to resize its swap partition?
4. I haven't had luck with GParted on a LiveCD (it never seems to finish searching for partitions), if I use QTParted that should suffice correct? Does anyone know of any issues using it?

Any other advice you can give would be greatly appreciated! Thanks everyone!!!

---

### Post by elmagno on 2007-10-24
The "df -h" command will show the current devices, sizes and mountpoints. But you'll need gparted or acronis to resize.

It sounds like you have a gutsy installation now? If so, what about running gparted (gksudo gparted) from your current install? At least you could resize your wolvix partition this way. I have also had good luck burning a gparted iso and booting that, but it sounds like you have tried that.

---

### Post by JawsThemeSwimming428 on 2007-10-24
Ok, like I said I am not very good with partitioning. Basically, what I want is Ubuntu to be most of the drive. I would like to use about 35GB for Ubuntu, however I would like to have a separate /home partition. I am not sure what I need to do. I have attached a screenshot of the output from QTParted (GParted does not ever work for me). With the partitions shown, how do I resize my Wolvix partition to allow for Ubuntu to occupy 35GB? 

I know I need a swap partition, a /home partition, an Ubuntu partition, a Wolvix partition, and a swap for Wolvix. I'm pretty sure sda3 is Ubuntu and sda1 is Wolvix. I do not know which swap is which and what I should resize them to? And I have no idea what sda2 is (extended)?

---

### Post by elmagno on 2007-10-25
Well, QTparted doesn't work for me but gparted does! (Qtparted comes up on my screen about two desktops wide). But here are some suggestions for proceeding:

1) Yes sda1 seems to be your Wolvix partition and sda3 is your Ubuntu. Sda2 is the extended partition that holds your two swap partitions.

2) I looked over the QTparted site, and it seems like the author is saying that what you want to do requires booting the program from a Live CD with QTparted on it. He suggests SystemRescueCd:
[http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)

3) Right now you've got about  8GB free on the Wolvix partition and 20GB free on Ubuntu. You'll have to decided how much to resize (downsize) the Wolvix partition. You will them resize (upsize) the Unbuntu partition will the amount you have freed.

4) You can gain some space by deleting  one of the swap partitions.
Edit both the Wolvix and Ubuntu fstab file to indicate the same swap file. For instance, keeping the 1.5GB swap would require this line in Ubuntu:

/dev/sda6 none swap sw 0 0

(Not sure about Wolvix).

So that's three operations in QTparted (or gparted) from a live cd.

5) I can't tell you all the steps for creating a separate home partition, but you said you've got instructions for that already. 

Generally what has to happen is that from the QTparted live cd, you'll be making another (ext3, I presume) partition from some of the free space you get from downsizing. 

Then you'll add a fstab line to mount it. But that's just the general procedure.

---

### Post by JawsThemeSwimming428 on 2007-10-26
Change of plans... I think what I am going to do is get rid of my Wolvix partition altogether. So what do I need to do to keep my existing Gutsy install but use the entire drive and have a separate /home partition?

---

### Post by JawsThemeSwimming428 on 2007-10-27
Can anyone help me out?

---

### Post by JawsThemeSwimming428 on 2007-10-29
OK... I reinstalled Gutsy fresh so I could try the psychocats walk through for creating a separate /home partition in an existing install. I booted up the LiveCD after I installed and fire up GParted. GParted did not finish scanning! I let it scan for an hour!!!!! I have tried to use GParted before and it has never worked. I don't understand because everything I read about it says it is an amazing tool but it has NEVER once worked for me! So,  that being said... I just left my install the way it is until I can think of something else to try. Thanks for trying!

---

