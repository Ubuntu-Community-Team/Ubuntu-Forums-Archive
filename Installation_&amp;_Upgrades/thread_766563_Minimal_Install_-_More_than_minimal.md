---
title: "Minimal Install - More than minimal"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by gatoelho on 2008-04-25
Hi All! I found the minimal install and it is really close to what I want for the install. The problem is that I have an EeePC, wich means that I'll
[need some very custom drivers to the install]("https://help.ubuntu.com/community/EeePC?highlight=%28eeepc%29#head-c52e91c6d7db8d9dfce3d5d09b5d60a66a0e81b1").

So, I want to know how can I add this drivers to the install.

My goal is something like [this]("http://eeeos.interactivelaboratories.com/"), but ubuntu.

Thanks

---

### Post by kerry_s on 2008-04-25
debian is better, you should just go with that since the work is done.

anyways, to go it on your own, grab the alternate cd and install the command line system, that's the base with no gui, you need to build up from there.

sudo apt-get install xorg slim (pick a wm) (what ever else you want)
reboot(ctrl+alt+delete)

then follow the rest of those instructions on that other link.

---

### Post by gatoelho on 2008-04-25
Why 'debian is better'?

---

### Post by kerry_s on 2008-04-25
> **gatoelho said:**
> Why 'debian is better'?

it's smaller, faster and more stable. it's also a rolling release so you only have to install once and you can always upgrade to the latest stuff. if you use lenny repo's you'll be more up to date then the latest ubuntu. 
ubuntu is a snapshot distro it takes a snapshot of debian sid/unstable and uses that, the packages are frozen, they only give security updates, by the time it's released some things are already old and your stuck till the next release, then you start the process all over again. being built on sid/unstable from the start, your stuck with any bugs not yet worked out, so if it's not security related it won't be fixed till the next release, if they even try and fix it at all since there might be a newer version.

anyways, it's up to you, but if your starting from a base install what would you want to build on? stable or unstable

---

### Post by nielsb on 2008-04-26
> **kerry_s said:**
> debian is better, you should just go with that since the work is done.

anyways, to go it on your own, grab the alternate cd and install the command line system, that's the base with no gui, you need to build up from there.
The alternate cd you talk about; is that the Ubuntu alternate or Debian alternate? I'm asking because I've briefly looked at the Ubuntu and cannot seem to remember that there were a CLI installation option?

Niels

---

