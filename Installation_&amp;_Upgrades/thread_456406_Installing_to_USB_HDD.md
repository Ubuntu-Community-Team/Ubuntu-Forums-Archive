---
title: "Installing to USB HDD"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by geoffers1 on 2007-05-27
I really need some help in trying to get Ubuntu working on an external USB HDD.

I have an IBM T43 latop with XP installed on the internal HDD.  As I'm new to Linux I thought I'd play safe and install to a USB HDD.  The installation of Ubuntu goes fine (of sorts after playing with disk partitioning!!) and everything installs fine. Rebooting after the install and everything is fine, Ubuntu boots off the external HDD and I can play about to my hearts content.

My problem comes when I switch off the laptop and come back to it at a later date.  With the USB HDD plugged in the laptop hangs at power up and won't boot off USB HDD.  I can boot off the GParted LiveCD, plug in the USB HDD and read everything fine, check the disk for errors and all is fine, reboot the laptop and Ubuntu might load, might not and just hang.

It really seems to be pot luck if I can boot off the USB HDD. I've tried many reinstalls now and each time I have this problem.

Does anyone else have this issue, or has anyone resolved it?  The only way I can see of doing it is to keep swapping the internal laptop HDD but I'm reluctant to do that as I'm likely to break something.

Thanks in advance.

---

### Post by DerHesse on 2007-05-27
Hi geoffers1.
Have you tried "F12" to select the boot device? If USB-HD is not available you need to enable it in the bios. 

My T43p works fine in dualboot, I can recommend it.

---

### Post by geoffers1 on 2007-05-27
I've sorted out the boot order. It's really frustrating that it works for a while.  I'm usinf 2.5" 60Gb disk in an ide to usb caddy. I've got 2 different disks and 2 different caddies. Are these good enough???

---

### Post by DerHesse on 2007-05-27
Have you tried to take the internal disk out before installing linux to usb?
Afterwards you should be able to boot ubuntu whenever the external disk is plugged in at boot.

Maybe your usb-drive consumes too much of electricity during startup, maybe you can try a Y-Conncetor to get more power to the device.

---

### Post by CocheseUGA on 2007-05-27
I don't know if this will help you or not, but I thought I'd share:

When I went to install Feisty Fawn on an external USB HDD (because my laptop's CDROM doesn't work), I had to edit the device.map and menu.lst files. It was because when I installed on the USB HDD, it saw it as the 3rd HDD (hd0,2 instead of hd0,0). Once I edited both files to show GRUB to load Linux off of the base HDD, I was golden. You might want to do check those files out for yourself and see if there are any conflicts. Of course, I was getting a Error 21 message though.

Just another idea.

---

### Post by geoffers1 on 2007-05-29
I'm not sure what is going wrong with my install. I can install to the USB HDD no problems with the Live CD, do a restart and everything works fine off the USB HDD.

The problem only occurs when I power off the laptop.  Plugging the USB HDD in then powering back on prevents the laptop booting up, and it hangs at the initial IBM splash screen, or it boots off the internal HDD into XP.

I have tried a different harddisk, but I'm guessing it might now be down to the USB enclosure I'm using for the disk. I did buy a cheap one off eBay which was doing this, so I bought another one and this still does the same.

If I trash the disk and format it to NTFS under XP I can then boot the laptop with the USB HDD connected, it just gets ignored, so this confuses the issue too.

One last thing, in the BIOS when I change the boot order, the USB HDD option is listed as -USB HDD (with the preceeding minus sign). Nothing else in the BIOS is preceeded with the minus sign.

I've tried a Y cable USB cable, as well as a single cable, both have this issue.  I might try a powered IDE to USB converter that I have with a 3.5" Seagate disk and see what that throws up.

Any thoughts from anyone else?

---

### Post by DerHesse on 2007-05-29
your built in harddrive is SATA. Once booted to linux from USB, your USB should be sdb, not sda.
Am I right? 
check ```
$ cat /etc/fstab
```

---

### Post by geoffers1 on 2007-05-29
Thats more or less right. All my disks are recognised as SDX, the internal being SDA and the USB disk as SDB.

---

### Post by gn2 on 2007-05-29
I've had this problem before, and it seemed to be that the USB hard drive didn't power-up fast enough to be recognised by the BIOS as a bootable device before being passed over and the internal drive booted.

Cured by using a powered 3.5" USB, but even then it sometimes wasn't detected in time.

---

### Post by CocheseUGA on 2007-05-29
Good point. You could try setting your boot order to anything and everything, then the USB, then finally the main internal drive. Perhaps it would give it the crucial second or two it needs.

And in a clarification to my previous post, you could be having a boot order issue with the USB HDD itself. Check the two files I mentioned above. Make copies (or print) those files and delete where it mentions the internal HDD, and switch the USB HDD to (0,0) but don't change sdb to sda. See if that works. Won't harm anything if it doesn't, and you can do this off of the LiveCD. When I was verifying my install to my laptop, I had my HDD setup the same way you do. I had to edit these files to get it to boot off of the USB HDD.

If it works, then you you're golden.

---

### Post by DerHesse on 2007-06-06
I was curious, so tried it myself.
Funny enough I do have sdb (USB) and hda (which is SATA and shold be sda), but NO sda.
After updating a newer kernel my menu.lst is messed up so I had to change by hand.

But I am golden, anyway ;)

---

### Post by Hugh Nano on 2007-06-07
I'm having troubles with this too. I've installed both Ubuntu and Xubuntu to an external HDD, and even edited the Grub menu.lst file to specify (hd0,0) as noted here, but every time I try to boot my Inspiron 6000 from the HDD, it hangs - even if I select booting from USB HDD from the F12 boot menu! Any tips or pointers would be much appreciated!

---

### Post by logos34 on 2007-06-07
.

---

### Post by logos34 on 2007-06-07
> **Hugh Nano said:**
> I'm having troubles with this too. I've installed both Ubuntu and Xubuntu to an external HDD, and even edited the Grub menu.lst file to specify (hd0,0) as noted here, but every time I try to boot my Inspiron 6000 from the HDD, it hangs - even if I select booting from USB HDD from the F12 boot menu! Any tips or pointers would be much appreciated!

Hugh, have you tried this from post #10 above:
> Good point. You could try setting your boot order to anything and everything, then the USB, then 
finally the main internal drive. Perhaps it would give it the crucial second or two it needs.

If it's not a hardware issue, then did you remember to edit device.map file in addition to menu.lst in the same directory? Could also be an error in the menu.lst.

Why don't you just run 

cat /boot/grub/menu.lst
cat /boot/grub/device.map
sudo fdisk -l

and post it.

That'll give us an idea what's going on.

If, for instance, your internal hard disk is IDE, then your device.map file needs to read thus:
[B](hd0) /dev/sda
(hd1) /dev/hda[/B]

---

### Post by geoffers1 on 2007-06-08
Guys, thanks for all the suggestions and advice. I have now got this sorted. I got myself an externally powered caddy for my harddisk and everything is now fine.

It looks like disks powered by the USB port don't spin up in time to boot from, regarldess of the boot order in the BIOS. Thats explains why booting off the LiveCD sees the disk everytime and can use it and install to it, but a reboot powers the USB port off thus the problem reoccurs.

For anyone trying to install to an external disk, I'd fully recommend an externally powered device, or just get a bigger internal disk and dual boot from that!

---

### Post by minispalla on 2007-07-04
ok i have been have this same problem when i install feisty on a eternal harddrvive the install goes good or so i though and when i go to boot it on my pc it restarts and i just see the word GRUB and nothing happens ( by the way i installed it on my laptop through the external enclosure and i took out the internal drive so it would install the grub on my external drive then i put it in to my big pc which can actully boot from a external usb device) 

any suggestions  ? did i forget something small ? 

ps installed the grub thing like 4 times and formated and reinstalled 2 times sooo yeah i am clueless at this point 
i would love any help with this

---

### Post by minispalla on 2007-07-04
could i get some help please ?

---

