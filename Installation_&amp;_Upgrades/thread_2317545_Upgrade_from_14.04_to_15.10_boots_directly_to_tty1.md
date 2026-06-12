---
title: "Upgrade from 14.04 to 15.10 boots directly to tty1"
date: 2016-03-17
forum: Installation &amp; Upgrades
---

### Post by lefteris3 on 2016-03-17
Greetings to all! I am not that experienced ubuntu user and I haven't found a similar thread.

As I explain in the title, I upgraded my dist to 15.10 and now boots into terminal directly.

System now runs on kernel 3.13.0-79-generic, version 15.10 wily. I am not sure it is relevant, but my system has an ATI Radeon card HD 3470, just in case there is a drivers problem.

How do I identify the problem and run again in GUI?

---

### Post by Edison_James on 2016-03-17
Can you get to GUI by pressing Ctrl+Alt+F7,?

---

### Post by grahammechanical on 2016-03-17
> System now runs on kernel 3.13.0-79-generic,

It should be Linux kernel 4.2

[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)

At the Grub boot menu select Advanced options for Ubuntu and then select a recovery mode kernel. At the recovery menu select Resume and see if that gets you to a desktop. If it does go to System Settings>Software & Updates>Additional Drivers and change to the open source video driver.

Or,

At the recovery menu select Network to connect to the internet. then Select Root shell prompt then run

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

When that is finished type exit to get back to the recovery menu and then select Resume and see if that gets you to a desktop.

Regards.

---

### Post by lefteris3 on 2016-03-19
@[COLOR=#000000]Edison_James

[/COLOR][COLOR=#000000]Ctrl+Alt+F7 transfers me to a black screen, cursor blinking system remain idle.

[/COLOR][COLOR=#000000]
@[/COLOR][COLOR=#000000]grahammechanical

You have a point but at GRUB menu the top choice is 3.13.0-40-generic + recover mode.

I ran recovery mode as you suggested and took me directly to tty1 again with larger fonts on login and pass indicators, no menu of some kind appeared to make a selection... and I do not have internet I have to configure the wifi to run upgrde commands.

Hope I won't have to install 15.10 from scratch because i had tones of apps installed in previous dist.[/COLOR]

---

### Post by lefteris3 on 2016-03-19
A [COLOR=#000000]dpkg --configure -a did the job.[/COLOR]

---

### Post by a-lendrum on 2016-08-24
Very similar situation upgrading from 14.04 to 16.04. Processor overheated during installation. When I booted up again I was in tty1. Your solution (sudo dpkg --configure -a) worked perfectly for me and I'm now up and running again.

---

