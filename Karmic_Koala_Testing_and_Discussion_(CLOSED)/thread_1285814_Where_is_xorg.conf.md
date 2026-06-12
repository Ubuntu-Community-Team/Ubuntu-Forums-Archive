---
title: "Where is xorg.conf ?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marzvix on 2009-10-08
I've installed Karmic Koala yesterday on two of my production machine.

One is a Dell Inspiron Desktop and everything worked smoothly. Except a LIC-200 LG webcam that did upside down (minor buzz). Sound, wireless keybord, desktop candies. All that is ok.

The other box, my notebook - Dell Vostro 1400 - was the same, except my Geforce 8400M GS (configure this device is allways a little bit tricky). 

In Debian, all is working pretty fine using another partition and same hardware. I know because of Nvidia logo at startup and it took me a whole day to update and tune kernel and install Nvidia native driver version 185.18.36.

My first step in configure that driver is make a backup of xorg.conf. 

Well, my issue is: I was starting install it on my new Karmic Koala and I could not realize where that file is.

Do somebody know what is going on or where the file is?

It seems there are some modification in this topic, X server changed or else. 

Anyway I could not find anything on Release Notes or something escaped from my attention. 

I'll appreciate and thanks for any directions.

---

### Post by taavikko on 2009-10-08
X will autodetect hw, so basically no need for xorg.conf.
However, if one is needed, you can create it to set extra options.

Close graphical interface (drop to vt*) and issue "sudo Xorg -configure"

---

### Post by dalonso on 2009-10-08
> **marzvix said:**
> I've installed Karmic Koala yesterday on two of my production machine.

One is a Dell Inspiron Desktop and everything worked smoothly. Except a LIC-200 LG webcam that did upside down (minor buzz). Sound, wireless keybord, desktop candies. All that is ok.

The other box, my notebook - Dell Vostro 1400 - was the same, except my Geforce 8400M GS (configure this device is allways a little bit tricky). 

In Debian, all is working pretty fine using another partition and same hardware. I know because of Nvidia logo at startup and it took me a whole day to update and tune kernel and install Nvidia native driver version 185.18.36.

My first step in configure that driver is make a backup of xorg.conf. 

Well, my issue is: I was starting install it on my new Karmic Koala and I could not realize where that file is.

Do somebody know what is going on or where the file is?

It seems there are some modification in this topic, X server changed or else. 

Anyway I could not find anything on Release Notes or something escaped from my attention. 

I'll appreciate and thanks for any directions.

With the latest Xorg release, xorg.conf is no more necessary. It should auto-configure using the information it requests from the HAL layer. It is still possibly to use the xorg.conf if you happen to have very especial requirements, but it should not be needed at all.

Regarding the nvidia propietary driver, it should be offered to you as well automatically after running your session for a while with the free nvidia driver. If this does not happen automatically, then open the restricted-drivers configuration in the Administration menu and select the recommended propietary driver. It will pull it from internet, install it for you and configure your xorg, all of this automatically.

No need to manually mess with xorg.conf

---

### Post by marzvix on 2009-10-08
Okdok.
But I could remember - in the past with Intrepid Ibex Alpha/Beta - something went wrong and I messed my xserver.

My central concern is: how to make backup of this configuration?

Ok, automagically ... But what if something pinch me in the middle of changes? My video can be distorted or in a kind of bad resolution that the config button are not acessible - it happened to me once. 

By the way there are no Restricted Drivers on my Administration menu (I can remember there is one in my old Ibex) and at least, something sonds weird because there was no offer pulling up, even when I tryied to set preferences->appearence->visuall effects. It starts a search of available drivers but at the end this option could not be set. 

In face of this weird I used to be cautious.

---

### Post by Tibuda on 2009-10-08
> **marzvix said:**
> By the way there are no Restricted Drivers on my Administration menu (I can remember there is one in my old Ibex) and at least, something sonds weird because there was no offer pulling up, even when I tryied to set preferences->appearence->visuall effects. It starts a search of available drivers but at the end this option could not be set. 
It was renamed to "Hardware Drivers". "Restricted" is not a very good name.

---

### Post by marzvix on 2009-10-08
> **danielrmt said:**
> It was renamed to "Hardware Drivers". "Restricted" is not a very good name.

Good. Everything is ok now !

Thanks all for replies !

---

### Post by emarkay on 2009-10-08
OP, this is already covered here:

[http://ubuntuforums.org/showthread.php?t=1282482&highlight=xorg.conf](http://ubuntuforums.org/showthread.php?t=1282482&highlight=xorg.conf)

Please mark this thread as "Solved"

Thanks!

---

