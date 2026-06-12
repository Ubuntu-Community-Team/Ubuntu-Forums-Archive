---
title: "Problems with audio after upgrade"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by leillo1975 on 2009-02-25
Hello

I'm install the last alpha of Jaunty today, and when the process ended, I see two volume controls in the upper bar of my desktop. The sound when I Log on are distorted, but then It works normally

Then I upgrade my system, restart, and Log on (logon sound ok). There are only a volume control y the upper bar (correctly), but I have no sound (I try with totem, vlc, amarok...). 

I try to configure sound in System-> Preferences-> Sound with all options but the problem persists.



Note: Sorry, my english is very bad, I'm from Spain

---

### Post by taavikko on 2009-02-25
It has something to do with HAL.
It should be fixed and available soon in repositories...

```
Date: Wed, 25 Feb 2009 15:00:28 -0000
From: Martin Pitt <martin.pitt@ubuntu.com>
Subject: [ubuntu/jaunty] hal 0.5.12~rc1+git20090204-0ubuntu3
       (Accepted)
To: jaunty-changes@lists.ubuntu.com
Message-ID:
       <20090225150028.26114.245.launchpad@cocoplum.canonical.com>
Content-Type: text/plain; charset="utf-8"

hal (0.5.12~rc1+git20090204-0ubuntu3) jaunty; urgency=low

 * 87_standalone_smbios.patch: Add missing bit from
   autoreconfiscation, which brings back the building and
   installation of hal-acl-tool. This repairs automatic ACLs, and
   thus sound card, camera, scanner, DRI, and other device access.
   Thanks to Mario Limonciello for the patch! (LP: #334299)
```

---

### Post by rogerdean on 2009-02-25
no idea if it's related, but i've just lost all sound...

---

### Post by doffe on 2009-02-25
same here, lost sound (HDA intel ALC260 Analog), just have to wait on a new update i guess.

---

### Post by cabernet54 on 2009-02-25
Here is SOLVED with a little workaronud:

[http://ubuntuforums.org/showthread.php?t=1012636&page=2](http://ubuntuforums.org/showthread.php?t=1012636&page=2)
> 
 Re: Null audio output device
Quote:
Originally Posted by frasch View Post
Hi,
Code:

sudo adduser <username> <groupnname>

example:
Code:

sudo adduser tom audio

or use systemsettings on gnome btw. kuser on kde

Frank
Worked like a charm. Thanks for the tip!

:guitar::popcorn:;)

---

### Post by rogerdean on 2009-02-25
Beat me to it! All works now, many thanks
Roger

---

### Post by leillo1975 on 2009-02-25
Thank you, now the sound works fine

Thanks again

---

### Post by Stephmau on 2009-02-25
New version of Hal. After upgrade and reboot, the sound comes back.

---

