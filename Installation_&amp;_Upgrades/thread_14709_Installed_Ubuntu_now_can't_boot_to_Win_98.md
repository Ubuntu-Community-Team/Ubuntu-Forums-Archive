---
title: "Installed Ubuntu now can't boot to Win 98"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by BarbiGirl8 on 2005-02-09
I have a 30gb hdd. 15 gb for Windows 98Se and 15gb free space. I ran the installer on the 15gb of free space and let the installer determine the best way to partion it. Installation went just fine. But now when I reboot I can't get to Windows 98. After doing some reading in the forums I am thinking that I need to do an fdisk /mbr in order to get Win 98 back up, but won't that mean that I will loose the ability to boot up to Ubuntu?

I would love to find a way so that I can do a couple of tweaks so that I can have the MBR prompt me to what OS I want to launch. And belive it or not Win 98 being the default if no choice is made. 

If this isn't possible, then just help me be able to get back into Win98.

---

### Post by Sye d'Burns on 2005-02-09
Check out [Ubuntuguide.org](http://ubuntuguide.org/#addwindowsentrygrubmenu)  for many, many helpful hints (including this one) 

All you should need to do is edit your /boot/grub/menu.lst 

>       $ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
      $ sudo gedit /boot/grub/menu.lst

Append the following lines at the end of file

      title           Windows 95/98/NT/2000
      root            (hd0,0)
      makeactive
      chainloader     +1
      savedefault
  
Save the edited file (sample)

---

### Post by lao_V on 2005-02-09
Also, you may need to press the ESC key to see the GRUB menu after switching on. You have to be quick as I think the default for this is only 2 secs.

---

### Post by BarbiGirl8 on 2005-02-09
IT WORKED IT WORKED IT WORKED!!!!. I even finally figured out not only how to get the Dual boot to work properly. I'm also surfing from linux right now \\:D/  \\:D/  \\:D/ I'm soooo happy.

---

### Post by lao_V on 2005-02-10
And how did you managed to do that?

---

### Post by BarbiGirl8 on 2005-02-11
I just followed the steps outlined above and it allowed me to boot up.

---

