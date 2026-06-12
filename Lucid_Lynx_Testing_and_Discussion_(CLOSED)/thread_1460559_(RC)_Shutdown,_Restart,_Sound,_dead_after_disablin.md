---
title: "(RC) Shutdown, Restart, Sound, dead after disabling some startup apps and restarting."
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swatspyder on 2010-04-23
Ubuntu 10.04 RC x64 with all updates current as of 09:00PM PST.

My system is still up after the initial restart and I am currently using it.

Sound Preferences shows that I have no hardware listed and Output shows "Dummy Output"

Startup Applications that I disabled before the initial restart:
Bluetooth Manager
Evolution Alarm Notifier
GNOME Login Sound
Ubuntu One
Visual Assistance.

Edit:
Tested each application one by one.  Everything is normal now with all of those disabled.  Has since booted up fine.

One thing that was odd was X being in TTY1 and none of the other terminals were available.  Just a blinking cursor.

---

### Post by bigsmitty64 on 2010-04-23
I would start by re-enabling one of these at a time,

[B]"Evolution Alarm Notifier
  GNOME Login Sound"[/B]

 to see if maybe one of them is related to this incident? I'd start there maybe?

Someone with more knowledge than I will more than likely have a better answer but, couldn't hurt to try.  
Good Luck,
Smitty

**EDIT: I clearly overlooked a big part of your post! sorry. You can't shut down?  **I'd hold the old power button in until it shuts down, but thats just me :)

---

### Post by swatspyder on 2010-04-23
> **bigsmitty64 said:**
> I would start by re-enabling one of these at a time,

[B]"Evolution Alarm Notifier
  GNOME Login Sound"[/B]

 to see if maybe one of them is related to this incident? I'd start there maybe?

Someone with more knowledge than I will more than likely have a better answer but, couldn't hurt to try.  
Good Luck,
Smitty

I would love to test each one by itself, but at the moment, using the power menu, I cannot restart or shutdown.  So that is the first issue that needs to be dealt with.

---

### Post by bigsmitty64 on 2010-04-23
> **swatspyder said:**
>  at the moment, using the power menu, I cannot restart or shutdown.  So that is the first issue that needs to be dealt with.I saw that after the fact. Sorry

---

### Post by swatspyder on 2010-04-23
> **bigsmitty64 said:**
> I saw that after the fact. Sorry

No problem. :)

---

### Post by bigsmitty64 on 2010-04-23
> **bigsmitty64 said:**
> I'd hold the old power button in until it shuts down, but thats just me :) 


I've never had a problem doing that.

---

### Post by VMC on 2010-04-23
> **swatspyder said:**
> 
Startup Applications that I disabled before the initial restart:
Bluetooth Manager
Evolution Alarm Notifier
GNOME Login Sound
Ubuntu One
Visual Assistance.

You can rest assured those that you have removed are not causing your problem. I always remove those among several other without any problems.

Are you afraid to use the terminal to shutdown the system?
You can also try the Alt+Sysrq+b for reboot.

---

### Post by swatspyder on 2010-04-23
> **VMC said:**
> You can rest assured those that you have removed are not causing your problem. I always remove those among several other without any problems.

Are you afraid to use the terminal to shutdown the system?
You can also try the Alt+Sysrq+b for reboot.

No, I restarted the system using the terminal in X about 10 min ago.  Tried disabling everything one by one.  Everything was normal and has since booted up fine with those applications removed.

What is weird though, is that when I tried to go to TTY1, it kept me in X.  When I went to TTY2 + it just gave me a blinking cursor.  No other terminal was available, and X was on TTY1 instead of TTY7.

---

