---
title: "used Alternate installer - now tries to network boot"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by mattisking on 2006-09-12
I accidentally used the Dapper alternate installer (wasn't paying close attention when I downloaded the ISO) instead of the "Live CD" for setting up my friend's laptop. That shouldn't really matter so I just went with it. However, once installation was complete, gnome wasn't installed. I had a booting system that let me login but no X. A quick check showed that a simple way to fix things was to install ubuntu-desktop which wasn't installed. Once this was done the machine boots great into Dapper.

However, the machine does something I'm not used to seeing. Upon booting, it first appears to try to boot off the network. It just sits there (I can get the text if needed) waiting to try and connect or something. If I simply hit <Ctrl><C> it stops that and moves right ahead to Grub and startup and runs great (with network support and all). Any ideas? It's a new install... I could certainly download the proper ISO and start over but I'd already done a fair amount of configuration and package installation so if there's a quick fix I'm all ears.

Thanks!

---

### Post by mattisking on 2006-09-12
Strike all that. I got it. It's just some strange BIOS setting in this old laptop.

---

