---
title: "Clear Boot directory, delete old kernels"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2015-09-09
During a long session trying every way I could come up with, I found that the items deleted from the Boot directory had found their way into a hidden file called /boot/.Trash-0, so that no matter what I did, the boot directory was too full.

So, 
1)  How did they end up there?
2)  What is the best way to make sure older files and kernels are automatically deleted from the boot directory, so updates will complete properly?  
3)  Is it possible to increase the size of the Boot directory?  How?

Below the ------- line is what I finally came up with, but I started out manually deleting files.
----------------------------------
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don&#8217;t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

1 - Go to Terminal and paste the following command: uname -r
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: 2.6.20-16-generic

2 - Go to Synaptic Package Manager via the System > Administration menus

3 - Paste this: linux-image-3 into the search box of Synaptic Package Manager

4 - Once you have located the old kernels, hightlight them and right-click then select Mark For Complete Removal then click Mark and then click Apply

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

Be careful of what you remove. Ensure that you don&#8217;t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.

Your computer and Grub menu should now be free of old kernels.

----------------------------
If still too full, check contents of /boot/.Trash-0  as root in XFE or nautilus + set nautilus prefs to show hidden files.  Delete all.

---

### Post by sandyd on 2015-09-09
1. That happens if you use the GUI to delete things. Using rm will not move files to a trash folder
2. Run apt-get autoremove every once in a while
3. You can resize it with gparted. LVM is a bit more complicated. As I remember, the boot partition is seperate, so you will have to shrink the LVM PV, and then increase the boot partition size. Not a fun task.

---

### Post by RogerDavis on 2015-09-09
Thanks, that makes things a bit more clear.

As for using GParted, Boot looks like a folder/directory, not a partition.  Am I mistaken?

---

