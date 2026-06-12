---
title: "i think i deleted my latest Kernel"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by gabrielaca on 2012-01-22
this is what happened; i tried to free disk space an d used the ubuntu tweak, it listed two old kernels, and 177 libs and a packeg that where deletables, so i did it listed a good 545mb to free up; now that was yesterday, this morning i starup the computer and after choosing Ubuntu (dual boot) it started (got the puorplish background an d then) i got a black background, so i restsrted it and went into recovery mode, i tried all the options and in root shell w/networking i typed Unity, and i come back with WARNING: no DISPLAY variable,setting to 0 .... no unity-panel-ser.... Fatal couldnt open DISPLAY; so i typed Display and got: unable to open Xsever then i typed lshv -c video and it list my video card and the on boardvideo, then typed lshv -c video and got no Display; HOW CAN I REINSTALL my Kernel?


Ubuntu 11.10 64 bit

---

### Post by darkod on 2012-01-22
Are you sure it's missing?
Use the ubuntu cd to boot into live mode, open your root partition and look into the /boot folder.
Do you see any vmlinuz and initrd files there?

Even if the latest kernel is missing, it should be able to boot an earlier one if available.

---

### Post by gabrielaca on 2012-01-22
yes there are both, thou initrd is a rar file

---

### Post by darkod on 2012-01-22
In that case the kernel is there.
Your problem might be a result of something else that was removed and wasn't supposed to. But I have no idea what unfortunately. Sorry.

---

### Post by gabrielaca on 2012-01-22
thanks anyway.

---

### Post by gabrielaca on 2012-01-22
i´m thinking of making a full reinstall, _***BUT***_ my important files are locked and if i try to move them it tells me, no cant do you got not enough permision, how can i declare my pasword? im trying to move them to  another computer (windows) via netcable.

---

### Post by snowpine on 2012-01-22
Does Ubuntu Tweak have a forum or any documentation to help you repair the damage it made to your system?

In the future I recommend using trusted tools such as the Ubuntu Software Center to administer your system.

---

### Post by gabrielaca on 2012-01-22
a smack in the hand; thanks, next time, yeah.

would you help me in trying to gain acces to my files via Terminal or whatever way to move my files? im on Live CD and got acces to another PC (win)i need to imput my passw in order to move them, any ideas?

---

### Post by snowpine on 2012-01-22
If you are on the Live CD then you can press Alt+F2 and type:

```
gksu nautilus
```

This will open your File Manager with "root" privileges so you can copy whatever files you like for backup purposes. :)

---

### Post by gabrielaca on 2012-01-22
Nutilus can not handle "network" locations, any ideas?

---

### Post by gabrielaca on 2012-01-22
rigth click on folder,  properties, permitions, owner=user 1000, file access/folder access=read delete; group and others should i change those too to read and delete?

---

### Post by gabrielaca on 2012-01-22
***_YES_*** so far so good, seems to be working, thanks a bunch, as soon as i can confirm the transfer ill mark this thread as solved; thanks again.

---

