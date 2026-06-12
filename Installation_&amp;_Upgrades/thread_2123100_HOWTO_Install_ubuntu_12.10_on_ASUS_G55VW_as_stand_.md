---
title: "HOWTO: Install ubuntu 12.10 on ASUS G55VW as stand alone OS"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by darkenedday on 2013-03-07
Not sure why, but this was a nightmare for me, maybe I'm a little rusty but this is how I eventually solved it, if you found an easier way feel free to post it.
NOTE: as if writing the open source nvidia drivers in 12.10 don't support the nvidia GTX 660m

I disabled secure boot in the BIOS you might now have to, but I know ubuntu's secure boot is somewhat buggy so I decided to not take the chance with it.
I DID NOT disable fast boot (may have made my life easier to diable it, but I wanted to see if it would help booting Ubuntu)
Ubuntu IS installed in EFI mode.

ok on to how to do this
I Used a live USB of 12.10 (I'm never going back to LIVE CD if I can avoid it)
I arrived at a somewhat different screen with this, it was a more grub like screen, but it was welcomed in this case. I could not get the "Try ubuntu" option to work in any case.
Highlighted "Install Ubuntu 12.10" press "e" on the "vmlinuz" line after the two dashes type "nomodeset" without the quotes, press f10 to boot.
Should now boot correctly to ubiquity. Configure and partition to your liking. restart.
I could not get this **** thing to show grub so that I could designate nomodeset again, but no matter, time for some CLI goodness.
this should boot directly to a CLI, 
login and follow the following install steps IN ORDER

NOTE: if you connected to a wireless network in the installer it should autoconnect to it on startup now. if wired you'll autoconnect regardless.

now for commands.

sudo apt-get upgrade

sudo apt-get dist-uprgade
(I rebooted here to be safe, you may not have to)

sudo apt-get install linux-headers-generic
(also rebooted here to make sure everything was applied, at this point I was paranoid)

sudo apt-get install nvidia-experimental-310 nvidia-settings-experimental-310
(you may choose to use nvidia-current if you want, I wanted 310 drivers for steam games)

sudo reboot

it should now boot into lightDM with no problems and you should be able to login.
I know to alot of you this will seem very simple, but to some (either the very CLI rusty or the very new to linux, it's not so obvious, especially when the order of those commands is important, don't tell me it's not because I did them out of order and kept trying to purge packages and start over, and it never worked, after a clean install THIS worked)

---

