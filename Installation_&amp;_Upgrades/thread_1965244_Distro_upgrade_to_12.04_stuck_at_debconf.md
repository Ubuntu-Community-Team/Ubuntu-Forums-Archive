---
title: "Distro upgrade to 12.04 stuck at debconf"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by bobbaluba on 2012-04-25
I ran update-manager -d, and tried to upgrade to 12.04.
Now the installer is stuck (and have been for about half an hour)

Screenshots doesn't seem to be working at the moment, so I'll try to copy the contents of the terminal and describe what i see.

The orange loading bar is at the start of installing updates.
The message says Preparing setup of debconf (translated from norwegian)

```
 &#9474; services to be restarted now, and correct it if needed.                 
 &#9474;                                                                         
 &#9474; Note: restarting sshd/telnetd should not affect any existing            
 &#9474; connections.                                                            
 &#9474;                                                                         
 &#9474; Tjenester som skal restartes for oppgradering av GNU libc-biblioteket:  
 &#9474;                                                                         
 &#9474; ssh postfix cups cron atd_______________________________________________
_&#9474;                                                                         
 &#9474;                                  <Ok>                                   
 &#9474;                                                                        
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;                                                                             
--
```The terminal looks really messed up, the purple bar for entering services extends to the first character on the next line. There's two dashes below the box, and the cursor is on the middle of the line two lines below the box.

What do I do now? Is it safe to kill the installer?

EDIT: I'm upgrading from 11.10

EDIT2: I had to use my computer, so I killed the installer and tried to reboot. After the grub menu, the screen just turns on and off forever until i get bored. Now I'm back in windows again.

---

### Post by oleink on 2012-05-07
> **bobbaluba said:**
> I ran update-manager -d, and tried to upgrade to 12.04.
Now the installer is stuck (and have been for about half an hour)

Screenshots doesn't seem to be working at the moment, so I'll try to copy the contents of the terminal and describe what i see.

The orange loading bar is at the start of installing updates.
The message says Preparing setup of debconf (translated from norwegian)

```
 &#9474; services to be restarted now, and correct it if needed.                 
 &#9474;                                                                         
 &#9474; Note: restarting sshd/telnetd should not affect any existing            
 &#9474; connections.                                                            
 &#9474;                                                                         
 &#9474; Tjenester som skal restartes for oppgradering av GNU libc-biblioteket:  
 &#9474;                                                                         
 &#9474; ssh postfix cups cron atd_______________________________________________
_&#9474;                                                                         
 &#9474;                                  <Ok>                                   
 &#9474;                                                                        
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;                                                                             
--
```The terminal looks really messed up, the purple bar for entering services extends to the first character on the next line. There's two dashes below the box, and the cursor is on the middle of the line two lines below the box.

What do I do now? Is it safe to kill the installer?

EDIT: I'm upgrading from 11.10

EDIT2: I had to use my computer, so I killed the installer and tried to reboot. After the grub menu, the screen just turns on and off forever until i get bored. Now I'm back in windows again.

I feel bad because I couldnt say anything earlier but all you really needed to do was click the little terminal drop down and press enter and the install would have continued ( you had to hit it at least twice if memory servers).  Anyway as for getting back, now you need to try to repair but i think if you try to repair it with the new version you may have better luck

---

### Post by stevemk2011 on 2012-05-07
I had the same problem after starting my 64 bit upgrade from Upgrade Manager. It stopped with the message "preparing setup of debconf...." while at the "installing the upgrades" step. After waiting two and a half hours I clicked on the terminal arrow to open the terminal, then saw the above message. Used cursor keys to step down to "OK" then as stated above pressed enter twice.

---

### Post by markbellis on 2012-05-10
Thanks! Saved me from stopping the install. Also using 64-bit.

---

### Post by mateor on 2012-12-12
Wow. I was digging through top trying to find what was stalled, I didn't even see the terminal menu.

I almost restarted as well, since for some reason 'repo'stopped working and I needed to push something.

This needs to be addressed in some sort of pop-up window, if they are going to push updates through the Software Center. I am not going to update like that again, especially since I see how close I was to compromising my system.

Through the terminal or not at all. Every time I violate that rule, I regret it.

---

