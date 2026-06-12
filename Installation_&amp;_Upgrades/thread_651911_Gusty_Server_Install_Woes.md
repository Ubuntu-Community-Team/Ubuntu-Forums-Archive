---
title: "Gusty Server Install Woes"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by AshtonTheGeek on 2007-12-28
Hi everybody,

I am a bit of a command line n00b so please bear with me. I am trying to set up a server (using Ubuntu 7.10 server) on an old machine I have (Compaq Deskpro 2000 5200MMX, with a Pentium MMX 200mhz, 96mb of RAM and a 2gb HDD) to run Apache with PHP 5, PostgreSQL, OpenSSH and possibly a mail server. So anyhow, I tried to install it this morning (the machine is fully functional and has been happily running Windows 2k for the last year or so), and I got an error saying that I would have to force ACPI using acpi=force in the boot parameters. So, I punched that into the extra boot options to force ACPI, and now I'm getting an error saying that I will have to specify where to mount something-or-other using a "root=" declaration in the boot options. I tried the following:

boot: install acpi=force root=hda0
boot: install acpi=force root=hda1

and neither worked. Yeah, I'm a bit of a n00b when it comes to the more technical things regarding Linux (i'm a full time Winblows user), so it would be most appreciated if anyone could give me a hand with this. Thanks.

---

### Post by Partyboi2 on 2007-12-28
I think you might struggle to install ubuntu with those spec's
maybe look at a different linux distro eg.
Darn small linux (dsl)
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by Partyboi2 on 2007-12-28
Sorry, I re-read what you had posted and realized you are trying to install the server version.
try updating your bios if you are able too.

---

### Post by AshtonTheGeek on 2007-12-28
> **Partyboi2 said:**
> Sorry, I re-read what you had posted and realized you are trying to install the server version.
try updating your bios if you are able too.

I'm pretty sure this thing is running the latest BIOS that is available for it.

---

### Post by Partyboi2 on 2007-12-28
Just to confirm
When you get to the main menu screen, you pressed F6 then at the end of the line you added
[SIZE=-1]**acpi=force** then pressed enter?
Then it gave you another error? what was the exact error?
[/SIZE]

---

### Post by AshtonTheGeek on 2007-12-28
> **Partyboi2 said:**
> Just to confirm
When you get to the main menu screen, you pressed F6 then at the end of the line you added
[SIZE=-1]**acpi=force** then pressed enter?
Then it gave you another error? what was the exact error?
[/SIZE]

Correct. It came up and said something along the lines of "unable to mount FS on root='NULL'" and then said please specify a root= or something like that. Sorry, I can't boot the machine at the moment because I am not at home.

---

