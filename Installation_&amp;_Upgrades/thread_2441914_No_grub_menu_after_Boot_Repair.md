---
title: "No grub menu after Boot Repair"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by ldcdc on 2020-04-27
Hello guys&gals,

I'm afraid that I can't find an answer online for this situation I encountered.

Initial setup: Ubuntu 18.04, Windows 10, dual boot, grub menu with Ubuntu, Advanced, Windows as options. One Ubuntu boot partition, one root. UEFI system.

Repartitioned the drive to get rid of the separate boot partition because I hate having to clean it up all the time due to it being small.

I have restored a Kubuntu 20.04 backup (fsarchiver) from another laptop to avoid setting/installing everything from scratch. Changed partition UUID and fstab UUID and hostname.

Ran Boot Repair from a Lubuntu 18.04 usb stick.

In BIOS/UEFI  I have ubuntu first, then windows, as boot options. They both run fine, I can get in both OSes via BIOS menu.

But with the "ubuntu" boot option I was expecting to be greeted by the familiar default 10 seconds waiting Grub menu, which I don't see at all.

Instead the screen is black, and after some seconds (possibly 10, but it's hard to say) Kubuntu starts. I want the grub menu back, and nothing I've tried helped. Sorry, but I can't recall all the stuff I attempted. Played around with the grub resolution, hidden timeout option etc. Nothing worked, though I may have done it wrong. To know the correct resolutions I would need access to Grub, and I don't have it.

If anybody could point me in the right direction, I would be really grateful. Thanks!

[https://paste.ubuntu.com/p/ykcdYGhGYN](https://paste.ubuntu.com/p/ykcdYGhGYN)

---

### Post by oldfred on 2020-04-27
Pastebin not shown?

Since image from a different system, do you have different video on the two systems.

I find it easier just to do a new install, restore /home from backup. I have all data on separate data partition which I also backup. And export list of installed apps to restore.

---

### Post by ldcdc on 2020-04-28
Sorry about that. Link corrected.

Yes, I used to have a separate /home partition as well, with a list of apps to reinstall. This is the first time I go about it this route, thinking it would be faster, and it was - with one exception. You learn by doing I suppose? :)

About the video cards, they're different but not too dissimilar. Intel integrated graphics. Original system has an intel core i5 gen 3. "New" system is intel core i5 gen4. There are no issues that i've seen other than Grub.

I enabled Grub via /etc/grub/default to beep once when it loads (using some option I can't recall now). If I do a shutdown, I hear it at the next boot. I don't hear it when doing a reboot though - weird. Pressing Esc repeatedly only stops the booting procedure. I tried to blindly choose a different boot entry with the up and down keys, but that doesn't seem to work. The beep confirms it though that Grub is there, in the dark.

One thing I tried was "bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi" which bootrepair suggested to do if getting to linux was a problem, which it wasn't for me, but heck, I tried it anyway. That resulted in not being able to boot Windows at all. If I chose Windows in BIOS/UEFI, it simply redirected to Kubuntu. Then I spent maybe an hour repairing that, because of course a boot-fix windows command chose to tell me "access denied", and then I ran around in circles for a good while until I found the door back to Wonderland. :)

PS. I already had your thread open in a tab, and a detailed answer of yours on askubuntu from 2014 in another, but they're a bit too much for me. At some point this stuff gets way over my head. Hence this thread.

PPS. Looks like the old system had Grub Legacy mode installed. Can that be the cause?

---

### Post by oldfred on 2020-04-28
If 'old' system was i5 gen3 that was UEFI, but you could have installed in old BIOS/MBR mode.

UEFI and BIOS are not compatible.
Once you start to boot from UEFI, you cannot change. Or from grub, you can only boot other installs in same boot mode.
You can boot different install that is BIOS directly from UEFI one time boot menu as long as UEFI Secure Boot is off.

---

### Post by ldcdc on 2020-04-28
I was reading that grub can be installed in efi mode though, if it wasn't originally. I can boot Kubuntu just fine, I just don't see the grub menu.

As per the instructions at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) I did:

[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"

The result is "Installed in UEFI mode". Says "legacy" on the old computer.

What I do not have though is a boot/efi entry in fstab.

---

### Post by oldfred on 2020-04-28
Your link above to pastebin is working.
It shows mount of ESP in fstab.

I do not see why grub would not show. 
You have timeout set to 10 sec & multiple grub entries. Grub does not normally show if you only have one install.

Can you press Escape right after UEFI/BIOS logo for system and before grub menu. Sometimes you have to press several times or try as timing can be tricky.
And if you have UEFI fast boot on, then you may not have time to press any key.

---

### Post by ldcdc on 2020-04-28
You're right, there is an fstab entry. My memory failed there.

Fast boot is off. Pressing Esc stops the booting processs, but nothing on screen.

CSM is on. I tried to force display to internal in BIOS (I have a dual display setup on the old computer). No change.

PS. I just removed Kubuntu entirely, deleted all linux/ubuntu entries from the efi partition, removed the ubuntu entry in BIOS. Then did a full install Kubuntu 20.04 with ext4 format. Same issue - grub menu not visible.

Ubuntu 18.04 was showing the menu, and probably using an older version of grub. So I'm guessing something is changed in grub itself. Should I try a grub alternative? I was reading something about rEFInd.

PPS. OK, it seems that I found a workaround. Possibly even good enough to be marked as a solution. For me it is one anyway. It appears that Grub simply cannot display correctly in graphical mode on my laptop, no matter which resolution I try. Anyway, long story short, I switched to what may be just a "text mode", by uncommenting "#GRUB_TERMINAL=console" in /etc/default/grub. Then ran ```
sudo update-grub
```

Now I can see and choose the various Grub entries when booting. 

In case that doesn't work for someone, or gets deprecated, I saw that adding GRUB_TERMINAL_OUTPUT=console, or GRUB_TERMINAL_OUTPUT=vga_text,  to /etc/default/grub , does the job as well.

---

