---
title: "Install seems to hang on &quot;Who are You?&quot; Screen"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by davbeisner on 2011-03-22
I've tried twice now to install Ubuntu 10.10 (fresh distribution, downloaded straight from Ubuntu's site) on a clean hard drive. Each time through the installation process I get to the screen where it asks me for my information (name, computer name, username, and password). After filling in the info, the "Forward" button is always grayed out. All the fields have green checks, signifying that everything is entered correctly. I've had this stall here twice, both times it completes installing files and tells me that it's ready when I am, but I can't hit forward.

What am I doing wrong? The second time through I noticed that on initial boot I had gotten a crash message up in the task bar that said something about Ubuntu Ubiquity crashing, but I noticed that the message came up before I ever launched the "install Ubuntu" program. Any suggestions? This is the first time I've attempted to install Ubuntu...

---

### Post by Quackers on 2011-03-22
Welcome to UF.
This is usually caused by beginning the username with a capital letter. Capital letters and "special" characters are not allowed in that field. 
Also a password must be entered and confirmed. An empty password is not allowed.

---

### Post by davbeisner on 2011-03-22
Ah, you're amazing! I did indeed have the username starting with a capital letter... All seems now to be going well.

This fresh install was prompted when my building got hit with a power outage and I received a message saying bootmgr was missing as soon as I tried to restart the computer. Thankfully the system had only been set up a day and I didn't have any data saved on it yet. Hopefully this fresh install on a fresh hard drive will be okay and now that I have the computer behind a power condition/battery backup I won't have to worry about power outages.

Many thanks!

---

### Post by Quackers on 2011-03-22
You're welcome :-)
Hope all goes well.
Power outages don't seem to go well with Ubuntu for some reason. I'm thankful that I use a laptop. The battery can come in very handy :-)

---

### Post by wallajg on 2012-06-03
I had a slightly different issue.  I was able to continue on by changing the default computer name assigned by the installation program.  The install program defaulted the computer name to "<user name>-SMBIOS-implementation".  Once I changed the computer name to something different, which did not include the user name, I was able to continue.

---

