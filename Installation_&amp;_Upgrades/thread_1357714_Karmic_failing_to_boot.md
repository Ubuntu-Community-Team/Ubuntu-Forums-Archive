---
title: "Karmic failing to boot"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Janeleaper on 2009-12-17
This is freaking me out.

I updated my Dell Inspiron 530 (pc 'A') desktop from 9.04 to 9.10 a couple of weeks ago.  There were teething problems.  I had Firefox working slowly, which I sorted out by disabling some add-ons.  I can't get the BBC iplayer to work properly.  But apart from that there were no serious problems, so a couple of days ago I updated our other Inspiron 530 (machine 'B') from 8.04 to 9.10.

Yesterday Firefox started crashing on both machines.  It only did it a couple of times and restarted without problems.

Then today, machine A would not recover from sleep mode.  I turned off and tried to reboot, but it took 3 attempts. On the first attempt I got the following message:

[I]fsck from util-linux-ng 2.16
/dev/sda1:clean, 282708/29769728 files, 4556972/59522825 blocks
modem manager: loaged plugin Novatel
modem manager: loaged plugin Gobi
modem manager: loaged plugin Huawei
modem manager: loaged plugin Nokia
modem manager: loaged plugin Generic
modem manager: loaged plugin ZTE
modem manager: loaged plugin MotoC
modem manager: loaged plugin Option
modem manager: loaged plugin Option High-Speed
modem manager: loaged plugin Ericsson MBM
modem manager: loaged plugin Sierra
* could not access PID file for nmb[/I]

On the second attempt to boot I got the same message but with these lines at the beginning:

usb-id(434):unable to access '/devices/pci0000:00/0000:001a.1/usb/4-1'
usb-id (437): unable to access '/devices/pci0000:00/0000:00:1a.1/usb4/4-2.

On the third attempt to boot I pressed F2 at the Dell screen and then the pc booted normally.  There is nothing obviously wrong now.

Does anyone have any idea what is going on?

NB.  I don't normally let my machine go into sleep mode, this happened because of a long phone conversation.  It might be the first time it's been in sleep mode since I upgraded.

---

### Post by Lomz on 2010-01-07
Same problem, although it happends on random basis (as far as I know).

---

