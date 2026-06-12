---
title: "Networking Broken After Distribution Upgrade"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by megsuma on 2007-12-17
Hi all, so here it goes:

I recently upgraded my room mate's laptop via the adept update manager and things didn't go so swell...a couple of times. Once I finally got it to take, I got some VFS root missing errors on boot with new kernel, but I'll go back for that later - my main concern right now is that (when I'm booted into the old kernel) the network goes plop.  At first I thought it was something fishy with the wireless, but no complaints from ipw2200 on boot up and the wired link doesn't work either. Both cards come up and work fine as far as I can tell.

On ifup, say for eth0 (wireless) I get something to the effect of (and I can't copy/pasta since that machine isn't online :P)

~# sudo ifup eth0
Blah blah blah dhcp software license notice etc
-snip!-
SIOCSIFADDR: Permission denied (even with sudo wtf?!)
SIOCSIFLAGS: Permission denied
SIOCSIFLAGS: Permission denied
Listening on LPF/eth0/ma:ca:dd:re:ss
Sending on LPF/eth0/ma:ca:dd:re:ss
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted

OK, so then it hangs until I ^C out of it - syslog (maybe messages I can't recall) repeats pretty much everything I put above with one additional message: 
kernel [some#s] eth0: No IPv6 routers present

The same happens for the wired connection except it gets the OFFER and ACK a little faster.

---

### Post by wilho on 2008-05-02
same happened to me after upgrading to hardy. Did you resolve this?

---

