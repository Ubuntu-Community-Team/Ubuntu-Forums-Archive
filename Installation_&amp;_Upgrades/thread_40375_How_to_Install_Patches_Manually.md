---
title: "How to Install Patches Manually?"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by Battlestar on 2005-06-08
Hi there,
         Im still newbie on this Ubuntu Linux and I want to learn some more. Please help me how to install patches manually which can be found at [http://patches.ubuntulinux.org/patches/](http://patches.ubuntulinux.org/patches/) . I dont have internet at house guys :(. I just download manually the patches to the site here in our office then save to my Flash Drive. Now my only problem is how to install this patch manually? And BtW, everytime I open the patches in the site others file like .diff, .patch, .dpatch re-direct me to another window and open like a notepad. Should I copy and paste this file? How can I Install this one? I can download only file like .tgz and diff.gz(It looks like they are zip file, Am I right?)..

Lastly, How can I update my Kernel? Everytime I install the Nvidia Driver for my VD. It always saying that I dont have a pre-compiled kernel(Sumthing like that).
And Where also can I find the GCC file?..Nah..Sorry to interupt you guys. I really want to learn this thing..

Once again..Thanks in Advance

---

### Post by connellr on 2005-06-08
Files with extensions .tgz (or .tar.gz) are G-Ziped Tar files which are similar to ZIP files.  if the file ends with either of these extensions you can unzip them with the command:
*tar -zxvf filename.tgz* or *tar -zxvf filename.tar.gz* 

If the file ends in .gz, but doesn't have a .tar before it you can unzip it with:
*gunzip filename.gz* 

I would assume once you get these files unziped there will be a file named something like INSTALL or README, or similar that will tell you how to manually install them.

Hope this helps,
RJ

---

### Post by Battlestar on 2005-06-09
Hi connellr,
         Thanks for your quick reply. How bout .diff, .patch and .dpatch file extension?
How can I install this manually? 



Thanks

---

