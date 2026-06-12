---
title: "Xorg still doesn't allow driver configuration during dpkg-reconfigure"
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-07-09
This behavior is explicitly preventing me from having a complete and detailed xorg.conf!

---

### Post by RAOF on 2008-07-09
This behaviour is here to stay.  In fact, dpkg-reconfigure *may* produce an entirely empty xorg.conf sometime during the Intrepid cycle.

For what particular reason do you want a complete and detailed xorg.conf?  X is moving away from static configuration towards dynamically Doing The Right Thing(tm).  If X *isn't* doing the right thing automatically, you should probably file a bug (exceptions would be where you explicitly want behaviour different to a default which is almost-always good).

---

### Post by psyke83 on 2008-07-09
> **RAOF said:**
> For what particular reason do you want a complete and detailed xorg.conf?  X is moving away from static configuration towards dynamically Doing The Right Thing(tm).  If X *isn't* doing the right thing automatically, you should probably file a bug (exceptions would be where you explicitly want behaviour different to a default which is almost-always good).

I can't speak about the OP's reasons for wanting a detailed xorg.conf, but I find it's necessary too. The (Alps) touchpad of my laptop (Dell Inspiron 510m) is detected as a generic mouse, meaning bad acceleration and no tap-to-click. Also, there is no way to configure an Alps/Synaptics touchpad without specifying options in the xorg.conf and/or enabling the SHMConfig option manually, for example. 

What if a user has the "nvidia" driver installed (but non-functioning) and needs to use the"nv" driver to temporarily troubleshoot an issue?

Xorg hotplugging isn't perfect yet, and it's nice to have even a bare-bones xorg.conf that doesn't specify drivers, but at least has the proper sections defined if you need to specify drivers/options.

---

### Post by RAOF on 2008-07-09
> **psyke83 said:**
> I can't speak about the OP's reasons for wanting a detailed xorg.conf, but I find it's necessary too. The (Alps) touchpad of my laptop (Dell Inspiron 510m) is detected as a generic mouse, meaning bad acceleration and no tap-to-click. Also, there is no way to configure an Alps/Synaptics touchpad without specifying options in the xorg.conf and/or enabling the SHMConfig option manually, for example. 

Right.  So, those are (at least) two bugs.  Are they filed? :)

If I remember correctly, it was intended for the synaptics driver, at least, to be patched to be configurable without SHMConfig.  I don't believe this happened for Hardy (but I think it is in Fedora 9).

> **psyke83 said:**
> 
What if a user has the "nvidia" driver installed (but non-functioning) and needs to use the"nv" driver to temporarily troubleshoot an issue?

The proprietary drivers are one major exception here; they still require an xorg.conf explicitly enabling them, so this particular use-case is covered at the moment (and doesn't seem likely to go away soon).  On the other hand, wouldn't it be nice if a non-functional nvidia driver resulted in X automatically trying a sequence of appropriate drivers (eg: nvidia -> nv -> vesa)?  This seems like a better solution to be aiming for.  We're certainly not there yet, though.

> **psyke83 said:**
> 
Xorg hotplugging isn't perfect yet, and it's nice to have even a bare-bones xorg.conf that doesn't specify drivers, but at least has the proper sections defined if you need to specify drivers/options.

Indeed.  Xorg hotplugging isn't perfect yet, and "absolutely no xorg.conf" is only likely to happen if the hotplug is sufficiently good.  Filing bugs where the auto-detect/hotplug *isn't* sufficiently good will influence this decision!

I'm not suggesting that Intrepid will leave everyone who needs to tweak their xorg.conf out in the cold.  Merely that the direction everything is moving is towards reducing the number of people who need to tweak their xorg.conf :).  As such, people shouldn't expect to find their xorg.conf's ballooning with options - it'll be going the other way, if at all.  Particularly, this thread is titled **Xorg still doesn't allow driver configuration during dpkg-reconfigure** - I'm saying that the "still" is misleading, in that it pre-supposes that driver configuration will be re-added at some point.  I don't believe this is so.

---

### Post by ronacc on 2008-07-09
I agree completley with psyke83 , as long as xorg cannot provide correct configuration for ALL hardware ( an impossibility) an xorg.conf will be necessary for some users/installs .especialy for the scenario he presents of a failure where it is necessary or desireable to call a fallback driver other than vesa .

---

### Post by plun on 2008-07-10
Well... a tty solution is nothing for the future.

Also strange commands for reaching a config...:)


I read Ubuntus X wiki and Mr Harrington has pointed out this.

[https://wiki.ubuntu.com/X/Projects](https://wiki.ubuntu.com/X/Projects)

"GUI xorg.conf editor. Allow turning on/off available Options, setting Virtual, configuring InputDevices. Probably should hook this in as an 'Advanced' tab from Screen Resolution. (C) "

But....howto handle it for the first start...:confused:


Everything about Ubuntus X work
[https://wiki.ubuntu.com/X/](https://wiki.ubuntu.com/X/)


(Cannot find any blueprint for x-related stuff)
[https://blueprints.launchpad.net/ubuntu/intrepid](https://blueprints.launchpad.net/ubuntu/intrepid)


More devs  ??...:)

---

### Post by PmDematagoda on 2008-07-10
> **RAOF said:**
> If I remember correctly, it was intended for the synaptics driver, at least, to be patched to be configurable without SHMConfig.  I don't believe this happened for Hardy (but I think it is in Fedora 9).

I don't think that has come to Fedora 9 yet since that issue still remains, but on my laptop it seems that the minimal xorg.conf is more a blessing than a curse.

---

### Post by BwackNinja on 2008-07-10
While having an empty-looking xorg.conf would be ideal, I think that the xorg hotplugging isn't moving as fast as things are being removed from xorg.conf. Thing have gotten better, I went from a 1024x768 to 1280x768 by default from feisty to gutsy, but I still needed a modeline to get 1360x768. The way its looking here is that I wouldn't even know where to put it.

I think that a gui xorg.conf editor and perhaps a cli one too for those (X-less-ly) bad situations would be ideal. And a skeletal xorg.conf would be nice too, where some stuff can be configured manually if necessary, just showing sections to put stuff, while everything that doesn't need to be configured manually is hidden.

Until everything can be (auto)configured elsewhere, xorg.conf should be here to stay. There will always be a special place in my heart for dpkg-reconfigure xserver-xorg, it has gotten me out of a lot of situations without X (mostly my fault).

Also, I guess this means I have to file a bug about my screen resolution not quite being detected properly. What should I file it against?

---

### Post by billstei on 2008-07-10
I noticed that a few days ago that VirtualBox will no longer install the video drivers via the VBox Guest Additions into Intrepid clients giving the message:

Detected Xorg 1.5 RCx, refusing to install the Xorg modules.

Is this essentially the same problem/situation as the blank xorg.conf issue described above?

Bill

---

### Post by Starks on 2008-07-10
I'm rather pissed that I can't disable tap-to-click on my touchpad. <_<

---

### Post by RAOF on 2008-07-11
> **billstei said:**
> I noticed that a few days ago that VirtualBox will no longer install the video drivers via the VBox Guest Additions into Intrepid clients giving the message:

Detected Xorg 1.5 RCx, refusing to install the Xorg modules.

Is this essentially the same problem/situation as the blank xorg.conf issue described above?

Bill

No.  This problem is that the video drivner ABI changed in Xorg 1.5, so the VirtualBox additions won't work.

---

### Post by Starks on 2008-07-11
My problem with Xorg 1.4 and above is two-fold.

1. Intel modesetting is all messed up.

2. Synaptic touchpad support sucks!

---

### Post by Gina on 2008-07-11
My synaptic touchpad works fine - in both Hardy and Intrepid.

---

### Post by PmDematagoda on 2008-07-11
> **Gina said:**
> My synaptic touchpad works fine - in both Hardy and Intrepid.

Is this after the recent X updates or before? I believe that X in intrepid before the update was 1.4, the recent update installs X version 1.4.99(and so on) which is the X-server which people have trouble with concerning Synaptic touchpads.

---

