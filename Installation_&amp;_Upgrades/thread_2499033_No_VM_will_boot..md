---
title: "No VM will boot."
date: 2024-07-08
forum: Installation &amp; Upgrades
---

### Post by towf on 2024-07-08
[COLOR=#333333][FONT=&amp]Hi. I'm running Kubuntu 24.04 LTS. I tried to start a VM of Windows 10 Home 22H2 on it and it returned this error.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]"Kernel driver not installed (rc=-1908)[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]'modprobe vboxdrv'[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]as root.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. "[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Anybody know how to fix this? Thank you.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]-TOWF[/FONT][/COLOR]

---

### Post by yancek on 2024-07-08
What happened when you followed the instruction suggested in your error output?

```
 [COLOR=#333333][FONT=&amp]modprobe vboxdrv[/FONT][/COLOR]
```

Do you have Secure Boot enabled in the BIOS?  Did you try turning it off to test?  When you boot the computer and access the BIOS, did you check to see if virtualization is enabled?  Exactly how to do this varies with manufacturer.  On my HP it is under the Configuration tab but that varies by manufactuer so you will just have to take a look around your BIOS options.

---

### Post by currentshaft on 2024-07-08
Why are you even using VirtualBox?

[https://virt-manager.org/](https://virt-manager.org/)

---

### Post by towf on 2024-07-13
"[COLOR=#000000]Why are you even using VirtualBox?[/COLOR]

[https://virt-manager.org/](https://virt-manager.org/)"

Idk, maybe it's because IT'S MY OWN PREFERENCE, and you should just STOP ADVERTISING THIS GARBAGE TO ME?

---

### Post by towf on 2024-07-13
"[COLOR=#000000]Do you have Secure Boot enabled in the BIOS? Did you try turning it off to test? When you boot the computer and access the BIOS, did you check to see if virtualization is enabled? Exactly how to do this varies with manufacturer. On my HP it is under the Configuration tab but that varies by manufactuer so you will just have to take a look around your BIOS options."

I do have secure boot enabled, and I do have virtualization on. Also executing "modprobe vboxdrv" comes up with this message.
```
modprobe: FATAL: Module vboxdrv not found in directory /lib/modules/6.8.0-38-generic
```
[/COLOR]

---

### Post by ubfan1 on 2024-07-13
Do you have the package virtualbox-dkms installed?  That package provides the source code for the virtualbox kernel module to be
 build with dkms. Kernel sources or headers are required to compile this  module. (i.e. build-essential, gcc, etc.).

---

### Post by currentshaft on 2024-07-13
> **towf said:**
> "[COLOR=#000000]Why are you even using VirtualBox?[/COLOR]

[https://virt-manager.org/](https://virt-manager.org/)"

Idk, maybe it's because IT'S MY OWN PREFERENCE, and you should just STOP ADVERTISING THIS GARBAGE TO ME?

Hilarious. Maybe you should learn to recognize what garbage software is before committing to an unhinged rant.

---

### Post by QIII on 2024-07-14
Perhaps, currentshaft, you should be more circumspect in your approach to providing advice.  Try a little less bile.  Also, it is not our place to make any judgement about a user's preference.  I don't use VirtualBox and have many reasons to recommend against it.  I am happy to suggest better alternatives, such as KVM -- because it is rolled into the Linux kernel natively -- but in the end it is up to the user.  VirtualBox is a useful, simple tool for those dipping their toes in VMs as they learn.  Make recommendations.  Don't be snide.

towf, virt-manager is hardly garbage, nor is currentshaft advertising it.  virt-manager is quite well respected and used often by those who use KVM and want a GUI for that purpose. It is not a commercial product, but a free and open-source tool.  You can download the code if you want.

Both of you, please take a breath.

---

### Post by towf on 2024-07-14
"[COLOR=#000000]Do you have the package virtualbox-dkms installed? That package provides the source code for the virtualbox kernel module to be[/COLOR]
[COLOR=#000000]build with dkms. Kernel sources or headers are required to compile this module. (i.e. build-essential, gcc, etc.)."

I tried running ```
sudo apt install virtualbox-dkms
``` ,  however, it came up with a bunch of errors such as
[/COLOR]```
[FONT=monospace][COLOR=#FF5454]**Job for virtualbox.service failed because the control process exited with error code.**[/COLOR]
[COLOR=#FF5454]**See "systemctl status virtualbox.service" and "journalctl -xeu virtualbox.service" for details.**[/COLOR]
[/FONT]
```[COLOR=#000000]
and
```
[/COLOR][COLOR=#FF5454][FONT=monospace]Failed to start virtualbox.service - LSB: VirtualBox Linux kernel module.[/FONT][/COLOR][COLOR=#000000]
```
[/COLOR]

---

### Post by ubfan1 on 2024-07-14
Hmmmm. I just did a clean install of virtualbox on a pretty fresh Ubuntu 24.04 Desktop without issue.  Lets look at Software&Updates/UbuntuSoftware -- I have main/universe,restricted, and muiltiverse  checked off. My gcc --version is 13.2, with the 6.8.0-38 kernel and headers.  Any more clues from the suggested systemctl and journalctl commands suggested by the error?  Ensure you have run sudo apt update and sudo apt upgrade before the install virtualbox.

---

### Post by towf on 2024-07-14
> **ubfan1 said:**
> Hmmmm. I just did a clean install of virtualbox on a pretty fresh Ubuntu 24.04 Desktop without issue.  Lets look at Software&Updates/UbuntuSoftware -- I have main/universe,restricted, and muiltiverse  checked off. My gcc --version is 13.2, with the 6.8.0-38 kernel and headers.  Any more clues from the suggested systemctl and journalctl commands suggested by the error?  Ensure you have run sudo apt update and sudo apt upgrade before the install virtualbox.

Hmm, all my packages are up to date, my gcc and kernel version are the same, and I can't find the Software & Updates/Ubuntu Software.

---

### Post by ubfan1 on 2024-07-14
From the launchpad icon (bottom right), there should be an icon for "Software & Updates".  Its first tab is "Ubuntu Software".

---

### Post by towf on 2024-07-15
> **ubfan1 said:**
> From the launchpad icon (bottom right), there should be an icon for "Software & Updates".  Its first tab is "Ubuntu Software".

I'm on KDE so I don't have that option.

---

### Post by QIII on 2024-07-15
I think Kubuntu still comes with Muon.  I don't remember if Discover is included.  I don't use either, even though I use Kubuntu.

I always install *synaptic* because it is a much better GUI if I want to use a graphical software package manager front end.

Try clicking the Application Launcher and type "software", which should get your options.

---

### Post by ajgreeny on 2024-07-15
Just like QIII, I also always installed synaptic in those days when I used Kubuntu simply because it has a more intuitive GUI than muon which I could not get to grips with.
I probably should have tried harder but why bother when synaptic worked without a need for me to learn  something new. 

It is something that I always install immediately after any new Linux OS installation if it isn't already a default application.

Highly recommended if you need a GUI application!

---

### Post by towf on 2024-07-16
Yes, I have tried synaptic. Still didn't work.

---

### Post by deadflowr on 2024-07-16
is this still a thing: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1587184](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1587184)
I guess you'll probably need to follow something like this [https://askubuntu.com/a/1456158](https://askubuntu.com/a/1456158)

Feels like this is an issue that should have been solved or fixed years ago.
If it hasn't actually already been fixed.

---

### Post by towf on 2024-07-17
> **deadflowr said:**
> is this still a thing: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1587184](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1587184)
I guess you'll probably need to follow something like this [https://askubuntu.com/a/1456158](https://askubuntu.com/a/1456158)

Feels like this is an issue that should have been solved or fixed years ago.
If it hasn't actually already been fixed.

First link is useless, second link, well, it might be useful, I just don't know how to work with MOKs.

---

### Post by towf on 2024-09-01
OK, I switched to regular GNOME Ubuntu and that seemed to have worked.

---

### Post by vs111 on 2024-09-05
Hi.
I am running Ubuntu 22.04 LTS currently with kernel 6.8.0-40-generic.
I have a Window XP VM running on VirtualBox and I get the same message as towf.
I don't know Linux, but I hope it might be helpful to tell you that if I am rebooting with 5.15.0-119-generic kernel everything works.
So I don't know what exactly the issue with the drivers might be, but maybe someone knowledgeable can figure it out.

---

### Post by aquacobalt on 2024-09-13
currentshaft you're not slick. If you're gonna comment on a help forum actually post something helpful instead of advertising another random VM [COLOR=#BFBFBF][FONT=&quot]&#128128;[/FONT][/COLOR]

---

