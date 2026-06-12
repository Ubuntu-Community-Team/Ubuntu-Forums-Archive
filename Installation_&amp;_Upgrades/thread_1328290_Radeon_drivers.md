---
title: "Radeon drivers"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2009-11-16
[FONT=Arial][SIZE=2]Hello

I've just solved my [muted Ubuntu after upgrade]("http://ubuntuforums.org/showthread.php?t=1317981") problem and have another one:/

Whenever I update my kernel I have to install ATI drivers again.
```
ls /boot/ | grep vmlinuz
vmlinuz-2.6.28-16-generic
vmlinuz-2.6.31-14-generic

```

I can't activate this one - don't know why, it's just not responding.
[http://img132.imageshack.us/img132/1909/44325774.png](http://img132.imageshack.us/img132/1909/44325774.png)

I tried to do it like last time.
Went to [/SIZE][/FONT][FONT=Arial][SIZE=2]"[/SIZE][/FONT][FONT=Arial][SIZE=2][ATI Catalyst&#8482; Display Driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")", but this time during installation I get:
```
_@_:~$ sudo sh ./Downloads/ati-driver-installer-9-10-x86.x86_64.run
[sudo] password for _: 
Created directory fglrx-install.wCROtA
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.661........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.4 and later releases 64-bit
loki_setup: directory: (null)
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.wCROtA
_@_:~$ 

```

What should I do now?

Regards
Jet
[/SIZE][/FONT]

---

### Post by darkod on 2009-11-16
I have not much experience with video drivers but I had issues with my HD3200 and 9.10 too. What worked for me was the EnvyNG package. It downloaded driver automatically (don't know from where) and installed it and it worked perfectly since.

---

### Post by jet-san on 2009-11-16
I found 3 options for "EnvyNG" in Synaptic Package Manager.
[http://img265.imageshack.us/img265/8451/spm.png](http://img265.imageshack.us/img265/8451/spm.png)
It doesn't work:(
[http://img20.imageshack.us/img20/7179/17749704.png](http://img20.imageshack.us/img20/7179/17749704.png)
Any other ideas please?

---

### Post by jet-san on 2009-11-17
someone please...

---

### Post by jet-san on 2009-11-20
Another bump.

---

### Post by agathian on 2009-11-20
your initial driver installation refers to some error in /usr/share/ati/fglrx-install.log.  Did you look there for any clues?

Also, i believe envyng also has a command line version..  you might want to try it to see what, if any, error it provides...

---

### Post by jet-san on 2009-11-21
I found this in /usr/share/ati/fglrx-install.log

Errors during DKMS module removal
Errors during DKMS module removal
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.661 to DKMS

but I have no idea what does it tells me:/

I tried to do a clean install, but I have another error there - can't see any discs:(
[http://img26.imageshack.us/img26/3448/screenshotlh.png](http://img26.imageshack.us/img26/3448/screenshotlh.png)
[http://img694.imageshack.us/img694/617/s6003148.jpg](http://img694.imageshack.us/img694/617/s6003148.jpg)
[http://img109.imageshack.us/img109/8817/s6003151.jpg](http://img109.imageshack.us/img109/8817/s6003151.jpg)

Further help needed please
Jet

P.S.
This is not a CD/DVD burning fault, because I did it twice and get same error everytime.

---

### Post by jet-san on 2009-11-22
Anyone knows why do I have this error during installation?

---

### Post by jet-san on 2009-11-23
Still don't have graphic drivers, help please?

---

### Post by agathian on 2009-11-23
Please checkout this thread
[http://ubuntuforums.org/showthread.php?p=8320046#post8320046](http://ubuntuforums.org/showthread.php?p=8320046#post8320046)

This sounds similar to your initial problem.

As far the clean-install CD issue, i would suggest starting a new thread with appropriate subject line.

When you say you burned CD twice - i assume you did set it to lower speed burning..

---

### Post by jet-san on 2009-11-25
Yes, it was lower speed burning.

Btw, I've already changed my grub options to boot into new kernel.
```
uname -r
2.6.31-14-generic

```
That gives me my sound back (muted on old kernel), but started a new problem with graphics (alright on old kernel), so I get sound instead of graphics:/

---

### Post by jet-san on 2009-11-26
I've just updated my kernel to
```
uname -r
2.6.31-15-generic

```and tried to install graphic drivers again.
Same error
```
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.4 and later releases 64-bit
loki_setup: directory: (null)
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.pNnU9N

```
Details inside this file:
"Errors during DKMS module removal
Errors during DKMS module removal
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.65 to DKMS"

What's wrong, does anybody know?

---

### Post by jjcv on 2009-11-26
How did you run the programme:

sudo ati-driver-installer-9-11-x86.x86_64.run

I have no idea what DKMS is myself over.

---

### Post by jet-san on 2009-11-27
Yatta!!!

Latest 9.11 version is working at last:)

SOLVED - Thanks:D

---

