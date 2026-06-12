---
title: "edgy: cannot mount cdrom /dev/hdc"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-05-01
I installed edgy a while ago and now I have a reason to use it. But, I have a problem. I cannot mount the dvd which is in the fstab as
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I try:
root@misty:/dev# mount /dev/hdc /media/cdrom0
mount: special device /dev/hdc does not exist

same thing for /dev/hdd.

I tried MAKEDEV, as I would on a Slackware install and it gave a message:
root@misty:/dev# MAKEDEV -v hdc
udev active, devices will be created in /dev/.static/dev/
create hdc      b 22 0 root:disk 0660
.
.

So, how do I get it so I can mount my dvd on /dev/hdc and my burner on /dev/hdd?????

tj

---

### Post by exoasol on 2007-05-02
I also have this same issue.  My DVD burner will not mount a DVD or CD because my /dev/hdc does not exist.

I am running feisty but figure it still applies.  The first install for me worked great and then I had to reinstall and now it doesnt work.

thanks for help in advance
aaron

---

### Post by 999alfred on 2007-05-02
I found my problem as to why I could not mount the cdrom. 
I boot either Slackware, Windows or Ubuntu using lilo. In the lilo config file I used had
  append="hdc=ide-scsi hdd=ide-scsi"
(I block copied the section form the slackware boot section.
 But, I had no module rule to use scsi for ide.
Duh, that ain't going to work.

The tell tale was the boot messages having
ide_setup: hdc-ide-scsi
But, cdrecord -scanbus listed no cdroms.

Removing the append command from the lilo.conf  Ubuntu section solved the problem.

tj

---

### Post by exoasol on 2007-05-02
i am not using lilo, i am using grub, could this till be a problem?

also ubuntu is my only OS on this computer and I like Ubuntu configure grub on install

---

### Post by 999alfred on 2007-05-02
I don't know if that would be it or not as I have never used grub.
The way to check would be to look in the /var/log/messages log file. This is the file boot messages are written to.
Search for "hdc" in that file. If it has the line:
<data/time>:ide_setup:hdc=ide-scsi
 Then this could be your problem....

I hope this helps.

tj

---

### Post by exoasol on 2007-05-03
unfortunately the grub files didnt show anything with hdc or cdrom and /var/log/messages had no entries for hdc or cdrom either.

I do not have a /dev/hdc but I do have a /dev/.static/dev/hdc

I tried to change the fstab to use the /dev/.static/dev/hdc but that didnt work, and I also tried to use /dev/.static/dev/sdc and that didn't work either.

thanks for all of your help so far
aaron

---

