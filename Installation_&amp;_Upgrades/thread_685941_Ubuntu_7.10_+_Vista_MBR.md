---
title: "Ubuntu 7.10 + Vista MBR"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by thach562 on 2008-02-02
Hello, I was using 7.10 and I followed the instructions on this website to install linux + windows 
[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

Everything went fine and for the first couple of boot ups it followed the regular process of using the Vista MBR. Then when I finished installing updates for my vista partition I restarted and....
GRUB! 
Yah I was surprised, I thought when I installed vista atop a linux base harddrive Vista wipes the MBR and installs its own. 
How is GRUB still there? At the moment, grub doesn't recognize vista as even being installed. I used G-parted live cd to see if I could mark the vista partition as boot, I did, but nothing happened the only choice I have is Grub for 7.10. 
I know of super grub live disk but if I use it to restore the MBR for windows it's possible to reinstall GRUB right?

---

### Post by thach562 on 2008-02-02
I tried using the vista installer dvd and going to repairs and repairing the windows boot up which is basically the fix /mbr command in windows and it says it fixed it but STILL GRUB LOADS. 

I tried using supergrub to repair the windows mbr, and it says it does it but still grub loads. 

any suggestions?

---

### Post by Pumalite on 2008-02-02
I would get a Knoppix Live CD and see if Vista is still there: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by froy02 on 2008-02-04
Post the output of the command 'sudo fdisk -l' before you do anything else. 
Since you've been only messing with the MBR your Vista installation should still be intact.

---

### Post by Ziggy72 on 2008-02-04
Try using your Vista install CD and go to Repair as you did previously. Then on the next page there will be several options, the last one being "Command prompt". Choose this.
Then type: ```

Bootrec /fixboot <return> and then
Bootrec /fixmbr <return>

```

Reboot

If that works ok and you have your Vista back, let me know and if you then want to dual boot Vista and Ubuntu without messing with the MBR I can probably help.

---

