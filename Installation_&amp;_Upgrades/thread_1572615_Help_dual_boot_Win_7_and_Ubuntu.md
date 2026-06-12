---
title: "Help dual boot Win 7 and Ubuntu"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by SmoothFreeze on 2010-09-11
Ok so I downloaded ubuntu-10.04-netbook-i386.iso and installed it to my thumb drive. I can run ubuntu from my thumbdrive perfectly. But when I wanted to install Ubuntu,it did not show the "install ubuntu side by side" option. Can anyone help? I already tried partitioning in win 7 from my computer>manage>disk management and gave 25gb of free space. Still not able to install. I tried out wubi but it takes 2 days to download the iso. So, can anyone help?

---

### Post by rory526 on 2010-09-11
Choose to manually specify the partitioning of the disk and create a new linux partition in the free space.

---

### Post by SmoothFreeze on 2010-09-11
how do i exactly do that? check out the screenshots attached
[IMG]http://img820.imageshack.us/img820/8936/screenshot1ub.png[/IMG]
[IMG]http://img835.imageshack.us/img835/1788/screenshot2ma.png[/IMG]

---

### Post by Cavsfan on 2010-09-11
I dual boot windows 7 and Lucid and I did it exactly like your pics look like.
You just need to create a swap file of about 2048 of the unused space - it will prompt you.
Then create the rest of the space ext4 with a "/".
That should do it.

But, if you wanted to free up more than 21GB for Ubuntu, go into Windows 7 and in the search box above the start button type "disk man" and disk manager should appear.
You can then click on one of your existing partitions (maybe more than one) and then click on "shrink" and see how much can be freed up.

---

### Post by Cavsfan on 2010-09-11
I had to defrag mine to be able to free 100GB, you may not need to.

---

### Post by SmoothFreeze on 2010-09-11
> **Cavsfan said:**
> I dual boot windows 7 and Lucid and I did it exactly like your pics look like.
You just need to create a swap file of about 2048 of the unused space - it will prompt you.
Then create the rest of the space ext4 with a "/".
That should do it.

But, if you wanted to free up more than 21GB for Ubuntu, go into Windows 7 and in the search box above the start button type "disk man" and disk manager should appear.
You can then click on one of your existing partitions (maybe more than one) and then click on "shrink" and see how much can be freed up.

21gb is fine for me atleast for now. How do I create a "swap file"? I'm stuck on the 2nd screenshot.

---

### Post by Cavsfan on 2010-09-11
Puran free edition offers a boottime defrag that is better than windows default or defraggler even.

[[COLOR=blue]_Puran Free Edition Download_[/COLOR]]("http://www.snapfiles.com/get/puranfree.html")

---

### Post by Cavsfan on 2010-09-11
> **SmoothFreeze said:**
> 21gb is fine for me atleast for now. How do I create a "swap file"? I'm stuck on the 2nd screenshot.

Just click on the Unused space then click on forward and it will ask you.

---

### Post by SmoothFreeze on 2010-09-11
> **Cavsfan said:**
> Just click on the Unused space then click on forward and it will ask you.

Thanks for the link. The Unused space shows up as unusable (look properly in the 2nd screenshot) Hmm i clicked forward and it gives me an error.

---

### Post by Cavsfan on 2010-09-11
> **SmoothFreeze said:**
> Thanks for the link. The Unused space shows up as unusable (look properly in the 2nd screenshot) Hmm i clicked forward and it gives me an error.
What happens when you click on the unused space? Can you click on any buttons below that?
I looked at you pic again and I don't think you could. I am not sure what the problem is.
Hopefully someone with more experience than I will come along and help.
I am wondering why it shows 2 windows 7 boot loaders.

You might try my suggestion to defrag at boot and see if you can free up more space.
I know you can only have 4 partitions on one hard drive and you already have 4.

You should be able to create logical drives though. I guess the sda4 is your recovery partition.

EDIT: you can have 2 logical partitions

---

### Post by Cavsfan on 2010-09-11
Hopefully this link will help - 

[[COLOR=blue]_Partitioning your disks_[/COLOR]]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")

---

### Post by SmoothFreeze on 2010-09-11
> **Cavsfan said:**
> What happens when you click on the unused space? Can you click on any buttons below that?
I looked at you pic again and I don't think you could. I am not sure what the problem is.
Hopefully someone with more experience than I will come along and help.
I am wondering why it shows 2 windows 7 boot loaders.

You might try my suggestion to defrag at boot and see if you can free up more space.
I know you can only have 4 partitions on one hard drive and you already have 4.

You should be able to create logical drives though. I guess the sda4 is your recovery partition.

EDIT: you can have 2 logical partitions

There is a revert button but does nothing. Will try defragging in the morning later. Thanks for the suggestion. Anyone else who can help,pls post... Any help will be greatly appreciated.

---

### Post by wilee-nilee on 2010-09-11
First when you take a screen shot use the take a screenshot but use the select an area to grab this will give us a picture that doesn't go over the whole page.

Take a screen shot of gparted it looks like you have 4 primary partitions already that is the limit. Any HD can have at the most 3 primaries and a extended partition for as many logical partitions you can fit in its space, or just four primaries.
[ATTACH]169154[/ATTACH]

---

