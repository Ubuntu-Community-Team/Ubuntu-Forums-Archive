---
title: "Warning to Cinnamon users: Upgrading 11.10 &gt; 12.04 might delete your Cinnamon"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by Roving Sign on 2012-05-10
I've just discoverd that I no longer have Cinnamon installed after upgrading.

Kinda frustrating.

Something to take note of - any suggestions to keep this from happening on my other machines?

Is there something during upgrade I should watch for...?

:confused:

---

### Post by wojox on 2012-05-10
ppa? Is it suported in 12.04?

---

### Post by Roving Sign on 2012-05-10
> **wojox said:**
> ppa? Is it suported in 12.04?

Supported or not - it should not have been removed.

Im ok if they wanted the machine to reboot to Unity after upgrade - but I dont like my stuff being removed.

---

### Post by nothingspecial on 2012-05-10
ppas are disabled when you upgrade to avoid breaking your system.

---

### Post by wojox on 2012-05-10
Was it removed or you just don't see it?

---

### Post by Roving Sign on 2012-05-10
> **wojox said:**
> Was it removed or you just don't see it?

Its not in the list of available Desktops when I log in...

I'll check the PPA...

---

### Post by wojox on 2012-05-10
> **nothingspecial said:**
> ppas are disabled when you upgrade to avoid breaking your system.

+1, Look in Software Sources and see if it's checked. Try adding the ppa again.

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

---

### Post by Roving Sign on 2012-05-10
Looks like it was disabled on upgrade - another issue - this was still using the old - merlwiz repo (1.3) - I tried to add the newer ppa - after update it says "error: dpkg cant lock" or something to that effect.

There is a muffin update in Update Manger (from the Cinnamon repo), but thats not going help much without Cinnamon.

So- for now - looks like Gnome classic for this box.

---

### Post by wojox on 2012-05-10
I'ts throwing that error due to the fact that you have more than one application open to update/install. Software Center, Synaptic ???

Purge the old repos and add the new one. I found that over here @ [4- Install Cinnamon]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/")

---

### Post by Roving Sign on 2012-05-10
> **wojox said:**
> +1, Look in Software Sources and see if it's checked. Try adding the ppa again.

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

Thanks wojox - hah - I got distacted by that dpkg error, and forgot to try the install command!

Ok - so it seems back! Thanks for the help...

Sorry to be cranky about this...my GF was whining about Unity.

Actually - I tried the Gnome classic - and I might just go back to that! I can never get the Cinnamon "Menu" button to be as repsonsive as I wish...

So the moral of the story is - if you find your missing something after upgrade, check to see if something hasnt been disabled.

---

### Post by Roving Sign on 2012-05-10
> **wojox said:**
> I'ts throwing that error due to the fact that you have more than one application open to update/install. Software Center, Synaptic ???

Purge the old repos and add the new one. I found that over here @ [4- Install Cinnamon]("http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/")

I had Synaptic open, but had closed it - seems like it doesnt give up it's lock?

---

