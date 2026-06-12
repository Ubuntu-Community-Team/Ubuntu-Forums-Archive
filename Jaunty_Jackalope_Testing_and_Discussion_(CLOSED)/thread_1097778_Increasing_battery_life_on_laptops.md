---
title: "Increasing battery life on laptops"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-16
Ok, i recently installed jaunty 64 bit on my laptop after coming from arch, this is my first time using a 64 bit distro, and im not sure if my battery life problems are being caused by the fact that i AM using 64 bit, but i noticed that my battery life is significantly less then when i was using arch linux

on arch, it was a 32 bit distro, but my battery went down like 10 percent every 30 minutes: (even when i had my hard drive set to never spin down cause of the load cycle thing)

[[IMG]http://img220.imageshack.us/img220/3128/screenshot1m.th.png[/IMG]](http://img220.imageshack.us/img220/3128/screenshot1m.png)

but now, im going down almost 20 or more % every 30 minutes:

[[IMG]http://img440.imageshack.us/img440/3618/screenshotpowerhistory.th.png[/IMG]](http://img440.imageshack.us/img440/3618/screenshotpowerhistory.png)

so obviously in ubuntu there is something that is sucking down battery life, in both cases i have my cpu scaling set to conservative (so its 800 mhz) and my brightness down to the lowest setting. Are there any tips to maximizing battery life?

---

### Post by smbm on 2009-03-16
Have you tried installing and running powertop?

It should tell you what is using the most power and some tricks to try and reduce consumption.

---

### Post by Polygon on 2009-03-16
powertop doesn't really work as i have an amd processor, and it just tells me to disable hal polling or something which i don't want to do

and i didnt do anything that powertop told me to do on arch linux either, yet i get like an hour+ battery life more on arch then ubuntu.

---

### Post by smbm on 2009-03-16
I see, I'm not really sure what to do other that that.

Sorry I couldn't be more help.

Good luck though.

---

### Post by Kobalt on 2009-03-16
Do you run the exact sames processes/applications at launch than you did with Arch? It's a pretty minimalist (but very efficient) distro, I'm guessing Ubuntu runs more processes (such as Tracker search deamon) than Arch does...

---

### Post by ghindo on 2009-03-16
A bit off-topic, but could the OP please post his desktop background?  Thanks :)

---

### Post by pferraro on 2009-03-16
> **ghindo said:**
> A bit off-topic, but could the OP please post his desktop background?  Thanks :)

Install the gnome-backgrounds package. It's in there - using a custom background color.

---

### Post by Polygon on 2009-03-16
yeah its in the gnome supplied wallpapers, i didn't change it though, so i dunno what he means by custom background color.

anyway, i turned off all the non essential stuff in my startup programs in system > prefs > startup programs, is there any other place where i can look at the daemons/modules that get started up automatically?

and tracker is not installed by default anymore (no space on the disk) and it was never ENABLED by default (as it didnt index anything unless you told it to), and further more it never indexs stuff while on battery unless you tell it to.

other then that, i had very similar stuff, i had sound, wifi, CUPS, nvidia drivers, gnome, DBUS, im not sure what else could be running that is tanking my battery life....

---

### Post by smbm on 2009-03-16
You could install boot up manager (bum in the repos I think) to tell you which daemons are autostarting.

---

### Post by ernstblaauw on 2009-03-16
I think Ubuntu should have an energy-efficient laptop mode. This is the main advantage other OSes, like Windows, have over Ubuntu if the OS is used on a laptop. !

---

### Post by zerted on 2009-03-16
Something changed in 8.10 that greatly reduces the battery life from 8.04.  It does appear that whatever it was hasn't been fixed for 9.04.  An old topic about this is here: [http://ubuntuforums.org/showthread.php?t=991395](http://ubuntuforums.org/showthread.php?t=991395)

That topic has some info on helping to get some battery life back.

---

### Post by Changturkey on 2009-03-16
Well this sucks for mobile users. Netbooks too probably.

---

### Post by Polygon on 2009-03-16
> **ernstblaauw said:**
> I think Ubuntu should have an energy-efficient laptop mode. This is the main advantage other OSes, like Windows, have over Ubuntu if the OS is used on a laptop. !

windows does not have a laptop mode. All it does is prevent indexing and other intensive services from running on the battery, it doesn't stop other programs from running

ill try BUM

---

### Post by ernstblaauw on 2009-03-17
> **Polygon said:**
> windows does not have a laptop mode. All it does is prevent indexing and other intensive services from running on the battery, it doesn't stop other programs from running

ill try BUM

Comparing Windows XP SP3 and Ubuntu 8.10 on my laptop: 
- Windows XP almost reaches three hours on my laptop (actually 2:45). 
- Ubuntu never lasts longer than 2 hours. 

This means Windows is able to pull three quarters more out of the battery than Ubuntu. I don't know what the reason is, but I think it is a major disadvantage for Ubuntu.

---

### Post by scaine on 2009-03-17
Well, you started this thread a day ago, so this forum topic might be relevant :
[http://ubuntuforums.org/showthread.php?t=1098459](http://ubuntuforums.org/showthread.php?t=1098459)

Basically, CPU frequency scaling is now set to "Performance" by default, meaning that your CPU will not "stand down" when it's idle (unless you change it that is).

---

### Post by Polygon on 2009-03-17
yeah i know about that, when im on battery i set my cpu scaling to 'conservative' which basically means its supposed to scale up slower then on demand...but all i ever see it do is just sit at the lowest speed it can get (in my case, 800 mhz) so that isnt the problem

i tried powertop, and it gave me some suggestions (stop hal from polling the cd drive, enable SATA power save, increase dirty writeback time), i dunno if any of these do anything because they keep getting reset on a reboot. Is there a way i can make the change permanent to see if they actually do anything?

---

### Post by smbm on 2009-03-17
I used this thread on Hardy to implement the Powertop changes:

[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

For some reason it didn't work on Intrepid for me though.

I'll probably give it another try when Jaunty is released and has settle down a bit.

---

### Post by jslinux on 2009-03-17
opensuse and zenwalk (slackware based) both get at least a half hour longer battery life than ubuntu for me, 3hrs+ vs 2.5. XP about an hour or more. But in Ubuntu I have also noticed (as have others) a big inconsistency between what gnome power manager reports and what powertop reports, with the former showing less time. Perhaps there is an issue with gnome power manager making us think we have less power left than we actually do and causing power management events to happen earlier than necessary?

---

### Post by ernstblaauw on 2009-03-17
> **Polygon said:**
> yeah i know about that, when im on battery i set my cpu scaling to 'conservative' which basically means its supposed to scale up slower then on demand...but all i ever see it do is just sit at the lowest speed it can get (in my case, 800 mhz) so that isnt the problem

i tried powertop, and it gave me some suggestions (stop hal from polling the cd drive, enable SATA power save, increase dirty writeback time), i dunno if any of these do anything because they keep getting reset on a reboot. Is there a way i can make the change permanent to see if they actually do anything?

I have a script (called 99-blabla.sh) and copied it to /etc/pm/power.d and /etc/pm/sleep.d. I did make this using some copy and paste from others here on the forum (can't find the thread right now) and added some stuff from powertop:
```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  echo 0 > /proc/sys/vm/laptop_mode
  echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:02\:00.0/power_level
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
  modprobe gspca_main
  modprobe gspca_vc032x
  modprobe bluetooth
  modprobe rfcomm 
  modprobe l2cap
  modprobe btusb reset=1
  /etc/init.d/bluetooth start 
  hal-disable-polling --device /dev/cdrom --enable-polling
  echo 10 >/sys/devices/virtual/backlight/asus-laptop/brightness
    su ernstblaauw -c "DISPLAY=:0.0 compiz --replace &"
  # USB Bus power levels -> 2 = 2 seconds
  for i in /sys/bus/usb/devices/*/power/autosuspend
    do echo 2 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/*/power/level
    do echo on > $i
  done
 echo 6 > /sys/bus/pci/drivers/iwl3945/0000:02:00.0/power_level    
else
# Turn on aggressive power savings
  hdparm -B 1 -S 36 -M 128 /dev/sda
  mount -o remount,commit=600 /
  echo 5 > /proc/sys/vm/laptop_mode
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000\:02\:00.0/power_level
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 6000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  /etc/init.d/bluetooth stop 
  hciconfig hci0 down
  modprobe -r btusb
  modprobe -r gspca_vc032x
  modprobe -r gspca_main  
  modprobe -r bluetooth
  modprobe -r rfcomm
  modprobe -r l2cap
  hal-disable-polling --device /dev/cdrom
  echo 0 >/sys/devices/virtual/backlight/asus-laptop/brightness
  su ernstblaauw -c "DISPLAY=:0.0 metacity --replace &"
  # USB Bus power levels -> 2 = 2 seconds
  for i in /sys/bus/usb/devices/*/power/autosuspend
    do echo 1 > $i
  done
  # USB Bus power levels -> auto = autosupend
  for i in /sys/bus/usb/devices/*/power/level
    do echo auto > $i
  done
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:02:00.0/power_level    
fi

```

---

### Post by scaine on 2009-03-17
That's a cool script, although it's worth noting that it looks like it does *very* aggressive power saving, such as turning off bluetooth and fair bit of other stuff I don't even recognise.

For the time being, I'll stick with the stock build in order to help testing.  There's still a good chance stuff like this will be fixed before the Beta or release.

---

### Post by Polygon on 2009-03-25
sorry, life happened and i coulden't check this post

i noticed that if i implemented all of the stuff that powertop suggests, the interrupts per second go WAY down and i went like a hour using like 20% battery life (course i had wireless disabled and only using open office), but its a great improvement, so i will try that script

and i still don't understand why ubuntu starts bluetooth on startup, even when you don't even have any bluetooth hardware. Stuff like this needs to be fixed, along with just general power saving options in gnome

---

