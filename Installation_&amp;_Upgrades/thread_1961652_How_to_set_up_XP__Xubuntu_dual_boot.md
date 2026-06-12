---
title: "How to set up XP / Xubuntu dual boot?"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by Blank000 on 2012-04-19
Hello everyone!
Here i am, wanting to try out Linux and getting stuck at - installing it.

Since my first try was a disaster of epic proportions (selected 80GB partition with data as swap), i should prepare a little better second time around.
But, the more i google the more confused i am.

So, XP is installed, partitions on disk are prepared as follows:
1. XP installed on it
2. for Xubuntu
3. for swap
4. for data

Besides XP all others are completely clean. Several things are unclear.
When installing i select "something else", that gives me the option to select partitions, but under "use as" there are several options. I know to select "swap" for swap, but what to select for Xubuntu (ext2, ext3, extxy...)?

Then, there is some talk of "home" partition? But there is also some about how one shouldn't have more then four partitions on disk?

Finaly, getting to actuall dual boot. I've found this [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

It speaks of GRUB, MBR, and how some changes to it will be necessary, but not a word about how, where and what am i supposed to change.
> GRUB2 is the boot manager installed in Ubuntu... This means Ubuntu is independent and avoids any need for writing to other operating systems. To accomplish this, the only thing in your computer outside of Ubuntu that needs to be changed is a small code in the MBR (Master Boot Record) of the first hard disk. The MBR code is changed to point to the boot loader in Ubuntu.

Enough with the question. For now :)
Can someone in plain language (don't go primary, secondary, extended, logical on me :) ) explain what do i do, to get this thing installed.

Thanks in advance!

---

### Post by zvacet on 2012-04-19
> (don't go primary, secondary, extended, logical on me

But that can be handy,because if you make extended partition then inside you can create more then just 4 partitions.You can have may 4 **primary** partitions,but if you have extended one things changed.But if you don´t want to make extended partition then as you partitioned your HD I will make this(I don´t know how much space do you have)

1. root=10-15GB                mountpoint /
2. swap=~2GB 
3. home= rest of fre space     mountpoint /home

At home partition will be your settings and files ( data if you want),so in case something goes wrong your settings will be safe.That is why is good to have separate home partition.Format partitions as ext4.If you have any more questions,just ask.

---

### Post by dzponce11 on 2012-04-19
Try using wubi, which can be found at the ubuntu website.

---

### Post by al111 on 2012-04-19
Better installing to its' own partition than in wubi-

Just my opinion-

---

### Post by oldfred on 2012-04-19
aysiu's example with screenshots is straight forward. It would be essentially the same process for different versions of Ubuntu.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For those who want lots of detail and explanation, but also with screenshots:
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by mastablasta on 2012-04-20
> **Blank000 said:**
>  
So, XP is installed, partitions on disk are prepared as follows:
1. XP installed on it
2. for Xubuntu
3. for swap
4. for data

 
Is "4. data " going to be shared with windows? because then this partition shouldnt' be /home.
> 
Besides XP all others are completely clean. Several things are unclear.
When installing i select "something else", that gives me the option to select partitions, but under "use as" there are several options. I know to select "swap" for swap, but what to select for Xubuntu (ext2, ext3, extxy...)?
 
Whatever you like. but it's best to use default ext4 file system if you don't know the difference.
> 
Then, there is some talk of "home" partition? But there is also some about how one shouldn't have more then four partitions on disk?

howm is where all data and settigns are stored. it can be a directory/folder or separate partition. on desktop it works kind fo like My Documents in windows or maybe more like the user's folder.
>  
Finaly, getting to actuall dual boot. I've found this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
It speaks of GRUB, MBR, and how some changes to it will be necessary, but not a word about how, where and what am i supposed to change.
 
 No worries, they are done automaticly for you. widnows MBR is replaced by GRUB, which will can handle the booting of a number of operating systems (such as Windows, linux, MacOS, i think also BSD...). you will then get a choice into which system you want to boot. it can also be customized a bit (background image, text colour etc.)
 
also note that creating additional linux partitions is actually not necessary. installer will do it for you. all you need to do is have empty disk space (i.e. unformated space).

---

### Post by Blank000 on 2012-04-20
Thanks guys, you're great! :)

Here i am, posting from Xubuntu and Midori browser ;)

I played with it for the last two hours, and i really like it. But, to my great disappointment, on this old computer i'm trying to bring back to life (Pentium IV 1.8, 512 RAM) it's actually slower then XP (GIMP is literally useless, vs. XP where it runs normally, Opera installation was a 20+minutes wait...), and once it goes to swap things get even worse.
I'll keep it for now, but it doesn't looks promising. Guess i'll be looking for "how to remove dual boot" real soon :D

---

### Post by mastablasta on 2012-04-21
what graphics card do you have? (you can type ```
lspci
``` in terminal to give you a list which you can copy and post here). Xubutnu shoudld eb much faster on such maschine than windowsXP. but if card is poorly supported then it could be slower. i am using a Chrunchbang XFCE on 256MB (32 MB taken by GPU), 1,2 Ghz computer. windows took between 8 and 10 minutes only to boot the OS. this debain verison with XFCE takes about 30 seconds. it seems card is well supported though.

try putting in 

```
top
``` command to see what consumes the ram and CPU. maybe a setting is wrong.

additionally you can try

```
free -m
```

command to see memorry usage. post it here as well.

---

### Post by Blank000 on 2012-04-21
> **mastablasta said:**
> what graphics card do you have? (you can type ```
lspci
``` in terminal to give you a list which you can copy and post here). 

Here they are:

**lspci:**
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 43)
02:03.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```


**top:**
```
top - 14:15:18 up 6 min,  0 users,  load average: 0.10, 0.42, 0.28
Tasks: 110 total,   2 running, 107 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.8%us,  3.6%sy,  0.0%ni, 81.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    508324k total,   436532k used,    71792k free,    45568k buffers
Swap:   524284k total,        0k used,   524284k free,   207372k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                 
 1082 root      20   0 39384  18m 7864 R  8.9  3.8   0:57.06 Xorg                                    
 1472 dario     20   0  331m  66m  27m S  5.0 13.4   0:46.59 midori                                  
 1684 dario     20   0  158m  13m  10m S  3.6  2.8   0:03.88 xfce4-terminal                          
 1231 dario     20   0 23868  11m 8380 S  1.3  2.2   0:03.44 xfwm4                                   
 1742 dario     20   0  2820 1120  848 R  0.7  0.2   0:00.17 top                                     
    4 root      20   0     0    0    0 S  0.3  0.0   0:01.10 kworker/0:0                             
    1 root      20   0  3316 1784 1216 S  0.0  0.4   0:01.40 init                                    
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.18 ksoftirqd/0                             
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.70 kworker/u:0                             
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                             
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                                  
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                                 
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                                   
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                             
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                             
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                             
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                                 
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff                                 
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                   
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md                                      
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.25 kworker/u:1                             
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.21 kworker/0:1                             
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                              
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                 
   21 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                    
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark
```

**free -m**
```
             total       used       free     shared    buffers     cached
Mem:           496        426         70          0         44        202
-/+ buffers/cache:        179        317
Swap:          511          0        511
```


I did what this page recommends [HTML]http://sites.google.com/site/easylinuxtipsproject/first[/HTML],  but when i start "Additional drivers" nothing is found.
Here is a Synaptic Package Manager screenshot:
[IMG]http://img593.imageshack.us/img593/8004/screenshot0421201202363.png[/IMG]


> windows took between 8 and 10 minutes only to boot the OS. this debain verison with XFCE takes about 30 seconds.

Forgot to even mention that, boot time is also longer for Xubuntu then XP. Opening programs, new tabs in Midori, even File manager takes longer than it should. It's just generally slow.

---

### Post by zvacet on 2012-04-21
If you didn´t get any better suggestion then try to switch to Lubuntu.It is easy thing to do and as far I know LXDE is lightest DE.Read [this]("http://www.psychocats.net/ubuntu/purelxde") under **Remove Xubuntu**.

---

### Post by Blank000 on 2012-04-22
> **zvacet said:**
> If you didn´t get any better suggestion then try to switch to Lubuntu.It is easy thing to do and as far I know LXDE is lightest DE.Read [this]("http://www.psychocats.net/ubuntu/purelxde") under **Remove Xubuntu**.

Considering everything mastablasta said, this looks like hardware support problem. If Xubuntu has problems, i guess Lubuntu will also have them. And it is less user friendly for a beginner.

---

### Post by Blank000 on 2012-04-23
> **zvacet said:**
> If you didn´t get any better suggestion then try to switch to Lubuntu.It is easy thing to do and as far I know LXDE is lightest DE.Read [this]("http://www.psychocats.net/ubuntu/purelxde") under **Remove Xubuntu**.

Unfortunately, Xubuntu in this state, on this computer is useless. So i'll have to give Lubuntu a try. Is it really so simple, just copy/paste into the terminal?

Is there anything i should know, prepare for, since it is a dual boot?

---

### Post by zvacet on 2012-04-23
Just copy/paste commands from given page and Xubuntu will be replaced with Lubuntu.Nothing to do with other partitions.You will just change desktop environment.

---

