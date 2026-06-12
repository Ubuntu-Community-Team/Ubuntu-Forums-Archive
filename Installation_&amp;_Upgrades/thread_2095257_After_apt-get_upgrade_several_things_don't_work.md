---
title: "After apt-get upgrade several things don't work"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by VanillaXtract on 2012-12-16
I installed some packages last night. I was doing some network troubleshooting so I rebooted my machine. Upon reboot I can no longer open terminal, system settings, or tweak tool. My dual monitors are in mirror mode and since I can't access settings, I can't change it back. Also my theme is back to default. Here is the apt-get history that I think caused this:
[http://pastebin.com/Wc1yWN2n]("http://pastebin.com/Wc1yWN2n")

And here is my sys log right after attempting to open system settings:
[http://pastebin.com/H2Q1J1CA]("http://pastebin.com/H2Q1J1CA")

Any help is greatly appreciated.

---

### Post by 2F4U on 2012-12-16
I found the following errors in the system log file:

> Dec 16 08:54:20 VX kernel: [   43.034692] bluetooth-apple[2174]:  segfault at 634 ip 00007f4b4333f0ad sp 00007fff4980afb0 error 4 in  libglib-2.0.so.0.3503.0[7f4b43307000+f7000]

> Dec 16 08:54:26 VX kernel: [   49.946897] gnome-control-c[2370]:  segfault at 6e0000009f ip 00007fd0827a70ad sp 00007fff99155270 error 4  in libglib-2.0.so.0.3503.0[7fd08276f000+f7000]

> Dec 16 08:55:19 VX kernel: [  102.821529] update-notifier[2804]:  segfault at 634 ip 00007fb073d6a0ad sp 00007fffb35ca980 error 4 in  libglib-2.0.so.0.3503.0[7fb073d32000+f7000]

> Dec 16 09:02:16 VX kernel: [  519.511598] gnome-control-c[2979]:  segfault at 6e0000009f ip 00007f33bf3170ad sp 00007fff77512bf0 error 4  in libglib-2.0.so.0.3503.0[7f33bf2df000+f7000] rtkit-daemon[1609]:  Supervising 3 threads of 1 processes of 1 users.

In the update logs I saw an update to Gnome Shell, among others.

---

### Post by VanillaXtract on 2012-12-16
> **2F4U said:**
> I found the following errors in the system log file:
In the update logs I saw an update to Gnome Shell, among others.

I'm new to linux. Should I try reinstalling an older version of gnome shell?

---

