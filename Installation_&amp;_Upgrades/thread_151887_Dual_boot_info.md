---
title: "Dual boot info"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by Israfel on 2006-03-28
I am going to install ubuntu on my computer, but I need to be able to acess my windows XP as I'm not the only user. I've read how to do this, but I want to know if dual booting is possible with one hard drive, and if I will still see all of my programs and such that I installed into windows when i do install ubuntu. I want to break free from windows, but have my parents be bale to start windows without having to re-install everything. Any help is appreciated.

---

### Post by mnl88 on 2006-03-28
Yes, you can dual boot, and Ubuntu will make it fairly easy for you.  Since you've just got the one hard drive, you need to make a seperate partition for your Ubuntu install.  You can use the Ubuntu installer to create seperate partitions, or use some other program.  Then, you install Ubuntu on the partition you made for it.  GRUB will let you choose which OS to boot into when you start your computer.

Just make sure you back up anything important before you do anything.  And, having an XP install disk laying around would be good, in case something goes wrong and you need to restore your previous setup.

---

### Post by Israfel on 2006-03-28
[QUOTE=mnl88]Yes, you can dual boot, and Ubuntu will make it fairly easy for you.  Since you've just got the one hard drive, you need to make a seperate partition for your Ubuntu install.  A quick Google search should explain how to do that (Partition Magic worked for me).  Then, you install Ubuntu on the partition you made for it.  GRUB will let you choose which OS to boot into when you start your computer.[/QUOTE]
So doing this will allow use of windows without losing any programs/info? (And thanks for the concise reply).

---

### Post by Sef on 2006-03-29
**Back up** your files before you dual boot.  Any installation is not 100% guaranteed to work.

Read this excellent tutorial on dual booting by Herman:

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

Don't use Partition Magic; it has known issues with Linux.  Instead use the partitioner on the install disk.

---

