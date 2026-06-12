---
title: "Moving Ubuntu from external USB to internal HDD"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by scyntax on 2010-06-16
Would this be a simple case of just installing a fresh copy of Ubuntu 10.04 on my HDD, then copying everything from the USB over? I, of course, would need to update grub to load from the HDD instead of the USB. Would there be any other way to accomplish this?

---

### Post by oldfred on 2010-06-16
Yes I would prefer a clean install rather than attempting to copy the operating system. All your user settings and data should be in /home which you can copy over or create a new separate partiton for /home and copy that data over. If you have any system settings they may be in /etc but since you will still have your USB version you can go back and find anything you miss.

If you have installed a lot of software you may want to export a list of installed apps and reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work. Check for added PPAs like medibutu

---

### Post by C.S.Cameron on 2010-06-16
You could use dd to clone the external USB to internal HDD.
This would duplicate the partition but it could be adjusted later using gparted.
the code is something like:

sudo dd if=/dev/sda of=/dev/hda

Where sda is the USB and hda is the HDD.
You would do this while booted from the Live CD.
Open gparted to verify which drive is which.
The new drive is an exaact duplicate of the old one,
you don't need to reinstall grub or anything.
Following is more info on the dd command:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by arrange on 2010-06-16
Or you can copy the system as well (preferably from a LiveCD):
 * prepare partitions on the HDD
 * copy the system from USB, f.e by *sudo rsync -aHAX /media/USB/ /media/HDD*
 * reinstall Grub on the HDD
 * change HDD's */etc/fstab* appropriately

Should be it.

---

### Post by scyntax on 2010-06-17
Thanks everyone for your replies. C.S.Cameron, when you say "the code is something like: sudo dd if=/dev/sda of=/dev/hda", is this the actual code I would use or would I need to research the proper code. I did click on the link you provided and there is a ton of info there, some of it very confusing. 

arrange, when you say "Or you can copy the system as well (preferably from a LiveCD)", do you mean to boot from a livecd then copy my existing USB system because I wouldn't want to copy a fresh copy from the livecd. Not sure what you mean by "change HDD's */etc/fstab* appropriately", but I will certainly research this command. 

Thanks again.

---

### Post by arrange on 2010-06-17
[COLOR="DimGray"]do you mean to boot from a livecd then copy my existing USB[/COLOR]
Yes, of course, sorry for my bad English, should have been "Or you can copy the system as well (preferably **using** a LiveCD)".

For *fstab* see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), but basically you need to tell the system where to find all the partitions, and this will change once you copy them from the USB disk. If you need more help with that, just ask.

---

### Post by C.S.Cameron on 2010-06-17
Once you have the drives plugged in and are booted from the Live CD open gparted and determine the designation of your internal hard drive and your external USB drive.
Run the command:

```
sudo dd if=/dev/sda of=/dev/hda
```

where sda is the drive you want to clone from and hda is the drive you want to clone to.
Nothing will seem to happen for a long time, no flashing lights etc.
Everything existing on hda will be wiped out.
A new partition will be written on hda the same size as was on sda.
It will contain everything that was on sda including boot records etc.

---

### Post by hobocaver on 2010-06-17
Hi   my user name is hobocaver and I just used a similar method to install UNR 10.04. I am not cli proficient at all, so it took a few days to work it out. UNR went on an Asus 1201 without an OS, looks fantastic and runs even better. Had to resort to Unetbootin, much head scratching, blue words, before I figured out that the USB stick lost it's MBR. Found a dd command in these forums, tried it , and voila, it boots. Wireless, 3g modems all work, out of the box. I am posting this to say thanks for the quality of your forums.

---

### Post by scyntax on 2010-06-18
cannot get this command to work, probably because I am entering it wrong. I think that the word "media" should be replaced with something even though I cannot find that word in the "info rsync" help. I do have the devs correct.  ```
sudo rsync -aHAX /media/sdb1/ /media/sda1

``` but when I enter this command, I get this errorr: rsync: change_dir "/media/sdb1" failed: No such file or directory (2)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]"

---

### Post by scyntax on 2010-06-18
I thought the dd command  would be my answer, but as you point out, this command wants to copy the entire partition, not just what's in it. consequently, after nine hours, the command failed because it wants to copy a 115gb partition to my 100gb HDD.

---

### Post by C.S.Cameron on 2010-06-18
I think there is a way to do it with the cp command that only copies the data.
Not sure if it copies the boot info though,
I guess you could reinstall grub.

I seem to recall getting dd to work copying from a smaller disk to a larger disk but I'm not sure.

---

### Post by scyntax on 2010-06-18
The dd command is the way to go. Before executing this command however, make sure your source partition will fit  on the destination drive. I had to resize it so that it would fit. After  doing so, this command worked like a charm. Thanks so much for  everyone's help on this.

---

