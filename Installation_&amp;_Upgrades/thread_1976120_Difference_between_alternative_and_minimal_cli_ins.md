---
title: "Difference between alternative and minimal cli install?"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2012-05-08
Hi all,

Simple questions before I go ahead and do one of the following: If I download the Xubuntu alternate ISO, choose to do a CLI install and add apps, is this going to be any different from downloading the Ubuntu minimal install ISO and doing the same? Will it be any lighter or identical or different in any way? If so, how?

One more; I imagine I can choose where to put grub during the manual partitioning section? I've just recently done a 10.04 minimal (which went great) but couldn't find that option. (This one's going to be 12.04 incidentally ... it would be 10.04 but that's never played nice with my machine which is why I was forced to use 10.10 which did but is now at EOL, if you follow me!)

All thoughts welcome. Cheers. ;)

---

### Post by mips on 2012-05-08
> **Bucky Ball said:**
> Hi all,

Simple questions before I go ahead and do one of the following: If I download the Xubuntu alternate ISO, choose to do a CLI install and add apps, is this going to be any different from downloading the Ubuntu minimal install ISO and doing the same? Will it be any lighter or identical or different in any way? If so, how?

They will both give you the same result BUT:
Minimal install cd will get the **latest** packages from the servers when you install.
Alternate install cd will install packages from the cd and afterwards if you do an update there might be a few newer packages it will download and install. Right now there are not that many new updates.

The alternate cd is nice to have around though in case you quickly need to do a full install.
I used the alternate xubuntu 64bit cd to do a base install and then I installed xfce 4.10 (ubuntu comes with 4.8) which was just released via a PPA.



> **Bucky Ball said:**
> 
One more; I imagine I can choose where to put grub during the manual partitioning section?

Yes, towards the end of the installation it prompts you for the location to install grub2 to.

---

### Post by Bucky Ball on 2012-05-08
Cheers mips. ;)

---

