---
title: "BIOS can't find bootable source"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by hankmorris on 2011-03-02
I purchased a book about Linux called the Linux Starter Kit. It came with a full install disc. The disc is labeled: Ubuntu 9.04 Jaunty Jackalope, Bootable & Installable LiveCD.

After playing with the thing for a while, I decided to take the plunge and install it on my Dell Inspiron laptop.
I went through the entire install. Everything worked fine.
I shut the computer down.

The very next time I turned on the computer I got the message "BIOS does not find a bootable source."

Right now, the laptop is a big paperweight--unless I either learn how to get Ubuntu to run installed so I can do real work with it, or reinstall XP.

What do I need to do?????

Thanks

---

### Post by Rebelli0us on 2011-03-02
If the machine worked fine before it should still work in Linux. The CD installer normally creates a boot loader. What type of installation did you do? Did you select to partition the disk?

---

### Post by SavageWolf on 2011-03-02
Maybe it's a bad disk? Try downloading one from the official Ubuntu website. You'll need to download it as an update anyway...

---

### Post by srs5694 on 2011-03-02
Download the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) boot using the Ubuntu CD's "try before installing" option (or whatever precisely it's called), and run the script. This will produce a file called RESULTS.txt. Post it here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That will give people here the information they need to help you. Without that, all you're likely to get are wild guesses.

---

### Post by miccorel on 2011-03-02
:),
1. Go to Bios Setup.
2. Change bootable device load 1st priority to your DVD.
 
Save and Restart.
 
Good luck

---

### Post by matt_symes on 2011-03-02
Hi

Follow srs5694 advice here. The boot script will tell us about your hard drives layout and that is what is causing the issue here.

Kind regards

---

### Post by psusi on 2011-03-02
9.04 is old and no longer supported.  You should download a more recent and supported release; either 10.04 or 10.10.

---

