---
title: "Kded4 eating up a CPU"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-02-21
Using Jaunty 2.6.28-8 64 bit kernel. Turned on this morning after installing a few updates and one of my CPUs is being used 100% of the time by kded4. I'm using an AMD64x2.
I've run top and get the following:
```
top - 11:52:01 up 19 min,  1 user,  load average: 1.07, 1.21, 0.91
Tasks: 140 total,   2 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.3%us, 34.1%sy,  0.0%ni, 45.3%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   3989344k total,   816972k used,  3172372k free,    17352k buffers
Swap:  4883720k total,        0k used,  4883720k free,   332336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3881 kevin     20   0  383m  24m  17m R  100  0.6  18:40.25 kded4
 3520 root      20   0  215m  73m  10m S    3  1.9   1:01.85 Xorg
 4180 kevin     20   0  255m  30m  15m S    3  0.8   0:05.20 konsole
 3940 kevin     20   0  283m  43m  27m S    2  1.1   0:35.92 kwin
 3947 kevin     20   0  669m  68m  30m S    2  1.8   0:39.22 plasma
 3990 kevin     20   0  241m  18m  12m S    0  0.5   0:00.52 kmix
 4272 kevin     20   0 19116 1348  984 R    0  0.0   0:01.25 top
    1 root      20   0  4104  920  628 S    0  0.0   0:00.97 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.01 khelper
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0
   15 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1
  132 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
  133 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
  136 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1
  138 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
  139 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  232 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue
  239 root      15  -5     0    0    0 S    0  0.0   0:00.04 ata/0
  240 root      15  -5     0    0    0 S    0  0.0   0:00.15 ata/1
  241 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
  242 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
  247 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd
  250 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod
  256 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd
  262 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn
  263 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn
  297 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0
  298 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1
  321 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  322 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  323 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  370 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  371 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
  387 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea
  580 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
  583 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
  598 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
  601 root      15  -5     0    0    0 S    0  0.0   0:00.07 scsi_eh_3
  631 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4

```

Edit: An update/upgrade from terminal and a reboot has solved the problem.

---

### Post by halfsane on 2009-02-21
How did you solve this? 

 I am seeing the exact same thing. 

Thanks!

---

### Post by zenarcher on 2009-02-21
I had the same thing this morning, but after a reboot, everything was back to normal.

Cheers,
zenarcher

---

### Post by halfsane on 2009-02-21
that did the trick!

---

### Post by mariuz on 2009-02-21
> **halfsane said:**
> that did the trick!
Ok i will do an dist-upgrade then reboot 
I have now the same issue with kde:KS

---

### Post by DougieFresh4U on 2009-02-21
I am having same with gnome. keeps switching between CPU's running 100%
AMD x2 5200

---

### Post by Kevbert on 2009-02-21
> **DougieFresh4U said:**
> I am having same with gnome. keeps switching between CPU's running 100%
AMD x2 5200

Same problem. I just did a
```
sudo apt-get update
sudo apt-get upgrade
```
and then a reboot and everything was all hunky-dory again...

---

### Post by Mindless Automata on 2009-02-21
Same here; reboot fixed it.  Dunno if it'll reoccur.

---

### Post by DougieFresh4U on 2009-02-21
> **Mindless Automata said:**
> Same here; reboot fixed it.  Dunno if it'll reoccur.

Did the 'update-upgrade' thing and reboot, still doing 100% back and forth between CPU's

---

### Post by Kevbert on 2009-02-21
The only other things worth trying in terminal are
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```
If this still doesn't help (after a reboot), if you raise a bug report on this, I'll confirm it for you.

---

### Post by caryb on 2009-02-21
My laptop has been running for a couple of days & is quiet warm atm on my lap I did a check in top & got the same. That explains the warm feeling on my lap!  


Cary

---

### Post by DougieFresh4U on 2009-02-21
I have added it to this bug  [https://bugs.launchpad.net/bugs/187383](https://bugs.launchpad.net/bugs/187383)
as it is only happening when System Monitor is open

---

### Post by Kow on 2009-02-22
> **DougieFresh4U said:**
> I have added it to this bug  [https://bugs.launchpad.net/bugs/187383](https://bugs.launchpad.net/bugs/187383)
as it is only happening when System Monitor is open

The 100% cpu usage system monitor bug has been around since hardy. System monitor needs to do a lot of calculations for the graphs... thats why you dont leave system monitor open all the time.

---

### Post by caryb on 2009-02-22
Unless top uses system monitor I'm not guilty of using it & my kde4 was using 100% CPU & the lappy was very hot! A update & reboot & KDE4 does not even register in top & is probably 15 degrees cooler (Celsius)


Cary

---

### Post by Kevbert on 2009-02-22
Same as Caryb. Was not using system monitor, but was (and am still) using a few plasmoids which come with Kubuntu for general monitoring (as conky causes a minor problem with my wallpaper).
I've added a comment to the bug report and cross referenced it to here.

---

### Post by LostOverThere on 2009-02-23
Actually, I've have the bug since Ubuntu 7.04 and chances are it was around before that time too.

---

### Post by mariuz on 2009-04-07
confirmed , i have some monitoring plasmoids and seems that they eat a lot of cpu with kded4 , 
I will try to remove them to see what is happening

---

### Post by Asraniel on 2009-04-07
no problem here... and i have a temperature and cpu monitor plasmoid on the desktop

---

### Post by mariuz on 2009-04-07
I killed it and i started it with strace 

$ qdbus org.kde.kded /kded loadedModules
kdedglobalaccel
networkstatus
powerdevil

now it seems that cpu usage is low again , i will see if it returns to eat it again :guitar:

---

