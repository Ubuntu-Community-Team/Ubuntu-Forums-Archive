---
title: "Can't access slave HDD since 7.10 upgrade"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by HeruLuingul on 2008-02-04
I recently made the switch from Windows to Linux completely, so I'm not dual booting or anything. I used a Feisty LiveCD to wipe the master hdd and install Ubuntu, then applied all the necessary upgrades to get it to Gutsy. The wierd thing is that for the short time I was running Feisty, I could READ from the slave hdd but not write to it. Now I can't access it at all; see screenshot.
[IMG]http://img214.imageshack.us/img214/2647/screenshotcopysw0.jpg[/IMG]
So does anyone know how to make it linux-friendly without formatting it? It's full of files I'd rather keep, and I have no temporary storage solution for them. Thanks in advance.

---

### Post by jago25_98 on 2008-02-04
try giving it  a scandisk in windows

---

### Post by Partyboi2 on 2008-02-04
Did you try what it suggested and mount the drive with
```
sudo mount -t ntfs-3g /dev/sdb1 /media/Cerebellum -o force
```
If so what happened?

---

### Post by tact on 2008-02-04
Yep feisty (unless you install some software) could by default read only NTFS partitions.

What has happened is that the last time the NTFS partition was accessed under windows it was not shut down cleanly.  If you mount read only (as feisty was doing) then no problem.

Gutsy, by default, has the added software installed and so can mount NTFS in read/write mode by default.  But for safety will not mount it in read/write mode if it was not marked "clean".

You got a few options here.  One is to take the chance and do as the dialog box (and partyboi2) suggested and "force" mount the partition though its not marked clean.  You may have problems and cause some data loss doing so.  But you may not also.  :)

You could also mount the partition read only just like under feisty.
```
sudo mount -t ntfs-3g /dev/sdb1 /media/Cerebellum -o ro
```

 /etc/fstab entry for the above:
```
/dev/sdb1/media/Cerebellum  ntfs-3g ro,0 0
```

---

### Post by HeruLuingul on 2008-02-04
I tried the force-mount thing and it gave me this: (copied from terminal)
```
heruluingul@nova:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/Cerebellum -o force
[sudo] password for heruluingul:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Cerebellum: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (Cerebellum)
heruluingul@nova:~$ 

```
Is the problem the name of the drive? Am I missing some kind of ntfs drivers or something?

EDIT: didn't see tact's post before making this one. thanks for the explanation, i'll try read-only for now, but I still want to get to the bottom of this.

EDIT EDIT: I just tried to access Cerebellum through regular file browsing, and I can now read AND write files. Worked even though the terminal gave me errors. Thanks I guess!

---

### Post by tact on 2008-02-04
It possibly failed because the mount point /media/cerebellum does not exist?  Sorry - should have told you you have to create the mount point before mounting

Even tho it failed the attempt to force mount the device reset the logfile flagging the partition as "dirty"  and thats why it works now.

Glad its all sorted out now anyway.  :)

---

### Post by rpaco on 2008-02-07
Hi this is nothing to do with windows. It must be to do with the automatic ntfs-3g update a couple of days back or the Gutsy update also a couple of days ago.
In fact it must be the Gutsy kernel update, because until I was instructed  to do a reboot after the kernel update I could access all 11 of my NTFS partitions on hdb1-11 fine. and could read/write/delete/create with no problems.

I note that they are now listed as sdb instead of hdb although they are not serial access drives.
It must be the kernel update which has caused this.
I have followed the instructions below in the error message and modified my fstab file.
Also chmoded /bin/ntfs-g3 to read/write by everyone. but still get the same error stating "
$LogFile indidcates unclean shutdown 0 0 Filed to mount sdb6.
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt/usbdisk -o force

    Or add the option to the relevant row in the /etc/fstab file:

[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]Could a guru please suggest a fix for this.[/FONT]

---

