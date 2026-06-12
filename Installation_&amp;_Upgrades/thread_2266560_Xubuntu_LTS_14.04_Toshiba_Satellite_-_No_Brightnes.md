---
title: "Xubuntu LTS 14.04 Toshiba Satellite - No Brightness control"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by kotelyan on 2015-02-23
Just installed Xubuntu LTS 14.04 on the new Toshiba Satellite C75D-B. 
Running Xfce.
Brightness control is not working.
Slider control on Brightness Plugin moves, but does not result in any brightness change. it looks like it is at maximum.

I checked this thread <http://ubuntuforums.org/showthread.php?t=2216428&page=2>, but it seems like my case is different.

cat /sys/class/backlight/acpi_video0/brightness

shows that moving the slide does change the value in the file.

---

### Post by tgalati4 on 2015-02-23
Install *acpitool*.  Open a terminal:

```
sudo apt-get install acpitool
```

> 
       -l x   Set  LCD  brightness  level  to  x, where x is in the range 0..7. Works only on Toshiba and IBM Thinkpad laptops.  Requires write access to
              /proc/acpi/tochiba/lcd or /proc/acpi/ibm/brightness
              Illegal values for x will result in the value being set to either 0 or 7.


Try using:

```
sudo acpitool -l 7
sudo acpitool -l 3
```

It's possible that you just need read access to the LED state variable:

```
sudo chmod 777 /sys/class/backlight/acpi_video0/brightness
```

---

### Post by kotelyan on 2015-02-24
I have tried that. acpitools was installed already, but I re-installed it just in case. It Didn't help. 
I am getting the message that file [COLOR=#000000]*/proc/acpi/tochiba/lcd*[/COLOR] does not exist.[COLOR=#000000]* *[/COLOR]

I can write into [COLOR=#000000][FONT=Ubuntu Mono]/sys/class/backlight/acpi_video0/brightness [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]and in fact, when I move the slide in Brightness Plugin - the value does indeed change.

---

### Post by kotelyan on 2015-02-24
Thanks, acpitool was already installed, I re-installed it just in case, here is what I get:
   sudo acpitool -l 7  
Could not open file : /proc/acpi/toshiba/lcd  
You must have write access to /proc/acpi/toshiba/lcd to change the LCD brightness level.  
Or ensure yourself you are running a kernel with Toshiba ACPI support enabled.    

It turns out there is a folder /proc/acpi, but no such file - /proc/acpi/toshiba/lcd  :-( 

 ls /proc/acpi 
ac_adapter  battery  button  toshiba  wakeup

---

