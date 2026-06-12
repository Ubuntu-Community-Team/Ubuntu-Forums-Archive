---
title: "Updates mean I can't boot ubuntu. Help!?"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Owen.C93 on 2010-03-03
I just installed some updates to ubuntu and now I can boot at all, or at least reach GDM.

I think it's a driver problem but I can't get into ububtu to change it. Is there anyway I can get in? I tried the recovery mode option but I'm not sure how to use it. And the blank screen I get cannot be passed by alt+f2 or ctrl+f12.

Any help would be greatly appreciated. I'm currently using the live CD but that doesn't mean I can acsess my documents :L

---

### Post by philinux on 2010-03-03
What graphics card have you got?

---

### Post by handaxe on 2010-03-03
You should be able to access your hard drive from the liveCD...

At the blank screen after a normal boot, can you ctrl-alt F1 ie get a terminal?  If you can, try ```
sudo restart gdm
```

I had something like this, but gdm restarted and presented the login screen

HA

---

### Post by Owen.C93 on 2010-03-03
Nvidia 6400 gs I think. I can acsess it now, I was being stupid and looking in the wrong place.


And I'll try restarting GDM brb.

---

### Post by Owen.C93 on 2010-03-03
Nope I can't do that. I can boot into recovery mode and type alt+f2, restart gdm does nothing, but just running GDM continues boot but then it freezes again. Is there anyway of fixing this or is a clean install in order?

All I did was update drivers and used the xorg one.

---

### Post by philinux on 2010-03-03
> **Owen.C93 said:**
> Nope I can't do that. I can boot into recovery mode and type alt+f2, restart gdm does nothing, but just running GDM continues boot but then it freezes again. Is there anyway of fixing this or is a clean install in order?

All I did was update drivers and used the xorg one.

When gdm freezes try this.

Alt+SysRq+k

Then try logging in again.

If you activated nvidia-current you could uninstall it from recovery.

---

### Post by handaxe on 2010-03-03
and keep in mind ```
sudo dpkg-reconfigure xserver-xorg
``` from recovery as another option....

If you have a bad update and have networking in recovery one can wait until a fixed package becomes available and sudo apt-get update && sudo aptitude safe-upgrade" to install it and other upgrades. A full re-install should not be necessary.

More specific to Xorg steps are:

```
sudo apt-get remove --purge xserver-xorg
```(entirely removes existing xorg)

```
sudo apt-get install xserver-xorg
```(installs a clean xorg)

```
sudo dpkg-reconfigure xserver-xorg
```(reconfigures Xorg)

hope this helps,

HA

---

### Post by Owen.C93 on 2010-03-03
I tried alt+sysrq+k but no luck.

Could you tell me how to uninstall or change the default driver please? Recovery mode just puts me in a terminal. With a few other options.

Thanks for all the help so far.

---

### Post by philinux on 2010-03-03
> **Owen.C93 said:**
> I tried alt+sysrq+k but no luck.

Could you tell me how to uninstall or change the default driver please? Recovery mode just puts me in a terminal. With a few other options.

Thanks for all the help so far.

```
sudo apt-get remove nvidia-current
```

You can reinstall it later.

---

### Post by nperry on 2010-03-03
I'm having exactly same problems as described. I'm unable to boot into recovery, all i can see if three lines. dark blue, light blue and white. Dark blue and light go across the screen and white covers them over. When white is fully accross the screen nothing else happens! Going to try booting from onboard graphics.

---

### Post by philinux on 2010-03-03
> **nperry said:**
> I'm having exactly same problems as described. I'm unable to boot into recovery, all i can see if three lines. dark blue, light blue and white. Dark blue and light go across the screen and white covers them over. When white is fully accross the screen nothing else happens! Going to try booting from onboard graphics.

The "progress bar" is plymouth. [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

How about booting an older kernel.

---

### Post by nperry on 2010-03-03
> **philinux said:**
> The "progress bar" is plymouth. [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

How about booting an older kernel.
tried .14 to no avail.

---

### Post by Owen.C93 on 2010-03-03
> **nperry said:**
> I'm having exactly same problems as described. I'm unable to boot into recovery, all i can see if three lines. dark blue, light blue and white. Dark blue and light go across the screen and white covers them over. When white is fully accross the screen nothing else happens! Going to try booting from onboard graphics.
Hi, this isn't the issue that I have.

My issue is a black screen before gdm but with no way to get a terminal or anyting.

Selecting recovery mode form grub menu just gives me a terminal.

---

### Post by Owen.C93 on 2010-03-03
Reinstalled GDM, xserver xorg and it works at the moment. Only in .14 not in .15 yet.

---

