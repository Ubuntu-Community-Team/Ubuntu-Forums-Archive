---
title: "Enable SHMConfig in Intrepid!?"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by emil.s on 2008-08-30
Is it possible to do that without editing xorg.conf?
Because now I doesn't have a xorg.conf at all, and I think that was the purpose with the later Xorg releases...

So can I change this with a parameter or something anywhere!? :)

---

### Post by nightfrost on 2008-09-07
I would like to know this as well.
In fact, shouldn't SHMConfig be enabled by default in intrepid?

---

### Post by wgrant on 2008-09-07
> **nightfrost said:**
> I would like to know this as well.
In fact, shouldn't SHMConfig be enabled by default in intrepid?

No. It is a massive security risk. It should never be enabled by default.

What do you want it for? Most alterations to Synaptics touchpad settings (the classic use for it) can now be performed using xinput. No security holes required.

---

### Post by nightfrost on 2008-09-07
Really? That's great news, I wasn't aware that xinput can be used to control touchpad settings. Does the mousepad setting in gnome-mouse-properties use it as well? Cause I wouldn't want to suggest to users to use xinput from the command line to enable horizontal scrolling, for example.

And, in that case, shouldn't xinput be installed by default instead?

---

### Post by wgrant on 2008-09-07
> **nightfrost said:**
> Really? That's great news, I wasn't aware that xinput can be used to control touchpad settings. Does the mousepad setting in gnome-mouse-properties use it as well? Cause I wouldn't want to suggest to users to use xinput from the command line to enable horizontal scrolling, for example.

And, in that case, shouldn't xinput be installed by default instead?

Since my changes a few days ago gnome-mouse-properties uses the same method as xinput to change settings. It doesn't expose any more options than it used to, but scrolling is there.

---

### Post by nightfrost on 2008-09-07
That's beautiful! Thanks :-)
I hope this patch ends upstream as well.

---

### Post by xerosis on 2008-09-07
What's the official way to increase the speed of the touchpad now then? The current speed is far too slow on my macbook. Also the 'Enable vertical scrolling' has no effect, is this a bug?

---

### Post by babyhuey on 2008-09-07
> **xerosis said:**
> What's the official way to increase the speed of the touchpad now then? The current speed is far too slow on my macbook. Also the 'Enable vertical scrolling' has no effect, is this a bug?

Same situation here. You'll have to resort to xorg.conf. Either use SHMConfig or manually set your parameters.

---

### Post by wgrant on 2008-09-07
Speed is a float, and the floats don't seem to be exposed via XI properties at the moment. Have you logged out and in since you last upgraded?

---

### Post by wgrant on 2008-09-07
> **babyhuey said:**
> Same situation here. You'll have to resort to xorg.conf. Either use SHMConfig or manually set your parameters.

You can also set settings through files like /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi now. You don't actually need xorg.conf.

---

### Post by xerosis on 2008-09-07
I have indeed logged out, I got the button actions as you said before but still not a reasonable default speed or vertical scroll. How will the default speed be handled for release? Will the float issue revert it to the previous behaviour or will we need to define a new default somewhere else?

---

### Post by wgrant on 2008-09-07
> **xerosis said:**
> I have indeed logged out, I got the button actions as you said before but still not a reasonable default speed or vertical scroll. How will the default speed be handled for release? Will the float issue revert it to the previous behaviour or will we need to define a new default somewhere else?

Do you perhaps have an alps touchpad? There are several bugs filed on alps touchpads being very slow; on most Synaptics touchpads it seems to be fine.

Are you sure you have no vertical scroll at all? In some cases it is just a much thinner area on the right than usual, but in others it seems to have ceased to exist.

---

### Post by babyhuey on 2008-09-07
> **fujitsu said:**
> You can also set settings through files like /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi now. You don't actually need xorg.conf.

Ah, thanks for the info!

---

### Post by xerosis on 2008-09-08
> **fujitsu said:**
> Do you perhaps have an alps touchpad? There are several bugs filed on alps touchpads being very slow; on most Synaptics touchpads it seems to be fine.

Are you sure you have no vertical scroll at all? In some cases it is just a much thinner area on the right than usual, but in others it seems to have ceased to exist.

There's definitely no scroll there, it's a macbook thought which I believe uses the appletouch driver too? It did break at the same time as the speed though so it must be related rather than a kernel problem etc.

It looks like a few people have had the same issue and incorrectly reported it here: [https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/102680](https://bugs.edge.launchpad.net/ubuntu/+source/linux-meta/+bug/102680)

---

### Post by Xehoz on 2008-10-08
> **wgrant said:**
> What do you want it for? Most alterations to Synaptics touchpad settings (the classic use for it) can now be performed using xinput. No security holes required.

Probably not in the "classic use or it" category, but is there a way to disable synaptics while typing? [syndaemon]("https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing") use to do it... but it requires shmconfig. I've already checked "xinput list-props", but no particular setting got my eye.

---

### Post by wgrant on 2008-10-08
> **Xehoz said:**
> Probably not in the "classic use or it" category, but is there a way to disable synaptics while typing? [syndaemon]("https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20the%20Touchpad%20Temporarily%20While%20Typing") use to do it... but it requires shmconfig. I've already checked "xinput list-props", but no particular setting got my eye.

Input properties don't do that sort of thing -- they just allow user apps to set driver properties, much like SHMConfig. syndaemon is where the disabling logic is implemented. I'll add a property mode to syndaemon tonight, so you can tell it to not need SHMConfig.

---

### Post by wgrant on 2008-10-09
I believe I have a complete port of syndaemon to use input device properties. Took a couple of hours, but it seems to work. Grab xserver-xorg-input-synaptics from [my PPA](https://launchpad.net/~wgrant/+archive) to try it out - complain here if you can't use it fine without enabling SHMConfig.

---

