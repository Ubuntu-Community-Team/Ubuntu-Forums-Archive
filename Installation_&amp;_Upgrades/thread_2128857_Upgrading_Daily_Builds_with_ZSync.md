---
title: "Upgrading Daily Builds with ZSync"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by Kookas on 2013-03-24
I'm trying to upgrade my 13.04 daily builds using ZSync, but it seems to refuse to do anything except download the relevant .iso:

```
#################### 100.0% 579.6 kBps DONE     

reading seed file raring-desktop-amd64.iso: *************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************
Read raring-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 822083584 local, fetched 0


```

Is this simply saying that there's not been any changes made, or is there more to it all?

---

### Post by oldfred on 2013-03-24
I have not updated mine for 3 months. It needed 70% new.

       ```
 fred@fred-Precise:~$ cd ISO
fred@fred-Precise:~/ISO$ zsync [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync)
#################### 100.0% 349.1 kBps DONE     

   reading seed file raring-desktop-amd64.iso: ********************************************************************************
Read raring-desktop-amd64.iso. Target 29.0% complete.      *************
downloading from [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso):
#################### 100.0% 405.9 kBps DONE      


```

---

