---
title: "Installed, but XP is the only OS recognized"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by mmyers on 2008-10-19
I am new to the Linux world and installed 8.0.4 on my Win XP Service pack 3 machine.  in the ubuntu guided setup, i chose to make my XP partition into 50% XP and 50% ubuntu.  The ubuntu installation completed successfully, however the PC always boots into XP and i never get any sort of prompt for which OS i would like.

i searched the forums and i honestly can't follow all the GRUB explanations.  I think i am 90% on the way to being able to use ubuntu if i could just get some help in allowing it to boot from my primary drive.

and yes, i need to keep XP on the machine for some apps that i run, so removing xp is not an option at this time.

thanks to anyone who can help me sort this out.

Mike

---

### Post by caljohnsmith on 2008-10-19
OK, how about first booting your Live CD again, open a terminal (applications > accessories > terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of the above commands, and also:
```
sudo fdisk -lu
```
If the above Grub commands complete successfully, try rebooting and let me know what happens. :)

---

### Post by mmyers on 2008-10-19
ok, i followed your instructions and it came up with hd2,4.

i performed all the commands and rebooted and was presented with the choice of OSes on my box.

BUT...when i selected ubuntu (the first item listed) it gave me Error 22 : No Such Partition

We're almost there...

thanks for your help so far.

---

### Post by caljohnsmith on 2008-10-19
Please read my instructions carefully, it would help if you would still post:
```
sudo fdisk -lu
```
Also, when you used the grub "setup" command, did you use "setup (hd2)"? 

Go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If that doesn't work, then try X = 1 and 2. One of those should work. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to the (hdX,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
If you can get this far, we can then work on booting Windows. Also, be sure to tell me which (hdX,Y) worked to boot Ubuntu.

---

### Post by mmyers on 2008-10-19
here are screenshots from ubuntu running off the cd as screen shot attachments.

i did not try any of your last posting instructions at this point.

my C: drive is labeled "WinXP" and it has an NFTS partition on it for windows that i want to keep.

it looks like ubuntu is installed on sdc5.

---

### Post by caljohnsmith on 2008-10-19
OK, looks good, go ahead and reboot and follow the instructions from post #4 about modifying the Grub menu on start up to boot Ubuntu. That should get you into Ubuntu, and be sure to let me know which (hdX,Y) worked; hopefully it will be (hd0,Y), because that would mean you are booting from the Ubuntu drive, which is most ideal at this point. :)

---

### Post by mmyers on 2008-10-20
ok, i edited the  line in grub to be hd0,4 and hit b and it booted up into ubuntu properly.  did i just get lucky the first time?  so now i should edit and save as you instructed?  at this point i haven't test my xp install to make sure it's still functional.

---

### Post by caljohnsmith on 2008-10-20
Yes, based on those screen shots you posted, the correct (hdX,Y) would be (hdX,4), so if you got (hd0,4) that's great because that means you are booting your Ubuntu drive on start up. So yes, go ahead and modify your menu.lst as given in post #4 so you can make the change permanent. 

Also to boot Windows, since you have two other drives, there is ambiguity which drive Windows will be on as far as the boot order goes; that means that probably the easiest way to boot Windows is to add both of the following entries to the bottom of your menu.lst and see which works:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
One of those should work to boot Windows, assuming you don't have any issues with Windows. Give it a shot and let me know how it goes.

---

### Post by mmyers on 2008-10-21
caljohnsmith,

thanks a lot for your help.  i changed the menu.lst file and now my pc correctly boots into Ubuntu from the hard disk.  I'll see if XP still starts.

I wanted to at least send you that much as my time is limited for tinkering these days.  I think the XP was ok off the grub menu before we made these changes, so i should be set.

thanks.

---

### Post by caljohnsmith on 2008-10-21
That's great news you can boot into Ubuntu now. Also, I forgot you said in your original post that your Windows was on the same machine as Ubuntu; never mind about the previous menu.lst entries I gave for Windows. Probably Windows will boot fine like you say, but if you get any Grub errors booting Windows, try the following entry:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Anyway, cheers and have fun Ubuntu-ing. :)

---

