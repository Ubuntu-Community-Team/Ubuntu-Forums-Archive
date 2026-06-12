---
title: "Trying installation with opensuse 11.3 present"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by vigneron on 2010-10-05
I am trying to install Kbuntu and I currently have OpenSuse 11.3 on my system.  I really don't want OpenSuse anymore but am having problems installing Kubuntu with OpenSuse already installed.

I tried to install from the live Kbuntu CD as a side by side installation.  I got an error message saying my /dev/sda7 was busy.  This is where my /home of Suse is located.

I downloaded gparted while running the live Kbuntu CD.  I was going to delete my current linux partitions.   I changed the root password but still can not run gparted.

Anyone know how to make it work or another work around to get Kbuntu installed and dual booting with windoze? - I don't care if suse installation gets deleted?

Would installing Kbuntu using largest partition option give me problems on bootup by not recognizing Windoze?  

Where is the best place to put Grub?

---

### Post by andrewthomas on 2010-10-05
> **vigneron said:**
>  I am trying to install Kbuntu and I currently have OpenSuse 11.3 on my system. I really don't want OpenSuse anymore but am having problems installing Kubuntu with OpenSuse already installed.
 
I tried to install from the live Kbuntu CD as a side by side installation. I got an error message saying my /dev/sda7 was busy. This is where my /home of Suse is located.
 
I downloaded gparted while running the live Kbuntu CD. I was going to delete my current linux partitions. I changed the root password but still can not run gparted.
 
Anyone know how to make it work or another work around to get Kbuntu installed and dual booting with windoze? - I don't care if suse installation gets deleted?
 
Would installing Kbuntu using largest partition option give me problems on bootup by not recognizing Windoze? 
 
Where is the best place to put Grub? 
You should select specify partitions manually
 
( see [https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu) )
 
Then choose your suse partitions (/ and /home and swap) and choose to format them.
 
You should have no problems with grub2 picking up windows and I would let it tnstall to the MBR.

---

### Post by vigneron on 2010-10-06
> **andrewthomas said:**
> You should select specify partitions manually
 
( see [https://help.ubuntu.com/community/GraphicalInstall/Kubuntu](https://help.ubuntu.com/community/GraphicalInstall/Kubuntu) )
 
Then choose your suse partitions (/ and /home and swap) and choose to format them.
 
You should have no problems with grub2 picking up windows and I would let it tnstall to the MBR.


Thanks, that worked

---

### Post by andrewthomas on 2010-10-06
You're welcome.  Glad to be of help.

---

