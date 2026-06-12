---
title: "Ubuntu burn error"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by mandarpowale on 2015-01-22
I downloaded UBUNTU 14.04.1 iso(64-bit) and tried to burn it to DVDR 4.7GB Moserbaer disc at 6x using Nero Express 10. I have Windows XP Home 32-bit installed.

Nero said that burn was completed successfully but it failed to verify the data. Is it because my OS is 32bit ?

Please reply ASAP.

Mandar

---

### Post by Doug S on 2015-01-22
> **mandarpowale said:**
> Is it because my OS is 32bit ?No.

---

### Post by Tom_Dalton on 2015-01-22
To elaborate, no -- the issue won't be that your OS is 32-bit. It could have been a bad blank DVD and it's worth just trying exactly what you did, again. If it fails again, you might try slower burn (though it sounds like you're already burning slowly) or try downloading the ISO again.

---

### Post by QIII on 2015-01-22
Hello!

There is no reason to ask for a reply ASAP.  That is a given, provided someone with an answer happens to be here.

Rather than bothering to find out what the issue is with your burning software first, it might be worthwhile to try the disk in a 64 bit machine using "Try Ubuntu" without attempting to install it.

If that doesn't work, try downloading/burning it again.

---

### Post by mandarpowale on 2015-01-24
The 'Try Ubuntu' option does work. I ran 'verify' test using IMGBURN with the mounted ISO(I mounted the iso using daemon tools in windows) and test results were positive but negative when I used the burnt DVD. So I think that the fault is due to burn, I'm going to try burning it using IMGBURN next. I think Nero is not as good as it used to be back in the old days.

> **Tom_Dalton said:**
> To elaborate, no -- the issue won't be that your OS is 32-bit. It could have been a bad blank DVD and it's worth just trying exactly what you did, again. If it fails again, you might try slower burn (though it sounds like you're already burning slowly) or try downloading the ISO again.

Yes I did it at lowest speed option. Could that be the reason it failed? I'm going to use IMGBURN now-on since it reports supported burn speeds of a DVDR.

I found this link which is helpful thanks to 'QIII'

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)


Add: I performed the check and it reported that the DVD had flaws.

Add: Burned it to a DVD using IMGBURN, performed the above check procedure and it shows success.

---

