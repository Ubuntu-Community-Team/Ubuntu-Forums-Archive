---
title: "Grub Installer Question..."
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by margni on 2005-10-07
Howdy,

I wanted to ask an install question - before I go and install...

If I already have a WinXP/Fedora Core 3 box set up, and I wanted to take more of the space and set up Ubuntu, then...

Will Ubuntu re-write or overwrite my current Grub.conf in FC3?  

I have a FC3 working really well, and I tried out the live CD of Ubuntu - I liked it Too!  Now I wanted to load/configure it to run as another partition...

So does anyone have any experience in a 'Triple' partition? 

Many thanks in advance...

Margni

---

### Post by aysiu on 2005-10-07
[QUOTE=margni]
Will Ubuntu re-write or overwrite my current Grub.conf in FC3?[/QUOTE] Only if you choose to install Ubuntu's Grub to the MBR.

---

### Post by margni on 2005-10-07
OK, 

So that means there's an option for this - installing over a current grub.

Second, does that mean Ubuntu will write itself into the FC3 Grub.conf file -OR- do I need to add to the FC3 File myself?

Margni

ps. thanks!

---

### Post by SilentCacophony on 2005-10-07
Hi. If you already have grub installed in fedora, then the grub stage 1 in the MBR is pointing to that partition currently.

If you choose to install grub to the mbr during the ubuntu installation, it should have no problem detecting your other two operating systems, and adding them to the /boot/grub/menu.lst on the ubuntu installation. From then on, though, the grub stage 1 in the MBR will then point to the ubuntu partition and use that configuration. It won't touch the config on fedora. One thing to watch out for is that if you delete the ubuntu partition, you'd need to reinstall grub to the MBR, pointing back to the fedora partition (I've had to do that, before I understood grub ;) ).

Alternatively, you could choose not to install grub with ubuntu, and manually add the boot lines for ubuntu to your current fedora boot config.

---

### Post by margni on 2005-10-07
Thanks!  

I'm going to install, then config my current Grub.conf inside of FC3...

Another question then is...  If I already have a swap file (the one that is with Fedora) then do I need a second for Ubuntu, or will Ubuntu 'see' the current swap?

---

### Post by SilentCacophony on 2005-10-07
Ubuntu will generally 'see' and automatically select and existing swap partition.

---

### Post by margni on 2005-10-07
many thanks!

As you can see, I went through 'rookie season' on FC3, and figured out enough to be dangerous ;-)   I want to put a second distro on, so I can see them side by side...

BTW...  is Ubuntu based off of Red hat, or Debian...

---

### Post by SilentCacophony on 2005-10-07
It's debian-based, though a bit more targeted toward newer packages than debian. Ubuntu has it's own repositories, for one thing. It's still pretty young, and has few rough edges to smooth out, but makes remarkably rapid progress, and is quite usable.

Here is an unofficial [guide]("http://www.ubuntuguide.org/") for some common tasks you might want to do after getting it installed.

---

### Post by margni on 2005-10-08
Silent...

Many thanks...  I'll report back after I get the computer down off the rack...

Margni

---

