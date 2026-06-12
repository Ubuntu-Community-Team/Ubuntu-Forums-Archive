---
title: "Installed New Kernel Opt. | Some Programs Don't Work"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by terces on 2006-11-07
I run on an Athlon 64 with 2GB RAM.

I currently had used Ubuntu 6.06 with a 2.6.15-27 i686 kernel.

I just recently installed 2.6.15-27 K7 kernel.

Some programs do not seem to work since switching, like Briquolo and VMWare Workstation.

Is it possible, with VMWare at least, that when I installed it I used i686 headers or something?  Any reason why these programs either never start or begin to appear in the task bar and then disappear?

---

### Post by codypumper on 2006-11-07
sudo apt-get install kernel-headers-2.6.15-k7
Give that a try...

---

### Post by terces on 2006-11-08
Sorry, I didn't mention that before posting I did have the headers appropriately placed.

---

### Post by codypumper on 2006-11-08
did you get linux headers?

---

### Post by terces on 2006-11-09
Sorry, I actually have the linux-headers installed and not the kernel-headers... I honestly didn't know there were two distinct groups of headers.

I did:

sudo apt-get install kernel-headers-2.6.15-k7

sudo apt-get install kernel-headers-2.6.15-27-k7

Unfortunately the package couldn't be found. 

I did a Google search for some headers but didn't seem to find a concrete place to get them. I also checked out kernel.org but I couldn't find any headers.

---

### Post by codypumper on 2006-11-09
are you running dapper?

---

### Post by terces on 2006-11-10
Yes, I am using Dapper.

---

### Post by codypumper on 2006-11-11
I too did a search for the kernel headers. All I could find are 2.4 headers. If you wanna give it a shot, you could install the 2.4 headers, or downgrade to 2.4 kernel for the headers. This could cause more issues, so I'd ask around a bit more, such as at [http://www.qunu.com](http://www.qunu.com)

---

