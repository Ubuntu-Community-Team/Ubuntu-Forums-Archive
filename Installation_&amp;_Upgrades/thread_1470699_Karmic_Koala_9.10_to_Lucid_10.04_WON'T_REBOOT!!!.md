---
title: "Karmic Koala 9.10 to Lucid 10.04 WON'T REBOOT!!!"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Mikolynx on 2010-05-03
Hey Guys,

I went in for the upgrade for 10.04 from Karmic Koala. I got through the processes fine...hangs on restart. I let it sit for 3 hours with nothing.

Help!

Thank you,

Miko

---

### Post by faulty_tower on 2010-05-03
Interesting,

maybe we are experiencing the same problem, could you please have a look at [http://ubuntuforums.org/showthread.php?t=1468716](http://ubuntuforums.org/showthread.php?t=1468716) ...

---

### Post by Mikolynx on 2010-05-03
See, when I reboot I see the system stuff run through and then I get a blinking cursor that lasts for 30 seconds and then a black screen.

You?

---

### Post by faulty_tower on 2010-05-03
You have disabled the splash screen (well, I have)? I don't get the blinking cursor thing, the last console output I get are some filesystem checks (fschk) that all succeed. As I've already described in my other thread my root partition has already been mounted at this stage, services are started etc. So i **think **the next service that should get started would be the X server which apparently not only fails but some locks my entire system. Then it's a black screen for me too.

---

### Post by Mikolynx on 2010-05-03
I think I need to do something about my video card driver...but I'm not sure how to do it if I can't get into the system...I can open up setup with F2...any thoughts?

---

### Post by will_cbe on 2010-05-03
I've got this same problem.  I think I've found a workaround.  When my pc gets stuck, I discovered I need to hit the reset button.  The boot cycle will start again, and the second time it will pass through the dead space after about a minute.  If your pc takes more that 2-3 minutes, it probably didn't work for you.  Not great, but it'll do until someone figures out what's wrong.
PS, I get the same thing under ubuntu as well as xubuntu.
Will

---

### Post by will_cbe on 2010-05-03
Check the release notes.
[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)
Towards the end, there's a note about video architecture.  I made this mod, and I now have a splash screen which goes quickly to the login screen.

---

