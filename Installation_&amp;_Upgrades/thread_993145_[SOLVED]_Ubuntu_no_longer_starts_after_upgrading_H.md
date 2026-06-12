---
title: "[SOLVED] Ubuntu no longer starts after upgrading Hardy to Intrepid"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by SDL on 2008-11-25
Hi.

I've just uninstalled Hardy and installed Intrepid. Now I cannot get past the login screen when the PC boots.

To complicate matters, Intrepid was working after running ```
sudo-upgrade
``` from Hardy but I wanted to clean out my junk so I installed Intrepid from disk over my Hardy install. Also the live CD was working - I don't know if it still does but I assume it is. Windows XP which is on a different partition of the same HDD is working fine.

Ever since I've been using Ubuntu - I think that I've used the five most recent versions - I have had to boot with the line ```
acpi=off
```. If I don't boot with this, my PC freezes just before the login screen - this is true of Intrepid too.

The new problem is that I get to the login screen and I cannot move the mouse or enter any keystrokes but the cursor continues to flash in the 'login' box. Does anyone have any ideas as to how I can resolve this problem please?

My initial thoughts are that the PC is either hanging at the login screen or perhaps there is some problem with the mouse and keyboard setup in my Intrepid install?

Thanks for your ideas.

Stephen.

---

### Post by lukjad on 2008-11-25
First, do you have all your data backed up?
Second, can you run the Inrepid Ibex as a Live CD and tell us if everything works? Also, you may wish to check out the CD integrity.

---

### Post by manishtech on 2008-11-25
Along with
**acpi=off**
also add[I]
**pnpbios=off**[/I]

and then try. This should work

---

### Post by SDL on 2008-11-25
Hi. Thanks for your replies.

All of my data is backed up and the Live CD still works fine.

pnpbios=off and acpi=off together didn't have any extra benefit over acpi=off. There is definitely a benefit in using acpi=off on its own so I wonder if my problem is unrelated to needing to use acpi=off?

I'm beginning to wonder whether it might be resolved if I install the nvidia drivers for my graphics card and the Broadcomm drivers for my wireless card. I generally choose to do these things shortly after installing Ubuntu anyway but they've not prevented me logging-in successfully in the past, so maybe I'm barking up the wrong tree! Not quite sure how to do this without a GUI but I'll give it a go.

Any more ideas please?

Stephen.

---

### Post by manishtech on 2008-11-26
Install Broadcom drivers as told here
[http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/](http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/)
[http://djkaos.wordpress.com/2008/10/31/fixing-broadcom-80211-linux-sta-driver/](http://djkaos.wordpress.com/2008/10/31/fixing-broadcom-80211-linux-sta-driver/)
[http://djkaos.wordpress.com/2008/11/02/running-wifi-on-ubuntu-810-hp-6515b/](http://djkaos.wordpress.com/2008/11/02/running-wifi-on-ubuntu-810-hp-6515b/)
The last one is specific to HP6515b laptop, but it can surely give you an idea how to do such.

**BTW What's the model number of your Laptop?**

---

### Post by SDL on 2008-11-26
I thought I'd try and fix Intrepid by reinstalling it again. Seems to work now, I'm not sure why but if it works that's fine by me!

Thanks for the information on the Broadcomm drivers, that's my next step. Incidentally, I don't have a laptop, I'm using a desktop that I cobbled together a few years back.

---

