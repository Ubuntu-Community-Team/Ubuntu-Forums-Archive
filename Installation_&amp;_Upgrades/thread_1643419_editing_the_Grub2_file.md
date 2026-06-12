---
title: "editing the Grub2 file"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by gilloz on 2010-12-11
I presently dual boot with Vista Home Premium and Ubuntu 10.04 LTS.  Since the installation of Ubuntu about 8 months ago, my Grub menu at boot up shows all the updates for Ubuntu 2.6.32-24, -25 and -26.  How can I eliminate the first two and only leave the latest update?  The Grub2 menu is getting bigger each time.

---

### Post by karthick87 on 2010-12-11
Install startup manager,
```
 sudo apt-get install startupmanager
```You can find it under System>>Administration>> 

[IMG]http://i.imgur.com/teNnF.png[/IMG]
[IMG]http://i.imgur.com/6viuN.png[/IMG]

In the second screenshot you can select how many kernels to  show.Just keep it on 1.

---

### Post by gilloz on 2010-12-11
Thanks karthick87 for your response.  My Startup Manager does not look like yours.  There are no Appearance or Security tabs in mine. Under the Advance tab, I only have Boot Menu Resolution and Create Floppy.  Nothing else.  Now what?

---

### Post by karthick87 on 2010-12-11
Install ubuntu-tweak,and clean your old kernels,

[ImG]http://imgur.com/ye5uY.png[/IMG]

---

### Post by matt_symes on 2010-12-11
Hi

This might be interesting as well. I have never used it so....

> **Grub Customizer** is a new graphical GRUB2 settings manager. For  now, it only allows you to edit the GRUB2 menu entries: reorder, rename  or add/remove entries. Since these are actually scripts which generate  the boot.cfg file, Grub Customizer changes the actual script order and  then generates a new boot.cfg so if you then run "sudo update-grub",  your customization won't be overwritten.


[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

If you try it post back your impressions.

Kind regards

---

### Post by gilloz on 2010-12-11
OK.  Tried that and no packages are listed.

---

### Post by ryadav on 2010-12-11
edit grub.cfg

make a backup first

sudo cp /boot/grub/grub.cgf /boot/grub/grub.cgf.backup

sudo nano /boot/grub/grub.cgf

look for menuentry and comment them out i.e:

#menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
#        recordfail
#        insmod part_msdos
#        insmod ext2
#        set root='(hd0,msdos1)'
#        search --no-floppy --fs-uuid --set e1791282-9347-4c24-8bfb-be54309d1159
#        echo    'Loading Linux 2.6.35-23-generic ...'
#        linux   /vmlinuz-2.6.35-23-generic root=UUID=68081c72-09eb-446b-b536-b00e2e61eedf ro single 
#        echo    'Loading initial ramdisk ...'
#        initrd  /initrd.img-2.6.35-23-generic
#}

---

### Post by karthick87 on 2010-12-11
+1 on post #7

---

### Post by Oldhacker on 2010-12-12
Installed Grub Customizer with no problem. However, the "Remove" option is grayed out when I highlight one of the entries.

---

### Post by Quackers on 2010-12-12
You can go into synaptic package manager and enter the kernel numbers into the search box. Mark them for complete removal and apply the changes. There will be 2 entries at least for each kernel.

If you edit grub.cfg your changes will be over-written when grub is updated.

---

### Post by matt_symes on 2010-12-12
Hi

> If you edit grub.cfg your changes will be over-written when grub is updated.Very true. Any kernel update or grub update will revert the changes. Any time you need to manually update grub will also overwrite the changes.

Can i make a suggestion? I would keep the last two kernels in case you have a problem. You can then boot into the older kernel.

Kind regards

---

### Post by matt_symes on 2010-12-12
Hi

BTW: This may be an interesting thread for you.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Kind regards

---

### Post by gilloz on 2010-12-12
I want to thank everyone for coming to my rescue.  I finally modified the Grub2 menu by doing what I was suppose to do several responses ago.  When I opened my Ubuntu-Tweak, and clicked on Package Cleaner, I then went to the Right side and clicked on Clean Packages instead of Clean Kernels.  That is why nothing was being listed.  After reading post from matt_symes and went to the link, that is where I realized my error.  I followed through with the instructions shown in the link and I was able to clear my Grub2 menu less one earlier Kernel.  All is good now, thank you all.

Added Note:  Karthick87's post had the image that would have solved my problem at the start.  I just missed it.  I really appreciate everyone's comments and inputs.

---

### Post by Quackers on 2010-12-12
You're welcome. Enjoy :-)

---

