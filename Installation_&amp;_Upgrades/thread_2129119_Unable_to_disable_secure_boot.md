---
title: "Unable to disable secure boot"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Countach on 2013-03-25
Using an ASUS x501a

Hello. I've been using Ubuntu for about 3 years, and I rather like it. I recently bought a computer that came infested with Windows 8, and immediately set to installing Ubuntu on it.

----

Hence, I discovered that secure boot needs to be disabled in UEFI, so I read how to do it and went in and...what...it's greyed out...I can't disable it.
Indeed, it says "secure boot control (disabled)", and I cannot enable it.

I tried setting up a password to access UEFI, as I've heard that will unlock all options, but it didn't.

So how do I disable it? I don't much fancy the idea of being forced to use 8 and only 8.

Thanks

---

### Post by dino99 on 2013-03-25
i've read somewhere on ubuntuforums that windows7/8 was required to disabling that secure boot in UEFI

---

### Post by oldfred on 2013-03-25
Microsoft requires Vendors to allow a user to turn secure boot off. So there is a way. But it varies by Vendor and some make it more difficult than others.
Some have a UEFI on setting that really turns secure boot off. Some have a BIOS/CSM mode (which you really do not want) that may change UEFI settings.
And you may have the password. Or settings on another screen.

Other Asus, someone may have posted details. UEFI should be similar, but details may vary some by model.
 Asus N56VJ-SH71-CD Shows default Windows partitons Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by mail.mail on 2013-10-29
One of my friend bought an Packard Bell EasyNote TE11BZ with windows 8 an got the same problem.   No way to disable the secure UEFI neither from the UEFI menu nor from the windows 8 UEFI settings menu.  > **oldfred said:**
> Microsoft requires Vendors to allow a user to turn secure boot off.   I'have that at contrary Microsoft only allow vendor to disable secure UEFI on x86 architectures but that's not mandatory. One ARM architecture secure UEFI with disabling feature unactiveted is required. Do you have any source for what you said?

---

### Post by oldfred on 2013-10-29
All Windows RT systems are totally locked down.
But all Windows 8 systems AMD or Intel have secure boot you can turn off.

 Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)
Windows RT - Locked UEFI
ARM run Windows RT which is not the Full Windows in Pro with x86
Windows RT has this new touch user interface called 'metro' that only runs apps you buy online from the microsoft app store. It doesn't run anything else. Its a lot like how an ipad works with itunes.
Windows 8 has everything Windows RT has, but it also has an extra tile called "Desktop Mode" where you can run software designed for desktop mode. It will also run software from previous versions of windows in "desktop mode".
More Details
[http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/](http://www.wired.com/gadgetlab/2012/10/windows8-windows-rt-explainer/)
[http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

---

### Post by mail.mail on 2013-10-29
Thank you for the fast answer.

But I need to precise that I tried to  way to disable the secure boot:
[LIST=1]
[*]From Windows 8 UEFI setting panel
There was no options to disable the secure boot
[*]Acces to the secure boot in UEFI menu
The option secure boot is present but not modifiable
[*]Find some documentation on the constructor site to see how to disable secure boot :
Nothing
[*]Check all constructor softwares installed in windows to see if there is any uefi manager:
Nothing
[/LIST]
So what did I forget?

what did I missed?

---

### Post by mail.mail on 2013-10-29
> **oldfred said:**
> All Windows RT systems are totally locked down.
But all Windows 8 systems ARM or Intel have secure boot you can turn off.


You said in your previous post that microsoft **requires** constructors to let an open door to disable secure boot in windows 8. And that for this fact that I ask some reference in hope that the protocol to disable it is given

I understood that Microsoft only **autorised** constructors to make computers where secure boot can be disabled but that this option is absolutely not mandatory.

---

### Post by oldfred on 2013-10-29
Some of the more inexpensive systems seem to have limited UEFI. So you just have UEFI secure boot and then a CSM/Legacy/BIOS setting? Some will boot from CSM in UEFI mode if boot files are in efi partition and if not then look in MBR to boot in BIOS mode.
Better systems have settings for secure boot on or off and CSM on or off. Some combination should give the three choices of UEFI with secure boot, UEFI without secure boot, or CSM/BIOS.

Is UEFI the most current version from vendor?

---

### Post by mail.mail on 2013-11-01
The computer is some inexpensive one so you're right, I only have UEFI with secure mode or legacy bios.  The UEFI is the last version.  Today I finally succed in installing ubuntu on it but without removing the recover partition of windows and without removing the secure boot.  So thank you four your advices.

---

### Post by grahammechanical on 2013-11-01
> [COLOR=#000000] without removing the secure boot[/COLOR]

Can we make clear something that has been overlooked in this discussion? Since Ubuntu 12.10 Ubuntu can install without needing to disable secure boot. That is not to say that with Windows 8 present it will be an easy task.

---

### Post by markir on 2014-01-25
I have just run into this with 2 Asus motherboards: P8H77M and H87M-PRO. In both of these cases the secure boot enable/disable tab is greyed out and no amount of fiddling lets you just change the state. I have a lengthy (and useless) email thread from Asus support where they essentially have no idea how to disable secure boot (and try to suggest that it can not be). 

After doing some reading it seemed likely that deleting the secure boot keys would force the BIOS into some sort of setup mode that would either automatically disable secure boot or else give me the option to. For the H87 board it just sliently disabled secure boot - so it is showing as 'disabled' after a reboot. Might pay to save the keys first... I will see how the procedure works with the other board (It is more vigorous in its demands for UEFI only bootable media)

---

