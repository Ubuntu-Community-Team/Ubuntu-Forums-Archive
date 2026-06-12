---
title: "grub2 won`t boot windows xp"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by NFoster on 2011-01-03
ok so sounds like everyone elses issue that i`ve seen on here but i had it all working properly until i booted into ubuntu and updated grub somehow and when it told me to reboot all i got was a grub rescue error.

Now i got ubuntu 10.10 installed to try and fix the grub 2 error but now cant get it to boot windows from the menu.  

total noob and i have tried to give myself a crash course in this but i am totally stumped and its probably something so stupid.

Please any help is appreciated.

thank you

heres the boot info

---

### Post by drs305 on 2011-01-03
I don't see a problem in the RESULTS.txt. What happens when you boot? Do you see the Grub2 menu, the Windows entry, what then?

You might just try running "sudo update-grub" to make sure Grub2 has the latest information in it's configuration file.

---

### Post by NFoster on 2011-01-04
I can boot to the grub menu but when i highlight the windows to boot all i get is a blank screen and a flashing curser until i reboot myself.  

i have tried the update-grub a bunch of times with no help also ran windows recovery and ran fixmbr and fixboot from there.   

Windows will boot from the recovery disk and runs fine just wont boot from the grub2 menu so it leads me to believe that the problem is in the mbr or grub.

when i try apt-get install grub-pc /dev/sda  i get an error about the /dev not being mounted 

should i just try and uninstall ubuntu and get windows working and reinstall ubuntu later after windows is up and running.

i was unclear with the boot_info script because a couple others that i have seen at the top says grub2 was installed on /dev/sda and on /dev/sba and i dont have that so i dont know if grub is installed to the right place on the hard drive.  

thanks again tell me if anything else will help. i just have no idea where to go now.

---

### Post by NFoster on 2011-01-04
results.txt looks messed up to me. not sure how to post code in the forums.

also i have a single 250gb hdd split into a 100gb partition with the windows installation and the remaining 150 or so is just storage. 

the new install of ubuntu 10.10 was put on the first partition with windows but was installed from a usb not thru windows itself.

dont know if this is normal but i had a older version of ubuntu on the second partition and it showed a folder for ubuntu in windows but now the new install for 10.10 i dont see a folder on that partition for ubuntu in windows.

the older version of ubuntu is since been deleted from the second partition.  only have 10.10 on same partition as windows and it was installed after grub was corrupted from an update with the older ubuntu to try and fix grub that way

---

### Post by TheHackOps on 2011-01-04
Its probably a sign its time to ditch Windows and just use what works

---

### Post by dandnsmith on 2011-01-04
> **NFoster said:**
> results.txt looks messed up to me. not sure how to post code in the forums.

also i have a single 250gb hdd split into a 100gb partition with the windows installation and the remaining 150 or so is just storage. 

the new install of ubuntu 10.10 was put on the first partition with windows but was installed from a usb not thru windows itself.

dont know if this is normal but i had a older version of ubuntu on the second partition and it showed a folder for ubuntu in windows but now the new install for 10.10 i dont see a folder on that partition for ubuntu in windows.

the older version of ubuntu is since been deleted from the second partition.  only have 10.10 on same partition as windows and it was installed after grub was corrupted from an update with the older ubuntu to try and fix grub that way

Looks like you've thoroughly messed things up in your efforts to fix things.

I can see the grub2 boot stuff in RESULTS.TXT, with no entry to boot XP, and a normal looking set of boot stuff for XP which lacks the Windows boot to trigger it.

You might be able to fix it by putting a menuentry in the grub.cfg to invoke chainloading of sda1

mine looks like:
```

menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 0cd8cb21d8cb07c2
	drivemap -s (hd0) ${root}
	chainloader +1
}

```
but you'd need to modify that to take account of your XP location in sda1:
change (hd0,3) to (hd0,1)
and alter the id code.

If you then do any grub update it is likely to disappear, so save the bits somewhere.

---

