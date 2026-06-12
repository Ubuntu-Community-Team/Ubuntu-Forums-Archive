---
title: "Fresh install will not boot with AMD GPU"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by NullCoding on 2014-01-12
I put together some parts I had lying around from a previous build (the case fans broke so I dismantled the unit and never got around to using the parts until now). It's a cool system and it POSTs totally fine. I put in a new HDD. It's pretty standard stuff for the most part. I put 64-bit 13,04 on a flash drive and booted to it, ran through the installer just fine, set up my account, and rebooted...except it won't load, well, anything.


[LIST]
[*]If I don't press anything and just let GRUB load normally, I get a blank purple screen. I've found plenty of information about WHY this happens, but all the steps to mitigate it assume I'm somehow able to access a terminal to edit configuration files, which I cannot!
[*]If I try to use keyboard shortcuts for anything, I get either a solid black, off-white, or purple screen. The system is clearly responsive to input, and the installation is (probably?) intact, but for example trying to load a terminal gives a black screen with no indication of there actually being a terminal prompt open.
[*]If I try to boot into the GRUB menu, I get the purple screen regardless. What is it these days, hold the right shift key? The left? Press ESC? because none of those change anything.
[*]Even if I try to boot to the flash drive again, I get a black screen, regardless of selecting "install Ubuntu" or "Try without installing." Both these options worked before - that's the strange thing.
[*]If I boot to the flash drive in CSM / Legacy mode (instead of UEFI) and select "install" or "try" from there, the system just reboots, which is super puzzling but probably unrelated to the existing installation (I hope)
[/LIST]

Yes, this is a UEFI (capable) machine. Yes, it's an AF HDD. Yes, it's a Radeon GPU, and yes, it is on [the list of "supported cards."]("https://help.ubuntu.com/community/RadeonDriver") I've already gone through the EFI settings on the motherboard to ensure I didn't have anything weird left over from the last build. It looks like the CPU is running about 100MHz higher than stock clocks, but with all the fans in this case that's not even an issue.

So here are the specs:

ASUS P8H67-M-LE (mATX)
Intel Core i5-2500K
Gigabyte WindForce Radeon HD 6850 1GB
Seagate 500GB AF SATA III HDD (note - running at SATA II speeds because of the motherboard)

I recognize this may be a simple fix, but I'm so utterly frustrated with what I've gotten by searching the web for days that I just have to ask here. If I had a graphical environment, presumably Unity, running in order to install in the first place, why's it suddenly not working?! 

Everything I've read seems to indicate that the drivers are either a) included in the installation if the hardware is detected, or b) somehow installable after-the-fact with other readily-available packages. According to [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), I shouldn't even be *having* this issue right now and shouldn't have in the first place. The article literally starts with the phrase "By default, Ubuntu will use the open-source driver..." and beyond that is utterly unhelpful to me because it, again, assumes I already have a working installation.

Before you suggest it, no, this is not a hardware problem. I've already booted a portable Windows environment on this machine with no problems. While I could give up and install Windows, it might not let me (re)use my key(s) and plus, I need a local Linux box of some sort. My webserver runs Ubuntu (cloud) and although there's no graphical environment I've still run into plenty of issues and fixed them as well. I run my database servers and mail server and everything else remotely, so you can hopefully understand why I may be getting frustrated with this problem, not even being able to *use *a fresh installation! :P

Thanks for your insight in advance. Apologies for the long-ish post. I can go into more detail wherever it's needed!

---

### Post by Dreamer Fithp Apprentice on 2014-01-12
> **NullCoding said:**
> I've found plenty of information about WHY this happens, but all the steps to mitigate it assume I'm somehow able to access a terminal to edit configuration files, which I cannot!Take out the drive and put it in another computer, not as the boot drive. Then edit all you like. Put it back in the other ... etc. PITA, I know but if it's as simple as editing a config file that should work. Or you could try making some live media from lots of different sources on another machine and try booting from some of them. Try a variety if you do that. There are several isos out that are intended to be jack-of-all-trades boot and fix it utility disks. Also trying very different distros you might luck into something. Try some as different as possible. Maybe PClinuxos since it is a Mandrake descendent, not a Debian. Good luck.

---

### Post by Bashing-om on 2014-01-12
NullCoding; Ouch !

I have a thought -> try and boot with the nomodeset boot parameter (??).

Can you boot to the grub menu ?
Cold boot and ;
a) As soon as the bios screen clears depress and hold the left shift key,
b) As soon as  the bios screen clears, repeated hit/release the left shift key ( a very small window in time for the system to recognize the key) - may have to repeat this several times to hit that window.
OK, got the grub menu ! 'e' key for edit mode;
arrow down and across to the term "quiet splash" and enter the term "nomodeset" -with out the quotes-.
key combo ctl+x to continue the boot process.
Do you boot to the GUI ?

No, let's see if you can boot to a terminal;
Boot to the grub menu -> 'e' key, edit out "quiet splash" and all after, insert the term "text" - with out the quotes -;
key combo ctl+x to continue the boot process.
Do you now boot to a terminal ?

Once you are booting into something we can take measures to get you all fixed up.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

