---
title: "Issues with kernel 11.04 and 11.10"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Llwynn on 2011-11-07
Tried both upgrades from 10.04 to 11.04 and from 11.04 to 11.10

AND

tried clean installs of 11.04 and 11.10 

and in each case, the current kernel (for 11.10) and the previous kernel (shipped with 11.04) fails to boot past grub, resulting in rebooting in an endless cycle.

If I choose to boot using the kernel provided with 10.xx it boots fine and loads both 11.04 and 11.10, however it fails to auto-up my eth card, resulting in requiring me to "sudo ifconfig eth0 up" and "add a connection".

Attempted to use each version of the NVidia drivers available, resulting in my having to recovery console remove them and re-install nouveau.

I have read that NVidia doesn't as of yet support the new X11 (if this is the case it's not really an issue for me, Unity 2d works fine until they catch up).

I've also noticed that adding Terminal to the launcher adds it with no icon, though that is unrelated :P

Any ideas on the kernel?
What would you like me to post to walk through it? 

:popcorn:

---

### Post by vicshrike on 2011-11-07
Does 10.04 work on your machine? What kind of computer specs do you have?

---

### Post by Llwynn on 2011-11-07
All prior versions work fantastically.

Its a Dual Core Pentium 4, using the x86 version of Ubuntu.
RAM wise I used 1gb, thought that might be the issue, and added another for a total of 2gb RAM.

/pro/cpuinfo:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 2793.228
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5586.45
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 2793.228
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5586.00
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

lspci for graphics card, onboard graphics, and ethernet card.
I am not using the onboard, but instead the NVidia card:

```
00:02.0 Display controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
04:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```

---

### Post by Llwynn on 2011-11-07
Bump cause it's getting buried under people asking the same questions over and over again without searching.

Also, is it possible for this to effect the overall speed of the ethernet card? Were talking almost 40 minutes to download 7mb from Ubuntu Software Centre on a 20meg down line through a gigabit network, yet on the other pc's there is no such latency.

---

### Post by MAFoElffen on 2011-11-07
> **Llwynn said:**
> Bump cause it's getting buried under people asking the same questions over and over again without searching.

Also, is it possible for this to effect the overall speed of the ethernet card? Were talking almost 40 minutes to download 7mb from Ubuntu Software Centre on a 20meg down line through a gigabit network, yet on the other pc's there is no such latency.
I don't try to get into supporting network cards, so I'll leave that to someone else...

But I am very good at supporting kernels and graphics- especially NVidia.

First a side question you had. 
> I have read that NVidia doesn't as of yet support the new X11
As far as my experience, NVidia is trying their best to catch up with Ubuntu's changes.  Unity is an Ubuntu thing and it's supporting it.  Nvidia works with the new xorg Xserver v1.11.2, but in Ubuntu you had to add:
```

Option     "ignoreABI" " 'true"

```To the xorg.conf file.

Where is your box locking up? Describe your boot... what it gets past (such as the Grub Menu), what it does and doesn't... where it looks up and what the screen looks like...

---

### Post by Llwynn on 2011-11-07
Essentially, Grub loads, gives me a list of options, I select the new 3.x image, It leaves grub, the screen looks like its about to switch over to the Ubuntu loading splash screen, but instead reverts to my bios loading as though I had instead told it to reboot. Same should I try to use recovery console instead.

Sadly, I don't know if it gets far enough into the boot to produce a log, though I will begin scouring for that, or see if I can force it to log it's post-mortem steps.

In the mean time, I'll work on adding that to xorg.conf and see if that sorts out my graphics side.

:UPDATE:

Attempted to do the NVidia fix, it failed to complete installation of the drivers on all 4 types.
[version 173]
[post-release 173]
[version-current]
[post-release]

---

### Post by MAFoElffen on 2011-11-08
> **Llwynn said:**
> Essentially, Grub loads, gives me a list of options, I select the new 3.x image, It leaves grub, the screen looks like its about to switch over to the Ubuntu loading splash screen, but instead reverts to my bios loading as though I had instead told it to reboot. Same should I try to use recovery console instead.

Sadly, I don't know if it gets far enough into the boot to produce a log, though I will begin scouring for that, or see if I can force it to log it's post-mortem steps.

In the mean time, I'll work on adding that to xorg.conf and see if that sorts out my graphics side.

:UPDATE:

Attempted to do the NVidia fix, it failed to complete installation of the drivers on all 4 types.
[version 173]
[post-release 173]
[version-current]
[post-release]
Current xserver in main is 1.10. Everything is fine with that version. Your driver should be nvidia-current, but... we really need to confirm  something a little more basic first.

On boot, hold the shift key, Let the Grub menu come up... <you comfirmed that comes up>. Press "e" to get into an edit mode. Arrow down until you get to the line that starts with "linux".  Arrow right to the text "quiet splash vt.handoff=7" and replace with "--verbose single". Press <cntrl><x> to boot...

That should boot the kernel in a single user mode into a text console.  Watch the messages, they will be turn on as verbose. Look for errors. It should boot to a text login prompt. Login.  Tell me if it does...  If it does, it can boot the kernel.  

Netx would be to boot on a LiveCD in "Try" mode and in the upper right of the menu panel, you should see your install filesystem, go to /var/log/Xorg.0.log... Or rather, here how the numbering shema goes for that log: 0 is current, 5 is oldest (0-5).  We want to look at a log were you tried to load a 3.x kernel with X (graphics) and failed... Please post is here.  The boot in Single-mode text does not gen an xorg log.

---

### Post by Llwynn on 2011-11-08
Did a clean install just to confirm everything wasn't a simple installation issue, same results, but, this time around while trying to use the:

2.6.38 recovery option I saw it fly through the loading and stop at:


12.368098] [drm] nouveau 0000:04:00.0: Register 0x00004030 not found

there was more behind it but it did the usual reboot before I could grab it.

I will in the meantime have it noisy boot to get as much more info as I can.

---

### Post by MAFoElffen on 2011-11-08
> **Llwynn said:**
> Did a clean install just to confirm everything wasn't a simple installation issue, same results, but, this time around while trying to use the:

2.6.38 recovery option I saw it fly through the loading and stop at:


12.368098] [drm] nouveau 0000:04:00.0: Register 0x00004030 not found

there was more behind it but it did the usual reboot before I could grab it.

I will in the meantime have it noisy boot to get as much more info as I can.
Please use the directions from my previous post to confirm boot on 3.x kernel in a text mode.

Once you can do that, there's other things I can guide you thorough from there.  i also asked for your xorg log so we can see where the errors are. If not, this could be weeks instead of hours.  I'm patient, but it gets hard to follow progress when there isn't- or have an idea on the status of an evolving, changing and moving target.

Here's the downrange plan of attack: You say it is kernel related with 3.x, but you just said that 2.6.38 failed on you.  We need to confirm 3.x booting  to completion before it loads any graphics... A TTY Text console would confirm that.  

In my first post I asked you if you could boot and run the Live Image of the LiveCD. Your response was that the install went fine... That is not running the live image.  Boot and use the "Try without installing" menu option... That would tell us that the kernel and default modules work okay on your machine and that later installed pieces are causing a problem.  If you need to use any boot option to successfully run the Live Image... That would have impact of how to run your installed instance.

Next would be the xorg log. That will tell "me" what drivers are loading, what hardware it getting queried and the data it send back, hwat modules get loaded and in what order... Sometimes the order things load is important or they get conflicts... and what errors there are.

Next would be to install drivers... I have lots of workarounds for this based on what we find out above.

Can you see that there is a plan... a logical order to the madness... Because things do depend on each other in layers for them to work right. Are we on the same page now?

---

