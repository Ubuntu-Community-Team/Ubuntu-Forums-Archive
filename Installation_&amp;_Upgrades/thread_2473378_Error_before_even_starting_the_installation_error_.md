---
title: "Error before even starting the installation error JBD2 Error -5"
date: 2022-04-02
forum: Installation &amp; Upgrades
---

### Post by blueju on 2022-04-02
Hi all,

I have a problem when trying to install Ubuntu (I also tried Xubuntu) on my Chuwi Larkbox.
I created a live-usb via Etcher and also tried via Rufus. When I try to start from it the automatic file checking is done and is passing, but afterwards I get the following errors.

[IMG]https://drive.google.com/file/d/1QhALpoATINvge59BbKCmnHa0e6de5OKy/view?usp=sharing[/IMG][https://drive.google.com/file/d/1QhALpoATINvge59BbKCmnHa0e6de5OKy/view?usp=sharing](https://drive.google.com/file/d/1QhALpoATINvge59BbKCmnHa0e6de5OKy/view?usp=sharing) (I tried to attach it or enter the picture directly but didn't work somehow.

I had ubuntu already working before, but I changed some setting in the bios which bricked the Larkbox, I had to manually reflash the bios. 
After I did that I got the same error with the already installed version of ubuntu. Therefore I tried reinstalling which gave also the error.
Installing windows worked on the other hand, but I dont want to use Windows on that machine.

Any clues or help on what the error means or how to resolve it even would be very welcome!
I am suspecting a bios issue with the version i have reflashed but maybe someone knows that error already

Many thanks,
Julian
[IMG]https://ibb.co/YBy15TL[/IMG]
[IMG]https://drive.google.com/file/d/1QhALpoATINvge59BbKCmnHa0e6de5OKy/view?usp=sharing[/IMG]

---

### Post by Bashing-om on 2022-04-02
Hello blueju.

Sorry to read that you are experiencing such difficulties to install :(

From the screen shot one can surmise that the partition table on the drive, sda, is hosed.

What toy might try -
from the liveUSB in "try ubuntu" mode. activate the gui tool Gparted, and delete the current partitions.
then:
1) verify the downloaded .ISO file:  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) Then once more check the copy to mefium - " check disk for defects" menu option
3) Try again to install - let the install wizard have control - " wipe disk and install ubuntu"

[INDENT]it is all in the process
[/INDENT]

---

