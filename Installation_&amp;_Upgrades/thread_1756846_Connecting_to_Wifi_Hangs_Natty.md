---
title: "Connecting to Wifi Hangs Natty"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Alchemise on 2011-05-12
Just upgraded to Natty on both my desktop and netbook. Desktop upgrade was a breeze, and I'm liking the changes.

Netbook isn't having such a good time however.

First login after upgrade (using default gnome settings) played the login sound and froze. No mouse movement/keyboard response. I tried again with Ubuntu Classic - nothing. Finally Ubuntu Classic No Effects did correctly boot/login. I allowed it to perform a proper shutdown (was doing a power flip beforehand), and it was able to boot into normal Ubuntu Unity.

I enabled the wifi module using the laptop's keyboard shortcut, and Ubuntu searched for nearby networks. After finding my prefered network, it started to connect and threw the system into a command console abyss and froze. 

Tried again on the Ubuntu Class no effects, and it freezes on connecting to a wifi network. If the laptop crashes and I have to perform a power cycle, I can't boot into normal Ubuntu mode. I have to go back into Classic no effects.


Thoughts?

--

Details

OS: Ubuntu 11.04 
Previous OS: 10.04 Ubuntu Desktop Edition
Laptop: Asus Eee 1001P
Wifi Network: WPA2/AES/PSK

---

### Post by NormanFLinux on 2011-05-12
I think you're right... the current Broadcom driver does not like 11.04. And that accounts for the desktop freeze. I'm betting if you shut your wireless LAN off in BIOS, the freeze disappears.

But then you have no wireless Internet connectivity.

And Canonical is not going to release updated drivers to fix the issue.

11.04 is a screwed pooch!

---

### Post by linux_one on 2011-05-19
the problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
to solve that you can download the latest kernel and install it very easily;
 go to 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.

---

### Post by Alchemise on 2011-05-21
Great fix!

Easy to follow instructions, took 5 mins and it works perfectly.

Did some quick tests and I'm getting good throughput, low ping & jitter, and no packet loss.


Many thanks

---

