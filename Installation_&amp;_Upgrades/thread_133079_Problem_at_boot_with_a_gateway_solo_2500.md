---
title: "Problem at boot with a gateway solo 2500"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by ImperialHunter904 on 2006-02-19
Hello, I have a 2000 gateway solo 2500 laptop [more specs further down]

I installed ubuntu, nothing during the installation process went wrong. I also created a new partition for ubuntu (I have very little experince with paritioning, just to add in) Now, after I rebooted my computer when it was done installing,  I get the GRUB loading stage 1.5 on the boot screen (after the specs), after that I get the ubuntu log in screen (loading modules,mounting root files, etc, all ok, the last one I see before the error is creating intial device nodes).

After I see creating intial device nodes on the kernel boot, I get an error saying 

[4294706.242000] Critical temperature reached (245 C), shutting down
(few seconds)
[4294706.242000] Critical temperature reached (245 C), shutting down
(few seconds)
[4294706.242000] Critical temperature reached (245 C), shutting down
(laptop shuts down)

Now, I left my computer alone for about 10 hours, thinking this really was an over heating problem, same thing. I checked the bios to see if it had anything on temperature readings/sensors, nothing.

I then proceeded to load Ubuntu via recovery mode. 3 of the checks fail. 

rm: cannot remove /ect/hotplug/.run/net.enable': read-only file system
*Stopping kernal log daemon
rm: cannot remove' /var/run/klogd/kmsg' read-only file system  [fail]

Critical temperature reached (245 C), shutting down 

Sending all processes the KILL process 

saving random seed...   [fail]

deconfiguring network interfaces [fail]

soon after that it shuts down, I cant really catch what it says, something about terminating devices.

I then formated the partition, made a new one ,reinstalled ubuntu, and I get the exact same thing.


My laptop is a gateway solo 2500

cpu = Pentium II 333 MHZ
ram = 128mb
HD  = 6gb

If you need any more information, please ask :). Thanks!

---

### Post by Harii on 2008-06-08
I have a solo much like yours
cpu = Pentium II 300 MHZ

It runs very warm and was wondering if you ever fixed your problem.
Most likely given the time of post --you should have a new laptop by now?

---

