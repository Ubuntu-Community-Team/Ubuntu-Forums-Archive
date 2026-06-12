---
title: "Trouble installing ubuntu."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by maxiscool on 2008-09-07
Well I wanted to try linux out so I downloaded wubi set everything up downloaded and then reboot. The Ubuntu loading bar appeared for a little awhile and then froze and my capslock key started flashing. So I messed around with the settings at the boot screen thing and got it to try and install with text and I get the error Kernal Panic: Aieeeee something something. So today I tried downloading the iso making sure I chose AMD64, burned it then booted but I got the same thing, the ubuntu loading bar appears forawhile but then freezes im not sure if its the same Kernal Panic thing but it probably is. 

My laptop is a compaq, TurionX64, Nvidia graphics, 3 gigs of ram with vista.

---

### Post by overdrank on 2008-09-07
> **maxiscool said:**
> Well I wanted to try linux out so I downloaded wubi set everything up downloaded and then reboot. The Ubuntu loading bar appeared for a little awhile and then froze and my capslock key started flashing. So I messed around with the settings at the boot screen thing and got it to try and install with text and I get the error Kernal Panic: Aieeeee something something. So today I tried downloading the iso making sure I chose AMD64, burned it then booted but I got the same thing, the ubuntu loading bar appears forawhile but then freezes im not sure if its the same Kernal Panic thing but it probably is. 

My laptop is a compaq, TurionX64, Nvidia graphics, 3 gigs of ram with vista.

Hi and welcome, when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add noapic. This will allow you to see any errors and hopefully boot to the live cd.

---

### Post by maxiscool on 2008-09-07
alright ill try it

---

### Post by maxiscool on 2008-09-07
Got this awesome error:

Kernal Panic: not syncing:Machine Check

---

### Post by maxiscool on 2008-09-07
im thinking of giving up, is there another distro I should try? or is this error a linux problem in general not a ubuntu problem?

---

### Post by maxiscool on 2008-09-07
the bumpz in da hood son wut up?

---

### Post by Sef on 2008-09-07
Don't bump until 24 hours have gone by.  Answers can take time.  Please have patience.

---

### Post by maxiscool on 2008-09-07
ight, i guess ill try and install debian in the meantime althought looks more complicated

---

### Post by maxiscool on 2008-09-08
bump, i tried installing openSUSE and got the same error

---

### Post by overdrank on 2008-09-08
> **maxiscool said:**
> bump, i tried installing openSUSE and got the same error

Hi and you may try some of these kernel options
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)
Good luck!

---

