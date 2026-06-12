---
title: "Lucid Power saving"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jochem on 2010-03-29
I've got an acer 1810tz of the timeline series. They should have high battery time. Using windows, my battery time seems to be quite longer than when I'm using Ubuntu.

I've found a few posts about power management, but I'm not sure if they are still up to date and usable.

A post about power management under Karmic, using my laptop model.
[http://forum.notebookreview.com/showthread.php?t=434638](http://forum.notebookreview.com/showthread.php?t=434638)

Ubuntu power saving in general.
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

I don't know which of these settings apply to Lucid, how good should the default power saving settings be?

I've also tried powertop, it suggests several things.

```
jochem@jochem-laptop:~$ sudo powertop -d
[sudo] password for jochem: 
PowerTOP 1.12   (C) 2007, 2008 Intel Corporation 

Collecting data for 15 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.4%)
polling		  0.0ms ( 0.0%)
C1 mwait	  0.0ms ( 0.0%)
C4 mwait	  9.4ms (99.6%)
P-states (frequencies)
  1300 Mhz     0.0%
  1200 Mhz   100.0%
Wakeups-from-idle per second : 107.1	interval: 15.0s
no ACPI power usage estimate available
Top causes for wakeups:
  31.7% ( 30.7)   [kernel scheduler] Load balancing tick
  26.1% ( 25.3)   [iwlagn] <interrupt>
  11.5% ( 11.1)   [extra timer interrupt]
   0.0% (  0.0)D  flush-8:0
   5.2% (  5.0)   syndaemon
   5.0% (  4.9)   [ahci] <interrupt>
   3.4% (  3.3)   [acpi] <interrupt>
   2.5% (  2.4)   [kernel core] hrtimer_start (tick_sched_timer)
   2.1% (  2.1)   multiload-apple
   2.1% (  2.1)   gnome-terminal
   2.1% (  2.0)   indicator-apple
   1.9% (  1.9)   [i915] <interrupt>
   1.4% (  1.4)   Xorg
   1.0% (  1.0)   gvfs-afc-volume
   1.0% (  0.9)   events/0
   0.6% (  0.6)   [HDA Intel] <interrupt>
   0.4% (  0.4)   [kernel core] inc_rt_group (sched_rt_period_timer)
   0.3% (  0.3)   clock-applet
   0.3% (  0.3)   rtkit-daemon
   0.3% (  0.3)   gnome-settings-
   0.2% (  0.2)   pulseaudio
   0.1% (  0.1)   upowerd
   0.1% (  0.1)   NetworkManager
   0.1% (  0.1)   PS/2 keyboard/mouse/touchpad interrupt
   0.1% (  0.1)   [Function call interrupts] <kernel IPI>
   0.1% (  0.1)   avahi-daemon
   0.1% (  0.1)   gnome-power-man
   0.1% (  0.1)   kerneloops
   0.1% (  0.1)   [kernel core] add_timer (sta_info_cleanup)
   0.1% (  0.1)   gnome-panel
   0.1% (  0.1)   [kernel core] inet_twdr_hangman (inet_twdr_hangman)

An audio device is active 100.0% of the time:
hwC0D0 Realtek ALC269 

A USB device is active 100.0% of the time:
USB device  2-5 : WebCam (SuYin)

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

Recent USB suspend statistics
Active  Device name
100.0%	USB device  2-5 : WebCam (SuYin)
  0.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.32-17-generic uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.32-17-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.32-17-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.32-17-generic uhci_hcd)
100.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.32-17-generic ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.32-17-generic ehci_hcd)

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 Realtek ALC269 
100.0%	hwC0D1 Intel G45 DEVCTG
```

Wireless power saving using the suggested command "iwconfig wlan0 power timeout 500ms" doesn't work properly, it doesn't "sacrifice network performance slightly to save power", it sacrefices my network performance greatly! I have to wait like 5 seconds before each web search.

I don't want to end up installing random scripts, that do not even apply to lucid. Could anyone get me into the right direction? I would be so happy! :)

---

### Post by jochem on 2010-03-29
Today I've used windows while studying in the library, because of longer battery time :-(

---

### Post by xfalcox on 2010-03-29
Here on Asus 1000ha, i use the Eeepc-acpi tray who let me shutdown things like wifi or webcam.

You can dim your lcd backligth too, and enable stop spinning disk on power preferences.

---

### Post by zoomy942 on 2010-03-29
i always used this set of tips. 

[http://ubuntuforums.org/showpost.php?p=7271995&postcount=7]("http://ubuntuforums.org/showpost.php?p=7271995&postcount=7")

---

### Post by Ibidem on 2010-03-29
Acer Aspire 1 here, 3-cell w/ i945 graphics, Suyin webcam, Realtek ethernet, AR5007 wireless.
The webcam is the biggest battery eater.  For some reason, I have not been able to find a GUI way to turn it off.  I *never* use it, so I just uninstalled xorg-video-v4l (or something like that).  That provides the driver.  But it seems to still be pulling power...
Powertop to suspend improves battery life.

I use cpufreqd (with extensive customization) for the cpu; ondemand governor

Figure out how to control the fan (start temp >60 deg if you dare, 70 is high, stop at least 5 deg. lower)--it should be acerhdf (check w/ lsmod|grep acer), here's my /etc/modprobe.d/acerhdf.conf:```

# fan control for acer aspire one fan
# according to: http://piie.net/files/acerhdf_README.txt
# check status with: dmesg|grep acerhdf
# read temperature with: cat /sys/class/thermal/thermal_zone0/temp
options acerhdf interval=5 fanon=61000 fanoff=53000 kernelmode=1
```

Intel's suggestions for the graphics-
Low brightness, enable screen compression (I think it's on by default), use a background w/ few changes in a given horizontal line (more compressible screen data->less bus bandwidth->less power usage, per Intel)

sudo ifconfig eth0 down
sudo modprobe -r <ethernet driver>
to eliminate the ethernet's pull on power.
(to restore ethernet-
sudo modprobe <ethernet driver>
sudo ifconfig eth0 up)

hdparm is supposed to help
Wireless--any change will cost you in performance

If you dare, disable usb (howto is in [here]("http://ubuntuforums.org/showthread.php?t=847773"))...

Note that Firefox sucks juice; likewise for Flash, video, probably Mutter (default in ubuntu-netbook)/ any compositing;
Mono got eradicated from ubuntu-netbook because it takes too much battery.
@zoomy942-Thanks for that link.

Ibidem

---

### Post by zoomy942 on 2010-03-30
for your webcam, cant you diable it in the bios?

---

### Post by jochem on 2010-03-30
Thanks everyone, I think my battery time increased, I'm on ~8W now.

Here is my pm-powersave file, I'm not sure if everything works, but at least it's noticibly better than before (/etc/pm/power.d/15_saving, it's made executable)

I disabled wireless power saving, since it crippled my wireless.

```
#!/bin/sh
  # Make sure brightness switch enabled stays on N, even on resume.
  echo N > /sys/module/video/parameters/brightness_switch_enabled
  # Disable wake on lan
  ethtool -s eth0 wol d

  #turning off bluetooth related thingies
  modprobe -r rfcommp
  modprobe -r l2cap
  modprobe -r bluetooth

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then


  # Set the drive to mostly stay awake.  Some may want to change -B 200
  # to -B 255 to avoid accumulating Load_Cycle_Counts
  # -S 240 => put in standby after 20 minutes idle
  # -B 200 => do not permit spindown
  # -M => not supported by my drive
  hdparm -B 200 -S 240 /dev/sda


  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds. This reduces disk activity.
  mount -o remount,commit=5,atime,diratime /
  mount -o remount,commit=5,atime,diratime /home

 # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Set SATA back to normal operation
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy;
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Manually set the wifi driver to no power savings.
  # broken in 2.6.31 kernel
  #iwconfig wlan0 power off

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

  # Disable Intel HD audio power saving:
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

  # PCI Express power savings
  echo powersave > /sys/module/pcie_aspm/parameters/policy

  #usb
  modprobe usbhid

   # Enable the webcam driver
  modprobe uvcvideo

  #ethenet
  modprobe atl1c
  ifconfig eth0 up



else # Save power
  
  # Set the disks to aggressively save power.
  # Some might find these settings too aggressive.  If so, change
  # "-S 4" to something larger like -S 24 (two minutes) and -B 1 to -B 255.
  # -S 4 => put in standby after 20 seconds idle
  # -B 1 => highest degree of power savings
  # -M => not supported by my drive
  hdparm -B 1 -S 4 /dev/sda

  # Change the ext3 commit times to 10 minutes.  Reduces disk activity
  # disable disk writes when reading
  mount -o remount,commit=600,noatime,nodiratime /
  mount -o remount,commit=600,noatime,nodiratime /home
  
 # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Set SATA to save power
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy;
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Manually set the iwl3945 driver to power savings.
  # broken in 2.6.31 kernel
  #iwconfig wlan0 power timeout 100ms

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Enable Intel HD audio power saving:
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

 
  # PCI Express power savings off
  echo default > /sys/module/pcie_aspm/parameters/policy

  # Remove the webcam driver
  modprobe -r uvcvideo

  #usb
  modprobe -r usbhid
	
  #ethenet
  ifconfig eth0 down
  modprobe -r atl1c

fi
```

---

### Post by DLGandalf on 2010-03-31
usbhid hasn't been a kernel module since jaunty I believe

---

### Post by Lampi on 2010-04-04
Does someone know a command, a sysfs file or a proc file to examine whether a drive is sleeping or not?

I noticed hddtemp does stop temperature checks if the drive is asleep - you can test that with:

```
hddtemp /dev/sda
```
In case sda is asleep you won't get a temperature report, but a notice like: "sda: drive is sleeping"

I wonder how hddtemp does that? Id'like to write a fews daemon shell scripts - they should check the drive's sleeping state as well first hand, to make sure the drive does not wake up.

[Edit] found it: hdparm -C /dev/sda

---

### Post by Axx83 on 2010-04-10
Jochem, honestly you're using old scripts with VERY redundant commands that lucid has already in place.

Instead of putting up with home made scripts that do weird mostly untested (with lucid of course) things why don't you go a much simpler way?

here:
[http://ubuntuforums.org/showthread.php?t=1326333](http://ubuntuforums.org/showthread.php?t=1326333)

ONLY read the part that says USB AUTOSUSPEND, do the things that are written in the post in that section and try unplugging the cable and running powertop now and let me know if things improved.

Ah and REMOVE that script you just installed before doing this, hear from you later.

---

### Post by jochem on 2010-04-14
I don't like homemade scripts, but I had to try something, but I'd like my battery time to be as long as when I'm using windows. Without any extra scripts, I get around 4,5-5 hours, 6 under windows.

I did notice battery time improvement using the script, so I don't think all of the settings are redundant. But you're right, even if they do improve battery life, they're probably not tested :( Which of the commands are redundant?

```
jochem@jochem-laptop:~$ sudo powertop -d
PowerTOP 1.12   (C) 2007, 2008 Intel Corporation 

Collecting data for 15 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.8%)
polling		  0.0ms ( 0.0%)
C1 mwait	  0.1ms ( 0.0%)
C4 mwait	  7.6ms (99.2%)
P-states (frequencies)
  1300 Mhz     0.0%
  1200 Mhz   100.0%
Disk accesses:
Wakeups-from-idle per second : 132.6	interval: 15.0s
no ACPI power usage estimate available
Top causes for wakeups:
  29.3% ( 31.6)   [kernel scheduler] Load balancing tick
  28.0% ( 30.2)   [iwlagn] <interrupt>
  10.3% ( 11.1)   [extra timer interrupt]
   5.4% (  5.9)   [i915] <interrupt>
   4.8% (  5.2)   [acpi] <interrupt>
   4.6% (  5.0)   syndaemon
   2.5% (  2.7)   [ahci] <interrupt>
   2.3% (  2.5)   [kernel core] hrtimer_start (tick_sched_timer)
   1.9% (  2.1)   gnome-terminal
   1.9% (  2.0)   multiload-apple
   1.1% (  1.1)   Xorg
   1.0% (  1.1)   events/0
   0.9% (  1.0)   gvfs-afc-volume
   0.7% (  0.8)   compiz
   0.6% (  0.6)   [Function call interrupts] <kernel IPI>
   0.6% (  0.6)   sensors-applet
   0.4% (  0.5)   update-notifier
   0.2% (  0.3)   [kernel core] inc_rt_group (sched_rt_period_timer)
   0.2% (  0.3)   gnome-settings-
   0.2% (  0.3)   nautilus
   0.2% (  0.3)   clock-applet
   0.2% (  0.2)   [Rescheduling interrupts] <kernel IPI>
   0.2% (  0.2)   NetworkManager
   0.2% (  0.2)   rtkit-daemon
   0.1% (  0.1)   gnome-power-man
   0.1% (  0.1)   events/1
   0.1% (  0.1)   [kernel core] add_timer (sta_info_cleanup)
   0.1% (  0.1)   PS/2 keyboard/mouse/touchpad interrupt
   0.1% (  0.1)   flush-1:0
   0.1% (  0.1)   flush-1:5
   0.1% (  0.1)   bdi-default
   0.1% (  0.1)   flush-1:13
   0.1% (  0.1)   flush-1:11
   0.1% (  0.1)   flush-1:1
   0.1% (  0.1)   flush-1:12
   0.1% (  0.1)   flush-1:8
   0.1% (  0.1)   flush-1:3
   0.1% (  0.1)   flush-1:10
   0.1% (  0.1)   flush-1:9
   0.1% (  0.1)   flush-1:6
   0.1% (  0.1)   flush-1:4
   0.1% (  0.1)   flush-1:2
   0.1% (  0.1)   flush-1:15
   0.1% (  0.1)   flush-1:14
   0.1% (  0.1)   flush-1:7
   0.1% (  0.1)   flush-8:0
   0.1% (  0.1)   upowerd
   0.1% (  0.1)   kerneloops
   0.1% (  0.1)   khungtaskd
   0.1% (  0.1)   [kernel core] add_timer (addrconf_verify)

An audio device is active 100.0% of the time:
hwC0D0 Realtek ALC269 

A USB device is active 100.0% of the time:
USB device  2-5 : WebCam (SuYin)

Suggestion: Enable USB autosuspend for non-input devices by pressing the U key


Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

Recent USB suspend statistics
Active  Device name
100.0%	USB device  2-5 : WebCam (SuYin)
  0.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
100.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 Realtek ALC269 
100.0%	hwC0D1 Intel G45 DEVCTG 

Recent SATA AHCI link activity statistics
Active	Partial	Slumber	Device name

```

I'm not sure what the usb_autosuspend did lol

---

### Post by Axx83 on 2010-04-14
It looks as the cable was plugged. Anyway is it a new installation of Lucid ?

Remove the script you took from the forum (the messy one) install only the usbautosuspend script in my guide, just as explained, restart system (so that all variables are back to default), then UNPLUG the cable.

Run this powertop command:

sudo powertop -d -t 120

it will go blank for exactly 2 minutes and record all data then put it on screen.

Write back these infos.

---

### Post by jochem on 2010-04-14
```
jochem@jochem-laptop:~$ sudo powertop -d -t 120
[sudo] password for jochem: 
PowerTOP 1.12   (C) 2007, 2008 Intel Corporation 

Collecting data for 120 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.5%)
polling		  0.0ms ( 0.0%)
C1 mwait	  0.4ms ( 0.0%)
C4 mwait	 13.2ms (99.5%)
P-states (frequencies)
  1300 Mhz     0.0%
  1200 Mhz   100.0%
Disk accesses:
The application 'flush-8:0' is writing to file 'wtmp' on /dev/sda5
The application 'flush-8:0' is writing to file 'home-3306fb61.log' on /dev/sda5
The application 'flush-8:0' is writing to file '?' on /dev/sda5
The application 'flush-8:0' is writing to file 'index' on /dev/sda5
The application 'flush-8:0' is writing to file 'data_0' on /dev/sda5
The application 'flush-8:0' is writing to file 'data_1' on /dev/sda5
The application 'flush-8:0' is writing to file 'data_1' on /dev/sda5
The application 'flush-8:0' is writing to file 'Current Session' on /dev/sda5
The application 'flush-8:0' is writing to file 'messages' on /dev/sda5
The application 'flush-8:0' is writing to file 'f_000215' on /dev/sda5
The application 'flush-8:0' is writing to file 'f_000216' on /dev/sda5
The application 'flush-8:0' is writing to file 'f_000217' on /dev/sda5
The application 'flush-8:0' is writing to file 'Current Tabs' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
Wakeups-from-idle per second : 75.7	interval: 120.0s
Power usage (ACPI estimate): 9.7W (4.4 hours) 
Top causes for wakeups:
  32.3% ( 25.5)   [iwlagn] <interrupt>
  26.8% ( 21.1)   [kernel scheduler] Load balancing tick
   0.1% (  0.1)D  rsyslogd
   8.7% (  6.9)   [extra timer interrupt]
   0.0% (  0.0)D  flush-8:0
   6.3% (  5.0)   syndaemon
   4.8% (  3.8)   [i915] <interrupt>
   4.2% (  3.3)   [acpi] <interrupt>
   2.5% (  2.0)   multiload-apple
   2.5% (  1.9)   gnome-terminal
   2.4% (  1.9)   [kernel core] hrtimer_start (tick_sched_timer)
   1.8% (  1.4)   [ahci] <interrupt>
   1.6% (  1.3)   Xorg
   1.4% (  1.1)   events/0
   1.3% (  1.0)   gvfs-afc-volume
   0.6% (  0.5)   update-notifier
   0.3% (  0.3)   clock-applet
   0.3% (  0.2)   gnome-settings-
   0.3% (  0.2)   [kernel core] inc_rt_group (sched_rt_period_timer)
   0.3% (  0.2)   rtkit-daemon
   0.2% (  0.2)   NetworkManager
   0.2% (  0.1)   gnome-power-man
   0.1% (  0.1)   ssh-agent
   0.1% (  0.1)   kerneloops
   0.1% (  0.1)   [kernel core] add_timer (sta_info_cleanup)
   0.1% (  0.1)   [kernel core] inet_twdr_hangman (inet_twdr_hangman)
   0.1% (  0.1)   upowerd
   0.1% (  0.0)   avahi-daemon
   0.0% (  0.0)   winbindd
   0.0% (  0.0)   [Rescheduling interrupts] <kernel IPI>
   0.0% (  0.0)   phy0
   0.0% (  0.0)   aptd
   0.0% (  0.0)   [kernel core] neigh_timer_handler (neigh_timer_handler)
   0.0% (  0.0)   gconfd-2
   0.0% (  0.0)   jbd2/sda5-8
   0.0% (  0.0)   cron
   0.0% (  0.0)   [kernel core] neigh_add_timer (neigh_timer_handler)
   0.0% (  0.0)   PS/2 keyboard/mouse/touchpad interrupt
   0.0% (  0.0)   [TLB shootdowns] <kernel IPI>
   0.0% (  0.0)   indicator-apple
   0.0% (  0.0)   [kernel core] ieee80211_sta_rx_notify (ieee80211_sta_conn_mon_timer)
   0.0% (  0.0)   compiz
   0.0% (  0.0)   flush-1:0
   0.0% (  0.0)   flush-1:1
   0.0% (  0.0)   flush-1:14
   0.0% (  0.0)   flush-1:6
   0.0% (  0.0)   flush-1:10
   0.0% (  0.0)   flush-1:9
   0.0% (  0.0)   flush-1:8
   0.0% (  0.0)   flush-1:2

An audio device is active 100.0% of the time:
hwC0D1 Intel G45 DEVCTG 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'Current Tabs' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'f_000217' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'f_000216' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'f_000215' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'Current Session' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'data_1' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'data_1' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'data_0' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'index' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'home-3306fb61.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'flush-8:0' is writing to file 'wtmp' on /dev/sda5.
This prevents the disk from going to powersave mode.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device  2-5 : WebCam (SuYin)
  0.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 Realtek ALC269 
100.0%	hwC0D1 Intel G45 DEVCTG 

Recent SATA AHCI link activity statistics
Active	Partial	Slumber	Device name

```

and another one:

```
jochem@jochem-laptop:~$ sudo powertop -d -t 120
PowerTOP 1.12   (C) 2007, 2008 Intel Corporation 

Collecting data for 120 seconds 


Cn	          Avg residency
C0 (cpu running)        ( 0.4%)
polling		  0.0ms ( 0.0%)
C1 mwait	  0.1ms ( 0.0%)
C4 mwait	 13.2ms (99.6%)
P-states (frequencies)
  1300 Mhz     0.0%
  1200 Mhz   100.0%
Disk accesses:
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'rsyslogd' is writing to file 'messages' on /dev/sda5
The application 'gvfsd-metadata' is writing to file 'home-918645e5.log.XQXXAV' on /dev/sda5
The application 'gvfsd-metadata' is writing to file 'home-918645e5.log.XQXXAV' on /dev/sda5
The application 'gvfsd-metadata' is writing to file '?' on /dev/sda5
The application 'gvfsd-metadata' is writing to file '?' on /dev/sda5
The application 'gconfd-2' is writing to file '%gconf.xml.new' on /dev/sda5
The application 'gconfd-2' is writing to file '%gconf.xml.new' on /dev/sda5
The application 'gconfd-2' is writing to file '?' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'syslog' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
The application 'rsyslogd' is writing to file 'kern.log' on /dev/sda5
Wakeups-from-idle per second : 75.6	interval: 120.0s
Power usage (ACPI estimate): 10.6W (3.9 hours) 
Top causes for wakeups:
  35.3% ( 28.0)   [iwlagn] <interrupt>
  25.7% ( 20.4)   [kernel scheduler] Load balancing tick
   0.1% (  0.1)D  rsyslogd
   6.3% (  5.0)   syndaemon
   6.1% (  4.8)   [extra timer interrupt]
   4.9% (  3.8)   [i915] <interrupt>
   4.2% (  3.3)   [acpi] <interrupt>
   2.5% (  2.0)   multiload-apple
   2.5% (  2.0)   [kernel core] hrtimer_start (tick_sched_timer)
   2.5% (  1.9)   gnome-terminal
   0.0% (  0.0)D  gvfsd-metadata
   1.9% (  1.5)   [ahci] <interrupt>
   1.7% (  1.3)   Xorg
   0.1% (  0.0)D  gconfd-2
   1.4% (  1.1)   events/0
   1.3% (  1.0)   gvfs-afc-volume
   0.6% (  0.5)   update-notifier
   0.4% (  0.3)   compiz
   0.3% (  0.3)   clock-applet
   0.3% (  0.2)   gnome-settings-
   0.3% (  0.2)   nautilus
   0.3% (  0.2)   [kernel core] inc_rt_group (sched_rt_period_timer)
   0.3% (  0.2)   rtkit-daemon
   0.2% (  0.2)   NetworkManager
   0.2% (  0.1)   gnome-power-man
   0.1% (  0.1)   [kernel core] add_timer (sta_info_cleanup)
   0.1% (  0.1)   ssh-agent
   0.1% (  0.1)   kerneloops
   0.1% (  0.1)   upowerd
   0.1% (  0.0)   phy0
   0.0% (  0.0)   [kernel core] ieee80211_sta_rx_notify (ieee80211_sta_conn_mon_timer)
   0.0% (  0.0)   [kernel core] inet_twdr_hangman (inet_twdr_hangman)
   0.0% (  0.0)   winbindd
   0.0% (  0.0)   jbd2/sda5-8
   0.0% (  0.0)   [kernel core] sk_reset_timer (tcp_write_timer)
   0.0% (  0.0)   [kernel core] neigh_add_timer (neigh_timer_handler)
   0.0% (  0.0)   cron
   0.0% (  0.0)   [kernel core] arm_supers_timer (sync_supers_timer_fn)
   0.0% (  0.0)   PS/2 keyboard/mouse/touchpad interrupt
   0.0% (  0.0)   [TLB shootdowns] <kernel IPI>
   0.0% (  0.0)   gnome-screensav
   0.0% (  0.0)   gnome-panel
   0.0% (  0.0)   [kernel core] add_timer (peer_check_expire)
   0.0% (  0.0)   bdi-default
   0.0% (  0.0)   flush-8:0

An audio device is active 100.0% of the time:
hwC0D1 Intel G45 DEVCTG 

Suggestion: Enable SATA ALPM link power management via: 
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Suggestion: Enable wireless power saving mode by executing the following command:
  iwconfig wlan0 power timeout 500ms
This will sacrifice network performance slightly to save power.

Suggestion: enable HD audio powersave mode by executing the following command:
   echo 1 > /sys/module/snd_hda_intel/parameters/power_save 
or by passing power_save=1 as module parameter.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'gconfd-2' is writing to file '%gconf.xml.new' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'gconfd-2' is writing to file '%gconf.xml.new' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'gvfsd-metadata' is writing to file 'home-918645e5.log.XQXXAV' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'gvfsd-metadata' is writing to file 'home-918645e5.log.XQXXAV' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'messages' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'kern.log' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

The program 'rsyslogd' is writing to file 'syslog' on /dev/sda5.
This prevents the disk from going to powersave mode.

Recent USB suspend statistics
Active  Device name
  0.0%	USB device  2-5 : WebCam (SuYin)
  0.0%	USB device usb6 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb5 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb4 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb3 : UHCI Host Controller (Linux 2.6.32-20-generic uhci_hcd)
  0.0%	USB device usb2 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)
  0.0%	USB device usb1 : EHCI Host Controller (Linux 2.6.32-20-generic ehci_hcd)

Recent audio activity statistics
Active  Device name
100.0%	hwC0D0 Realtek ALC269 
100.0%	hwC0D1 Intel G45 DEVCTG 

Recent SATA AHCI link activity statistics
Active	Partial	Slumber	Device name

```

---

### Post by xir_ on 2010-04-14
i have a timeline. The best thing i did was update the bios, that reduced my consumption by 2 watts (by introducing a 800mhz p state).

Choice of programs is very important. For instance using chrome will wake the cpu up a lot (from my experience). Also you could try something like crunch-bang as it should be lighter on resources.

Also try to not use the touch-pad as it wakes up the cpu a lot from c0.

---

### Post by jochem on 2010-04-14
I'm using bios version v1.3310, the latest afaik.
I'm using the touchpad 90% of the time, so not using isn't an option I guess...
And I really like chrome/chromium ;)

---

### Post by PatrickVogeli on 2010-04-14
> **Axx83 said:**
> Jochem, honestly you're using old scripts with VERY redundant commands that lucid has already in place.

Instead of putting up with home made scripts that do weird mostly untested (with lucid of course) things why don't you go a much simpler way?

here:
[http://ubuntuforums.org/showthread.php?t=1326333](http://ubuntuforums.org/showthread.php?t=1326333)

ONLY read the part that says USB AUTOSUSPEND, do the things that are written in the post in that section and try unplugging the cable and running powertop now and let me know if things improved.

Ah and REMOVE that script you just installed before doing this, hear from you later.

Hey Boss.. Usb autosuspend, great tip. Specially when I believe since Jauny those are the default values..:popcorn:

Calm down a little and stop thinking you know the absolute truth.

---

### Post by jochem on 2010-04-14
> **PatrickVogeli said:**
> Hey Boss.. Usb autosuspend, great tip. Specially when I believe since Jauny those are the default values..:popcorn:

Calm down a little and stop thinking you know the absolute truth.

Hello PatrickVogeli, as you've probably noticed, I used your script (and added a few things that probably won't do anything :D). Does it work with lucid like it does with Karmic?

---

### Post by xir_ on 2010-04-14
> **jochem said:**
> I'm using bios version v1.3310, the latest afaik.
I'm using the touchpad 90% of the time, so not using isn't an option I guess...
And I really like chrome/chromium ;)

then you and i are cut from the same cloth.

I'm going to try to see if its possible to increase ram caching so that the hard drive can sleep more.

I even posted this as an issue on mark shuttleworths blog. I think it would be great to make linux the greenest operating system. What a selling point that would be.

---

### Post by Axx83 on 2010-04-14
I'm not a programmer and I don't know a lot about scripts. I simply look at the code, look at what powertop tells me and what are the scripts that comes as default with every version of ubuntu (pm-utils scripts).

I'm not a boss and I don't know no truth. But I am right when I add the autosuspend script that turns to autosuspend all the usb ports that don't automatically go in that state when you unplug ac (webcam as an example). 

Powertop clearly shows the difference.

Most of the commands in the scripts I was referring to are indeed redundant or overcome default scripts that comes with Lucid, whether the latter are less efficient than those...it depends, surely they are safer.

And sorry but I DO think that Ubuntu's programmer know a little bit more than the average guy that writes here.

This is a forum to help people, sarcasms is a great thing in real life, here usually it's misinterpreted and only brings bad feelings. Avoid it.

Calm down.

---

### Post by Axx83 on 2010-04-14
Oh about the real issue. My father has a timeline, don't remember what model. The processor is an intel SU-something, a core 2 solo ultra low voltage anyway, the lowest mhz is 800 and it lasts 6 hours, the battery is a 6 cell. Maybe it's a close model maybe not, but I think it should normally go down to 800.

---

### Post by PatrickVogeli on 2010-04-14
I have an Acer 1810TZ and I think I have some tips for you.

First, forget about putting the scripts in /etc/pm/power.d or sleep.d. Currently, lucid is a bit broken in our machine, and it won't work that way.

Second, don't mess with hdparm and so on. Lucid already does that.

I'm using the script below:

```

#!/bin/sh

  # Acer 1810tz specific brightness key fix
  echo N > /sys/module/video/parameters/brightness_switch_enabled
  # Disable wake on lan
  ethtool -s eth0 wol d

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=30,atime,diratime /
  mount -o remount,commit=30,atime,diratime /home

  # Disable SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Set the Intel wifi to no power savings.
  iwconfig wlan0 power off

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo N > /sys/module/snd_hda_intel/parameters/power_save_controller
else # Save power
  
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600,noatime,nodiratime /
  mount -o remount,commit=600,noatime,nodiratime /home

  # Enable SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Set the intel wlan to save power
  iwconfig wlan0 power on

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
  
  # Put down the controller when not in use
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
fi

```

To use it:

```

sudo chmod +x script_name
sudo cp script_name /etc/pm
gksudo gedit /etc/acpi/power.sh

```
Now, edit the file and, below #!/bin/sh put /etc/pm/script_name

The script will now execute when it detects a change in the power state. However, it will run more than one time, but that shouldn't harm.

I've also put up the following script to check if the settings are bein applied:
```

#!/bin/sh

  echo "\nThis script will output various Power Saving parameter and some system info:"
  echo "It is meant to help debuging power management issues"
  echo "By patrick.voegeli at gmail dot com"
  
  echo "\nRunning kernel info:"
  echo "\tKernel version: `uname -r`"
  echo "\tArchitecture: `uname -m`"
  echo "----------------------------------"
  
  echo "\nPower management scripts:"
  echo "/etc/pm/sleep.d/ files and attributes:"
  echo "\t`ls -la /etc/pm/sleep.d/`"
  echo "/etc/pm/power.d/ files and attributes:"
  echo "\t`ls -la /etc/pm/power.d/`"
  echo "----------------------------------"
  
  echo "\nLaptop is running on battery?:"
  if ( $(on_ac_power) )
  then
    echo "\tNo"
  else
    echo "\tYes"
  fi
  echo "----------------------------------"
  
  echo "\nAcpi output:"
  echo "\t`acpi -a`"
  echo "\t`acpi -b`"
  echo "----------------------------------"
  
  echo "\nSata power saving:" 
  echo "Expected result: min_power (not all of them)"
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo "\t`cat $foo`";
  done
  echo "----------------------------------"
  
  echo "\nWireless power saving:"
  echo "Expected result: On"
  echo "`iwconfig wlan0 | grep "Power Management"`"
  echo "----------------------------------"
  
  echo "\nLower file system access:"
  echo "Expected results: 90 1 6000 "
  echo "\tDirty ratio: `cat /proc/sys/vm/dirty_ratio`"
  echo "\tDirty background ratio: `cat /proc/sys/vm/dirty_background_ratio`"
  echo "\tDirty writeback centisecs: `cat /proc/sys/vm/dirty_writeback_centisecs`"
  echo "----------------------------------"
  
  echo "\nFilesystem mount options:"
  echo "Expected results include: noatime,nodiratime,commit=600"
  echo "\tRoot: `cat /etc/mtab | grep "/ ext"`"
  echo "\tHome: `cat /etc/mtab | grep "/home ext"`"
  echo "----------------------------------"
  
  echo "\nIntel HD Audio:"
  echo "Expected result: 10 Y"
  echo "\tSeconds before putting the controller down: `cat /sys/module/snd_hda_intel/parameters/power_save`"
  echo "\tPut the controller down when not in use: `cat /sys/module/snd_hda_intel/parameters/power_save_controller`"

```
Paste into gedit and save. Then make it executable chmod +x script_name and, in a terminal, you can run it by doing ./script_name. The output will show you if the values are changing.

Thinks that also help are switch to metacity when on battery, blocking flash when surfing internet, no bluetooth, etc..

Hope it brings some light!

---

### Post by jochem on 2010-04-14
Thanks, I'm gonna try these things tonight!

edit: Ok tried it, seems to work! Btw, I just copied it to /etc/pm/power.d, and it seems to work, even after switching back and forth between battery and ac. Didn't need the power.sh shellscript. Why is this needed?

@Axx83 I was looking for a way to set brightness_dim_battery to 100%, found it in your guide, great :)

---

### Post by PatrickVogeli on 2010-04-14
> **Axx83 said:**
> I'm not a programmer and I don't know a lot about scripts. I simply look at the code, look at what powertop tells me and what are the scripts that comes as default with every version of ubuntu (pm-utils scripts).

I'm not a boss and I don't know no truth. But I am right when I add the autosuspend script that turns to autosuspend all the usb ports that don't automatically go in that state when you unplug ac (webcam as an example). 

Powertop clearly shows the difference.

Most of the commands in the scripts I was referring to are indeed redundant or overcome default scripts that comes with Lucid, whether the latter are less efficient than those...it depends, surely they are safer.

And sorry but I DO think that Ubuntu's programmer know a little bit more than the average guy that writes here.

This is a forum to help people, sarcasms is a great thing in real life, here usually it's misinterpreted and only brings bad feelings. Avoid it.

Calm down.

Hey,

you're right, sorry. I suppose I was a little too rude with you, and I had no need to act like that. Sorry.

About the usb autosuspend.. I'm not fond of it. Problem one: if I do it, my mouse stops working. It's not an old mouse and it's probably a quite common one: logitech v450 nano.

So, as you said, the ubuntu programmers probably now a little more that you and me, and there's a reason for not all the usb ports being on auto.

Cheers mate

---

### Post by xir_ on 2010-04-14
thanks for the script. I'm looking forward to benchmarking it.

---

### Post by jochem on 2010-04-14
> **xir_ said:**
> thanks for the script. I'm looking forward to benchmarking it.

Wireless power saving isn't really nice, I recommend leaving it off, but try it, and decide for yourself. 

To turn it off add # before "iwconfig wlan0 power on", and "iwconfig wlan0 power off".

---

### Post by xir_ on 2010-04-14
> **jochem said:**
> Wireless power saving isn't really nice, I recommend leaving it off, but try it, and decide for yourself. 

To turn it off add # before "iwconfig wlan0 power on", and "iwconfig wlan0 power off".

Ahh its something i normally enable anyway. I really do treat this laptop as a test bed for getting maximum battery life.

---

### Post by jochem on 2010-04-14
> **xir_ said:**
> Ahh its something i normally enable anyway. I really do treat this laptop as a test bed for getting maximum battery life.

Don't you have to wait for like 5+ seconds each time you open a new website, before the wireless card starts working again?

---

### Post by xir_ on 2010-04-14
> **jochem said:**
> Don't you have to wait for like 5+ seconds each time you open a new website, before the wireless card starts working again?

not that i have noticed. Also it does save around 1.5 watts on this system when enabled.

---

### Post by jochem on 2010-04-14
> **xir_ said:**
> not that i have noticed. Also it does save around 1.5 watts on this system when enabled.

Do you have an Intel wifi link 1000 (if i remember the name of my wlan card correctly)?

---

### Post by Axx83 on 2010-04-14
ifconfig on my notebook (thinkpad x60s with iwl3945) does not work with lucid's kernel, don't know why actually but it seems a common problem

---

### Post by PatrickVogeli on 2010-04-15
> **jochem said:**
> Do you have an Intel wifi link 1000 (if i remember the name of my wlan card correctly)?
I have an Intel Wifi Link 1000 and it seems to work fine with the power saving enabled...

---

### Post by xir_ on 2010-04-16
might not be related but i've noticed that my screen no longer has the ability to dim. Although we are in beta.

---

