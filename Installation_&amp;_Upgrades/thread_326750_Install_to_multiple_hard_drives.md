---
title: "Install to multiple hard drives"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by SurferJoe on 2006-12-28
Currently have Ubuntu 6.10 installed but not happy with the way I have set up partitioning.
So ,a few suggestions are needed.

I have 1 of 320GB HDD and 1 of 300GB hdd

Did the install and assigned home to the 300GB.

Is there a way to say have 100GB assigned for the "file system" and the balance available to the user home folder giving maximum space for data storage?

Please excuse wording - hope this all makes sense.

Additionally , is there a way of repartitioning with say QParted without doing the full reinstall? Not fussed if I have to reinstall but would prefer not too obviously.

Also , is there a way of obtaining a list of all packages I have installed and then reinstall this list automatically with a fresh install if needed ,without having to go through the process of manually installing each.

---

### Post by halfvolle melk on 2006-12-28
> **SurferJoe said:**
> 100GB assigned for the "file system"
Do you mean 100GB for Ubuntu / the operating system itself? It's hard to imagine you'll ever need more than 10% of that. Open a terminal, run **df -h** and post the output here so we can have a look.

> Additionally , is there a way of repartitioning with say QParted without doing the full reinstall?
Yes. You can either use QParted from the live install CD or use the [GParted live CD](http://gparted.sourceforge.net/livecd.php). In any case, the partitions that you want to resize need to be unmounted (and this is so when using a live CD).

> Also , is there a way of obtaining a list of all packages I have installed and then reinstall this list automatically with a fresh install if needed ,without having to go through the process of manually installing each.
Here's a neat trick inspired by Azz:
```
dpkg --get-selections > mypackages #writes all installed packages to "mypackages"
# save "mypackages" on a USB stick, copy it to a fresh install
cat mypackages | sudo dpkg --set-selections #selects all packages from "mypackages"
sudo apt-get dselect-upgrade #installs them
```

---

### Post by SurferJoe on 2006-12-28
Thanks for your replies.

Contents posted here :

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             273G  3.1G  256G   2% /
varrun                506M  152K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  8.0M  498M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1             294G   78G  201G  28% /home


From what I understand , which may of course be wrong , the user data is all stored under home directory.
What I want is to assign the majority of my hard drive space - approx 580GB total to this user area so I have max available space - I have a huge collection of MP3s and TV shows I like to keep available over the network at home.

Thanks for the tip re QParted. Will look more closely at this over the weekend.
Also going to try to get into Quanta Plus and Ajunta for my web development and programming needs - really want to leave Windows behind if I can.

---

### Post by insane_alien on 2006-12-28
i only have a 9GB '/' partition and i only use 3.77GB of it. the rest of the entire drive is a /home partition

---

### Post by SurferJoe on 2006-12-28
Thanks , but the problem is with 2 separate drives.

EG with an old version of Red Hat I have here if I do the install it formats both drives as the one volume so I get full capacity available for user files.
With Ubuntu I want to do similar - eg format hda1 for O/S plus home directory , but also include hdb1 as space for home directory , so enabling full capacity.

---

### Post by SurferJoe on 2006-12-29
Thanks for all tips but I have sort of worked things out for now.
Rebooted with Live CD and ran GParted.
Repartitioned hda1 down to 20GB for Ubuntu files
Created extra partition of 260GB called hda2
Left hdb1 home partition as is.
After completion rebooted and logged in as root.
Mount partition hda2 and modified fstab to suit - just copied the entry for hda1 with just changing the label to hda2
Modified permissions for folder so user could write/read to it.
Logged off and logged in as user.
All working OK again.

Easier than I thought really.

As an addon , for those having endless problems with printer drivers please check out a program called TurboPrint - I actually bought a copy of this a couple of years back when I first tried out Linux then gave it the flick. With my current Ubuntu setup my printer the Canon ip1000 was having a major dummy spit in getting it to work until I remembered this program.
Downloaded again off their website but of course had lost my keyfile over the last year or two.
Sent an email off and actually got a reply within 24 hours ( at Christmas too! )with the keyfile enclosed.
So , if you do have problems getting a printer up and running , this is well worth the money to solve your problems. You can download and test it to see if your printer is supported etc - the keyfile simply removes the watermark on the output.

Thanks again to all Ubuntu users for their input.

---

