---
title: "An application is preventing the volume 'U571' from being unmounted"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-10-15
uh, what application is that?

this is a DVD in a DVD drive

when this happens, nothing works except a reboot.

another error message just popped up

Unable to eject U571

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.



I can using nautilus, view all the files. And totem can play the disk. BUT, vlc locks up and stops responding if I try to use VLC right now to open the disc.

just got another error

Unable to poll CD-RW/DVD-ROM Drive for media changes


top does not show me anything
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6766 root      20   0  365m  66m  22m S  6.6  6.6   2:46.17 Xorg               
 7664 scott     20   0  129m  23m  12m R  3.3  2.3   0:01.30 gnome-terminal     
 7355 scott     20   0 22304 3380 2028 S  0.7  0.3   0:08.20 gnome-screensav    
 8696 scott     20   0  2416 1180  884 R  0.7  0.1   0:00.78 top                
 4924 mysql     20   0  127m  20m 5320 S  0.3  2.0   0:02.93 mysqld             
 7701 scott     20   0  228m  71m  24m S  0.3  7.0   1:19.28 firefox            
    1 root      20   0  3056 1884  564 S  0.0  0.2   0:01.44 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   11 root      15  -5     0    0    0 R  0.0  0.0   0:00.00 ftraced            
   47 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   49 root      15  -5     0    0    0 S  0.0  0.0   0:00.44 kblockd/0          
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid   

```

---

### Post by sdowney717 on 2008-10-15
This medium contains software intended to be automatically started. Would you like to run it?

The software will run directly from the medium "U571". You should never run software that you don't trust.

If in doubt, press Cancel.

this disc has some strange software that loads a PC friendly player for the computer when running windows. I wonder if somehow this is causing the problem. 

In windows, Avast kicks up with a virus warning on this commercial disk from Universal

---

### Post by dagrump on 2008-10-15
It seems the windows dreck even tries to follow that wherever it goes. It phones home before it plays on windows, wonder what it sends? It's an old movie is anyone even listening? But the point that it's on a commercial disk is rather sad. If you ran windows the warning wouldn't even pop up, just a unknown install. Oh well it's just a windows install, colnezilla is your friend.

---

