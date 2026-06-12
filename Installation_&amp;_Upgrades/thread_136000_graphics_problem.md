---
title: "graphics problem?"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by c-2501 on 2006-02-25
ok i have first to confess to being a totoal noob when it comes to this so here goes:

i installed the OS, no problems everything seemed to go fine untill the first time i booted.

ubuntu apears to start normally, with no errors until the point where (im guessing) the login screen should be displayed.  instead of this i get a horribly corrupted looking mess that i cant do anything with.

my system specs are:
athlon 64 3200+ (i have the 64 bit Ubuntu version)
Asus A8NSLI Deluxe motherboard
Nvidia 6600GT graphics card (i thought perhaps i needed to install the exact Nvidia drivers. but how do i do this during the install :confused: )

if you need any more info just ask.
sorry if this is something that has been posted before, i did a quick search and found nothing similar.

---

### Post by alamba on 2006-02-25
Try this:
1. Boot into recovery mode (press esc during grub and go into the recovery boot)
2. cd /etc/X11
3. vi xorg.conf
4. Find the line that says Driver "XXXXX" (XXXX denotes a word nv or nvidia)
5. Change that to "vesa". (Don't use the quotes if it isn't there)
6. Reboot

This should fix your bootup for now. Once you're in the system search the forum for nvidia driver and install your latest driver.

Also try sudo dpkg-reconfigure xserver-xorg on the command line in normal bootup.

A

---

### Post by c-2501 on 2006-02-25
thanks for getting back so quick, will give this a go and let you know

---

### Post by alamba on 2006-02-25
Don't forget to save xorg.conf after making the change. 
<Press esc>
:
wq

Good luck!

---

### Post by Trab on 2006-02-25
if that doesnt work, let us know, there are some other things you can do...
latz
-Trab

---

### Post by c-2501 on 2006-02-25
*edit* nvm

---

### Post by alamba on 2006-02-25
nvm???

---

### Post by c-2501 on 2006-02-25
lol dont ask. 
ok ive changed the xorg.conf file and am able to load the desktop, all thats left now is to install the nvidia drivers, thanks for the help

---

### Post by alamba on 2006-02-25
yw. Installation of nvidia drivers is pretty well documents in the forums here. A search should bring you upto speed.

A

---

