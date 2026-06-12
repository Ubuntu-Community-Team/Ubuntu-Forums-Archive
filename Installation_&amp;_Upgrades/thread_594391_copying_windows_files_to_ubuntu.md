---
title: "copying windows files to ubuntu"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by esei15 on 2007-10-27
i'm going to install ubuntu on my laptop but and get rid of vista but i want to copy all of my files so that i can have them when ubuntu installs. i dont have a flash drive or a external hard drive that could hold this. is there any way to get the files from windows and save them while in the live cd so that they are there after the install?

---

### Post by taurus on 2007-10-27
In that case, you need to create a separate partition to store your files.  You can use gparted that comes with the LiveCD to do that.  Then, you can mount that new partition and the one with windows on and start copying stuff over.  I recommend you make that new partition to be ext3 filesystem.  Once you have installed Ubuntu, you can mount that partition and then just copy files to your $HOME.

---

### Post by esei15 on 2007-10-28
ok, thanks

---

### Post by Kizlum on 2007-10-28
Add a [Solve] tag on the post title ;)

---

### Post by esei15 on 2007-10-30
ok and i actually just shrunk my windows partition, one thing vista got right, and i just access all of my files off of it now

---

