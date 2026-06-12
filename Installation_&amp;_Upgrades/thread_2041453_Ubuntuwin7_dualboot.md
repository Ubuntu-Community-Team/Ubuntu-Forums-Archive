---
title: "Ubuntu/win7 dualboot"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by Kaail on 2012-08-12
I'm trying to dualboot ubuntu and windows 7 and I found this little gem in the archives. However when I type the first bit into the Terminal, it comes back with "cp: cannot stat `menu.lst': No such file or directory" What should I do?

> You're easiest off if you make Windows drive slave and Ubuntu drive  master. Then open terminal (Applications->Accessories->Terminal)  and type
     
Code:
     cd /boot/grub sudo cp menu.lst menu.lst_backup sudo gedit menu.lst 
and paste the following lines in the very end of that file.
     
Code:
     title           Windows root            (hd1,0) savedefault makeactive map             (hd0) (hd1) map             (hd1) (hd0) chainloader     +1


---

### Post by darkod on 2012-08-12
Those instructions are very old. The menu.lst doesn't exist any more with grub2. These days ubuntu can pick up windows automatically and create the dual boot grub2 menu.

Are you having problems getting the dual boot menu? What exactly isn't working?

---

### Post by Kaail on 2012-08-12
I don't get a dual boot menu. Ubuntu just loads up straight away. I've got ubuntu on a master drive and win7 slave. Thanks for the fairly quick reply :)

---

### Post by darkod on 2012-08-12
Are they on one hdd or you have more? Was the windows disk connected during install?

The first thing to try is to boot your ubuntu, open terminal and try:
sudo update-grub

That should scan and detect all present OSs. If it doesn't detect windows, its boot files might be missing because in reality it detects the boot files only.

---

### Post by phalantice on 2012-08-12
The grub2 system has a section in etc where you can customise the menu list.  

If it boots straight to ubuntu and you dont see grub either A grub got installed on the win7 drive or didnt properly install to the primary mbr if the update did not fix it you may need to start grub up from the cmd prompt and have it reinstall to the ubuntu     "sda" drive mbr.  

I almost forgot.  if you have an invalid entry in the menulist file it does that where it will skip straight to the default os.  as stated above the update command should resolve that issue. we dont have to manually edit most primary files any more  the distro's are starting to get that way with every thing.  if the update misses win7 and you get a boot menu with just linux partition  edit /etc/grub.d/40 or 41 _custom

---

### Post by Kaail on 2012-08-12
I have 3 separate hard drives, one with win7 one with ubuntu and one that is just a data drive. Only the ubuntu drive was connected during install. I ran sudo update-grub and it detected both OSs. I never see grub at all.

---

### Post by darkod on 2012-08-12
> **Kaail said:**
> I have 3 separate hard drives, one with win7 one with ubuntu and one that is just a data drive. Only the ubuntu drive was connected during install. I ran sudo update-grub and it detected both OSs. I never see grub at all.

You didn't see it because it thought ubuntu was the only OS. No point having a boot menu if there is only one OS. Since it couldn't detect windows during the installation, it didn't create an entry for it.

The update-grub does detect all OSs and creates entries for them, so now you should have grub2 boot menu. If you still don't, you might be booting from the wrong disk (but I have to say it doesn't sound like that since you wouldn't be booting ubuntu at all if it was the wrong disk). So, if you still don't see grub2 boot menu after running the update-grub try changing the hdd boot order in your BIOS. The correct grub2 might be on another disk.

---

### Post by Kaail on 2012-08-12
When I ran update-grub it came back with this;

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
Found Windows 7 (loader) on /dev/sdb1
done

So it has detected the win7 OS.

EDIT: I have just restarted the computer and it all works now! I'm editing this post from Win7 and you sirs, have my thanks.

---

