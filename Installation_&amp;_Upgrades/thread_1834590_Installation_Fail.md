---
title: "Installation Fail"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by macboer on 2011-08-27
So this is what I've been up to:

I made a bootable Ubuntu CD and I could boot from it and it works perfectly, but when I tried to Install Ubuntu it gave me a " clean your dvd/cd drive or your hdd is faulty" error-popup.

So, I made a Bootable USB drive, and it gives me exactly the same error on exactly the same % of the installation process. I have no problem when I run Ubuntu from the USB drive.

What can be the problem?
The machine is 7 years old and I guess the HDD might be faulty, but I haven't had any previous "HDD problems" with it running Windows XP.

Thanks in advance.

---

### Post by Quackers on 2011-08-27
Welcome to UF :-)
Have you checked the md5sum od the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by macboer on 2011-08-28
will check that out THANKS A BUNCH!

---

### Post by macboer on 2011-08-28
Where is a good place to download an .iso???

---

### Post by coffeecat on 2011-08-28
> **macboer said:**
> Where is a good place to download an .iso???

If you made a bootable Ubuntu CD, you already have the ISO. Do you mean that the md5sum check failed on the ISO you have? If so, this is where you go:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Click on "Get Ubuntu".

If the ISO passed the md5sum test, there is something else you can check. Boot up the live CD and choose "try Ubuntu". Then open the Disk Utility application and click on the internal hard drive in the left pane. See if there is any mention of SMART in the right pane and do a self-test if SMART is supported in your hard drive.

---

### Post by macboer on 2011-08-28
I compared my hash (that I got through the TERMINAL to the list of hashes on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and I couldn't find my hash "b6f83ad0dda11507dc5e150dd1312273".

So, now I'm downloading a new .iso file.

Is this the right procedure?

I checked the SMART Status of the HDD and it says "DISK IS HEALTHY" :)

---

### Post by coffeecat on 2011-08-28
> **macboer said:**
> I compared my hash (that I got through the TERMINAL to the list of hashes on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and I couldn't find my hash "b6f83ad0dda11507dc5e150dd1312273".

Which ISO did you download originally? What is its filename?

---

### Post by macboer on 2011-08-28
File Name: 

**ubuntu-10.04.3-desktop-i386.iso**

---

### Post by coffeecat on 2011-08-28
> **macboer said:**
> File Name: 

**ubuntu-10.04.3-desktop-i386.iso**

Yup! Your ISO is definitely giving you the wrong md5 hash. :) Good luck with the download. Let us know how you get on.

---

### Post by macboer on 2011-08-28
THANKS FOR YOUR HELP!

Will let you know how I solve it. It's the Ubuntu Way :P

---

### Post by macboer on 2011-08-28
THANKS FOR YOUR HELP!

Will let you know how I solve it. It's the Ubuntu Way :P

---

### Post by macboer on 2011-08-28
So This is what i'm doing:

I downloaded an iso from "http://releases.ubuntu.com/lucid/"

the UbuntuHash was correct and so I made an bootable USB from within the faulty Live CD UBUNTU.

THAT DIDN"T WORK! :(

so now I'm writing a Bootable CD from within OSX...

---

### Post by macboer on 2011-08-28
*feww* seems to be working now!

---

