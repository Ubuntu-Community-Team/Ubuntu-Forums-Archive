---
title: "Xubuntu 16.04 slow response, shutdown &amp; boot issues"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by jet74-5 on 2016-05-03
Hello,

I have a fresh install of Xubuntu 16.04 (64-bit) and something seems to be wrong. I really have no idea what might be the problem, and any help is very much appreciated.

The computer is a HP nx6325. It's old, but has been running flawlessly on Xubuntu before (14.04 32-bit)

Symptoms:
-Slow input. The pointer is responsive but keyboard input is slow. So is navigating menus and applications.
-Fan running constantly at full speed. However, the computer does not seem hot at all.
-Shutdown behaves a bit odd. Hard to explain, but it doesn't sound right, like it just cut's power at some point.
-Boot behaves odd. It will not start normally but is just locked at a black screen. At this point I am forced to do a hard power off. After that it boots normally, but then next time it wont boot. The rebooting function always freezes up. Also I get a message every boot that /dev/sda6 is clean. Whatever that means. 

Neither cpu nor ram seems to be under heavy load. This is the output of "top":



```
top - 11:30:36 up 31 min,  2 users,  load average: 0,33, 0,38, 0,41
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
top - 11:31:04 up 31 min,  3 users,  load average: 0,39, 0,39, 0,41
Tasks: 179 total,   1 running, 178 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1,8 us,  1,5 sy,  0,0 ni, 96,5 id,  0,2 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  2435356 total,  1505764 free,   494128 used,   435464 buff/cache
KiB Swap:  2488316 total,  2488316 free,        0 used.  1886872 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                    
  807 root      20   0  260792  47760  30772 S   2,6  2,0   1:41.99 Xorg                                                                       
 1631 conan     20   0   52036   3616   3024 R   1,3  0,1   0:18.47 top                                                                        
 1458 conan     20   0  407308  26284  20480 S   1,0  1,1   0:12.11 xfce4-terminal                                                             
 1503 conan     20   0 1027564 308320  91968 S   0,7 12,7  10:30.64 firefox                                                                    
   14 root      20   0       0      0      0 S   0,3  0,0   0:02.81 kworker/1:0                                                                
  675 root      20   0  392784  17712  14872 S   0,3  0,7   0:03.14 NetworkManager                                                             
 1326 conan     20   0  206976   5200   4704 S   0,3  0,2   0:00.45 at-spi2-registr                                                            
 1689 root      20   0       0      0      0 S   0,3  0,0   0:00.23 kworker/u4:0                                                               
 1705 root      20   0       0      0      0 S   0,3  0,0   0:00.31 kworker/0:2                                                                
    1 root      20   0  119792   5800   3848 S   0,0  0,2   0:04.58 systemd                                                                    
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kthreadd                                                                   
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.36 ksoftirqd/0                                                                
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                               
    7 root      20   0       0      0      0 S   0,0  0,0   0:05.48 rcu_sched                                                                  
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                     
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/0                                                                
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.03 watchdog/0                                                                 
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/1                                                                 
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/1                                                                
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.42 ksoftirqd/1                                                                
   15 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                               
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                  
   17 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                      
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 perf                                                                       
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd                                                                 
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                  
   21 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd                                                                       
   22 root      39  19       0      0      0 S   0,0  0,0   0:03.35 khugepaged                                                                 
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto                                                                     
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                     
   26 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                    
   27 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                    
   28 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md                                                                         
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq                                                                 
   33 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0                                                                    
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 vmstat                                                                     
   35 root      20   0       0      0      0 S   0,0  0,0   0:00.00 fsnotify_mark                                                              
   36 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-kthrea                                                            
   51 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld                                                                   

```

---

### Post by kc1di on 2016-05-03
Hi Jet74-5 and Welcome to Ubuntu,

Could you go to a terminal and type the following commands and list the output here. They may tell where the hold up on boot is and give clues to other problems.

```
systemd-analyze blame
```  & ```
systemd-analyze critical-chain
```

---

### Post by jet74-5 on 2016-05-03
Thank you for your reply!

Just to be clear: The black screen freeze is before the grub menu. When I power of with holding the power button I can boot again normally and then boot time seems pretty standard. Also, I might add that I have XP installed as well. This was installed before xubuntu and works normally both during shutdown and boot.

Anyway:

```
conan@conan-HP-Compaq-nx6325-EY349ET-AK8:~$ systemd-analyze blame
         11.131s accounts-daemon.service
          9.993s apport.service
          9.782s dev-sda6.device
          8.753s apparmor.service
          7.940s networking.service
          7.729s thermald.service
          7.233s speech-dispatcher.service
          6.970s pppd-dns.service
          6.968s lm-sensors.service
          6.938s systemd-user-sessions.service
          6.915s rsyslog.service
          6.501s NetworkManager-wait-online.service
          6.353s NetworkManager.service
          5.941s ModemManager.service
          5.453s grub-common.service
          5.096s systemd-logind.service
          5.078s avahi-daemon.service
          4.618s irqbalance.service
          3.252s gpu-manager.service
          1.865s lightdm.service
          1.782s systemd-tmpfiles-setup-dev.service
          1.607s systemd-udevd.service
          1.598s systemd-journald.service
          1.261s systemd-modules-load.service
          1.233s resolvconf.service
          1.226s upower.service
          1.133s sys-kernel-debug.mount
          1.120s dev-hugepages.mount
          1.117s dev-mqueue.mount
           978ms plymouth-start.service
           977ms console-setup.service
           850ms systemd-tmpfiles-setup.service
           794ms udisks2.service
           776ms ondemand.service
           713ms systemd-udev-trigger.service
           600ms wpa_supplicant.service
           546ms [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
           541ms dev-disk-by\x2duuid-ef5f5218\x2de86c\x2d4ac3\x2dbed6\x2d105602b
           531ms ufw.service
           498ms systemd-journal-flush.service
           496ms kmod-static-nodes.service
           447ms systemd-update-utmp.service
           422ms systemd-random-seed.service
           416ms systemd-sysctl.service
           415ms systemd-timesyncd.service
           399ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
           320ms plymouth-read-write.service
           257ms hddtemp.service
           256ms polkitd.service
           191ms alsa-restore.service
           155ms systemd-rfkill.service
           153ms systemd-remount-fs.service
           138ms rtkit-daemon.service
           124ms systemd-update-utmp-runlevel.service
            87ms ureadahead-stop.service
            77ms snapd.socket
            75ms rc-local.service
            70ms brltty.service
            51ms plymouth-quit-wait.service
            12ms sys-fs-fuse-connections.mount
lines 38-60/60 (END)
```

and


```
conan@conan-HP-Compaq-nx6325-EY349ET-AK8:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @34.216s
&#9492;&#9472;multi-user.target @34.211s
  &#9492;&#9472;getty.target @34.205s
    &#9492;&#9472;getty@tty1.service @34.190s
      &#9492;&#9472;rc-local.service @33.729s +75ms
        &#9492;&#9472;network-online.target @33.696s
          &#9492;&#9472;NetworkManager-wait-online.service @27.185s +6.501s
            &#9492;&#9472;NetworkManager.service @20.805s +6.353s
              &#9492;&#9472;dbus.service @15.820s
                &#9492;&#9472;basic.target @15.507s
                  &#9492;&#9472;sockets.target @15.506s
                    &#9492;&#9472;snapd.socket @15.362s +77ms
                      &#9492;&#9472;sysinit.target @15.351s
                        &#9492;&#9472;apparmor.service @6.596s +8.753s
                          &#9492;&#9472;local-fs.target @6.563s
                            &#9492;&#9472;run-user-1000.mount @31.611s
                              &#9492;&#9472;local-fs-pre.target @6.558s
                                &#9492;&#9472;systemd-remount-fs.service @6.301s +153ms
                                  &#9492;&#9472;systemd-journald.socket @2.319s
                                    &#9492;&#9472;-.slice @2.310s
conan@conan-HP-Compaq-nx6325-EY349ET-AK8:~$ 

```


/Erik

---

### Post by jet74-5 on 2016-05-05
Anyone got a clue?

---

### Post by jet74-5 on 2016-05-06
I have also tried to reinstall xenial xerus from scratch. I got the exact same symptoms.

---

### Post by Morbius1 on 2016-05-06
Don't have an answer but I have installed Xubuntu 16.04 3 times now - 2 on real hardware and 1 in Virtualbox. The only install that shuts down properly is the one in VirtualBox.

The hard drive makes a weird click sound like it really wants to power off when shutting down but the fans and the screen / monitor are still running and will continue to run unless I hold the power button on the machine for what seems like an eternity.

The silverbacks in this forum always warn not to install the xx.04 when it's released but wait for the xx.04.1 to be released. Always ignored that and never had a problem until now so I guess they were right.

---

### Post by jet74-5 on 2016-05-06
Ok, thanks for your reply. 

Actually, I have it installed on another machine and there it works flawlessly.

---

### Post by egeezer on 2016-05-06
FWIW, I had a similar problem with Xubuntu 15.10, so instead I tried the experimental Xubuntu Core ISO.  That consists of a minimal-install plus a cut-down Xubuntu desktop to which you add whatever software you want.  Liked it so much I stuck with it for the 16.04 Beta and also the 16.04 Final, both of which have been stable since installation.  
 
 
 [FONT=DejaVu Sans Mono][[FONT=Liberation Serif][SIZE=3]https://unit193.net/xubuntu/core/[/SIZE][/FONT]]("https://unit193.net/xubuntu/core/")[/FONT]
 
 
 [FONT=DejaVu Sans Mono][FONT=Liberation Serif][SIZE=3]I[/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]t [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]takes a bit of forethought to set up [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]everything you need[/SIZE][/FONT][FONT=Liberation Serif][SIZE=3], but the result has been really great, especially for my slooooow DSL connection – 555MB as opposed to 1.2GB for the full Xubuntu.[/SIZE][/FONT][/FONT]
 
 
 [FONT=DejaVu Sans Mono][FONT=Liberation Serif][SIZE=3]D[/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]isclaimer: I’m not associated with Unit193, I’m just a big fan of his/her work.[/SIZE][/FONT][/FONT]

---

### Post by jet74-5 on 2016-05-08
Thanks for the tip egeezer. I might try it out. Or downgrade to earlier xubuntu version.

Noticed another thing. It seems that sometimes at boot there's a message "a tpm error (7) occurred attempting to read a pcr value" or something like that. Don't know if it's related...

---

### Post by jet74-5 on 2016-05-09
> **jet74-5 said:**
> Thanks for the tip egeezer. I might try it out. Or downgrade to earlier xubuntu version.

Noticed another thing. It seems that sometimes at boot there's a message "a tpm error (7) occurred attempting to read a pcr value" or something like that. Don't know if it's related...

This error was solved by enabling tpm in the BIOS. I also updated the BIOS. No improvement when it comes to performance or shutdown though.

Looking at "top" now while actually doing something I can see that CPU usage runs abnormally high. Just writing these words make the firefox entry run up to 40-50%, if I scroll this page it's 60-65. If I hit reload page it goes up above 100. Doesn't really seem normally on a dual-core processor does it? There doesn't seem to be any undue hard drive access or anything like that but I'm not very good at interpreting the numbers...

Posting in the thread made the firefox CPU usage peak at 146%. Memory is at a steady 10-11% though. 

It's not just firefox. Running the software manager or libreoffice makes the cpu hit the roof as well. And everything is really sluggish. Scrolling, resizing windows, accessing menus.

---

### Post by jet74-5 on 2016-05-09
Downgraded to Xubuntu 14.04.4. Exact same symptoms.

It seems to me that the bad performance is somehow graphics related. CPU usage peaks whenever i do something that has graphic output (scrolling etc).

So I ran the script here:
[http://www.free3d.org/](http://www.free3d.org/)

It gives me about 200 fps, which seems really low considering the hardware. 

So, since it seemed graphics related I added the xorg-edgers ppa and updated graphics drivers from there.

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-core
sudo apt-get update
 sudo apt-get upgrade
```

No improvement. Starting to run out of ideas....

---

### Post by marugaca on 2016-08-23
Hi 

I'm having the same problem on my nx6325 laptop. Since I upgrade to Ubuntu 16.04 it is extremely slow. With Ubuntu 14.04 it was performing nicely.

But I do not know what to do to about the bad performance :-( 

I also had problems with the WIFI, Buetooth and rebooting (the computer hangs)

---

### Post by marugaca on 2016-08-23
Hi

I had the same problems as you, and after investigating some time I found this:

For improving performance try this:

apt-get install amd64-microcode

For enabling WIFI

modprobe -r b43; modprobe b43

For activating Bluetooth (after activating WIFI)

rfkill unblock bluetooth

For reducing fan speed:

echo 0 > /sys/class/thermal/cooling_device1/cur_state
echo 0 > /sys/class/thermal/cooling_device2/cur_state

Finally use unity-tweak-tool to disable all visual effects under "general", "desktop", and "search" sections 

If it is not installed on your system... apt-get install unity-tweak-too :-)

Hope it will help you :-)

I still have problems rebooting the computer, it hangs. And Bluetooth does not work properly, dmsg says "Bluetooth: hci0 urb ffff880074db3b40 failed to resubmit"

Reloading kernel module btusb does not solve the problem.

---

### Post by marugaca on 2016-08-23
I have solved bluetooth problems changing the firmware, I found the solution here

[http://askubuntu.com/questions/617513/bluetooth-not-connecting-to-devices-even-though-it-recognizes-themre](http://askubuntu.com/questions/617513/bluetooth-not-connecting-to-devices-even-though-it-recognizes-themre)

---

### Post by mahmod3 on 2016-08-25
The same behavior happens with me too, but it's not only Ubunut it's Mint and Archlinux too, the slowness/unresponsiveness kicks in when i do sudo apt-get upgrade, CPU peaks and fans go high when i run an GUI app, Intel 4770K, R9 290X, Samsung SSD EVO 840 120GB

---

### Post by dqsully on 2016-09-05
Same issue, same computer, running default Ubuntu. In doing more searching I found this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). It appears in version 16.04 the original fglrx driver provided by AMD is not supported anymore. For multiple reasons, Ubuntu now defaults to using the 'radeon' and 'amdgpu' drivers for AMD GPUs (radeon for our chipset).

Also, correct me if I'm wrong, but the nx6325 laptop contains an RS482 or RS485 chipset. However, I have found that Ubuntu is treating it like an RS480.

I hope this gives someone a lead to follow, I'm still pretty new to Linux. Personally, I wonder if the new driver is missing compatibility with the Xpress 1150 graphics and treating it like the closest chip to it: the Xpress 200.

---

### Post by oygle on 2016-10-18
I was using Kubuntu 14.04

Did a fresh installation today to 16.04.1 . The installation worked flawlessly. But after a reboot, Kubuntu is so slow. When I'm entering data via Kate, it takes 3 to 4 seconds, sometimes much more, for the characters to appear. Even at konsole, a command is entered, and the characters take about 4 seconds to display. Poor response in other applications.

The computer is "old" but it ran 14.04 very well. There are about 300,000 files and folders to sum at 207 Gb, and file searching and general navigating was never a problem with 14.04. Under 14.04 when a character was keyed in, the character would display as it was being keyed in.

Now with 16.04.1 , the display for any 'window' activity is very poor, sometimes black, or parts of grey, and then finally some words appear.

The computer is an [ASUS P5Q Pro]("https://www.asus.com/Motherboards/P5Q_PRO/specifications/")

---

### Post by oygle on 2016-10-18
Here are some brief specs for the computer, purchased in 2008

* ASUS Motherobard -- Model: P5QL-PRO
* 4GB RAM 2x 2GB Sets -- T800UX2GC4 (DDR2 800)
* Asus Video -- Model: Card EN9400GTSLN-HTP-512)
* Intel CPU (BX80562Q6600) 2.4Ghz Quad Core

---

### Post by oygle on 2016-10-22
Here are the 2 major problems I experienced.

1. [Fresh install of 16.04.1 - Now mount problems ]("https://ubuntuforums.org/showthread.php?t=2340456") - now resolved

2. [Fresh install of 16.04.1 - Now display is very slow ]("https://ubuntuforums.org/showthread.php?t=2340444") - Since the mount issues were resolved, video/display is much better. Not as good as 14.04, but much better.

---

### Post by thosecars822 on 2016-12-11
> **jet74-5 said:**
> Hello,

I have a fresh install of Xubuntu 16.04 (64-bit) and something seems to be wrong. I really have no idea what might be the problem, and any help is very much appreciated.

The computer is a HP nx6325. It's old, but has been running flawlessly on Xubuntu before (14.04 32-bit)

Symptoms:
-Slow input. The pointer is responsive but keyboard input is slow. So is navigating menus and applications.
-Fan running constantly at full speed. However, the computer does not seem hot at all.
-Shutdown behaves a bit odd. Hard to explain, but it doesn't sound right, like it just cut's power at some point.
-Boot behaves odd. It will not start normally but is just locked at a black screen. At this point I am forced to do a hard power off. After that it boots normally, but then next time it wont boot. The rebooting function always freezes up. Also I get a message every boot that /dev/sda6 is clean. Whatever that means. 

Neither cpu nor ram seems to be under heavy load. This is the output of "top":



```
top - 11:30:36 up 31 min,  2 users,  load average: 0,33, 0,38, 0,41
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
top - 11:31:04 up 31 min,  3 users,  load average: 0,39, 0,39, 0,41
Tasks: 179 total,   1 running, 178 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1,8 us,  1,5 sy,  0,0 ni, 96,5 id,  0,2 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem :  2435356 total,  1505764 free,   494128 used,   435464 buff/cache
KiB Swap:  2488316 total,  2488316 free,        0 used.  1886872 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                    
  807 root      20   0  260792  47760  30772 S   2,6  2,0   1:41.99 Xorg                                                                       
 1631 conan     20   0   52036   3616   3024 R   1,3  0,1   0:18.47 top                                                                        
 1458 conan     20   0  407308  26284  20480 S   1,0  1,1   0:12.11 xfce4-terminal                                                             
 1503 conan     20   0 1027564 308320  91968 S   0,7 12,7  10:30.64 firefox                                                                    
   14 root      20   0       0      0      0 S   0,3  0,0   0:02.81 kworker/1:0                                                                
  675 root      20   0  392784  17712  14872 S   0,3  0,7   0:03.14 NetworkManager                                                             
 1326 conan     20   0  206976   5200   4704 S   0,3  0,2   0:00.45 at-spi2-registr                                                            
 1689 root      20   0       0      0      0 S   0,3  0,0   0:00.23 kworker/u4:0                                                               
 1705 root      20   0       0      0      0 S   0,3  0,0   0:00.31 kworker/0:2                                                                
    1 root      20   0  119792   5800   3848 S   0,0  0,2   0:04.58 systemd                                                                    
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.01 kthreadd                                                                   
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.36 ksoftirqd/0                                                                
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                               
    7 root      20   0       0      0      0 S   0,0  0,0   0:05.48 rcu_sched                                                                  
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                     
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/0                                                                
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.03 watchdog/0                                                                 
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 watchdog/1                                                                 
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.01 migration/1                                                                
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.42 ksoftirqd/1                                                                
   15 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                               
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                  
   17 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                      
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 perf                                                                       
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 khungtaskd                                                                 
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                  
   21 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd                                                                       
   22 root      39  19       0      0      0 S   0,0  0,0   0:03.35 khugepaged                                                                 
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto                                                                     
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                     
   26 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                    
   27 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                    
   28 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md                                                                         
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq                                                                 
   33 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kswapd0                                                                    
   34 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 vmstat                                                                     
   35 root      20   0       0      0      0 S   0,0  0,0   0:00.00 fsnotify_mark                                                              
   36 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-kthrea                                                            
   51 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld                                                                   

```

Hallo

I have exactly each and all of the same problems you described with this computer Compaq nx6325. I have tried with both lubuntu 14.04 and 16.10 and both of them have the same problems you described. If anyone finds a solution, I will be eager to see it. Thanks in advance.

---

### Post by thosecars822 on 2016-12-31
Do you know what other free operative system might work for this computer Compaq nx6325? With Lubuntu it is of no use whatsoever because it runs really slow...Just typing sentences in a wordprocessor takes forever......
If you already have installed another operative system that works, please let me know. This computer just needs to be able to surf websites in the internet by means of Wifi. So it does not need anything secial.
Thanks

---

### Post by arthur333 on 2017-01-10
I am running xubuntu 16.04 on a nx6325. The problem seems to be the newer kernel (3.something in 14.04 ran just fine) which seems to **** up acpi detection.

The bad performance originates with the CPU, which is stuck on 800 MHz - and does not speed up when loaded.

Adding the kernel boot parameter "acpi=noirq" seems to improve some of the issues - at least, CPU frequency switching resumes to work, which solves the bad performance problem.

 However, there seem to be additional issues with power management (for example, the only available energy profiles are "suspended" and "standby" - no higher profiles can be selected).

Is there a changelog somewhere, which details the changes in power management between kernels 3.13 and 4.4?

---

