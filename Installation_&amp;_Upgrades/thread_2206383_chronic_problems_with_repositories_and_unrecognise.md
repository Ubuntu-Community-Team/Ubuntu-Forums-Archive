---
title: "chronic problems with repositories and unrecognised commands in the terminal 12.10"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by apiglet on 2014-02-18
Hello: 

My original problem was as stated in the title: missing repositories and packages that I could not install, getting dead ends while following forum advice, having commands in the terminal come up "unrecognised". 
I followed some advice to check for a better server, I pressed "recharge" (sorry translating from Spanish) in Synaptic. I got this message (translated from Spanish): "the repository indexes couldn't all be downloaded: the repositories aren't available or couldn't be contacted due to problems with your connection (there is no problem with it). Older ones will be used or if they don't exist, these will be ignored". Specific information inside the box: "Impossible to obtain cd rom:// Ubuntu 12.10 Quantal-Quetzal release (such and such, etc.)"
Then it says "Utilice apt-cdrom para hacer que APT reconozca este CD-ROM. apt-get update no se puede usar para añadir nuevos CD-ROM", which more or less means "use apt-cdrom to get APT to recognise this CD-ROM. apt-get update can't be used to add new CD-ROMs.
It says this several times.

Am I right in making a wild guess that the guy that sold me the computer and somewhat reluctantly put Ubuntu on it for me, may not have done it properly? I am guessing this because I have had so many problems following instructions to download packages, and follow instructions on forums, and now it is talking about a CD-ROM, which makes me think that something went wrong at the time someone input a CD-ROM into the computer to load the operating system.

Any advice?

Thank you!

---

### Post by Bucky Ball on 2014-02-18
It sounds like it is attempting to use the CD as a repository. This can be done and is not an oddity, but leaving it checked is an oversight. 

Open your Software Sources (you can get there via update manager and 'Settings' in the bottom left corner) and make sure the CD is unticked. Once you've done this, run these three commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors, please.

---

### Post by deadflowr on 2014-02-18
In case 12.10 didn't have "Update Manager"(I think that's when it changed to "software updater")  look and see if you have a program called 
"Software and Updates". then follow the suggestion of post 2 on what to do.

Also, if software and updates is not there, then open the program "System Settings".
I believe software sources was put into there for 12.10.

It's been well over a year since I last ran 12.10, so memory is scant.
(And probably mixed in with other releases like raring)

---

### Post by apiglet on 2014-02-20
Thank you both. The CD is unchecked and running those commands seems to have caused a lot to happen. 
It looks hopeful. I will mark it solved. I really appreciate your help!!

---

