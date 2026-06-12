---
title: "grub doesnt detect windows 7 after karmic install"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rixtr66 on 2009-09-17
i installed karmic from a cd and it works fine,however it didnt detect my windows partition as usual ubuntu installs do.my question would be how do i manually write the windows partition into the grub menu?
its been awhile since ive used ubuntu so im a little rusty!
any help would be greatly appreciated!
Rick ](*,)
upon further exploration ive found that the menu.lst is blank?so now im really lost!
maybe im not typing the right command?sudo gedit /grub/menu.lst?im currently looking at another thread that is similar,but i dont have the same knowledge.
this is how the partitions are setup;dev/sda1-ntfs(seems to be unreadable)dev/sda2-extended,dev/sda5-ext4,dev/sda6-swap,again any help would be appreciated.

---

### Post by alien21010 on 2009-09-17
To fix this, edit the file in /boot/grub/menu.lst.  Within that file there should be a couple of listings for various Ubuntu kernels, etc.  At the bottom add the following lines:

title Windows 7
root (hd0,2)
savedefault
makeactive
chainloader +1 

In the line root(hd0,2), replace 0,2 with the number of your disk (starting from 0) and the number of the partition that Windows is on (starting from 0).  You might have to guess around a few times to figure out what number it is...  So if your Win 7 install was on the 4th partition of the 2nd hard drive it would be root(hd1,3).  For you, it looks like your Win 7 install is at root(hd0,0).  Try that first.

If you reboot and it complains that it cannot find that hard drive, then select the Windows 7 title in the Grub list, and press "e".  This will take you to an editable screen, press "e" again on the root(hd_,_) line, and change the numbers.  Then press "b" to try booting into that partition.  If it fails, it will drop you back to the main GRUB screen, from which you can try again.  Once you find and successfully boot into your Win 7 partition, then permanently edit /boot/grub/menu.lst to get it to boot there permanently!

That should do it.

---

### Post by rixtr66 on 2009-09-17
thank you alien21010,thats what i was looking for,but also im leary of adding the lines as there is nothing in /boot/grub/menu.lst?
keep in mind im running ubuntu 9.10 karmic.if i put this in it will be the sole entry,so how will i boot into ubuntu?im a little perplexed as ubuntu has always had the /grub/menu.lst,and has always picked up windows.so i guess i have to make a menu.lst?but dont know how.:confused:
now what?
Rick

---

### Post by QIII on 2009-09-17
On a fresh install, Karmic uses GRUB2, and menu.lst is meaningless.  GRUB2 doesn't use menu.lst.

Even still, the latest Alpha needs some help

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```

Here are some other peoples' suggestions:

[https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/402795](https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/402795)

---

### Post by rixtr66 on 2009-09-17
Thank you ,that worked!!!!!!!!!!!!!
didnt know about the grub 2.0 stuff.
thanks again!!
Rick:guitar:

---

### Post by basec0m on 2009-09-18
Just wanted to confirm this works... thanks

---

### Post by skinnie on 2009-09-22
thanks a lot :) it help me too!

---

### Post by leoave on 2009-09-24
> **QIII said:**
> On a fresh install, Karmic uses GRUB2, and menu.lst is meaningless.  GRUB2 doesn't use menu.lst.
Even still, the latest Alpha needs some help


Yes just installed daily build from sep-23 and it did not got my xp on grub, but running
```
sudo update-grub
```
fix it

---

