---
title: "DVB-T problem getting it working"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by Ralthor on 2015-09-11
Let me start out with I am quite experienced with computers in general but a total noob when it comes to linux. Over the years I have tinkered with various incarnations including red hat, suse, early versions/flavours of ubuntu. Lets just leave it at noob. :) 

Anyhow, I recently installed Ubuntu 14.04 LTS 64bit on my media machine. I have got everything working properly except for the DVB card. I have been struggling with this for the last week or so to no avail. The point I am at now shows no errors in dmesg. It appears to be loading the firmware properly. The card is a Mystique SaTeCaBiX S2/T2/T/C which is basically a renamed  [DVBSky T9580 (PCIe)]("http://www.linuxtv.org/wiki/index.php/DVBSky_T9580_(PCIe)") every thing I found said basically the same thing as that page.

From what I understand I should have: adapter0/frontend0, adapter1/frontend0, adapter1/frontend1 
What I actually have in /usr/share/dvb/dvb-t: adapter0/frontend0, adapter1/frontend0

When I try to use Kaffeine it tells me: No available device found
When I try to scan -a 0 -f 0: WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM) - Makes sense as this is the DVB-Sport.
When I try to scan -a 1 -f 0: FATAL: failed to open '/dev/dvb/adapter1/frontend0': 16 Device or resource busy

Any help here much appreciated.

dmesg | grep dvb:
```
[   12.410323] cx23885_dvb_register() allocating 1 frontend(s)
[   12.410328] cx23885[0]: cx23885 based dvb card
[   12.764830] cx23885_dvb_register() allocating 1 frontend(s)
[   12.764832] cx23885[0]: cx23885 based dvb card
[   44.814759] si2168 9-0064: downloading firmware from file 'dvb-demod-si2168-a30-01.fw'
[   48.224050] si2157 13-0060: downloading firmware from file 'dvb-tuner-si2158-a20-01.fw'
[19081.119889] m88ds3103 10-0068: downloading firmware from file 'dvb-demod-m88ds3103.fw'
```

*EDIT 

Typical, been struggling with this for a week. Finally admit defeat and post looking for help, then fix it in an hour or 2 after that! 

Anyhow more searching revealed someone fixed a similar issue by removing the v4l utils and firware, I did the same and presto kaffeine scans and finds channels. :D

---

