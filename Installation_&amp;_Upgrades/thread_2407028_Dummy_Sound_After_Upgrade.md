---
title: "Dummy Sound After Upgrade"
date: 2018-11-29
forum: Installation &amp; Upgrades
---

### Post by sparky772 on 2018-11-29
My Device


justin@justin-HP-Pavilion-x2-Detachable:~$ neofetch
            .-/+oossssoo+/-.               justin@justin-HP-Pavilion-x2-Detacha 
        `:+ssssssssssssssssss+:`           ------------------------------------ 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 18.10 x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: HP Pavilion x2 Detachable 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 4.18.0-11-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 19 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 1669 (dpkg), 9 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 4.4.19 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1280x800 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 3.30.1 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: GNOME Shell 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Yaru [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Yaru [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel Atom x5-Z8300 (4) @ 1.840 
    .ossssssssssssssssssdMMMNysssso.       GPU: Intel Atom/Celeron/Pentium Proc 
      -+sssssssssssssssssyyyssss+-         Memory: 1072MiB / 1915MiB 
        `:+ssssssssssssssssss+:`




When opening alsamixer in terminal the sound card is "Intel HDMI/DP LPE Audio", but "This sound device does not have any controls."


in terminal i have remove and installed 


sudo apt remove --purge alsa-base pulseaudio
sudo apt install alsa-base pulseaudio


in settings the sound card is still Dummy Output.


Don't know how my device is going to get sound working,

---

### Post by yancek on 2018-11-29
Try running the following commands separately and posting the output and someone might be able to suggest something with that information.  

> aplay -l
sudo  lspci -v | grep -A7 -i "audio"

Has the sound ever worked on Ubuntu?  Do you have any other OS installed?  If so, does the sound work on it?

---

### Post by dshimer on 2019-03-30
Old post, assuming it is fixed by now but I want to post the solution that worked for me.

Based on [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1801538](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1801538)    

```
systemctl stop timidity.service
systemctl disable timidity.service    

```    
Affect of the "stop" was instant and everything was fully restored.

---

