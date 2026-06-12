---
title: "boot-repair unable to fix PC"
date: 2018-11-01
forum: Installation &amp; Upgrades
---

### Post by fensflyer on 2018-11-01
My Ubuntu PC performed an apt update which caused it to stop booting. Running boot-repair from a LiveUSB didn't fix the problem - it just shows a blank Ubuntu-purple screen instead of a boot menu. The following link was created from my last attempt - [http://paste.ubuntu.com/p/PFqGtvXsWf/](http://paste.ubuntu.com/p/PFqGtvXsWf/)

Can anyone suggest what looks wrong with my configuration - it looks like all of the drives are intact, it's only the boot information that's gone (I hope!).

Thanks in advance

---

### Post by fensflyer on 2018-11-05
I guess that since the main partitions seem to be intact, if there's no suggestions about how to repair the bootloader/grub section, is it possible to perform a "reinstallation" but get it to only touch the bootloader bits, leaving the main root partition intact?  I'd quite like to have the machine back up and running as-is, so a clean reinstallation isn't too appealing, although if that's the only option I'd better look into it...

---

### Post by oldfred on 2018-11-05
Boot-Repair is for Booting issues.

What happened on apt update, or what was being updated?
Can you mount system and check log files?

       Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[URL="https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621"]https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621
      [/URL]
 Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line) 
    [URL="https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621"]
[/URL]

---

### Post by fensflyer on 2018-11-05
Thanks for the reply - sorry, I wasn't as clear as I should have been.

I think that my PC performed some updates in the background - this has happened before - and then wanted to perform a reboot.  Before I allowed it to do that, further updates were performed.  The next time I came to reboot it couldn't (I forget now what error was displayed).  This has happened once or twice in the past, and boot-repair has been an instant-fix.  This time it failed with the linked error message.

I will attempt to recover the log files to see what updates caused the failure.

---

### Post by oldfred on 2018-11-05
Often new kernel or related drivers or grub updates are the only reason a re-boot would be required.

Is UEFI Secure Boot on?
There seems to be some changes to newer kernels & grub related.

Can you boot with older kernel in grub menu? Or recovery mode?
You may need to press escape key before boot starts but after UEFI screen to get menu.

---

### Post by fensflyer on 2018-11-05
UEFI Secure boot is currently not on.

I get no grub menu at all at the moment.  When the PC boots from hard disk, I'm just presented with a blank screen in Ubuntu purple/orange (what is that colour called?).  There doesn't seem to be any obvious activity or timeout at that point.  Is there a magic button to access a menu - or is that the escape key press you refer to?

---

### Post by oldfred on 2018-11-05
There are keys to get into UEFI or UEFI boot menu.
And then escape key (with UEFI installs) is the key to get grub menu. But it has to be pressed after UEFI and before booting starts. If fast boot is on in UEFI, you may have no time to press a key as UEFI immediately jumps to booting and then it may depend on timeout settings you have in grub. 

My UEFI allows me to set time, so I set 3 sec for UEFI boot and 3 sec (default is 10 sec) for grub menu. Increase boot time a lot with my SSD, but gives me a chance to press a key just in case.

---

### Post by fensflyer on 2018-11-06
Ah - so I hit the escape key at the critical moment, and instead of getting the blank "orange" screen I got a boot menu which listed *Ubuntu, Advanced options for Ubuntu, some EFI files and System setup.  I assume that the * means default, and sure enough the Ubuntu option leaves me with a blank screen.  If I select the Advanced option I get a list of kernels that I must have had through various updates.  Selecting the latest one leaves me with a blank screen (again) but selecting the next latest allows the system to boot correctly!  Hurrah!

I haven't had time to reboot and see if that's consistent.  I think the main thing from here is to find what went wrong and try to get the "default" boot option to work again.

---

### Post by oldfred on 2018-11-06
Also the recovery boot includes nomodeset. 
Is it recovery mode boot that works or just next last older kernel?

You can remove quiet splash from linux line and see boot process. Often error is a few lines before last line posted.

---

### Post by fensflyer on 2018-11-12
The next last older kernel works fine - no need to invoke recovery mode.

---

