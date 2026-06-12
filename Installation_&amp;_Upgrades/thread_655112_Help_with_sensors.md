---
title: "Help with sensors"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by gregcss on 2007-12-31
I Installed the following packages lm-sensors. Next step is Run the mkdev.sh script in the lm-sensors source. What does this mean? i searched my HDD and i dont have mkdev.sh

---

### Post by PmDematagoda on 2007-12-31
All I did to get lm-sensors to work properly was to execute:-
```
sudo sensors-detect
```
then add the required modules for auto-loading on start-up and finally reboot the PC. Lm-sensors should work properly after following the previous steps.

---

### Post by gregcss on 2007-12-31
ok did that. i do not have the following file, i am showing hidden as well. :(

/etc/modprobe.d/local

---

### Post by PmDematagoda on 2007-12-31
Just allow the required lines to be added automatically, that is easier and works just as well.

---

### Post by gregcss on 2007-12-31
Thanks for your support :) 
Now I i shall get this into conky.! I am such a newb

---

### Post by PmDematagoda on 2007-12-31
> **gregcss said:**
> Thanks for your support :) 
Now I i shall get this into conky.! I am such a newb

Glad you got it running:), good luck with Conky.

---

### Post by gregcss on 2007-12-31
one quick question. i have dual core, i understand temp 1 & 2 but what is temp3 @ -1C?

temp1:       +36°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       +23°C  (low  =  +127°C, high =  +127°C)   sensor = diode   
temp3:        -1°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor

---

### Post by PmDematagoda on 2007-12-31
Not very sure, but, do you live in a very cold region?

---

### Post by gregcss on 2007-12-31
.

---

### Post by tgalati4 on 2008-01-01
It's not connected.  Some motherboards have an on-board video chip temp sensor.  Some have a power regulator temp.  Your modules are put in /etc/modules.  You can modify the sensors configuration file to set up sensible alarm limits.

---

### Post by chudder on 2008-01-02
> **PmDematagoda said:**
> All I did to get lm-sensors to work properly was to execute:-
```
sudo sensors-detect
```
then add the required modules for auto-loading on start-up and finally reboot the PC. Lm-sensors should work properly after following the previous steps.

I downloaded every possible bit of softward via synaptic for lm-sensors and I typed in the above command and I ran everything automatically at the last step but I can't see anything different, I can't say I know what to do after I restart or before.  I could use some clarification.

My intent is to use lm sensors to link them to gdesklets.  

Thanx to anyone greatly!

Chudder

---

