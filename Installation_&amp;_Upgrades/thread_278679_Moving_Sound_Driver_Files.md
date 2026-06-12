---
title: "Moving Sound Driver Files"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2006-10-16
I have an onboard ESS 1869 sound chip and got the ALSA driver.  As I followed the instructions, I tried to get the downloaded file from my /home/name file folder to the created /usr/src/alsa folder, but I couldn't get the cp syntax right nor could I just move the file folder using the "file browser".

       " cp /home/name/alsa-driver-1.0.12.tar.bz2 . "

gave me an error.  I typed cp --help but saw no solution.  I was following the instructions from ALSA website for my driver.  I would like to know both the right syntax for "cp" and how to move files in "file browser."

Thanks!
Dave

---

### Post by ebutton on 2006-10-16
I'm fairly new to Ubuntu, but the file manager should let you get around priviledge restrictions if you start it at the command line with:

gksudo nautilus

Sorry, but I don't know how to make the commands appear in the "special window".  Hopefully, you can still copy/paste.

Regards,
EdB

---

### Post by SToL on 2006-10-16
cp /path/to/copy /path/to/copy/to

for example

cp /directory/filename /newdirectory/

If you're coping an entire directory use the -R flag...  cp -R /directory

---

### Post by Sierra_Dave on 2006-10-17
Thanks For the Help!

---

