---
title: "Freezes at start up"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Ohwii on 2012-11-13
Hey Guys,

I am in desperate need. My Xubuntu just died on me. I am unable to boot. See the spalsh for a few seconds then I get 

```
* PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned 

* Checking battery state ...               [OK]
```

and then it just freezes.

I pressed alt+ctrl+F2 logged in and got this 
```
lspci -vnn | grep VGA
... 00:02.2 VGA compatible controller [0300]: Intel Corporqtion N10 Family 
Integrated Graphics Controller [8086:a011](Prog-if 00[VGA controller])
```

The version that I am using is 11.10.

If anybody can help me that would be great.

---

### Post by ercherramon on 2012-11-13
try with this:


```
sudo gedit /etc/default/pulseaudio
```

search the line:

```
PULSEAUDIO_SYSTEM_START=0
```

change for:

```
PULSEAUDIO_SYSTEM_START=1
```

and save the changes.

---

### Post by ercherramon on 2012-11-13
about xorg-video, try this:

```
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ohwii on 2012-11-13
Thanks for the reply! Unfortuneatly the editing of the pulseaudio file did not change it. it still freezes.

It says 
```
saned disabled: edit /etc/default/saned 

* Checking battery state...           [OK] 
```

I am in agony. :(

---

### Post by ercherramon on 2012-11-13
already tried reinstalling the drivers for your graphics chip?

try to do as you mentioned and commented how it went.

---

### Post by ercherramon on 2012-11-13
try to see if you have broken packages.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

commented how it went.

---

### Post by Ohwii on 2012-11-13
Thanks for the tipps. But no luck at all at one point I removed something and I couldnt do anythink. 
If you have any more tipps please let me know.

---

### Post by ercherramon on 2012-11-13
Well, of course, there is one last option that you can apply in your case. you can edit the grub. try with this command:

```
sudo gedit /etc/default/grub
```

search the line:

```
GRUB_CMDLINE_LINUX=""
```

and add these parameters:

```
GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"
```

save the changes and apply the command:

```
sudo update-grub
```

reboot the system and you comment how  went.

---

