---
title: "Install Truecrypt 6.3a on Ubuntu 10.04"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by woodfire on 2010-07-12
Hi, I have just shifted from windows to Ubuntu so I have little experience with this system.
I used Truecrypt in Windows and it worked pretty well. I tried to install the program on Ubuntu but got some problem. Here is what I did and the problems I got:
1. I downloaded the standard 32-bit tag.gz file from [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)
2. Extract the file onto desktop
3. Installed by double clicking and run in terminal or directly run in terminal (I assume they are equal)
4. Follow the instructions till 'Press Enter to exit'. 
For me it seems that the program is installed successfully, and the icon shows up in the Application- Accessories menu. However, it doesn't respond at all when I click the icon. 
Could anyone please help me out of this? For most of the software I used in Windows, I have already found equivalents that are working fine. And I really don't want to go back to Windows because this program. 
Thanks a lot!

---

### Post by woodfire on 2010-07-12
If someone knows that there is another program that can decrypt the volume created by Truecrypt in Windows, I would also appreciate the information.

---

### Post by John-B on 2010-07-12
woodfire,
I suggest you un install and then reinstall.
I have TrueCrypt 6.3a working fine on two computers using Ubuntu 10.04 :p

---

### Post by woodfire on 2010-07-12
Thank you for your suggestion. Here is another naive question: how do I uninstall the Truecrypt? I can not find it from Synaptic. :popcorn:

---

### Post by woodfire on 2010-07-12
OK, I uninstalled the program using the code 'sudo truecrypt-uninstall.sh'.
Then I reinstalled it, it is still the same, no response when I click it.
I can re-uninstall it, though:popcorn:

---

### Post by confused57 on 2010-07-12
Try right-click on Applications--->Edit Menus, click on Accessories in the left pane, double-click Truecrypt in the right pane, in the Command line just enter "truecrypt"(without quotes).  See if it works now.

---

### Post by woodfire on 2010-07-22
> **confused57 said:**
> Try right-click on Applications--->Edit Menus, click on Accessories in the left pane, double-click Truecrypt in the right pane, in the Command line just enter &quot;truecrypt&quot;(without quotes).  See if it works now.

 Thanks for the advise.  I haven't realized that there was no "Truecrypt" in the right panel of the Accessories until I right clicked and Edit the menu. I tried to create an item called "Truecrypt" but had no idea where to find the application to make the linkage.  Someone to help me out of this?

---

### Post by confused57 on 2010-07-22
> **woodfire said:**
> Thanks for the advise.  I haven't realized that there was no "Truecrypt" in the right panel of the Accessories until I right clicked and Edit the menu. I tried to create an item called "Truecrypt" but had no idea where to find the application to make the linkage.  Someone to help me out of this?
Just entering "truecrypt"(without quotes) should work, but to be sure you could enter "/usr/bin/truecrypt"(again, without quotes) in the "Command" line.

---

### Post by woodfire on 2010-07-22
> **confused57 said:**
> Just entering &quot;truecrypt&quot;(without quotes) should work, but to be sure you could enter &quot;/usr/bin/truecrypt&quot;(again, without quotes) in the &quot;Command&quot; line.

 Unfortunately, it still doesn't work. So wired

---

### Post by MrGrey1 on 2010-08-10
Same problem here.
10.04 with true-crypt 7. Extracted the file to desktop, double clicked to run. Apparently installed successfully. True-crypt icon appears in the Applications menu but trying to run it nothing happens. Upon reboot the icon disappears.
Trying to run from terminal:

~$ truecrypt 
bash: /usr/bin/truecrypt: cannot execute binary file

Any ideas?

EDIT: after removing 'easycrypt' the true-crypt icon is now staying in the menu after reboot. It is however still not running.

EDIT 2: My stupid mistake. Was trying to run 64 bit on 32 bit. 
Note to self: keep better track of which system has which version OS... :)

---

### Post by ponchi_trip on 2010-10-27
any command for install truecrypt directly?????????

---

