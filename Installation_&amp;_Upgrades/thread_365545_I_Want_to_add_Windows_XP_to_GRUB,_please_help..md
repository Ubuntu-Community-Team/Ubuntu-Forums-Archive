---
title: "I Want to add Windows XP to GRUB, please help."
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Tahir on 2007-02-19
Hello all,

When I installed ubuntu, I installed it on different harddrive because I did not want it to mess with my Windows xp harddrive.  I did this by unplugging the hd which had windows xp installed on it and plugging in the harddrive with ubuntu on it.  

Now the only way I can get into linux or windows is if I connect the hd to the computer that its installed on and disconnect the other one.  As you can imagine, this becomes quite tedious.

Before I started the installation of ubuntu to a new hd, I thought that I could connect both hd's to the computer and use the bios to select which one I want loaded.  I tried this and it did not work. 

If I have two SATA drives connected to my motherboard, then it will load up the first of the two harddrives.  What I want to do is put the hd with ubuntu installed on it in the first plug/port (whats the word?) and put windows xp as the second hd, and then write an entry into grub from which I can select to load up windows xp if I so desire.

How would I go about doing such a thing?:confused: 

-Tahir

P.S Ubuntu is so fantastic I don't even notice that I am using it instead of Windows -- seriously!  And I can tell you that setting it up was quite difficult considering that I had to give it wireless access with wpa but everything is sorted now and I can surf the web and download and chill just as I can do with Windows XP.

---

### Post by Kateikyoushi on 2007-02-19
Here are the steps how to add win to your grub menu. [LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_add_Windows_entry_into_GRUB_menu")

If you want to know your partition layout use:

```
sudo fdisk -l
```

---

### Post by confused57 on 2007-02-19
Since Windows & Ubuntu are on separate hard drives, you'll need an entry similar to that described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It's very similar to the entry described in the link from Kateikyoushi...

---

### Post by orb9220 on 2007-02-19
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Tahir on 2007-02-20
Yes I have managed to do it.

I connected the windows drive to the second SATA port and then edited the menu.lst file and added it.

its all good now!!!!

Thanks every1.

I added this:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

