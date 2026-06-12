---
title: "Ubuntu 24.04 won't boot after upgrade"
date: 2024-08-31
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2024-08-31
Hi!  I today, I was prompted to upgrade from 22.04.02 (I think) to 24.04.01.  This is a LTS to LTS upgrade.  :)   Anyway, I started the upgrade process and while the packages were being installed, I stepped away from the computer. I did click the buttons to switch Thunderbird to the SNAP version.  Other than that, I left the machine alone.   After a while, I looked at the screen and it was black.  I thought the monitor went into sleep mode, so I moved the mouse and pressed the space bar. Eventually a message reading "Gave up waiting for suspend/resume device" appeared.  Then, some other messages appeared, including an alert indicating a UUID couldn't be found.  I took a picture of the messages and will attach them to this post.

Anyway, I was eventually dropped in a "BusyBox" shell with an "(initramfs)" prompt.  When I tried typing "help" for commands, nothing appeared on the screen.  I did some web searches on "gave up waiting for suspend/resume device" and found some information on various commands to run, but I'm not sure how/where to run those commands.  For example, do I boot from an Ubuntu USB flash drive and still be able to run the "initramfs" or "grub" commands suggested to resolve the issue?    I did boot a Fedora USB flash drive I have and was able to run "blkid" and found the UUID of the SSD where Ubuntu was installed *matched* the UUID contained in the "alert" message.

At this point, I'm not sure what happened and I'm not sure how to proceed.  The last time I upgraded Ubuntu on this system, it went fairly smoothly.  The time before that, I had issues because the UEFI partition was too small and ran out of space.  lol

Any suggestions on how to proceed would be greatly appreciated!  Thanks in advance!

---

### Post by ubfan1 on 2024-08-31
The usual start for an LTS upgrade is to apply all the existing upgrades first.  22.04.2 is really out of date, if that's what you really started with. The UUID message might indicate an old grub.cfg stub was used.  Do you have more than one EFI partition hanging around (like the old small one)?  Check the partition flags the boot,esp flags should be on the EFI partition with the current information.  An upgrade doesn't normally touch the EFI partition unless grub or shim get upgraded. If you did change the root partition, then the EFI/boot/grub.cfg stub will need the new UUID (and maybe fix the explicit disk/parttiion hints).

---

### Post by tomdkat on 2024-09-01
Thanks for the reply!  I actually DID install updates before starting the upgrade process.  The system actually has 22.04.1 on is, so I was upgrading from 22.04.1 to 24.04.1.  When I encountered the issue with the EFI partition being full, I actually "nuked" the drive, re-built the EFI partition during the Ubuntu install process and got 22.04 LTS installed.   The EFI partition flags look good ("boot, esp" are set).

Soooo, what I ended up doing is re-installing 22.04.1.   The installer detected 24.04.1 was installed, so I chose the option to DELETE 24.01.1 (including my data) and install 22.04.1.   That went well.  Then, I did an update of 22.04.1 and it installed a bunch of stuff.  After that was done, if offered me the 24.04.1 upgrade.  I tried it again and noticed two things:

1)  The 24.04.1 installer stalled when installing the Thunderbird snap package.  I got the "force quit" popup several times (maybe close to 10) and chose to wait to give it a chance. It eventually finished and the installation resumed.

2)  After the installation completed, I rebooted and got the same "gave up waiting" problem I posted about above.

Sooo, there might be some kind of compatibility issue with this particular system (an HP Pavilion P7-xxxx (I forget the model,but I'll post that later)).    I re-installed 22.04.1 again and I haven't attempted the upgrade again.    I have another desktop I'll try installing 24.04.1 on and see how that fares.

This has been one of more rough Ubuntu upgrades I've done and I certainly hope this is an issue with my system, not with the 24.04.1 upgrade process itself.  Even with the 22.04.1 re-install, I've had to go through some "hoops" to get my data restored.  For example, Firefox 1.0.3 was installed and I had to "know" to update the snaps to get Firefox upgraded to 129 so my backed up data would work (bookmarks, extensions, etc).

Anyway, that's the latest for now.  :)

---

### Post by ubfan1 on 2024-09-01
The "point" numbers on the Ubuntu releases just indicate a patch level. A regularly updated/upgraded system will automatically change its lsb_release -a description to the appropriate number, and ISOs are made available at that patch level, so an install need not get years of updates.  I tend to have (at least) two root partitions on a system and alternate LTS releases, to keep the running system until I am happy with the new one.  I have upgraded at least one 22.04 system to 24.04, and didn't notice any particular issues. Check the UUID again from the EFI/ubuntu/grub.cfg which should use the Ubuntu root UUID, I would think a fresh install would overwrite it, but the 24.04 installer will actually use the user supplied device for the bootloaders (which might not be the one in use with multiple disks/ESPs).

---

### Post by tomdkat on 2024-09-11
> **ubfan1 said:**
> The "point" numbers on the Ubuntu releases just indicate a patch level. A regularly updated/upgraded system will automatically change its lsb_release -a description to the appropriate number, and ISOs are made available at that patch level, so an install need not get years of updates.  I tend to have (at least) two root partitions on a system and alternate LTS releases, to keep the running system until I am happy with the new one.  I have upgraded at least one 22.04 system to 24.04, and didn't notice any particular issues. Check the UUID again from the EFI/ubuntu/grub.cfg which should use the Ubuntu root UUID, I would think a fresh install would overwrite it, but the 24.04 installer will actually use the user supplied device for the bootloaders (which might not be the one in use with multiple disks/ESPs).

Thanks for the reply!  So, since I last posted I learned something.  I installed Ubuntu 22.04 on a different system, run updates and then upgraded to 24.04.  This time, the upgrade worked.  So, I think there's something peculiar about the original system I had the upgrade issue with.   Something else, on the second system, where the upgrade worked, I was prompted to answer more questions that I wasn't prompted to answer on the first system.  So, I think something might have caused a premature reboot, on the original system, such that the upgrade had not completed before the reboot.   The UUIDs all match.

I do plan on migrating to the second system, so I'll use that as my "resolution" to this issue.

Peace...

---

