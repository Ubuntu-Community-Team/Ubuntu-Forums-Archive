---
title: "Enabling wireless on startup?"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macvr on 2009-07-28
Currently in Karmic, the wireless works fine , But i have to enable wireless at each startup by using the killswitch.

**Is there a way to auto-enable wireless on every startup?**

So far i have tried adding the new $rfkill command [rfkill unblock wifi]to the rc.local , but it doesnt seem to take effect.

Also adding options to the /etc/modprobe.d/ does not take effect. [this was where i had the options set in intrepid ,which in Jaunty was auto-migrated to elsewhere,i'm not sure where.]

I'm using iwl3945 , acer-wireless 

$ rfkill list
0: acer-wireless: Wireless LAN
1: acer-bluetooth: Bluetooth
2: phy0: Wireless LAN

---

### Post by buzzmandt on 2009-07-28
I also have acer

If you have atheros wifi you should have a look at this:
[https://bugs.launchpad.net/bugs/395565](https://bugs.launchpad.net/bugs/395565)

---

### Post by jfernyhough on 2009-07-28
Don't panic. I've had the exact same problem ever since .31 and I'm assuming it's a bug in the kernel driver which is likely setting the wrong default state. The Intel stack (iwl...) is widely-used so I'd expect it to be fixed in rc5 or rc6.

At least it's better than before where I had to do a
$ sudo rmmod iwlagn
$ sudo modprobe iwlagn
just to get wireless up!

---

### Post by macvr on 2009-07-28
> **buzzmandt said:**
> I also have acer

If you have atheros wifi you should have a look at this
Nope , its 
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection

> **jfernyhough said:**
> 
At least it's better than before where I had to do a
$ sudo rmmod iwlagn
$ sudo modprobe iwlagn
just to get wireless up!

hehe... i used to do > sudo rmmod iwl3945; sudo modprobe iwl3945

But, yeah .... the wireless is so much better, the killswitch works great , just doesnt remember the previous session state.

---

### Post by macvr on 2009-08-04
This seems fixed in Kernel > [2.6.31-5-generic] , 
But could someone tell, where these settings are set now ?

---

