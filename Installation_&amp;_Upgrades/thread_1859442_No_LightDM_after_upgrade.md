---
title: "No LightDM after upgrade?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by iomtalach on 2011-10-13
In 11.04 I had kubuntu installed as an extra shell, and when I upgraded to 11.10 I don't get the pretty LightDM login that I was looking forward to. I get what looks like an updated version of the old login screen.

I've removed kubuntu completly, and now have the usual ubuntu boot-up, and manually installed Lightdm, rebooted, but still no pretty-ness.

Any idea how to make it happen?

Thanks!

Edit: Seems to be the unity-greeter that isn't starting. Hmm. More digging.

---

### Post by iomtalach on 2011-10-14
Weird. I get this:
[   20.314241] init: lightdm main process (1038) killed by TERM signal
 in dmesg...hmmmm...

---

### Post by iomtalach on 2011-10-14
Ha! Victory for ZIM!

Figured it out.

sudo apt-get remove kdm (it was still lingering. sheesh. Noticed it in dmesg.)
sudo apt-get remove lightdm
sudo apt-get install lightdm...which brought up a nice little term config wanting to know which manager I wanted as a default, gdm or lightdm. Selected lightdm, rebooted.

Yay! I has the pretty now. Now all I have to do is figure how to get a resolution higher than 1024x768 on my mom's hp G6 with in the intel i915 issue. Works with mint, but not Unity. sigh.

---

