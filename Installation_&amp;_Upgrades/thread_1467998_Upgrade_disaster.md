---
title: "Upgrade disaster"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by PeregrinGo on 2010-05-01
Hola chavos:

I was trying to update from 8.04 to 10.04 using the recommended method outlined below. I got to -- quite literally -- the last few minutes of the upgrade, and my computer apparently overheated and shut itself off. When it had cooled enough to try a restart, I get an error message and I'm left with the **_intrafms prompt_**. I have absolutely no idea where to go from here. Should I just download and burn the live CD .iso? Will I still be able to preserve my files, etc? I can still access the file structure from the Windows side.

Any tips or fixes?

> Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Press Alt-F2 and type update-manager --devel-release
   2. Click the Check button to check for new updates.
   3. If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   4. A message will appear informing you of the availability of the new release.
   5. Click Upgrade.
   6. Follow the on-screen instructions. 


---

### Post by PeregrinGo on 2010-05-01
92 Reviews and no responses? Please help! Anyone?!?!?

---

### Post by ieee488 on 2010-05-01
Unless someone more knowledgeable comes along with a better idea, I would back up your files when booted to Windows to a USB flash drive, then do a clean install.

---

### Post by Rasa1111 on 2010-05-01
hi peregrinGo , 

 I dont think i can offer much help but to bump your thread back to the top.

 I do know that an install from a liveCD would probably be better though. 
(it is faster).. less time to overheat.. maybe? 

 Im not sure about your old files though..
but i think if you can access them through windows side.. you should probably back them up, and then try the install...

but please, dont go on my words.. 
probably best to wait for someone who knows better than i. 

 good luck mate

---

### Post by linuxnoob420 on 2010-05-01
okay you can try this i will try to help you save your files start a live cd once your in the live desktop go to places you should see your ubuntu and windows partitions e.g 80gig file system and 100 gig i don't know what your scheme looks like any way you should be able to click and drag your ubuntu files to any were you like then do a clean install

---

### Post by AlanR8 on 2010-05-01
From the live CD you should be able to open a terminal window then:

> sudo mount -a

That should give you access to your files that you can the save elsewhere. 

Have to ask why you didn't do that before the attempted upgrade?

---

### Post by ChadMMc on 2010-05-01
Question: Do you have your /Home as a separate partition? If so, then you can reinstall to your hearts content and your private files, configs, etc. should be safe.

---

### Post by PeregrinGo on 2010-05-01
Thanks for those who have offered their advice. And to those who have questioned why I didn't back up my files, I should clarify:
I have access to my all my files through either the live CD or my Windows partition. In addition, I have a backup USB hard drive. The doubt that I wished to express was whether or not I would be able to continue the **upgrade**, as opposed to a fresh install, and, thus, maintain all of my files and, to some extent, the numerous modifications I had made.

In addition, I did attempt, on SEVERAL occasions, to make a custom live CD with remastersys, but I continually received an error saying that there was just entirely too much data to create an .iso. And that's despite the fact that I moved all of my photos and videos to the aforementioned backup USB hard drive.

Ugh. I wouldn't have bothered to upgrade had I know this would happen. I was perfectly happy with HARDY.

---

### Post by PeregrinGo on 2010-05-01
This is actually an excellent idea, and given that my original home folder has been preserved, perhaps I should take advantage of this situation in order to convert my preserved home folder into a home / shared files partition. Although I'm certain many people have done so, I never really ran across a post, blog, or site strongly advocating that, so it didn't really cross my mind.

> **ChadMMc said:**
> Question: Do you have your /Home as a separate partition? If so, then you can reinstall to your hearts content and your private files, configs, etc. should be safe.

---

### Post by PeregrinGo on 2010-05-03
~bump~

---

### Post by antiram on 2010-05-03
You could overtake the installation from a livecd with eg (sda5 is your /, sda1 is /boot):

sudo mount /dev/sda5 /mnt
sudo mount /dev/sda1 /mnt/boot
for fs in proc sys dev dev/pts; do sudo mount --bind /$fs /mnt/$fs; done

overtake with:
sudo chroot /mnt

Your installation is not finished? Then do it now from the chroot enviroment:
apt-get update
apt-get dist-upgrade

or if only the /boot/initrd.img-xxxx is unfinished then
update the initrd (some or all) with:
update-initramfs -u -k all
for all initrds or only one with:
update-initramfs -u -k 2.6.32-21-generic

---

### Post by uncleV on 2010-05-03
> **PeregrinGo said:**
> 92 Reviews and no responses? Please help! Anyone?!?!?
While waiting here you can ask Canonical's too :)
[https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

I saw there similar questions once upon a time about upgrading to 9.10 directly from distros like 7.* and 8.*. They said this is not a good idea.

---

