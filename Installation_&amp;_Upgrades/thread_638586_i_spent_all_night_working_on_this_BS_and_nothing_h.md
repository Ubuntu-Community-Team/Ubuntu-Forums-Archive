---
title: "i spent all night working on this BS and nothing happend."
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by shuarma on 2007-12-12
i spent ALL night working on this crap ubuntu and nothing seems to work.
from 11pm - 8am i spent trying to get this cube compiz fusion garbage to work.

first i had a problem installing the nvidia drivers.
then, people are telling me at other boards i dont need nvidia drivers, just enable it in the restricted drivers manager. so i enable it. and then install the drivers using envy.
i probably rebooted about 10-15 times tonight, and it hasn't been going my way.
i had my appearance set to extra, and for some reason, i dont have the wobbily windows anymore, just transparency.
i dont know what  the hell is going on, and i'm about to format and start all over again.

somebody PLEASE point me in the right direction.

---

### Post by LeAstrale on 2007-12-12
you ought to go to bed, and then sleep a lot. then return when rested and ready to explain properly what you have tried and what didn't work?

---

### Post by shuarma on 2007-12-12
> **astral-1 said:**
> you ought to go to bed, and then sleep a lot. then return when rested and ready to explain properly what you have tried and what didn't work?
ok, here is exactly what i did.
first, i was looking how to install beryl, then i realized it is now called compiz fusion, i searched all over the place, and figured i need nvidia drivers for my 7900GT to support these features. i download the nvidia drivers and i do not know how to install them, but then somebody told me i already have the nvidia drivers because i am using the restricted drivers manager. then, i used envy to install the proper nvidia drivers. and then all of a sudden when i reboot, i no longer have wobbily windows, but i am still on the 'extra' setting in appearance. then, i installed something called compizconfig settings manager. i click that, and they said i'm supposed to have something in System > Preferences called 'advanced desktop manager' or something like that. but i don't have it.
 i dont know whats going on, so please help.

---

### Post by dward526 on 2007-12-12
>  then, i installed something called compizconfig settings manager. i click that, and they said i'm supposed to have something in System > Preferences called 'advanced desktop manager' or something like that. but i don't have it.
 i dont know whats going on, so please help.

through synaptic, search for 'advanced desktop manager',or 'compiz' and look for 'advanced desktop settings',  it is an additional package you install in 7.10 and gives you compiz-fusion.  Now, in preferences, you will have this control, and it is a very intuitive interface.

Let us know how it works out.

---

### Post by shuarma on 2007-12-12
> **dward526 said:**
> through synaptic, search for 'advanced desktop manager',or 'compiz' and look for 'advanced desktop settings',  it is an additional package you install in 7.10 and gives you compiz-fusion.  Now, in preferences, you will have this control, and it is a very intuitive interface.

Let us know how it works out.
nothing worked out. i downloaded and installed everything. i see nothing.

---

### Post by mozetti on 2007-12-12
I think part of your problem is using multiple methods of installing the nVidia drivers.

One way is to use the Restricted Drivers Manager in Ubuntu. That will download and install the nvidia-glx-new driver for your card, and is probably the easiest (point & click) method.

A second way is to use Envy. I haven't used it, but I know it's another, separate method.

A third way is to download the linux drivers directly from nvidia and install them manually.

If I had to guess, I'd say that your problems are because you installed the restricted drivers manager version of the nVidia driver, and then used Envy to install the nVidia driver.

In most cases, to use Advanced Desktp Effect you just have install the nVidia driver using the restricted drivers manager, and then turn on the Advanced Desktop Effects. 

After you get that working, you can install the Compiz Config Settings Manager to adjust the settings and add more plugins, should you choose to do so. To install this, go to the terminal and type:```
sudo aptitude install compiz-config-settings-manager
```

---

### Post by shuarma on 2007-12-12
> **mozetti said:**
> I think part of your problem is using multiple methods of installing the nVidia drivers.

One way is to use the Restricted Drivers Manager in Ubuntu. That will download and install the nvidia-glx-new driver for your card, and is probably the easiest (point & click) method.

A second way is to use Envy. I haven't used it, but I know it's another, separate method.

A third way is to download the linux drivers directly from nvidia and install them manually.

If I had to guess, I'd say that your problems are because you installed the restricted drivers manager version of the nVidia driver, and then used Envy to install the nVidia driver.

In most cases, to use Advanced Desktp Effect you just have install the nVidia driver using the restricted drivers manager, and then turn on the Advanced Desktop Effects. 

After you get that working, you can install the Compiz Config Settings Manager to adjust the settings and add more plugins, should you choose to do so. To install this, go to the terminal and type:```
sudo aptitude install compiz-config-settings-manager
```
ok, but how do i *turn on* Advanced Desktop Effects?

---

### Post by mozetti on 2007-12-12
Go to Preferences->Appearance and the last tab is for the Advance Desktop Effects. But, as you mentioned it's already set to "Extra" and you're getting the transparency. So, that sounds like they're on but something is screwed up.

Run the command at the bottom of my previous post to install the Compiz Config Settings Manager. If you don't see a menu item under preferences menu for Advanced Desktop Effects Settings (or something like that, I forget what it's titled), then run it from the terminal using:```
ccsm
```

If it's all installed and turned on, and you still have major problems then I'm not sure what to tell you other than undoing everything you've done so far and starting over. As I mentioned above, it shouldn't take that long if you use the restricted drivers manager to install the nVidia driver and then turn on the Advanced desktop effects.

I don't know why it's taken you so long to do it, and with so many problems.

---

### Post by shuarma on 2007-12-12
> **mozetti said:**
> Go to Preferences->Appearance and the last tab is for the Advance Desktop Effects. But, as you mentioned it's already set to "Extra" and you're getting the transparency. So, that sounds like they're on but something is screwed up.

Run the command at the bottom of my previous post to install the Compiz Config Settings Manager. If you don't see a menu item under preferences menu for Advanced Desktop Effects Settings (or something like that, I forget what it's titled), then run it from the terminal using:```
ccsm
```

If it's all installed and turned on, and you still have major problems then I'm not sure what to tell you other than undoing everything you've done so far and starting over. As I mentioned above, it shouldn't take that long if you use the restricted drivers manager to install the nVidia driver and then turn on the Advanced desktop effects.

I don't know why it's taken you so long to do it, and with so many problems.
[IMG]http://i15.tinypic.com/6z79qoo.png[/IMG]

i think my best bet is just to format and do this all over again. i see it should take no longer than 5 minutes to do.

---

