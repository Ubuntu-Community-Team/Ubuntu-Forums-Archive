---
title: "Ubuntu 11.10 Black Screen"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by flyingfisch on 2011-12-08
SYSTEM INFO:
Windows XP pro and Ubuntu 11.10 dual boot
nVidia Graphics card
emachines T2482
 
 
OK, so today, i boot up my computer and i get the grub 2 boot menu as usual. I select Ubuntu and i get a black screen with a white cursor blinking in the corner. So i booted up my LiveCD and searched for the problem on the internet. I found that since I have nVidia graphics card, I can edit the boot script line that says:
 
```

splash quiet quiet splash

```(idk if that was the exact code, but it was similar)
 
and replaced it with:
 
```

nomodeset

```It showed text now and got hung up at:
 
```

Begin: Running /scripts/init-bottom ... done

```I can boot the LiveCD.
 
I can boot windows XP.
 
I can boot Recovery mode.
 
Does anyone know whats going on? (it was working for a few days before this happened)

---

### Post by flyingfisch on 2011-12-08
OK, i have tried the flowchart located here: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
 
I have booted into tty mode, and i get this:
 
```

[   26.559490] init: unreadahead-other goal changed from start to stop
[   26.559853] init: unreadahead-other state changed from spawn to stopping
[   26.560127] init: handling stopping event
[   26.560406] init: unreadahead-other state changed from stopping to killed
[   26.560664] init: unreadahead-other state changed from killed to post-stop
[   26.560860] init: unreadahead-other state changed from post-stop to waiting
[   26.561212] init: Handling stopped event

```
 
At this point it freezes. :(
 
Now, is this some kind of an error? Or is this how its supposed to boot up. I can't use my keyboard and ctrl+alt+del doesn't reboot.

---

### Post by flyingfisch on 2011-12-08
ok, i have booted into the liveCD and reinstalled nvidia drivers, etc. I still get stuck at:
 
```

Begin: Running /scripts/init-bottom ... done

```
 
Questions:
 
How do I reinstall the kernel from the liveCD? Should I reinstall the kernel?
If i should try something else, what should i try? Please Help!!

---

### Post by flyingfisch on 2011-12-08
I ran boot-repair from the liveCD and rebooted. Right now its displaying:
 
```

[   28.501089] i2c i2c-0: sendbytes: NAK bailout.
[   28.550861] i2c i2c-0: sendbytes: NAK bailout.

```
 
Its been displaying this for 2 minutes now. Should I force a reboot? Should I let it go for a few more minutes?
 
Thanks in advance.

---

### Post by flyingfisch on 2011-12-08
I renamed xorg.conf to xorg.conf.bak

Right now its displaying 3 NAK bailout messages. I'm gonna let it sit there for a while while i eat dinner.

---

### Post by flyingfisch on 2011-12-08
OK, i turned it off [the computer] cuz it seems to be frozen again. [IMG]http://omnimaga.org/Smileys/classic/undecided.gif[/IMG]
 
It seems like it might be a kernel problem.
 
What i want to do now is reinstall ubuntu but keep things such as personal settings. Does anyone know how to go about this?

---

### Post by MAFoElffen on 2011-12-08
> **flyingfisch said:**
> OK, i turned it off [the computer] cuz it seems to be frozen again. [IMG]http://omnimaga.org/Smileys/classic/undecided.gif[/IMG]
 
It seems like it might be a kernel problem.
 
What i want to do now is reinstall ubuntu but keep things such as personal settings. Does anyone know how to go about this?
Just got hone... I'm the person who came up with that Trouble Shooting Flow Chart.

From what you did, reinstalling the video drivers are not going to gain anything untill you have a working base system- and it isn't.  You tried booting into a TTY Text console and still have the problem. At least now it's showing.

I would say replacing the kernel would be an easy try -BUT- you said in your first post:
> I can boot Recovery mode.
What exactly did you mean by that? Can you boot to a Root prompt without error? Can you go safemode/low graphics? Can you boot from a previous Kernel?

It varies with the answers you give on those.  It may be a kernel of an initramfs image... both easily corrected. Next would be a module loading problem from udev or modeprobe.d...

Could you Boot from a LiveCD and post the /var/log/syslog from your installed sys?

---

### Post by flyingfisch on 2011-12-08
> **MAFoElffen said:**
> Just got hone... I'm the person who came up with that Trouble Shooting Flow Chart.

From what you did, reinstalling the video drivers are not going to gain anything untill you have a working base system- and it isn't.  You tried booting into a TTY Text console and still have the problem. At least now it's showing.

I would say replacing the kernel would be an easy try -BUT- you said in your first post:

What exactly did you mean by that? Can you boot to a Root prompt without error? Can you go safemode/low graphics? Can you boot from a previous Kernel?

It varies with the answers you give on those.  It may be a kernel of an initramfs image... both easily corrected. Next would be a module loading problem from udev or modeprobe.d...

Could you Boot from a LiveCD and post the /var/log/syslog from your installed sys?

OK, i only have ubuntu 11.10 and WinXP on my PC right now. 

What i meant by recovery mode is in GRUB i have this option: "Ubuntu linux 11.10 (recovery mode)"

When i boot in this mode, i get this menu:

```

Recovery  Menu (limited read-only menu)

resume     Resume normal boot
fsck       Check all file systems (will exit read-only mode)
remount    Remount / read/write and mount all other file systems
root       Drop to root shell prompt

<Ok>                        <Cancel>

```

But, i am going to try to reinstall linux if i can, unless i can fix it easily with recovery mode.

---

### Post by flyingfisch on 2011-12-08
I am reinstalling ubuntu right now. I hope this works  [IMG]http://omnimaga.org/Smileys/classic/undecided.gif[/IMG]

---

### Post by MAFoElffen on 2011-12-08
> **flyingfisch said:**
> I am reinstalling ubuntu right now. I hope this works  [IMG]http://omnimaga.org/Smileys/classic/undecided.gif[/IMG]
I believe it will.

---

### Post by flyingfisch on 2011-12-08
My only question is why it worked for at least 3 days up till now. :P

---

### Post by MAFoElffen on 2011-12-08
> **flyingfisch said:**
> My only question is why it worked for at least 3 days up till now. :P
I have NVidia, ATI and Intel GPU's. At home here I have 7 Desktop, 4 Laptops, 3 Servers, 4 RAID servers, NATS, etc. I test development versions of operating systems and software. For a while now, I've spendta lot of time on this forum helping people fix their graphics problems... and then poof

My main box I keep on released.  2x Nvidia GeForce 9800 GTX SLI bridged..

Last week what happened to you, what I've helped hundreds (maybe thousands) of people to solve- happened to me. You would think my own jewel of a PC would just be humming past something like that. LOL An update hosed my nvidia drivers. I reinstalled drivers and went on. 

Why you say?  I guess it just keeps things entertaining. All in the way you look at things right?

---

### Post by flyingfisch on 2011-12-09
Yep. Like my dad told me, "welcome to the world of computers, where everything seems to be based on random number generators".

What i meant to say was, should i do anything different this time to prevent it from happening again, or was it some kind of a corruption that happened that I could do nothing about. 

I don't want to cause any other problems, lol.

---

### Post by MAFoElffen on 2011-12-09
> **flyingfisch said:**
> Yep. Like my dad told me, "welcome to the world of computers, where everything seems to be based on random number generators".

What i meant to say was, should i do anything different this time to prevent it from happening again, or was it some kind of a corruption that happened that I could do nothing about. 

I don't want to cause any other problems, lol.
I have one: "The one with the last laugh, had a good backup..."

AFter you get everytihng all setup, if you don't do a full or partial backup, at least backup your /etc/X11/xorg.conf file.  I figure whatever I do or what something else does, I can recreate or fix.  Critical data and pictures, I have stored on one of my RAID Servers, where there is repetition. (a higher chance of recovery). 

If things like this do happen again, you do have a little more confidence and experience to fall back on.  There is a whole lot of experience here in these forums...

---

### Post by flyingfisch on 2011-12-09
Thank you. And I already reinstalled ubuntu. Did you want me to backup xorg.conf before or after i reinstalled?

---

### Post by MAFoElffen on 2011-12-09
> **flyingfisch said:**
> Thank you. And I already reinstalled ubuntu. Did you want me to backup xorg.conf before or after i reinstalled?
After you get it working.

---

### Post by flyingfisch on 2011-12-09
Oh ok, why?

---

### Post by MAFoElffen on 2011-12-09
> **flyingfisch said:**
> Oh ok, why?
Because you had asked for things that may help you next time.  If error, then you could copy it back in place... Otherwize - nevermind.

---

### Post by flyingfisch on 2011-12-09
Oh ok. Well, i guess this prob is solved. Could someone change the thread name?

---

### Post by MAFoElffen on 2011-12-09
> **flyingfisch said:**
> Oh ok. Well, i guess this prob is solved. Could someone change the thread name?
When You, the OP look at the thrasd, at the top of the page there will be a link that says "Thread Tools." Under that will be a link (for you) that says "Mark Thread As Solved." Once you select it, it will change the status to "Solved"

Good Luck and happy holidays.

---

