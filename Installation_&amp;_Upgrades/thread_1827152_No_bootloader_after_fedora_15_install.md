---
title: "No bootloader after fedora 15 install"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by jfed on 2011-08-17
Hello, I have seen multiple others with this problem, I now have it too. I had Ubuntu 10.10 installed on my entire disk, then I installed Fedora 15 with it. The resizing-the-disk went smoothly, everything is great, but now when I turn on my machine, I get no grub, no boot loader, nothing. I just get thrown right into Fedora. I saw on a few other posts that if you manage to get into Ubuntu, you can open a terminal and type something along the lines of sudo grub update, and that would do the trick. The only issue is that I can't even get into ubuntu. I also was told that if you boot from a livecd you can edit the boot config, or view it, or something. I'm pretty new to all this "bootloader grub" jazz, and am hopelessly confused. How do I make it so that upon startup, I am able to choose between Ubuntu and Fedora?

Any input is apreciated, thanks in advance.

---

### Post by YesWeCan on 2011-08-17
Hi there. It is because fedora's boot-loader code (legacy Grub) over-wrote Ubuntu's boot-loader code (probably Grub2) as they occupy the same disk area. The trick would have been, and there is no way you would have know to do this, to install fedora without installing Grub and then boot Ubuntu and run 'sudo update-grub' to add fedora to Ubuntu's Grub menu.

Ways to fix Ubuntu's Grub are here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) in Section 12, assuming your 10.10 is using Grub2.

---

### Post by Elfy on 2011-08-17
Alternatively you can add ubuntu to the fedora bootloader or [even install grub2 to it]("http://forums.fedoraforum.org/showthread.php?t=262670").

---

### Post by jfed on 2011-08-17
I followed the guide YesWeCan posted, and used Boot Repair and ran the First Repair option. Now when I boot up, I have grub again, but no option listed for Fedora, only Ubuntu. I was going to run the Second Repair option, but evidently I have to remove all my GRUB 2 files from /boot/grub. Then it nicely tells me that my system would be then unbootable if i don't install another bootloader. I thought this was implying that it was going to re-install grub,  but i'd rather not take my chance.

So I don't think I can add Ubuntu to Fedora's loader now, because I can't get into Fedora anymore.

I'm still hopelessly lost. :(

---

### Post by drs305 on 2011-08-17
jfed,

For now, just don't do anything rash. Someone familiar with Fedora's boot process will come along and either tell you what to put in the Grub 2 40_custom file or how to chainload into Fedora's boot loader so you will be able to get a working Fedora menuentry in the Grub 2 menu.

---

### Post by jfed on 2011-08-17
Well if you insist. I have no problem wiping my disk and reinstalling both operating systems, because it seems the root of my problem stems from installing Fedora incorrectly. Or I could just wait like you said. :p

---

### Post by drs305 on 2011-08-17
> **jfed said:**
> Well if you insist. I have no problem wiping my disk and reinstalling both operating systems, because it seems the root of my problem stems from installing Fedora incorrectly. Or I could just wait like you said. :p

It's obviously up to you, and how much time you want to spend either waiting or reinstalling.

You could do a search for "Fedora menuentry" and you would probably find an example of what to put in /etc/grub.d/40_custom. Since 'menuentry' is unique to Grub 2 and not Grub legacy, you would probably find an example if it can be done this way. 

If you find one, you would just need to change the 'set root' line to the proper drive/partition and edit the 'linux' line to make sure the UUID or other reference pointed to the correct partition.

---

### Post by jfed on 2011-08-17
Would it be possible to just delete my Fedora partition all together using a program like gparted? That way I could just go back to using Ubuntu alone, and perhaps try Fedora some other time.

By the way, thanks for all your help.

---

### Post by YesWeCan on 2011-08-17
Hi again. fedora 15 uses LVM and this makes it is easy for update-grub to recognize it. You have to install LVM in Ubuntu first and have it activate the fedora volumes.

sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub
sudo grub-install /dev/sda  (assuming your disk is named sda)

and watch the output of update-grub to see that it lists fedora

---

### Post by jfed on 2011-08-18
Really? Thats it? :D

And yes, I believe my hard drive is /sda. I can just make sure through gparted.

Well, I'll do that. And report back here, hopefully this will fix my problem. Thanks for all your help!

EDIT
Okay well everything was going great, I ran all the commands you said to. And I did watch the output from update-grub, and sure enough, Fedora was listed! Yay me. So then I ran grub-install, and it told me the installation failed, and said there was also no error report. "Great." I thought. I actually posted that here, but then I decided to just give my computer a reboot, and there it was.A Fedora option listed at the bottum of my boot menu. So in other words, everything is solved.

Thanks everyone for helping me so much, especially you YesWeCan.

---

### Post by YesWeCan on 2011-08-18
Good stuff. I should have suggested this earlier in the thread but although when I installed fedora I used this LVM detection method, I wasn't sure whether it was necessary or not because I never tried without it. Fiddling about with Grub config files leaves me a bit cold. ;)

---

### Post by dmbtimmyb212000 on 2011-08-19
> **YesWeCan said:**
> Hi again. fedora 15 uses LVM and this makes it is easy for update-grub to recognize it. You have to install LVM in Ubuntu first and have it activate the fedora volumes.

sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub
sudo grub-install /dev/sda  (assuming your disk is named sda)

and watch the output of update-grub to see that it lists fedora

Avid ubuntu-user (Pinguy OS 10.04.3 LTS) who wanted to give gnome3 a whirl w/ Fedora 15.  Actually prefer it over Unity.  I am very savvy w/ Linux (ubuntu especially) but I had all the same aforementioned problems as original poster. 

Your solution worked perfectly!!  Thanks very much.  The only thing I did different was running step 4 before step 3 (grub-install /dev/sda, THEN update-grub).  

open your source.  open your mind.  :D

---

### Post by jfed on 2011-08-19
> **dmbtimmyb212000 said:**
> Avid ubuntu-user (Pinguy OS 10.04.3 LTS) who wanted to give gnome3 a whirl w/ Fedora 15.  Actually prefer it over Unity.  I am very savvy w/ Linux (ubuntu especially) but I had all the same aforementioned problems as original poster. 

Your solution worked perfectly!!  Thanks very much.  The only thing I did different was running step 4 before step 3 (grub-install /dev/sda, THEN update-grub).  

open your source.  open your mind.  :D

lol really? I hate both unity and gnome 3! I haven't updated either my mintbox or my ubuntubox to 11 yet haha, i'm going to be moving to xfce i think, gnome three is too user friendly for me =;

---

