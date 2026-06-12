---
title: "No Ubuntu selection on Windows Dev Preview"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by 65Hyper on 2011-10-01
I installed the preview of Windows 8, and I needed Ubuntu for some reason. After using Wubi, restarted, it shows the Windows 8 bootloader and doesnt show Ubuntu selection. Help, really need Ubuntu.

Windows Developer Preview 8102, Ubuntu 11.04

---

### Post by Mark Phelps on 2011-10-03
Then you shouldn't have installed a Pre-Beta of a new Windows OS!

It's going to be a WHILE before the Wubi developers get around to making Wubi work witn Win8.  You would do better installing it in its own partition, that way, changes to Win8 won't affect your ability to use Ubuntu.

---

### Post by bcbc on 2011-10-03
From what I can see, the developer preview uses the same boot mechanism as windows 7. At least on the vm i used it's the same. Go to windows explorer, right click on Computer, Properties, Advanced system settings, Startup & recovery settings... then see if Ubuntu is in the drop down list (don't set it as the default). Check the time to display operating systems = 10

If you didn't get any errors during the installation that should be it.

---

### Post by syedsufyan on 2011-10-19
> **65Hyper said:**
> I installed the preview of Windows 8, and I needed Ubuntu for some reason. After using Wubi, restarted, it shows the Windows 8 bootloader and doesnt show Ubuntu selection. Help, really need Ubuntu.

Windows Developer Preview 8102, Ubuntu 11.04

You have to burn the Ubuntu ISO to a USB flash drive and boot to it.  You don't have to install it, you just have to run it once and you should get the selection of W8Dev, Windows 7, or Ubuntu next time you boot up.

---

### Post by searchfgold6789 on 2011-11-14
> **syedsufyan said:**
> You have to burn the Ubuntu ISO to a USB flash drive and boot to it.  You don't have to install it, you just have to run it once and you should get the selection of W8Dev, Windows 7, or Ubuntu next time you boot up.
I don't get it... You're saying that once I boot from the USB for Ubuntu and then simply reboot, it works?

---

### Post by Mark Phelps on 2011-11-14
> **searchfgold6789 said:**
> I don't get it... You're saying that once I boot from the USB for Ubuntu and then simply reboot, it works?

Probably NOT.

From my previous experience with Wubi, it does not use GRUB; instead, it uses something known as GRUB4DOS -- which is a form of GRUB that can be installed to, and run from, an NTFS partition.

When you install via Wubi, onto a Wiin7 (or Win8) PC, it attempts to modify the BCD to add entries.

Messing around with the BCD manually is a sure-fire way to hose up your PC and render it unbootable.  SO instead, you should download and install EasyBCD from NeoSmart technologies website.

Once that is installed, open it and use the Add an entry option -- and use the information there to try to add an entry for Ubuntu.

---

### Post by searchfgold6789 on 2011-11-14
Why thank you very much; I believe that's the most helpful and enlightening information the internet has seen on this topic yet. I am certainly going to give that a try, and then I'll post back with my results. I've got a couple of other things up my sleeve as well.
 - search

---

