---
title: "nForce 780a: dmraid doesn't recognize SATA raid array"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by silanea on 2008-07-16
Hello!

I have run into trouble while trying to install Ubuntu 8.04 AMD64 onto a rig with an ASUS M3N-HT Deluxe mobo, sporting an NVIDIA nForce 780a chipset which supports SATA fakeraid, with two Seagate Barracuda ES.2 500GB drives configured as RAID 0 array. The raid is confirmed to work (Windows 2008 installed). Ubuntu fails me though. BIOS setting for the controller is "raid" btw.

Here's what I did so far:
[LIST]
[*] Since Ubuntu has trouble identifying any of my SATA drives including the disk drive, I boot off the AMD64 live cd with additional parameter [COLOR="Green"]pci=nomsi[/COLOR] which I found here in the forums. [COLOR="Green"]all_generic_ide[/COLOR] didn't do anything for me. I remove the two [COLOR="Green"]silent[/COLOR] options to see what the system actually does.
[*] The live cd boots, but I get errors about the HDDs being read beyond their limit.
[*] GPartEd shows only the two HDDs.
[*] I install dmraid.
[*] [COLOR="Blue"]dmraid -r[/COLOR] lists the drives correctly, both showing the same *nvidia_somestring* identifier.
[*] [COLOR="Blue"]dmraid -s[/COLOR] shows the *nvidia_somestring* set.
[*] [COLOR="Blue"]dmraid -ay[/COLOR] does not return any message.
[*] I run [COLOR="Blue"]dmraid -s[/COLOR] again. The set is **not** shown as active.
[*] I check the contents of /dev/mapper. There's only the default item (*control*, I think it was), but not the *nvidia_somestring*.
[*] GPartEd still only shows the individual disks.
[*] Nothing in /var/log/ shows anything out of the ordinary.
[*] I try [COLOR="Blue"]dpkg-reconfigure dmraid[/COLOR] which is successful, repeat above steps. No change.
[/LIST]

I tried the same with an Intrepid nightly live cd and a 8.04 32-bit live cd, same result.

[edit] Out of desperation I tried a Fedora 9 live cd (64-bit). Same problem, although I got an error message "I/O error, dev sr0" that I didn't get with Ubuntu. The raid set still wouldn't activate, just as under Ubuntu. [/edit]

What else could I try?

Thanks,

Flo

---

