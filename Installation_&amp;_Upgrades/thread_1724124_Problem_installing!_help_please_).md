---
title: "Problem installing! help please :)"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by chg123 on 2011-04-07
Hi, I am running a toshiba laptop with 320 gig hd, 3 gigs of ram, and a 2.3 Ghz dual core intel.
I have downloaded ubuntu 10.10 and 10.04 and neither of them are installing. I know its not the disc as i am writing this off of the ubuntu OS but just the cd rom not the hard drive.

On both versions I have tried to install they get about a minute into installation and then it wont copy ext4/ to the partition or some thing like that. Its the same error on both versions so im starting to wonder if it issomething wrong with my hardware/hardrive? 

In addition, I dont have another OS on the laptop and i have tried swiping the hard drive and putting ubuntu onto the hard drive with no partitions or anything else. I dont know if that was stupid or even did anything but nothing I have tried is working!

Help would be greatly appreciated and you would be compensated with good karma (:

---

### Post by Quackers on 2011-04-07
Welcome to UF.
When booting from the live cd select "try Ubuntu" rather than "install Ubuntu" and see if the live desktop loads.

---

### Post by chg123 on 2011-04-07
I did do that! Thats what I meant by im running it off of the cd rom I suppose I didnt make that clear enough. But that works fine im using it right now it is only the installation I am having problems with.

---

### Post by Quackers on 2011-04-07
Ok thanks.
Are you using a raid array?
If you open gparted from within the live desktop (System > Admin > gparted) does it show any partitions present?
And how much ram do you have installed?

---

### Post by chg123 on 2011-04-07
Im sorry I am not sure what a raid array is.
When I open up gparted nothing shows up, I cant click on any buttons and it only says "No devices connected"
And I have 3 Gigabytes of ram installed in the computer

And thank you very much for trying to help me!

---

### Post by Quackers on 2011-04-07
You're welcome.
It seems that Ubuntu cannot see your hard drive! That is the problem.
What settings are in use in bios? Is AHCI selected? If not select it and try again.

---

### Post by heavy metal on 2011-04-07
maybe your hdd isn't recognized because the firmware is corrupt or maybe the hdd is dead, you should try getting a new hdd from a store who gives you 30 days or so to return the new hdd just in case it is not a problem with the old hdd, but I think is a prob with the old hdd...Trial and Error! for me is the best way to find answers to pc problems!

---

### Post by chg123 on 2011-04-07
"SATA Controller Mode: [AHCI]
 I assume that is what your'e speaking of and yes it was set to AHCI :/
The only other mode is compatibility mode.

---

### Post by Quackers on 2011-04-07
Ok, try compatibility mode and see if things improve.
Other than that we may be looking at a bad drive, or it needs re-seating perhaps - check leads, although in a laptop that's not likely unless you've had the drive out for some reason.

---

### Post by chg123 on 2011-04-07
I just tried turning on compatibility mode then saved changes and turned off the computer. Turned it back on and switched back at AHCI and then restarted again and tryed installing and now its working! It is farther than the installation has gotten yet so im being optimistic. 

Thank you for your help!!

---

### Post by Quackers on 2011-04-07
Hmm, bioses can be strange sometimes.
Good luck with your install! :-)

---

### Post by chg123 on 2011-04-08
The install worked! but unfortunately a notice popped up and told me hard drive failure is imminent! :O
but thank you for your help!

---

### Post by Rizzo4 on 2011-04-08
I download Ubuntu last night to install it  in my ToshibaSatellite pro L630, 320GB/HD 2G/RAM.
I try to checkout the the DEMO and it di not load it, also try to install it and all the time stop in the same place exctracting the file, I attached a pic you can look the way Ubuntu stop and did not load the system, I hope some could tell what can I do in order to install it, by the way I have a destk top and I could see de Demo

---

### Post by Quackers on 2011-04-08
Welcome to UF, Rizzo4.
When booting from the live cd, at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language and on the next screen press F6. Some options will appear bottom right. Click on the acpi=off option and then select the "try ubuntu" option to make sure the live desktop loads.

---

### Post by Rizzo4 on 2011-04-09
Quackers thanks a lot, it work, I will check how it work here then I will Install it, I work before with Reat Hat:KS:popcorn:

---

### Post by Rizzo4 on 2011-04-09
Quackers, thanks a lot, it works jut to check the Demo, I install it two time and always stop in the same place. also did not let my win 7 to work alone with it
[ATTACH]188543[/ATTACH]:confused:

---

### Post by Quackers on 2011-04-09
If you use acpi=off option for the live cd, you will also have to use it for booting the installed system.
If you have no other operating system you may need to hold down the shift key so that the grub menu shows up during boot. At the grub menu make sure that your Ubuntu system is highlighted then press the "e" key. On the next screen navigate to the end of the kernel line, which ends with "quiet splash". After quiet splash leave a space and enter acpi=off, then press ctrl+X to boot.
To make the change permanent you need to edit /etc/default/grub as described in this guide (the guide examples nomodeset, but you can replace that with acpi=off)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also be aware that turning acpi off can have undesirable results (although it often doesn't), like over-heating. Keep an eye on anything unusual.

---

### Post by Rizzo4 on 2011-04-09
When I finish the instalation and ask to remove the CD, another window pop up and it said filling the whole screan with this
[FONT=Calibri][SIZE=3][1023.738555] end_request: I/O error, dev sr0, sector 570236 this one is the first,,,,,, more in betwen until the last one that is the other one.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][1023.849786] end_request: I/O error, dev sr0, sector 570332.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]What can I do to fix this?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
 
#-o

---

### Post by Quackers on 2011-04-09
That's ok, it just happens sometimes with bad timing of the cd being ejected. It's nothing to worry about :-)

---

### Post by Rizzo4 on 2011-04-25
Does the new Ubuntu 11.4 would be compatible with Toshibas notebooks?:confused:

---

