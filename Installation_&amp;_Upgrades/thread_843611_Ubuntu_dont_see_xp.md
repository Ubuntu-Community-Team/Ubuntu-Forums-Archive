---
title: "Ubuntu dont see xp"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Kaneda187 on 2008-06-28
Im doin a fresh install of hardy from a live cd but i get to the partitioning part and it wont give me the option of dividing it with xp it just says use entire disk or manual:confused: any ideas thanks guys:popcorn:

---

### Post by cpetercarter on 2008-06-28
Have you defragmented the Windows disk?

---

### Post by damis648 on 2008-06-28
If that still does not work, just manually partition it.

---

### Post by logos34 on 2008-06-28
maybe you need to defrag windows, or there's not enough free space, etc.  Try the suggestions [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html").  Hopefully that will get you the 'guided' option next time you run the installation

---

### Post by Kaneda187 on 2008-06-28
ive tried defragging but i shouldnt even need to as its a fresh install of xp so:confused: still puzzled because i did this b4 and it worked great:(

does the format of the hdd make any difference? like ntfs or fat32 which is better?? or does it matter?

---

### Post by connord94 on 2008-06-28
As far as I know the formatting wont make a difference - becuase the installation re-formats it to ext3 - but I'm only a linux beginner - so  ?


Connor

---

### Post by Kaneda187 on 2008-06-28
thanks anyways ill just keep trying stuff! its so annoying i just wanna know why it doesn't see the XP os on the hdd i mean i did all the right things and it worked perfectly for me before so it just don't make sense!:(:confused:

---

### Post by damis648 on 2008-06-28
Try just resizing the partition with parted magic, create a swap and Ext3 partition, and try the installation again, manually paritioning. Just format the Ext3 parition and mount as / and that should do it. I use parted magic a lot, it it good software.

---

### Post by Kaneda187 on 2008-06-29
ended up using parted magic great app thanks guys it working great again!!:)

---

