---
title: "Installation freezes after 2nd step &quot;Preparing to install Ubuntu&quot;"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by akshatk on 2012-12-23
m facing issue while trying to install lubuntu 12.10.

During installation, it stuck after 2nd step (step after selecting language) "Preparing to install Ubuntu".

m using a bootable cd, before writing iso file to cd, i verified its mdsum value, burnt it with lowest rate, also checked the cd via "check disc for errors" before installation.

Its stuck at this stage for 45 mins.

please help ??

---

### Post by Dennis N on 2012-12-23
> **akshatk said:**
> m facing issue while trying to install lubuntu 12.10.

During installation, it stuck after 2nd step (step after selecting language) "Preparing to install Ubuntu".

m using a bootable cd, before writing iso file to cd, i verified its mdsum value, burnt it with lowest rate, also checked the cd via "check disc for errors" before installation.

Its stuck at this stage for 45 mins.

please help ??

A number of people have this problem. A solution is to use the alternate CD and the installation should complete:

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

Note: this alternate installer is text based, and you navigate with the keyboard. Just read the directions carefully.

---

### Post by Toadmund on 2012-12-30
Having this problem as well, actually got past it the first time, then I wasn't sure about the install, so I hit back.
Then tried again and again, messed around with gparted, still no luck.
Then tried ext2, worked once, but I selected a wrong option, and went back again.
Many attempts, no luck.

Two more disk coasters I have now.

To add:
I thought this was a Ubuntu thread, like the title indicates.
Looks like I may have to find an alternative to Ubuntu now, as alternate CD's are discontinued.
First time I have ever had this problem and the first time I ever needed an alternate CD.

---

### Post by Toadmund on 2012-12-30
Problem solved, decided to try Mint 14 Nadia.
So far so good.

---

### Post by ibjsb4 on 2012-12-30
> **akshatk said:**
> m facing issue while trying to install lubuntu 12.10.

During installation, it stuck after 2nd step (step after selecting language) "Preparing to install Ubuntu".

m using a bootable cd, before writing iso file to cd, i verified its mdsum value, burnt it with lowest rate, also checked the cd via "check disc for errors" before installation.

Its stuck at this stage for 45 mins.

please help ??

I wonder if its ubiquity-slideshow-lubuntu giving you trouble.

Fire up the live CD and go to try Lubuntu.  Then open up a terminal and enter:

```
sudo apt-get remove ubiquity-slideshow-lubuntu
```

And now from that point, click on install Lubuntu.

---

