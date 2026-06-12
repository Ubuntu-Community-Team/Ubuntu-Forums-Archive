---
title: "Boot Repair wants me to enable repository"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by JohnnyB2060 on 2012-07-12
Hi, I'm new to this, but i've installed the remix version of Ubuntu via dvd. I've installed it to an external hd. It will not boot, says BOOTMGR is missing.

(Its an Acer Aspire 5315 Laptop with a shot internal drive (now removed))

Then I came across Boot Repair.  However it keeps asking me to "enable a repository containing the [linux] packages in the software sources of ............12.04LTS(sdc1)"

Have I made any sense?! :confused:

 [http://paste.ubuntu.com/1088545/](http://paste.ubuntu.com/1088545/) (this may help?!)

And now, after reinstalling for the tenth time today, it's actually booted! I'm am so over joyed ! LOL!

---

### Post by oldfred on 2012-07-13
Welcome to the forums.

And glad you got it working.

the Bootmgr missing is a Windows error, so the Windows boot loader was in the MBR and looking for Windows in a partition with the boot flag. If you had no boot flag or the flag was on a Linux partition then the Windows boot loader does not work and gives the error.

Some BIOS also require a boot flag on a primary partition, but grub does not use one.

It just seems like you did not get grub2's boot loader installed to the MBR of sda at first but must now if it works. :)

---

### Post by YannBuntu on 2012-07-13
Hello, and welcome among us :)

> **JohnnyB2060 said:**
>  [http://paste.ubuntu.com/1088545/](http://paste.ubuntu.com/1088545/) 

For information, your previous install had failed, as there were some important system files missing (eg. no kernel).

Happy Ubuntu-ing :)

---

