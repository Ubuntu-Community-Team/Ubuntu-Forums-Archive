---
title: "Why cant i install Ubuntu on my system?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by jaymz789 on 2007-01-11
I cannot install ubuntu to my system, it is giving a list of errors. Then i tried installing fedora too but that is also giving me a list of errors.Find attached two pics of error msgs that i found trying to install both the OS. What are these errors?

---

### Post by Jussi Kukkonen on 2007-01-11
At what stage of the install does this happen -- right at the beginning or do you get to the installer?

Also, can you describe your hardware? How much memory? Could the memory be faulty?

---

### Post by unisol on 2007-01-11
sounds like a memory error to me. can you use the cd to do a memtest?

---

### Post by speckbe on 2007-01-12
I am also new to Linux and I to get the exact same error message.  The error message seems to occur at about the time the Ubuntu splach screen disapears.  I get the error when I try to run from the Live CD, Safe Graphics, or install.

My configuration is:
Dell 2350
1Gig Ram
P4 2.4
gForce 5500 graphics card.

---

### Post by jaymz789 on 2007-01-14
Hey unisol, if it is a memory error why am i running Win XP smoothly on my system? And how can i do a mem test with the cd?

And Jussi Kokkonen, My config is Dell Optiplex L60, P4 2.0Ghz, 512MB Ram, 256MB Geforce FX 5500 PCI Display.

---

### Post by wpshooter on 2007-01-14
Did you test the integrity of your Ubuntu installation CD by running the verification function found on the initial Ubuntu boot screen menu ?

---

### Post by old_geekster on 2007-01-14
> **jaymz789 said:**
> And how can i do a mem test with the cd?
Memtest is on on the installation disk.  If, however, you can't find it there, run Memtest in Windows.  This will give you the same outcome.  Bad memory is bad memory.

---

### Post by louieb on 2007-01-15
My guess is that you get to enjoy playing with boot options. 
Some of most common ones can be found here.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
The first one  I try is ide=nodma.

---

### Post by Bartender on 2007-01-15
louieb -
Do you know where they list any more of these boot options?  I checked out your link.  

I've got a modern ASUS motherboard, running a P4 Intel CPU, SATA HDD, nothing exotic.  Yet it has refused to run any flavor of Ubuntu - Xu, Ku, Ubuntu Breezy thru Edgy.  Tried Mint Bea and it failed too.
I let Dapper flail away for an hour or so.  It stalled at "detecting hardware" for a long time.  It finally got to a desktop but when I went into Device Manager it couldn't even tell that there was a HDD in the system.

A PCLOS "Big Daddy" LiveCD gave me a desktop without complaint.

I'd kinda given up on dual-booting Ubuntu, but now would like to try some of these boot options.  I'll try your ide=nodma first.

---

### Post by louieb on 2007-01-15
> **Bartender said:**
> louieb -Do you know where they list any more of these boot options?  I checked out your link.  
Not really I usually do a [Google-Linux search.]("http://www.google.com/linux?hl=en&lr=&q=boot+options&btnG=Search") One thing to think about is boot options are something used by the Linux Kernel and are not specific to any particular Linux distro.  That means if you find a page of boot options for Debian or Red Hat or some other distro go ahead and try it. They all use pretty much the same Linux kernel.

---

### Post by Bartender on 2007-01-15
OK, thanks, louie -
I tried ide=nodma, no difference.  It still hung at "detecting hardware".  Then after ten minutes or so it said "fail" and tried to move on but if it ever gets to the desktop it won't see a HDD.

---

