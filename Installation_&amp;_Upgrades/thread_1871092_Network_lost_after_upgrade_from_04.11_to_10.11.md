---
title: "Network lost after upgrade from 04.11 to 10.11"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by styleruk on 2011-10-28
Hi

I've just upgraded from 04.11 to 10.11 and now have no network available.  Not sure what to do here now!
I have the icon at the top right flashing and when selected shows my 'Realtek TRL' greyed out.  Does anyone have an idea.  I think I seemed to have lost it after installing samba to transfer files from one pc to this one.
All went well, even after samba, the files started transfering but now no network to the outside world.
Trying hard to come to terms with the new interface and crayon style buttons but struggling.

Si

---

### Post by TBABill on 2011-10-28
Have you right clicked on the network icon and adjusted settings to make sure it's available to all users and set to connect on boot? Those are easy first steps. After that we'll have to know what chipset the device uses to help further, but I'd check the easy ones first.
 
And just a note, not at all meant to be rude, but Ubuntu is versioned as 11.04 and 11.10. Not a big deal, but keeps things less confusing.

---

### Post by styleruk on 2011-10-28
Hi, thanks for quick response.  Yes, I have ticked the 'allow all users', and 'connect automatically'. 
And sorry about the version thing... Used UK date coding by accident.

---

### Post by TBABill on 2011-10-28
Can you open a terminal and paste the output of the following codes ```
lspci
``` and ```
lsmod
```

---

