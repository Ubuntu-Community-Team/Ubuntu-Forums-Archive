---
title: "Problem with dpkg --configure -a"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by 0623000 on 2008-11-13
First I would like to say "Hello" to all ubuntuforums.org members as this is my first contact.
Today I managed to prepare a 1GB USB Stick to run Ubuntu 8.10 (downloaded from [www.ubuntu.com](www.ubuntu.com)) on my Aspire One.
Looks good - feels good - but WLan did not work. Found out that 
"sudo apt-get install linux-backports-modules-intrepid-generic" should solve the problem. But I am getting the error: dpkg was interrupted, manually run dpkg --configure -a to correct the problem
When I do so theres an other error telling me, that there was a problem when parsing file /var/lib/dpkg/updates/0067 near line 1 Fieldname #padding
I took a look at this file - its full with:
#padding
#padding
#padding
.
.
.
anyone any idea how to solve this?
Chris

---

### Post by oilchangeguy on 2008-11-13
in the terminal type sudo dpkg --configure -a and press enter.

---

### Post by 0623000 on 2008-11-13
Thanks for your quick reply!
Thats what I did half the day - but always getting the "padding" error stated in my first thread.

---

### Post by rv53705 on 2008-11-13
I'm getting the same problem. ([http://ubuntuforums.org/showthread.php?t=981003](http://ubuntuforums.org/showthread.php?t=981003))

---

### Post by Steve1961 on 2008-11-13
> **0623000 said:**
> First I would like to say "Hello" to all ubuntuforums.org members as this is my first contact.
Today I managed to prepare a 1GB USB Stick to run Ubuntu 8.10 (downloaded from [www.ubuntu.com](www.ubuntu.com)) on my Aspire One.
Looks good - feels good - but WLan did not work. Found out that 
"sudo apt-get install linux-backports-modules-intrepid-generic" should solve the problem. But I am getting the error: dpkg was interrupted, manually run dpkg --configure -a to correct the problem
When I do so theres an other error telling me, that there was a problem when parsing file /var/lib/dpkg/updates/0067 near line 1 Fieldname #padding
I took a look at this file - its full with:
#padding
#padding
#padding
.

.
anyone any idea how to solve this?
Chris

Well I don't have that file in /var/lib/dpkg/updates/ so I'd be tempted to recommend getting rid of it, or at least move it somewhere else.  However, that's what I would do and there might be a better way.  perhaps wait to see of there are other suggestions.  Also, you might try running sudo apt-get clean to see if that helps.

---

### Post by 0623000 on 2008-11-13
Hy Steve 1961!
Will try and report!
Thanks

---

### Post by 0623000 on 2008-11-13
Well - removing the file solved the problem - but the next appeared...
some files in bad condition (think it was the update-manager)....
I will now try to copy the whole image to the stick again.
Good luck rv53705

---

### Post by cariboo on 2008-11-13
Have you tried going to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages?

Jim

---

### Post by Pumalite on 2008-11-13
You can also try in the Terminal:
sudeo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

