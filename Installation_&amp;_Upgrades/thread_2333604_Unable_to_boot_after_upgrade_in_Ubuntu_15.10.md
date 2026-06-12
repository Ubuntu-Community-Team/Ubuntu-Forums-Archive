---
title: "Unable to boot after upgrade in Ubuntu 15.10"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by germinalzh on 2016-08-11
Hi :-)

I upgraded my Ubuntu OS yesterday - I did not pay attention to it as it was a small upgrade (about 70 MB), so I don't know what has been upgraded. I'm very sorry about that.
After having installed the required modules, the system asked me to restart my computer. The result is a black screen with the message: "operating system not found"

I've found several answers to similar problems and tried to fix the problem with boot-repair. Unfortunately, it didn't work - here the report: [http://paste.ubuntu.com/23018910/](http://paste.ubuntu.com/23018910/)
I access my laptop via bootable USB.

My computer is a Lenovo X121e with Ubuntu 15.10 (only Linux).

I would be very happy if someone could help me. I'm pretty sad as I love this small laptop and scared about the unreliability of Ubuntu. I can't believe that I am the only one having this problem.

Thank you in advance! :-)

Bruno

---

### Post by howefield on 2016-08-11
The log files in 

```
/var/log/apt/history.log
```
and
```
/var/log/apt/term.log
```

should give you an idea of what was upgraded and perhaps point the finger at whatever package.

PS. 15.10 is at End of Life and the repositories are not updated any longer and also will be moved at some point. If that bothers you give some thought as to how you get to the next release which is 16.04.1 and supported till 2021.

---

### Post by grahammechanical on 2016-08-11
I ran Ubuntu 15.10 every day during is 26 week development period. I updated every day and I never had this problem. I also ran Ubuntu 16.04 every day of its development period and updated it every day and never had this problem.

You have a hard drive with GPT partitioning and Ubuntu installed in EFI mode. That means that the Ubuntu boot files are put in a special efi_boot partition (sda1). All this is fine except that boot repair is saying that Grub is installed in the Master Boot Record (MBR) of sda. And that should not happen. In your case Boot Repair should be saying that Grub is not installed in the MBR of sda. How Grub got installed into the MBR, I have no idea.

You accepted the offer of Boot Repair to re-install the Ubuntu boot loader (Grub). Do you now get a Grub boot menu? Or are you still seeing the message: "operating system not found?"

You may wish to enter the UEFI boot system settings utility and make sure that the motherboard is not trying to load Microsoft Windows. The efi_boot partition also has Microsoft efi boot files. I assume that this machine once had Windows installed on it. So, I am assuming that the UEFI boot system is trying to load Windows and not finding an OS to load. And that is why you are seeing that message.

You should also confirm that the motherboard is set to EFI mode and not BIOS/Legacy/CSM mode.

Regards

---

### Post by germinalzh on 2016-08-11
Hey. Thank you for your answer! :-)

Today I found out that Ubuntu 15.10 is no longer supported. I will upgrade to 16.04 as soon as I have fixed the boot problem (when I manage to do it). 

You're right indeed. I can see in term.log several lines with GRUB, efi and Boot. 

Is there a standard procedure to deal with this problem?

I am helpless.

Here the history.log:

Start-Date: 2016-08-11  00:31:53
Commandline: aptdaemon role='role-commit-packages' sender=':1.107'
Install: linux-image-extra-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic), linux-image-4.2.0-42-generic:amd64  (4.2.0-42.49, automatic), mokutil:amd64 (0.3.0-0ubuntu3~15.10.1,  automatic), linux-headers-4.2.0-42:amd64 (4.2.0-42.49, automatic),  linux-headers-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic), linux-signed-image-4.2.0-42-generic:amd64 (4.2.0-42.49, automatic)
Upgrade:  shim-signed:amd64 (1.11+0.8-0ubuntu2, 1.18~15.10.1+0.8-0ubuntu2),  linux-headers-generic:amd64 (4.2.0.41.44, 4.2.0.42.45),  libarchive13:amd64 (3.1.2-11ubuntu0.15.10.1, 3.1.2-11ubuntu0.15.10.2),  dh-python:amd64 (2.20150826ubuntu1, 2.20150826ubuntu1.1),  flashplugin-installer:amd64 (11.2.202.626ubuntu0.15.10.1,  11.2.202.632ubuntu0.15.10.1), thermald:amd64 (1.4.3-5ubuntu2,  1.4.3-5ubuntu3), libpurple0:amd64 (2.10.11-0ubuntu4.1,  2.10.11-0ubuntu4.2), linux-signed-generic:amd64 (4.2.0.41.44,  4.2.0.42.45), libpurple-bin:amd64 (2.10.11-0ubuntu4.1,  2.10.11-0ubuntu4.2), linux-signed-image-generic:amd64 (4.2.0.41.44,  4.2.0.42.45), linux-libc-dev:amd64 (4.2.0-41.48, 4.2.0-42.49),  linux-image-generic:amd64 (4.2.0.41.44, 4.2.0.42.45),  linux-generic:amd64 (4.2.0.41.44, 4.2.0.42.45)
End-Date: 2016-08-11  00:35:35

---

### Post by germinalzh on 2016-08-11
Hey Grahammechanical. Thank you for your answer :-)

When I now start the laptop I get a Grub boot menu (Boot menu and Application menu). Before that I get a black screen with several errors concerning grub.

No idea how can I go on

---

### Post by germinalzh on 2016-08-11
Does make sense to fix this problem or would be better to install Ubuntu 16.04 directly? Will I have the same problem with 16.04?
Whats your opinion?
Cheers :-)

Bruno

---

### Post by mörgæs on 2016-08-12
You will be better off with a fresh install of 16.04.1. 
Troubleshooting abandoned software can be a pain.

---

### Post by germinalzh on 2016-08-13
I saved all the relevant data and installed Ubuntu 16.04. Everything works fine now. :)

Thank you for your advice.

Cheers

Bruno

---

