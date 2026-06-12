---
title: "Can upgrading solve hibernate issues?"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by mreq on 2013-03-28
Some time back I had hibernation working (most of the time) properly on my 12.04.

Had to reinstall recently and now I am quite happy with my system. However, the hibernation does not work. The only notable difference from my former 12.04 install is that I have RAID-connected SSDs (had 2x128, now 1x256) and that I am using XFCE over Gnome.

Is it worth trying to upgrade to 12.10 or 13.04 in order to get hibernation to work? Could it be caused by RAIDing? I'd love to have hibernate working properly.

Currently I'm at a 64bit 12.04 on a Sony Vaio Z21V9E/B.

---

### Post by kc1di on 2013-03-28
Hello mreq,

I think if I remember right that 12.04 comes with hibernate not enabled.  and here is a page telling how to re-enable it.
[http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/]()

That being said - I believe you may have to also enable it in xfce by uninstalling xfce4 power manager and installing gnome power manager. 
good luck

---

### Post by mreq on 2013-03-28
Hi kc1di,

perhaps I wasn't clear in the original post.

I do have hibernation enabled, but after using ```
sudo pm-hibernate
``` and turning the PC on again, I get the same result as with ```
sudo shutdown
```, ie the session or whatever we call it is not restored.

---

### Post by ahallubuntu on 2013-03-28
~

---

### Post by mreq on 2013-03-28
I have enough swap space. However, the UUIDs don't match. I'll try to update them and see how goes.

---

### Post by mreq on 2013-03-28
Nope, didn't help :(

What's strange is that I get some strange messagess (but that happened on my farmer install as well).

```
option: option_instat_callback error -2
```

I asked, even started a bounty, but to no avail: [http://askubuntu.com/questions/250673/hibernate-option-option-instat-callback-error-2](http://askubuntu.com/questions/250673/hibernate-option-option-instat-callback-error-2)

---

### Post by ahallubuntu on 2013-03-28
~

---

### Post by mreq on 2013-03-28
Yes it is. I only have 2x128 = 1x256 disc in my laptop. I'll try to play with a flash drive and gparted.

---

### Post by mreq on 2013-04-01
The problem was in RAID partition /dev/mapper/someswappartition receiving dynamic UUIDs on boot.

Therefore the /etc/initramfs-tools/conf.d/resume was always outdated. I solved it by not using RAID (wanted a clean install of xubuntu anyway).

---

