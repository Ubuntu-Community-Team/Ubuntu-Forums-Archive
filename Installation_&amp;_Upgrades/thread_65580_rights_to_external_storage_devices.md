---
title: "rights to external storage devices"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by jrev on 2005-09-14
Hi all,

Has anybody the answer to this simple question :

[COLOR=Blue][SIZE=3]What is to be done so that everybody can access the floppy and zip100 internal drive in read & write mode ?[/SIZE][/COLOR]

please don't send me to a page that I have probably read without finding the proper answer to this (I hope) simple question 

I am on ubuntu Hoary 5.04 

I can provide my /etc/fstab on request ...

Thanks  :wink:

---

### Post by mlomker on 2005-09-14
[QUOTE=jrev]please don't send me to a page that I have probably read without finding the proper answer to this (I hope) simple question 
[/QUOTE]

Why don't you give me a link to every page that you've already read?  :-P

Seriously...post your fstab file.  It's usually just a matter of doing this in a terminal prompt.

```

sudo chmod 777 /media/floppy

```

You'd replace the path with the mount point for your device.

---

### Post by Miguel on 2005-09-14
I would make sure your users also belong to the group "floppy". I wouldn't take it for granted. Easyest way to check this is going to system->administration->users and groups

Once there, go to the "Groups" tab. Check the "show all users and groups" tab and double-click on "floppy" (its gid is 25 on my ubuntu). Add users as needed (but not more, just in case).

If you are more of a "terminal guy" (bad joke, I know) you could type
```

sudo adduser  name_of_user  floppy

```

If this doesn't help, then seize the power of fstab ;)

---

### Post by jrev on 2005-09-15
I just re-installed the system 


I had in fstab  :

/dev/hdd4 /media/zip vfat auto,rw,user  0   0 for the zip 100 or 
/dev/hdd4/media/zip vfat auto,rw,user,uid=1000,umask=0 0  0    

the command : sudo chmod 777 /media/floppy  has no effet if there is a line in the fstab for the same device 

fstab has prededence over the chmod command 

Thanks for your answers ...

I think Miguel has the right track for this problem...
I don't think there is a zip100 group but I had this device working some time ago on ubuntu hoary so ...

---

### Post by mlomker on 2005-09-15
After doing some research I've learned a bit. Using chmod, as I had suggested, does work just fine--I've tested it with flash drives.  The problem is that the permissions get reset on each mounting.

What I didn't know is that you can set the permissions on the directory at the time of mount using this option:

umask=000

This mask would set the mount point to 777.  umask is an inverse of chmod.  If you want 755 then set umask to 022.

Perhaps your line isn't working because of the spaces?

---

### Post by Miguel on 2005-09-16
Hmmmm...

I guess that mlomker is right. There should be no spaces between numbers in umask.

---

### Post by jrev on 2005-09-16
thanks Mlomker,
I have learned something new ... :wink:

---

### Post by mlomker on 2005-09-17
Here's a set of parameters for /etc/fstab that will allow any user to mount the device and everyone will have read/write access to it.  If the device should not be mounted at boot-up (perhaps it's CD or a hotplug device like a flash drive) then add the **noauto** option after **users**.

If you are mounting a vfat (Windows 9x) partition then you need the umask option.
```

/dev/sda1       /mnt/sda1       vfat     defaults,user,umask=000  0  2

```
If you are mounting a linux partition type then you omit the umask part. 
```

/dev/sda1       /mnt/sda1       ext2     defaults,user   0   2

```

---

### Post by jrev on 2005-09-18
I will check it when my PC is back 
the graphic card seems to be out !
Thanks

---

