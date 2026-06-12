---
title: "System froze during first update"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Jugney on 2007-12-19
Hello all,

I just installed 7.10 on an HP Pavilion dv6000 and am very excited. However, when doing the first update (from the top bar), it downloaded 137 updates and got through installation of most of them, and toward the end it froze. I believe it was working on installing the common unix printing support, or something like that. It just froze and the hard drive wasn't doing anything.

After a hard reboot, now every time I boot up I get to the login screen, type in my user name and password and then it hangs. It just remains frozen at a monocolor screen the same color as the login screen background, and I can see the mouse pointer int he middle of the screen. But nothing happens.

Do I need to reinstall? Or is there a simple fix?

I also read Gutsy Gibbon may not run well on my HP laptop. If the group doesn't think it's worth trying to make it work I coudl always install 7.04 instead.

Thank you! I can't wait to get this up and running. I used Ubuntu for a day before going to install the updates, and I LOVE IT!!!!!

Jugney

---

### Post by PmDematagoda on 2007-12-19
Start Ubuntu in Recovery Mode and post the result of:-
```

apt-get update
```

---

### Post by Jugney on 2007-12-19
Thank you for the quick reply!

First of all, I cannot boot into recovery mode normally. If I try it freezes after checking my processors at the following lines:

[ 0.552000] Enabling IO-APIC IRQ
[ 0.552000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

FOr whatever reason, I can get around this by booting from my text install CD (LiveCD didn't work), then rebooting again after the menu comes up from the CD, this time without the CD. If I go into Recovery Mode, then it magically works. Would be nice to have this issue fixed too.

Anyway, this is what I got from apt-get update

A BUNCH of lines that more or less said "Failed to fetch ... Could not resolve http://us.archive.ubuntu.com" etc. 
Then finally:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

This is even though I have a network cable plugged in with a good connection. 

Help?

Jugney

---

### Post by PmDematagoda on 2007-12-19
Do as the error message suggested:-
```

sudo dpkg --configure -a
```

That will complete the updates.

---

### Post by Jugney on 2007-12-24
Thank you! It was as easy as that!

---

