---
title: "Lenovo T530 Touchpad is not working in fresh installed Ubuntu 20.04"
date: 2020-05-06
forum: Installation &amp; Upgrades
---

### Post by slkamath on 2020-05-06
Hi All,

Hope everyone are good at your side & safe.

I have newly installed fresh 20.04 and my touchpad is not working after that. while installing itsself it was not working. I thought it will work after reboot but no luck. Can someone help me to solve this?

Laptop - Lenovo T530
OS - Ubuntu 20.04
```
okeshkamath# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Liteon Dell Wireless Device Mouse           id=11    [slave  pointer  (2)]
&#9116;   &#8627; Liteon Dell Wireless Device Consumer Control    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=9    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device                 id=10    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device System Control    id=13    [slave  keyboard (3)]
    &#8627; AT Raw Set 2 keyboard                       id=14    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=15    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device Consumer Control    id=16    [slave  keyboard (3)]
```

```
lokeshkamath# sudo nano /etc/default/grub
  GNU nano 4.8                   /etc/default/grub                              
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"
GRUB_CMDLINE_LINUX=""
```

Few things i tried using google. no luck.

So please help me to solve this issue.

Lokesh Kamath

---

### Post by slickymaster on 2020-05-06
*Thread moved to **Installation & Upgrades**.*

---

### Post by ActionParsnip on 2020-05-06
Is this ongoing or is the issue resolved, please?

---

### Post by slkamath on 2020-05-06
No. It is not resolved.

---

### Post by slkamath on 2020-05-07
Can someone help me please

---

### Post by ActionParsnip on 2020-05-07
Try changing:
```

GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"

```
to:
```

GRUB_CMDLINE_LINUX_DEFAULT="i8042.irqpoll quiet splash"

```
or:
```

GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"

```
or:
```

GRUB_CMDLINE_LINUX_DEFAULT="i8042.nomux quiet splash"

```

Obviously, run:
or:
```

sudo update-grub
sudo reboot

```

to test each option in turn.

HTH

---

### Post by slkamath on 2020-05-07
Thank you for your response.

No luck. It is still not working.

---

### Post by slkamath on 2020-05-08
I tried reinstalling the Ubuntu 20.04, still while installing it'self it is not detecting.

---

### Post by mörgæs on 2020-05-08
The problem has been posted for a few other users under 20.04. If everything else fails you could install 19.10 and use it for two months more.

---

### Post by slkamath on 2020-05-08
Ok. Thank you so much.

I will wait for 2, 3 months.

---

### Post by ubfan1 on 2020-05-08
Did you check your BIOS/UEFI Settings for trackpad/enable choices?

---

### Post by slkamath on 2020-05-10
Yes. I tried that too.

But no luck.

---

### Post by jeremy31 on 2020-05-10
Any results for ```
dmesg | grep i2c
```

---

### Post by slkamath on 2020-05-11
Thanks for your reply.

Result of 
dmesg | grep i2c
[    0.848972] i2c /dev entries driver

---

### Post by jeremy31 on 2020-05-11
Is there a setting in BIOS to enable?

---

### Post by slkamath on 2020-05-11
Yes. It is enabled.

In Laptop Trackpoint is working. But touchpad & Touchpad let & Right button is not working.

---

### Post by slkamath on 2020-06-20
Any update on this?

---

### Post by ubfan1 on 2020-06-20
Run xinput in a terminal and please post the output.  From a terminal, run xev, move the cursor to the windows that opens, and use the touchpad, and its buttons to see if the move and button press/release events are seen in the terminal window.

---

### Post by slkamath on 2020-06-27
Sorry for the delayed response.

Output of xinput: 
xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Liteon Dell Wireless Device Mouse           id=12    [slave  pointer  (2)]
&#9116;   &#8627; Liteon Dell Wireless Device Consumer Control    id=13    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=9    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device                 id=10    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device System Control    id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=16    [slave  keyboard (3)]
    &#8627; Liteon Dell Wireless Device Consumer Control    id=17    [slave  keyboard (3)]


if i run xev in terminal, my external mouse is working. not touchpad. Touchpad is not working.

---

### Post by ubfan1 on 2020-06-27
I have a w520, and see a line from xinput like:
&#8627; SynPS/2 Synaptics TouchPad                  id=14
Take a look at the output of dmesg to see if the device is seen at all:
dmesg |grep -i touchpad
(You might get a touchpad on your mouse also if it has a thumbswipe)
Might be a hardware problem, and you need to check the cable (which might have been messed up if you removed the keyboard for a memory insert).

---

### Post by slkamath on 2020-06-28
Thanks for your reply. 

before update to 20.04 I had 18.04. In that it was working fine. I never removed keyboard or any other thing. I tried installing windows 10. Touchpad is working fine in that.

So not a hardware problem.

Lokesh Kamath

---

