---
title: "Shared Firefox profile will not open"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2010-02-05
Hi all,

Got an out of the ordinary problem here.

HP Compaq NC6000 laptop w/
Windows 7 RC1 and Lucid Lynx Alpha 2
partitions:
1 - Windows 7 (primary)
2 - NTSF data (primary)
3 - extended partition
3a - linux swap
3b - Lucid Lynx (ext3)

My Firefox profile information resides on the 2nd partition and have pointed the profile.ini in each Firefox installation to that folder. 

My Windows installation launches and runs just fine. However, when I try and open my ubuntu installation it tells me that Firefox is already running, but is not responding.

When I shut down Firefox in Windows I close it with FILE>EXIT to make sure its closed.

Anybody have any suggestions?

Robert

---

### Post by mdurham on 2010-02-06
Which version of Firefox are you running?

---

### Post by Robertjm on 2010-02-06
I actually got into my linux installation, which is:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2) Gecko/20100125 Ubuntu/10.04 (lucid) Firefox/3.6 (.NET CLR 3.5.30729)

The Windows installation should be the same.

I think the problem may be in the NTSF partition not automatically being mounted. I clicked on Places and navigated to the shared partition to copy a file and then noticed a HDD icon appear on my desktop. Then, when I tried to get into Firefox it worked. 

Haven't been back over to Windows yet to test the theory.

---

