---
title: "Installing Breezy on multiple machines"
date: 2006-05-25
forum: Installation &amp; Upgrades
---

### Post by uddunderline on 2006-05-25
Hi all,

I have a bunch of machines that will be installed at school. They are in the same LAN. We decided to put Linux on them. As i'm also a user of Ubuntu so I convince my colleagues to try Ubuntu Breezy.

Well, the headache comes when you have to install 50 PCs in a day with the same OS and configuration by using CD-ROM.

I'd like to know if there's a way to create a set up server facilitating this multiple machine installation via network?

Thanks before hand for the recommendation and help.

Udd

---

### Post by frodon on 2006-05-25
For all the PC which are exactly the same do the install once on one of them then create an image of the linux partition, and just paste this image on the other computers.
If they run also windows and you want them to dual boot then you will have to install GRUB with the install CD.

---

### Post by sanjayjainuk on 2006-05-25
Will that work for iMacs? I have 20 G3s that I'd like to install xubuntu and then load the educational games etc.... again, this is going in to a school. Edubuntu is too slow on them.

If yes, how do you "create an image of the linux partition"?

Thanks
Sanjay

---

### Post by frodon on 2006-05-26
You can use partimage to do that for example, unfortunately it's not on the ubuntu live CD and you will need a live CD with partimage to put the image on another computer so i advice you to download the knoppix live CD which include partimage.

links : 
[http://www.knoppix.org/](http://www.knoppix.org/)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

