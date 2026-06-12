---
title: "[SOLVED] Linux-noob can use some help with my boot-up errors!!"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by swoody on 2008-04-04
I don't know where else to post this so here goes.....
I have Ubuntu installed as a dual boot with windows vista, and everything's been running good for a while, but after I installed a new theme for Ubuntu, and one for Firefox I can't fully boot up Ubuntu anymore. Since I originally installed Ubuntu I've always got a couple messages before the loading screen:

> [16.948412] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[16.948477] PCI   "      "      "     "  region 8 of "  "  "
[16.948539]PCI:  "       "     "     "    region 7 of bridge 0000:00:1c.2
[16.948600]PCI: "        "            "   region 8 of "           "        "       "
[16.948695]PCI: "       "              "  region 0 of device 0000:06:00.0

(the quotation marks just signify the same info as the above entry, in case you didn't know:D )

These messages are still coming up now that Ubuntu won't fully load.
After the loading screen comes up for a little bit it goes back to a black and white DOS looking page that has the above messages at the top and then the following:

> Loading, please wait......
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu 7.10 steve-laptop tty1

steve-laptop login:
password:
Last login: ............................ on tty1
Linux steve-laptop 2.6.22-14-generic #1 SMP Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software:
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with absoloutly no warranty, to the extent permitted by
applicable law.
steve@steve-latop:~$

So what can I do to get back to loading Ubuntu normally? The last line is a terminal entry line thingy, so I can work on it, but I don't have the slightest idea what to do.

Thank you VERY much in advance. I just got the system set up nicely, and I don't want to have to reinstall everything again.

---

### Post by Pumalite on 2008-04-04
Have you tried Ctrl-D?

---

### Post by swoody on 2008-04-05
Oh, and to add, it displays this screen in both normal and recovery modes.

No, I'm in the middle of downloading a large file, and if I disconect I'll have to start over, but when that's done I'll give it a shot. [-o< Thx

---

### Post by swoody on 2008-04-05
> **Pumalite said:**
> Have you tried Ctrl-D?

Nope, I tried ctrl+d and it just cleared whatever info was on the screen and asked for my login info again.

Just for fun, I tired every other combination of ctrl+ a letter, and got nothing useful as far as I can tell.

---

### Post by Pumalite on 2008-04-05
username
password
Try:
sudo dpkg-reconfigure xserver-xorg

---

### Post by swoody on 2008-04-05
> **Pumalite said:**
> username
password
Try:
sudo dpkg-reconfigure xserver-xorg

Nope, sry. I ran the whole configuration (twice to make sure) and it just gave me a post installation warning that I may be overwriting possibly customised configuation file, and it was backed up. Afterwards, I rebooted, and still the same thing :confused:

---

### Post by Peter Westley on 2008-04-05
Steve,

By way of some background for you:

It looks like your X-server (that's the graphics screen driver that allows all the fancy windows an' stuff) isn't starting properly and it might be something to do with having loaded the new theme but that's not clear.

The PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0 errors are quite possibly unrelated - especially if it was workng when you had these errors before.

The DOS thingy that it goes to with the $ prompt is a "command shell" running in "terminal". This is what unix (Linux) always used to look like! And it's where you give it commands when you don't have an X11 graphical user interface.

Pumalite's suggestion was to re-reconfigure the X-server in case something didn't get done right when you installed the theme.

I can't really be of much more assistance other than to try and take note of what if anything gives a [FAIL] when booting.

Hope the background info helps in your quest.

---

### Post by swoody on 2008-04-06
> **Peter Westley said:**
> 
It looks like your X-server (that's the graphics screen driver that allows all the fancy windows an' stuff) isn't starting properly and it might be something to do with having loaded the new theme but that's not clear.

I can't really be of much more assistance other than to try and take note of what if anything gives a [FAIL] when booting.



There aren't any [FAILED] of [OK] things listed when I boot up Ubuntu. When I shut it down or restart it, it lists some of them.

There's nothing that said [FAILED], but there was one message that said:

> NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connetion is closed
Network Manager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus connection' failed

Then after a couple seconds I think it flashed [OK] right before it shutdown.

---

### Post by swoody on 2008-07-03
Just wound up reinstalling Hardy, but this time I got rid of Vista completely. Everything works so much better now, lol :D

---

