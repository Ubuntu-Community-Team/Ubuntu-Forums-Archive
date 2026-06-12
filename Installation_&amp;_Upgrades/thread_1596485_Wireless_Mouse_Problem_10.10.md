---
title: "Wireless Mouse Problem 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by beegary on 2010-10-14
I use a Kensington Wireless Netbook Mouse.
 
It has worked well in Ubuntu 9.10 and 10.04.
For some reason in 10.10 it works, but every now and again it sticks for a second or two. Sometimes the left button stops working.
If I pull out the dongle for the mouse and put it back in my mouse works fine.
 
Any ideas?

---

### Post by beegary on 2010-10-16
ill try somewhere else

---

### Post by beegary on 2010-10-19
Its lonely in here.

I thought this was unique to my hardware, but it seems not:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311)

I have tried some of the posted solutions with no help so far.

---

### Post by edulimaabreu on 2010-11-13
Same problem here, i have a combo (mouse+keboard and one dongle USB) with Microsoft wireless Mouse 5000.

Try the steps bellow, seems to working for me (for now)

InTerminal:

> xinput --listwill appear something like that, showing all your input devices:

> eduardo@PCi5Lin:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=8    [slave  keyboard (3)]
eduardo@PCi5Lin:~$ have 2 lines to my mouse, i used the line bellow (ID = 10)


them type:

> xinput set-int-prop YOUR_ID "Device Enabled" 8 0im my case:
xinput set-int-prop 10 "Device Enabled" 8 0


if not work for you, back your configurations:
xinput set-int-prop YOUR_ID "Device Enabled" 8 1

---

