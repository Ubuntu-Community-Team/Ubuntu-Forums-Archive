---
title: "Lubuntu on Compaq Armada E500"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by live4suffer on 2011-05-03
I have a Compaq Armada E500 with 192 MB Sdram and Intel Pentium III 850.0 MHz.

My problem is; after booting from CD-Rom , I select either "Try Lubuntu" or "Install Lubuntu" , it never goes further than Purple Splash Screen with text "Ubuntu 10.10" . It took more than an hour and I watched the screen but nothing happened. Why cannot I go further? I want to use this old pc and I was told that Lubuntu would be great on it. 

Any help would be great. 

Thanks .

---

### Post by mikewhatever on 2011-05-03
From the Lubuntu system requirements:
> To use the graphical installer from the live-cd, you need at least 256 MB of memory. You need to use the "Install Lubuntu" entry when you boot the Live-CD. 

You simply don't have enough RAM to run the live cd.

---

### Post by live4suffer on 2011-05-03
> **mikewhatever said:**
> From the Lubuntu system requirements:
```
To use the graphical installer from the live-cd, you need at least 256 MB of memory. You need to use the "Install Lubuntu" entry when you boot the Live-CD. 
```

You simply don't have enough RAM to run the live cd.

Thanks but when I use "Install Lubuntu" , nothing happens again. I wait, wait and wait .... It never comes to Installation progress or Installation screen

---

### Post by mikewhatever on 2011-05-03
The graphical installer needs at least 256MB of RAM which you don't have. You could use the Alternate Ubuntu cd to install the base command line system and then add the 'lubuntu-desktop' metapackage. That's probably the only way to install something like Lubuntu. On the other hand, there are even more light weight distros like Puppy Linux, AntiX, and DSL that you could try.

---

### Post by 4AD on 2011-05-18
A way to install on an Armada E500 is using the minimal ubuntu iso:
[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

 The long version: Instead of using Ubuntu 11.04 Natty Narwhal Minimal CD (11.04 had a problem with grub2 in my case) go to [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and download Ubuntu 10.04 Lucid Lynx Minimal CD.  After rebooting and logging in, install the update-manager and select the new version 10.10. After this upgrade is completed select 11.04 and your done.

---

### Post by mörgæs on 2011-05-18
Whoa, an E 500! I actually have one of those. 

Here is what I did:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

---

### Post by sTpny on 2011-07-02
I just put ubuntu on a friends e500 not too long ago.. I had to use the alternate installation CD, but it works just fine.  No 3D graphics though.  As I understand it, the 3D is down due to a security issue that will be fixed sometime in the near future.

---

### Post by mörgæs on 2011-07-02
I doubt such a computer will ever run 3D graphics.

---

