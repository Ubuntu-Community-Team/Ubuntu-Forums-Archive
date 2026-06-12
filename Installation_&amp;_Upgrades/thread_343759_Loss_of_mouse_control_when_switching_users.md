---
title: "Loss of mouse control when switching users"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by joe100 on 2007-01-21
Just upgraded from Dapper to Edgy. Everything went well until I tried to log on second user. Mouse control lost at login screen. I was able to log in though (kybd okay). It happens every time and regardless of which user I log onto first. I've not seen this before. Any ideas? Thanks.

---

### Post by haiku99 on 2007-01-21
> **joe100 said:**
> Just upgraded from Dapper to Edgy. Everything went well until I tried to log on second user. Mouse control lost at login screen. I was able to log in though (kybd okay). It happens every time and regardless of which user I log onto first. I've not seen this before. Any ideas? Thanks.

no ideas, but I have the same problem and made a similar post, no replies....

---

### Post by joe100 on 2007-01-22
FWIW I installed Dapper from disk and then upgraded to Edgy immediately after.

---

### Post by joe100 on 2007-01-24
Turns out it does the same thing in Dapper. I just hadn't noticed since I went straight to the upgrade to Edgy after loading Dapper. My machine is a Dell Inspiron 5100 laptop. haiku99, what's your setup? I can get by with restarting to switch users for now.

---

### Post by pheebs on 2007-02-17
*Bump

I'm also having this problem with an old Sony VAIO.  Maybe it has something to do with the touchpad?  I'll try a usb mouse to see if it makes a difference.

---

### Post by Adam Brockett on 2007-02-17
I know that there has been some problems with optical mice on the liveCD version of ubuntu, especially with the ps/2 port.  I havn't heard of problems with the touchpad, but perhaps these are related?

If a fix is to be found, could it perhaps be that when a new user is created, the xorg.conf file is set to "default" values, rather than those that were carried over from earlier versions, as which may have happened with the first user?

---

### Post by pheebs on 2007-02-17
I just tried my USB mouse, and now the login screen works perfectly.

---

### Post by dahen on 2007-03-19
I have the same problem with my laptop computer.

After I switch user, the new X server cannot control the mouse. But if I then use CTRL-ALT-F7 to get back to the first user, I get a password prompt but can then control the mouse. If I simply press CTRL-ALT-F9 to get to the second user again, I still have mouse control. So every time I want to log in with a new user, I have to do this CTRL-ALT-F7 and then CTRL-ALT-F9.

It would be nice if it just worked instead.

---

### Post by folkdevil on 2007-03-23
*bump* again.
Another one in the same boat as dahen etc.

No idea what to do. Any progress on ideas on this?

Thanks a lot.

---

### Post by folkdevil on 2007-04-02
Dahen's F7 & F9 workaround works for me.
But I am using the following workaround instead:

Instead of clicking on "Switch user..." I just click on "Lock screen" and wait a couple of secs. Then I move the mouse and under the password entry it gives me the option to switch user, which then works OK.

---

