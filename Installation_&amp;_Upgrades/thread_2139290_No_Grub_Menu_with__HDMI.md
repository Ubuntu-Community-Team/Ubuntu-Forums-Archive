---
title: "No Grub Menu with  HDMI"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by AVH on 2013-04-26
If I try to boot using an HDMI cable I get no Grub Menu. The MB slash, post, and Bios info all display and also the the background for the Grub Menu. But, nothing else. There does not seem to be any keyboard input either.

When I hook up a second monitor with a DVI cable everything displays fine on the DVI monitor and the HDMI  monitor gets no video signal until I reach the log-in screen at which point both monitors work properly.

I can boot off a live cd with no problems using only HDMI, so I believe the problem is with grub not recognizing the HDMI properly.

Any sugestions?
Should I file a bug report?


12.04 LTS
Gigabyte MB GA-965P-DS3
EVA Nvidia Gforce GT 520 w/ nvidia-current drivers

---

### Post by dino99 on 2013-04-26
What says the gigabyte MB doc about using hdmi ?  which kind of hdmi cable is it ?  
Seems to me a conflict dvi/hdmi; how many video output on that gt520 ? maybe some related bios/uefi settings

[http://www.google.fr/#hl=fr&gs_rn=11&gs_ri=psy-ab&pq=ubuntu%20hdmi%20black%20screen&cp=17&gs_id=4d&xhr=t&q=ubuntu+hdmi+grub2&es_nrs=true&pf=p&tbs=qdr:y&sclient=psy-ab&oq=ubuntu+hdmi+grub2&gs_l=&pbx=1&bav=on.2,or.r_qf.&fp=9afa058267fd07a2&biw=1674&bih=888](http://www.google.fr/#hl=fr&gs_rn=11&gs_ri=psy-ab&pq=ubuntu%20hdmi%20black%20screen&cp=17&gs_id=4d&xhr=t&q=ubuntu+hdmi+grub2&es_nrs=true&pf=p&tbs=qdr:y&sclient=psy-ab&oq=ubuntu+hdmi+grub2&gs_l=&pbx=1&bav=on.2,or.r_qf.&fp=9afa058267fd07a2&biw=1674&bih=888)

---

### Post by AVH on 2013-04-26
MB doc says nothing about HDMI since there is no built-in graphics.
Standard high speed HDMI cable.
GT 520 has VGA, DVI, HDMI.

Older MB no uefi, and no settings for video.

---

### Post by AVH on 2013-04-28
Fixed it! I had to remove "quiet splash" from the kernal parameters.

 I then had problems with being stuck in low resolution. I had to remove and re-install the video drivers to fix that problem. I ran into the old problem of Nouveau conflicting with Nvidia. I now have the "This driver is installed but not not currently activated" message even though Unity and the Nvidia control panel are working fine and Nouveau has been removed. Really??? This bug is still around?

---

