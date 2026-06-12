---
title: "New laptop with four partitions?"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-11-10
I have just met with an acquaintance who has fairly recently purchased a new laptop. It is a widescreen Samsung with 3GB ram, 500 GB hard drive and Windows 7.
Retail price in UK around 400 UK pounds he said.

I tried an Ubuntu 10.04.1 live CD, out of interest, and it all seemed to work ok, video, audio, wireless.

However, I was interested to see that the hard drive is arranged as two small (restore) partitions and also two large partitions. The large ones are each more than 230 GB. One of these seems to have only about 15GB contents, which apparently includes some system stuff. The other only has 30GB  contents anyway (light user....).

Thus, all four primary partitions are allocated.

There is still more than enough room for another one (or more) OS's..... and I trust that the Ubuntu installer would work itself into an extended partition existence (??). 

Has anyone got experience of letting the recent installers run with this sort of environment?

I know that wise council suggests to avoid conspiracy theory when a simple foul up will explain things, but it does seem strange. Any comments anyone?

---

### Post by oldfred on 2010-11-10
Many new systems install all 4 partitions. Windows uses a (hidden) boot/restore and a main partition. Vendors then do not provide an install DVD but offer an image to restore system to as purchased (eraseing all changes) and then they have some utilites. Some special keys may be directly connected to the utilities via either BIOS or modified windows boot.

If you can make restore DVD and/or windows repair CD from the restore partition, you should do that. Some only let you write one restore DVD and if it does not work, you have to go back to the vendor and buy one.

You will have to decide to delete one partition. I would not want to restore windows except as last recourse as it deletes every change and upgrade. Often the utilities do not offer much and as a small partition can be easily backed up.

Back up every thing important and use windows MMC to modify the size of the main windows partition. Reboot windows several times as it will want to run chkdsk or other repairs after resizing.

Once you have deleted one partition you can use gparted or the installer to make a new extended partition and add many logical partitions for Ubuntu.


Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

