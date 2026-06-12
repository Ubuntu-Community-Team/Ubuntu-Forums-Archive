---
title: "Problem with Grub rescue and Boot repair"
date: 2016-10-09
forum: Installation &amp; Upgrades
---

### Post by jjjacob on 2016-10-09
Hello, I have managed to create a problem with my boot partition.

I am able to boot using this: [https://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition/495993#495993?newreg=0347346a14e3400ebd656b1c95165da8](https://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition/495993#495993?newreg=0347346a14e3400ebd656b1c95165da8)

So, when I run the commands, I get this:

grub rescue > set root=(hd0,gpt2)
grub rescue > set prefix=(hd0,gpt2)/boot/grub
grub rescue > insmod normal
grub rescue > normal
Where I'm booting to /dev/sda2. Ok so far. When I then run

update-grub # <-- this is fine

But, when I run the following, I get errors:

[COLOR=#212121][FONT=wf_segoe-ui_normal]user@system-243abf:~$ grub-install /dev/sda2[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]Installing for i386-pc platform.[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]grub-install: error: cannot delete `/boot/grub/i386-pc/sleep_test.mod': Permission denied.[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]user@system-243abf:~$ sudo grub-install /dev/sda2[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]Installing for i386-pc platform.[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]grub-install: error: failed to get canonical path of `aufs'.[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]user@system-243abf:~$ sudo grub-install /dev/gpt2[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]Installing for i386-pc platform.[/FONT][/COLOR]
[COLOR=#212121][FONT=wf_segoe-ui_normal]grub-install: error: failed to get canonical path of `aufs'.[/FONT][/COLOR]

I tried umount to unmount the volume, but of course it is busy.

So, I try Boot Repair and I get this:

"Please close all your package managers (software center, update manager, synaptic, ...) Then try again"

I don't have any of that open, and I've tried rebooting several times. So clearly I'm missing something.

I've pasted my boot info here [http://paste.ubuntu.com/23299723/](http://paste.ubuntu.com/23299723/)

Any help offered would be greatly appreciated.

Thanks in advance,

JJ

---

### Post by oldfred on 2016-10-09
You always install grub to a drive, not to a partition.

[COLOR=#212121][FONT=wf_segoe-ui_normal]grub-install /dev/sda2
should be, if booted into your install, if live installer, you must mount install partition first.
[/FONT][/COLOR]        sudo grub-install /dev/sda 
    
Or you can just run Boot-Repair's update.
If still issues, then run Boot-Repair's advanced mode to totally uninstall & reinstall all of grub2.

---

