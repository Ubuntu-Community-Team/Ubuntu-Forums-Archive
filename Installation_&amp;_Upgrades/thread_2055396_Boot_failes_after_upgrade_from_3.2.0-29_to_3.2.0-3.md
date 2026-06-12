---
title: "Boot failes after upgrade from 3.2.0-29 to 3.2.0-30"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by flacone on 2012-09-09
Hello,
recently I uprgaded Ubuntu from 3.2.0-29 to 3.2.0-30 and the boot process fails shortly after the Ubunu logo shows up. Up to two dots below marking the progress show up and then it hangs. However if I boot with the older 3.2.0-29 Kernel it still works.
Is it better to downgrade again and wait for newer versions where the problem may be solved. If so, how to downgrade? Or how to select the older Kernel by default at bootup?

tnx

---

### Post by kc1di on 2012-09-09
if you desire to remove the new kernel you can do that by the following terminal commands 

```
sudo apt-get purge <exact name of kernel you want to remove>
```

you can find the kernel name your currently using by typing
```
uname -r
```

if you want to leave the kernel installed and us a different one you will have to modify the /etc/default/grub file to boot the one you want 

in the /etc/default/grub file look for the line that looks like this
```
Default=0
```
change it to the number of the grub entery that contains the kernel you want to boot. 
I'm assuming it would be ```
Default=2
```
Remember grub starts counting at 0
so if you do a ```
sudo update-grub
```
the first line in the list will be zero , second line would be 1 third line 2 , etc. 

do a sudo update-grub and reboot to old kernel

---

### Post by flacone on 2012-09-09
Thank you! 
I chose to select the default entry (2) for Grub. That works. 

Even though I am quite curious what could be the problem, and how likely it is that the problem will be solved in future versions.

---

### Post by kc1di on 2012-09-09
> **flacone said:**
> Thank you! 
I chose to select the default entry (2) for Grub. That works. 

Even though I am quite curious what could be the problem, and how likely it is that the problem will be solved in future versions.

I'm not a developer but from what you discribed sounds like it may be a broken video driver , that is the video driver may not be compatible with the new kernel.  But that's just a guess.n Sometimes the drivers don't keep up immediately with the newer kernel. 
good luck
Keep smiling :)

---

### Post by itsjustarumour on 2012-09-10
> **flacone said:**
> Hello,
recently I uprgaded Ubuntu from 3.2.0-29 to 3.2.0-30 and the boot process fails shortly after the Ubunu logo shows up. Up to two dots below marking the progress show up and then it hangs. However if I boot with the older 3.2.0-29 Kernel it still works.
Is it better to downgrade again and wait for newer versions where the problem may be solved. If so, how to downgrade? Or how to select the older Kernel by default at bootup?

tnx

Just had exactly the same thing with updating from 3.2.0-29 to 3.2.0-30 kernel.

---

### Post by itsjustarumour on 2012-09-10
> **kc1di said:**
> what you discribed sounds like it may be a broken video driver , that is the video driver may not be compatible with the new kernel.  But that's just a guess.n Sometimes the drivers don't keep up immediately with the newer kernel

Thats as may be, but if so then its pretty p*ss poor QA on a Long Term Support Release thats been out for nearly 5 months and is being touted as stable and solid enough for business Desktop use (I'm on 12.04 64-bit).  I know how to get round it easily enough, but thousands of office workers using Ubuntu won't.

---

### Post by flacone on 2012-09-22
hello again.
After booting into the recovery mode with the 3.2.0-30 Kernel I upgraded to the 3.2.0-31 Kernel and with this new one its still not booting. It hangs with "BUG: soft lockup - CPU#1 stuck for 22s! [modeprobe:1067] then some information about the call trace And repeating it. Here is a screenshot:

[IMG]http://ubuntuone.com/04V0ZzGma1EklNb9WUFxaD[/IMG]

So after the problem is not solved in the newer Kernel I lost a bit my hope. Shall I do some kind of bug report?

My system is a IBM Thinkpad Lenovo T60.

---

### Post by flacone on 2012-10-12
Kernel 3.2.0-32 is installed: the same issue. 3.2.0-29 works fine, > 29 does freeze during booting

---

### Post by dino99 on 2012-10-12
> **flacone said:**
> Kernel 3.2.0-32 is installed: the same issue. 3.2.0-29 works fine, > 29 does freeze during booting

so its a regression, report it

---

### Post by flacone on 2012-10-24
Okay. So I filed a bug report. And hopefully I did it on the right place:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070994)

If somebody has the same behaviour should confirm this bug there.

Meanwhile I tried it also with the new Ubuntu 12.10 and the Kernel 3.5.0-17 and the same thing occurred. The error messages are (still):

"Loading the saved-state of the serial devices..."
"Illegal UART type: undefined"
"/dev/ttyS1 at 0x02f8 (irq = 3) is a undefined"
"[ 34.608007] serial8250: too much work for irq3"
"[ 34.611448] serial8250: too much work for irq3"
"[ 34.617296] serial8250: too much work for irq3"
"[ 60.084018] BUG: soft lockup - CPU#1 stuck for 22s! [modeprobe:1204]"
"[ 95.116005] INFO: rcu_sched detected stalls on CPUs/task: { 0} (detecte by 1, t=15002 jiffies)"
"[ 95.116009] INFO: Stall ended before state dump start"
"[ 116.084018] BUG: soft lockup - CPU#1 stuck for 23s! [modeprobe:1204]"

---

### Post by Pilot6 on 2012-10-24
I think the problem is not a bug. Did you install proprietary video drivers not from a repository? If yes, you need to reinstall them after every kernel update.

---

### Post by flacone on 2012-10-24
> **Pilot6 said:**
> I think the problem is not a bug. Did you install proprietary video drivers not from a repository? If yes, you need to reinstall them after every kernel update.
Why do you think the problem is related to a proprietary video driver? Anyway I did not installed such a driver. I have an ATI Mobility Radeon X1400 btw.

---

### Post by Pilot6 on 2012-10-24
I think it, because it is a very common problem. If you install AMD/ATI drivers using a file downloaded from AMD site and after that update kernel, system won't start properly.

---

### Post by flacone on 2012-10-24
> **Pilot6 said:**
> I think it, because it is a very common problem. If you install AMD/ATI drivers using a file downloaded from AMD site and after that update kernel, system won't start properly.

That makes sense. Thank you for the suggestion. But ("unfortunately") I did not installed downloaded drivers.

---

### Post by Pilot6 on 2012-10-24
Then try to install them using Additional drivers.

---

### Post by flacone on 2012-11-20
I played a bit around. But apparently the proprietary drivers does not work. 
I am still running Ubuntu 12.10 with the old 3.2.0-29 kernel since the newer do not work. However I tried running with a start up disk and there the computer runs. So I will probably give up to solve the issue and when i have time (lol) I will reinstall Ubuntu

---

