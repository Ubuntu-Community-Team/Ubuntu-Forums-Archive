---
title: "Jaunty wireless light blinking question"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by laptoplinux on 2009-04-10
I'm still running Hardy, but from what I've seen, the newer kernels change a little bit in how the wireless drivers behave, at least with the Intel 3945.  I have a Dell Latitude D820, and in the Jaunty Beta, the wireless light blinks on any network activity.  This gets kinda distracting due to the placement of the wifi light on my laptop.  

In Hardy, the wifi light just simply stays off the whole time.  

I found a script in these forums back when Ibex came out that is supposed to stop the blinking light:

```

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger 

```

When this script is placed in /etc/network/if-up.d/ with root-level permission to execute, it causes the wifi light to simply not light up at all in Jaunty.  This is how it behaved in Hardy for me, so this is acceptable.  But, I was wondering if there is any way to make the light have the following behavior:

Wifi card off --> wifi light off
Wifi card on and connecting to new network --> wifi light blinking momentarily until fully connected

Wifi card on and fully connected to network --> wifi light on steady.  Solid light, no blinking on network activity.

Is there a way to change the wifi light's behavior to this under Jaunty?  I would file a bug report about this, but I hesitate to since, technically, the behavior that annoys me is supposedly the intended behavior for these kernels.  But it is still annoying to me and I would like to find a way to change this behavior.  I just wish that future kernels might adopt a default light behavior like this instead of the current behavior.

---

### Post by laptoplinux on 2009-04-10
Ok, well, based on what I think I understand about the wifi led, I should be able to achieve what I want by only having the lines with TX and RX in the script and removing the lines with assoc and radio.  

However, I tried that on a live USB instance of Jaunty beta, and even though the config file registers the change (confirmed by catting it), the wifi light continued to blink all the time.

Then I changed the assoc and radio options to none as well, and the light stayed on in a constant state, like I had wanted.  I'm not sure why the last time I tried something like this on the Jaunty Beta the light just turned off completely.  

I guess I'll just wait for the Jaunty final release and then upgrade whenever I get the chance.  If I manage to get the wifi light working to my satisfaction, I'll keep it.  If not, I'll go back to Hardy again.  That, or buy a Mac.  :neutral::-k

---

### Post by laptoplinux on 2009-04-11
I may have figured out a solution to this problem.  

I've done a little more digging with it in the Jaunty Beta. I also played with it some in the Fedora 11 Beta. This is a kernel issue, so the distro shouldn't affect things too much.

At least with Fedora (and I'm assuming it would be the same on Jaunty--Fedora just happens to be what I tested under):

The /sys/bus/pci/drivers/iwl3945/0000:0c:00.0/leds/iwl* and /sys/class/leds/* settings appear to mirror each other; change on and the corresponding setting in the other area is changed. Symbolic link maybe?
That being the case, I'd just go for changing the /sys/class/leds/iwl* triggers. Less to type.

Also, under the latest release betas, I found that changing the RX and TX triggers to "none" appeared to have no effect. Changing the radio trigger to "none" made the light turn off completely, and changing the assoc trigger to "none" made the light remain solidly on (so long as the radio trigger was in its default setting and not set to "none" as well.)

In case anyone is wondering, the values of these triggers can be found by using cat (example):

cat /sys/class/leds/iwl-phy0\:assoc/trigger

This will produce a list of values, with the one in brackets being the currently selected one.

Again, this is just some digging I did in preparation for giving Jaunty a shot later. I don't really understand this stuff, and I can't guarantee it will work for any machine other than mine.

---

