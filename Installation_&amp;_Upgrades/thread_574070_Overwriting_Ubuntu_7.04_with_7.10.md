---
title: "Overwriting Ubuntu 7.04 with 7.10???"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by cad2blender on 2007-10-12
Hey guys I currently have ubuntu 7.04 and will be upgrading soon to 7.10. Now I am wondering if I can just use the 7.10 live cd and installing it by installing it over the same partition that the current 7.04 ubuntu uses? Will the bootloader "update" it self so it knows that the new version is installed. This might seem method of installing it, but the reason is that I have not really have important data on the ubuntu partition I don''t mind losing it, I have a backup. So is this possible, will I have to come back and post with a a MASSIVE boot error?

Thanks guys.

---

### Post by vishzilla on 2007-10-12
If you are using the Live CD, you will do a fresh install more like formatting and installing. You will lose all your personal files. If you wanna upgrade, use the update manager

this page should help you [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by forestpixie on 2007-10-12
if you install over the feisty install and tell it to format it will wipe the slate clean before it installs, grub will as well be reinstalled 

if you're going to be doing that it might be worth thinking about having a separate /home partition then next time you data should be safe

---

### Post by R.Bucky on 2007-10-12
It would be easiest to updrage to 7.10 by the update manager or ```
sudo apt-get upgrade and update
```. No need to make another cd.

---

### Post by dabl on 2007-10-12
> **R.Bucky said:**
> It would be easiest to updrage to 7.10 by the update manager

I would agree, except for all these "I tried to upgrade to Gutsy and it's all borked up" posts. ](*,)

I would say:

(a) if you were wise enough to make a separate partition for "/home" and your data is there, then the lowest-risk approach is to do a clean new installation from a CD (I prefer Alternate Install, but Live will work).  When I did this with Gutsy Beta, I found I needed to re-format the "/" partition as it was trying to re-use some of the Tribe 5 files, and it was getting confused and generating errors.  After a re-format of the partition, it went down clean and error-free.

(b) if you have a "monolithic" installation (everything but swap on the same partition), then you've got a problem saving your data that's in in your user folder.  You can be brave and try the dist-upgrade (get the details on the Ubuntu site), or else start backing up to DVDs before you do anything rash.

HTH!  :)

---

### Post by chefweb on 2007-10-12
when you want upgrade via update-manager, try this 
sudo update-manager -d

---

### Post by forestpixie on 2007-10-12
the op doesn't appear to worried about data - I'd agree with dabl and do the clean install  (I didn't but luckily no problems)

it'd also give him the opportunity to do some partitioning and get a /home - then it'll be easier next time or , heaven help us, when something goes completely wrong and a reinstall beckons

---

### Post by cad2blender on 2007-10-12
Whoa thanks guys 6 responses in a couple of hours. Ok then I think I will use the live cd reformat method.

---

### Post by forestpixie on 2007-10-12
time to mark thread solved then :)

glad we could help, maybe use gparted [livecd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") to format - very easy

---

