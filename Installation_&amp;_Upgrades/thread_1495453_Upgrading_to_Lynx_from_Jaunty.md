---
title: "Upgrading to Lynx from Jaunty"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by HamletDRC on 2010-05-28
I am about to upgrade to Lynx from Jaunty. 

I heard that it is better to do a fresh install and reformat the hard drive in a different format than Jaunty uses because that will make it boot up the fastest. 

Should I burn a DVD and do a fresh install? Or is it completely the same as clicking "Upgrade" in the Update Manager screen of Gnome? 

Thanks,

---

### Post by pmlxuser on 2010-05-28
well if you have all your data backed up you can just do a fresh install, its quicker converting a file system during an upgrade can also risk the loss of data.

 you are forewarned, back up your data first and then you can do any of the two if you get alot of time..

---

### Post by HamletDRC on 2010-05-28
Just to be absolutely clear: 

Is there any difference in the final installed system when you do a fresh install vs. an upgrade in upgrade manager? Will my disk have the same format and boot options, etc?

---

### Post by wilee-nilee on 2010-05-28
Jaunty is ext3 and grub legacy unless you upgraded the grub and installed with ext4. Lucid is grub2 and ext4, and you would have to go from jaunty to karmic to lucid. Do yourself a favor check to make sure your graphics card is going to work in Lucid, and try out the live cd, if all is well back up your system and do a fresh install. 

The upgrading process would probably take a whole day even withe a fast internet connection and leave you without the latest ext4 at the least. A fresh install is what I would do.

---

### Post by HamletDRC on 2010-05-28
@wilee-nilee That is what I suspected. Thanks.

---

### Post by kanolsen on 2010-05-28
I find that after a reinstall I spend a day reconfiguring anyway after followed the "The perfect desktop" and other how-to's. So I try to upgrade first, but I usually find that it fails and I have to export the relevant files and reinstall and copy them back in, cumbersome and it almost always gives me plenty of work on the net following different leads to get things to work as it should again.

Is there a way of easily exporting config files so I can check the new and original file for differences and easily copy the changes back?


Kanolsen

---

