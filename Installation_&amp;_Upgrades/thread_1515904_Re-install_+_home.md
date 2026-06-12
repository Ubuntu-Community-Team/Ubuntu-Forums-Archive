---
title: "Re-install + /home"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by inka1 on 2010-06-23
Greetings!
I would like to ask a couple of questions regarding the /home directory.
I have searched the forums, but I could not find a clear answer for them.

I have installed Kubuntu a couple of month ago and managed to switch completely from windows, but I`m still noob to most things.

I want now to switch from Kubuntu to Ubuntu and reinstall completely the system.
I have a /home partition but I do not know what to do with it. 
Should I save the documents from it and remake it?
Do I need to point the installer to this partition? (somebody said here that this should not be done, but why?)

What happens to the settings in the hidden directories? Should I keep them all even if I don`t install the application?

Another problem:
currently the boot time is horrible! Grub starts very slowly and after the OS selection Kubuntu also is extremely slow. Does a reinstall fix this or how can I force a clean Grub install?

Thank you for your time and patiance!

---

### Post by dino99 on 2010-06-23
/home is where you have all your data and settings, so you can reinstall your system without troubles (of course dont reformat it when reinstalling)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by ktat on 2010-06-23
When installing a new operating system you need a partion called **/** this is youre root partition.  Now, you also have created a **/home** partition on your hard drive.  This is where all your personal files you have made/stored and some configuration settings are kept from using your previous OS.  To keep this information and continue using the partion as before you need to create a **mount** **point** called **/home** when installing your new OS. Make sure you **do not** check the **format partition** option as this will wipe off all you data.

---

### Post by darkod on 2010-06-23
> **inka1 said:**
> 
Do I need to point the installer to this partition? (somebody said here that this should not be done, but why?)



It MUST be done, otherwise it will just sit there unused.

Linux will never assume you want to use any partition, and for what. You have to specifically tell it.

You need to use Manual Partitioning when installing ubuntu, and for each partition that exists and you want to use, click on it to select it and then the Change button at the bottom.
Then just select the filesystem (it has to be same as before), the mount point (this is telling ubuntu how to use it) and whether to format or not.

As already mentioned, DO NOT format the /home partition because you want to keep the data there.

---

