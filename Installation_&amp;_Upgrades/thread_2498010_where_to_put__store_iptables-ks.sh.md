---
title: "where to put / store iptables-ks.sh"
date: 2024-05-26
forum: Installation &amp; Upgrades
---

### Post by heian on 2024-05-26
Hi,

I'm on Ubuntu 24.04 LTS  (fresh install)  and added my PrivateVPN account in open VPN.  The VPN works fine.

Now I'm trying to add a Kill switch to it, and the guys from PrivateVPN send me a modified  iptables-ks.sh  file.
They asked me to _"use"_  it.  (it is on my desktop now  :confused:).

( Next thing I have to do is to run:  # chmod +x iptables-ks.sh # ./iptables-ks.sh in the terminal )

Can someone point me out what to do exactly with this file?  Do I need to replace an 'old' iptables-ks.sh for the modified one, or 
just store it in a folder?  (which one?)

It goes far beyond my knowledge atm.

---

### Post by TheFu on 2024-05-26
PrivateVPN has provided you with specific instructions for a script they created.  Only they know what "use it" means or where it should be placed.  iptables-ks.sh is just a name for a file they made up.  I've never seen it before and it certainly isn't "standard" for openvpn installs.

Typically, system-wide stuff like a VPN configuration and tools for it would be placed somewhere under /etc/.  Of course, the package manager version of openvpn would install the programs, libraries, and kernel module(s) where those belong in the overall Linux hierarchy. 

I keep my openvpn stuff in /etc/openvpn/, but that is certs and configs, not scripts.  For a script that does what I can only guess the provided script does, I'd place it in /usr/local/sbin/ .... or I'd find a way to have it start and stop using the openvpn start/stop  scripts provided from the VPN vendor.  My openvpn start and stop scripts are non-trivial and customized for my needs, so they wouldn't be too useful to anyone else.  I've been running my own servers for about 15 yrs.  Before doing it at home, I deployed enterprise VPN systems for a few companies - we didn't use openvpn and had hardware tokens required for logins.  Plus, I stopped using openvpn at home a few years ago, choosing wireguard instead.  Much easier to setup and much faster throughput.

Sorry, I suspect all of this isn't much help and your eyes may have glazed over. I figured some response was better than none.  Perhaps not.  In short, get more support from the VPN provider.

---

### Post by currentshaft on 2024-05-26
0-1

---

### Post by MAFoElffen on 2024-05-27
Supplied by your Vendor? 

First, since they say that was a changed/modified/amended script for them... After making it executible, I would do
```

find / -name iptables-ks.sh 2>/dev/null

```
To see where they had it installed to, then move the new script there to overwrite the old one.

If it is a new script to be used for all users on the system (not just  you), then the logical place to put it in either /usr/local/bin or  /usr/local/sbin.

If it is just for you and your use (say a family shared computer, and  you just use that for work-at-home), then the logical place to put that  would be in ~/.local/bin...

Either way, what they need it to do it to execute from a system call or  user commandline. For that to happen without a full path given, it needs  to be in the search path. To check for how that is set up on your  computer for Vendor and user scripts, do this:
```

printenv | grep -e '^PATH' | grep 'local'

```
Here is an example on my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ printenv | grep -e '^PATH' | grep 'local'
PATH=/usr/[COLOR=#ff0000]local[/COLOR]/cuda-12.0/bin:/home/mafoelffen/Scripts:/home/mafoelffen/.[COLOR=#ff0000]local[/COLOR]/bin:/home/mafoelffen/Scripts:/home/mafoelffen/.[COLOR=#ff0000]local[/COLOR]/bin:/usr/[COLOR=#ff0000]local[/COLOR]/sbin:/usr/[COLOR=#ff0000]local[/COLOR]/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/[COLOR=#ff0000]local[/COLOR]/games:/snap/bin:/usr/[COLOR=#ff0000]local[/COLOR]/go/bin:/usr/[COLOR=#ff0000]local[/COLOR]/go/bin

```

---

### Post by TheFu on 2024-05-27
MAFoElffen, Or he could just **echo $PATH** to see the value.  K.I.S.S. I know, seem odd coming from me. ;)  I'm trying to be simple, when that is possible and still accurate.

---

### Post by Doug S on 2024-05-28
> **MAFoElffen said:**
> 
... To see where they had it installed to, then move the new script there to overwrite the old one...I would suggest to make a copy of the old script first, just in case you want to undo changes later.

---

