---
title: "Anyone else have GRUB problems with XP?"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-03-12
I'm trying to boot my dual boot into XP.

I've got GRUB on the system, when I select the last entry (XP) it just comes up with the word GRUB on the screen, and the system stops doing anything.

Unfortunately my knowledge of GRUB stops around running grub-mkconfig (which I've done, but didn't seem to help out at all).

---

### Post by VMC on 2010-03-12
> **Arla said:**
> I'm trying to boot my dual boot into XP.

I've got GRUB on the system, when I select the last entry (XP) it just comes up with the word GRUB on the screen, and the system stops doing anything.

Unfortunately my knowledge of GRUB stops around running grub-mkconfig (which I've done, but didn't seem to help out at all).

We need a tad bit more information. Instead of asking for this and that ,download boot_info_script(see my blue link below), and run using sudo. Then attach the RESULTS.txt file.

---

### Post by Arla on 2010-03-12
> **VMC said:**
> We need a tad bit more information.

Yeah, I thought that might be the case, should probably add that, at least as of when I was running 9.10, this was working fine (been trying Lucid since about Alpha 3)

I've run and attached the results, many thanks for any assistance

---

### Post by Tikkyca on 2010-03-12
I was having when i dual booted xp and ubuntu,after uninstalling ubuntu xp crashed and now i just use ubuntu because it is awesome.

---

### Post by Arla on 2010-03-12
Would love to stick with just Ubuntu, but there are things that I need to use Windows for, as much as I'd love not to.

---

### Post by VMC on 2010-03-12
This is looks normal:>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.


There is something wrong with your XP partition:> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 49721964 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
 
Here's my XP partition as an example:> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


Maybe you have grub installed on your XP partition as well as the MBR of sda. That's what its saying anyway.

Everything else , UUID's, match.

---

### Post by Arla on 2010-03-12
> **VMC said:**
> 
Maybe you have grub installed on your XP partition as well as the MBR of sda. That's what its saying anyway.


Well no clue how that would have happened, I'm just doing updates via Synaptic every few days, but maybe I selected something odd, I do recall some odd GRUB config menu a while back (and I boot to XP infrequently enough not to know when it might have died on me).

I'll boot with my XP disc, and fix that way I guess, thanks for the assistance.

---

