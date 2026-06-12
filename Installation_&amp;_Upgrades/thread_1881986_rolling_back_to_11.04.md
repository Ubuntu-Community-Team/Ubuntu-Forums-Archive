---
title: "rolling back to 11.04"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by hanansela on 2011-11-16
Hello
I got tired of  ubuntu 11.10. After three weeks of heavy use I found that it is less user friendly than the gnome classic of 11.04.   The gnome options in 11.10 seems not appealing at all. I have decided to roll back to 11.04. I do not know if i did the right thing,  but I have installed 11.04 side by side with 11.10 (on two separate partitions). Now I have an empty 11.04 system with no additional software installed and no documents. I can  copy all my files from one system to the other but is there a way to get all the installed software with out re installing them one by one?   Alternativly,  is there is a way to roll back 11.10 to 11.04 on the 11.10 partition? and to keep all my installations and personal files? 
Thank you

---

### Post by TBABill on 2011-11-16
They use different repos so I assume packages are different for each, particularly since one is Gnome 2 and the other is Gnome 3. Best bet is to move all your personal files (office docs, pictures, MP3, videos, etc.) after reinstalling 11.04. There is no mechanism in place to roll back and I doubt you'd want to share installed apps between different distros. Best and safest bet is to reinstall 11.04 and start from scratch.

---

### Post by ghostborg on 2011-11-16
Backup,Backup,Backup my friend.

---

### Post by philinux on 2011-11-16
> **hanansela said:**
> Hello
I got tired of  ubuntu 11.10. After three weeks of heavy use I found that it is less user friendly than the gnome classic of 11.04.   The gnome options in 11.10 seems not appealing at all. I have decided to roll back to 11.04. I do not know if i did the right thing,  but I have installed 11.04 side by side with 11.10 (on two separate partitions). Now I have an empty 11.04 system with no additional software installed and no documents. I can  copy all my files from one system to the other but is there a way to get all the installed software with out re installing them one by one?   Alternativly,  is there is a way to roll back 11.10 to 11.04 on the 11.10 partition? and to keep all my installations and personal files? 
Thank you

Unfortunately no. Reinstall after you've backed to important stuff. Or start a new thread to side out any problems you have. Remember one problem per thread.

---

### Post by castrojo on 2011-11-18
Also of note, if you boot off the old CD (11.04) it will tell you that you can "upgrade" back to 11.04, but this is actually broken:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/891711](https://bugs.launchpad.net/ubuntu-release-notes/+bug/891711)

If you want to follow along.

---

