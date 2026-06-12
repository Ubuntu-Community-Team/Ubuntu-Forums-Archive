---
title: "Error in upgrading grub-pc"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by Ansowi on 2012-07-30
Hi guys.

I just installed a copy of Xubuntu 12.04 on my 40GB HDD. It installed fine, and now when I started it up I used apt to update the packages.

They all installed fine, however I seem to be having a problem updating the package grub-pc, as seen below:

```

bui@bluefly:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  hplip hplip-data libhpmud0 libsane-hpaio linux-generic linux-headers-generic linux-image-generic printer-driver-hpcups printer-driver-hpijs
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up grub-pc (1.99-21ubuntu3.1) ...
cp: reading `/usr/share/grub/unicode.pf2': Input/output error
cp: failed to extend `/boot/grub/unicode.pf2': Input/output error
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
bui@bluefly:~$ 

```

I'm not completely sure what the issue is here, but now I'm concerned that the ugprade failure may have messed up my GRUB, making me unable to boot on my next restart.

Here is a result log from the boot info script, so someone can check and see if my GRUB is corrupt, and see if there's anything I should do to upgrade it correctly.

[http://dpaste.org/hsssE/](http://dpaste.org/hsssE/)

I already tried running apt-get clean and installing again, however it keeps failing.

Thanks a lot.

---

### Post by Ansowi on 2012-07-30
Update: I went ahead and restarted my machine (without properly updating GRUB) however now I get this instantly when booting from hard drive:

```
error: ELF sectors outside core
grub rescue> 
```

Any suggestions on this? I can't seem to find a solution.

---

### Post by westie457 on 2012-07-30
Hi best suggestion from me is go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and follow this part - 2nd option : install Boot-Repair in Ubuntu

---

### Post by Ansowi on 2012-07-30
> **westie457 said:**
> Hi best suggestion from me is go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and follow this part - 2nd option : install Boot-Repair in Ubuntu

Just ran that, seems to have failed, still giving me the same GRUB error. Here's the log it gave me:

[http://paste.ubuntu.com/1119223/](http://paste.ubuntu.com/1119223/)

---

### Post by oldfred on 2012-07-30
I think Boot-Repair has a grub purge/reinstall repair in advanced options, grub options.

You may be able to manually boot from chroot:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)


IF that does not work you may need to chroot and run the total grub2 uninstall/reinstall.

HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by suvindu on 2012-07-30
Using another PC, Download "Boot-Repair-Disk" (Search Google) It should be an ISO file, Burn it into a CD and Boot from it. It'll give you an option to Repair GRUB.

---

### Post by Ansowi on 2012-07-30
> **oldfred said:**
> I think Boot-Repair has a grub purge/reinstall repair in advanced options, grub options.

You may be able to manually boot from chroot:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)


IF that does not work you may need to chroot and run the total grub2 uninstall/reinstall.

HOWTO: Purge and Reinstall Grub 2 from the Live CD
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Alright. I attempted to use the chroot method in the second thread you linked.

It seemed to install GRUB successfully, so I went ahead and rebooted.

The screen turned black for about half a minute after booting from hard disk, before an error appeared:

```

error: couldn't read file

Press any key to continue...

```

So I pressed a key, and it resulted in a kernel panic. Here's the error it displayed:

```

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
Pid: 1, comm= swapper/0 Not tainted 3.2.0-32-generic #36-Ubuntu

```

I rebooted, and ran Boot Repair again. It didn't return an error, so I rebooted again. The GRUB menu showed, and I select the first (Xubuntu) option. The same thing happened as before.

Here's the log: [http://paste.ubuntu.com/1119705/](http://paste.ubuntu.com/1119705/)

Any idea on what I should do now? Thanks!

---

### Post by Ansowi on 2012-07-30
> **suvindu said:**
> Using another PC, Download "Boot-Repair-Disk" (Search Google) It should be an ISO file, Burn it into a CD and Boot from it. It'll give you an option to Repair GRUB.

I'm running Boot Repair from a Xubuntu 12.04 Live USB, I'm not completely sure booting from a CD will make much of a difference.

---

### Post by oldfred on 2012-07-30
It looks like grub2's boot loader is installed correctly. If you hold shift key from BIOS until menu appears do you get a grub menu?

Some video cards/chips required boot parameters and some older systems (and very new) need other boot parameters. Did liveCD work without using f6 and adding boot parameters?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
Some parameters often used:
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by Ansowi on 2012-07-30
> **oldfred said:**
> It looks like grub2's boot loader is installed correctly. If you hold shift key from BIOS until menu appears do you get a grub menu?

Some video cards/chips required boot parameters and some older systems (and very new) need other boot parameters. Did liveCD work without using f6 and adding boot parameters?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
Some parameters often used:
noapic nolapic noapci noirqpoll nosmp irqpoll

I fortunately managed to solve the issue myself before your post. I noticed that when I was installing the GRUB packages some Linux kernel packages were kept pack. I upgraded them with dist-upgrade, re-installed GRUB, and it works perfectly now.

Thanks for your help! :D

---

