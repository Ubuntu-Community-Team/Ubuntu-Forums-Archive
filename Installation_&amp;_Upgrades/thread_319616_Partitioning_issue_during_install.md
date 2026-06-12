---
title: "Partitioning issue during install"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by mrmcctt on 2006-12-15
I have downloaded the Ubuntu 6.10 iso and burned it to a cd.  I ran it as a live cd and was very surprised to see my wireless came up as soon as the live cd booted.  I decided tha I wanted to dual boot this on my WinXP Pro laptop.

I double click on the install icon on the desktop and start the installation.  As far as I can see I am following the steps almost verbatim with what [this link]("http://www.psychocats.net/ubuntu/installing") is telling me to do.  The installation is pretty straight forward.

However, when I get to the partitioning step, I try to manually edit the partitions by using free space on the laptop's hard drive.  I cannot seem to resize the hard drive to allow me to set up Ubuntu.  I get an error when I try to do so.  Basically the system tells me that I cannot resize the Windows partition.  Am I not able to resize the the Windows partition in a live cd session because the entire drive is set to be used by Windows?

Do I need to do something with the partition before running the install so I can use the free space on the hard drive?  I basically want to free 20GB of the 60GB to use for Ubuntu.  I want to take that 20GB partition and use about 1GB for the swap, roughly 7-8GB for the O/S and the rest for a /home partition.

Thanks for any help.

---

### Post by taurus on 2006-12-15
From the LiveCD, use gparted to resize your harddrive first, leaving an big empty space at the end.  Then, click on the install icon and choose the empty space to install Edgy on it...

---

### Post by Fully216 on 2006-12-15
When I started using ubuntu, I do so on my laptop with only one hard drive.  Because of this, I had to resize the windows partition as you need to as well.

As to my knowledge, the partition manager cannot resize the windows partition.  There is an open source solution to this, using the KNOPPIX Live CD, which uses qtparted to resize partitions.  I am not sure if that is what ubuntu uses or not.  To do so, simply boot into Knoppix, open a terminal window, and type the command qtparted.

you can also use ntfsresize.  It is a small bootable tool that will do the same.

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

By the way, you need your swap space to be at least as big as the amount of RAM you have.  The rest I would leave for the OS (which will include /home).  There is no need to separate you home directory, unless you just want to.

Hope this helps.  ;)

EDIT: Ah, so ubuntu uses gparted.  I knew there would be a way to do it with the live cd, although I wasn't sure.  You learn something new every day.  Thank taurus!

---

### Post by taurus on 2006-12-15
Gparted on the LiveCD can resize your Windows and so does GParted LiveCD...

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by mrmcctt on 2006-12-15
Thanks for the quick replies.

I'll give them a try tomorrow (got a few other things to do tonight so I'll have to try tomorrow) and I'll post back the results.

---

### Post by mrmcctt on 2006-12-16
> **taurus said:**
> From the LiveCD, use gparted to resize your harddrive first, leaving an big empty space at the end.  Then, click on the install icon and choose the empty space to install Edgy on it...

This is how I partitioned my drive for the install.  Thanks Taurus and Fully216 for your help.  I did not need to try the Knoppix Live CD or the GPARTED Live CD that Taurus suggested.

After resizing the partition, I set approximately 8GB for the / partition, 11GB for the /home partition, and 1GB for the swap partition.

Now my only question is, how can I be sure that my /home partition is where all my documents and settings are going?  I did a "df" from terminal and got this:  

```
rlodge@rlodge-laptop:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              8072336   1885532   5776748  25% /
varrun                  225152        84    225068   1% /var/run
varlock                 225152         0    225152   0% /var/lock
procbususb               10240       128     10112   2% /proc/bus/usb
udev                     10240       128     10112   2% /dev
devshm                  225152         0    225152   0% /dev/shm
lrm                     225152     17580    207572   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hda3             11282424    137780  10571528   2% /home
/dev/hda1             37889264  16408956  21480308  44% /media/hda1
rlodge@rlodge-laptop:/$ 

```

I'm assuming (and we know what happens when we do this!!!) that my /home directory was set up on the /home partition but would like to make sure.

Again, thanks for your help.  

(BTW, I'm posting this from the installed Edgy on my dual boot laptop and both Windows and Ubuntu are working great.):mrgreen:

---

### Post by taurus on 2006-12-16
Look in your /etc/fstab and you will see an entry for /dev/hda3 mounting on /home.  So all your personal stuff and settings will be in /home/**username**.  ;) 

```
cat /etc/fstab
```

---

### Post by moshuptrail on 2006-12-16
When you log in as rlodge, your "home" directory (equivalent of Documents and Settings/rlodge in windows) will be /home/rlodge.  If you add a user joe, joe's home will be in /home/joe and so on.  All will be on the partition mounted as /home.

Ubuntu will create a whole pantload of hidden files in your home directory to hold your settings and preferences.  To see them, open a terminal and type ls -a.

---

### Post by mrmcctt on 2006-12-16
Cool....Thanks for the help.

Looks like I'm good to go.

---

