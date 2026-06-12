---
title: "VMWare Player with Ubuntu 6.06"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by GeoffLaw on 2006-09-04
I have downloaded Ubuntu-6.06.1-i386.zip and extracted it to load into VMWare Player. However the player complains that Ubuntu-6.06.1-i386.vmdk has problems, which can be fixed by correcting the following lines:

RW 4192256 SPARSE "Ubuntu-6.06.1-i386-s001.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06.1-i386-s002.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06.1-i386-s003.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06.1-i386-s004.vmdk"
RW 8192 SPARSE "Ubuntu-6.06.1-i386-s005.vmdk"

However, does anyone know the root password?

Thanks

Geoff

---

### Post by kaffelars on 2006-09-04
That should be available from where you downloaded the image.

---

### Post by GeoffLaw on 2006-09-04
Unfortunately not! I got it from here: [http://cdimage.ubuntu.com/vmware/](http://cdimage.ubuntu.com/vmware/)

There is no explanation or anything. I can easily contribute an updated file so others do not have the same pain I did. However the root password would be very useful!

Anyone?

Geoff

---

### Post by Cornald on 2006-09-04
I don´t know if matches, I once had a (Ubunut) vmware with rootlogin:
"ubuntu"
Try upper/lower case "u/U".

Please post the result if this should fit

---

### Post by GeoffLaw on 2006-09-04
Thanks for the tip, however I still cannot get in. I can use ubuntu:ubuntu but I cannot figure out the root password, even after lots of tries.

Can anyone please help?

Geoff

---

### Post by GeoffLaw on 2006-09-04
I have cracked it!

Just to summarise the whole process for anyone else who needs it:

- Download Ubuntu-6.06.1-i386.zip from [http://cdimage.ubuntu.com/vmware/](http://cdimage.ubuntu.com/vmware/)
- Extract the ZIP file
- Edit Ubuntu-6.06.1-i386.vmdk and add the bold text to the following lines:
```
RW 4192256 SPARSE "Ubuntu-6.06**.1-i386**-s001.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06**.1-i386**-s002.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06**.1-i386**-s003.vmdk"
RW 4192256 SPARSE "Ubuntu-6.06**.1-i386**-s004.vmdk"
RW 8192 SPARSE "Ubuntu-6.06**.1-i386**-s005.vmdk"
```
- Start VMware Player (or other VMware product)
- Load Ubuntu-6.06.1-i386.vmx
- Login with ubuntu:ubuntu
- Start a Terminal session
- Type "sudo su -"
- When prompted for a password type "ubuntu"
- You are now logged in as root
- Type "passwd"
- Enter and then re-type your new root password

Job done.

Regards

Geoff

---

