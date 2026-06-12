---
title: "Configuring Italc and Smoothwall SW3"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by ElectronicCarpenter on 2011-03-28
I thought Italc was not working, I have tried just about everything in the forums for my issue. 

The Master and Client do not communicate fully. They see each other as far as being able to say no user logged in vs the unreachable host.

I had a problem with the avahi-daemon not starting..
Found help in the forum to fix that.. etc/default/avahi-daemon

Changed the settings to...
AVAHI_DAEMON_DETECT_LOCAL=0
AVAHI_DAEMON_START=1

Logged out and when  I logged in again.. services running same with a reboot which always failed.

I still could not connect... saw some old posts but opted to get back to basics.  I bypassed the smoothwall hooked a router withdhcp on it rebooted the machines, opened Italc and auto discovery still does not work.  I added the ip and it worked seamless telling me that the issue is routing internally.  

I just do not know the correct ports or how to correctly forward internal traffic on a smoothwall could someone help me. I have put the smoothwall back into place and and am waiting for your response.

Thanks
:guitar:

---

