---
title: "Black screen &amp; mouse pointer after logon"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by caryb on 2009-07-02
As the title says for the last 48 hours I have only a black screen & mouse pointer, I have tried alternative drivers NV & Vesa they give me the black bubble screen & nothing else. I have tried to alt +F2 to bring up a task manager but I get a slight flicker of the hard drive & nothing else.

System Kubuntu 64 current patches Graphics card Nvidia 140 mobile chipset.

Another disturbing thing I have found is that if I boot to recovery mode the resolv.conf does not get populated & I get a drive mount error? I have to boot normally & ctl + alt + F1 to a console to do updates.

Ok Kubuntu users am I on my own with this one? Are there any thoughts of what I can do to remedy this issue? rebuilding is a possibility but I find that a sort of defietest Microsoft mentality to fixing problems.


Cary

---

### Post by franz007 on 2009-07-30
Hello 

I have just installed the kubuntu karmic alpha 3 and after fetching the newest upgrades I have the very same problem.

My hardware is a Samsung NC10 Netbook

---

### Post by dino99 on 2009-07-30
i'm with gnome & at start up, 2 black lines crossed the mid-screen, sometimes thin sometimes not, but it's not not a problem as the lines desappeard then. That comes 2 days ago & dont know what upgrade can be pointed.

---

### Post by Tim 3255 on 2009-07-30
I have the the same deal in a Thinkpad X41. 
Beta 3 loaded onto the regular hard drive gives me the black screen with cursor syndrome on re-boot, after activating my wireless and bluetooth plus all updates. 
I re-installed the from the CD and I'm going through the updates one by one to see where the problem is.
So far I have the CD install (only) which is fine. Install with wireless activated also fine. Install with bluetooth also fine.
I'll do the updates tonight.
Tim S

---

### Post by dentaku65 on 2009-07-30
> **dino99 said:**
> i'm with gnome & at start up, 2 black lines crossed the mid-screen, sometimes thin sometimes not, but it's not not a problem as the lines desappeard then. That comes 2 days ago & dont know what upgrade can be pointed.

+1 here

---

### Post by ronacc on 2009-07-30
> **dino99 said:**
> i'm with gnome & at start up, 2 black lines crossed the mid-screen, sometimes thin sometimes not, but it's not not a problem as the lines desappeard then. That comes 2 days ago & dont know what upgrade can be pointed.

I've got that also , it looks like the login box dosent completly disapear when the desktop loads and the top and bottom borders persist for a while .

---

### Post by BCurtisWX on 2009-07-30
File a bug, but make sure someone hasn't done so already.

---

### Post by Tim 3255 on 2009-07-30
After a few hours of testing I've narrowed the black screen/cursor problem to one of the update files. The file or files are between kde-zeroconfig and libxaw7. I updated repository files in groups then rebooted; the screen turned black after the above grouping was installed.
I'm currently reinstalling the Beta and will narrow it down further. 
Got it..... Libkdecorations4. Now I have to reinstall again then put in every update except this one and see what happens.
Unfortunately Libkdecorations4 must be attached to another file because it updates even when unchecked!
Tim S

---

### Post by sweetsinse on 2009-08-05
i get the black screen also on a IBM t43 laptop.

alpha 3 works fine, then after 150mb of updates i either get the black screen or the grey login background with no desktop.  i can still alt+f2 and launch stuff/etc but the actual desktop doesn't load.

sucks as this is my first time trying KDE again after many years; i used to loathe it for performance reasons -- used to run xfce/fluxbox -- but i like my friends computer at work, looks sharp and i like the completeness.

hopefully just a bug, as i realize its still alpha, but i couldn't get nm-applet/network-manager to connect to WPA either; works perfectly on karmic ubuntu/gnome.

---

### Post by caryb on 2009-08-06
the fix is to reinstall kubuntu-desktop it gets uninstalled in some cases during the upgrade.


Cary

ctl + alt + F1
logon as self
```
sudo apt-get install kubuntu-desktop
```
reboot

---

### Post by taavikko on 2009-08-06
> **caryb said:**
> the fix is to reinstall kubuntu-desktop it gets uninstalled in some cases during the upgrade.


It doesn't get uninstalled by accident, you have to give the green light.
If we learned something in here, don't do partial upgrades.

If you just had to reinstall kubuntu-desktop, did it bring any other packages with it?

---

### Post by caryb on 2009-08-06
> **taavikko said:**
> It doesn't get uninstalled by accident, you have to give the green light.
If we learned something in here, don't do partial upgrades.

If you just had to reinstall kubuntu-desktop, did it bring any other packages with it?

I want going to be so harsh, I did fall for this trap as well it's hard to tell if a package has been obsoleted or is not compiled yet.


Cary

---

### Post by taavikko on 2009-08-06
> **caryb said:**
> I want going to be so harsh, I did fall for this trap as well it's hard to tell if a package has been obsoleted or is not compiled yet.


Cary

Yep, it is sometimes pretty hard to tell the difference, but then abort the upgrade and check the changelogs, "aptitude changelog <package>" or via launchpad
to see, it almost always states what the issue is.

[http://launchpad.net/ubuntu/karmic/+queue](http://launchpad.net/ubuntu/karmic/+queue) you can check the state of packages.
repositories are synced once in a hour period.

---

### Post by caryb on 2009-08-06
Or jump in feet 1st & see what breaks! I now know what kubuntu-desktop does:P

---

### Post by taavikko on 2009-08-06
> **caryb said:**
> Or jump in feet 1st & see what breaks! I now know what kubuntu-desktop does:P

I prefer head first, so it will break the neck ;)

Yep, pretty much what every metapackage.

---

### Post by Tim 3255 on 2009-08-11
Unfortunately re-installing the desktop does nothing, so I'm passing on the updates. Hopefully it will get sorted out in the next Beta.
Tim S

---

### Post by jerrylamos on 2009-08-11
On latest "updates" IBM Thinkpad R31 intel i830 video hangs after login, brown screen & mouse pointer.  

Workaround: install karmic A2 and DON'T UPDATE!.

Yes, on the A3 boot I've got the latest PPA blue intel driver installed and it still hangs.

This IBM ThinkCentre intel i845 video hangs brown screen & mouse pointer as well with KMS modeset=1.

Workaround: set nomodeset in grub.cfg and driver "vesa".

My two pc's with ATI Radeon will boot KMS modeset=1, but video graphics performance is half speed as measured by GtkPerf from Synaptic.

Workaround: set nomodeset in grub.cfg.

Of all four, one won't boot on A3 at all, one will only with ancient video driver vesa, two will boot as ubuntu developers intend but with a big video performance drop compared to jaunty.

Hmmm.  A4 coming out soon?

Jerry

p.s. yes there are launchpad bugs on these issues.

---

