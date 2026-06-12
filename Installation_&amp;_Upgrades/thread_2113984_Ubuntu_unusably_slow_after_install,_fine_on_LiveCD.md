---
title: "Ubuntu unusably slow after install, fine on LiveCD"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by cephalopods on 2013-02-08
I am (attempting) to run ubuntu 12.10 on a ThinkPad T530. I am typing  this message on it running from a LiveCD. It works wonderfully -  wireless works without trouble, special function keys respond, and the  gui is crisp and responsive. Sadly, this is  not the ubuntu I get when I install alongside windows 7 from this very  same disk. I have gone through the upgrade/reinstall procedure to 12.10  several times on this computer, and every time it is the same. When  booting into ubuntu from the harddrive, it is unusably slow/freezy. 

Hitting  tab to autocomplete in terminal takes 5-10 seconds to generate a  completion. The graphics for switching windows freezes mid-transition.  Clicking into a text field on a webpage I have to wait 5-10 seconds  before any text I type shows up or the mouse changes from a pointer to  the text cursor. Typing in a text file will just stop displaying what I  type after a few words, then the words typed in the meantime show up  seconds later all at once. It is incredibly frustrating to try and get  anything done. 

Since it works fine from the disk and only  displays these problems after install, I've dubbed it an installation  problem. Running from the cd/flashdrive all the time is sadly not very  practical. Any ideas on what might cause this or how I can fix it?

---

### Post by offgridguy on 2013-02-08
> **cephalopods said:**
> I am (attempting) to run ubuntu 12.10 on a ThinkPad T530. I am typing  this message on it running from a LiveCD. It works wonderfully -  wireless works without trouble, special function keys respond, and the  gui is crisp and responsive. Sadly, this is  not the ubuntu I get when I install alongside windows 7 from this very  same disk. I have gone through the upgrade/reinstall procedure to 12.10  several times on this computer, and every time it is the same. When  booting into ubuntu from the harddrive, it is unusably slow/freezy. 

Hitting  tab to autocomplete in terminal takes 5-10 seconds to generate a  completion. The graphics for switching windows freezes mid-transition.  Clicking into a text field on a webpage I have to wait 5-10 seconds  before any text I type shows up or the mouse changes from a pointer to  the text cursor. Typing in a text file will just stop displaying what I  type after a few words, then the words typed in the meantime show up  seconds later all at once. It is incredibly frustrating to try and get  anything done. 

Since it works fine from the disk and only  displays these problems after install, I've dubbed it an installation  problem. Running from the cd/flashdrive all the time is sadly not very  practical. Any ideas on what might cause this or how I can fix it?
I would try another download, burn another CD and try that.

---

### Post by ahallubuntu on 2013-02-08
This is a dual boot installation right?  Windows and Ubuntu on the same drive?  How much disk space did you allocate for Ubuntu?

In Ubuntu, please open a terminal and type:

```
sudo parted -l
```

and

```
free -m
```

You might also start this in a terminal (it will fresh itself - hit Ctrl C to end it).

```
top
```

The processes that use the most CPU are at the top.  What are they and what %CPU do they show?

---

### Post by cephalopods on 2013-02-09
It is indeed a dual boot setup, with the Ubuntu partition at ~307 gigs on a 500 gigabyte harddrive. 
Requested output: 

For sudo parted -l  :
```

Model: ATA TOSHIBA MK5061GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1574MB  1573MB  primary   ntfs         boot
 2      1574MB  165GB   163GB   primary   ntfs
 4      165GB   485GB   321GB   extended
 5      165GB   472GB   307GB   logical   ext4
 6      472GB   485GB   13.5GB  logical
 3      485GB   500GB   14.7GB  primary   ntfs


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 13.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  13.5GB  13.5GB  linux-swap(v1)

```
free -m: 
```

             total       used       free     shared    buffers     cached
Mem:          7711       2177       5533          0         56       1012
-/+ buffers/cache:       1108       6603
Swap:        12912          0      12912

```

For top, a sample of what I'm seeing over a couple minutes: 
```

1189 root      20   0  200m  19m 7060 S   4.6  0.3   0:49.59 Xorg                                    
 2469 nathan    20   0  528m  20m  12m S   3.7  0.3   0:02.76 gnome-terminal                          
 3711 nathan    20   0  930m  81m  21m S   2.3  1.1   0:18.70 chrome                                  
 2077 nathan    20   0 1292m  90m  30m S   1.7  1.2   0:34.94 compiz                                  
 2793 nathan    20   0  476m  30m  20m S   1.0  0.4   0:34.38 chrome                                  
 1176 avahi     20   0 33604 2948 1484 S   0.7  0.0   0:37.14 avahi-daemon                            
 2325 nathan    20   0  677m 100m  41m S   0.7  1.3   0:51.52 chrome                                  
  419 root      20   0     0    0    0 S   0.3  0.0   0:01.34 kworker/0:2                             
 2053 nathan    20   0  981m  20m  13m S   0.3  0.3   0:02.21 gnome-settings-                         
 2085 nathan    20   0 20208  948  772 S   0.3  0.0   0:02.07 syndaemon                               
 2233 nathan    20   0  306m  11m 9072 S   0.3  0.2   0:01.08 gtk-window-deco                         
 2246 nathan    20   0  349m 5136 3540 S   0.3  0.1   0:04.72 hud-service                             
 2787 nathan    20   0  314m  20m  14m S   0.3  0.3   0:02.79 chrome                                  
    1 root      20   0 24600 2604 1396 S   0.0  0.0   0:00.94 init                                    
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd                                
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.21 ksoftirqd/0                             
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.14 migration/0                             
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.02 watchdog/0       

```
The percentages bob up and down a bit, but generally everything is staying in the single digits. The top is typically Xorg or chrome. 

I also created a new USB to boot from, but I want to hold off on trying a new install until I see if this troubleshooting can get anywhere.

---

### Post by ahallubuntu on 2013-02-09
OK, you've got plenty of disk space, huge swap space, plenty of RAM, etc.  CPU use sounds not unusually high.

I'd also check the hard drive.  Install GSmartControl:

```
sudo apt-get install gsmartcontrol
```

start it up, and check the Attributes tab (these are S.M.A.R.T. Attributes saved by the hard drive's firmware).  Any Attributes highlighted in pink?  If so, which ones?  If none are highlighted in pink the drive probably isn't failing.

---

### Post by cephalopods on 2013-02-09
Attributes in pink: **Reallocated Sector Count** and **Reallocation Event Count**. I've attached a screenshot of the whole attributes page if any further details from that report are helpful.

---

### Post by cephalopods on 2013-06-06
Worked beautifully on a new harddrive, and even more so now on a solid state drive. After several months there have been no signs of any of the original symptoms, so it looks like that was indeed the problem. Thanks all for your help!

---

