---
title: "Boot failure after Upgrade to 10.10"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by jkirby65 on 2010-11-22
Hi all,

I was happily running 10.04--- really worked fantastically!  Then, I updated all, and upgraded to 10.10 using the upgrade manager in Ubuntu Desktop.  Now, when I choose Ubuntu from the boot page, the computer shuts down--- no errors, it just reboots and I get right back to the boot page.  I cannot boot into Ubuntu at all, and I am now stuck with Windows 7 once again.  Help!

J

---

### Post by bcbc on 2010-11-22
if this is a wubi install - it sounds like it is - copy the c:\ubuntu\winboot\wubildr over c:\wubildr.

---

### Post by jkirby65 on 2010-11-22
Thanks so much.  Here's a stupid question--- what the heck is wubi?  I installed using "installer for windows".  It was very different than my first install of ubuntu several years back--- I didn't need to partition my drive.  Is this "wubi"?.  I must say it was REALLY easy.  What is the disadvantage?  I have heard others refer to a "proper" installation, as opposed to a wubi installation.  Not sure what to think here.  

Thanks for your help!

J

---

### Post by bcbc on 2010-11-22
Wubi (Windows Ubuntu Installer) refers to the method of installing Ubuntu under Windows. The key difference to a normal partition install is that Ubuntu is installed to a virtual disk (a file that lives under the windows file system.
Another difference is that Ubuntu boots from the Windows boot manager using a special wubildr (grub2's wubi bootloader).

Both of those are causes of wubi problems. The virtual disk can corrupt (although in most cases you can easily get your data off or fix, from what I've seen).
The grub problems are mostly - but not always - due to user action from very confusing screen prompts during updates (only affects installs on a partition other than Windows - e.g. if you installed to drive D: instead of C: ). 
And what affected you was the upgrade process (it was mentioned in the 10.10 release notes that wubi installs would break). But I've seen the same problem with the 10.04.1 grub update as well. These only affect wubi installs on the main windows partition because Grub2 is updating the c:\wubildr and corrupting it in the process.

But, having a direct partition install won't make you immune from problems. I've seen many normal installs failing to boot after grub updates as well. But not many people on ubuntuforums use wubi so you will get quicker, better support. Also, it's easier to repair grub than try and fix wubildr's.

If you want to migrate your wubi install to a partition install you can use this guide: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) (you have to create the partitions first manually)

---

### Post by jkirby65 on 2010-11-23
This is such great info--- thanks!  Also, your suggested fix worked just fine, so I have my ubuntu back!  

As I have little invested so far, I think I will just uninstall ubuntu and reinstall on a partition.  Thanks again for your terrific help!

---

### Post by bcbc on 2010-11-23
> **jkirby65 said:**
> This is such great info--- thanks!  Also, your suggested fix worked just fine, so I have my ubuntu back!  

As I have little invested so far, I think I will just uninstall ubuntu and reinstall on a partition.  Thanks again for your terrific help!

You're welcome. Enjoy!

---

