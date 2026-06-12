---
title: "Ubuntu trainwreck"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by train on 2006-11-30
Ok I goofed the first install and that is my fault.

What happened is I made a stupid mistake when choosing my keyboard and I should have just chosen plain English however I chose right-handed and it completely changed my keyboard, so when choosing my login it made that a mess, an e was showing up as a q and so forth.

Long story short is I can not login to the install as I have know idea what my user name was as I typed in a few with the keyboard in quirks mode.

I installed Edgy on a second hard drive and have no problems other than how can I choose to boot XP? The bootloader will only load Vista.

Also how can I get rid of the first install on my other hard drive? 

I have used Windows to delete that partition and free up space but it has not changed the original Ubuntu bad install. Ubuntu only allows me to completely format that drive and I do not want to alter Vista.

TIA

---

### Post by bulldog on 2006-11-30
Well bad luck with your keybord,never heard of such an option though.

To enter XP you have to make another entry for windows in your menu.lst,which points to your XP install.
It's pretty much the same as your Vista entry only it should point to another partition or hard disk.

To remove Ubuntu just format the partitions it created,you won't get rid of GRUB though,you need to use a windows install disk to repair the MBR of this disk.
But if you do so you won't be able to boot Edgy either.
You can however,delete the entry's in GRUB which are pointing to your non existing ubuntu install.

---

### Post by train on 2006-12-01
Thanks Bulldog,

Sorry for the late reply.

When selecting a keyboard in set up, I should have just selected English, there were about five choices for English, left-handed,right-handed and I said ok I am right handed and I chose that particular one thinking oh I can always change it later but it made mt keyboard type in morris code.

It seems to be a learning level in partitioning my hard drives. I formatted the original hd, ie gone with Vista and Ubuntu and had it on my main hd with XP, whatever the reason is (fat)both drives were dirty after installing Ubuntu, the first drive Windows straightened out easily although the second dirty drive was a mess, took Windows and 45 minutes to correct.

When I was using Ubuntu, I liked the way FF worked, it seemed much faster than it is on the Windows platform.

I was a little taken back that I could not play a DVD out of the box, Totem required a plug-in but in the GUI there is not an option to download or install plug-ins.

So I did some searching and I decided to try to add another player. It called for me to place the codecs into **usr/local/lib/codecs** as the normal install location. I chose to create folder but the OS would not allow me to create a new folder.

It seems to me as though this may be a tough learning curve just to be able to play a DVD.

One problem is I can not seem to regain the space back that Windows had on my main HD. I have 10 gigs that I would like to give back to MS, I can partition it or leave it unallowcated but I cannot extend the Windows partion...?

I am adding Ubuntu back to the second HD, does anyone know any good tutorials for adding programs in Ubuntu?

---

### Post by bulldog on 2006-12-01
Take a look at automatix,it can install a bunch of apps for you.
Including java,flash,win32codecs,fonts and a lot more.

[http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation](http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation)

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

---

