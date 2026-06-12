---
title: "Moving from Gentoo"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by Cossins on 2005-02-27
Hi there!
I'm a long time Gentoo user (veteran on the forums and everything ;)), but Gentoo has just fried the second hard disk for me (emerge sync every day and heavy compilation tears down the poor bastards). So after trying the 4.10 LiveCD that I got from a friend, I decided to give Ubuntu a go.

So I wanted to know, as I expect here are other converts, what should I be aware of? Any classic Gentoo-user pitfalls that I might fall into?

Another thing that concerns us (me and Smeagol) is the following:
I noticed that the LiveCD (apparently) ran XFree86. Months with Xorg 6.8 on Gentoo has made me very reluctant to want to take such a huge step backwards - I've grown fond of composite, fixes and damage, and the general spiffyness of Xorg compared to XFree86. And how does Xorg (supposing it is possible to get) play with NVIDIA drivers?

Thanks.

- Simon

---

### Post by Leif on 2005-02-28
I don't want to dampen your enthusiasm to try out ubuntu, but if you're having regular harddrive failures, it's unlikely to be due to gentoo. If they were relatively new, I'd check the PSU ratings, or for faults with the harddrives themselves.

---

### Post by Cossins on 2005-03-01
[QUOTE=Leif]I don't want to dampen your enthusiasm to try out ubuntu, but if you're having regular harddrive failures, it's unlikely to be due to gentoo. If they were relatively new, I'd check the PSU ratings, or for faults with the harddrives themselves.[/QUOTE]
 Well, the harddrive failures isn't the only reason I want to try Ubuntu, I'm also getting tired of compiling all the time. :)

The harddrive in question is 2 years old. The problem is bad sectors.

- Simon

---

### Post by p!=f on 2005-03-01
> **Cossins]Hi there!
I'm a long time Gentoo user (veteran on the forums and everything  said:**
> 
Hi and be welcomed.
[QUOTE=Cossins]
So I wanted to know, as I expect here are other converts, what should I be aware of? Any classic Gentoo-user pitfalls that I might fall into?

For package management:
man apt-get
man apt-cache
man dpkg
synaptic (in GUI)

Ubuntu does not use root. Use sudo instead.
To get a root prompt
```

sudo -s

```
[QUOTE=Cossins]
Another thing that concerns us (me and Smeagol) is the following:
I noticed that the LiveCD (apparently) ran XFree86. Months with Xorg 6.8 on Gentoo has made me very reluctant to want to take such a huge step backwards - I've grown fond of composite, fixes and damage, and the general spiffyness of Xorg compared to XFree86. And how does Xorg (supposing it is possible to get) play with NVIDIA drivers?

Thanks.

- Simon[/QUOTE]
Yes. Ubuntu Warty (current stable release) still uses heavily patched XFree86. 
If you want Xorg dist-upgrade to Hoary (current development branch). It uses 6.8.2.
I have FX5200 on AGP bus, works like a charm. I'm still missing my old trusty twice as fast compared to FX5200 Titanium 4200. ;)
```

[~] > dpkg -l nvidia-glx
ii  nvidia-glx                    1.0.6629-0ubuntu21            NVIDIA binary XFree86 4.x/X.Org driver

```
I'm on Hoary so I'm not sure what version stable uses.
Feel free to ask and have good times with Ubuntu.

BTW: Something for a little nostalgy. Guess what apt-build world does. ;)

---

### Post by Cossins on 2005-03-02
[QUOTE=p!=f]BTW: Something for a little nostalgy. Guess what apt-build world does. ;)[/QUOTE]
:D

Guess what, in the true Gentoo'er spirit I already dist-upgraded to Hoary. It did b0rk the ALSA init script (solutions?), but apart from that is working fine.

I hear Warty is prelinked by default, is the same true for Hoary? (is it true at all?) The Desktop does seem a little more sloppy, and although I have the right nvidia driver installed and RenderAccel On, the Xorg process uses an awful lot of processing power when widgets are redrawing... :roll:

- Simon

---

### Post by Joeb on 2005-03-02
*I hear Warty is prelinked by default, is the same true for Hoary? (is it true at all?)*

I don't think Warty is pre-linked.  If I recall, I had to apt-get the prelink package.  Then, after that, I had to edit the script to actually turn it on.  Worked like a charm after that.

I'm not sure about Hoary, either, although with all the updates going in, it might be counter-productive to pre-link it.

As for moving from Gentoo, I did a little time with it, but it got a little old compiling all the time.  Coming from a previous KDE based distro, it's taken a little time to get used to Gnome, but for the most part, I like it (when I'm not running XFCE). 

A lot of people argue about this distro or that, but from a technical perspective, you can pretty much install anything on any distro.  The biggest plusses that Ubuntu has, in my opinion, is the overall philosophy and the community.

I can't say enough about the community!  Rarely will you see other distros bashed and people will very quickly try and help others out.  Periodically, you'll even see non-Ubuntu questions answered as cordially as if they were Ubuntu related.

Anyway, welcome aboard.  Ubuntu does a few things different, out of the box, than Gentoo (particularly, no root account, but sudo is your friend), but for most of these, you can change.  

Joeb

---

### Post by nocturn on 2005-03-02
[QUOTE=Cossins]:D

Guess what, in the true Gentoo'er spirit I already dist-upgraded to Hoary. It did b0rk the ALSA init script (solutions?), but apart from that is working fine.

I hear Warty is prelinked by default, is the same true for Hoary? (is it true at all?) The Desktop does seem a little more sloppy, and although I have the right nvidia driver installed and RenderAccel On, the Xorg process uses an awful lot of processing power when widgets are redrawing... :roll:

- Simon[/QUOTE]

Welcome Simon

One of the major pitfalls is what to do with all the time you used to spend compiling ;-)

Warty is not prelinked and AFAIK Hoary isn't either.

About the CPU usage, have you switched to NVAgp instead of AGPGART?  That did wonders for me.

---

### Post by Marauder1 on 2005-03-02
[QUOTE=nocturn]
About the CPU usage, have you switched to NVAgp instead of AGPGART?  That did wonders for me.[/QUOTE]

Sorry about that but ....
What is NvAgp and what does it do ?
I have a GF3 ti-200 and my performances are decent.
Would it help to have better one ?

Thanks

---

### Post by Cossins on 2005-03-02
I don't use NvAGP, since the AGPGART module is loaded by default. I'm not sure how to properly disable this. Should I add agpgart to /etc/hotplug/blacklist?

- Simon

---

### Post by p!=f on 2005-03-02
[QUOTE=Cossins]I don't use NvAGP, since the AGPGART module is loaded by default. I'm not sure how to properly disable this. Should I add agpgart to /etc/hotplug/blacklist?

- Simon[/QUOTE]
It never worked for me. I preferably compile a custom kernel with the Nitro / CKO patchset without AGPGART support at all and set NvAGP to 1 (use internal Nvidia AGP). With this setup I always get better graphic performance. I should mention I use VIA chipset.
Or you could try dirty way, rename agpgart module in /lib/modules/`uname -r`/kernel/drivers/char/agp/agpgart.ko ;)

---

### Post by p!=f on 2005-03-02
[QUOTE=Cossins]
I hear Warty is prelinked by default, is the same true for Hoary? (is it true at all?) The Desktop does seem a little more sloppy, and although I have the right nvidia driver installed and RenderAccel On, the Xorg process uses an awful lot of processing power when widgets are redrawing... :roll:
- Simon[/QUOTE]
```

sudo apt-get install prelink readahead

```

Prelink:
[http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80](http://www.ubuntuforums.org/showpost.php?p=9864&postcount=80)

Yeah. I've found Hoary slower on the desktop side compared to Warty but with comming updates I feel it's getting better and better. Updating xorg to 6.8.2-2 right now. :)

---

