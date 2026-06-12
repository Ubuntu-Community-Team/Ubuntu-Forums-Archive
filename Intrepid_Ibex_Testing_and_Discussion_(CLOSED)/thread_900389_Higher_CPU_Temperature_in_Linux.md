---
title: "Higher CPU Temperature in Linux"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-08-25
In Windows I have 40°C for basic usage (Firefox) while I have 45°C for the same thing in Linux.

[C1E is disabled]("http://ubuntuforums.org/showthread.php?t=900286") for both OSes.

---

### Post by mrtomservo on 2008-08-25
Well, lots of things can affect cpu temps.  Perhaps in your linux setup it's running more background programs?  Try comparing the cpu load vs cpu temp.  Also, I have personally always had different reported temps in windows vs linux.  But not a 5 degrees Celsius difference. 

What's your temperature monitoring setup look like?  (ie lm-sensors, gkrellm, etc)

---

### Post by klange on 2008-08-25
It's also possible that your fan configuration isn't supported, which could cause your fan to run sub-optimally, increasing CPU temperature.

(Why are you posting here? Are you on Intrepid?)

---

### Post by ssam on 2008-08-25
install powertop. you need to run it with sudo
```
sudo powertop
```

it will tell you which programs or drivers are keeping you CPU active. (it can be quite surprising, one of my biggest things was ssh-menu, due a bug in ruby-gtk)

---

### Post by grigio on 2008-08-25
I don't have anything special loaded.

```
Wakeups-from-idle per second : 331,2    interval: 5,0s
no ACPI power usage estimate available

Top causes for wakeups:
  72,7% (378,6)       <interrupt> : uhci_hcd:usb1, fglrx[0]@PCI:1:0:0, rtl8180 
   8,6% ( 44,8)           firefox : futex_wait (hrtimer_wakeup) 
   4,3% ( 22,4)       <interrupt> : uhci_hcd:usb3, ehci_hcd:usb4, uhci_hcd:usb7,
   3,0% ( 15,8)      <kernel IPI> : Rescheduling interrupts 
   2,4% ( 12,6)   USB device  7-2 : USB Optical Mouse (Logitech) 
   2,3% ( 11,8)       <interrupt> : uhci_hcd:usb6, ohci1394, ata_piix, ata_piix
```

WindowsSucks:
```
$ sudo fancontrol 
Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
```

---

### Post by ssam on 2008-08-25
over 300 wakes per second is quite a lot. that means your CPU can't spend much time in low power modes before being woken up again. yours are most being caused by a hardware driver, but it is tricky to know which one.
[http://www.lesswatts.org/projects/powertop/known.php](http://www.lesswatts.org/projects/powertop/known.php) might help.

This is what i have right now. with quite a lot of apps open. the keyboard/mouse/touchpad goes away if i leave the mouse still.
```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (12.1%)         1400 Mhz    12.7%
C1                0.0ms ( 0.0%)         1000 Mhz     0.0%
C2                7.5ms (23.5%)          800 Mhz     0.3%
C3                7.5ms (64.4%)          600 Mhz    87.0%


Wakeups-from-idle per second : 117.1    interval: 15.0s
no ACPI power usage estimate available

Top causes for wakeups:
  49.0% ( 63.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  11.5% ( 14.8)             xchat : schedule_timeout (process_timeout) 
   9.3% ( 12.0)           empathy : schedule_timeout (process_timeout) 
   4.9% (  6.3)          metacity : schedule_timeout (process_timeout)
   2.8% (  3.6)   gnome-screensav : schedule_timeout (process_timeout)
   2.2% (  2.9)          trackerd : schedule_timeout (process_timeout)
   2.1% (  2.7)       <interrupt> : uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, ohci1394, radeon@pci:0000:01:00.0, Intel 82801
   2.0% (  2.6)       gnome-panel : schedule_timeout (process_timeout)
   1.8% (  2.3)       <interrupt> : acpi
   1.8% (  2.3)       liferea-bin : futex_wait (hrtimer_wakeup)
   1.5% (  1.9)           firefox : futex_wait (hrtimer_wakeup)
   1.4% (  1.8)    gnome-terminal : schedule_timeout (process_timeout)
   0.9% (  1.1)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0.8% (  1.1)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer)
   0.8% (  1.0)            dhcdbd : schedule_timeout (process_timeout)
   0.8% (  1.0)         nm-applet : schedule_timeout (process_timeout)

```

if i enable wireless then
```
67.3% (115.3)       <interrupt> : uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, ohci1394, radeon@pci:0000:01:00.0, Intel 82801
```
jumps to the top. (just using the network manager applet to disable the wifi).

note: i am on a IBm thinkpad x31, with hardy

---

### Post by grigio on 2008-08-25
I'm going to open a bug.. When it tries to compile something it reach >60°C

---

### Post by jpittack on 2008-08-25
The issue resides in the 300 wakeups per second.  I have a feeling you are on an amd platform using 64 bit.  That is the kernel waking up to see if there is work to be done.  The issue may be resolved in future kernels.

Amd processors should be able to handle over 80 C.  Then do run hot in some generations and thus have the higher tolerance.  That said, I am not on intrepid and don't know of any changes that may have occured.

---

### Post by grigio on 2008-08-25
no, it's intel e8400

---

### Post by Gina on 2008-08-25
The CPU on my AMD64 running either Hardy or Intrepid runs at 35C max (I don't have Windoze on that machine) - I think the fan speed could be reduced :lol:

---

### Post by syko21 on 2008-08-25
Are the changes made by powertop persistent? Will they stay active after reboot etc? (I realize the modules will be reloaded but it said other settings would be changed too like writeback time)

---

### Post by Nullack on 2008-08-25
Its not a problem - refer to the AMD thermal specifications

You could consider a better aftermarket cpu cooler if your concerned

---

### Post by grigio on 2008-08-25
It's a regression because with hardy's Livecd I get:
50 wakeups in 5sec.. but i wouldn't transfom my intrepid in frankenstain. I already donwgraded X to have a quite functional system.

---

### Post by Nullack on 2008-08-25
The temps are well within AMDs specifications are not a problem.

There might be a power management issue here but it requires further diagnosis.

---

### Post by grigio on 2008-08-25
I've opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261282](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261282)

Now the differences are increasing (50°C in idle)

---

### Post by SarahKH on 2008-08-25
Personally, I'd poke my head inside the machine (with it turned OFF) and see if the fans are caked in dust.  Especially if the temps are creeping up.  Once you've got rid of the dust inside using a paint brush, power it up and make sure all fans are rotating properly. 

Fans can, and do die. 

I'd also try yoinking everything out of the USB bus and try running powertop again, just for giggles, as it looks like USB polling is waking the system up.  Possibly a USB keyboard or mouse?

Either way, check the fans first.

---

### Post by Gina on 2008-08-26
I had a dead fan on the graphics card in my P4 system.  It was so dead it had fallen off and was lying on the PCI card below!!  It was clogged up with dust.  I had not cleaned the machine for 2 or 3 years and the build-up of dust was staggering.  The processor cooler was partly clogged up with dust too.  I gave it a good clean and (with some creative fiddling) put a new fan on the graphics card and it's all working again fine now.  But it just goes to show how dirt can build up.  I was lucky that the graphics card had not failed.

MORAL :- Clean dust out of your conputer(s) regularly - perhaps annually - to avoid failure due to dust clogging cooling systems.

---

### Post by Nullack on 2008-08-26
Handy hint : Stick a screwdriver into the fan blades to prevent damage to the bearings and squirt it with one of those compressed air in a can items. Much faster than a brush and no electric static discharge issues.

---

### Post by ronacc on 2008-08-26
yes compressed air is your best soldier in the war on dust.:)

---

### Post by Gina on 2008-08-26
I use a vacuum cleaner, being careful not to touch exposed solder connections etc. to avoid possible static on the nozzle end.

---

### Post by ronacc on 2008-08-26
actualy a combination of both is what I use, the vaccum cleaner to get the surface stuff and also to suppress the dust cloud when I use compressed air to blast the dust out of crevices and heatsink fins. The main thing is get the dust out any way that works .

---

### Post by highlandsun on 2008-08-26
I just installed Ubuntu on a new laptop (2 days ago) and it definitely runs about 10 degrees hotter under Linux than under Vista. It's not anything to do with dirt clogging the cooling vents, since this is a brand new machine. I upgraded to Intrepid alpha4 today, to play with Networkmanager 0.7. I also upgraded to a 2.6.27-rc4 kernel, which seems to be a little better as far as halting the CPU when it's idle. (cpuidle says it's using C1E support, which is good. <=2.6.26 didn't do that, and showed bogus values for the ACPI power state all the time.)

(This is an HP dv5z with Turion Ultra. According to AMD's BIOS/kernel Developers' Guide, this processor only supports C0, C1, and C1E states. On older kernels it seemed to be stuck in C0 all the time, thus maximum power draw.) I already know there's Windows-specific support in the BIOS. Just wish I could track down everything they're doing...

---

### Post by grigio on 2008-08-26
Oh my g0d! a thread full of comments that explain me how to clean my fans :lolflag:

It's NEW Pc and the fans too, the dust is the same in Linux or in Windows.

---

### Post by Nullack on 2008-08-26
Perhaps if you conduct further diagnosis with powertop to isolate what the calls are?

---

### Post by MaX on 2008-08-26
Ok I'm reading this thread and hear that over 300 wakeups is bad... 
I have 450 in idle and above 800 when Transmission is running.
```
     PowerTOP version 1.10      (C) 2007 Intel Corporation

< Detailed C-state information is not P-states (frequencies)
                                        2,21 Ghz     9,4%
                                        2,00 Ghz     0,0%
                                        1,80 Ghz     2,3%
                                        1000 Mhz    88,3%


Wakeups-from-idle per second : 491,6    interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  42,5% (308,3)       <interrupt> : ohci_hcd:usb1, eth0 
  20,1% (145,8)       <interrupt> : nvidia 
  18,1% (131,4)   /sys/bus/usb/devices/1-1 
   4,8% ( 34,8)      <kernel IPI> : Rescheduling interrupts 
   4,0% ( 29,3)           firefox : futex_wait (hrtimer_wakeup) 
   2,6% ( 19,1)              Xorg : do_setitimer (it_real_fn) 
   2,5% ( 18,0)       gnome-panel : schedule_timeout (process_timeout) 
   1,3% (  9,5)   gnome-system-mo : schedule_timeout (process_timeout)
   1,1% (  8,1)            python : schedule_timeout (process_timeout)
   0,6% (  4,4)       <interrupt> : PS/2 keyboard/mouse/touchpad
   0,6% (  4,1)       <interrupt> : pata_amd
   0,2% (  1,1)        pulseaudio : schedule_timeout (process_timeout)
   0,1% (  1,0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer)
   0,1% (  1,0)            dhcdbd : schedule_timeout (process_timeout)
   0,1% (  1,0)          nautilus : schedule_timeout (process_timeout)
   0,1% (  0,9)    cpufreq-applet : schedule_timeout (process_timeout)
   0,1% (  0,6)     <kernel core> : __enqueue_rt_entity (sched_rt_period_timer)
   0,1% (  0,6)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_
   0,1% (  0,6)   gnome-settings- : schedule_timeout (process_timeout)
   0,1% (  0,5)    sensors-applet : schedule_timeout (process_timeout)
   0,1% (  0,5)   hald-addon-stor : schedule_timeout (process_timeout)
   0,1% (  0,5)   gnome-system-mo : hrtick_set (hrtick)
   0,1% (  0,5)   gnome-system-mo : sk_reset_timer (tcp_delack_timer)

Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a

```

So how do I get rid of "ohci_hcd:usb1, eth0" ???
I'm on a AMD64 X2 Processor.

---

### Post by Nullack on 2008-08-26
You dont want to get rid of eth0 more than likely :)

---

### Post by BC7333 on 2008-08-26
> **highlandsun said:**
>  I also upgraded to a 2.6.27-rc4 kernel, which seems to be a little better as far as halting the CPU when it's idle. .

How did you get 2.6.27-rc4?

---

### Post by MaX on 2008-08-26
> **Nullack said:**
> You dont want to get rid of eth0 more than likely :)

Of course I want my network, but the network makes 300 wakeups by itself?
Is it an issue with the Nforce chipset I use?

---

### Post by Gourgi on 2008-08-26
> **grigio said:**
>  the dust is the same in Linux or in Windows.
LOOOL !!!
great answer!
man i love you :lolflag:

---

### Post by grigio on 2008-08-26
Guys, the temperature is the same in Windows or in Linux. :popcorn:

!!!
The problem is that in Linux **fancontrol** and the **cpu scaling** doesn't work in my config.
!!!

The difference is that Asus Ai utility uses CPUTIN value while coretemp uses cpu #0 and #1

sensors-detect doesn't detect **mainboard** and **GPU** sensors any advices to setup them?

---

### Post by klange on 2008-08-26
Are you sure the dust levels are the same?
You should measure them. Windows could be spinning the fan faster, causing more dust to come loose.


[size="1"]Sorry, I have no idea what the problem is or how to help, but thought I'd take a stab at a witty and comical comment.[/size]

---

### Post by Gina on 2008-08-26
Both my AMD machines show CPU scaling under Intrepid.  The others don't have the facility anyway.

---

### Post by ronacc on 2008-08-26
on my amd64x2 4600 both cores run at 30 to 34 at idle the same as in hardy , thats with an nvidia 7600 gs the 177 driver and compiz running .

---

