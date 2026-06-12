---
title: "Screen saver turns the backlight off"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2011-12-31
I installed Oneiric (default AMD64) on a new laptop. One of the issues I get is that the screen saver blanks the screen and will not resume. I can see that something is displayed on the screen but the backlight is off. If I press any key nothing happens unless I close and reopen the lid... 

Anyone know how to solve this?

Hybrid graphics card Nvida/Intel on my [ASUS U31JG laptop]("http://www.linlap.com/wiki/asus+u31jg").

---

### Post by 2F4U on 2011-12-31
I guess it is not just the screen saver kicking in but your computer goes into suspend mode. I have the same problem on a MacBook running Xubuntu. Disabling the screen saver didn't change anything for me, so I guess it is some hardware power management thing built into my machine, which I can't change. I got somehow used to it since it wakes up very fast from suspend and this doesn't cause any issues such as screen artefacts.

---

### Post by 1/0 on 2012-01-01
> **2F4U said:**
> I guess it is not just the screen saver kicking in but your computer goes into suspend mode. I have the same problem on a MacBook running Xubuntu. Disabling the screen saver didn't change anything for me, so I guess it is some hardware power management thing built into my machine, which I can't change. I got somehow used to it since it wakes up very fast from suspend and this doesn't cause any issues such as screen artefacts.

That could be but I can see some of the desktop if i look at the screen with a lamp. So I'm unsure if it's suspended (plus I've set the laptop not to suspend). 

The only relevant info in the Xorg.0.log seems to be:

```
[ 11489.243] (II) PM Event received: Capability Changed
[ 11489.243] I830PMEvent: Capability change

```

I don't understand why the lid solves the problem. Somehow that triggers something more than keystrokes or the touch pad.

---

### Post by 1/0 on 2012-01-05
Bump

---

### Post by 1/0 on 2012-01-12
When mplayer is on everything works as it should.

---

### Post by 1/0 on 2012-01-25
A few times recently, nothing except hard reboot has been able to start the screen. When I say that I mean not even dropping out to shell via ctrl + alt + f1 and then logging in end typing sudo reboot etc or ctrl + shift + alt + sysrq + r,e,s,i,u,b. Nothing. It's as if the keyboard and mouse is shut down.

I'm thinking it's time to file a bug unless anyone has some suggestions. Any suggestions on relevant info for a bug?

---

