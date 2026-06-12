---
title: "/dev/sda1 is clogged"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by wack82 on 2009-12-03
I’m trying to find out what is hogging /dev/sda1
  I have 14G set aside for this and it is showing 72% usage.
  df –h shows the following (attached):


    I have run:
  apt-get clean
  apt-get autoclean
    with no tangible results as far as freeing up space.
  I have also emptied trash  /.local/share/Trash
   
  I have tried disk analyzer but can’t find out what is eating up the space.
   
  Any thoughts?

---

### Post by darkod on 2009-12-03
I am not too experienced myself but
sudo apt-get autoremove

is also one of the commands for cleaning up.

---

### Post by wack82 on 2009-12-03
Thanks but I tried that as well. Mimimal cleanup was done and the usage is still 72%

---

### Post by darkod on 2009-12-03
How about something like this at least to tell you where most of the size is held up?
[http://ubuntuforums.org/showthread.php?t=211270](http://ubuntuforums.org/showthread.php?t=211270)

---

### Post by wack82 on 2009-12-04
Thanks [darkod]("http://ubuntuforums.org/member.php?u=946366"). I used baobab and was able to clear out some files which brought my / space usage down to 64% (from 72%). I'm still unsure why so many files are under /dev/sda1. I'm weary of deleting any more since I'm sure they are there for a reason. I did notice some online gaming files were stored there as well.

---

