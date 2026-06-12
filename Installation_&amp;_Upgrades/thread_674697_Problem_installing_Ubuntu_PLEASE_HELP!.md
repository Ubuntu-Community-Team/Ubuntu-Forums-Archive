---
title: "Problem installing Ubuntu PLEASE HELP!"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by AG336 on 2008-01-22
Hi guys, 

Ok I downloaded and burned the correct version of Ubuntu for my pc to a cd. 

I then proceeded to reboot.. I get the Ubuntu screen with the Start or Install Ubuntu and so on.. so far so good..

When I choose ANY of the options (Start or Install, Safe Graphics Mode) it gives me this error:

MP-BIOS bug: 8254 timer not connected to IO-APIC
 Kernel pasnic - not syncing: IO-APIC + timer doesn't work!
Boot with apic=debug and send report.Then try booting with "noapic" option

now, I did some research on this issue and learned that I had to press F6 then added 'noapic' to the end of the command line that opens at the bottom.

I did this, and it did infact get rid of that error screen and then I get the Ubuntu logo and a loading bar but then I get this:

Busybox v1.1.3 (Debian 1:1.1.3-3unbuntu) Built in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) 

it looks like I'm supposed to enter something on here? but I have no idea.. I tried typing help to see the commands and I have no idea what to do.. my friend who installed Ubuntu didn't go through this and the installations guide never mention any of this..so i'm guessing that's not what is supposed to come up..

any help would be appreciated I wanna get rid of Windows it just keeps pissing me off more and more everyday!!

thanks

---

### Post by jon_gunnar on 2008-01-22
> **AG336 said:**
> Hi guys, 

Ok I downloaded and burned the correct version of Ubuntu for my pc to a cd. 

I then proceeded to reboot.. I get the Ubuntu screen with the Start or Install Ubuntu and so on.. so far so good..

When I choose ANY of the options (Start or Install, Safe Graphics Mode) it gives me this error:

MP-BIOS bug: 8254 timer not connected to IO-APIC
 Kernel pasnic - not syncing: IO-APIC + timer doesn't work!
Boot with apic=debug and send report.Then try booting with "noapic" option

now, I did some research on this issue and learned that I had to press F6 then added 'noapic' to the end of the command line that opens at the bottom.

I did this, and it did infact get rid of that error screen and then I get the Ubuntu logo and a loading bar but then I get this:

Busybox v1.1.3 (Debian 1:1.1.3-3unbuntu) Built in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) 

it looks like I'm supposed to enter something on here? but I have no idea.. I tried typing help to see the commands and I have no idea what to do.. my friend who installed Ubuntu didn't go through this and the installations guide never mention any of this..so i'm guessing that's not what is supposed to come up..

any help would be appreciated I wanna get rid of Windows it just keeps pissing me off more and more everyday!!

thanks

Maybe this posting may be of help for you.
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

Looks like there is at least a couple of things that has worked for other with the same problem.

---

### Post by AG336 on 2008-01-22
> **jon_gunnar said:**
> Maybe this posting may be of help for you.
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

Looks like there is at least a couple of things that has worked for other with the same problem.

Thanks but I think I'm past the MP-BIOS noapic problem.. 

Also, I did some more research on the INITFRAMFS problem and tried typing 'modprobe ide_core' then enter then exit then enter.. it didn't work..

---

### Post by AG336 on 2008-01-22
*bump* Anybody? lol help me install Ubuntu :( I hate Windows

---

### Post by AG336 on 2008-01-22
2nd bump*

---

### Post by kellemes on 2008-01-22
Sorry, I'm too stupid to help ;-)

You can try the alternate-installer, you need to tick the checkbox at the downloadpage to get it.. Often it seems to work when the livecd has issues.

---

### Post by AG336 on 2008-01-23
Do I need to know any special codes to install with a text based installer? sorry i'm a total n00b with linux..

---

### Post by kellemes on 2008-01-23
> **AG336 said:**
> Do I need to know any special codes to install with a text based installer? sorry i'm a total n00b with linux..


No, nothing special to do.. well, except the usual stuff, think about where you want it to install etc..
The installer speaks for itself mostly.

Let us know if you have questions..

---

### Post by AG336 on 2008-01-24
damn it same thing happens lol this sucks there's a lot of ppl that have this problem and just gave up on it :(

---

### Post by AG336 on 2008-02-25
anybody hear about any solutions to this problem? i can't go on with windows i might just sell this pc so i can install ubuntu on a new one lol

---

