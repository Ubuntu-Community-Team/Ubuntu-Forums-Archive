---
title: "running karmic beta, but grub not right"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2009-10-02
hello.

i have finally managed to install the beta of karmic, seems to be okay (im not expecting miracles) 

now here comes the first problem, for some reason my other hard drive which has xp pro 64 bit on isnt in the grub menu list, eg theres no option to select the different os's at boot up, i have had a look in the boot/grub folder in the file system for the grub men.lst file, but it isnt there, i was going to add it by editing that file, which is what i have done in previous installs when for some reason xp didnt get included in the grub menu list.

any help will be appreciated, i can still boot into the xp drive, by selecting the hard drive where it lives at boot up, but this is a little bit of a hassle.

any help would be appreciated

cheers

---

### Post by The Cog on 2009-10-02
You need to create a file in /etc/grub.d, make it executable, and then run update-grub. Try this:

Create a file called /etc/grub.d/07_windows with contents similar to this:
> #!/bin/sh
exec tail -n +3 $0

menuentry "Windows XP" {
        insmod ntfs
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set e0d4e1aed4e186de
        drivemap -s (hd0) ${root}
        chainloader +1
}

but you will have to use the appropriate disk and partition numbers and UUID of course. You can get these by running the command **sudo blkid**. If your windows is on /dev/sdb1 then the grub reference will be (hd1,1). Grub2 partitions start from 1, not 0 like the old grub did. 

Once you have created the file, make it executable: **sudo chmod +x /etc/grub.d/07_windows**. Then run the command **sudo update-grub** which will rewrite /boot/grub/grub.cfg including the output from this script.

You can change the order in which the sections get written to grub.cfg by changing the number at the start of the filename.

---

### Post by QIII on 2009-10-02
No need for the script, changing permissions or editing a configuration file by hand.  Karmic uses GRUB2.

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```

---

### Post by techno-mole on 2009-10-07
cheers, that did the trick

---

