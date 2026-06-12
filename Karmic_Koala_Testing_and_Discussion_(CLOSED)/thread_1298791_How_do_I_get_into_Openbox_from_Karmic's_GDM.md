---
title: "How do I get into Openbox from Karmic's GDM?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2009-10-23
Hi,

I can't log into an openbox session from the new GDM. I searched this forum and I was only able to find one person using openbox in Karmic, but the topic didn't cover getting into openbox, or even what type of *buntu, and nobody responded either.

I used **sudo apt-get install openbox**  and the openbox session appears in the session menu, and I am able to select it, but it won't log into openbox. It keeps bringing me right back to the GDM screen. I'm thinking that the openbox package hasn't been updated to work with the new GDM, since I had no trouble at all getting into openbox in Jaunty's GDM.

Should I try using KDM or XDM instead of GDM? Or is there a way to make openbox work with the new GDM? This is openbox version 3.4.7.2-4 for Karmic. I had this problem in Karmic Beta, and still having the same problem in Karmic RC. 

Thanks,
James.

---

### Post by ikisham on 2009-10-23
I can't tell you how to fix it but you could report the bug. Alt+F2, then
```
ubuntu-bug openbox
```

---

### Post by Tibuda on 2009-10-23
Open a xterm session instead and run "openbox-session" there. It will output any error when running Openbox.

---

### Post by ankspo71 on 2009-10-23
Thanks Ikisham and Danielrmt.

I reported the bug at launchpad.
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/459005](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/459005)

I discovered this problem wednesday morning, I should have reported it then. 

I also included the xterm session output for the command openbox.

Xterm session reports:
openbox
(openbox:4185): Openbox-Warning **: Openbox is configured for 4 desktops, but the current session has 1. Overriding the Openbox Configureation. Openbox message: Unable to find a valid menu file debian-menu.xml

Thanks,
James.

---

### Post by gjoellee on 2009-10-23
EDIT: Removed....

---

### Post by ankspo71 on 2009-10-23
Hi again,

I came back to let everyone know that I installed lxde and I was able to log into the lxde session through GDM easily, but I still can't log into the openbox session. I also now have  today's updates installed and still no change with openbox. I haven't seen anybody else report a bug for this in karmic so this might only be effecting me. Can anybody here confirm this problem by installing openbox and see if you can log into it? **Make sure you have automatic login _disabled_ before attempting this!** 

Thanks,
James.

---

### Post by ikisham on 2009-10-23
The bug could be with gdm, but if it's the case they will change it in the bug report.

---

