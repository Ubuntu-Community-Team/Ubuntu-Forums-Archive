---
title: "Upgrade Woes"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by danbicknell on 2011-05-08
I like Ubuntu 11.04 but this has been THE ROUGHEST upgrade I've experienced so far.

Background:  I had a 9.04 server that I decided to upgrade 11.04.  Because of difficulties, I had to scrap the upgrade and installed 11.04 from scratch.  My primary use of this machine is a server, so I installed that first.  But I also like to use it as a desktop and installed Gnome on top of this.  I have spent a great deal of time since wrestling with various installation glitches - here are the remaining 3 unsolved:

1)  In Gnome, if I try to use Synaptic Package Manager or the Update Manager, it will not accept my password.  However, if I drop to the command line, I can run these (sudo /usr/sbin/synaptic).  Gnome appears to accept my password for root privileges everywhere else.

2)  My system does not support Unity (it's an older computer).  I have set the default Gnome to Ubuntu Classic.  Still, with new users added or attempting to log in with NXServer, it tries to go to Unity first.  

3)  During boot up, when I get to GRUB, the system switches to an unsupported video mode (again, I have an older system) and I cannot see the GRUB menu (I can however, hit the down arrow key once and press enter to go into Recovery mode).  What on earth is Ubuntu doing switching graphics modes BEFORE you get past GRUB?  Seriously, is there a way to disable this?  How are you supposed to recover if you're having graphics issues?

Any help with any of these would certainly be appreciated!

Thanks,
Dan

---

### Post by Hedgehog1 on 2011-05-08
I can help with #3, at least.

After booting into Ubuntu, please do this:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by danbicknell on 2011-05-08
> **Hedgehog1 said:**
> I can help with #3, at least.
After booting into Ubuntu, please do this:
```
gksudo gedit /etc/default/grub
```[COLOR=Red]and change this line:[/COLOR]
#GRUB_GFXMODE=640x480
[COLOR=red]to this:[/COLOR]
GRUB_GFXMODE=640x480
```
sudo update-grub
```
***The Hedge***
:KS

Thanks - that worked.  Or at least that solves #3.

I know that Ubuntu wants to mask everything to make the OS simple to use - they're trying to go mainstream and I applaud them for this.  Still, that isn't why I want to run a Linux server.  I'll keep Ubuntu on my laptop (Unity and all) - I really respect Ubuntu and want to see them become a major  OS.  But I'm wondering, with the direction Ubuntu is going, if it's still the best choice for a Linux server?

---

### Post by mörgæs on 2011-05-08
For a server installation, I would choose 10.04.2. It is supported until 2015, and after getting to the .2 step, it is rock-solid.

---

