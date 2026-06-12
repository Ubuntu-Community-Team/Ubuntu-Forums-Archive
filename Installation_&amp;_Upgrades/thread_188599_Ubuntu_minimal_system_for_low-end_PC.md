---
title: "Ubuntu minimal system for low-end PC"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by davidbd on 2006-06-04
Hello,
I would like to install Ubuntu for low-end PC.
I need the simplest and fastes window-manager.

I think of installing Ubuntu-Server and than install X-server and x-windows and basic windows-manager.

What is the recommnedad steps to do so and it is possible.

Best-Regards
David.

---

### Post by Poirot on 2006-06-04
How about Xubuntu?

---

### Post by Poirot on 2006-06-04
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by davidbd on 2006-06-04
[QUOTE=Poirot][http://www.xubuntu.org/](http://www.xubuntu.org/)[/QUOTE]

What is the size of the installation ?

I need minimla HDD/CPU usage.

Main purposes:
- FTP server
- SSH server
- SMBA server
- Surfing - Firefox
- Mail clent
- P2P client ( amule/bittorent)

Not need to all desktop tools and not need for KDE/Gnome.

I need simple and fast Window-manger.

Regards,
David.

---

### Post by rcarring on 2006-06-04
The low-end pc -- if you have less than 128mb ram it will seriously impact your experience, I am not even sure that Dapper Desktop will boot with less than 128mb ram.

Dapper Server may be an alternative.

---

### Post by davidbd on 2006-06-04
[QUOTE=rcarring]The low-end pc -- if you have less than 128mb ram it will seriously impact your experience, I am not even sure that Dapper Desktop will boot with less than 128mb ram.

Dapper Server may be an alternative.[/QUOTE]

[QUOTE=Poirot][http://www.xubuntu.org/](http://www.xubuntu.org/)[/QUOTE]

I have :
- 256M RAM
- 3G HD
- P-III 700MHz

Ho to install minimal x-window support with simple window-manager ?

Regrads,
David.

---

### Post by rcarring on 2006-06-04
Do a default install.
Make sure it works.

Then search on the net for a low-end window manager and install it, alternatively it may be listed in the All section under synaptic.

Your disk space may be a problem as the default install may use probably 90% of it.

I guess this is why you want the minimal install.

Try Dapper Server.

Then you can add x support and so on.

---

### Post by davidbd on 2006-06-04
[QUOTE=rcarring]Do a default install.
Make sure it works.

Then search on the net for a low-end window manager and install it, alternatively it may be listed in the All section under synaptic.

Your disk space may be a problem as the default install may use probably 90% of it.

I guess this is why you want the minimal install.

Try Dapper Server.

Then you can add x support and so on.[/QUOTE]

How to install x support ?
David.

---

### Post by rcarring on 2006-06-04
Assume you have a working network connection...

```


sudo apt-get install xserver-xorg xserver-common


```

This should pull in the dependencies.

---

### Post by davidbd on 2006-06-04
[QUOTE=rcarring]Assume you have a working network connection...

```


sudo apt-get install xserver-xorg xserver-common


```

This should pull in the dependencies.[/QUOTE]

What about the windows manager ?
What are your recommnedations ?

---

### Post by rcarring on 2006-06-04
xfce4

This is the recommended environment for low-end systems.

```

sudo apt-get install xfce4

```

This is a meta-package that will pull in dependencies.

Hope this helps.

I checked some others, however there is a wealth of info on xfce4 and people have installed it.

---

### Post by msofer on 2006-06-04
(not sure why you may want *my* recommendation)

I run icewm, which is fairly complete and small and fast. I have been using it for many years now: familiarity is a big reason in my choice too. Other popular choices for small distros are jwm (puppylinux), fluxbox (dsl), fvwm2, fvwm95. I have seen enlightenment being praised for such uses too.

You may want to choose yourself - interesting resources to help you might be [xwinman]("http://plig.org/xwinman/") and maybe [this]("http://www.linux.org/apps/all/GUI/Window_Managers.html").

---

### Post by confused57 on 2006-06-04
You might want to try Puppy Linux:

[http://www.puppylinux.org/user/readarticle.php?article_id=4](http://www.puppylinux.org/user/readarticle.php?article_id=4)

[http://www.puppylinux.com/](http://www.puppylinux.com/)

I think you'd need to use gparted to format your hd with ext2, and maybe a 250 mg swap partition before installing:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

I'm planning on trying to install Puppy Linux to triple boot, I plan on doing it this way:
1.)Use gparted to make partitions.
Steps taken from link above(start Puppy Live CD):
2.)Start--->Setup--->"Install Puppy Hard Drive"
3.)Option 2, full install
4.)partition to install on /dev/hda1(or whatever your partition is)
5.)install grub to mbr(or to floppy, I plan on not installing grub, I'll just add an entry to my grub/menu.lst for puppy)

The Puppy Linux documentation takes awhile to navigate, but I've tried to summarize how I plan on doing it...it's an option for you...if you try this, let us know how it worked.

---

### Post by az on 2006-06-04
[QUOTE=davidbd]Hello,
I would like to install Ubuntu for low-end PC.
I need the simplest and fastes window-manager.

I think of installing Ubuntu-Server and than install X-server and x-windows and basic windows-manager.

What is the recommnedad steps to do so and it is possible.

Best-Regards
David.[/QUOTE]
Do not install the server setup, you will end up with a kernel that is not optimised for what you want.  Use the alternate installer cd and use th eminimal option (used to be called server, nut I am not sure if that still is so.  The actual server install now has it's own cd - don't use that.

Once you reboot into your new system, at the command line edit /etc/apt/source s.list

sudo nano /etc/apt/sources.list

and uncomment the universe repo.

sudo apt-get update

sudo apt-get install x-window-system-core gdm icewm menu synaptic xterm

---

### Post by woopud on 2006-06-04
[QUOTE=davidbd]I have :
- 256M RAM
- 3G HD
- P-III 700MHz

Ho to install minimal x-window support with simple window-manager ?

Regrads,
David.[/QUOTE]

Give me a break! low end pc...., I run Dapper on a P1 433 mhz using Gnome runs just fine.

Bert

---

### Post by adament on 2006-06-05
[QUOTE=davidbd]What about the windows manager ?
What are your recommnedations ?[/QUOTE]
You might want to give fluxbox a look. [http://fluxbox.sourceforge.net/]("http://fluxbox.sourceforge.net/") last time I used it, it was pretty minimal and fast

---

### Post by ouphe on 2006-06-05
[QUOTE=adament]You might want to give fluxbox a look. [http://fluxbox.sourceforge.net/]("http://fluxbox.sourceforge.net/") last time I used it, it was pretty minimal and fast[/QUOTE]

I'd have to agree. It ran fine/very fast on a p200 mmx system with 256MB RAM. The configuration is a bit cumbersome but fairly easy.

---

### Post by Poirot on 2006-06-06
I hear fluxbox is pretty neat.
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

---

