---
title: "Default boot after Hardy upgrade (minor problem)"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by tedrow on 2008-05-29
Dell D630 - originally delivered with XP Pro. I loaded Gutsy successfully last year, all worked great.  Unattended boot -> default option would go to XP after 10 secs.

Last week, upgraded to Hardy 2.6.24.14, mostly OK - minor problems with sound (resolved). Boot menu reflects 3 Hardy's (.14, .16 and .17) because I updated the Hardy kernel. Things work pretty well, although Hardy has a tendency to lock up.

Problem: The boot process no longer defaults to XP. 

After initial Hardy upgrade, default boot selection was "Other Operating System" and after time-out, would return error.  After Hardy updates, default is now .14 generic (recovery mode).

Question: How do I set Win-XP as my default unattended boot option?

Thanks - Ubuntu forums rank among the best I've ever relied upon.

---

### Post by didac on 2008-05-29
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
```

Count the number of lines beginning with 'title'. The first one will be 0, the second 1, and so on. The line whose Title is XP will be the one you are looking for to make your default.

Now go to a line that begins with default, at the beginning of the file. Whatever the digit is, put it at the end. If XP is the 5th title (that is number 4, remember), make the line look:

```
default 4
```

Save and reboot. You are there.

Hope isn't too confusing.

---

### Post by tedrow on 2008-05-29
A world of thanks, Didac - clear as a bell and easy to implement.  I'm all set.  Many thanks.

---

