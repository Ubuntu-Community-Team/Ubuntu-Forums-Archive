---
title: "kworker - excessive CPU useage - Ubunt 14.04 64 bit  fresh install"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-08-25
I am at a loss for how to get kworker or what is driving kworker to suck up sooo much cpu.

Here is what I tried so far: 

meow@MeowBatunde:~$ uname -r
3.13.0-34-generic


```

   89  echo disable > /sys/firmware/acpi/interrupts/gpe01
   90  unrame -r
   91  uname -4
   92  uname -r
   93  sudo swapoff -a
   94  top
   95  sudo apt-get install linux-tools
   96  uname -r
   97  sudo apt-get install linux-tools-generic 3.13.0.34.40
   98  sudo apt-get install linux-tools-generic 3.13.0.34-generic


```

$ top 

```

 4851 root      20   0       0      0      0 R  54.5  0.0 441:50.09 kworker/7:3                                
    7 root      20   0       0      0      0 R  46.3  0.0  79:49.14 rcu_sched                                  
 2382 meow      20   0 2366816 985176  56804 R  41.6 12.0 151:25.21 firefox                                    
 1204 root      20   0  324512 107016  46336 S   6.6  1.3  24:42.66 Xorg                                       
 1972 meow      20   0 1814752 128712  40864 S   2.3  1.6   5:51.06 compiz                                     
 2583 meow      20   0  729720  21620  13580 S   2.3  0.3   0:06.16 gnome-terminal                             
 2032 meow      20   0 1810864  76564  49084 S   2.0  0.9   0:10.41 nautilus   

```

Is this related to my delta66 sound card?
[HTML]
http://www.archivum.info/ubuntu-bugs@lists.ubuntu.com/2011-04/17233/%28Bug-755226%29-%28NEW%29-syndaemon-starts-eating-up-100-CPU-after-waking-laptop-from-sleep.html
[/HTML]

from 2011 -- some things which did not work for me
[HTML]https://lkml.org/lkml/2011/3/31/68[/HTML]


```

meow@MeowBatunde:~$ echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
bash: /sys/kernel/debug/tracing/set_event: Permission denied
meow@MeowBatunde:~$ sudo echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
bash: /sys/kernel/debug/tracing/set_event: Permission denied
meow@MeowBatunde:~$ 


```

I am having a festival of boot loader (GRUB) issues.  I wonder if the advice from a prior post would help ... 
> Re: Kworker constant 85% w/ ivy bridge I5
Update: I've disabled acpi and that corrected the problem. Still not sure why that would cause this to happen. 

[HTML] http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting[/HTML]

```
meow@MeowBatunde:~$ grep . -r /sys/firmware/acpi/interrupts/
/sys/firmware/acpi/interrupts/sci:       0
/sys/firmware/acpi/interrupts/error:       0
/sys/firmware/acpi/interrupts/gpe00:       0   invalid
/sys/firmware/acpi/interrupts/gpe01:       0   invalid
/sys/firmware/acpi/interrupts/gpe02:       0   invalid
/sys/firmware/acpi/interrupts/gpe03:       0   invalid
/sys/firmware/acpi/interrupts/gpe04:       0   disabled
/sys/firmware/acpi/interrupts/gpe05:       0   invalid
/sys/firmware/acpi/interrupts/gpe06:       0   invalid
/sys/firmware/acpi/interrupts/gpe07:       0   invalid
/sys/firmware/acpi/interrupts/gpe08:       0   invalid
/sys/firmware/acpi/interrupts/gpe09:       0   invalid
/sys/firmware/acpi/interrupts/gpe10:       0   disabled
/sys/firmware/acpi/interrupts/gpe11:       0   disabled
/sys/firmware/acpi/interrupts/gpe12:       0   disabled
/sys/firmware/acpi/interrupts/gpe13:       0   disabled
/sys/firmware/acpi/interrupts/gpe14:       0   invalid
/sys/firmware/acpi/interrupts/gpe15:       0   invalid
/sys/firmware/acpi/interrupts/gpe16:       0   invalid
/sys/firmware/acpi/interrupts/gpe0A:       0   invalid
/sys/firmware/acpi/interrupts/gpe17:       0   invalid
/sys/firmware/acpi/interrupts/gpe0B:       0   disabled
/sys/firmware/acpi/interrupts/gpe18:       0   disabled
/sys/firmware/acpi/interrupts/gpe0C:       0   invalid
/sys/firmware/acpi/interrupts/gpe19:       0   invalid
/sys/firmware/acpi/interrupts/gpe0D:       0   invalid
/sys/firmware/acpi/interrupts/gpe0E:       0   invalid
/sys/firmware/acpi/interrupts/gpe0F:       0   disabled
/sys/firmware/acpi/interrupts/gpe1A:       0   invalid
/sys/firmware/acpi/interrupts/gpe1B:       0   disabled
/sys/firmware/acpi/interrupts/gpe1C:       0   invalid
/sys/firmware/acpi/interrupts/gpe1D:       0   enabled
/sys/firmware/acpi/interrupts/gpe1E:       0   invalid
/sys/firmware/acpi/interrupts/gpe1F:       0   invalid
/sys/firmware/acpi/interrupts/sci_not:       0
/sys/firmware/acpi/interrupts/ff_pmtimer:       0   invalid
/sys/firmware/acpi/interrupts/ff_rt_clk:       0   disabled
/sys/firmware/acpi/interrupts/gpe_all:       0
/sys/firmware/acpi/interrupts/ff_gbl_lock:       0   enabled
/sys/firmware/acpi/interrupts/ff_pwr_btn:       0   enabled
/sys/firmware/acpi/interrupts/ff_slp_btn:       0   invalid
```



thoughts? suggestions?

---

### Post by xigen on 2014-08-25
I have no clue what worked....

Upon re-boot kworker is no longer an issue.

---

