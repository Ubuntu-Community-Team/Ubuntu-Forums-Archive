---
title: "Locked out my user from sudo"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by staubsaugen on 2010-10-28
I installed kubuntu 10.10 with an encrypted LVM filesystem and I then put on virtualbox and wanted to get the USB passthrough working so I did sudo usermod -G vboxusers <username>.  What I didn't realize was that it took away all the other groups.  Now I can't sudo anymore.  I then wanted to boot into single user mode, but I can't figure out how cause I don't get a grub screen so that I can edit the boot line.  I need to add myself back to the admin group somehow.  Any ideas would be greatly appreciated!!!

---

### Post by CharlesA on 2010-10-28
Are you able to boot into a root shell from recovery mode?

Not sure if that'll work due to the encrypted LVM.

---

### Post by staubsaugen on 2010-10-28
I don't see any sort of option for a recovery mode anywhere.

---

### Post by CharlesA on 2010-10-28
Reboot and hold shift to get to the grub menu and select recovery mode.

It should be there.

---

### Post by staubsaugen on 2010-10-28
Thank you so much!  That was exactly what I needed!

---

### Post by staubsaugen on 2010-10-28
Actually, can you tell me one more thing?  What are the groups the default user is in so I can add myself back in?

---

### Post by CharlesA on 2010-10-28
They are just in the admin group as far as I know.

---

