---
title: "Intel 3945abg"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dazzler on 2009-10-13
Can someone tell me if Intel 3945 WLAN cards are still (borked) on Karmic or have I messed something along the way, my iPhone is not the better web browser and I would like my lappy back :)

---

### Post by zoomy942 on 2009-10-13
> **dazzler said:**
> Can someone tell me if Intel 3945 WLAN cards are still (borked) on Karmic or have I messed something along the way, my iPhone is not the better web browser and I would like my lappy back :)

they work fine buddy.

---

### Post by dazzler on 2009-10-13
Hmmm how can if fix it, i think its network manager thats gone wrong my cards seen in iwconfig, but network manager doesnt see it at all.

PS its the wlan0 interface im interested in ra0 is my temp solution (pcmia)

> lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"dazzler"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1B:2F:45:F6:9B   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-45 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by dazzler on 2009-10-14
Nope its still borked, just did a complete reinstall from the latest daily build and network manager wont let me start wireless, gutted.

Time to reinstall things

---

### Post by Zorael on 2009-10-14
Any difference with wicd?

The only issues I've had with my 3945 is that I had to disable HW scanning by enabling that module option. Other than that it's been working nicely.

---

### Post by Starks on 2009-10-14
My 3945abg works fine for me with Network-Manager and Wicd.

Only complaint is that Ubuntu doesn't handle weak signals as efficiently as Windows does.

---

### Post by dazzler on 2009-10-14
Well the only other difference i can think off is my hardware wifi toggle button is not recognized, do you know how i can toggle it on via the terminal ive tried iwconfig wlan0 up and start and a few other things i can remember from backtrack but i cant get it toggled

Bit more info 

> dazzler@dazzler-medion:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


My bios only has wifi off or last state so i think i may need to toggle it somehow

**Just an update seems to be something stupid specific to this backward brand of laptop, i had to install winblows, download the shortkey app, enable wifi, then quickly get rid of that rubbish and reinstall ubuntu, :)**

---

