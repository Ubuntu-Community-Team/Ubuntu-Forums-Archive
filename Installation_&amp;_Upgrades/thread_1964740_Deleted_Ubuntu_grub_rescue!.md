---
title: "Deleted Ubuntu grub rescue!"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by Neo4 on 2012-04-24
Hi!

I have an eee pc tha had xp and Ubuntu. Yesterday I've deleted Ubuntu and wanted to keep only xp.

Now I am stuck in the grub rescue....

Isn't possible to restore grub or fix mbr without live cd? I'm on vacations and I only have an iPad and an android phone with an sd, my eee can boot from sd cards, any help?


Thanks a lot, this is a little bit urgent :/

---

### Post by darkod on 2012-04-24
You will have to create a usb stick or sd card with ubuntu that can boot into live mode. Or a cd if the computer has a cd-rom.

When you boot into live mode, open terminal and execute:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be a warning about the lilo configuration but ignore that. Those commands will write a generic mbr that can boot xp.

Another option if you have a cd-rom in the machine and a cd of xp, you can repair the bootloader with the xp cd.

---

### Post by Neo4 on 2012-04-24
As i said , I'm on vacations so limited access, so no CDs etc.... Ubuntu live could work?

---

### Post by darkod on 2012-04-24
I was trying to cover more information with a single post. Just select what is suitable for you.

I did say at the start that a usb stick or sd card with ubuntu that can boot in live mode will work.

---

### Post by Neo4 on 2012-04-24
Yes, but downloading Ubuntu on my android isn't suitable at all, and I don't think that I can create an bootable ad from my android either...

---

### Post by darkod on 2012-04-25
I am sorry, but I don't know of a way to fix this without any CDs, without any ubuntu live usb options, without anything. How do you expect to fix it if you can't have access to anything?

---

### Post by Buddhika Udaya Sri on 2012-04-25
[Neo4]("http://ubuntuforums.org/member.php?u=235003")  I got the same problem with grub rescue. If you want to keep Xp only, you have to repair it XP CD or bootable usb or sd card. I saw some way that you can give some commands to grub & solve the problem itself long time ago. But I don't know that method, & It's hard way .. Sorry :(

---

### Post by km3952 on 2012-04-25
> **Neo4 said:**
> Hi!

I have an eee pc tha had xp and Ubuntu. Yesterday I've deleted Ubuntu and wanted to keep only xp.

Now I am stuck in the grub rescue....

Isn't possible to restore grub or fix mbr without live cd? I'm on vacations and I only have an iPad and an android phone with an sd, my eee can boot from sd cards, any help?


Thanks a lot, this is a little bit urgent :/

Would it be possible to buy a pendrive & use an Internet Cafe to get a live pendrive image onto it?

---

### Post by Neo4 on 2012-04-25
In have a USB but all pcs in hotel have limited accounts that cannot access USB or cannot format it... :/

I tried download unetbootin and damn small Linux but with limited access the pcs can't format the USB pen

---

### Post by oldfred on 2012-04-25
I do not know which of the Windows/Linux repair CD/USB include a way to repair Windows MBR.

This is Supergrub's all in one 
[http://rescatux.berlios.de/wiki/Main_Page](http://rescatux.berlios.de/wiki/Main_Page)

This is Boot-Repair which you can add to a liveCD or download as a liveCD

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

But all these will require you to be able to write to a CD or USB flash drive.

If you know anyone with Windows 7, you can use it to fix the MBR. It still should boot any Windows.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

