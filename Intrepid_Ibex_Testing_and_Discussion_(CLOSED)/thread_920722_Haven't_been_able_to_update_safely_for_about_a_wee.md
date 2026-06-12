---
title: "Haven't been able to update safely for about a week"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Playa1313 on 2008-09-15
As usual with development distributions, you will be warned about partial upgrades and to wait until that warning goes away before upgrading.

Just for your information, my Intrepid 36-bit is clean, I haven't really installed or uninstalled many programs.

Well, for the past week, or at least 5 days, I haven't been able to upgrade because several packages are deselected and are causing the updater to display that partial upgrade window.  I now have 125 updates waiting to be installed as of this morning.

The packages currently unable to be selected:

Firefox
Firefox-3.0
Firefox-3.0-gnome-support
Gnome-applets
Gnome-control-center
Gnome-settings-daemon
Libdirectfb-1.0-0
Libgnome-window-settings1
Libgnomekbd-common
[B]Linux-generic
Linux-headers-generic
Linux-image-generic
Linux-restricted-modules-generic[/B]
Smartpm-core
**Xorg**

These are such major packages that it makes me afraid to do a partial upgrade even when its ok to do them on certain occasions.

Does anyone have any suggestions or is having this problem also?

---

### Post by autocrosser on 2008-09-15
You might take a look with Synaptic to see if it's just a simple remove/add issue--And as always--think before you tic "OK"

I've had several of those as everyone else has--took the time & went thru them without problems--the "normal" nVidia upgrade stuff of course, but with the proper setup--no problems.....

---

### Post by cariboo on 2008-09-15
Try in a terminal:

```
sudo aptitude safe-upgrade
```

Jim

---

### Post by Playa1313 on 2008-09-15
> **autocrosser said:**
> You might take a look with Synaptic to see if it's just a simple remove/add issue--And as always--think before you tic "OK"

I've had several of those as everyone else has--took the time & went thru them without problems--the "normal" nVidia upgrade stuff of course, but with the proper setup--no problems.....
ah, yes! I see.

I went to synaptic, marked all the upgrades and it told me libgnomekbd2 and libgnomekbdui2 would be removed, but newly installed would be libgnomekbd3 and libgnomekbdui3.  There were no other issues, so I will go ahead and do that.  

Thank you.

---

### Post by gjoellee on 2008-09-15
I have not had any problem with the parial updates, but I am making sure if anything important doesn't get deleted

---

### Post by sdowney717 on 2008-09-24
partial updates means some packages cant be updated, due to unmet dependencies, but most can be updated.

So eventually when the devs get the packages fixed up and released, the partial updates problem will vanish. At least this has happened to me on all my other os ubuntu upgrades.

---

### Post by jerrylamos on 2008-09-25
> **sdowney717 said:**
> partial updates means some packages cant be updated, due to unmet dependencies, but most can be updated.

So eventually when the devs get the packages fixed up and released, the partial updates problem will vanish. At least this has happened to me on all my other os ubuntu upgrades.

Not with Intrepid!  On my laptop IBM Thinkpad and on my desktop Compaq Presario partial updates killed the Intrepid installs.  On both however I did have dual boot with an un-updated install so they are still running Intrepid.

With Feisty, Gutsy, Hardy I didn't have trouble with partial upgrades.  Just Intrepid....

Jerry

---

