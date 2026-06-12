---
title: "Installing windows to dual boot"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by EV1CR8R on 2007-10-27
Well I completely got rid of  windows on my laptop a while back and now my wife needs my laptop to go away on a course. She has to run proprietary software that only runs on windows so now I have been charged with putting windows back on my feisty laptop. Where can I find help on putting windows back as dual boot on this laptop. Thanks in advance

---

### Post by taurus on 2007-10-27
Download GParted LiveCD and boot from it.  Then, use it to resize your harddrive, making room for Windows.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Now, install Windows and at this point, it will overwrite your GRUB on MBR so you can't boot to Ubuntu anymore.  Therefore, you need to reinstall GRUB so you can boot both Ubuntu and Windows.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

