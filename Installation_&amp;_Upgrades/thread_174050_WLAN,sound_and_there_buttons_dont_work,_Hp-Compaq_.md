---
title: "WLAN,sound and there buttons dont work, Hp-Compaq nx9420"
date: 2006-05-11
forum: Installation &amp; Upgrades
---

### Post by rickeboy on 2006-05-11
Hay all! 
Have installed Kubuntu 5.10, all latest upgrades and I brought in latest kernel from kernel.org. 

WLANcard: Intel PRO Wireless 3945ABG
Soundcard: Analog Devices HD1981

My problem is this: When the system is up the MUTE ON/OFF button on the laptop shows that MUTE is ON (light) I press it but nothing happens. The WLAN ON/OFF button shows OFF (no light) I press it; nothing. 
The WLAN card drivers loads good but that makes no one happier if the card isnt on does it? :rolleyes: 
I checked in alsamixer and it found the sound card with out any trouble everthing seeams to be good... in KDE the speaker next to the clock is muted I right click it and press so that it becomes none muted but the light on the MUTE button is still there so no sound output...

What do u guys think? ACPI? Others?

//rickeboy

---

### Post by rickeboy on 2006-05-15
Aight guys latest report: the sound is up...(!) still no WLAN thou... will keep trying...

//rickeboy

---

### Post by rickeboy on 2006-05-16
All is solved... solved it by installing Kubuntu Dapper Flight 7. Sound worked out-of-the-box and after some fixing the WLAN card came up also WPA...

//rickeboy

---

### Post by atlas95 on 2006-12-27
> **rickeboy said:**
> All is solved... solved it by installing Kubuntu Dapper Flight 7. Sound worked out-of-the-box and after some fixing the WLAN card came up also WPA...

//rickeboy

Hi,
Could you explain fix for wireless and fix for other things maybe?
I will buy it next week and I search information for install it easyly...

Sorry for my english

Thanks :)

---

### Post by dg88 on 2007-01-23
apt-get update will fix everything except the cardreaders on nx9420. only problems i have excedpt the cardreaders is long boot time.

---

### Post by the_toddster on 2007-03-20
Have you found a solution for the long boot time? I used the live cd version of 6.06 and 6.10, but am unwilling to install until I have a reasonable expectation that it will be usable.

I also have a strange problem where my laptop is periodically unresponsive: works for 5 seconds, freezes for 5 seconds, works for 5 seconds, etc....

---

### Post by the_toddster on 2007-03-23
After disabling wifi, I tried 6.10 again lastnight and had great success!! Looks like wifi was the culprit causing the slow boot. Maybe that was the cause of the strange periodic booting too?

Whatever, it works well now.

Just need to get a client for Guild Wars and I'll be good to go  :-)

---

