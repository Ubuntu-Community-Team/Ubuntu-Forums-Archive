---
title: "Selecting which drive to erase and encrypt?"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by ziphnor2 on 2023-10-27
I am trying to install Ubuntu 23.10 onto the secondary NVME ssd of my laptop. The primary SSD is encrypted with bitlocker and contains a windows installation. During installation I can select "erase disk" and then advanced features for full disk encryption, but it complains about bitlocker so I assume its picking the wrong drive. I can choose manual partitioning instead, but I see no options for encryption on that path.

What is the correct way to achieve this?

As a seocndary question, does Ubuntu support** hardware **full disk encryption (as supported by the drive (a Samsung 980 Pro ) ), and is there documentation on enabling it?

---

### Post by MAFoElffen on 2023-10-27
This is just how I would do that... First, when you are working with a dual boot of Windows, and it has bitlocker encrypted partitions, protect yourself by going into Windows control panel and suspending bit-locker. 

This will do two things: 1) It will let other tools be able to see into that partition and be able to identify what is there. 2.) It will help protect bitlocker from crashing from a corrupted filesystem.

I do this if I am doing things, like installing Linux alongside of Windows.

To further protect your Windows installation, you are doing the right kind of thing, by installing the new install to another physically separate drive altogether... You can go one step further, by disconnecting the Windows drive, before starting that new installation, so that there is no possible way, that the orignal installation of Widows will be affected.

After the install, shut down your computer, point the UEFI BIOS to your Ubuntu install to boot to it, enable OS_PROBER to be able to find your Windows OS on the other drive, so it can add it to the Grub2 boot menu during an update-grub... 

After it does that with the Grub2 menu update, then go back into Widows, into the control panel,  and turn bitlocker back on. And then you are all done.

Yes, that is just summarized instructions of that process. And yes... The canned script driven install of an encryted install in the installer, does erase, and install to a "full" disk. Not just to a partition.

If you wanted to do a manual install of LUKS encrypted, I have few recipes posted on the Forum for that.

I didn't catch which release of Ubuntu your are going to install. There are subtle differences in the release install options offered.

---

### Post by tea for one on 2023-10-27
> **MAFoElffen said:**
> To further protect your Windows installation, you are doing the right kind of thing, by installing the new install to another physically separate drive altogether... You can go one step further,[COLOR="#0000FF"] by disconnecting the Windows drive,[/COLOR] before starting that new installation, so that there is no possible way, that the orignal installation of Widows will be affected.l
Yes, this is the key to stress-free dual boot systems.

---

### Post by TheFu on 2023-10-27
Another option is to use virtualization rather than dual boot.  Then only 1 OS has direct access to the hardware, so there won't be conflicts.

---

### Post by MAFoElffen on 2023-10-27
> **TheFu said:**
> Another option is to use virtualization rather than dual boot.  Then only 1 OS has direct access to the hardware, so there won't be conflicts.
If you do that, enabling Hyper-V and installing Ubuntu as a Guest VM, then it already resides within the encrypted bitlocker container of the host, so would not need to be encrypted again as a VM Guest... That satisfies most IT policies where they that require encryption of OS'es for security.

---

### Post by TheFu on 2023-10-27
> **MAFoElffen said:**
> If you do that, enabling Hyper-V and installing Ubuntu as a Guest VM, then it already resides within the encrypted bitlocker container of the host, so would not need to be encrypted again as a VM Guest... That satisfies most IT policies where they that require encryption of OS'es for security.

Exactly.

Or, better, wipe that commercial OS from the hardware, install Ubuntu using the "Encrypt" checkbox, which will wipe the entire drive, then load that other commercial OS into a virtual machine to help limit the damage the commercial OS vendor might do to your Linux install in the future.

---

### Post by MAFoElffen on 2023-10-27
LOL!

Windows runs very well as a KVM VM Guest... And "contained", it cannot mess with the Host like it does in a Dual-Boot[SUP]*[/SUP]...

[SUP]*[/SUP] -- Which brings up something that hasn't been touched upon much here in this thread. You say you want to dual-boot. That means you accept that Windows has an ego and thinks it exists in a vacuum on a system. It takes over everything and acts as if anything it does is okay, because it works for them. That breaks a dual-boot sometimes. Things are going to happen, that you just have to accept will happen "eventually". Just like if you have NVidia on Linux. I've done multi-boots, and had NVidia since 2005. I know. It's happened to me many times.

This is what TheFu is hinting about.

---

### Post by ziphnor2 on 2023-10-28
> **MAFoElffen said:**
> 
This will do two things: 1) It will let other tools be able to see into that partition and be able to identify what is there. 2.) It will help protect bitlocker from crashing from a corrupted filesystem.


Ideally I would not want to touch anything on that disk at all, not even the bootloader. My frustration is that the ubuntu installer does not allow me to proceed when it sees bitlocker on one of the drives.

> **MAFoElffen said:**
> 
To further protect your Windows installation, you are doing the right kind of thing, by installing the new install to another physically separate drive altogether... You can go one step further, by disconnecting the Windows drive, before starting that new installation, so that there is no possible way, that the orignal installation of Widows will be affected.

I guess I will have to do that then, the BIOS has no option to disable the drive. Is there really no way to get the Ubuntu installer to ignore the bitlocked drive?

> **MAFoElffen said:**
> 
I didn't catch which release of Ubuntu your are going to install. There are subtle differences in the release install options offered.


Its 23.10 desktop.

Also, can I get Ubuntu to use the hardware encryption that the drive supports? Are there any guides for that?

---

### Post by TheFu on 2023-10-28
> **ziphnor2 said:**
> Ideally I would not want to touch anything on that disk at all, not even the bootloader. My frustration is that the ubuntu installer does not allow me to proceed when it sees bitlocker on one of the drives.


That's more to do with MSFT than any Linux.  When MSFT shuts down a computer, to save 0.000000000001 seconds, they don't actually dis-mount the file systems. They use hibernation mode instead, which leaves the file system "open".  Since EFI partitions are shared across all OSes on a computer - this is a standard too - that means that Linux knows not to touch anything.  You are upset about this, but it is a security feature, since obviously, you decided to encrypt the systems.  And bitlocker is proprietary, so it isn't like Linux can peak inside to see what's there.

I call this refusal to touch a "feature".

> **ziphnor2 said:**
> I guess I will have to do that then, the BIOS has no option to disable the drive. Is there really no way to get the Ubuntu installer to ignore the bitlocked drive?
Sure. Unplug the drive. That's "one way".  If your BIOS won't disable it, that's on the BIOS, since many BIOS will allow disabling specific drives.

> **ziphnor2 said:**
> Its 23.10 desktop.


Ah .. you like pain.  Great!  Thanks for being a tester. The rest of us appreciate it.  My stance is that nobody new to Linux or with less than 2 yrs hands-on, full-time, experience should use anything except an LTS release. The current LTS is 22.04. The next one will be 24.04.  Thanks again, for your service.

> **ziphnor2 said:**
> 
Also, can I get Ubuntu to use the hardware encryption that the drive supports? Are there any guides for that?

Depends on the drive.  Everything I've read about that leads me to believe it leaves a back door for the drive vendor and anyone with subpoena power to access the data. Perhaps I'm paranoid.  IDK.  I'd rather NOT have a company who likely sells hundreds of millions of USD to my govt being asked by said govt to unlock data on any storage device to actually have that ability.  It is a matter of trust.  I trust the LUKS guys 1000x more than I trust and HDD manufacturer or any govt, including mine.

Anyway, [https://wiki.archlinux.org/title/Self-encrypting_drives](https://wiki.archlinux.org/title/Self-encrypting_drives) has caveats (tpm must be enabled) and a guide for tools to be used.  I know nothing more than what is in that link about the tools.  Looks like about 40 steps to get to the point where installation of the OS is possible.

Or you can just check 1 box in almost any Ubuntu-based installer to use LUKS encryption and go with the defaults. This will setup boot, efi, and another partition. The other partition will be LUKS encrypted and inside that LUKS container, LVM will be setup to make using LVs rather than partitions for flexible storage possible. Almost always, I quickly reduce the "root" LV allocation to 35GB, add a 4.1G swap LV and add LVs for /var and /home to keep those separate from the OS. These are all inside the LUKS container, so for proper security, I need to fully shutdown the system whenever I take it from this building.  hibernation and standby modes leave encrypted storage susceptible to attacks.

For more security, you can setup a yubikey challenge/response to access the LUKS container.  That way, you'll not actually know the passphrase to unlock it, just the required challenge entry to have the yubikey device enter whatever the correct keyboard entries are.  With this mode, you also make the storage portable, since it isn't tied to 1 specific TPM chip.  That can be good or bad, depending on your needs.

---

### Post by MAFoElffen on 2023-10-28
> **ziphnor2 said:**
> Ideally I would not want to touch anything on that disk at all, not even the bootloader. My frustration is that the ubuntu installer does not allow me to proceed when it sees bitlocker on one of the drives.
...
Its 23.10 desktop.

Also, can I get Ubuntu to use the hardware encryption that the drive supports? Are there any guides for that?

The previous option I posted, I will refer to as option #1

This will be option #2:
With 23.10, the new Flutter installer is BitLocker aware... But it you download the Legacy 23.10 installer, which is on the same download page, that installer is ot bitlocker aware, so will let you install the encrypted option and should be able to choose which drive to install to, but that one will not create a separate EFI partition, but rather will add it's entries into the existing EFI partition.

Option #3:
Second question, I am assuming that you are talking about native SSD drive encryption... Yes, but you would have to do a quasi-manual-automated install where you would have a chance to unlock the drive, during the boot process. That process sort that would have to be added in a sort of hack. I have seen people do that for non-root drives, but for bootable OS'es, you would need to boot from a USB token key, to be able to start the boot process, unlock the drive, then hand off to that drive, to do it... Because it becomes a chicken before the egg affair. I cannot start a boot process from a natively locked drive. Setting that up is an advanced installation.

Option #4:
Which bring up another advance option. You can always install manually, where you setup the drives as LUKS containers, were you want them, and then start installer, use the patitoner in te "Do something else" mode, to choose which partitions to use, for what, then continue the installation... Though with that option, you need to use the legacy version of the installer, as the new Flutter Installer, though it recognizes bitlocker, is not volume manager aware, so does not recognize things like LVM, ZFS, BTRFS, and LUKS, if they exist on the Drive already.[SUP]*[/SUP]

[sup*[/sup -- I have a bug filed on this, for the new installer's partitioner. I feel that is something it needs to be aware of. Not being aware of these things that's those options away from us.  

Option #5:
There is a 5th option. That option is to remove the Windows drive and choose TPM backed encryption. With that option, I would not have the original drive physically connected during the install. Ensure to get and copy the recovery key before the first boot. Make a backup of the LUKS header ad recovery Key onto a USB drive. PM me to be able to generate a key-file for your backup, for the just-in-cases. It is a good idea, but is experimental and has some quarks to it. Currently- If the TPM's firmware is updated, that wipes everything in a TPM, and you would be required to manually enter the long recovery key each time it boots to unlock the encrypted rive.  and there is only a work-around that I have come up with, to be able to repair the install back to re-enroll the TPM back to for it to unlock the encrypted drive. I have a bug filed on that, with Launchpad, and an issue filed with the GitHub. It because of the real format of the underlying key, way they have that key-slot populated. The "recovery key" is really a translation of the real stored key. The user does to have the real master-key, to be able to authorize adding more keys to it's key-slots, or to be able to change a key, without the work-around I created to be able to do that...

Option #6 is to do TPM keyed LUKS manually...

Too many choices, and/or too much information? That is just for LUKS encryption, without going into if you are using Volume Managers within them... You kept asking question , so I laid them all out. That is Linux, where there are many ways to do the same things.

---

### Post by ziphnor2 on 2023-10-28
> **TheFu said:**
> 
Depends on the drive.  Everything I've read about that leads me to believe it leaves a back door for the drive vendor and anyone with subpoena power to access the data. Perhaps I'm paranoid.  IDK.  I'd rather NOT have a company who likely sells hundreds of millions of USD to my govt being asked by said govt to unlock data on any storage device to actually have that ability.  It is a matter of trust.  I trust the LUKS guys 1000x more than I trust and HDD manufacturer or any govt, including mine.


This is not a concern since this a work laptop, so no personal privacy issues.

> **TheFu said:**
> 
 Anyway, [https://wiki.archlinux.org/title/Self-encrypting_drives](https://wiki.archlinux.org/title/Self-encrypting_drives) has caveats (tpm must be enabled) and a guide for tools to be used.  I know nothing more than what is in that link about the tools.  Looks like about 40 steps to get to the point where installation of the OS is possible.


It was also a pain on Windows I can tell you. Some of those security vulnerabilities are pretty serious though (thanks for the link).

[> **TheFu said:**
> 
Or you can just check 1 box in almost any Ubuntu-based installer to use LUKS encryption and go with the defaults.


My primary concern is performance, at least in Windows performance impact is not neglible: [Tested: Windows 11 Pro's On-By-Default Encryption Slows SSDs Up to 45% | Tom's Hardware (tomshardware.com)]("https://www.tomshardware.com/news/windows-software-bitlocker-slows-performance")

---

### Post by TheFu on 2023-10-28
With LUKS and a CPU with AES-NI features, the performance hit is 3-20%, depending on the specific workload.  In my testing is is always sub-5%, so not really a concern at all.  Plus, if I need performance, I won't be using a laptop to start.  We all have different patterns of use and different needs.

I've been using LUKS on laptops for over a decade.  I don't bother backing up the LUKS header or key(s).  I do have excellent system/data backups, however.  Whenever encryption is used, having excellent backups is NOT optional. A little error can make access to the entire drive impossible, so any data could become effectively gone if a solar flare flips 1 bit in just the right place.  I used to work on spacecraft, so that was a real concern. We always had triple-redundant systems to avoid those strange things that could happen in hardware.

---

### Post by MAFoElffen on 2023-10-28
> **ziphnor2 said:**
> My primary concern is performance, at least in Windows performance impact is not neglible: [Tested: Windows 11 Pro's On-By-Default Encryption Slows SSDs Up to 45% | Tom's Hardware (tomshardware.com)]("https://www.tomshardware.com/news/windows-software-bitlocker-slows-performance")
My suggested Option #1 for installation (LVM in LUKS). Short de-encryption process on boot when the LUKS container is unlocked. Performance is great from there on... especially compared to bitlocker.

---

### Post by ziphnor2 on 2023-10-29
Okay, so just wanted to report where I ended up. First I removed the primary NVME drive, and went with erase disk in 23.10. As other have mentioned, STS releases are a bit rough around the edges as I quickly discovered. So decided to go with 22.04 instead. Being too lazy to remove the primary nvme drive this time, I was pleasantly surprised that this older installer did not complain about BitLocker but allowed me to simply select the disk I wanted to erase. However, after installation I found that the Windows boot was broken (booting into the rescue/troubleshooting mode). I tried using the Repair-Boot tool, but it appeared to just make things worse. In the end I went to the Windows repair command line and ran the bcdboot command, which fixed the immediate problem (booting from the primary disk now goes straight to windows).

The only remaining problem I have is that if I switch between booting Windows directly from the primary drive and from the grub option, then I have to use my Bitlocker recovery key. But I guess I will just use the grub menu.

---

### Post by TheFu on 2023-10-29
Yes, all OSes and machines expect there to be only 1 EFI partition to boot.  Having 2 (1 on each SSD) is going against the expectations, but if the installer finds the EFI on another disk,  then it will try to use it in a cooperative way. Linux usually plays nice with other OSes.  OTOH, MSFT never plays nice with other OSes - and when you used bcdboot, it "fixed" things by ignoring Linux.

Remember when I suggested using virtual machines instead way back in post #6?  Maybe it is clearer why now.  I haven't dual booted in a very long time.  These sorts of issues don't happen when 1 OS is booted on 1 hardware configuration - physical or virtual.

Hope you get things working the way you'd like. Good luck.

---

### Post by ziphnor2 on 2023-10-29
> **TheFu said:**
> 
Remember when I suggested using virtual machines instead way back in post #6?  Maybe it is clearer why now.  I haven't dual booted in a very long time.  These sorts of issues don't happen when 1 OS is booted on 1 hardware configuration - physical or virtual.


I have used VM's frequently in the past, but the problem is performance. My primary reason to going to Ubuntu is that I am tired of the various performance trade-offs in WSL 1 and 2.

> **TheFu said:**
> 
Hope you get things working the way you'd like. Good luck.

It looks like it. My hope is that I can use Ubuntu for 90%+ of the work I do (C# software development, containers/kubernetes etc). It is all part of an attempt to convince our IT department to "allow" our developers to use Linux.

---

### Post by MAFoElffen on 2023-10-29
Suspend bitlocker in the Windows Control Panel.

Edit the /etc/default/grub file with elevated permissions:
```

sudo nano /etc/default/grub

```
Go to this line
```

[COLOR=#ff0000]#[/COLOR]GRUB_DISABLE_OS_PROBER=false

```
Remove that "#" character to uncomment it... like this
```

GRUB_DISABLE_OS_PROBER=false

```
Save and save it, by doing <Cntrl><O>, <Enter>, <Cntrl><X>.

Update the changes and let OS_PROBER find the Windows OS in the system
```

sudo update-grub

```
Watch the output for the message that it found Windows and added it to the Grub Menu...

Restart Windows and turn bitlocker back on in the Control Panel. On the next boot of Windows you will have to enter in the bitlocker key, but after that, it should just open on it's own.

Point the UEFI back to Ubuntu. Test all the menu items.

If that all works, then will I add some other notes in a later post, what I do after that, for other added options for encrypted installs

---

