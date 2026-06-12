---
title: "Ubuntu 8.10 stuck at &quot;Configuring network Interface&quot;"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by isomerase2210 on 2008-11-02
Hi!

I have upgraded from Ubuntu 8.04 to 8.10 today (via update manager, as described on the website) and everything seemed to work fine.

Until the system needed to reboot.

The boot process gets stuck at:

"**Configuring network interfaces...**"

On top of the "boot log" it says: 

"**Loading hardware drivers .... [COLOR=Red]Fail[/COLOR]**"

All the other "checkpoints" seem to be fine since it puts an [OK] next to each one.
Apparently he does recognise the keyboard, because i can use it to type. 
Pressin Ctrl+Alt+Del seems to drive on the boot process a little further but it gets stuck again at:

"**1052.751899 pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.**"

Please help! I am writing from another maching but I it is extremely important for me to get my Ubuntu PC working again, as I have a lot of non-backuped files on there.

_THANK YOU!_

---

### Post by Aroleto on 2008-11-03
Hi; 

FYI, same happens to me; if I do a Ctrl-Alt-Del, it continues booting, desktop is loaded, and everything seems to work right...so I'm not sure what's causing this, but at least in my case, everything goes well after the Ctrl-Alt-Del.

---

### Post by Peter09 on 2008-11-03
As a test:

type 'ESC' at the grub prompt and edit the second line in the boot prompt. (select the line and type E). Remove the 'quiet' option and insert 
'noapic noquiet' (without quotes).

Type B to let the boot process continue.

---

### Post by isomerase2210 on 2008-11-03
Thanks for your replies Peter09 and Aroleto! I am a linux newbie and really appreciate your help.

Okay, I opened the grub menu (which I didn't know existed, so thanks again for showing me!) and edited the line as you said. Unfortunately it did not have any effect.

Next I tried booting with the following line (without editing):

[B]Ubuntu 8.10, kernel 2.6.[COLOR=Red]27-7[/COLOR]-generic (recovery mode)
  [/B]
This time it said "Hardware drivers _found_" but got _stuck_ on 

**pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature**

I pressed Ctrl+Alt+Del and a menu came up with "Resume Boot" and a few other options (clean, dpkg, fsck, root, xfix). So I ran a **File System Check **andnoerrors came up so I assume everything is fine.

After that I did **Resume Boot** and the same thing as above happened, i.e. no fail messages, but stuck on "pan0: Dropping NETIF_F_UFO... bla bla"

NOW THE GOOD NEWS.

I went back to the grub menu, and this time i tried booting with what looked like the "older" kernel:

**Ubuntu 8.10, kernel 2.6.[COLOR=Red]24-21[/COLOR]-generic (recovery mode)**

And tadaaaa! It booted straight to the desktop and everything worked perfectly.

I also checked the lsb-release file located in /etc and it says:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid 
DISTRIB_DESCRIPTION="Ubuntu 8.10"

So I guess the upgrade from 8.04 to 8.10 did actually work! :p

Thus I have another question:

How do I make Ubuntu always **automatically choose** this "older" kernel at booting? In other words, [U]how do I make this change in the boot sequence permanent?
[/U] 
Thank you for your time!
isomerase2210

---

### Post by Peter09 on 2008-11-03
Here is the known bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059)

---

### Post by isomerase2210 on 2008-11-03
Thanks for the link Peter.

I found a temporary solution to the problem. 

I booted with the "stable" kernel from the grub menu.

Once on the desktop I did:
```
gksudo gedit /boot/grub/menu.lst
```

And I changed "**default=0**" (top of the page) to "**default=2**" because my working kernel was the** third** listed from the top (i.e. number 2 when counting from 0). This changed it to being the default boot kernel.

Now it boots normally :p YAY!

How important is it to use the "newest" kernel though? I hope there will be a fix for this soon... 

Anyway, thanks 1000x for your assistance!
I think we can close the thread as "solved".

---

