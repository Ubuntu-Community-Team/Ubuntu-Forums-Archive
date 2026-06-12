---
title: "ubuntu 16.04 slow, why???"
date: 2017-09-07
forum: Installation &amp; Upgrades
---

### Post by jaxom98 on 2017-09-07
Uefi mobo  128Gb ssd data drive 2Tb  4Gb ram
dual booted win7 / ubuntu 16.04
Old OS was ubuntu14.04 and booted up relatively quickly(40 seconds).
Upgraded 14.04 to 16.04, - slooow bootup. Is approximatly 80 seconds to boot.  Win 7 boots up in 60 seconds. 

2nd computer,
bios mobo 500Gb hdd  4Gb ram
clean install of 16.04  and got the same slooow boot times. Why is 16.04 a slow OS to boot up from upgrade and clean install?  

Note this machine was running 14.04 with similar  boot times as the above computer.

---

### Post by BenginM on 2017-09-08
1st, Make sure the UUID for the SS/HD disk in  /etc/fstab match the UUID entire of sudo blkid.
2nd, you may want to adjust the disk cache ..

3rd, You can find out which service takes how much time to finish starting up by entering the following command in terminal: 
$ systemd-analyze blame

## You may also wish to see a graphical detailed view of your system boot  procedure. you can generate a plot bootshart image. in a terminal run: $  systemd-analyze plot > bootchart.svg
the .svg file will be saved in your home directory and you can view it with an image viewer.

So disable services that you don't use at all, and apps you don't need at start up.

My current system with a HDD flyin' Xubuntu 17.10 boots at ..
```

sary@tru-uli63:~$ systemd-analyze
Startup finished in 6.395s (kernel) + 41.314s (userspace) = 47.710s

```

---

### Post by jaxom98 on 2017-09-09
Excuse the delay in reply, work got in the way.
#1 and #2 how do I find them?
#3 In terminal, Any command with "systemd-analyse"in it comes up "$  command not found" ??? what is going on.
I still don't know what is running or how to find and shutdown unused services and apps

New data, discovered via disk usage analyser that new data is being dumped in the sshd and has filled that drive to 100 Gb of 128Gb.  All data should be going to the data drive. 
How do I reset data to go to data drive?
How do I transfer data on OS drive(sshd) to data drive?

---

### Post by ian-weisser on 2017-09-09
> **jaxom98 said:**
> #3 In terminal, Any command with "systemd-analyse"in it comes up "$  command not found" ??? what is going on.

You seem to have misspelled it. See the correct spelling above and try again.

---

### Post by Geoffrey_Arndt on 2017-09-09
What data are you referring to?   You can just cut/paste data from one location to the other of your choice using the files (aka Nautilus) manager.

Each program that generates data usually has default save options or properties that can be adjusted.

Re finding out what's running, you can run "htop" from the terminal or just open the "System Monitor" gui program.:   

NOTE    Just don't PANIC.    You can goto YouTube to search for tutorials on all your Linux questions.    Then use a simple program like "CherryTree" to create your notes or knowledge base.

---

### Post by jaxom98 on 2017-09-12
Below is the output from the "systemd-analyze blame" command.
  How do I decide which are essential and which are not and can be turned off or set for delayed start up?  
```
          7.636s NetworkManager-wait-online.service
          5.284s udev-configure-printer@-devices-pci0000:00-0000:00:12.2-usb1-1\
           991ms apt-daily.service
           970ms dev-sda5.device
           653ms udisks2.service
           545ms apt-daily-upgrade.service
           528ms epoptes.service
           333ms apparmor.service
           210ms ModemManager.service
           192ms accounts-daemon.service
           181ms upower.service
           166ms systemd-logind.service
           143ms keyboard-setup.service
           129ms grub-common.service
           128ms networking.service
           127ms console-setup.service
           110ms apport.service
           110ms irqbalance.service
           106ms ondemand.service
           105ms systemd-journald.service
           104ms systemd-modules-load.service
            98ms speech-dispatcher.service
            92ms NetworkManager.service

```lines 1-23
 Also in my meddling I have some how changed the startup screen. There is now what looks like a list of all the processes starting up ( about 11/2 - 2 screens worth) with a time, 1min 30seconds, and a timer counting up to the 1min 30secondmark.
This post was logged last night but did not go through so I reposted tonight.

---

### Post by ian-weisser on 2017-09-12
I'm not seeing anything out-of-line there.
Systemd already delays unnecessary services and prioritizes critical-path services.

---

### Post by HankB on 2017-09-13
>>>> ... with a time, 1min 30seconds, and a timer counting up to the 1min 30secondmark.

Can you tell us what else is on that line? I believe that is systemd counting down something it is waiting for (that is not happening.) After 90 seconds it gives up and completes booting.

I have seen something similar when I had done something that caused drive UUID or device name to change and that caused systemd to delay/timeout on boot.

---

### Post by jaxom98 on 2017-09-18
The problem was eventually tracked down to systemd trying to find  a nonexistant swap partition on the sdb drive.( sdb is data only.  sda contains the OS's and partitions.)
 The instruction was cancelled/ stopped. This restored the ubuntu OS to it's textbook speedy boot times.
This was done for me by a third party ,so I can't say what  procedure was used.
To the posters who tried to help, thank you.  This is the first time I tried to tackle a boot problem.

---

