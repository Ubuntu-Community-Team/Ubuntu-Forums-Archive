---
title: "VirtualBox - kernel driver not installed after upgrade to Lucid"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by lava on 2010-05-04
Hello all,

I upgraded to Lucid last night, and I'm getting this error when I try to run virtualbox-ose:

> Kernel driver not installed (rc=-1908)

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.

I try it, then I get:
> modprobe vboxdrv
FATAL: Module vboxdrv not found.

I have no idea what's going on. Can anyone help? The version of virtualbox is 3.1.6-dfsg-2ubuntu2

---

### Post by BlueVark on 2010-05-04
Hi,

Had same problem...just do what the error message says.  Execute 'modprobe vboxdrv' as root.  Or open terminal and copy/paste sudo 'modprobe vboxdrv'

Hope this helps.

---

### Post by lava on 2010-05-04
it's the same thing,

FATAL: Module vboxdrv not found.

---

### Post by lechien73 on 2010-05-04
What happens if you try recompiling the kernel driver?

```
sudo /etc/init.d/vboxdrv setup
```

I had to recompile it before VirtualBox would work for me.

---

### Post by lava on 2010-05-05
/etc/init.d/vboxdrv didn't exist on system for some reason. I ended up uninstalling and reinstalling via synaptic. It's working now.

---

### Post by piedro on 2010-05-10
I have exactly the same problem. 

reinstalled vbox with synaptic - and it works! 

BUT ONLY UNTIL REBOOT!!! 

After that "sudo /etc/init.d/vboxdrv setup" says it doesn_t exist again? 

What's wrong here? 
I'm using the official Lucid Lynx Repositories? 

plz help, 
thx, 
piedro

---

### Post by piedro on 2010-05-10
I installed the virtualbox-ose-source also but still can't find any "/etc/init.d/vboxdrv" ... 

Another manual says you have to add users to the group vboxusers ... 
That group doesn't exist either - no matter how often I reinstall! 

plz help, 
piedro

---

### Post by baldeante on 2010-05-10
Hello did you try to remove the old vbox rep and set the new one ??

Check this virtual box page

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

In my case the upgrade just disable the vbox rep ... i just added the new one seems to be working ...

---

### Post by piedro on 2010-05-11
Yes I did. Doesn't work still. 

dmesg gives me: 
> [   28.399141] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.399141] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   28.399141] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   28.399142] vboxdrv: the usage of hardware performance counters by
[   28.399143] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   28.399146] vboxdrv: Found 2 processor cores.
[   28.399214] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d62a20
[   28.399227] vboxdrv: fAsync=0 offMin=0x15f offMax=0x1ccb
[   28.399263] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.399264] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[   28.818074] vboxguest: exports duplicate symbol RTMemExecFree (owned by vboxdrv)
[   29.704567] ppdev: user-space parallel port driver
[  143.075118] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  143.075122] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[  143.075123] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[  143.075124] vboxdrv: the usage of hardware performance counters by
[  143.075125] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[  143.075129] vboxdrv: Found 2 processor cores.
[  143.075244] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d62a20
[  143.075259] vboxdrv: fAsync=0 offMin=0x20a offMax=0x17a9
[  143.076319] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  143.076322] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[  143.283532] vboxguest: exports duplicate symbol RTMemExecFree (owned by vboxdrv)
[  508.763556] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  508.763559] vboxdrv: Successfully done.
[  508.763560] vboxdrv: Found 2 processor cores.
[  508.763635] VBoxDrv: dbg - g_abExecMemory=ffffffffa0f26a20
[  508.763646] vboxdrv: fAsync=0 offMin=0x132 offMax=0x73e
[  508.763687] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  508.763688] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[  508.970431] vboxguest: exports duplicate symbol RTMemExecFree (owned by vboxdrv)
[  532.751100] vboxguest: exports duplicate symbol RTMemExecFree (owned by vboxdrv)
[  624.564974] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  624.564977] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[  624.564978] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[  624.564978] vboxdrv: the usage of hardware performance counters by
[  624.564979] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[  624.564982] vboxdrv: Found 2 processor cores.
[  624.565478] VBoxDrv: dbg - g_abExecMemory=ffffffffa1165a20
[  624.565492] vboxdrv: fAsync=0 offMin=0x15f offMax=0x19ce
[  624.565874] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  624.565876] vboxdrv: Successfully loaded version 3.1.8 (interface 0x00100001).
[  624.773174] vboxguest: exports duplicate symbol RTMemExecFree (owned by vboxdrv)

I tried 
> echo 2 > /proc/sys/kernel/perf_counter_paranoid 

but that gives me: 
> no such file or directory

plz help someone, 
Virtualbox either as OSE or SUN version was running no problem at all all the time, just after Lucid Lynx update stopped working ... 

thx, 
piedro

---

### Post by redsparrow on 2010-05-12
I was having the same problem.

I opened Synaptic and highlighted all of the installed VirtualBox OSE packages and selected "mark for reinstallation" and applied the change.  This seemed to rebuild the required modules against the current kernel and now everything is working fine.

---

### Post by piedro on 2010-06-04
Yes! 

Seems like new package versions fixed the problems. 

thx, 
p.

---

