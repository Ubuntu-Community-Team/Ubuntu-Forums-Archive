---
title: "Weird problems after todays update"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by steelaz on 2008-10-09
I was updating my system this morning (distribution update) and it got stuck on last step ("Clean Up"), I checked the terminal output and last line said "Removing nvidia-kernel-common". I waited for a while but nothing happened, so I rebooted. After reboot my windows are missing min, max, close buttons, dialog boxes are missing borders, ALT+TAB is no longer working, title bars are grey instead of ubuntu-brown.

Any ideas?

---

### Post by autocrosser on 2008-10-09
Either rerun your upgrade or run sudo apt-get update & sudo apt-upgrade. Really, you should never just reboot until you resolve problems like that......

---

### Post by StR34k on 2008-10-09
I have the same / similar problem.  I installed the updates, except update-manager hung for a while, so I killed it.  went to the term, finished the upgrades, and found when I rebooted that there was a problem starting x, since the nvidia kernel module wasn't built properly/at all... so I reinstalled the nvidia modules, which then seem to have built the modules correctly, since x started fine.  except now there is a prob with compiz, not providing window borders. (where you see the min/max/close buttons)

---

### Post by Incubuss on 2008-10-09
I experienced the same problem, the update stopped, I left it for a while before I had to shut down (laptop) and when I turned it back on no window borders in Compiz. I can get them back by turning off Compiz. 

When I try and install Compiz I get this:

> james@james-laptop:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  compiz: Depends: compiz-fusion-plugins-main (>= 0.7.8 ) but it is not going to be installed
          Depends: compiz-fusion-plugins-extra (>= 0.7.8 ) but it is not going to be installed
E: Broken packages


Not too sure what caused any of this. I'm using an integrated intel graphics card if that makes any difference.

---

### Post by plun on 2008-10-09
I filed a bug and Compiz is broken for the moment

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/280778](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/280778)


All packages where updated today to 0.7.8

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/thread.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/thread.html)

---

### Post by StR34k on 2008-10-09
Same here, but I fixed it with:

```

sudo apt-get update
sudo apt-get install compiz-gnome
```

Maybe they fixed something in the repo's since I had the prob. on 2 comps, and tried to install compiz-gnome with out updating on one of them, and it was still giving me errors....  but this still doesn't fix the package compiz. and trying to install it still gives errors, but at least I still have my pretty window effects.)

P.

---

### Post by bigken on 2008-10-09
I also have the same problem it hangs at Cleaning Up rebooted system and had to run repair xserver :confused:

---

### Post by canabal on 2008-10-09
The same happened for me, so i force quit the program and ran the updates again through the terminal and it all worked fine.

---

### Post by steelaz on 2008-10-09
> **StR34k said:**
> Same here, but I fixed it with:

```

sudo apt-get update
sudo apt-get install compiz-gnome
```

Maybe they fixed something in the repo's since I had the prob. on 2 comps, and tried to install compiz-gnome with out updating on one of them, and it was still giving me errors....  but this still doesn't fix the package compiz. and trying to install it still gives errors, but at least I still have my pretty window effects.)

P.

Thanks, that fixed it for me too.

---

### Post by tghe-retford on 2008-10-09
I've had the same problems with Compiz. It looks as if things are being updated slowly but surely. It's just compiz-fusion-plugins-extra which isn't currently able to be installed. However, the updated animations plugin in compiz-fusion-plugins-main is broken. You have to now type in the effect you want, as opposed to the much easier to use drop down menu you had previously, plus if you type in a valid animation (ie. animation:Skewer or animation:Fade), it uses the default animation instead.

---

### Post by StR34k on 2008-10-09
No Problem :)

---

### Post by jerome1232 on 2008-10-09
For me I needed compiz-fusion-plugins-main; compiz-fusion-plugins-unsupported; and I can't get compiz-fusion-plugins-extra, it complains that compiz-core is missing, it's installed and I tried reinstalling it. :(

I miss my 3d windows and cylinder.

---

