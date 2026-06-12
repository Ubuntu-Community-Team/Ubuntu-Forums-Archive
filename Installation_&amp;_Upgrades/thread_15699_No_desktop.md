---
title: "No desktop"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by Knutchi on 2005-02-16
I went from windows to Linux.

And linux wont work.

I got a Aopen aeolus 6800.
Linux need to get a driver, from the web i guess.
After giving it the correct settings. Internet dont work
i got wlan.
on startup, Hot plug subsystem, and name resolution
Fails. 

Edit: btw. I need a total NOOB description. I cant get Desktop to work either.
(And i am a TOTAL newcomer)

checked the guide,  dont understand it.

I have (graphics card): Aeoulus 6800 (Nvidia based gpu).(producer is Aopen)

---

### Post by Yamakazi on 2005-02-16
My first question is: why put a card that expensive in it?

Anyway what do you mean with no desktop??? Do you end up at a prompt (shell)
Try typing startx
And tell us what the exact errors are.

---

### Post by wallijonn on 2005-02-18
You may need to boot with the LiveCD and set the init level to 1 in /etc/inittab on the hda which has Ubuntu on it. Reboot. Now run whatever programs you need, like fglrxconfig to configure your ATI video card. 

When you boot from the LiveCD check out the /var logs for messages which may help you to determine what the possible problem may be and if it is hotplug you can add it to the blacklist file.

---

