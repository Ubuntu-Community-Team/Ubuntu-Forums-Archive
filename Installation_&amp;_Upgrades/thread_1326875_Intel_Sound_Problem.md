---
title: "Intel Sound Problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by smee56 on 2009-11-14
Hello all,

Having installed 9.10 (on a asus z99j)today the first problem I have run into is that my speakers and mic are not working.

I have looked at some tutorials on the forums, and still nothing is working.

Below is the information that i have come across so far, hope it helps, thanks in advance.



daniel@daniel-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1986A
Codec: Generic 1543 Si3054


daniel@daniel-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Intel Corporation 82801G (ICH7 Family) High Definition Audio

Please help as i could really do with some sound.

ps i am a noob so if you could dumb it down a little it would help.

---

### Post by ratansingh on 2009-11-15
I have same problem

---

### Post by feddozz on 2009-11-15
I just upgraded to 9.10 and I can't get any audio output.

---

### Post by kleeman on 2009-11-15
> **smee56 said:**
> Hello all,

Having installed 9.10 (on a asus z99j)today the first problem I have run into is that my speakers and mic are not working.

I have looked at some tutorials on the forums, and still nothing is working.

Below is the information that i have come across so far, hope it helps, thanks in advance.



daniel@daniel-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1986A
Codec: Generic 1543 Si3054


daniel@daniel-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Intel Corporation 82801G (ICH7 Family) High Definition Audio

Please help as i could really do with some sound.

ps i am a noob so if you could dumb it down a little it would help.

I was just debugging a similar soundcard and it appears you may need to add some options to the file /etc/modprobe.d/alsa-base.conf

This thread kind of explains it:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

open the above file as root:

gksu gedit /etc/modprobe.d/alsa-base.conf

Look at the bottom of the file for a line like 

options snd-hda-intel

and at the end of this line add the following

position_fix=1 model=3stack

save the file

and reboot. If that doesn't work remove the "position_fix=1" piece above from the file I mentioned and try again. Also make sure that your mixer controls are OK i.e. not muted). In a terminal type

alsamixer

and use the arrow keys to move across looking at all the sliders and unmuting any that look relevant.

---

### Post by smee56 on 2009-11-15
Can you please advise on what one to add the following line onto


options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N



EDIT: Looking at the first post where the command "cat /proc/asound/card0/codec#* | grep Codec" was used, gave the return Codec: Analog Devices AD1986A
Codec: Generic 1543 Si3054
why arnt these devices turning up as something like Intel HDA then number?

---

### Post by kleeman on 2009-11-15
Add them at the end of the last line which will become

options snd-hda-intel power_save=10 power_save_controller=N position_fix=1 model=3stack

Edit: The solution was in this thread:

[http://ubuntuforums.org/showthread.php?t=231032](http://ubuntuforums.org/showthread.php?t=231032)

I googled 

AD1986A hda options

because that is your codec.....

---

