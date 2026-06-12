---
title: "How can I backup my files to restore Windows"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by hawkscreecher on 2012-06-26
I just got a new hp pavilion m6 laptop and I tried to install Ubuntu so I could dual boot.  Unfortunately I messed up somehow and now my windows 7 will not boot at all. None of my recovery tools are working so I decided to completely reinstall windows 7.  In Ubuntu I can still access the files that I put on the hard drive while using Windows.  I would like to know if there is a way I can back up these files so that when I reinstall Windows I can quickly install all my programs, access my files, and keep the same system settings.  Any help is appreciated.

---

### Post by darkod on 2012-06-26
You can copy data like documents, photos, videos, etc but I don't think you can backup the program files and settings from ubuntu and then restore them in windows.

You will have to reinstall all programs and configure all settings unless you can save the current installation.

What exactly is happening when you try to boot windows?
And do you have any idea how you "messed up"? :)

---

### Post by Mark Phelps on 2012-06-27
If the following is true:
1) You actually installed Ubuntu to its own separate partition -- NOT a Wubi install
2) Ubuntu boots and works just fine

Then ... you can use Clonezilla to back off the Ubuntu partition to an image file on an external drive. You will need a Clonezilla LiveCD to do this as it can not back off the partition it's using.

You can use the same LiveCD and Clonezilla image to restore that partition later -- after you have reinstalled Win7.

---

