---
title: "Hangs and X (DRM) failures on 12.04 with Ivy Bridge MB"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by PencilGeek on 2012-07-13
I just bought a brand new Asus Ivy Bridge motherboard, installed fresh 12.04 download. About one of four boots, X won't start. The Xorg log file complains of DRM failures.
 
When the desktop is running, the system will occasionally hard hang. It hard hangs so bad that the RESET button won't recover it, but POWER button will.
 
I've searched the web, and found this is a common problem with Ivy Bridge motherboards (oh great!).
[http://intellinuxgraphics.org/2012.02.html](http://intellinuxgraphics.org/2012.02.html)
[INDENT]
*Additionally, the following stability patches are currently available in the **drm-intel-fixes** branch and should be available on the stable **3.2.x** kernel after this release:*
[LIST]
[*]*Stability fixes for hard hangs on Ivy Bridge platform: those patches fix occasional hard-hangs on Ivy Bridge platforms when running GL workloads:*[*patch 1*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015000.html")*,*[*patch 2*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015001.html")*,*[*patch 3*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015002.html")*,*[*patch 4*]("http://lists.freedesktop.org/archives/intel-gfx/2012-February/015003.html")*.*
[/LIST]
[/INDENT]So I downloaded the Ubuntu source, compiled it, patched the drm-intel fixes, recompiled the kernel; installed it. Then I updated the libdrm as instructed at the site mentioned above. But none of it has helped. I'm still getting DRM errors in Xorg log file, and still getting occasional hard hangs. It's forced me to run in terminal mode until this is sorted out.
 
Motherboard: Asus P7Z77-V Pro
CPU: Intel i7 3770K
Memory: 16GB DDR3 1600M
Boot disk: Crucial M4 256GB
Swap disk: 256GB SATA
 
Log files:
[http://www.rcollins.org/public/Asus/](http://www.rcollins.org/public/Asus/)
[FONT=Courier New][     6.214] (EE) intel(0): [drm] failed to set drm interface version.
[     6.216] (EE) intel(0): Failed to become DRM master.
[/FONT]
 
It looks like the Intel Ivy Bridge support has been churning for a while. Has it stabilized? Is there a known solution to this, further patches. Any ideas?

---

### Post by clintspann on 2012-07-16
I'm running 12.04 with Ivy Bridge GT2.  

This is my machine:  [http://www.frys.com/product/7103322?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/7103322?site=sr:SEARCH:MAIN_RSLT_PG)

Chipset: Intel® H77
Processor: Intel® Core&#8482; i7-3770
Graphics:  Intel HD4000 Integrated Graphic

System randomly hangs.  Have to do power down and restart.  Errors I've observed are as follows:

[  738.394841] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[  738.394849] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[  739.894553] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung

AND

[   737.052] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Device or resource busy.
[   740.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Device or resource busy.
[   740.068] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[   740.068] (EE) intel(0): When reporting this, please include i915_error_state from debugfs and the full dmesg.

Any help is greatly appreciate.  Otherwise the machine runs great.  Hope we can sort this out soon.

---

### Post by clintspann on 2012-07-16
It looks like this solution has worked for everyone who has tried it:

[http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html)

Simply upgrade the kernel.

I will try this as well.

---

### Post by PencilGeek on 2012-07-16
> **clintspann said:**
> It looks like this solution has worked for everyone who has tried it:
 
[http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html)
 
Simply upgrade the kernel.
 
I will try this as well.
 
I upgraded to k3.4 last week and the hang issue does seem to be resolved.  However, the DRM error in Xorg.0.log still persists on about 1 of 4 boots.  When it happens, the gui manager fails to load.  I applied the patches that claimed to fix the problem, but the problem still persists.  It's the same problem quoted in my first post.
 
[FONT=Courier New][ 6.214] (EE) intel(0): [drm] failed to set drm interface version.
[ 6.216] (EE) intel(0): Failed to become DRM master.[/FONT]


So one problem down, one problem to go.

---

### Post by OliHe on 2012-07-17
Hello together

i had exactly the same issue while booting Ubuntu 12.04. I also have an up-to-date ASUS-Board with Z77-Chipset and an IvyBridge i7-3xxxx CPU.

My 'solution' is very simple:
```
# in the upstart-config-file /etc/init/lightdm.conf
...
# add the following line just above the exec-Call to "lightdm" :
sleep 5
...

```


The idea behind:
It's a race-condition which happens if your system boots extremly fast (fast CPU and fast boot-SSD). The kernel switches at some point to a high-res-text-mode (i think with DRM). And through the lightdm-Script the X-Server will be startet, which also wants to switch to some Graphics-Mode (also with DRM). And perhaps the second one comes too fast, so that DRM is still 'busy' (or however you want to describe this).

A shorter sleep than 5 second smay also be sufficient. I didn't try this yet, i wanted to share my idea as soon as possible with you.

Greetings from switzerland
Oli

---

### Post by anastasios on 2012-07-19
Same set up here. I just ran the upgrade to kernel 3.3 and will post back if there are any further issues with either hanging or drm errors in dmesg. Might help confirm for someone that this fix does work.

---

### Post by anastasios on 2012-07-29
Confirming this fix. Online for over a week without crashes and doing normal ops that caused crashes previously. 

# uptime
 10:11:11 up 8 days, 45 min,  9 users,  load average: 0.81, 1.13, 1.45

---

### Post by DGINSD on 2012-08-17
Could you give a little more clarification on this fix?

---

### Post by leespa on 2013-04-05
This worked for me - thanks all.

I was getting: 

```
/var/log/Xorg.log

(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
(II) intel(0): Creating default Display subsection in Screen section
```

Added:

```
/etc/init/lightdm.conf 

sleep 2

    exec lightdm
end script
```

lightdm now loads properly. Easy fix.

This is on a fast system too - Intel DH67BL mobo, i3770 cpu + Samsung 830 128 GB SSD. Typical boot-time approx 15 sec to lightdm.

---

