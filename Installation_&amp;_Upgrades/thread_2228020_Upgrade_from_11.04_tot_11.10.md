---
title: "Upgrade from 11.04 tot 11.10"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by Lars_Swiers on 2014-06-05
I'm in a bit of a jam here. I installed a clean version of 11.04 today - since it was the only bootable version i had lying about.

Sadly Update Manager won't allow me to update to 11.10 - it insists i don't have an internet connection (I beg to differ).

Once again: this is a clean version of 11.04 - no other software is installed - what am I missing?

---

### Post by LastDino on 2014-06-05
Do you happen to connect to internet through Wifi? What kind of system are you on?

Also, I don't even know when 11.04 came out, let alone figure out what might be the problem, your best bet would be to tell us your system config and according to that we tell which new Ubuntu version to install.

---

### Post by monkeybrain20122 on 2014-06-05
Both 11.04 and 11.10 have long expired (11.10 reaches end of life 2013 April, 11.04  6 months before that) Please install a supported version of Ubuntu (12.04 or 14.04), 13.10 will expire in a month so no point installing it either.

---

### Post by Lars_Swiers on 2014-06-05
I'm on a cable connection - system specs are as follows:

1.66 GHz / 1GB Mem

I used to run Win7 on this baby and I figure I should be able to get 12.04 running - sadly I need to go through 11.10 to get where I want.

---

### Post by monkeybrain20122 on 2014-06-05
Just do a fresh install and forget about 'upgrade', it will take a long time even if works, and chances are it won't.

Edited: With your specs you would have better luck with a light variant like Xubuntu than Ubuntu.

---

### Post by Lars_Swiers on 2014-06-05
made both a xubuntu and an ubuntu 12.04 bootable USB but unfortunately my laptop refuses to recognize em during boot... when i try to boot them from within ubuntu 11.04 it insists that it won't work - booting the iso doesn't present a problem though

Edit: Mounting the iso doesn't present a problem - it refuses to be run

---

### Post by monkeybrain20122 on 2014-06-05
> **Lars_Swiers said:**
> made both a xubuntu and an ubuntu 12.04 bootable USB but unfortunately my laptop refuses to recognize em during boot... when i try to boot them from within ubuntu 11.04 it insists that it won't work - booting the iso doesn't present a problem though

Edit: Mounting the iso doesn't present a problem - it refuses to be run

How do you "boot it within Ubuntu 11.04"?? I am afraid it doesn't make any sense.

You download the iso for a current supported version of *buntu, then use either something like unetbootin or startup disk creator in Ubuntu 11.04 to make a live usb with the .iso

Then you want to boot from the live usb, but before you do this you have to configure your BIOS to allow that, so you need to enter the BIOS to alter the boot order so that usb device should be first. You enter the BIOS usually by pressing a fkey during boot, may be f10, f11 or even Esc depending on your computer, usually this info would flash by when the computer boots. 

After you change the boot order save and exit BIOS, turn off the computer, plug in the live usb and start the computer, it should boot into the live usb.

If you don't find an option in the BIOS to boot from usb then your computer doesn't support it,--this is rare unless your computer is > 10 years old,-- in that case you would have to burn a DVD with the .iso and boot from it.

---

### Post by grahammechanical on 2014-06-05
The Update manager has a limited set of reasons for being unable to do what we want it to do. It presents the most obvious reasons, such as a failure to have an internet connection. Ubuntu 11.04, 11.10 have both reached End of Life and the archives are not only closed but they have been moved. So, Update Manager is unable to connect to the archives because it has the wrong url. Update Manager does not know it has the wrong url so it assumes that the problem is to do with the internet connection.

You need to edit the sources.list and change the url.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Good Luck

---

