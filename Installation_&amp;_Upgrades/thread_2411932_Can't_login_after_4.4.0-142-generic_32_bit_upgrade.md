---
title: "Can't login after 4.4.0-142-generic 32 bit upgrade"
date: 2019-02-05
forum: Installation &amp; Upgrades
---

### Post by marknaz on 2019-02-05
Hi all,

After upgrading my 32 bit Ubuntu-16.04 system to the 4.4.0-142-generic kernel, I can no longer login.

What happens is, I enter my login, hit the enter key, and instead of waiting for my password, the cursor advances to the next line, and complains about an invalid login. Or words to that effect.

I am able to login properly when I boot to the previous 4.4.0-141-generic kernel.

Any help would be appreciated.

Thanks!

---

### Post by ubfan1 on 2019-02-06
I haven't noticed any problems on the 64 bit 4.4.0-142 kernel.  Can you switch to a virtual terminal (ctl + alt + f3 ) and login?  I't your username causing the problem, right?  Check the NUM lock state, that might get switched in software, and some machines don't even have an indicator light.  Are you using a keyboard with a separate keypad, or are the keypad numbers overlayed with the letters on the right side of the keyboard?  What is the keyboard set to (special language,  etc.)? That state may get changed at the wrong time.

---

### Post by marknaz on 2019-02-07
Thanks for your reply, Ubfan1.

Seems there's a bug report on this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1815122?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1815122?comments=all)


Edit Mar 15, 2019:
Have successfully upgraded my 32 and 64 to 4.4.0-143-generic, and all seems well.
Thanks!

---

