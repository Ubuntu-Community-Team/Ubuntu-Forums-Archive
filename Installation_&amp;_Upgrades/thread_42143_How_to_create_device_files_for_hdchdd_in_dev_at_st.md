---
title: "How to create device files for hdc/hdd in /dev at start up?"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by busser on 2005-06-16
Hi!

I've got this problem:
I've installed Ubuntu using debootstrap. Now there are no files named hdc, hdc1, etc., and hdd, hdd1, etc. in the /dev directory (hda and hdb are there allright). So I can't access my CD-RW (hdc) and DVD-RW (hdd) drives. I've successfuly created these files using MAKEDEV script (I hope I've got that name right) and then I could access both drives. But the files disappeared after I had rebooted the machine. So I quess the content of /dev is generated automatically. Right?
So, how (and where) can I tell Ubuntu to create the device files when it starts up?

Thanks for any ideas!!!

---

### Post by frodon on 2005-06-16
in the fstab file in /etc repertory, it contain all the devices to be mounted at start up.

---

### Post by busser on 2005-06-17
Thanks Frodon!
Unfortunately, it didn't work... I have appropriate lines in /etc/fstab, that is not the problem.

I quess it has something to do with **udev**. It doesn't create the /dev/hdc nor /dev/hdd files for me. I looked in the files in /etc/udev directory, but they seem to be alright.

Any ideas anybody?

---

### Post by busser on 2005-06-20
Allright, I've solved it. So just in case, somebody runs into the same problem:

The problem was that the ide-cd module was not loaded. So a new line with 'ide-cd' on it in /etc/modules did the job.

---

