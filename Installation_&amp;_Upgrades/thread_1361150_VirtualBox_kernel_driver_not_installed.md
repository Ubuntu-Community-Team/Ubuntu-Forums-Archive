---
title: "VirtualBox kernel driver not installed"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by caradeporra on 2009-12-21
I have been scanning the forums all day and have not found a solution. 

The issue i seem to be having is when virtualbox 3.1 installs (or virtualbox 3.0 for that matter), it tries to run linux-headers-'uname -r' which for some reason tells it to look for kernel release 2.6.28-15-generic.  i have version 2.6.31-17-generic.  

I have uninstalled and reinstalled several times with no fix.  The virtualbox-ose installed fine.

---

### Post by snowpine on 2009-12-21
Please post the output of:

```
uname -r
```

You might also want to:

```
sudo apt-get install dkms
```

for future convenience updating your modules when you upgrade the kernel.

---

### Post by caradeporra on 2009-12-21
dkms is already installed.  the uname -r is 2.6.28-15-generic.  This is the issue i believe, but I am not sure how to adjust this.

---

### Post by snowpine on 2009-12-21
It's possible 2.6.31-17-generic is *installed*, but you're not running it.

Choose the correct kernel from your GRUB boot menu.

Let's back up a second though and let me ask you this: Is VirtualBox working OK, and if not, what happens?

---

### Post by caradeporra on 2009-12-21
Virtualbox will start up correctly.  once i try to start the virtual machine (i was able to create the virtual machine but never start it - so it is not loaded or anything.) it throws the error telling me to run the /etc/init.d/vboxdrv setup.

when the setup is run it is looking for a file in the 2.28.6 directory (the older directory is still in tact.

---

### Post by snowpine on 2009-12-21
This should get you going:

```
sudo apt-get install linux-headers
sudo /etc/init.d/vboxdrv setup
```

---

### Post by caradeporra on 2009-12-21
ok, before i try that, the old kernels were the only one available in the boot menu - I need to add the new kernels to the menu.lst file.  I am going to do that first.  When i updated to 9.10 i didnt update that file because i didnt want to mess up my dual boots.

---

### Post by caradeporra on 2009-12-21
ok, i added the new kernel to the boot menu and have booted off of that.  Thats enough for today, i will pick it back up in the morning.  Really appreciate all the help and quick responses!  I'll let you know how it goes tomorrow.

---

### Post by snowpine on 2009-12-21
I understand now. :)

I am not a GRUB expert but it sounds like you are way ahead of me :)

Tomorrow we can solve the VirtualBox problem.

---

### Post by caradeporra on 2009-12-22
SnowPine,

  You hit the nail on the head.  I knew the problems were with the headers but I did not know that those were changed in the Boot menu.  

  I am posting the solution for future references to other users.  I appreciate all your help.

  I did
```
sudo gedit /boot/grub/menu.lst
```

  and copied the existing Linux entry, for both normal and recovery mode, so that if I messed up I would still have the original entries.  I then changed the kernel in the entry to my current kernel, and I also changed the initrd to the latest kernel as well.  So my menu.lst went from:

title   Ubuntu 9.10, kernel 2.6.28-15-generic
uuid    xxxxxxxxxxxxxxxx
kernel  /boot/vmlinuz-2.6.28-15-generic root=uuid=xxxxxxxxx
initrd  /boot/initrd.img-2.6.28-15-generic

and then copied it to look like this:

title   Ubuntu 9.10, kernel 2.6.31-17-generic
uuid    xxxxxxxxxxxxxxxx
kernel  /boot/vmlinuz-2.6.31-17-generic root=uuid=xxxxxxxxx
initrd  /boot/initrd.img-2.6.31-17-generic

before changing this, I navigated to the /boot folder and made sure I had the vmlinz and initrd files.

 I then rebooted and chose the new entry from the grub menu and logged in, I then re-ran
```
sudo /etc/init.d/vboxdrv setup
```
and it ran correctly. Opened virtualbox and started up a session and it is working.

  If any one who knows more about the grub menu has any advice, or thinks there is a better way or more proper way - please chip-in your 2-cents!

Thanks SnowPine!

---

