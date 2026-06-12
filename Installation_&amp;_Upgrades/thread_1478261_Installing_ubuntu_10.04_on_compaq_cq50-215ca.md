---
title: "Installing ubuntu 10.04 on compaq cq50-215ca"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by m_raguraman on 2010-05-09
Hi,
    I am trying to install Ubuntu 10.04 on my Compaq CQ50-215CA laptop. But, instead I am seeing a blank screen. This laptop has Geforce Nvidia 8200G M video card.

Not sure whether it is related to the video card or not, but thought it is better to get tips from people who were successful in installing on this type of laptop.

Many thanks for you guys help.

Ragu

---

### Post by Catharsis on 2010-05-09
Do you have Lucid installed or are you trying to boot the LiveCD?

---

### Post by m_raguraman on 2010-05-09
I am trying to bring it up with Live CD and if I can do that I would like to go ahead and install it on the disk.

Thanks for your help

Ragu

---

### Post by Catharsis on 2010-05-09
When you get to the purple screen with a keyboard and stickfigure at the bottom, hit Enter. Then select your language, and (making sure "Try Ubuntu without making changes" is selected) press F6 at the menu. Then select "nomodeset". Hit enter. Does that get you into the LiveCD?

---

### Post by m_raguraman on 2010-05-09
After I select nomodeset and enter for *Try Ubuntu without installing *the screen is frozen. I waited for quite a while for it to comeup.

I am still missing something in this setup.

Thanks again for your help

Ragu

---

### Post by Catharsis on 2010-05-09
Try checking if your iso was downloaded correctly:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, check the integrity of the LiveCD in the menu by selecting "Check Disc Integrity" or something like that.

---

### Post by m_raguraman on 2010-05-10
md5 checksum was fine.

So, I tried to use wubi to install the iso and was successful. But it doesn't explain why install using cdrom doesn't work.

At least it does say to me that Ubuntu can come up in my laptop.

Thanks a lot Catharsis for giving a helping hand. Appreciate it a lot.

---

