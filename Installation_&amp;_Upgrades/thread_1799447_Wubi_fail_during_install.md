---
title: "Wubi fail during install"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by pnhearer on 2011-07-07
I think this may have to do with my hardware configuration (I have 2 drives in Raid 0). Now on to the problem.

Tried to install Wubi (the lastest version, just downloaded it this morning) from Windows 7 SP1 x64 and when the computer reboots I tried to boot into Ubuntu and then I receive the following error.

"No root file systems defined
 Please correct this from the partitioning menu"

.. I'll less the logs if I need to but I was wondering if any else had the problem before I did.

---

### Post by Rubi1200 on 2011-07-07
Hi and welcome to the forums :-)

Although Wubi installs to RAID are theoretically possible, in practice we have seen few cases where it succeeded and it has not been thoroughly tested.

In any event, the best thing to do so we can get a better overview of the situation is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bcbc on 2011-07-07
There are some raid configs that mess up ubiquity (the installer). Have a read of this and see if it applies: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/560748](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/560748)

Also this is interesting: [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

Note that these are referring to non-wubi installs, but since Wubi uses the same installer - the problem will be the same, even though it's trying to install to a 'virtual disk' (loop device)

edit: and what Rubi1200 said ;)

---

### Post by pnhearer on 2011-07-07
Hello Rubi,

I was thinking that maybe RAID was the issue, Ubuntu probably saw 2 disks and couldn't find where to grab the virtual FS and crapped out. So I'll grab your script and see where it's buggered up. Posting back in a few.


V/R
pnhearer

---

### Post by pnhearer on 2011-07-10
Just a quick update.

I gave up, actually I don't want to admit I gave up, so instead I actually chose an alternative and installed a Ubuntu into a virtual Machine.

---

### Post by Rubi1200 on 2011-07-10
Thanks for sharing the update. Actually, I don't consider this as giving up at all. You have decided to continue using Ubuntu and found a way to do so.

If you need more help with anything, please let us know.

Good luck :)

---

### Post by pnhearer on 2011-07-10
Hi Rubi!

Thanks for the positive feedback, and just so you know that I didn't brush off your help without a second thought, I did boot on the live CD and gave the script a go and I got the same results as people you were helping on a couple other threads. I am positive it is a raid issue. It may even be the Nvidia RAID controller issue, it may even be a JMICRON controller issue. All of which are too technical for me to tackle at my skill level. I was in tears trying to compile the linux kernel from source so...I think this way was for the best.

Ta ta
V/R
Pnhearer

---

### Post by Rubi1200 on 2011-07-10
Wubi installs to RAID can be problematic. In fact, I have only seen a couple of examples where it worked successfully.

Another option worth considering would be to get hold of a spare external drive and install Ubuntu on it separately before plugging it into your system. Then choose to boot from it using BIOS rather than messing with your current setup.

---

