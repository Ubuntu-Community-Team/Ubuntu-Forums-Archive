---
title: "Hardware Raid issue - New install (not onto Raid)"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Xanadu79 on 2008-10-23
Hello All,

   I'm moving off of the darkside and onto Ubuntu for my home fileserver. I have installed Ubuntu 8.04 onto a test box and installed all the software I would use just to make sure it met my needs and it does. Here's my issue:

I currently have a windows 2003 server with a disk for the OS and a Sil PCI RAID 1 card in it with 2 500 gb drives attached. I have them about half full. 

I did a boot from CD to check and make sure that Ubuntu would recognize my controller and when I do Ubuntu sees both disks in the array instead of the 1 array. I can't find any posts about this. Everyone that has posted about this issue is using a mobo raid controller (fake raid). Can anyone help?

I don't want to install Ubuntu onto the array. I want to keep the data on the array intact and install Ubuntu on the 3rd system disk.

Any thoughts?

Thanks in advance!
Landon

---

### Post by Xanadu79 on 2008-10-23
Ok, looks like my card is Software Raid. Even so, the Fake Raid setup guide assumes I want to install ubuntu onto the array, which I don't. Any thoughts?

Thanks,
Landon

---

### Post by Xanadu79 on 2008-10-24
No one have any ideas??

---

### Post by kubug on 2008-12-08
Xanadu,

I came across your post because I was researching the PCI card you were using. 

As far as your question goes, I would look at the 'dmraid' package to be able to view the RAID array.

Do you know what chipset the RAID card has? The reason I am asking is to make sure 'dmraid' will support your card.

By default, ubuntu doesn't load dmraid. One distro that does load dmraid is Fedora. Maybe you want to try that one and see if you can see the RAID array. If yes, you can always come back to ubuntu ;) and simply install the dmraid package and configure it to see the RAID.

Hopefully this helped. Maybe you want to look at some of the docs for fakeraid, dmraid and ubuntu. I made mine work. I am quite positive you will be able to get your working.

---

