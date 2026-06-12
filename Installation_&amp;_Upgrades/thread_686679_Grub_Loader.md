---
title: "Grub Loader"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by kjhud on 2008-02-03
I have read around and haven't found anything.

I have a 320GB Passport external HDD that I used vista to partition 10 GB aside for ubuntu on it, I have gotten passed most the of installation but I am at a point where it says 

"The following other operating systems have been detected on this computer: Dell Utility Partition, WIndows Vista/Longhorn (loader), Microsoft Windows XP Embedded

If all of your operating systems are listed above, then it should be safe to install the boot loader to the master boot record of your first hard drive. When your computer boots, you will be able to choose to load one of these operating systems or your new system.

Install the GRUB boot loader to the master boot record?"


I am wanting to put multiple OSs on my external HDD and be able to access them from any computer so what option should I choose? I am not clear of what it says and do not want to mess up the installation.

---

### Post by ph1 on 2008-02-03
The GRUB is basically a list of the operating systems that your computer can use to boot--it comes up as a list, asking you to select one, after the BIOS is loaded.  (I.e. after the Dell loading screen is finished, since it seems you are using a Dell.)

The message is telling you that Ubuntu has detected those other operating systems on your hard disk, and is asking you if there's a problem--for example, if you had XP installed and it didn't appear, then you would have a problem.  If your other operating systems besides ubuntu are all listed (seems to me they are), then go ahead--this will make sure they are added to the GRUB file so that you can access them.

As a note, the GRUB file automatically sets Ubuntu as the default operating system, and gives you 10 seconds to choose.  If you want to change the default OS or the amount of time, you can edit the GRUB file inside your /boot folder--but be careful.  Cutting and pasting the OS you want to be default to the top of the list is the best idea.  (You can just change the number of seconds by changing the number.)

---

### Post by confused57 on 2008-02-03
You don't want to install grub to the master boot record of the first hard drive...this may overwrite your mbr on your internal hard drive & you won't be able to boot your computer without the external drive connected.

There should be an "Advanced" button in the lower right of the final install screen...click this, then type in something like /dev/sdb(or however your Ubuntu partition is recognized by the installer/partitioner)...this should install grub to the mbr of the external drive, then set your bios to boot first to the external drive.

You should get a grub boot menu, highlight your Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it is...this change is temporary, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kjhud on 2008-02-03
thx guys, I had already clicked yes on it but I have loaded vista fine when the external drive wasnt plugged in ( I went to the BIOS and put the USB before the internal HDD)

---

### Post by neonum6 on 2008-02-03
Write 'solved' in thread's name. ;)

---

