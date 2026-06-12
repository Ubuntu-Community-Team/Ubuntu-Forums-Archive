---
title: "Compact Flash installation trouble"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by tgunner on 2008-07-04
So I'm trying to install ubuntu onto a Compact Flash card. I have an IDE to CF adapter as master on the same cable as the slave DVD drive (my board only has one IDE connector, and all 4 Sata connectors are taken up.) When I try to boot ubuntu, it does it's thing for awhile and then flashes to BusyBox. Then it keeps looping code that reads:
```
ata1.00: status: { DRDY }
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
```

I've tried the "ide=nodma" boot option, but it does not help. Any ideas? :confused:

---

### Post by PmDematagoda on 2008-07-05
Is this while trying to install Ubuntu or trying to boot up an Ubuntu install? If you are trying to boot-up an Ubuntu install, where is it located?

---

### Post by tgunner on 2008-07-05
This is while trying to boot from the CD.

---

### Post by PmDematagoda on 2008-07-05
> **tgunner said:**
> This is while trying to boot from the CD.
Did you check the disc for any errors? Also at what speed did you burn it?

---

### Post by tgunner on 2008-07-05
The disc is fine, I have used it for many installs. Just to confirm, I swapped the CF card with a standard hard drive and installed ubuntu just fine.

---

### Post by tgunner on 2008-07-05
I've tried a few other things including an alternate install, but still no go.

---

### Post by lank23 on 2008-07-05
You might use VirtualBox to install to a CF.  I have done this couple times and works well.

lank23

---

### Post by tgunner on 2008-07-06
> **lank23 said:**
> You might use VirtualBox to install to a CF.  I have done this couple times and works well.

lank23

I use VirtualBox, but how would I go about installing directly to an IDE CF drive without the creation of a virtual hard drive file?

---

### Post by PmDematagoda on 2008-07-06
> **tgunner said:**
> I use VirtualBox, but how would I go about installing directly to an IDE CF drive without the creation of a virtual hard drive file?

I think the issue might be with the CF card itself since those errors you showed are usually due to hard disk/storage read/write errors. Did you check your CF card for any problems?

---

### Post by lank23 on 2008-07-06
tgunner;

only way to write to a CF in Virtual Box is using the virtual hard drive file *.vmdk

Look at section 9.9 of the help file show you how to make a *.vmdk file.

lank23

---

### Post by tgunner on 2008-07-07
I made the .vmdk file and installed ubuntu to the file, but the drive appears to still be empty. Windows shows it at only a few MB used. If this becomes a problem, I might try a new IDE -> CF adapter; mine is pretty cheap.

---

### Post by lank23 on 2008-07-07
tgunner

you can not install to a *.vmdk file.  It is a simple text file that has the layout of the drive to be used by VirtualBox.  You have either made the *.vmdk file wrong or you have install Ubuntu 8.04 to a *.vdi file.

Take a look at /home/your-username/.VirtualBox/VDI/  and look for a *.vdi file that you might have installed Ubuntu too.

If you created the *.vmdk file correct, you can get the CF as a second or primary drive, open VirtualBox and click on 'File', then on 'Virtual Disk Manager'.  Add you CF to the hard drive by clicking on "add" button and you will be prompted for the location of your *.vmdk or *.vdi file.  But you want to find your CF.vddk file that you created.  Once you had added this drive you can now select it in you virtual machine as a primary or secondary drive.

lank23

---

