---
title: "I like my machine setup. How do I make a snap shot of it?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Simon Cropper on 2010-05-25
Hi,

I have over the last few months played around, installed and configured my machine to use all my favorite programs (and hardware) and would be devastated if I needed to recreate the setup from scratch.

I regularly backup my data but was wondering how I could backup my software setup and configuration. I don't necessarily mean file by file, although creating a LiveCD of my setup would not be bad, but somehow creating a log of files and where they were obtained so this could be feed into apt-get (after you somehow updated the package sources with a similar script).

Aside from this what about all the configuration files the export, xorg.conf, fstab, etc files as well as the individual files / directories used by the software?

The expectation is that if my computer dies. I buy a new computer and shove a disk in the CD/DVD press go and the system is recreated, with all the nuances found on the system previously. Alternatively, install 10.4 from the Internet or CD, then run a range of scripts to recreate the software profile then scripts to reestablish the configuration.

Some sort of GUI that allows you to select if you copy xorg.conf (just in case the hardware is not the same) would be great but having searched for such an option I think I am pushing the envelope.

Any help would be appreciate.

Simon

---

### Post by irv on 2010-05-25
Check out this website:
[ttp://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("ttp://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by irv on 2010-05-25
> **irv said:**
> Check out this website:
[ttp://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("ttp://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

I tried to load the "deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/" in the repository and it could not find it. This might be an old site and this might not work for you.
Sorry.

---

### Post by irv on 2010-05-25
Here is another one to look at:
[http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")
I find doing a search in google will get you some places to start.

---

### Post by _Mark_ on 2010-05-25
Is this what you're looking for?
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by dustinmarlowe56 on 2010-05-25
yeah remastersys is still out there and functional, you just have to set up the repositories/ run sudo add-apt-repository and run sudo apt-get update, but it does work. i've made a few live cds just in the past week with it.

---

### Post by Simon Cropper on 2010-05-25
Thanks guys, this package appears to be what I was looking for. I will try it and post some feedback when done. Cheers.

---

