---
title: "Dual boot Windows XP and Lubuntu:  Want GRUB as bootloader"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-09-02
Hi guys.  Nevermind about why I still use XP.  Long story.

I have XP as the only OS.  I want to make the computer a dual boot system, with Lubuntu as the other OS.  I know how to install it.  Normally I would do this:

During Lubuntu installation, at the part where I'm supposed to choose where to put GRUB, I choose dev/sda6 , which is the Lubuntu partition.  That way, Windows boot manager won't be overwritten by GRUB.  Then I boot into Windows and use EasyBCD to add Lubuntu to the list of operating systems that Windows boot manager shows at boot.

HOWEVER, that only works with Windows 7, NOT XP.  EasyBCD does not work in XP.

As I don't need Windows 7 on this particular computer, I would be fine with GRUB taking control of dual booting.  So during installation of Lubuntu, correct me if I'm wrong, I should choose dev/sda (not sda5 or 6, etc) as the part where GRUB is to be put.  This way, whenever I turn on the computer, it is GRUB that will show which OS I want to use, since GRUB has overwritten Windows boot manager.   

So my question is this, is it possible that I would be able to boot into Lubuntu, but if I choose XP in GRUB boot manager, XP would not boot? If that happens, do I simply boot into  XP cd and repair?  And after repair, would it still be GRUB as the main boot manager?

I know I could just try this out myself but I think that would be too time consuming.  This partiticular computer is being used everyday, all day.  

By the way, can GRUB detect FreeDOS that is installed in another partition?

Also, if GRUB is used instead of Windows boot manager, what would happen if I upgrade the Lubuntu to the latest version? And if I upgrade XP to 7 or 8 or 10?

Thank you for your time!!!

---

### Post by TheFu on 2015-09-02
The things you describe were fairly common before XP became unsupported.  

Every time Windows is installed, it will wipe the grub information in the MBR. MSFT doesn't play nice. Be prepared for that with a boot disk/flash drive.

We can't talk about what might work or might not work in the future, but it is likely things that worked in a certain way will continue to work in that way unless there is a bug or a reason for it to change.  For example, I bet that nobody will be testing WinXP and grub anymore. It will be hard enough to work with Win10.

My LUG is having an InstallFest in a few weeks - I may know more then.  I like trying new things on someone else's system. ;)

---

### Post by yancek on 2015-09-02
> I should choose dev/sda (not sda5 or 6, etc) as the part where GRUB is to be put.

Yes, particularly if you only have one hard drive.

> is it possible that I would be able to boot into Lubuntu, but if I choose XP in GRUB boot manager, XP would not boot? 

Yes that is possible although unlikely to the point of being a rare occurrence.  If it does happen, you can just run os-prober from Lubuntu and update Grub and that should solve the problem.

I've never used FreeDos but I expect you would be able to chainload to it and boot.
If you upgrade Lubuntu you should not have any problems and still be able to have the functioning bootloader.  However that is a major change to a system and you should always have everything of value backed up.  Always keep the installation medium of your install as situations like this are much easier to repair if you have problems.

Upgrading your windows will overwrite the boot code in the MBR.  You will not be asked if you want to do this nor will you be informed that it is happening.  If you go to windows 8 or 10, you need to inform yourself about UEFI booting.

---

### Post by TheFu on 2015-09-02
Win8+ do not require UEFI booting for upgrades. It is only for pre-installed systems where UEFI is required ... or to boot off GPT disks - then (64-bit Windows and UEFI) are mandatory.

+1 on having backups.

I assumed since the current boot is WinXP - no UEFI is supported on the hardware.

---

### Post by KayeNg on 2015-09-03
Thanks guys.  Another question if you don't mind. If a computer has both Lubuntu and Windows 7, and the system uses Windows Boot Manager, how can I replace WBM with GRUB? Should I boot into my Live Lubuntu USB? Then what would be the next step?
Thanks much!

---

### Post by TheFu on 2015-09-03
You don't replace it.  Just install any Ubuntu version and during the install, you will be asked about grub.  If there is 1 HDD connected, the answer will be pretty safe.

BTW - most of these questions would be answered by just looking at 1 of 1000 youtube videos of Ubuntu dual boot installations.

---

### Post by yancek on 2015-09-03
If you can boot into Lubuntu installed, just install Grub from Lubuntu to the master boot record.  In your case with only one hard drive it should be:

sudo grub-install /dev/sda

A lot of details on Grub with Ubuntu at the official site below:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by KayeNg on 2015-09-11
I know this thread is marked closed but allow me to share what I did.  To replace windows boot manager with grub, I typed these two lines in the terminal of Live USB:

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

Thanks!

---

