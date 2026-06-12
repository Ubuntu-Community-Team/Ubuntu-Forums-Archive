---
title: "Newby Installation Question"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by drich290195 on 2007-01-25
Write this is my problem i am new to Ubuntu, i insert the cd and boot from it i go to install. Okay i have a 60gb harddisk with win xp on and 17gb free. 

Now i dont want to loose my windows i want to dual boot. What partition option do i choose can i choose the one to rezise and create new, will that keep my old windows in tact. Can someone please guide me through the installation process.

Thanks guys i am totally baffled.

---

### Post by drich290195 on 2007-01-25
Can anyone help how do i install this thing ithout loosing xp, the option to use free space returms an error.

---

### Post by confused57 on 2007-01-25
See this site, it has most of the info you'd need to install Ubuntu:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

When you say 17 Gb free, do you mean a separate partition or just part of your Windows partition that's has no data(which would require resizing your Windows partition)?  What was the error message?

---

### Post by drich290195 on 2007-01-25
Yeah 17gb free space on the windows partition if i resize will it delete windows.

---

### Post by housam on 2007-01-25
No, Resizing will not harm your windows. but you have to defrag the partition at least two times before the resizing. and also back-up all your data and files.
Now you can use the Gparted partitioning tool to do the job. it is on the live CD . you boot through the live CD and click system >> admin. >> Gnome partition editor.
Resize the windows ( by clicking on the partition and shrinking it from the right end ) to create an unallocated space of only 11Gb to leave some space for windows to work in.
Now devide the unallocated space to two new partitions:
10 Gb ext3 for the root ( / )
1 Gb swap for the  ( swap )
After that go for the installation and when it comes to the partition mater , choose the manual way .

Good luck.

---

