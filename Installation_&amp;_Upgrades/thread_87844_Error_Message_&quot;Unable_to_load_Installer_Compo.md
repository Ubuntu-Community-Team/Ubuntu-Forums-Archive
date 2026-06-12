---
title: "Error Message &quot;Unable to load Installer Component&quot;"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by satshen on 2005-11-08
I tried to install Breezy on dual boot (second hard disk 20Gb) with WinXP on first hard disk 80Gb. The check for MD5SUM for the downloaded ISO showed the file is ok & without errors.

The first few steps of the installation (language, location etc) went off without any problems.

However, the installation suddenly stopped & I got an error message "unable to load Installer Components from CD - Retry <yes>  <no>. When I selected <no> the next screen came up with the message "some Installer Components could not be loaded <continue>. On selecting <continue> I was presented with a list of options that covered all the steps in the installation like "partition disk" , "Load GRUB on Hard Disk" ,............ "Abort Installation"  - its like a drop down menu with the installation task list in  sequence. Not knowing whether one could proceed with the installation, I selected "Abort Installation" and booted back to WinXP.

Please let me know if its possible to continue with the installation by sequentially selecting options from the list of options.

Thanks

---

### Post by yesplease on 2005-11-10
You get this message when there are files on the disk. Ubuntu does not want to overwrite an existing installation. 

In your case I would proceed to partitioning and manually make a / (root), /swap and /home partition of the size you prefer. If you are sure that you do this on the right disk you wont do any damage. Retry wont damage anything either. A separate disk is ideal and 'should' work without problems.

---

