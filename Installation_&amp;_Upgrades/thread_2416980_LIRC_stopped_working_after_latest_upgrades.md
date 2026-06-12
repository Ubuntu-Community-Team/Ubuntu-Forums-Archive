---
title: "LIRC stopped working after latest upgrades"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by dvjunk on 2019-04-18
I am running Mythbuntu 16.04.6 LTS and Mythtv 28.2. I use LIRC with an MCE remote and "Homebrew" Serial Port and this has been working for me for years, since I built my system.

On Sun 4-14 I performed upgrades as scheduled by Software Center. I think this is the list of stuff that was installed then.

```
2019-04-14 18:48:52 status installed man-db:amd64 2.7.5-1
2019-04-14 18:48:52 status installed install-info:amd64 6.1.0.dfsg.1-5
2019-04-14 18:48:53 status installed systemd:amd64 229-4ubuntu21.21
2019-04-14 18:48:54 status installed ureadahead:amd64 0.100.0-19
2019-04-14 18:48:55 status installed grub-common:amd64 2.02~beta2-36ubuntu3.21
2019-04-14 18:48:55 status installed grub2-common:amd64 2.02~beta2-36ubuntu3.21
2019-04-14 18:48:55 status installed grub-pc-bin:amd64 2.02~beta2-36ubuntu3.21
2019-04-14 18:49:13 status installed grub-pc:amd64 2.02~beta2-36ubuntu3.21
2019-04-14 18:49:16 status installed rsyslog:amd64 8.16.0-1ubuntu3.1

```

After these upgrades LIRC stopped working. I tried all of my normal LIRC setup/fixes with no luck. This included
Purging/Installing LIRC
Configuring the Hardware (dpkg-reconfigure lirc)
Editing the hardware.conf
Using IRW and mode2 and cat /dev/lircx to check for responses

I have LIRC0 and LIRC1 in /dev and tried using both. I have had issues with my port being re-enumerated randomly to LIRC0 and LIRC1 in the past.

Did something change that would cause LIRC to stop working?

Any thoughts greatly appreciated.

Don

---

### Post by dvjunk on 2019-05-08
I tested the signal going into my motherboard with an oscilloscope and it is working fine, so I'm sure something in software broke the homebrew lirc input.
After not getting any responses to either of my posts, I decided to purchase a new USB IR receiver. I got an HP OVU400103/00 off ebay for $8. I plugged it in, re-installed LIRC, selected "Windows Media Center Transcievers/Remotes (all)" for the receiver and none for blaster. I re-copied my mce usb lircd to lircd.conf, restarted lirc, restarted Mythtv frontend and viola it is working fine.
I don't know what stopped the homebrew lirc config from working, but hopefully this will also solve my issue with the port randomly being assigned to 0 or 1.
Hopefully this will help someone else in the future.

---

