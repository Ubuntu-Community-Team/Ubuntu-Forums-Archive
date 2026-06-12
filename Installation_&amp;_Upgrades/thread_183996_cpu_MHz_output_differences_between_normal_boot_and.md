---
title: "cpu MHz output: differences between normal boot and hibernation"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by henriquemaia on 2006-05-29
I found this while posting on this [thread]("http://ubuntuforums.org/showthread.php?p=1063836#post1063836").

It's rather simple. The output of 

**cat /proc/cpuinfo**

have different cpu MHz value after a normal boot and after hibernation.

In my case, under a normal boot I get:

cpu MHz         : 2210.220

After a hibernation, I get:

cpu MHz         : 1004.645

This is not very serious, since I don't feel any performance lost. I just want to understand why. Is this normal or a bug?

I'm running Dapper 64bit RC. Can anyone check this on their systems?

---

### Post by henriquemaia on 2006-05-29
A small bump, to see if anyone can test this out.

---

### Post by henriquemaia on 2006-05-30
Another little bump.

---

### Post by henriquemaia on 2006-05-31
Following another thread, I installed **cpufrequtils**. 

After hibernation, the output of cpufreq-info was:

analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  **current CPU frequency is 1000 MHz.**

So I started to mess with cpufreq-set to change this. After passing the command **cpufreq-set -c 0 -g performance**, the output of the previous command was:

analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  **current CPU frequency is 2.20 GHz.**

Can anyone try this out on their systems, before and after a hibenation?

---

### Post by RAOF on 2006-05-31
This sounds like expected behaviour.  Try adding the Gnome "CPU Freq" applet to one of your panels - you should see the CPU frequency change, depending on what you're doing (high processor tasks will have full CPU frequency, just browsing the web will have min CPU freq, etc).

If this **doesn't** happen after a resume from hibernate, then it's a bug, and we should investigate the cause/post a bug on malone.

---

### Post by henriquemaia on 2006-05-31
[quote=RAOF]This sounds like expected behaviour.  Try adding the Gnome "CPU Freq" applet to one of your panels - you should see the CPU frequency change, depending on what you're doing (high processor tasks will have full CPU frequency, just browsing the web will have min CPU freq, etc).

If this **doesn't** happen after a resume from hibernate, then it's a bug, and we should investigate the cause/post a bug on malone.[/quote] 
Thanks for your reply. I have added the CPU Frequency Scaling Monitor applet and now I notice that the cpu is not always working at full speed. 

I have tested after a normal boot and after hibernation. I didn't know about this scaling, since I have turned if off on the BIOS. Once again, thanks a lot for your reply.

---

### Post by RAOF on 2006-05-31
[QUOTE=henriquemaia]Thanks for your reply. I have added the CPU Frequency Scaling Monitor applet and now I notice that the cpu is not always working at full speed. 

I have tested after a normal boot and after hibernation. I didn't know about this scaling, since I have turned if off on the BIOS. Once again, thanks a lot for your reply.[/QUOTE]
I didn't know that it would work even if disabled in the BIOS.  But when it works, it should have no downside: your computer runs more cooler/less power when you don't need the full power of the CPU (such as almost all the time), and you get the full CPU speed whenever you **do** need it :)

---

### Post by henriquemaia on 2006-05-31
[quote=RAOF]I didn't know that it would work even if disabled in the BIOS.  But when it works, it should have no downside: your computer runs more cooler/less power when you don't need the full power of the CPU (such as almost all the time), and you get the full CPU speed whenever you **do** need it :)[/quote]

Yes, you're right. On the first post I pointed out that I was not feeling any lack of performace although the different cpu MHz values. It's also good to know that I have this, since I have my computer on a attic and during day time it gets very hot here (30º+).

This also adds some points on my satisfaction of using Dapper. This is going to be a very impressive release.

Thanks again for your help.

---

