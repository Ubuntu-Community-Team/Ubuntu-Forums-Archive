---
title: "Thinkpad t500 shutdown issue"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-12-18
I don't know why this is happening, not a clue...

I tested my old karmic install on this machine, shutdown works fine.
Newly installed lucid alpha 1 and daily build(16th) shutdown won't work.
The symptom is click shutdown or restart or execute "sudo reboot" or execute "sudo shutdown -h now" will shut all programs, then run to a black screen, and somehow freezes(no further reaction, keyboard CapsLock won't work, magic key alt+prtSc+b to reboot will work, but have about 10 secs deley).

I'm really lost here...could someone be so kind to point me to the right direction..
thanks

edit: gonna try to install a different kernel...hope it works..
edit2: the livecd won't shutdown or reboot either..
edit3: tested 2 different kernels, still have the problem..

---

### Post by phillw on 2009-12-19
Hi,
the boyz & girlz over in the hardware & laptops area are more upto speed with acpi and thinkpads. I've helped out there a couple of times, with daemons not running etc.
Can you follow the threads checking on the various daemons, and see if any are running on 9.10 that are not running on 10.04 
It has been a fairly common theme with ThinkPads
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)


Hope that helps,

Phill.

---

### Post by Vanishing on 2009-12-19
Thank you sir, will do.

---

### Post by Vanishing on 2009-12-19
> **phillw said:**
> Hi,
the boyz & girlz over in the hardware & laptops area are more upto speed with acpi and thinkpads. I've helped out there a couple of times, with daemons not running etc.
Can you follow the threads checking on the various daemons, and see if any are running on 9.10 that are not running on 10.04 
It has been a fairly common theme with ThinkPads
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)


Hope that helps,

Phill.
I tried various things like:
-adding acpi kernel parameters
-disable wireless before shutdown
-use ifconfig script in rc*.d
-different kernels
-/etc/init.d/alsa-utils(does not exist)
-disabled/enable apci-support and apm
those are the most common shutdown issue's solutions, but my install still can't shutdown or restart properly. 

due to plymouth, i won't be able to see the shutdown terminal output messages, is there anyway to log them?

---

### Post by Vanishing on 2009-12-19
Just did a little tweaking in bios, disabled ati graphic card, using integrated intel card, now shutdown will display some error messages.

> 
init: tty2 main process (935) killed by TERM signal
....: cron ........................................
....: tty1 ........................................
acpid: exiting
init: hal main process terminated with status 1
....: avahi-daemon ............................

nm-dispatcher.action: Error in get-property : Message did not receive a reply (timeout by message bus)
nm-dispatcher.action: Caught signal 15, shutting down

init: Disconnected from system bus
nm-patcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1


now i know it is a network problem, but what is the fix or workaround?

thanks guys

edit: took networking off in rc0.d and rc6.d, now the nm-dispatcher.action line disappeared, but still hangs at shutdown or reboot, now the most likely problem is with init or modem-manager......

---

### Post by phillw on 2009-12-19
> **Vanishing said:**
> Just did a little tweaking in bios, disabled ati graphic card, using integrated intel card, now shutdown will display some error messages.



now i know it is a network problem, but what is the fix or workaround?

thanks guys

edit: took networking off in rc0.d and rc6.d, now the nm-dispatcher.action line disappeared, but still hangs at shutdown or reboot, now the most likely problem is with init or modem-manager......

This *could* be totally un-related, but when I put the modem driver onto my laptop (Gateway - so deffinately NOT an IBM), I lost sound and had other 'funnies' - Going into System --> Administration --> HardWare Drivers and removing it sorted it for me. So, I've lost my modem - lol

It's worth a try.

Phill.

---

### Post by Vanishing on 2009-12-19
> **phillw said:**
> This *could* be totally un-related, but when I put the modem driver onto my laptop (Gateway - so deffinately NOT an IBM), I lost sound and had other 'funnies' - Going into System --> Administration --> HardWare Drivers and removing it sorted it for me. So, I've lost my modem - lol

It's worth a try.

Phill.

Hmm..I don't have anything in Hardware Drivers except for that ATI graphic, which I don't want to mess with now.

From what I've heard and seen, the main problem could be with my bios settings, which I'm not so sure which one....
it could also be init problem...
let's wait and see if update could solve the problems, getting my fingers crossed...

Also, when I used the magic keys(alt+prtSc+reisub), usually it should restart immediately, but on this t500, it will freeze for about 10-15 secs before it actually restarts....

Thanks mate.

---

### Post by Vanishing on 2009-12-20
I did a little experiment today, and I found out if I do 
> sudo /etc/init.d/restart stop, it actually restarts, which made me lol....
> sudo shutdown -h now
and 
> sudo reboot
still hangs.

---

### Post by ranch hand on 2009-12-20
I am on a desktop box so this may be different but haveyou checked your power settings?

I always set the power button to "shut down" when pushed.  This has worked for me when no other method was available or were not working.

---

### Post by Vanishing on 2009-12-21
> **ranch hand said:**
> I am on a desktop box so this may be different but haveyou checked your power settings?

I always set the power button to "shut down" when pushed.  This has worked for me when no other method was available or were not working.

I set it to "Ask me"
Ill try to set it to shutdown..

---

