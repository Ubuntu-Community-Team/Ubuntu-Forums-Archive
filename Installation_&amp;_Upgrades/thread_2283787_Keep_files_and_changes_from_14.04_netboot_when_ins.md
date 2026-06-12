---
title: "Keep files and changes from 14.04 netboot when installed"
date: 2015-06-24
forum: Installation &amp; Upgrades
---

### Post by Jake_Lester on 2015-06-24
I've got a 14.04 Live CD running on our netboot server. I'd like to be able to save files to a location (/etc/skel) while in the live environment, then have them persist when Ubuntu gets installed to the hard drive. Is this possible? I found a bunch of info on persistence using a USB drive, but that seemed to only apply to live boots. Thanks!

---

### Post by ajgreeny on 2015-06-24
I think you will need to be very careful doing something like this in a working server environment as you could easily damage the server filesystem itself.  What exactly are you wanting to do and why?  Are you going to install this live system over the current server or have I totally missed your point?

The only way you can save files to a folder on your server's system will be as root, and as you can not run the live GUI as root I think you will have to create and save the files you want in the live system, then copy then with terminal to the location you want with the **sudo cp **command, but I think it is too risky to go ahead without knowing more about your intentions.

---

### Post by Jake_Lester on 2015-06-24
No, sorry, I just realized OP was extremely confusing. I'm not trying to save anything to the server. I'd like to be able to netboot a computer into a 'live' Ubuntu (we already have this ability), save some files to a location in that live environment, then install Ubuntu to that computer with the files saved to the hard drive. 

So basically I'd like to boot a computer into a live Ubuntu environment, create a file in that environment, then have that file exist on the hard drive when I finally install Ubuntu from the live environment. If that makes any sense at all :)

---

### Post by ajgreeny on 2015-06-24
OK, I've now followed what you want.  Regrettably I do not know if it is possible in any simple way, nor actually in any complicated way, depending on exactly what this change is that you want to the live USB.

However, have a look at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) to see if that might fit the bill for you.  I have never used this and know only what I read in that web-page so will have to leave you to work it out for yourself..

---

### Post by Jake_Lester on 2015-06-24
Thanks for the advice! I've checked out that guide, I think it might actually help in a roundabout way.

I have a program that I run on the live CD that spits out a txt file, which I'd like to save to /etc/skel. I could potentially store that txt file to a unique location on a local server. If I customize the live CD to have a script (with an entry in init.d) that checks to see if that file exists and copies it over, that boot-up script (and init.d config) would be installed to the HDD and would run when the computer boots to the hard drive (right?). If it's successful, the script could delete the init.d config which would stop it from checking on every single boot. Maybe....

---

