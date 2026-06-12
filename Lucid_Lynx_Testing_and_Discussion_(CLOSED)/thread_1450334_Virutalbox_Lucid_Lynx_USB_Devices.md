---
title: "Virutalbox Lucid Lynx USB Devices"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Socialsymbol on 2010-04-08
I have Virtualbox installed in Ubuntu 10.04 64 bit. I am running Windows XP 32bit as the guest OS. I am trying to sync my iPhone in iTunes on WinXP.

The problem I have is when I boot into the guest OS, the only USB devices virtualbox reads is my mouse and keyboard. In the USB device drop down on the virtualbox window, nothing is listed (No devices available).

After excessive googling I've found several posts claiming that USB devices should all work by default in Lucid, however that is clearly not the case right now for me. I've also found posts saying to add myself to the vboxuser group, however that group does not exist on my computer (usermod: group 'vboxusers' does not exist).

I'd really appreciate any help, as I REALLY need to sync my iPhone. I'd also like to update to the new 4.0 firmware. I'm loving Linux so far, my iPhone is the ONLY thing holding me back.

---

### Post by marshmallow1304 on 2010-04-09
VirtualBox OSE (the one in the Ubuntu repositories) does not work with USB devices (other than mouse/keyboard).  You will need to get the PUEL version of VirtualBox [from their website]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by iMisspell on 2010-04-09
Being Lucid Lynx is still in beta, maybe that is the issue ?

This forum section might be of help also...
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

_

---

### Post by Socialsymbol on 2010-04-09
> **marshmallow1304 said:**
> VirtualBox OSE (the one in the Ubuntu repositories) does not work with USB devices (other than mouse/keyboard).  You will need to get the PUEL version of VirtualBox [from their website]("http://www.virtualbox.org/wiki/Linux_Downloads").

Thanks, I'm at school now (posting off said phone). What version should I install? 10.04 is not yet listed, so should I just install the 9.10 version?

---

### Post by WinterRain on 2010-04-09
> **Socialsymbol said:**
> Thanks, I'm at school now (posting off said phone). What version should I install? 10.04 is not yet listed, so should I just install the 9.10 version?

Unfortunately, you will have to wait until 10.04 goes official and they come out with a version for lucid.

---

### Post by AlanR8 on 2010-04-09
I'd give the 9.10 version a go. I had it running on Lucid Alpha 2!

---

### Post by Socialsymbol on 2010-04-09
I just wanted to take the time to say thanks to Marshmellow for helping me out, the PUEL version is working fine! Thanks a lot man, I was really at a loss.

---

