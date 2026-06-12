---
title: "Lock-up problem when updating."
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Mikjoba on 2010-06-07
Lock-up problem when updating.
I recently installed the 64bit version of 10.04 on a new PC, A Packard Bell imedia A4240NC
Hardware as follows:
Processor: AMD Athlon II X2 240 dual core.
Graphics: ATI Radeon HD 4650 1024MB
HDD: 1TB (no dual boot Linux uses the whole disc).
Memory 4GB DDR2

After the initial install all worked well, more or less, the only slight problem was with the graphics, it was usable but gave "choppy edges" to windows when they were moved from side to side, I then went to Administration > Hardware drivers and found that ATI/AMD proprietary FGLRX graphics driver was shown as available but not activated, I therefore proceeded to activate this driver, it was downloaded and installed and after a restart it showed up as being active, the graphics were improved slightly after this activation, and it was possible to use 3D effects etc., although I was expecting more from a graphics card with 1024MB on-board, I should perhaps add that I am using a Fujitsu Siemens D22W-1 monitor, resolution (native) 1680 x 1050.
Now we come to the actual problem, Update manager presented itself and stated that updates were available,(kernel header) I then proceeded with the update and chose to view more details so that I could see what was going on, the update ran its course but the PC locked-up completely with a message showing the following:
Run-parts: executing/etc/kernel/postinst.D/Nvidia-common 2.6.32-22-generic/boot/vmlinuz-2.6.32-22-generic
There was no visible disk activity and the PC was left running for about 90 minutes, just in case it would unfreeze itself, which was not the case so I had to hit the on/off switch, after a reboot I tried to go into Synaptic Package manager but got the following message:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to
> correct the problem.
> E: _cache->open() failed, please report.
I followed this advice and dpkg then continued (probably from the point it had stopped) and all seemed well apart from the choppy graphics again so I decided to try to uninstall and reinstall the FGLRX drivers which got me back to the same position as prior to the lock-up.
After this I decided to download and install two programs from the Ubuntu Software Center, Gramps Genealogy System and Hardinfo, both installed without any problems, but when I went to the Update Manager a day or so later it stated that there were new updates available, so I allowed it to install updates and exactly the same thing happened again! it stopped at exactly the same point:
Run-parts: executing/etc/kernel/postinst.D/Nvidia-common 2.6.32-22-generic/boot/vmlinuz-2.6.32-22-generic
Now for the strange part after the Synaptic message was followed:
manually run 'dpkg --configure -a'
I had a working PC again but I did not need to reinstall the proprietary ATI/AMD FGLRX graphics driver because now the graphics were perfect no choppiness at all, better than before, and what was even stranger is that it was no longer active! ("No proprietary drivers in use on this system").
It would appear from what I have been able to read on this forum that this behaviour from the ATI graphics it not that unusual, although I still don't understand why, but what is still a problem is the updating lock-up which happened yet again today, unfortunately I had forgot to click on more details so I do not know at which point it froze (probably the same) also this time instead of going to synaptic after a reboot I went to Update manager which stated that a partial update had taken place which should be continued (and which was), A lot of information, but I thought it best to mention the the graphics problem when I saw that it was locking up at: Run-parts: executing/etc/kernel/postinst.D/Nvidia-common 2.6.32-22-generic/boot/vmlinuz-2.6.32-22-generic, perhaps there is no connection but if not I am at a loss to know what is causing this, until I get some kind of feedback I will have to refrain from updating, not good for this computer having to turn it off at the switch!
Thanks in advance

Mike

---

### Post by drs305 on 2010-06-07
It appears to be hanging on an nvidia-common script. You mention ATI. Are you using any nvidia drivers? If not, perhaps you could try to uninstall nvidia-common via synaptic. 

If that doesn't work (or via the command line where you could see error messages), you could probably clear the error by renaming /etc/kernel/postinst.D/Nvidia-common to /etc/kernel/postinst.D/Nvidia-common.bad and then trying the updates. That wouldn't fix what is wrong, but it would bypass the nvidia-common script and thus avoid generating the error.

NOTE: I have used the capitalization in your post, but linux should be using lower case and that is what you should be using in terminal commands unless yours are different. *postinst.D/Nvidia-common* is not equal to *postinst.d/nvidia-common*

---

### Post by Mikjoba on 2010-06-07
Firstly postinst.D/Nvidia-common was a typo from my side, I obviously couldn't screen dump when this happened so this was written down by hand thus the mistake, but you did give me a clue drs305, this PC is so new (for me) that I hadn't noticed that not only is there a dedicated graphics card it also has an integrated card as well! this would appear to be a Nvidia GForce 8200, it was hidden behind a black cover that I thought was only for blanking, but there was a VGA connector behind it, if I go to the BIOS (Phoenix) on this machine I cannot actually disable it, my choice is Primary Display (PCIEx) which it is set to, or integrated.
Unfortunately my Nvidia problems do not end there, it would appear that when I check out resources with the help of HardInfo I have a lot of Nvidia associated resources see below:
<tt>0170-0177 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>  0170-0177 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>01f0-01f7 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>  01f0-01f7 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>0295-0314 </tt>		: pnp 00:02
<tt>0376-0376 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>  0376-0376 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>03c0-03df </tt>		: vga+
<tt>03f6-03f6 </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>  03f6-03f6 </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>04d0-04d1 </tt>		: pnp 00:02
<tt>0800-0805 </tt>		: pnp 00:01
<tt>0970-0977 </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
<tt>  0970-0977 </tt>		: AHCI SATA low-level driver
<tt>09f0-09f7 </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
<tt>  09f0-09f7 </tt>		: AHCI SATA low-level driver
<tt>0b70-0b73 </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
<tt>  0b70-0b73 </tt>		: AHCI SATA low-level driver
<tt>0bf0-0bf3 </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
................................................................
<tt>1c00-1c3f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
<tt>  1c00-1c3f </tt>		: nForce2_smbus
<tt>1c40-1c7f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
<tt>  1c40-1c7f </tt>		: nForce2_smbus
<tt>1d00-1dff </tt>		: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
<tt>9000-9fff </tt>		: PCI Bus 0000:04
<tt>  9c00-9cff </tt>		: VIA Technologies, Inc. Device 3403 (prog-if 10)
<tt>a000-afff </tt>		: PCI Bus 0000:03
<tt>b000-bfff </tt>		: PCI Bus 0000:02
<tt>  bc00-bcff </tt>		: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
<tt>c000-cfff </tt>		: PCI Bus 0000:01
<tt>d800-d807 </tt>		: nVidia Corporation MCP77 Ethernet (rev a2)
<tt>  d800-d807 </tt>		: Reverse Engineered nForce ethernet driver
<tt>dc00-dc0f </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
<tt>  dc00-dc0f </tt>		: AHCI SATA low-level driver
<tt>f000-f00f </tt>		: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
<tt>  f000-f00f </tt>		: low-level driver for AMD and Nvidia PATA IDE
<tt>fc00-fc3f </tt>		: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
....................................................................
 nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
<tt>  fe020000-fe023fff </tt>		: ICH HD audio
<tt>fe026000-fe027fff </tt>		: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2) (prog-if 01)
<tt>  fe026000-fe027fff </tt>		: AHCI SATA low-level driver
<tt>fe029000-fe02900f </tt>		: nVidia Corporation MCP77 Ethernet (rev a2)
<tt>  fe029000-fe02900f </tt>		: Reverse Engineered nForce ethernet driver
<tt>fe02a000-fe02a0ff </tt>		: nVidia Corporation MCP77 Ethernet (rev a2)
<tt>  fe02a000-fe02a0ff </tt>		: Reverse Engineered nForce ethernet driver
<tt>fe02b000-fe02bfff </tt>		: nVidia Corporation MCP77 Ethernet (rev a2)
<tt>  fe02b000-fe02bfff </tt>		: Reverse Engineered nForce ethernet driver
<tt>fe02c000-fe02c0ff </tt>		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
<tt>  fe02c000-fe02c0ff </tt>		: ehci_hcd
<tt>fe02d000-fe02dfff </tt>		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
<tt>  fe02d000-fe02dfff </tt>		: ohci_hcd
<tt>fe02e000-fe02e0ff </tt>		: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
<tt>  fe02e000-fe02e0ff </tt>		: ehci_hcd
<tt>fe02f000-fe02ffff </tt>		: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
<tt>  fe02f000-fe02ffff </tt>		: ohci_hcd

So it would appear that Nvidia is involved in audio and NIC amongst other things, the removal of the Nvidia common script would surely effect these parts of the system as well?
The strange thing is of course that updates seem to continue where they stopped after a restart, and the PC is rock steady apart from this problem, is there no log file that would tell me exactly which particular part of the Nvidia common script is the culprit?

---

### Post by drs305 on 2010-06-07
You could just try running the script in a terminal and see what output you get:
```
sudo /etc/kernel/postinst.d/nvidia-common
```

As far as removing the script - since you have nvidia components *and* your downloads continue after you reboot then it isn't as imperative to try this. 

If you were never able to get the updates, disabling the script might have allowed the updates to complete; since the script is generating an error and not completing as is, disabling it temporarily would most likely not effect the system negatively and would allow the other updates.

---

### Post by Mikjoba on 2010-06-08
Not at my PC at present, but I will try your solution this evening, running the script from a terminal to see what happens, if this does not give me any useful information I will temporarily disable as you mentioned next time there is an update and see if it helps.
Thanks
Mike

---

### Post by Mikjoba on 2010-06-08
sudo /etc/kernel/postinst.d/nvidia-common from the terminal reported nothing at all, I have noticed after more research that there are several bug reports in and around this problem, for the moment I decided to uninstall and reinstall from Synaptic which gave no problems at all, this method was one of the solutions given but there did not seem to be a clear consensus about if this bug has been resolved or not, I am not going to force this, I will wait until the next kernel update and see what happens, if it locks up again I will try your suggestion about disabling it temporarily.
Thanks for interest shown.

Mike

---

