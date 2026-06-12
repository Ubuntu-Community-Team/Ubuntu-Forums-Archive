---
title: "Variant Hopping"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by scoon on 2014-09-24
Hey there, 

I am currently running kubuntu and I'd like to give unity a try.  I've never run it before and thought it would be interesting to try out.  If I install ubuntu-desktop and remove kubuntu-desktop and dependencies, will that be the same as if I had just installed ubuntu from dvd?

Thanks, 

Skip

---

### Post by sudodus on 2014-09-24
It is very hard to remove all software, that was bundled with the previous desktop environment (without breaking something). You can try and have a system with several desktop environments available at the log in screen, but it will get bloated with doublet application programs, and there might be conflicts. I have such a system with the desktops of Lubuntu, Xubuntu and Kubuntu added to an original standard Ubuntu system, but I do not recommend it for your standard production system.

Make a clean installation instead. If you keep your personal files in a ***data*** partition, each operating system's root partition will be rather small and easy to manage (update/upgrade, backup etc).

---

### Post by Dennis N on 2014-09-24
kubuntu-desktop is a metapackage which is used to install packages as dependencies. It is more like a shopping list. Removing it does not remove the items on the list. You would have to specifically remove any installed packages you don't want (and don't effect the operation of your system).

To see what would happen when installing ubuntu-desktop, you can simulate the install with:

```
apt-get install -s ubuntu-desktop
```

note there is no sudo used with this.

(on my system, 435 new packages would be installed)

I believe you could try just the unity desktop environment (DE) by installing **unity**.

(on my system, a simulation shows 196 new packages would be installed by unity)

**Either of these options is very difficult to reverse!**

Personally, If I were interested in trying out Ubuntu and Unity, I would do it by installing Ubuntu in a virtual machine, or doing a dual-boot setup. Either of these would be easy to remove and my original Kubuntu is still there intact and as it was.

---

### Post by oldfred on 2014-09-24
One more vote for a clean install. 

I once installed Kubuntu into my Ubuntu and never was able to fully remove it. Complicating it even more I like a couple of k apps like K3b and Kmymoney which pull in many dependencies. I later had to just to a new clean install to fix things.

I now install experiments in another 20 or 25GB partition, so my working install is not changed. If just trying out you probably only need 10 to 15GB. But you do have to keep track of which install controls MBR and is default boot. I have not used a VM but if you have the hardware to support that, then it is a good alternative also.

---

### Post by tgalati4 on 2014-09-24
It will work exactly as you expect.  A removal of KDE and a installation of Unity will take about 10 minutes and it will look and feel like a new computer.

Or

It may not and you will have strange behavior and search the forums for answers but never know what exactly is causing the problem.

So although I agree that a clean installation is best, give the "easy" way a try and let us know if it works--exactly as you expect.

---

### Post by scoon on 2014-09-24
Hey there, 

It worked almost as easy as I thought it would.  I did take a couple of precautions.  The first was to do this on TTY1 and the second was to plug into my router and not use wifi.  After that, the only stumbling block I had was with lightdm looking for a kdm greeter instead of the the unity one.  As a result, lightdm wouldn't start.  To resolve, I (re)moved /etc/lightdm out of /etc and re-installed lightdm.

To clean up orphaned debs, I used ```
apt-get remove --purge `deborphan`
```  

Thanks for all the input.

Skip

---

