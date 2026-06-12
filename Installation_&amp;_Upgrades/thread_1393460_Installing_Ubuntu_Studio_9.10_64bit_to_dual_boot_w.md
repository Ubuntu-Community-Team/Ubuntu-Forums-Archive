---
title: "Installing Ubuntu Studio 9.10 64bit to dual boot with existing windows 7 OS"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by NEWrangling on 2010-01-29
I'm currently running a brand new toshiba 505 laptop with Windows 7 64 bit and I'm moving away from windows.  I want to first install using wubi and when I start the process and then reboot my keyboard is dead so i cannot finish the install.  I searched for this problem and just cannot find it anywhere.

For reference I'm using the 9.10 version.  

Any help would be appreciated as it's preventing me from getting started.:confused:

---

### Post by FlyingBuzz on 2010-01-29
Why don't you try to install Ubuntu normally?
Cut some space out of your existing partition(s) ~10-20 Gb and install ubuntu on thar space. Grub (boot manager) will automatically detect your veendoze partition and add it to boot menu - you'll be able to choose between two OSes.

---

### Post by FlyingBuzz on 2010-01-29
Here is some helpful information:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by NEWrangling on 2010-01-29
I'm giving it a try via this guide, I will post up if things have changed. :popcorn:

Does the computer need to be connected via line to the internet?  

I got a Cannot reserve MMIO region error

freeing invalid mem type
udevd[134]: worker [1021]unexpectly returned error

This is during boot up

I got to the graphical screen where it asks for language but the keyboard and mouse is dead.

---

### Post by NEWrangling on 2010-01-29
tried everything and it still hangs at the point when you need the keyboard and mouse.  Same issue when I try to install Fedora instead.  this 64bit machine is starting to tick me off.

---

### Post by Sef on 2010-01-29
What happens when you run the live cd?

---

### Post by NEWrangling on 2010-01-29
it gets to the questions screen (graphical interface)  When it gets here I can't use the keyboard or mouse as it's frozen so I can't select english and answer the 6 questions. 

Almost like there is no drivers to run them.

---

### Post by NEWrangling on 2010-01-29
just now when launching I get this in the middle of the launch

udevd-work[204]: '/sbin/modprob -b acpi:LNXVIDEO:' unexpected exit with status 0x0009

it hung at this point so I had to restart

---

### Post by NEWrangling on 2010-01-29
holy crap I figured it out.  Went to f6 before selecting install ubuntu and deselected the first two options as I read this on someone elses install and it worked.

---

### Post by NEWrangling on 2010-01-29
holy crap I figured it out.  Went to f6 before selecting install ubuntu and deselected the first two options as I read this on someone elses install and it worked.

---

### Post by VideoRoy on 2010-01-30
> **NEWrangling said:**
> holy crap I figured it out.  Went to f6 before selecting install ubuntu and deselected the first two options as I read this on someone elses install and it worked.
I am guessing one of the options you chose was "noacpi" or something to that effect?  I cannot remember the exact option but have had to do that before.

I am setting a new laptop right now as well (HP Win7 64bit) and I appreciate you reminding me of this option.

BTW you may need to make sure whatever items you choose end up as kernel parameters in Grub2 or you will probably continue to have issues after the install.

---

