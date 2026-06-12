---
title: "ubuntu stopped booting"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by chopra on 2015-02-15
Hi Guys,

I very recently installed Ubuntu along side windows 8.1, as detailed on the thread that I just marked as solved.
[http://ubuntuforums.org/showthread.php?t=2262097](http://ubuntuforums.org/showthread.php?t=2262097)

Everything was going fine, until I tried to look at the grub menu.  When the computer would start up, I got a series of options. The top was ubuntu, there was one for windows,
and then there were some others.  I can't go back and look at the grub menu now, but when I clicked on ubuntu advanced settings, it took me to another menu that had two
options, which looked like names to kernel files.

When I clicked on one of those, it took me to the regular unity login screen.  I went to restart, and ended up in the original grub menu again.

Okay, nothing bad happened yet, but then, in the grub menu, I went to "system settings".  This took me to a sub-menu of the original manufacturer's boot menu.
Before installing Ubuntu, pressing f12 at boot time gave me the boot menu, and one option was "enter system settings".  (system settings could be gotten to directly by
pressing f2 at boot time. Not sure why they set it up with that redundancy.)

Once I saw that I was on the system settings screen, I selected "exit without saving changes".  This then took me to windows.  The only problem is that now, the machine boots
directly to windows, I can't even get to the grub menu.  I've tried a hard reset (holding down the shift key and the power button until the machine shuts off), but this
does not help.

The good news is that the system I installed still appears to be intact.  I can boot from the live USB thumb drive that I originally installed ubuntu from, and I can see my
root directory mounted as a partition within the media directory.  All of the files are still there, except that they're owned by 1000 instead of my username (makes sense.
If the username isn't on the system, it'll just default to the UID.) 

I saw this thread, 

[http://ubuntuforums.org/showthread.php?t=2265397](http://ubuntuforums.org/showthread.php?t=2265397)

posted just four hours before mine, and I followed the initial advice that patrickbo did, and entered the following command into an administrator command prompt:

bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi

That did nothing.  So I'm at a loss for what's happened.

Thanks, Chopra

---

### Post by v3.xx on 2015-02-15
I do not run efi, but I ran across this.

[http://askubuntu.com/questions/348269/after-update-ubuntu-12-04-does-no-longer-boot-on-a-uefi-machine](http://askubuntu.com/questions/348269/after-update-ubuntu-12-04-does-no-longer-boot-on-a-uefi-machine)

Maybe someone using efi will come along :)

---

### Post by grahammechanical on 2015-02-15
> [COLOR=#000000]Everything was going fine, until I tried to look at the grub menu. When the computer would start up, I got a series of options. The top was ubuntu, there was one for windows,[/COLOR]
[COLOR=#000000]and then there were some others. I can't go back and look at the grub menu now, but when I clicked on ubuntu advanced settings, it took me to another menu that had two[/COLOR]
[COLOR=#000000]options, which looked like names to kernel files.[/COLOR]

[COLOR=#000000]When I clicked on one of those, it took me to the regular unity login screen. I went to restart, and ended up in the original grub menu again.[/COLOR]

All that is normal. do you not agree? If we select Restart from the login screen the machine will restart and we will be back at the Grub boot menu. This bit is not normal

> [COLOR=#000000]Okay, nothing bad happened yet, but then, _in the grub menu, I went to "system settings"._ This took me to a sub-menu of the original manufacturer's boot menu.[/COLOR]
[COLOR=#000000]Before installing Ubuntu, pressing f12 at boot time gave me the boot menu, and one option was "enter system settings". (system settings could be gotten to directly by[/COLOR]
[COLOR=#000000]pressing f2 at boot time. Not sure why they set it up with that redundancy.)[/COLOR]

I have never seen an option in the Grub boot menu to enter the BIOS or UEFI settings utility. Certainly not on my BIOS machine. Maybe some others will correct me regarding the Grub boot menu on machine with a UEFI boot system.

I think that somehow you entered into the motherboard boot system (UEFI) settings utility.

Regards.

---

### Post by chopra on 2015-02-15
The instructions in the link provided by v3.xx did the trick.  Strange thing is, I had to install efibootmgr while I was "logged in" as "ubuntu" from the flash drive. Presumably, this means that it wouldn't have been installed when I created the operating system.

Now, it's on my machine. That's very puzzling.  Installing it while signed in via the flash drive shouldn't put int permanently in the system if I've already installed the system...right?

Chopra

---

### Post by chopra on 2015-02-15
Just an update:  I found that the solution I used may not have been entirely necesarry.  What I should have done was simply change the boot order first, because ubuntu was already a boot option, it just wasn't first.

sudo efibootmgr -o 7,5,3,.......(not sure if specifying the partition is necesarry, I didn't need to.)

Also, I found that simply going to the BIOS menu in the first place resets the boot order, regardless of how I exit (discard changes or save changes).  This, I am guessing, is a problem with Toshiba's firmware, although I'll have to look further into it.  So if you're considering a new laptop, and Toshiba Sattelite (or any Toshiba) appeals to you, be forewarned.

Chopra

---

