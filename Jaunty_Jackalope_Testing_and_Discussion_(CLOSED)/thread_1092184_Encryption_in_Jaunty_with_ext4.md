---
title: "Encryption in Jaunty with ext4"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by blazemore on 2009-03-10
I know the Alternate Install CD can do Guided with Encrypted LVM, but Guided uses EXT3. Is there a way I can get full-disk encryption, but use ext4?

If someone can post a quick guide, maybe they (or me, or someone) could update the wiki, as I'm sure this is going to be a question for a lot of people.

---

### Post by Nullack on 2009-03-10
Crpyt doesnt care about the FS, just use the standard methods as per the wiki

---

### Post by Jordanwb on 2009-03-10
You can use the LiveCD to set up Encrypted file systems as well as LVM. As root install lvm2 and/or cryptsetup, then chroot into your install and repeat (don't forget to bind /dev and mount proc). There's a wiki how to set up encrypted file systems so the initrd will ask for a password on startup.

---

### Post by blazemore on 2009-03-10
I don't think you understand.

On the installation cd, there is an option for automatic encryption, but that does everything for you, and uses ext3.

I want to install to ext4, but use the full FS and/or disk encryption.

---

### Post by Nullack on 2009-03-10
I dont think you understand :)

Try reading the wiki :)

Also, use manual partitioning, as detailed in the wiki.

---

