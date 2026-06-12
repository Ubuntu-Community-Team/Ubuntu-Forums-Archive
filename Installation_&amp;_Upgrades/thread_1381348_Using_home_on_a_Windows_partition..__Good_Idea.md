---
title: "Using /home on a Windows partition..  Good Idea?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2010-01-14
I bought a new computer that has Windows preinstalled and I want to install Ubuntu to dual boot.  I'm considering making /home on a separate Windows partition in Gparted..  would it slow the performance significantly if I used this setup?  I'd like to be able to access my important files regardless of whether I boot into Windows or Linux..

---

### Post by ajgreeny on 2010-01-14
You can not put your /home on to a windows ntfs or fat32 partition as neither filesystem will allow for the linux permissions needed to use the files properly.

What you can easily do, however is make a shared partition in ntfs which you can use to keep all your personal documents, photos, music, videos etc etc.  This partition can be mounted automatically at boot by adding an appropriate line to /etc/fstab, or more easily by installing ntfs-config and doing things the GUI way.

---

### Post by oldfred on 2010-01-14
Bottom line you cannot do that. Linux needs its file system to have permissions and users/group control. NTFS does not support that.

That said there is nothing wrong with having another data partition as NTFS with all the data you want to share. My original setup 3 years ago was just that was I was tying to get my wife to not realize we were converting. I went with openoffice, firefox, thunderbird, and later picasa all in windows. Then set up a shared partition with all the data and profiles for firefox and thunderbird so all data was the same in both. Now we are 90% Ubuntu and I have a lot of data in a /data partition that windows will never need to see but still have the NTFS shared partition for the occasions we are in windows.

I got too wordy do aj beat me to it. I agree with him.

---

### Post by audiomick on 2010-01-14
do put /home on a separate partition. Do not use a windows files system for it.

I have seen posts from someone who said his home was only a couple of hundred MB big and had syslinks to everything. Don't know how that works, but it is apparently possible.

What is easy is to set up your home the way Ubuntu expects, but tell things like open office to use a default store path to a data partition or where ever instead of to /home.

---

### Post by oldfred on 2010-01-14
I had a standard install for the last three years with just an additional (then FAT32, now NTFS) windows partition. With Karmic I went all out and moved /home to a new partition but also set up a /data for everything else. I have all my data in the data partition and /home only has the hidden files and folders ( but some seem to have 3 years of history). My /home is about 1GB. On my portable I just went with the standard location for /home but all my data in  my /usr/local/fred/data.

I pretty much followed this (mostly from one of the comments)
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

and linked like this:
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents

---

