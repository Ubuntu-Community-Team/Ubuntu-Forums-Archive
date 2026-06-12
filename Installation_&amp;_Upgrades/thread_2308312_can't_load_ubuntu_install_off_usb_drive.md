---
title: "can't load ubuntu install off usb drive"
date: 2016-01-01
forum: Installation &amp; Upgrades
---

### Post by matious on 2016-01-01
Hello,

I have put ubuntu on usb drive using the pendrive unsiversal usb installer and also with unetbootin (two separate times) . However, after selecting to boot off a usb it always fails to load ubuntu. The directory for the ubuntu install package is view able from here.

I am on windows 10, the usb is fat32.

Any thoughts?

---

### Post by dcsoldschool53 on 2016-01-01
which ubuntu were you loading on to the usb stick 14.04 or 15.04

---

### Post by matious on 2016-01-01
14.04

---

### Post by C.S.Cameron on 2016-01-01
Check this:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-01-01
Boot to Windows, switch off hibernation and faststart. Presuming Win10 was preinstalled when you bought the computer, it will be in UEFI. You need  to boot to the BIOS and confirm Ubuntu USB is booting in UEFI also. While you're there, switch off secureboot for good measure. It can cause problems.

Any improvement? Also, the ISO may be damaged/corrupt. Did you check the md5sum? The best, and safest way, to get the ISO is via a torrent (see alternative downloads> Bit Torrent on the download page). It is checked for defects on the way down so you are pretty much guaranteed a non-corrupted ISO at your end.

---

### Post by matious on 2016-01-01
redownloading now.

Disabled fast start and secureboot, hibernating settings were already off. I also downloaded 32 bit the first time, going to try 64 this time. 

I will let you guys know once its done downloading--approx 30 minutes

---

### Post by Bucky Ball on 2016-01-01
Yep, 64bit, particularly if your machine has more than 3Gb of RAM. The 32bit install will only recognise 3Gb (and that applies to any 32bit OS install). 64bit will see and use whatever amount is there. :)

Looking forward to an update. And remember to check in BIOS whether Win is in UEFI mode or BIOS: boot the Ubuntu USB in the same mode. V important.

---

### Post by matious on 2016-01-02
Only 2 gigs of ram, just checked

Had an issue with the download so going to take longer than initially expected, likely another 45 mins or so here.

Thanks for the responses

---

### Post by Bucky Ball on 2016-01-02
You are sure you are running a 64bit processor? Might be a silly question, but if it is 32bit, the 64bit won't run/install in any case. Better check if you're not sure.

---

### Post by matious on 2016-01-02
OK. Got it running fine now. However, it isn't picking up my Wi-Fi card, I'm getting no networks. Googling the problem suggests this would be solved by temporarily connecting via Ethernet port and doing terminal sudo apt install of kernel source. The problem is my netbook doesn't have a Ethernet port. Any ideas?

Typed this on my phone.

---

### Post by Bucky Ball on 2016-01-02
That can be tricky(er) but by no means impossible. Open a terminal on the computer and:

```
sudo lshw -C network
```

... for starters and let's see what's in there. Please post the output between code tags (see last link in my signature).

---

### Post by Bucky Ball on 2016-01-02
Ok. [Just saw this]("http://ubuntuforums.org/showthread.php?t=2308332"). Please mark this thread as solved (see first link in my signature) and let's move on to the new thread. Pursuing your network issue there and here would be considered duplication which we don't allow here. Confusing.

---

