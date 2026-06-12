---
title: "&quot;Install third-party software for graphics...&quot; option failed; why?"
date: 2019-09-10
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2019-09-10
I tried to install Ubunutu 18.04 last night. I've installed 16.04 many times, but this is only the second time with 18.04.

I selected the "Install third-party software for graphics..." option, partly because I'd otherwise have to install a graphics driver immediately after, but mainly because I'd never tried that option before and I wanted to see how it worked. Here's what happened:

Installation appeared normal. When it was done I rebooted. Ubuntu came up to the point where it displayed the "Ubuntu" logo and a row of blinking dots. Then the screen started flashing on and off in an irregular pattern at approximately 1 Hz. It continued flashing and displaying the same screen for so long that I had to leave it and go to dinner. I wasn't sure whether it was behaving normally, so I left it running. I returned just before going to bed. The logo was still on the screen, but the flashing had stopped and the blinking dots were gone. Ubuntu didn't respond when I shook or clicked the mouse or pressed the space bar. I pressed Ctrl+Alt+Del, and it rebooted. I was out of time then, so I turned it off before it finished the POST.

Tonight I'll see if I can reboot it, and if not, I'll reinstall without the "install third-party..." option. Whether I can reboot or not, though, I'd like to understand what happened.

The motherboard is an ASRock Extreme3. The graphics card is an NVIDIA GeForce 8800 GTS.

---

### Post by ajgreeny on 2019-09-10
I have never had an Nvidia graphic card, but assuming your problem relates to an incorrect driver being installed, I am pretty certain you can remove that driver using the command line which you can get to with Ctrl+Alt+F2 and running command ```
sudo apt remove nvidia*
```
You can try that command with the -s option, ie ```
sudo apt remove -s nvidia*
``` to simulate what would happen first if you want some assurance that this is not doing anything disastrous.

---

### Post by TheFu on 2019-09-10
I don't think apt works with globbing like apt-get does. I've made the same mistake.

```
sudo apt-get remove nvidia*
```

I don't know if GeForce 8800 GTS is currently supported by nVidia drivers.  My 7600 GS lost support in 2017 and the F/LOSS drivers didn't support the correct native resolution of the main monitor.

---

### Post by CatKiller on 2019-09-10
> **TheFu said:**
> I don't know if GeForce 8800 GTS is currently supported by nVidia drivers.

340 branch: so, legacy, but not ever so far off. I *think* that one got a bit squirrelly with newer kernels, but I also seem to recall that they made some effort to fix that.

Doing the install with nouveau and then installing 340 manually is probably the best approach, for maximum feedback of the process. Progress bars are pretty and all, but not quite as useful as terminal output.

---

### Post by mastablasta on 2019-09-11
so basically after they drop support you can throw away a working GPU card if you want an up to date OS?

---

### Post by orthoducks on 2019-09-11
When I visited this topic earlier only ajgreeny had replied, so this  message responds only to that one. Thank you all for your comments,  though.

I tried removing nvidia* packages but did not find joy; apt claimed that *no *nvidia* packages were installed. That may be due to the problem TheFu mentioned.

Linux  apparently trashed the disk the first time I tried to boot. When I   tried to continue a normal boot after running apt in safe mode, it   displayed a list of disk errors which seemed, literally, endless. After   about an hour of waiting for it to finish I rebooted, reformatted the   partition, and reinstalled Ubuntu without "Install third-party   software". Then my time was up for the night.

Tomorrow I'll find  out if it will boot with the generic driver, and if  so, with a manually  installed NVIDIA driver. If it won't do both I'll  be seriously  concerned, since Ubunutu 16.04 runs just fine with both  drivers on the  same mobo and graphics card.

---

### Post by CatKiller on 2019-09-11
> **orthoducks said:**
> 
Linux  apparently trashed the disk the first time I tried to boot. When I   tried to continue a normal boot after running apt in safe mode, it   displayed a list of disk errors which seemed, literally, endless. 

It's much more likely that your prior boot problems were because of your hard drive errors, and nothing to do with the installation of the Nvidia drivers.

Linux doesn't "trash disks." I would check for hard drive failure.

---

### Post by orthoducks on 2019-09-11
I think it's extremely unlikely that I had actual disk errors. I scrubbed the drive shortly before using it, with no errors reported by Linux or START. Then I installed Windows 10, used it for a while, and installed Ubuntu twice, with no problems reported. It's possible that hundreds or thousands of disk errors occurred during the boot attempt between the first and second Ubuntu installs despite perfect performance before and after, but it's not plausible. Time will tell.

---

### Post by SeijiSensei on 2019-09-11
To install an NVIDIA driver, use the Device Manager in the system settings after you've installed the system.

---

### Post by TheFu on 2019-09-11
> **orthoducks said:**
> I think it's extremely unlikely that I had actual disk errors. I scrubbed the drive shortly before using it, with no errors reported by Linux or START. Then I installed Windows 10, used it for a while, and installed Ubuntu twice, with no problems reported. It's possible that hundreds or thousands of disk errors occurred during the boot attempt between the first and second Ubuntu installs despite perfect performance before and after, but it's not plausible. Time will tell.

Run a smartclt test. Then run a smartctl report.  That's the only way to see current SMART data.  Anything else is guessing which doesn't provide current facts.

How do you expect Linux to "report"  disk errors?  I only see the reports via email because I have send-only MTA setup on all my systems so smartctl can let me know.  I've never seen any popup error.  Basically, if you don't have an MTA setup, I don't know how you'd get any disk issue report except by running a smartctl test+report and looking at it.

---

### Post by pcfan1234 on 2019-09-12
> **mastablasta said:**
> so basically after they drop support you can throw away a working GPU card if you want an up to date OS?

You can use the default driver nouveau. It still supports older cards, see here: [https://nouveau.freedesktop.org/wiki/FeatureMatrix/](https://nouveau.freedesktop.org/wiki/FeatureMatrix/)
[https://nouveau.freedesktop.org/wiki/CodeNames/](https://nouveau.freedesktop.org/wiki/CodeNames/)

---

### Post by TheFu on 2019-09-12
nouveau doesn't support all the resolutions that the proprietary driver did, at least for my nvidia GPU that I ended up retiring.  It would only go to 1080 with nouveau when it did 1200p with the 14.04 proprietary nvidia driver.  When I moved to 16.04, nvidia dropped driver support for that GPU.  It was old and it was cheap 10 years earlier when purchased.

---

### Post by mastablasta on 2019-09-13
and let's not even mention that it doesn't offer the full hardware acceleration (for games etc...)

---

