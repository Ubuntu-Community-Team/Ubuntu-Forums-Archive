---
title: "ubuntu and win 7 dual boot, grub menu never show up"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by unclesam.xu on 2011-10-31
Hi, I have been using ubuntu for 4 yesrs and never see problem like this.

I recently assembled a new pc. just put win 7 on it. next step is put ubuntu on it because I am mainly using ubuntu daily . No matter I choose custom install or default install , when it is done, restart, computer only boot into win 7 directly , the grub menu never shows so I have no chance go into ubuntu. I installed easyBCD in win 7 it won't help neither. 

please see if any one know this problem.

I don't want to use win 7 everyday.

sam

---

### Post by zghawking on 2011-10-31
I am trying a similar setup, except that installation fails to install Grub onto /dev/sda5 (a partition i made for /boot) see this thread: [http://ubuntuforums.org/showthread.php?t=1773665]("http://ubuntuforums.org/showthread.php?t=1773665")

I tried adding the entry for Ubuntu using EasyBCD but it just takes me to a prompt: grub>

---

### Post by oldfred on 2011-10-31
@zghawking Please start your own thread & include EasyBCD in title  and output of boot script. I do not know Easy but a few here do.

@unclesam.xu
Post this so we can see what is installed where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by raja.genupula on 2011-10-31
Hi small confirmation ,  have you tried to hold up shift key while you boot up for GRUB menu ?

---

### Post by unclesam.xu on 2011-10-31
no, I didn't hold any key. I tried use this guy's help to manage to get the grub 2 shows :

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

I applied his #2 method, I have to regenerate grub.cfg file because withtout doing it , grub only shows a grub=>. 

when I regenerate the grub.cfg. after I type "chroot /mnt update-grub
", system only report it found windows 7, and then I reboot, win 7 is back as a menu item , but still no ubuntu 11.10. 

This is really funny because I did it in ubuntu live cd mode. I use ubuntu live cd to get my win 7 back but still can't load into ubuntu 11.10

---

### Post by raja.genupula on 2011-10-31
Hi man 
     Look at my signature for grub recovery and i am sure that gonna help you.

All the best.

---

