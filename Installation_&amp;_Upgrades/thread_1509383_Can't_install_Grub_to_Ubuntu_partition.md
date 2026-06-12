---
title: "Can't install Grub to Ubuntu partition"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by setcho on 2010-06-14
Hi,

I am trying to dual boot XP and Ubuntu Netbook Remix 10.04 on my Samsung NC10 using Easybcd 2 (build 100) however when I press the 'Advanced' button to give me the choice of where to install the bootloader I only have the option sda1 (which is XP) and sda-1. If I choose sda-1 it doesn't allow me to proceed any further as the 'Next' button is greyed out.

I didn't have this problem with UNR 9.10 which I ran for a while last year so just to check that it wasn't a problem with my hardware I downloaded UNR 9.10 again and tried to do the same thing. This time when I press the 'Advanced' button I am given the option to install Grub in either sda1 or sda5, which is as it should be. I then chose sda5 completed the install and successfully used Easybcd to boot UNR 9.10. 

So my question is, does anyone have an idea why there is a difference between the two?

Further info: I patitioned my drive so that XP had 80 GB and 69 GB was left as free space. During the 10.04 install I noticed that the partitioner was showing incorrect values when I chose to install on the largest free space, it said XP was 85 GB and the Ubuntu partition would be 75 GB (total is larger than my HD of 150 GB). At the same point in the 9.10 install I was given the correct values.

Both installs where done using the Universal usb installer method. I also tried Ubuntu 10.04 and I still only got the sda-1 option.

The above has offered me a workaround, I am currently in the process of upgrading from 9.10 to 10.04 via the online update however it is taking a long time and as I like to hop between distros quite often I would like to resolve this issue so that I can reinstall UNR 10.04 quickly when I want to.

Any suggestions would be appreciated.

Thanks.

---

### Post by darkod on 2010-06-14
Suggestion #1: Simply put grub2 on the MBR.

Otherwise, I don't know why it doesn't allow you to install to a partition. Maybe because it needs to be forced and they decided to take that option away during the installer. I know you can force it from terminal later on.

I have never tried to put grub2 on a partition anyway.

---

### Post by setcho on 2010-06-15
Thanks for the reply.

Has the option to install grub to it's own partition really been removed in 10.04? It would be foolish it had been. 

When I searched the forum for dual boots and easybcd I found some replies that mentioned that in order to dual boot grub needs to be installed to its own partition so it can't have been removed.

Does anyone else have any suggestions?

---

### Post by Mark Phelps on 2010-06-15
> **setcho said:**
> Hi, I am trying to dual boot XP and Ubuntu Netbook Remix 10.04 on my Samsung NC10 using Easybcd 2 (build 100) however when I press the 'Advanced' button to give me the choice of where to install the bootloader I only have the option sda1 (which is XP) and sda-1. If I choose sda-1 it doesn't allow me to proceed any further as the 'Next' button is greyed out.

EasyBCD does NOT use GRUB; instead, it uses GRUB4DOS -- which, as the name implies, must be installed to an MS Windows formatted partition.

If you want to stay with EasyBCD, then go to the proper forum to get support -- the NeoSmart Technology forums.

If you want to use GRUB2 instead, then remove EasyBCD and follow the advice folks will give you here on using GRUB2.

IF you start messing around with having both GRUB4DOS and GRUB2 on your system, you'll quickly end up with something that is unbootable.

---

### Post by setcho on 2010-06-15
Apologies,  I think I may be confusing the terms Grub and Bootloader.

My question has nothing to do with easybcd. My question is why can I not install the bootloader to the Ubuntu partition?

As I mention above, I am given the option to install it on sda5 in UNR 9.10 but in UNR 10.04 I am only given the option sda-1 and when I try this I cannot proceed any further.

---

