---
title: "[SOLVED] How to upgrade Ubuntu Desktop (generic) to Server"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by TheR on 2008-09-03
I have problem instaling Ubuntu 8.04 on XenEnterprise 3.2. Basicly, keyboard is death on the first instalation dialog (choose language). This is happening since 7.04.

Nevermind. I am able to install Ubuntu 8.04. from mini CD instalation. But the problem is that whatever configuration I choose on software select it always installs Desktop (generic) kernal, which I assume won't have 5years of support.

So I am thinking now. Is it possible to upgrade generic kernel to server kernel?

by
TheR

---

### Post by TheR on 2008-09-05
No way or nobody knows?

by
TheR

---

### Post by Bucky Ball on 2008-09-05
Upgrade through the desktop take forever and can be problematic. The server install is text based anyhow. You would actually be looking to *remove* a lot of stuff that a server doesn't need. You would actually be downgrading rather than upgrading (no gui - you need to download gnome). Just download (or torrent - faster and more reliable) the server install and stick it in, then sudo apt-get the packages you are wanting to use.

Details of your machine will help as if it is old and not much ram, that could be your problem with 8.04 LTS.

Incidentally, LTS = long term support - 6 months. Intrepid Ibis should be about before christmas as Hardy launched in April. This is not really an issue and it is not like windoze so wouldn't worry anyhow, just enjoy!

 :)

---

### Post by kalesh7 on 2008-09-05
First up I would not recommend it, as you have 3 years support with desktop (generic) and by the time its three years you will most likely be running the latest version (which will have 3 years support from its release date) so just keep upgrading as the ditros come out and you have lifetime support 

but if you are bent on it
just installing the kernel
sudo apt-get install linux-server
(or use sypnatic to install linux-server)
I do not know if this will have compatibility problems with other ubuntu programs or such so do it on your own risk
also following that you may need to edit the grub menu or something

moving to full server edition
just get the server cd and do a reinstall:)
as stated previously this will not have gui and a lot of other stuff and you probably don't want this

---

### Post by Bucky Ball on 2008-09-05
Sorry, I stand corrected - LTS = 3 years. :)

---

### Post by TheR on 2008-09-05
Thanks guys I will try to update kernel next week.

As I sad I had to install from mini CD version which offers cli installation and doesn't install any gui and no programs at all. It is almost as server environment, only that  the kernel suffix is generic and not server.

And I can not install from original cd, because I am instaling into virtual machine on xen 3.2 server and instalation chokes on initial screen where the keyboard just dowsn't work.


by
TheR

---

### Post by Bucky Ball on 2008-09-05
Cool. :)

Could you mark this thread as solved using 'Thread Tools' and catch you in the forums.

---

