---
title: "natty install"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by rvchari on 2011-06-21
i was happily using maverick32 bit with / and /home seperate. i went for a natty clean install after erasing 10.10. i could do it successfully but with one problem. my user is created in the /home created within and not on the seperate partition i had been using previously. now i am using natty and its running successfully.

is there a way i can shift the home folder to the other partition (which is now un named) ? my previous user folder and documents are intact there ! if i can do this, i need not go for re-install. is there a way to move the home folder to that partition and then make grub boot with /home mounted ?

i ll be happy if i can do this rather than go through the process of complete reinstall !

thanks in advance

---

### Post by ajgreeny on 2011-06-21
You obviously just forgot to mark the mountpoint of your old /home partition as /home in the new installation dialog.

I am not totally sure but all it may need is a couple of lines added to /etc/fstab like this
```
# /home was on /dev/sda2 during installation
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
```
Just make sure you get the UUID and format type (ext4) correct from sudo blkid, then edit my line above to fit yours, and add to /etc/fstab by using ```
gksu gedit /etc/fstab
```
Finally use command ```
sudo mount -a
```and hopefully your new home will now mount, and do so at every boot.

---

### Post by rvchari on 2011-06-22
i erased everything and went for a fresh install all over. you were right, i forgot to direct the mount point of home during my first install !  i fiddled around a lot and then went for a fresh install. now things are falling into place.... natty looks and feels r good but yet to be called stable when compared to maverick !

tweaking and configuring is going on as usual after every fresh install.

wish to ask you one doubt. this thread may not be related but i wish to ask how to issue command for system wide configuration of proxy settings in natty ? (i had an option in maverick where i could simply choose the location and click on "apply systemwide"

---

### Post by ajgreeny on 2011-06-22
Sorry, but I've no idea about setting up a proxy in any version of Ubuntu.

---

