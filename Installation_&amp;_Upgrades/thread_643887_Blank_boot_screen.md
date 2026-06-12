---
title: "Blank boot screen"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Leion on 2007-12-18
Hi,

I have just installed ubuntu 7.10 into my IBM T43 laptop
dual boot with windows.

Live CD was good 

However on booting from hdd, after grub, All i see is black screen. I have to wait for about 4-5 minutes before I get into the login page.
This seems slow and I can hear alot of activities in my hdd. 

I am able to see the checking and loading of packages and devices with the live cd, so can anyone help me in this? I do not like looking at blank screen during boot. If there is any error, i would not know.

Thanks in advance

---

### Post by taurus on 2007-12-18
What's the spec of your IBM laptop?  

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
free
```

---

### Post by Leion on 2007-12-18
> **taurus said:**
> What's the spec of your IBM laptop?  

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
free
```

```
leion@leionuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        514688     509120       5568          0       9100     210940
-/+ buffers/cache:     289080     225608
Swap:      1044184      34740    1009444
leion@leionuntu:~$ 

```

This is the free command

specs of my laptop : 512mb ram 1.8Mhz if i am not wrong

---

### Post by taurus on 2007-12-18
How about

```
top
```

---

### Post by Leion on 2007-12-20
```

leion@leionuntu:~$ top

top - 21:37:50 up 25 min,  2 users,  load average: 0.28, 0.50, 0.53
Tasks: 107 total,   3 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.5%us,  1.8%sy,  0.0%ni, 77.5%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    514688k total,   492192k used,    22496k free,     6120k buffers
Swap:  1044184k total,    34736k used,  1009448k free,   195248k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5760 leion     15   0 58216  44m 4736 R 16.1  8.9   0:28.29 wish                                                            
 5766 leion     17   0 1251m  81m  21m S  2.6 16.2   0:47.10 java                                                            
 5266 root      15   0 64752  30m  13m S  2.3  6.1   0:23.57 Xorg                                                            
16939 leion     15   0  2368 1156  876 R  0.5  0.2   0:00.09 top                                                             
 5709 leion     15   0 92576  21m  12m R  0.3  4.2   0:00.54 gnome-terminal                                                  
 5746 leion     15   0  154m  47m  20m S  0.3  9.5   0:11.26 firefox-bin                                                     
    1 root      15   0  2952 1856  532 S  0.0  0.4   0:01.14 init                                                            
    2 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                        
    7 root      19  -5     0    0    0 S  0.0  0.0   0:00.01 khelper                                                         
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0                                                       
   27 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  142 root      10  -5     0    0    0 S  0.0  0.0   0:00.35 kseriod                                                         
  161 root      15   0     0    0    0 S  0.0  0.0   0:00.10 pdflush                                                         
  162 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush                                                         
  163 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 kswapd0                                                         
  214 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 2127 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 2128 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 2250 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 ata/0                                                           
 2251 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 2254 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 2255 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 scsi_eh_1                                                       
 2614 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 kjournald                                                       
 2819 root      14  -4  3028 1376  408 S  0.0  0.3   0:00.17 udevd                                                           
 3758 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                         
 3760 root      10  -5     0    0    0 S  0.0  0.0   0:00.74 ipw2200/0                                                       
 3832 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused            



```

This is the output of my top command.
does this help?

---

### Post by willie_wang on 2007-12-20
this post by LeeAdkins might work - 4th/5th post down

[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

---

### Post by Leion on 2007-12-20
> **willie_wang said:**
> this post by LeeAdkins might work - 4th/5th post down

[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

Thanks.
I have removed the usplash program and removed the quiet settings in the grub menu.lst file
now i am able to boot fast.

Thanks again :)

---

### Post by willie_wang on 2007-12-20
you can still boot fast if you follow the instructions in the post further down the page in the previous link.

the reason why it's booting slow is something to do with the resolution settings in the usplash.conf file. but your choice :)

---

### Post by Leion on 2007-12-20
I understand your point 
but i had already uninstalled usplash before i saw your post
so I went ahead and removed the lines

it just thrills me to know a problem has been fixed. now my alt control f1 console screen is not fug up too
:)

---

