---
title: "Upgrade ubuntu 9.04 to 9.10 from CD not work"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2009-11-26
Hello,

I have tried to upgrade from the CD ( I got it from ubuntu only) and by mounting the .ISO. However, all have been unsuccessful.

I have tried to follow the instructions from this website [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

First I tried to mount the ubuntu-9.10-desktop-i386.iso using the following:

sudo mount -o loop ~/Desktop/ubuntu-9.10-desktop-i386.iso /media/cdrom0

Which mounted it. But I never got the dialog box that says 'run upgrade'

I then did 'Alt F2' and typed the following:

gksu "sh /cdrom/cdromupgrade"

Still nothing happened.

I can browse the files from the mounted *.iso and on the burnt CD. However, the dialog doesn't appear.

I can boot from the CD if I restart my computer. However, I just want to do a upgrade and not clean install.

I can't do an upgrade from the update-manager as my Internet is too slow and unreliable.

Also i want to unmount my cdrom which is throwing ubuntu installation file after clicking on it.( From which i have mounted :: sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0 )

Now i want to unmount  it  and also want to upgarde my system to 9.10.

I have updated all the previous updates for 9.04


Hope for the earliest response from your side.

---

### Post by rameshvr on 2009-12-26
I am also facing the same problem. Please help.

---

