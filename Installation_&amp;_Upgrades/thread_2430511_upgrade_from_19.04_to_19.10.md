---
title: "upgrade from 19.04 to 19.10"
date: 2019-11-03
forum: Installation &amp; Upgrades
---

### Post by icegood on 2019-11-03
Hi there. My system died while upgrading from 19.04 to 19.10 : it locks screen but cannot login back anymore. 
I switched to additional terminal via CTRL+ALT+F2
and continued upgrading via
```
dpkg-reconfigure -a
```
As far as i understand process is broken during upgrading of nvidia drivers since it was the first package to reconfigure from command above. After upgrade finished i restarted laptop and found no way to use desktop anymore:
mouse and keyboard are frezed, and on the left-top corner i see black cursor => desktop dies.

My questions are:
1) Could i upgrade system from given state or should i upgrade from scratch from e.g. USB stick?
2) How do i correctly describe this bug in ubuntu bug tracker?

---

### Post by Autodave on 2019-11-03
I would do a clean install.  Before you even do that, you could make your boot medium and boot and run from that to see if it runs OK.

I learned a long time ago NOT to do upgrades: they just create problems.  Stick with the LTS releases and when 2 or 4 years are up, I do a clean install of a new LTS release.  18.04 was the last LTS and 20.04 will be the next one.  20.04 = year 2020, month 04 (April).

---

### Post by Mark Phelps on 2019-11-03
I agree with @Autodave -- as I tried an Upgrade just to see what would happen, and while it APPEARED to work, when I rebooted the next day, I got serious errors that prevented booting.  I ended up doing a Clean-Install and now, all is working properly.

---

### Post by pablosquared on 2019-11-03
I experienced a similar problem when upgrading from 19.04 to 19.10. In my case, I'd recently upgraded the NVIDIA driver to version 440 before attempting the o/s upgrade. Uninstalling the NVIDIA driver and replacing it with the older 390 version fixed the problem and a subsequent 2nd go at the upgrade completed successfully. I was able to install the 440 driver afterwards.

---

### Post by NovHak on 2019-11-03
My upgrade experience is far from being top notch either, at first it seemed to be relatively okay, and the next day the whole thing freezed during boot, not even a tty login available, and the Grub menu had disappeared, so no way to even choose a recovery option.

Even worse, at first I booted the 19.04 live image to perform some diagnostics, but thought it would be better to boot a 19.10 image. The 19.10 live image turns out to have problems (most likely everyone is concerned) such as being unable to be loaded to ram since /var/log and /var/crash are still on the support, and even written to ! Seriously, considering the problems, they should better have released 19.10 in november or even later, or even not release anything before 20.04. Respecting delays is worth nothing with quality problems such as these.

Anyway, I finally managed to recover, though I'm not quite sure yet what the problem was (but it seems it's related to Optimus), in part by removing the nvidia drivers from the init ramdrive (which was put there because of the FRAMEBUFFER option being set by some package), and setting the GRUB timer type back to the default of "menu" in /etc/default/grub (since the "hidden" option was triggering some errors), and temporarily switching the nvidia prime profile from "intel" to "nvidia".

I don't know if everything was really useful to solve my problem, but clearly setting back the prime profile to "nvidia" enabled me to boot the system again. Now I can switch profiles again, but there are problems, such as :

[LIST]
[*]the Nvidia GPU not being detected in hardware if the systems boots with the "intel" profile activated (which in such a case requires to switch to nvidia and reboot to be able to use the dGPU)
[*]when switching back to intel, closing the graphical session isn't  enough, it's necessary to stop/start the gdm service to have the modules  unloaded
[/LIST]

---

### Post by rsteinmetz70112 on 2019-11-04
Just to add a little counter balance. I've upgraded many installations many times. I've never had one completely fail although there have been problems. I find a new install takes longer to get into use by the time I add an reconfigure all of the things I need. IF you have a plain desktop  install with few additional packages and little customization a clean install is easier. 

If you want to try to save your broken install two commands will go a long way to figuring out what is wrong:

```
sudo dpkg --reconfigure -a
sudo apt install -f
```

This commands can fix a partially broken upgrade and if not will give you a lot of information about how to get it to work.

---

### Post by NovHak on 2019-11-05
The upgrade process *per se* went well, so to speak, and indeed, a crash in the middle of the process would have been worse imho. I think one important rule is when one gets a warning about replacing a configuration file or keeping the customised one, it's far better to say "replace" and then possibly come back to it, rather than keeping the old one.

To whose that it may help, my upgrade problem was likely related to the Optimus Prime utilities being upgraded to manage the "on-demand" profile, while at the same time keeping an old Nvidia proprietary driver that's incompatible with it. Getting the latest driver version (as of now, nvidia-driver-435) helped me. Moreover, it brings us closer to how it works on Windows, with the ability to run all programs on the iGPU, except for a few, designated ones.

For me it's still problematic since it doesn't power off the dGPU when it isn't used, and it's not even possible as long as X is running in the on-demand config. Actually I think it's supposed to work with Turing-based GPUs and later, but mine is too old (GTX 880M). I tried force-powering it off anyway (when it's not used) with a direct ACPI call, and oops I shouldn't have done this, as a reward I got a "GPU has fallen off the bus" message and X froze completely. I couldn't have the keyboard input quit raw mode to be able to switch to another vt, since it's disabled by default on Ubuntu (I wonder why btw), so I had to "emergency reboot".

---

