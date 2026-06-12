---
title: "help. please - 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by timbuktoo on 2011-10-14
so I clicked on the update managers upgrade system and let that run overnight
this morning I agreed to a liscencing agreement for IDK what and ree booted.

after reebooting it said something about internet drivers but was just not doing anything for a half hour so I turned it off and on again.  when I pressed the power button and it looked like it ran a shut down protocal or something and it said when it turned on:


```
SmartLink modem driver not available for this Kernel. please read README.Debian
or try to install the package sl-modem-source. Exiting...
speech-dispatcher disabled; edit /etc/defaust/speech-dispatcher
*starting the winbid daemon winbind
*starting bluetooth
[COLOR=Orange]* [COLOR=Black]PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned[/COLOR][/COLOR]
[COLOR=Orange][COLOR=Black]rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S90binfmt-support start

Since the script you are attmpting to invoke has ben converted to an
Upstart job, you may also use the start(8) utility, e.g start S()binfmt-support
start: unknown job: S90binfmt-support
*checking battery state...
[/COLOR][/COLOR]
```and then it stops doing anything and has just a flashing cursor.  I can turn it off by pressing the power button and it runs a shut down and turns off. and I can turn it back on and consistently get that message.

If anyone can give me advice I would gladly take it
-timbuktoo

---

### Post by MAFoElffen on 2011-10-14
> **timbuktoo said:**
> so I clicked on the update managers upgrade system and let that run overnight
this morning I agreed to a liscencing agreement for IDK what and ree booted.

after reebooting it said something about internet drivers but was just not doing anything for a half hour so I turned it off and on again.  when I pressed the power button and it looked like it ran a shut down protocal or something and it said when it turned on:


```
SmartLink modem driver not available for this Kernel. please read README.Debian
or try to install the package sl-modem-source. Exiting...
speech-dispatcher disabled; edit /etc/defaust/speech-dispatcher
*starting the winbid daemon winbind
*starting bluetooth
[COLOR=Orange]* [COLOR=Black]PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned[/COLOR][/COLOR]
[COLOR=Orange][COLOR=Black]rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S90binfmt-support start

Since the script you are attmpting to invoke has ben converted to an
Upstart job, you may also use the start(8) utility, e.g start S()binfmt-support
start: unknown job: S90binfmt-support
[COLOR=Red]*checking battery state[/COLOR]...
[/COLOR][/COLOR]
```and then it stops doing anything and has just a flashing cursor.  I can turn it off by pressing the power button and it runs a shut down and turns off. and I can turn it back on and consistently get that message.

If anyone can give me advice I would gladly take it
-timbuktoo
Can you boot on a LiveCD?

Can you get to a Grub Menu?

Of the error messages you posted:
Of the smart-link modem driver- It was probably installed with a kernel version schema check that looks to see if the kernel is 2.6.x, where the kernel in 11.10 is 3.0.x.  The kernels are really the same series, but have a diffrent numbering schema--> The driver will work but doesn't know that.  It would have to be reinstalled to pick up the Linux patch/fix that is in 11.10 for it to relearn that.
> 
[COLOR=Orange][COLOR=Black]rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S90binfmt-support start[/COLOR][/COLOR]You have to look in dmsg or syslog to see what this is...

*** Even though it had those erros, they were not fatal nor where they enough to stop the boot process.  It still tried to continue, until it got passed the battery check message...

At that point in the boot sequence, that is where the process looks for and tries to load the xorg and graphics drivers. That is where it looks like it hits a fatal error and locks up.

What video card do you have?

If you got to a grub menu, selected rescue mode, then selected contue boot and hold the shift key down... That should end up at the commandline.  Login.  zPost the result of this:
```

lspci -vnn | grep VGA

```

---

### Post by kooldino on 2011-10-15
I have this issue too...

the lspci command spits out:

01:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 8400 GS] etc etc

---

### Post by kooldino on 2011-10-15
[http://ubuntuforums.org/showthread.php?t=1741512&page=2](http://ubuntuforums.org/showthread.php?t=1741512&page=2)

---

### Post by MAFoElffen on 2011-10-15
> **kooldino said:**
> [http://ubuntuforums.org/showthread.php?t=1741512&page=2](http://ubuntuforums.org/showthread.php?t=1741512&page=2)
Which, like I said previously... right after the status for battery check to the System 5 Compatibility Check is where it tries to start Xorg-xserver and access the Video Driver.

Since you have NVidia, if you:
1. At boot, hold down or press repeatedly the shift key. That should bring up the Grub Menu.
2. At Grub menu, Press "e".  That will put you into an edit mode.
3. Arrow down to the line starting with "linux". That is the kernel boot line.
4. Arrow right until after the boot options "quiet splash".
5. Insert the kernel boot option "nomodeset" before the option "vt.handoff=7"
6. Press <cntrl><x> to boot with that option.

Once it boots, go to System Settings > Additional Drivers...  Install your driver, which should be nvidia-current.

---

