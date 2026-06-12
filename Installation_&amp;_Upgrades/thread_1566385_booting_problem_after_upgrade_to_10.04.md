---
title: "booting problem after upgrade to 10.04"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by webmidget01 on 2010-09-02
hi,
im not very experienced in ubuntu/ linux...

im using a dual boot machine with windows vista 64 bit and ubuntu 10.04 on it.
i was previously using ubuntu 9 with no problems. then i decided to upgrade to 10. the upgrade and installation process finished when i was afk and computer rebooted itself. it booted to windows vista automatically.then i tried to reboot to see how ubuntu 10.04 looks like. when booting from ubuntu partition an error message came out : "couldnt find boot partiton on /dev " or something like that. then i tried to figure it out by myself and ran the recovery mode. it did somethings , i mostly said yes when it asked to me. then rebooted again. that error message appeared again but the booting process continued and ended up with login prompt but no graphical interface.i logged in and write "startx" into command line and it started smoothly. now im using ubuntu 10.04 without any graphical problem. 

my problem here is : how can i make the booting process end up with a normal graphical login screen not command line prompt ? i mean how can i make x server start automatically? 

thanks ...

---

### Post by presence1960 on 2010-09-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by webmidget01 on 2010-09-02
thanks for reply..
im doing your instructions and post the result when im done...
btw i have carefully read the error message during boot sequence...it says : 

        mounting hd(0,6) ext3 
        starting up

after that 
    
        mounting none on /dev failed : no such device (numbers here)

---

### Post by webmidget01 on 2010-09-02
[code]

---

