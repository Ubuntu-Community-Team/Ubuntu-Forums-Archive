---
title: "Dual Intel CPU won't boot after installing 17.04 server"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by balsax on 2017-04-23
I just finished installing Ubuntu server on an Intel S2600C0 motherboard with dual Intel E5-2670 CPU's.  The system will only boot with one CPU installed.  When I install both CPU's, the system hangs shortly after selecting OS in grub.  These are the last few messages shown during boot before system hangs...

```
[ 0.244041] x86: Booting SMP configuration:
[ 0.244133] .... node #0, CPUs:       #1
[10.244389] smpboot: do_boot_cpu failed(-1) to wakeup CPU#1
```

shortly thereafter, the system reboots.

I have tried many things from playing with BIOS settings to swapping CPU's to rearranging memory to different versions of Ubuntu.  Nothing seems to work and the problem persists.  The only way I can get the OS to boot is to remove the second CPU.  What is strange is that the BIOS recognizes the second CPU when it is installed and that the system boots shortly past grub then fails.  I did have a difficult time installing Ubuntu since the system would reboot after grub using install CD until I removed the second CPU.  After that, everything installed fine.  Could this problem be because I installed Ubuntu with only one CPU?
Please let me know what other information would be beneficial.  Thanks in advance for any advice you have!
-Mike

---

### Post by fabio.hipolito on 2017-04-26
Similar problem with a Lenovo P50 runing Ubuntu-Gnome 17.04, every once in a while the boot hangs at line
x86: Booting SMP configuration

It appears that this only affects the laptop when running on battery, as whenever I plug it to power boot proceeds normally.
The same hardware runs fine with Ubuntu-Gnome 16.04 LTS

---

### Post by fabio.hipolito on 2017-05-22
Hi, this problem was solved in my machine by updating the BIOS to the latest version, as discussed here
[https://answers.launchpad.net/ubuntu/+question/632650](https://answers.launchpad.net/ubuntu/+question/632650)

---

