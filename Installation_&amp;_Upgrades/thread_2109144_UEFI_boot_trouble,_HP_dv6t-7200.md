---
title: "UEFI boot trouble, HP dv6t-7200"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by coastwatcher on 2013-01-26
[http://paste.ubuntu.com/1567809](http://paste.ubuntu.com/1567809).

Xubuntu 12.04 Amd64 installed on an HP dv6t-7200 laptop (EFI and
Win8), gave the following results.  If I just powered up the machine, it booted Win8.  If I pressed F9 during POST to get to the boot selection in the BIOS, I could choose "ubuntu", which then gave me Grub.  Selecting Linux from Grub worked fine, but the Grub entries for Windows and Windows Recovery didn't work.

Perhaps I should have left well enough alone, but I then booted a CD of Ubuntu 12.04.1 Secure Remix AMD64 and ran BootRepair.  I let it update itself from the web site, then chose the default repair.

After that, Windows no longer boots at all, either from the OS Boot Manager or from Grub.  From the OS Boot Manager, HP's substitute for a wristwatch icon, a string of balls chasing each other around a circle, continues indefinitely.  The same happens if I attempt HP's "automatic repair" function from F11 during startup.

Linux still runs fine (booting via F9 -> Ubuntu -> Grub).  I can mount any of the Windows partitions under Linux, and the contents appear superficially reasonable, so the partitions have not been totally overwritten. I cannot say more than that.

I'll probably have to re-image the machine from the recovery partition and then reinstall Xubuntu to be able to use Win8.  Before I do that, though, I'd like to find out how to avoid damaging the Windows installation, so I don't wind up in the same situation again.

I did run BootRepair a second time: the link is at the top of this message.

I'd really like to get to a state where:
1.  booting gets me to Grub by default
2.  the Windows items in Grub work.

Alternatively, I can re-image, reinstall Xubuntu, avoid BootRepair, and put up with needing F9 every time I boot.

OBTW, "efibootmgr -n 2000" DOES work: the machine boots to Grub the next time without manual intervention.  However, "efibootmgr -o ..." does not work.  The command gives no error output, but a subsequent efibootmgr with no operands shows the same boot order as before, and a reboot still won't come up in Grub without F9.

I could hack in a shutdown script to run "efibootmgr -n 2000" on every shutdown of Linux, but that's really ugly and should not be necessary.

One last detail: I did the Xubuntu install with manual partitioning, to put everything except /boot into a encrypted volume group.  I doubt that this matters, but thought I should mention it.

Suggestions gratefully accepted.

--coastwatcher

---

### Post by oldfred on 2013-01-26
I do not see shim file for grub2's version of the Windows secure boot. Maybe Xubuntu does not install that?

Do you have secure boot and fast boot still on, make sure you have turned them off.

Normally when you have run boot repair it adds correct Windows boot entries to 25_custom. Grub2's os-prober still creates old style BIOS boot entries that do not work.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by coastwatcher on 2013-01-29
I thought that the shim arrived with 12.10: I'm running 12.04.1.
I turned secure boot off before my first attempt to install Xubuntu on this machine.  I don't know anything about fastboot, but if it's on, it doesn't seem to be a problem.  (I did some command-line magic inside Win8 to get it to really shutdown, rather than hibernating: perhaps that's what's meant by disabling fastboot?)

What worked, since I had a working Xubuntu, was to install BootRepair in my working system, rather than booting the Secure Remix CD.  Running BootRepair under my working system and carefully following all the instructions it displayed did the trick.

My guess is that the reason that I needed to run BootRepair from my running system was one of the following:

1.  Since all of my install except /boot was on encrypted LVM, BootRepair run after booting from the Secure Remix CD did not have access to enough my working system to figure out what to do;

2.  The CD had booted in legacy mode, and that kept BootRepair from doing all the right things.

My Win8 is still hosed, but at least Grub does all the right things, including let me select any *.efi in the EFI boot partition of my drive.

I'll probably have to get a set of restore DVDs from HP to use in restoring the Win8 setup, then repartition and reinstall Xubuntu.
This time I'll know enough to run BootRepair only from my running Xubuntu system, not from the Secure Remix CD.  The light at the end of the tunnel might NOT be an oncoming train. :-)

Thank you.

--coastwatcher

---

