---
title: "Installing 7.10 64-bit on HP 8510w"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by El Pirata on 2008-02-27
Not a new Linux user, but a new comer to the Ubuntu world...

I decided to take 7.10 for a spin, which for me usually means trying it from the live CD before it is installed on my laptop. I started with 7.10 32-bit and I was able to get it up an running. Feeling encouraged by this, I decided to try the 64-bit version, and that is where things got a bit weird.

If I have the laptop (HP 8510w) on my docking station, the systems comes up and becomes fully functional. If I try the same thing undocked, the system hangs during the boot up process.

I have already tried adding the following options to the boot parameters to no avail:

- noapic irqpoll noirqdebug
- VGA=796 noapic nolapic

Should I just do the install while docked and tweak the system afterwards for undocked operation? That option does not fill me with confidence... :-(

Any suggestions will be greatly appreciated.

EP

---

### Post by mrsteveman1 on 2008-02-27
Interesting problem. What devices are additional on the dock? Usually there are extra usb ports, sometimes an SPDIF header, and even an extra hard drive (in the HP base things). I would bet one of those devices are causing the problem, though i would think you would have problems WHILE its docked.....


At what point in the boot process does the system hang? Can you read the kernel messages?


For sure install the system any way it works and figure out the problem later on, at least you will have a base to start with and logs to read (assuming root has a chance to mount before the failures).

---

### Post by El Pirata on 2008-02-27
Thanks, Steve.

I get past the "loading kernel" message... after a minute or two of getting a blank screen I get the following message:

"Ubuntu is running in low-graphics mode"

with the options of "Configure", "Shut Down" or "Continue"

If I click "Configure" and select the nv graphics driver and leave the resolution at 800x600 the system tries to continue and does the following:

* Checking battery state...				     [OK]
* Running local boot scripts (/etc/rc.local)		[OK]

It then hangs there - there is no indication of disk activity) and nothing happens after that.

---

### Post by mrsteveman1 on 2008-02-27
/etc/rc.local is near the end of the boot process, so this sounds to me like the kernel is ok (at least during the boot you described, docked or not etc).

Try doing vga=normal in the boot line and see what happens, it sounds like xorg isn't starting for some reason.

Once the system does boot press ctrl-alt-f1 and see if you get a login prompt.

---

### Post by El Pirata on 2008-02-28
Interesting...

I added the "vga=normal" option to the boot options and it made no difference in the results, so I went back and tried it again, this time with no additional boot options and just selecting "Continue" when told Ubuntu was running on low res mode.

After I got to this point

* Checking battery state... [OK]
* Running local boot scripts (/etc/rc.local) [OK]

I used ctrl-alt-f1, as you suggested and did get a command prompt

ubuntu@ubuntu:~$

where I was able to use regular commands.

So it looks like the issue is indeed xorg related. Do you have any suggestions on how to fix or work around this? BTW, the laptop is an HP 8510w with nvidia Quadro graphics.

- EP

---

### Post by mrsteveman1 on 2008-02-28
Boot with "xforcevesa" as a kernel option and see what happens.

It's SUPPOSED to boot the failsafe mode when you do that. If it doesn't the failsafe mode can be started manually, though it should work that way.

---

### Post by El Pirata on 2008-02-28
Using the "xforcevesa" option did not improve things... :-( As expected, the boot process did not complain about Ubuntu running in low res mode, but once it got to the "Running local boot scripts..." part, nothing else happened.

I then did the ctrl-alt-f1 again and then entered "startx", just for kicks and was pleasantly surprise when the GUI came up (including sound)... I then went back an rebooted, this time w/o the "xforcevesa" option and once again, after a ctrl-alt-f1, startx started the GUI (sound and all)...

So, not really sure of what is happening here, but at least I can now get it up and running and take it for a spin before installing.

Thanks for your help, Steve!

-EP

---

### Post by brymchik on 2008-03-01
I can confirm this. I've tried all this on my 8510w and - no go.

I've also tried to disable/enable devices from BIOS, nothing changed? I can get to 

* Running local boot scripts (/etc/rc.local) [OK]

and the machine is alive (it can get to command promt and it can shutdown itself) but can't load.

---

