---
title: "Triple boot W11, OpenSUSE TW, Ubuntu 22.04.3 LTS"
date: 2023-11-08
forum: Installation &amp; Upgrades
---

### Post by SJLPHI on 2023-11-08
Hello,

I am a long time unofficial dev for OpenSUSE and my work requires me to use Ubuntu in some parts so I tried installing the Ubuntu 22.04.3 LTS and I had some issues:
[LIST=1]
[*]Metalink download keeps getting corrupt. I resolved it by downloading through utorrent and checksum before/after flashing a USB drive.
[*]I try to share the same /EFI partition between the OpenSUSE (managed by YAST) AND Ubuntu, and keep the partition unformatted.
[*]Windows 11 uses TPM and secure boot is absolutely required by the employer, will not disable it whatsoever.
[/LIST]

I am having trouble understanding with a couple of things.

During the installation, I was able to set up the partitions the way I think it should be without too much problem but when the UI asks where to install the "boot loader" what is it referring to exactly? Is it asking me where to install grub or the .efi image?

Upon installation, Ubuntu fails to boot because it cannot mount its / because kernel is not signed. This is with the "enable secure boot" option checked during installation.

Finally, it over-writes the Grub managed by YAST and does not find the OpenSUSE EFI, it looks like I may even need to install another /EFI partition dedicated for Ubuntu, which is not a big problem but odd.

For relevant information:
W11 is on a 1 TB NVMe SSD, isolated with its own EFI, home and etc. obviously GPT.
OpenSUSE TW is on a 2TB NVMe SSD, with 500MB EFI in the beginning, 300GB / partition BTRFS, shared 1TB /home partition ext4
In my current attempts I tried to shove the "boot loader" in the same as OpenSUSE TW EFI, without formatting and mounted as EFI, new 275GB partition ext4 as / , mount the shared ext4 /home on the same 2TB NVMe SSD (again, GPT)

TLDR; questions:
[LIST=1]
[*]In Ubuntu installer what does it mean by "install boot loader in xxxx partition"?
[*]Why is secure boot option not working?
[*]Why does Ubuntu's GRUB fail to find OpenSUSE EFI?
[/LIST]

Thank you.

---

### Post by yancek on 2023-11-08
Ubuntu generally will install its EFI files on the first EFI partition it finds  which might be the windows EFI partition.  This has changed but I'm not sure if 22.04   still does this.  Try mounting the EFI partition on the windows drive to see if you have a directory named ubuntu.  If not, repeat the process for the Opensuse drive.

Did you select and boot using the UEFI option in the BIOS for Ubuntu?  On a single drive, selecting either the drive or the EFI partition should work.  On multiple drives, you may have the problem mentioned above so check both drives for an ubuntu directory in the EFI partition.  There are efi files and a grub.cfg file in the ubuntu EFI directory on Ubuntu.  This grub.cfg file doesn't boot Ubuntu but simply points to the partition on which the Grub files exist.  Do not select to install Grub to a partition except the EFI partition.

I have 3 Linux systems installed with the default windows 10 and all Linux systems boot with TPM disabled or enabled while windows only boots with it enabled.  

I don't know why the EFI files for Opensuse could be overwritten as Ubuntu creates a separate ubuntu directory on the EFI paritition and installs its files there.  You should still have a directory there for Opensuse.  

Creating a separte EFI partition on the same drive as Opensuse is going to lead to other problems and is not advisable.
If you run:  sudo efibootmgr -v from Opensuse, to you see an ubuntu entry in the output?

---

### Post by SJLPHI on 2023-11-09
> **yancek said:**
> Ubuntu generally will install its EFI files on the first EFI partition it finds  which might be the windows EFI partition.  This has changed but I'm not sure if 22.04   still does this.  Try mounting the EFI partition on the windows drive to see if you have a directory named ubuntu.  If not, repeat the process for the Opensuse drive.


Well the installer offers to specify where to install the "boot loader", is this what the installer is calling EFI partition? It's definitely not in the Windows EFI partition, in fact when I specify the OpenSUSE EFI partition, it seems to over-write OpenSUSE EFI and grub completely.
> **yancek said:**
> 
Did you select and boot using the UEFI option in the BIOS for Ubuntu? On a single drive, selecting either the drive or the EFI partition should work. On multiple drives, you may have the problem mentioned above so check both drives for an ubuntu directory in the EFI partition. There are efi files and a grub.cfg file in the ubuntu EFI directory on Ubuntu. This grub.cfg file doesn't boot Ubuntu but simply points to the partition on which the Grub files exist. Do not select to install Grub to a partition except the EFI partition.

Yes, I set the UEFI (they are technically no longer called BIOS) to not support MBR/CSM and the USB stick is also flashed in EFI mode.

Again, can you explain to me what Ubuntu installer means by "boot loader"?

> **yancek said:**
> 
I have 3 Linux systems installed with the default windows 10 and all Linux systems boot with TPM disabled or enabled while windows only boots with it enabled.


Windows 11 is... special.. especially under corporate license with Azure. As a long time dual+ booter, I can tell you that Windows 11 is quite different from W10.

> **yancek said:**
> 
I don't know why the EFI files for Opensuse could be overwritten as Ubuntu creates a separate ubuntu directory on the EFI paritition and installs its files there. You should still have a directory there for Opensuse.

Well... it's gone. I chose not to format the efi partition but I did specify the "boot loader" to be installed in that partition.

> **yancek said:**
> U
Creating a separte EFI partition on the same drive as Opensuse is going to lead to other problems and is not advisable.


Sorry but why is it not advisable? Almost everyone chants that but I've never seen boot time issue from having multiple EFI's especially when you can identify them rather easily and mount the correct one for correct systems. I have it in a quad boot fine.

> **yancek said:**
> U
If you run: sudo efibootmgr -v from Opensuse, to you see an ubuntu entry in the output?
Yes, but since Ubuntu installer killed OpenSUSE's EFI, I had to use a flash drive to boot OpenSUSE and I was able to repair the boot-loader with YAST but this goes back to shim failure and the lack of signature on the Ubuntu kernel.

---

### Post by yancek on 2023-11-09
Bootloader means Grub and the expected install will be to create an ubuntu directory in the EFI partition separate from anything else there.  It should not overwrite anything in the EFI partition as long as there is room on the partition to do so.  I expect you would get an error message if that were the case but don't know for sure.  The standard files in this directory would be:

```
 BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
``` 

The grub.cfg file on the EFI partition has only a configfile entry point to the actual grub.cfg file on the system partition which is what is seen on boot.

>  Yes, I set the UEFI (they are technically no longer called BIOS)

Correct, I use the term BIOS because my HP refers to it as such, even though it has no option to boot in Legacy mode and is actually not able to do so.

>  Well... it's gone. I chose not to format the efi partition but I did  specify the "boot loader" to be installed in that partition.

If you have an ubuntu directory there with the appropriate files and your Opensuse files are gone, that would be surprising and I have no idea why that would happen.

There is not technical reason why multiple EFI partitions cannot exist on the same computer or the same drive.  It is just simpler for most users to have one.  I have multiple systems on the same drive and one EFI partition and no problem booting any so I have no reason to create more than one.

I don't have an explanation for the problem you report, the Opensuse EFI being overwritten which is definitely unusual behavior.

---

### Post by SeijiSensei on 2023-11-09
Have you tried using KVM and installing to virtual machines? 

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by MAFoElffen on 2023-11-09
Everyone please back and take a breath please...

What kind of machine are we talking about? 

OpenSUSE TW is  installed under SecureBoot Right? Please run the UbuntuForums 'system-info' script so that we can all see what is there already, as Hardware ad software. Keep SecureBoot and the TPM enabled for that.

Please backup... Use the Ubuntu 23.04.3 Installer LiveUSB > "Try"... In the desktop, open a terminal and do this:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
mokutil --sb-state

```
Just to ensure that the LiveUSB booted as UEFI mode.

The installer will do SecureBoot and TPM 2.0, which for business machines I had to service, that was their minimum, IT requirement... I could go into that more, but shouldn't need to. For the installer to toggle that option, it needs to be booted from UEFI and be able to see that the BIOS is set to SecureBoot Enabled... For 23.10 & Dev 24.04, there are more options that pop up when it see's the TPM enabled...

[s]Next, since you already have Grub2 installed with OpenSUSE Tumbleweed, do you want it to be the primary for managing the bootloader or Ubuntu? Because if it were me, I want to go one place to manage that, ad I do not need redundancy that sometimes gets confused on who is the primary, right?

If so, then ope a terminal and do this:
```

subiquity -b

```
That will install Ubuntu, but skip installing Grub2... (After the install, start OpenSUSE > Update Grub and let it's OS Prober find Ubuntu to add it to the existing menu...)[/s] <<Edited: explained in next post...>>

As I remember, when you get to the the first panel that asks if you want to install full or minimal, check the two checkboxes under that, with seeing the other two prerequisite conditions mentioned above there, that additional will trigger the signed kernels install mode to trigger and add to the screen to will ask for the password to enroll the EFI entries and kernels as trusted on the first boot... If you do not see that in the install before it asked for your UserData (Full Name, Hostname, UserName, Password), stop and post back here. You need that to happen, ad that would be an indicator that it doesn't see one of the conditions...

There is no sense to you to go through installing what does not meet your ITs Requirements.

Understood?

EDIT: That is off memory, but I do about 3-4 installs every day...I'm going to spin up a test-case for you, so I can confirm exactly what triggers that, and take screenshots for you, so you know what to look for. Okay?

---

### Post by MAFoElffen on 2023-11-09
This is what you want to see:
```

ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
UEFI Firmware mode
ubuntu@ubuntu:~$ mokutil --sb-state
SecureBoot enabled
ubuntu@ubuntu:~$ 

```
Attached is the screenshot...

Confirmed, check the box that says: "Install third-party..." Only when you check that box, with SecureBoot enabled, then the bottom ""Configure Secure Boot" will appear as editable, with the password fields to enroll the keys <-- Note: it cannot be a blank or null password, so make it something you can remember. You will only need to use it once, but still...

Then it will install the signed kernels... Thinking this through...


I'm going to edit my post from before... It will install the signed kernels, but you will still might need to install Grub2... To enroll the keys, they have to exist in the UEFI already... So if not, then you would have to skip that step, create the efi boot entries, then manually enroll them as trusted. That would be a chicken before the egg kind of thing. Might be easier to install Grub2 and let Ubuntu manage that. Would be a lot less manual work.

---

### Post by SJLPHI on 2023-11-10
> **SeijiSensei said:**
> Have you tried using KVM and installing to virtual machines? 

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)
 
No and I don't intend to. I need the raw interface.

---

### Post by SJLPHI on 2023-11-10
> **MAFoElffen said:**
> Everyone please back and take a breath please...

What kind of machine are we talking about? 

A modern intel 64bit laptop with embedded W11 license managed by a corporate. 

> **MAFoElffen said:**
> 
OpenSUSE TW is installed under SecureBoot Right? Please run the UbuntuForums 'system-info' script so that we can all see what is there already, as Hardware ad software. Keep SecureBoot and the TPM enabled for that.

Yes but I won't be posting the system-info script anytime soon as this is my currently my primary work computer, not booted in Ubuntu and I've passed off the job that requires Ubuntu to a desktop.

> **MAFoElffen said:**
> 
Please backup... Use the Ubuntu 23.04.3 Installer LiveUSB > "Try"... In the desktop, open a terminal and do this:
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
mokutil --sb-state

```
Just to ensure that the LiveUSB booted as UEFI mode.

I use Rufus to flash the drive and I can force GPT/EFI only and the UEFI on the laptop literally does not have CSM support.

> **MAFoElffen said:**
> 
[s]Next, since you already have Grub2 installed with OpenSUSE Tumbleweed, do you want it to be the primary for managing the bootloader or Ubuntu? Because if it were me, I want to go one place to manage that, ad I do not need redundancy that sometimes gets confused on who is the primary, right?

Yes, I like the Yast from OpenSUSE to handle the grub altogether.

> **MAFoElffen said:**
> 
If so, then ope a terminal and do this:
```

subiquity -b

```
That will install Ubuntu, but skip installing Grub2... (After the install, start OpenSUSE > Update Grub and let it's OS Prober find Ubuntu to add it to the existing menu...)[/s] <<Edited: explained in next post...>>

As I remember, when you get to the the first panel that asks if you want to install full or minimal, check the two checkboxes under that, with seeing the other two prerequisite conditions mentioned above there, that additional will trigger the signed kernels install mode to trigger and add to the screen to will ask for the password to enroll the EFI entries and kernels as trusted on the first boot... If you do not see that in the install before it asked for your UserData (Full Name, Hostname, UserName, Password), stop and post back here. You need that to happen, ad that would be an indicator that it doesn't see one of the conditions...


Yeah, the only thing I am worried about this step is the Mokutil not registering the EFI on boot.

---

### Post by SJLPHI on 2023-11-10
> **MAFoElffen said:**
> This is what you want to see:
```

ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
UEFI Firmware mode
ubuntu@ubuntu:~$ mokutil --sb-state
SecureBoot enabled
ubuntu@ubuntu:~$ 

```
Attached is the screenshot...

Confirmed, check the box that says: "Install third-party..." Only when you check that box, with SecureBoot enabled, then the bottom ""Configure Secure Boot" will appear as editable, with the password fields to enroll the keys <-- Note: it cannot be a blank or null password, so make it something you can remember. You will only need to use it once, but still...

Then it will install the signed kernels... Thinking this through...


I'm going to edit my post from before... It will install the signed kernels, but you will still might need to install Grub2... To enroll the keys, they have to exist in the UEFI already... So if not, then you would have to skip that step, create the efi boot entries, then manually enroll them as trusted. That would be a chicken before the egg kind of thing. Might be easier to install Grub2 and let Ubuntu manage that. Would be a lot less manual work.

Thanks! Okay, I do remember this creen and I remember checking the SecureBoot enabled but I don't remember having to enter a password at all.

I will give this another go when I have downtime again. I am also convinced that I probably do want to have a separate EFI for Ubuntu because Tumbleweed WILL destroy the /EFI when they totally fudge something up, it happened once in the past 6 years.

---

### Post by oldfred on 2023-11-10
Ubuntu & some recent flavors still use Ubiquity installer with this very old bug that really only applies to those who do not want /EFI/ubuntu on the Windows drive or a real requirement if an external drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
I use Kubuntu and more recent versions of it still were using Ubiquity.
Supposed the newer Subiquity installer does let you choose which ESP to use.

The installer question on which drive for boot files is really left over from BIOS installs. With BIOS it works, but with UEFI it defaults to first drive's ESP, no matter what you select. See bug report above.

You should be able to have both installs in one ESP, but if using /boot partition, you should not share /boot as that leads to conflicts. One may delete the other.

HP has not been the most friendly with UEFI boot. It does not seem to support boot order changes with efibootmgr. Grub install uses efibootmgr to change boot order. Typically most recent install or major update, whether Windows or Linux updates EFI settings to have that system as default. 
Many with HP have posted they could only change boot order with HP's system settings & boot tab, not UEFI boot menu.

What format does OpenSUSE use for / ?
If not ext4, you may need to add drivers in grub for Ubuntu to see it and an insmod command in grub's boot stanza so grub can see it.
Some with other formats often have to copy boot stanza from other install into 40_custom to have correct grub configuration. Os-prober does not always get it correct.

---

### Post by MAFoElffen on 2023-11-10
I just happen to be the author, project lead, and repository administrator for that script... I intended it to be open to other Distributions, and made sure it was tested for OpenSUSE and SUSE (and more). I made sure it was even more 'open' after it got a great review from DistroWatch on it. My intent was that it was targeted for Ubuntu Support here on the Forum to help it's members, but also a good tool for all Linux Users as a whole. The Forum Admin Council reviewed and blessed it when I gave it to the Forum for it's use... It is not just some random script. I made sure there was Forum Community involvement to make it "their own".

There is an eyes-only version of the report that displays to screen, but the 'finished report' is sanitized for privacy and security.

 LOL. oldfred is one the valuable 'testers' for it...

[hr][/hr]
Sorry if I get a little technical sometimes, I try to tailor that to who I'm speaking to. 

After doing that with the MOK password in the installer, the prompt to enroll the key doesn't show up until the next boot sequence.

There are some machines that are exceptions, o some branded computers, where they try to have the BIOS locked down to MS Windows itself... but you have OpenSUSE installed on it, so I do not suspect that is the case with what you have.

---

### Post by SJLPHI on 2023-11-10
> **oldfred said:**
> Ubuntu & some recent flavors still use Ubiquity installer with this very old bug that really only applies to those who do not want /EFI/ubuntu on the Windows drive or a real requirement if an external drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
I use Kubuntu and more recent versions of it still were using Ubiquity.
Supposed the newer Subiquity installer does let you choose which ESP to use.

The installer question on which drive for boot files is really left over from BIOS installs. With BIOS it works, but with UEFI it defaults to first drive's ESP, no matter what you select. See bug report above.

You should be able to have both installs in one ESP, but if using /boot partition, you should not share /boot as that leads to conflicts. One may delete the other.

HP has not been the most friendly with UEFI boot. It does not seem to support boot order changes with efibootmgr. Grub install uses efibootmgr to change boot order. Typically most recent install or major update, whether Windows or Linux updates EFI settings to have that system as default. 
Many with HP have posted they could only change boot order with HP's system settings & boot tab, not UEFI boot menu.

What format does OpenSUSE use for / ?
If not ext4, you may need to add drivers in grub for Ubuntu to see it and an insmod command in grub's boot stanza so grub can see it.
Some with other formats often have to copy boot stanza from other install into 40_custom to have correct grub configuration. Os-prober does not always get it correct.
My Tumblweed / is BTRFS. Honestly I am spoiled with YAST managing Grub for me with a UI and I will always prefer that over manually manging it and using mkconfig. Still useful but YAST Boot Loader can very easily re-write the ESP and often save a fudged installation.

So, you're telling me that the installer will just grab whatever the first partition is on the drive Ubuntu is being installed and puts grub in it? Yikes... sounds dangerous. I install using "something else" and try to specify each component and there I was already confused with the installer asking for where I want the boot loader even after I told it to mount the existing EFI partition.

---

### Post by SJLPHI on 2023-11-10
> **MAFoElffen said:**
> I just happen to be the author, project lead, and repository administrator for that script... I intended it to be open to other Distributions, and made sure it was tested for OpenSUSE and SUSE (and more). I made sure it was even more 'open' after it got a great review from DistroWatch on it. My intent was that it was targeted for Ubuntu Support here on the Forum to help it's members, but also a good tool for all Linux Users as a whole. The Forum Admin Council reviewed and blessed it when I gave it to the Forum for it's use... It is not just some random script. I made sure there was Forum Community involvement to make it "their own".

There is an eyes-only version of the report that displays to screen, but the 'finished report' is sanitized for privacy and security.

 LOL. oldfred is one the valuable 'testers' for it...

[HR][/HR]
Sorry if I get a little technical sometimes, I try to tailor that to who I'm speaking to. 

After doing that with the MOK password in the installer, the prompt to enroll the key doesn't show up until the next boot sequence.

There are some machines that are exceptions, o some branded computers, where they try to have the BIOS locked down to MS Windows itself... but you have OpenSUSE installed on it, so I do not suspect that is the case with what you have.
No need to apologize, technical is good even if it requires some readers to do a bit of research, we learn things that way.

Regarding enrolling MOK. I have never seen Ubuntu installation requesting it, even in a successful stable triple boot on my desktop (with secure boot enabled in UEFI).

My machines are not locked to MS products, but there is already a very annoying concept of MS Azure trying to use bitlocker on everything that exists that is readable by Windows, which is why I 100% separate the Windows drive and linux drive and keep the linux drive "offline" by Windows disk manager. However UEFI is set to boot from the linux EFI so that I can choose what to boot from with GRUB.

---

### Post by oldfred on 2023-11-10
With Ubiquity installer, i have tried everything.
The work around I do is to open terminal & unmount incorrect EFI and mount correct one at the screen where you input username & password. Mount is not shown in mount command until then.

Most remove esp,boot flags from other ESP, so then it only finds the one you want. Or disconnect other drives, so only one drive is seen.
Multiple work arounds posted in bug report.

---

### Post by MAFoElffen on 2023-11-10
What brand and model laptop (if you do not mind me asking? This would be so simple, if you could add a drive like my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME     LABEL       SIZE FSTYPE     MOUNTPOINT MODEL
sda                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   {SYSTEM}    550M vfat       /boot/efi  
&#9500;&#9472;sda2               128M                       
&#9500;&#9472;sda3   {Windows}   900G ntfs                  
&#9500;&#9472;sda4               983M                       
&#9500;&#9472;sda5                30G                       
&#9500;&#9472;sda6                32G                       
&#9474; &#9492;&#9472;swap swap         32G swap       [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member            
&#9500;&#9472;sda8   rpool       500G zfs_member            
&#9492;&#9472;sda9   hpool     397.4G zfs_member            
sdb                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1   kpool      1000G zfs_member            
&#9492;&#9472;sdb2   dpool       863G zfs_member            
sdc                  1.8T                       Dogfish SSD 2TB
&#9492;&#9472;sdc1   backups     1.5T zfs_member            

```
I have 6TB in it. I figure I can go up to about 18TB of internal storage... But I would rather invest elsewhere.

If you could add another drive, then it would be just isolating that disk during the install, just for Ubuntu and let it do what it needs to do to install, and keep it totally separate from windows ad whatever else you do not want changed... With no worries. Just pop out the other disks during the install and let it go, as if it were the only disk.

See the 3rd drive on mine? That is a 2TB mSATA SSD drive in a WWAN slot (which is a SATA slot). I have it setup for my ZFS snapshot backups, but since it is SATA, it will boot from that drive. 

Just throwing out other possible options.

---

### Post by SJLPHI on 2023-11-10
> **MAFoElffen said:**
> What brand and model laptop (if you do not mind me asking? This would be so simple, if you could add a drive like my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME     LABEL       SIZE FSTYPE     MOUNTPOINT MODEL
sda                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   {SYSTEM}    550M vfat       /boot/efi  
&#9500;&#9472;sda2               128M                       
&#9500;&#9472;sda3   {Windows}   900G ntfs                  
&#9500;&#9472;sda4               983M                       
&#9500;&#9472;sda5                30G                       
&#9500;&#9472;sda6                32G                       
&#9474; &#9492;&#9472;swap swap         32G swap       [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member            
&#9500;&#9472;sda8   rpool       500G zfs_member            
&#9492;&#9472;sda9   hpool     397.4G zfs_member            
sdb                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1   kpool      1000G zfs_member            
&#9492;&#9472;sdb2   dpool       863G zfs_member            
sdc                  1.8T                       Dogfish SSD 2TB
&#9492;&#9472;sdc1   backups     1.5T zfs_member            

```
I have 6TB in it. I figure I can go up to about 18TB of internal storage... But I would rather invest elsewhere.

If you could add another drive, then it would be just isolating that disk during the install, just for Ubuntu and let it do what it needs to do to install, and keep it totally separate from windows ad whatever else you do not want changed... With no worries. Just pop out the other disks during the install and let it go, as if it were the only disk.

See the 3rd drive on mine? That is a 2TB mSATA SSD drive in a WWAN slot (which is a SATA slot). I have it setup for my ZFS snapshot backups, but since it is SATA, it will boot from that drive. 

Just throwing out other possible options.
One of those newer "hipsters' facebook machines" Dell. It only has 2 NVMe slots and they are fully occupied and I had to make a bit of a case even just to get my 2nd SSD. A bit of negotiation after being suggested to use a WSL + Cloud to resolve the linux access and larger storage... I did convince them that the 2nd SSD was necessary eventually. When I was installing the 2nd NVMe, I did see an unoccupied NGFF 2422 slot but I don't want to bother... 

In my case I think an additional EFI partition would be best option... I will probably have to let Ubuntu absorb the existing EFI partition that is in the beginning of the SSD for linux drive and make a new one for OpenSUSE so that Ubuntu doesn't touch it.

My "dream setup" is at home and cannot use it for work, Lenovo P51 with 10TB, 2 NVMe 2TB SSDs and a 2.5" SATA

---

### Post by SJLPHI on 2023-11-10
> **oldfred said:**
> With Ubiquity installer, i have tried everything.
The work around I do is to open terminal & unmount incorrect EFI and mount correct one at the screen where you input username & password. Mount is not shown in mount command until then.

Most remove esp,boot flags from other ESP, so then it only finds the one you want. Or disconnect other drives, so only one drive is seen.
Multiple work arounds posted in bug report.
Well I have to say, it has been over 5 years since last time installing Ubuntu and it is a lot more frustrating than I was hoping it would be... I'm a bit bothered by that the bug you mentioned in [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) is still there after 10 years.

---

### Post by oldfred on 2023-11-10
Several years ago I installed both Fedora & Debian just to see if grub worked better. And it did. In both cases I was able to choose my sdb drive & it installed grub boot files into that drive's ESP.

Some systems do not like more than one ESP per drive. But you can work around it as it only seems important during install & initial creation of UEFI boot files which use GUID of ESP.
Grub does not care if a FAT32 partition has esp,boot flags. So you can move boot flag install grub & move boot flag back. Grub will still find another FAT32 with boot files to configfile into or directly boot an install on another drive.

With my very old 2006 BIOS only system, I was able to create a boot stanza to direct boot a full UEFI install with gpt partitioning on my external SSD. Actually made old slow system functional. But with only 1.5GB of RAM, could not load much at once. But when I loaded too much, swap was much faster than with old slow HDD.

I like full installs on external drives. I used to have multiple flash drives, but writes are very slow. Once I started using an external SSD, I now prefer that and added a second one. Full Kubuntu installs with ESP on external drive, so I can boot on other systems, if needed.

I see that grub has [IMG]https://ubuntuforums.org/audio/x-mod;base64,f0VMRgIBAQAAAAAAAAAAAAEAPgABAAAAAAAAAAAAAAAAAAAAAAAAAKBkAAAAAAAAAAAAAEAAAAAAAEAADwAOAAQAAAAQAAAABQAAAEdOVQACAADABAAAAAMAAAAAAAAA8w8e ki4AAAAAAAAAABIiff/4PMPHvpIuAAAAAAAAAAASIn3/ DzDx76QVRJvAAAAAAAAAAAVUiJ/VO7AQAAAEiLvUALAAA5nUgLAAB2FonYSMHgBEiLPAdIhf90A0H/1P/D69tIuwAAAAAAAAAA/9NIi714CwAA/9NIie9IidhbXUFc/ DzDx76UEiLf1BIuAAAAAAAAAAA/9AxwFrD8w8e kFWRYnGQVVBic1BVEmJ9FWJ1VOLB0iJ 41QAYtHBIkXOcJ2QL4CAAAAQbgLAAAA9 aJRwRwS4nASIt/CEhr8BhIuAAAAAAAAAAA/9BIhcB1D0i4AAAAAAAAAABEiwDrIUiJQwiLA0UxwP/ISGvAGEgDQwhMiSCJaAhEiWgMRIlwEFtEicBdQVxBXUFew/MPHvpBV0mJ90FWSYn QVVBVFVTTInDSIPsSEiJVCQISIkMJEmB P//AQB3RUi4AAAAAAAAAAC/AAACAP/QugAAAgBJicRJicVIhcB1Lki AAAAAAAAAAAxwDHtvwMAAABIugAAAAAAAAAA/9LpgwAAAEyLLCRMicJFMeRIiVQkEEiD7CC5BgAAAEi4AAAAAAAAAABIiUQkSEi4AAAAAAAAAABIiUQkUEi4AAAAAAAAAABIx0QkWAAAAABIjXQkSEiJ5/Ol/9BIg8QgSItUJBBIhcBIicV1Jki AAAAAAAAAAC/AwAAAEi6AAAAAAAAAAAxwP/SSIPL/ mIAAAASIlUJBhMif5MifdIuAAAAAAAAAAA/9BJvwAAAAAAAAAASIlEJBBIicdB/9dMi0QkEEiLVCQYhcB1H0iJ70yJ8UyJ7ki4AAAAAAAAAAD/0EiJx0H/14XAdBRIvgAAAAAAAAAAvxoAAADpfP///0iLdCQISIs8JEiJ2ki4AAAAAAAAAABMAe7/0Ei4AAAAAAAAAABMief/0EiJ70i4AAAAAAAAAAD/0EiDxEhIidhbXUFcQV1BXkFfw/MPHvpBVDHAVUiJ9VNIiftIg wgi49ICwAASIl8JAhIiXQkEEjHRCQYAAAAADnBdh9IicJI/8BIweIESAOTQAsAAEg5agh15UiLAum7AAAASL8AAAAAAAAAAEiNdCQISLgAAAAAAAAAAP/Qi4NICwAA/8CJg0gLAAA7g0wLAAB2ar4CAAAA9 ZwDYPAAYmDTAsAAHMK6zeJg0wLAADrL0yLo0ALAACJxki4AAAAAAAAAABIweYETInn/9BIiYNACwAASIXAdSRMiaNACwAASItEJBhIhcB0M0iJx0i4AAAAAAAAAAD/0DHA6yCLg0gLAACNUP9Ii0QkGEjB4gRIA5NACwAASIlqCEiJAkiDxCBbXUFcw/MPHvpNY8BBVzHAQVZJAdBJvgAAAAAAAAAAQVVJweAFSYn9SL8AAAAAAAAAAEFUTY18MDBNicxJidBIugAAAAAAAAAAVb6iAgAAU0iD7BBNi08ISItsJEhJjRwJSLkAAAAAAAAAAFNB/9ZMie9JizdIuAAAAAAAAAAA/9BBW0FdSIXAdDFIidpIwesJSIs4SYnoQVlIid5MieFbgeL/AQAAXUFcSLgAAAAAAAAAAEFdQV5BX//gSLoAAAAAAAAAADHAvqoCAABIuQAAAAAAAAAASL8AAAAAAAAAAEH/1ki4AAAAAAAAAADHAAAAAAC4DgAAAFpbXUFcQV1BXkFfw/MPHvpIixaDyP9IORdyLLgBAAAAdyWKTgiDyP84TwhyGrgBAAAAdxNIi1YJg8j/SDlXCXIGD5fAD7bAw/MPHvpBUEg5VjB0Pr46AQAAMcBIuQAAAAAAAAAASLoAAAAAAAAAAEi/AAAAAAAAAABJuAAAAAAAAAAAQf/QSL4AAAAAAAAAAOtZSIPGIEiDxyC6EAAAAEi4AAAAAAAAAAD/0IXAdFC QAEAADHASLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAASbgAAAAAAAAAAEH/0Ei AAAAAAAAAAC/CQAAADHAWUi6AAAAAAAAAAD/4ljD8w8e kFXSb8AAAAAAAAAAEFWSYn QVVJifVBVFVIvQAAAAAAAAAAUzHbSIHsOAsAAEiLdQBMjUQkBbkrCwAAMdJMifdB/9dBicSD At0eLoIAAAASI18JEVIvgAAAAAAAAAASLgAAAAAAAAAAP/QhcB1SYXbdAtJi0VISDlEJE12GborCwAASI10JAVMie9IuAAAAAAAAAAA/9D/w4P7BHQaSIuEJNYAAABIg8UISMHoCUg7RQAPh3X///9Bg/wLdAVFheR1P4XbdSJIvgAAAAAAAAAAvwkAAAAxwEi6AAAAAAAAAAD/0kGJxOsZQYP8C3UTSLgAAAAAAAAAAEUx5McAAAAAAEiBxDgLAABEieBbXUFcQV1BXkFfw/MPHvpVU1FIiy9Ihe11Iki AAAAAAAAAAC/CQAAADHASLoAAAAAAAAAAP/S6YQAAABIuAAAAAAAAAAASIn7v4ALAAD/0EiJxUiFwHRoSInGSIs7SLgAAAAAAAAAAP/QhcB1J8eFTAsAABAAAAC/AAEAAEi4AAAAAAAAAAD/0EiJhUALAABIhcB1E0i4AAAAAAAAAABIie8x7f/Q6xhIi5XJAAAAx4VICwAAAQAAAEiJGEiJUAhIiehaW13D8w8e ki4AAAAAAAAAABBVEm8AAAAAAAAAABVU0iJ80jHBgAAAAD/0EiFwA EigAAAEiJxWZEi0goZkSLQCZIvwAAAAAAAAAAZotIJGaLUCJJugAAAAAAAAAAZotwIFBmQcHBCGZBwcAIhulmi0UuRQ 3yUUPt8CG8mbBxgiG4A 39g 3yQ 30g 3wFBmi0UshuAPt8BQZotFKobgD7fAUDHAQf/SSInvSIkDSLgAAAAAAAAAAEiDxCD/0EGLBCRbXUFcw/MPHvpIuAAAAAAAAAAAQVRJvAAAAAAAAAAAVVNIifNIxwYAAAAA/9BIhcB0LUiNuCsBAABIicW AAEAAEi4AAAAAAAAAAD/0EiJ70iJA0i4AAAAAAAAAAD/0EGLBCRbXUFcw/MPHvpIuAAAAAAAAAAAVVNIifNIgew4CwAA/9BIicUxwEiF7Q EsAAAAEiLfQBIhf8PhIkAAABIuAAAAAAAAAAASI10JAX/0IP4CXUjSLgAAAAAAAAAAEiJ7//QSLgAAAAAAAAAAMcAAAAAADHA62qFwHQdSLgAAAAAAAAAAEiJ7//QSLgAAAAAAAAAAP/Q69tIiwO6EAAAAEiNdCQlSI14IEi4AAAAAAAAAAD/0IXAdQ5Ii0MISDmEJM4AAAB0EUi4AAAAAAAAAABIie//0OubSIlrELgBAAAASIHEOAsAAFtdw/MPHvpIY/ZIweYESAH g34IAHUWSLgAAAAAAAAAAMcADgAAALgOAAAAw0yJwkiJz1BIizZIuAAAAAAAAAAA/9BIuAAAAAAAAAAAxwAAAAAAMcBaw/MPHvpBV0FWQVVBVFVIidVTSIPsOIsXSDnyD4e AQAASYn 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 AF0O0i6AAAAAAAAAAC 4gMAADHASLkAAAAAAAAAAEi/AAAAAAAAAABB/9QPt1UsSL4AAAAAAAAAAOk2AgAASIXAdQW7AAIAAEiJ3kyJ/0iNlCSwAAAASLgAAAAAAAAAAP/QTCt0JAhIiYQkqAAAAEj/wEgPr8NKjRww6RcDAAC4AQAAAP/A/8C 9wMAAEi5AAAAAAAAAABIugAAAAAAAAAAiUQkEEGJwDHASL8AAAAAAAAAAEH/1EiLXQBMibwksAAAAEjHhCSoAAAAAAAAAEQPt00sTAHzSCtcJAhEO0wkEA EBwMAAESLRCQQMcBIuQAAAAAAAAAASLoAAAAAAAAAAEi/AAAAAAAAAAC AgQAAEH/1A 3TSyLVCQQvwkAAABIvgAAAAAAAAAAMcBJuAAAAAAAAAAAQf/Q6RwJAABIuQAAAAAAAAAAvg4EAAAxwEi6AAAAAAAAAABIvwAAAAAAAAAASb4AAAAAAAAAAEH/1EiNlCTAAAAASIneTIn/Qf/WSI2UJKgAAABBD7f1SInHQf/WSIuUJMAAAADp4wEAALkBAAAAZoN9LgBIid5Mif9Bic6JTCQQZkQPRXUuSI2UJMAAAABJvwAAAAAAAAAAQf/XMdKLTCQQSInHRInoZkH39kiNlCSoAAAAZoXAD0TBD7fwQf/XQQ 31kQPt0UuQQ 3zkgPr5QkqAAAAIlMJBBID6/DSImUJKgAAABIi5QkwAAAAEgB0Egp00iJhCSwAAAAZkGD AIPhLABAABIugAAAAAAAAAAvjMEAAAxwEi5AAAAAAAAAABIvwAAAAAAAAAAQf/UD7dVLki AAAAAAAAAAC/CQAAADHASLkAAAAAAAAAAP/R6c8HAACA4oB0L0i5AAAAAAAAAAC RQQAADHASLoAAAAAAAAAAEi/AAAAAAAAAABB/9S5AQAAAOstSLkAAAAAAAAAAL5KBAAAMcBIugAAAAAAAAAASL8AAAAAAAAAAEH/1LkCAAAASIlMJBBMif9Iid5FD7ftSI2UJMAAAABJvgAAAAAAAAAAQf/WSItMJBBIicdJOc13D0i AAAAAAAAAADpcfr//02J6EiNlCSoAAAASSnITInGTIlEJBBB/9ZIi7wkqAAAAEiNlCSoAAAATInuSYnHSAHHQf/WTItEJBBIjZQkuAAAAEyJ7kuNPDhB/9ZIi5QkwAAAAEyJ EgPr8NIKdNIAdBIiYQksAAAAMdEJBABAAAA604xwL6QBAAASLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAAQf/USItVGL8YAAAAMcBIvgAAAAAAAAAASLkAAAAAAAAAAP/R6W0GAABIhdt1Iki AAAAAAAAAAC/JgAAAEi6AAAAAAAAAAAxwP/S6UYGAABIOVwkQMdEJGACAAAASA9GXCRASYnfSIsEJL6mBAAASLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAATItACUFSD7dFLv91EEyLTQBQD7dFLFAxwEH/1DHAvq8EAABMi0QkKEi6AAAAAAAAAABIuQAAAAAAAAAASL8AAAAAAAAAAEiDxCBB/9QPt0UsSInCSMHgBUiDwDBIOUUAD4InBQAAZoP6KQ HHQUAAEiDfCRoAA EqwQAAE2J UUxwEiJ7ldIuAAAAAAAAAAA/3QkMEiLjCTAAAAASLsAAAAAAAAAAEiLlCS4AAAASIt8JDD/0McDAAAAAEFYQVmFwA E1gQAAEiLhCS4AAAARA 3dSy EAAAADHbSb0AAAAAAAAAAEiJRCRwSIuEJKgAAABMifdIiUQkeEiLhCSwAAAASImEJIAAAABIi0UYSIlEJFhIuAAAAAAAAAAA/9BIiUQkGEiDfCQYALgDAAAAD4TTAwAASTnediRMif9B/9VIi0wkGEiJ2kjB4gRIiQQRSIXAD4R2BAAASP/D69dIi0QkGEyNbTAx20jHRCQwAAAAAEiJRCQ4SIlEJEhMO3QkMA GSAEAAEyLhCSAAAAATQNFCDHASLkAAAAAAAAAAEyJhCSIAAAATYtNAL4YAwAASLoAAAAAAAAAAEi/AAAAAAAAAABB/9RJi3UASIt8JCBIuAAAAAAAAAAA/9BMi4QkiAAAAEiFwHUxTYtNAEyLRCQwSLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAAvh8DAADpmwAAAEiLTCRITInCTInGSIs4geL/AQAASMHuCUi4AAAAAAAAAABMiwFMifn/0IXAdT9Ii0QkSE2LTQBIuQAAAAAAAAAASLoAAAAAAAAAAEyLRCQwvisDAABIvwAAAAAAAAAAx0AIAQAAADHAQf/U6zRNi00ATItEJDC MAMAADHASLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAAQf/USP/DSP9EJDBJg8UgSINEJEgQ6a3 //9Mi2wkWEGB5YAAAABIg/sBdmxNhe10IUmJ2U2J8Ei5AAAAAAAAAABIugAAAAAAAAAAvjkDAADrLUiD wJ0QA 6ZCRYCHM4SYnZTYnwSLkAAAAAAAAAAEi6AAAAAAAAAAC QQMAAEi/AAAAAAAAAAAxwEH/1LgOAAAA6YcCAAAxwEmJ2U2J8L5IAwAASLkAAAAAAAAAAEi6AAAAAAAAAABIvwAAAAAAAAAAQf/UTYXtD4Q/AQAARTHASItcJBhMicBIweAEg3wDCAB0Ck05xnYFSf/A6 NNOcZ1LUi5AAAAAAAAAAC xwIAADHASLoAAAAAAAAAAEi/AAAAAAAAAABB/9TpKwEAAEi5AAAAAAAAAAAxwDHbSLoAAAAAAAAAAEi/AAAAAAAAAAC ywIAAEm9AAAAAAAAAABB/9RBuQEAAABJOd4PhugAAABIi0QkOIN4CAAPhI0AAABFhcl0E0iLMEiLfCQoTIn6Qf/VRTHJ63VIi0QkOEyJ UiLMEiLRCQoSInySAnCg IHdBGKFkj/xjAQSP/ASP/JdebrSTH/SYnISSn4SYP4B3YOTIsEPkwxBDhIg8cI6 ZIic9JichIwe8DSYPg Ehr//hMAcBMAcZIAflIOdF0DUCKPBZAMDwQSP/C6 5Ig0QkOBBI/8PpTf///0i4AAAAAAAAAABWRTHJTIn2UEi4AAAAAAAAAABqAEFXTItEJEiLjCSQAAAAi5QkmAAAAEiLfCQ4/9BIg8QgMcDpzAAAAIlEJDBIi3wkGEi6AAAAAAAAAAD/0otEJDCFwHVU63ZIuwAAAAAAAAAARTHtTYn5UEWJ6EiJ7v90JDBIi4wkwAAAAEiLlCS4AAAASIt8JDD/01pZhcB0Pki5AAAAAAAAAABB/8XHAQAAAABEOWwkEHW7g3wkYAF0EsdEJGABAAAA6Uz6// 4CQAAAKMAAAAAAAAAAOtsTCl8JEBMAXwkKEwBfCQIg3wkVAAPhPjx//9IuAAAAAAAAAAASInv/9Dp5PH//zHA6zq4AwAAAEm9AAAAAAAAAAAx20k53g GH////4lEJDBIidpIi0QkGEj/w0jB4gRIizwQQf/Vi0QkMOvXSIHE AAAAFtdQVxBXUFeQV/D8w8e kFXSYn3QVZBVUmJzUFUSYnUVUiJ/VNMicNIgeyYAAAAQYsHhcAPhDgBAAD/yEiJwkhrwBhJA0cIi3gIjU8BiUgIO0gMcw9JvgAAAAAAAAAA6YwAAABBiRfrxkhr9iFFMcC5IQAAAEiJ70gB1kiNVCQKQf/WhcAPhawAAABFMcBIi3QkG7llAAAASInvSI1UJCtB/9aFwA FjAAAAEiLVCQbSI10JCtIie9IuAAAAAAAAAAA/9BFMcCAvCSPAAAAAEyJ/0EPlMBIi3QkGzHSi4wkiwAAAEi4AAAAAAAAAAD/0EGLB//ISGvAGEkDRwhIiwiDeBAAi3AISI1RZQ EWP///0hr9hlMjUwkK0UxwEiJ77kZAAAASAHWTInKQf/WTI1MJCuFwHQE99jrN4tEJECLVCQ8uREAAABIid9Mic5JiUUAQYsH/8hIa8AYSQNHCEiLAEiNRAJlSYkEJLgBAAAA86RIgcSYAAAAW11BXEFdQV5BX8PzDx76SLgAAAAAAAAAAEFUSYnUVUiJzVNIifNIgewQAQAASItPUEjHRCQ/BQAAAEjHRCRIAAAAAMZEJEeEagBqAEiJfCQYTI1MJDBMjUQkKEiNVCQ SI10JE//0FpZhcAPhYsAAABIi0QkLkg5RCQ/dRuKRCQ2OEQkR3URSItEJDdIOUQkSEiLfCQIdB9IvgAAAAAAAAAAvwkAAAAxwEi6AAAAAAAAAAD/0utFRTHASIt0JBi5wAAAAEiNVCRQSLgAAAAAAAAAAP/QhcB1I0iLlCQAAQAAxkMIVEjHQwkAAAAASMcDAAEAAEmJFCTGRQACSIHEEAEAAFtdQVzD8w8e ki4AAAAAAAAAABBVEmJ9FNIidNIg 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 // LVCQgSInevwEAAABBxkYIVEi4AAAAAAAAAAD/0GoATIn2agD30EiLfCQgSYlGCUiLRCQoTI1MJHBMjUQkaEiLCEi4AAAAAAAAAABIjVQkf//QXl FwA FVgMAAEiNdCRvTIn3SLgAAAAAAAAAAP/QhcAPhYsDAABIi0QkYEg7RCQwdk9JvwAAAAAAAAAASAHATInnSIlEJDBB/9dIi0QkMEiNeAFIuAAAAAAAAAAA/9BJicRIhcB1GkyJ70H/10iJ70H/16EAAAAAAAAAAOn9AwAARTHASItMJGBIi3QkWEyJ4ki4AAAAAAAAAABIi3wkEP/QhcAPhbYCAABJuAAAAAAAAAAATYniTInRTCnhSDtMJGAPjekCAABBD7dCG0g5RCQgdBRBD7dSG0EPt0IZTI1UAh5NAeLrz0iJTCRISY16HkiLVCQgSIneTIlUJEBB/9BMi1QkQEiLTCRISbgAAAAAAAAAAIXAdbtIO0wkYA NjQIAAEGKQh08Bw FkQEAAP9MJDx1O0i7AAAAAAAAAABMief/00yJ7//TSInv/9O/GQAAAEi AAAAAAAAAABIugAAAAAAAAAAMcD/0ukNAwAASItEJBhJixJMiVQkIEiNtCSAAAAASLsAAAAAAAAAAEiLfCQQSIsISLgAAAAAAAAAAP/QTItUJCCFwHQMiUQkCEyJ5 m4AQAATIu8JJAAAABMiVQkIEi4AAAAAAAAAABIi3wkCP/QSY18BwFIuAAAAAAAAAAA/9BMi1QkIEiFwEmJx3UPTInn/9NMie//00iJ7 tFSYnASItEJBgxyUmLMkyLjCSQAAAASIt8JBBIixBIuAAAAAAAAAAA/9BIO4QkkAAAAHQZTInn/9NMie//00iJ7//TTIn//9PpI/7//0i4AAAAAAAAAABIi3wkCP/QSIu8JJAAAABIi3QkCEiNUAFIuAAAAAAAAAAATAH//9BMie//00GAPy90DUyJfCQITYn96ez7//9Ii0wkKEiLVCQYTIn2SLgAAAAAAAAAAEiLfCQQ/9CFwA FvwEAAOvLSIt0JCiIBkGKUgiA gEPhM4AAACA oQPhT4BAABIi0QkEEyJ1kiLSFBqAEi4AAAAAAAAAABqAEiLfCQgTIlUJDBMjUwkcEyNRCRoSI1UJH//0FpZhcBMi1QkIHVCSItEJG9JOQIPhYUAAACKRCR3QThCCHV7RTHASIt0JFhIi3wkELnAAAAASI2UJIAAAABIuAAAAAAAAAAA/9CFwHQaiUQkCEyJ50i7AAAAAAAAAAD/00yJ7//T629Ii4QkMAEAAEiLTCQYQcZGCFRJx0YJAAAAAEnHBgABAABIiQHp4vr//0iLdCQIgD4AdEr yHVGSLsAAAAAAAAAAEyJ5//TTInv/9NIieq/BQAAADHASL4AAAAAAAAAAEi5AAAAAAAAAAD/0YlEJAhIie//04tEJAjphwAAAEiLRCQouREAAABMifdMidbzpIA4Ag Fc/r//0HGRghU6Wn6//9MiVQkCEyJ70i7AAAAAAAAAAD/00iJ7//TTInn/9NMi1QkCL8JAAAAMcBIvgAAAAAAAAAASLkAAAAAAAAAAEEPtlII/9HrG0i7AAAAAAAAAABMief/00iJ7//TTInv/9MxwEiBxEgBAABbXUFcQV1BXkFfw/MPHvpIuAAAAAAAAAAAQVZBVUmJ9UFUVVNIiftIgezAAAAASIt/CP/QSIXAdRJIuAAAAAAAAAAARIsg6dsAAABIicdIjUwkDkiNdCQPSInFTI2wMAsAAEi4AAAAAAAAAABMifL/0EGJxIXAD4WMAAAATI1EJA5MifFIjVQkD0yJ7ki4AAAAAAAAAABIie//0EGJxIXAdWaAfCQOAXQxSLgAAAAAAAAAAEiJ7//QvwQAAAAxwEi AAAAAAAAAABIugAAAAAAAAAA/9JBicTrTEiLVCQPSIuNMAsAAEiNdCQgSInvSLgAAAAAAAAAAEiJlTgLAAD/0EGJxIXAdBFIuAAAAAAAAAAASInv/9DrDUiLRCQwSIlrUEiJQ0BIgcTAAAAARIngW11BXEFdQV7D8w8e ki4AAAAAAAAAABBV0FWSYn2QVVBVFVTSIHsOAEAAEiJVCQISIlMJBD/0EiFwHUOoQAAAAAAAAAA6UkDAABIicVIjUwkJ0iNVCQ4SInHSLgAAAAAAAAAAEiNdCRW/9CFwA FlAAAAEyNRCQnSI1MJDhMifZIie9IuAAAAAAAAAAASI1UJFb/0IXAdW AfCQnAnQxSLgAAAAAAAAAAEiJ7//QvwQAAAAxwEi AAAAAAAAAABIugAAAAAAAAAA/9LpwwIAAEi4AAAAAAAAAABqAEiJ70yNdCRIQVZIi0wkSEyNTCRATI1EJDhIjVQkd0iNdCRm/9BaWYXAdByJRCQISInvSLoAAAAAAAAAAP/Si0QkCOlwAgAAgHwkb1R1DEiLRCRWSDlEJGd0MEyNRCRnSI1MJDBMifZIie9IjVQkKEUx7Ui4AAAAAAAAAAD/0EGJxIXAfwjpAwIAAEUx5EUx7THbgHwkb1QPhe0BAABIi0QkVkg5RCRnD4XdAQAASItEJDBIOdh2NkiNHABMie9IuAAAAAAAAAAA/9BIjXsBSLgAAAAAAAAAAP/QSYnFSIXAdQuhAAAAAAAAAADrI0UxwEiLTCQwSIt0JChMiepIuAAAAAAAAAAASInv/9CFwHQK99hBicTpcwEAAE2F7Q E9gAAAEEPt1UbQQ 3RRlIjUQCHkg5ww D9gAAAOnZAAAASItMJDhJixZIjbQkkAAAAEiJ70H/17oYAAAAMfZIjXwkeIlEJBxIuAAAAAAAAAAA/9CLTCQchckPhMIAAABIuAAAAAAAAAAAxwAAAAAAQQ 3RhtJjX4eSI10JHhBikwGHkHGRAYeAIpEJHhBgH4dAg UwohMJByD4P4J0EiLVCQQiEQkeEiLRCQI/9CFwA FuQAAAEEPt1YbikwkHEiJ0EGITBYeQQ 3VhlMjUQCHk NdAUATInwTCnoSDtEJDB9WUEPt1YbQQ 3RhlIjUQCHkg5ww DJ////0i4AAAAAAAAAABBvPX////HAAsAAADrXEm/AAAAAAAAAABNie7rtEiLhCQYAQAAgEwkeAJIiYQkgAAAAOk0////TI1EJGdIjUwkMEiJ70i4AAAAAAAAAABIjVQkKEiNdCRA/9BBicSFwA PCv7// sDRTHkSLsAAAAAAAAAAEyJ7//TSIt8JEj/00iJ70i4AAAAAAAAAAD/0ESJ4PfYSIHEOAEAAFtdQVxBXUFeQV/D8w8e ki AAAAAAAAAABIvwAAAAAAAAAASLgAAAAAAAAAAP/g8w8e ki/AAAAAAAAAABIuAAAAAAAAAAA/ DzDx76oQAAAAAAAAAAVUmJ8EGJ0Um6AAAAAAAAAABThcB0CIn4MdL30OtnTYnTMfa7AQAAAInyMcC5BwAAAPbCAXQGid3T5Qno0eqD6QFz7sHgGLoIAAAAjQwAwfgfJUFv3B4xyP/Kde 5HwAAAKgBdAaJ3dPlCerR6IPpAXPv/8ZBiRNJg8MEgf4AAQAAdaXrkUE50X4XicFBMgQQSP/CD7bAwekIQTMMgonI6 T30FtdwwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAIAAAAAAAAAACAAAAAAAAAAAAACAABmYWlsZWQgYWxsb2NhdGUgYSB6c3RkIGJ1ZmZlcgBmYWlsZWQgdG8gY3JlYXRlIGEgenN0ZCBjb250ZXh0AHpzdGQgZGF0YSBjb3JydXB0ZWQAc3RyaXBlICVseCBtYXBzIHRvIDB4JWx4CnJlYWRpbmcgcGFkZHIgMHglbHgKAGJ0cmZzAGZzL2J0cmZzLmMAY291bGRuJ3QgZmluZCBhIG5lY2Vzc2FyeSBtZW1iZXIgZGV2aWNlIG9mIG11bHRpLWRldmljZSBmaWxlc3lzdGVtCgBidHJmc19oZWFkZXIuYnl0ZW5yIGlzIG5vdCBlcXVhbCBub2RlIGFkZHIKAGhlYWRlciBieXRlbnIgaXMgbm90IGVxdWFsIG5vZGUgYWRkcgBidHJmc19oZWFkZXIudXVpZCBkb2Vzbid0IG1hdGNoIHNibG9jayB1dWlkCgBoZWFkZXIgdXVpZCBkb2Vzbid0IG1hdGNoIHNibG9jayB1dWlkAF9CSFJmU19NAG5vdCBhIEJ0cmZzIGZpbGVzeXN0ZW0Abm90IEJ0ckZTACUwNHglMDR4LSUwNHgtJTA0eC0lMDR4LSUwNHglMDR4JTA0eAB0b28gZGVlcCBidHJmcyB2aXJ0dWFsIG5lc3RpbmcAcmV0cmlldmluZyAlbHggJXggJWx4CgBpbnRlcm5hbCBub2RlIChkZXB0aCAlZCkgJWx4ICV4ICVseAoAbGVhZiAoZGVwdGggJWQpICVseCAleCAlbHgKAHNlYXJjaGluZyBmb3IgbGFkZHIgJWx4CgAlbHggJWx4IAoAY291bGRuJ3QgZmluZCB0aGUgY2h1bmsgZGVzY3JpcHRvcgB6ZXJvLXNpemUgY2h1bmsKAGdvdCBhbiBpbnZhbGlkIHplcm8tc2l6ZSBjaHVuawBjaHVuay1zaXplIHRvbyBzbWFsbAoAZ290IGFuIGludmFsaWQgY2h1bmsgc2l6ZQBubyBjaHVuawoAY2h1bmsgMHglbHgrMHglbHggKCVkIHN0cmlwZXMgKCVkIHN1YnN0cmlwZXMpIG9mICVseCkKAHNpbmdsZQoAaW52YWxpZCBSQUlEX1NJTkdMRTogbnN0cmlwZXMgIT0gMSAoJXUpCgBpbnZhbGlkIFJBSURfU0lOR0xFOiBuc3RyaXBlcyAhPSAxICgldSkAUkFJRDEgKGNvcGllczogJWQpCgBpbnZhbGlkIFJBSUQxOiBuc3RyaXBlcyAhPSAldSAoJXUpCgBpbnZhbGlkIFJBSUQxOiBuc3RyaXBlcyAhPSAldSAoJXUpAFJBSUQwCgBpbnZhbGlkIFJBSUQxMDogbnN1YnN0cmlwZXMgIT0gMiAoJXUpAFJBSUQ1CgBSQUlENgoAaW52YWxpZCBSQUlENS82OiBucGFyaXRpZXMgPj0gbnN0cmlwZXMAdW5zdXBwb3J0ZWQgUkFJRAoAdW5zdXBwb3J0ZWQgUkFJRCBmbGFncyAlbHgAcmVhZGluZyBsYWRkciAweCVseAoAcmVhZGluZyBwYWRkciAlbHggZnJvbSBzdHJpcGUgSUQgJWx4CgBzdHJpcGUgJWx1IEZBSUxFRCAoZGV2IElEICVseCkKAHN0cmlwZSAlbHUgT0sgKGRldiBJRCAlbHgpCgBzdHJpcGUgJWx1IFJFQUQgRkFJTEVEIChkZXYgSUQgJWx4KQoAbm90IGVub3VnaCBkaXNrcyBmb3IgUkFJRCA1OiB0b3RhbCAlbHUsIG1pc3NpbmcgJWx1CgBub3QgZW5vdWdoIGRpc2tzIGZvciBSQUlEIDY6IHRvdGFsICVsdSwgbWlzc2luZyAlbHUKAGVub3VnaCBkaXNrcyBmb3IgUkFJRCA1OiB0b3RhbCAlbHUsIG1pc3NpbmcgJWx1CgBjYWxsZWQgcmVidWlsZF9yYWlkNSgpLCBidXQgYWxsIGRpc2tzIGFyZSBPSwoAcmVidWlsZGluZyBSQUlEIDUgc3RyaXBlICMlbHUKAG5vIHJvb3QAaW5vZGUgbm90IGZvdW5kAGV4dGVudCBub3QgZm91bmQAZXh0ZW50IGRlc2NyaXB0b3IgaXMgdG9vIHNob3J0AHJlZ3VsYXIgZXh0ZW50IDB4JWx4KzB4JWx4CgBlbmNyeXB0aW9uIG5vdCBzdXBwb3J0ZWQAY29tcHJlc3Npb24gdHlwZSAweCV4IG5vdCBzdXBwb3J0ZWQAZW5jb2Rpbmcgbm90IHN1cHBvcnRlZABwcmVtYXR1cmUgZW5kIG9mIGNvbXByZXNzZWQAdW5zdXBwb3J0ZWQgZXh0ZW50IHR5cGUgMHgleABub3QgYSBkaXJlY3RvcnkAZmlsZSBgJXMnIG5vdCBmb3VuZAB0b28gZGVlcCBuZXN0aW5nIG9mIHN5bWxpbmtzAHVucmVjb2duaXNlZCBvYmplY3QgdHlwZSAweCV4AG5vdCBhIHJlZ3VsYXIgZmlsZQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABMSUNFTlNFPUdQTHYzKwAAZ3ppbwBsem9waW8AcmFpZDZyZWMAenN0ZABidHJmcwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwACAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAFAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAGAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAJAAAAAAAAAAAAAAAAAAAAAAABAAAAAgACABgzAAAAAAAAJAAAAAAAAAAPAAAAAgACADwzAAAAAAAAGgAAAAAAAAAdAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAApAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAA/AAAAEAAAAAAAAAAAAAAAAAAAAAAAAABMAAAAEAAAAAAAAAAAAAAAAAAAAAAAAABbAAAAEAAAAAAAAAAAAAAAAAAAAAAAAABoAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAB1AAAAEAAAAAAAAAAAAAAAAAAAAAAAAACGAAAAEAAAAAAAAAAAAAAAAAAAAAAAAACjAAAAEAAAAAAAAAAAAAAAAAAAAAAAAACvAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAC9AAAAEAAAAAAAAAAAAAAAAAAAAAAAAADWAAAAEAAAAAAAAAAAAAAAAAAAAAAAAADlAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAD8AAAAEAAAAAAAAAAAAAAAAAAAAAAAAAAKAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAAVAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAAhAQAAEgACAFYzAAAAAAAAswAAAAAAAAAwAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAA9AQAAEAAAAAAAAAAAAAAAAAAAAAAAAABOAQAAEAAAAAAAAAAAAAAAAAAAAAAAAABaAQAAEAAAAAAAAAAAAAAAAAAAAAAAAABmAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAByAQAAEAAAAAAAAAAAAAAAAAAAAAAAAACEAQAAEAAAAAAAAAAAAAAAAAAAAAAAAACQAQAAEAAAAAAAAAAAAAAAAAAAAAAAAACiAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAC2AQAAEAAAAAAAAAAAAAAAAAAAAAAAAADBAQAAEAAAAAAAAAAAAAAAAAAAAAAAAADSAQAAEAAAAAAAAAAAAAAAAAAAAAAAAADcAQAAEAAAAAAAAAAAAAAAAAAAAAAAAADpAQAAEAAAAAAAAAAAAAAAAAAAAAAAAAD9AQAAEAAAAAAAAAAAAAAAAAAAAAAAAAASAgAAEAAAAAAAAAAAAAAAAAAAAAAAAAAhAgAAEAAAAAAAAAAAAAAAAAAAAAAAAAAAZ3J1Yl9tb2RfaW5pdABncnViX21vZF9maW5pAGdydWJfc3RybGVuAGx6bzF4X2RlY29tcHJlc3Nfc2FmZQBaU1REX2lzRXJyb3IAZ3J1Yl94YXNwcmludGYAZ3J1Yl9yZWFsbG9jAGdydWJfbWVtbW92ZQBncnViX2RldmljZV9vcGVuAFpTVERfZmluZEZyYW1lQ29tcHJlc3NlZFNpemUAZ3J1Yl9zdHJkdXAAZ3J1Yl9kaXZtb2Q2NABaU1REX2NyZWF0ZURDdHhfYWR2YW5jZWQAZ3J1Yl9kaXNrX3JlYWQAZ3J1Yl9yYWlkNl9yZWNvdmVyX2dlbgBaU1REX2ZyZWVEQ3R4AGdydWJfZXJybm8AZ3J1Yl9tZW1zZXQAZ3J1Yl9nZXRjcmMzMmMAZ3J1Yl9mc19saXN0AGdydWJfcHJpbnRfZXJyb3IAZ3J1Yl96YWxsb2MAZ3J1Yl9zdHJjaHIAZ3J1Yl9tYWxsb2MAZ3J1Yl9yZWFsX2RwcmludGYAZ3J1Yl9jYWxsb2MAZ3J1Yl9kZXZpY2VfY2xvc2UAWlNURF9kZWNvbXByZXNzREN0eABncnViX2Vycm9yAGdydWJfbGlzdF9yZW1vdmUAZ3J1Yl9mcmVlAGdydWJfc3RybmR1cABncnViX2RldmljZV9pdGVyYXRlAGdydWJfemxpYl9kZWNvbXByZXNzAGdydWJfbGlzdF9wdXNoAGdydWJfbWVtY21wAAAAAAYAAAAAAAAAAQAAACQAAAAAAAAAAAAAABkAAAAAAAAAAQAAAB0AAAAAAAAAAAAAAC4AAAAAAAAAAQAAACAAAAAAAAAAAAAAAGcAAAAAAAAAAQAAACQAAAAAAAAAAAAAAJEAAAAAAAAAAQAAAAEAAAAmAAAAAAAAAOUAAAAAAAAAAQAAAAwAAAAAAAAAAAAAAPYAAAAAAAAAAQAAABYAAAAAAAAAAAAAAF8BAAAAAAAAAQAAAB0AAAAAAAAAAAAAAIABAAAAAAAAAQAAAAMAAAAAAAAAAAAAAJMBAAAAAAAAAQAAACIAAAAAAAAAAAAAALwBAAAAAAAAAQAAAAEAAAATAAAAAAAAAMsBAAAAAAAAAQAAAAEAAAAAAAAAAAAAANoBAAAAAAAAAQAAABIAAAAAAAAAAAAAAAoCAAAAAAAAAQAAAAMAAAAeAAAAAAAAABkCAAAAAAAAAQAAACIAAAAAAAAAAAAAADsCAAAAAAAAAQAAAA8AAAAAAAAAAAAAAEcCAAAAAAAAAQAAAAoAAAAAAAAAAAAAAHMCAAAAAAAAAQAAACEAAAAAAAAAAAAAAIkCAAAAAAAAAQAAAAMAAAA AAAAAAAAAKkCAAAAAAAAAQAAAA0AAAAAAAAAAAAAALgCAAAAAAAAAQAAACQAAAAAAAAAAAAAAMoCAAAAAAAAAQAAABUAAAAAAAAAAAAAADgDAAAAAAAAAQAAAAEAAADsCAAAAAAAAEcDAAAAAAAAAQAAACYAAAAAAAAAAAAAAJADAAAAAAAAAQAAAAwAAAAAAAAAAAAAAMMDAAAAAAAAAQAAACAAAAAAAAAAAAAAAAwEAAAAAAAAAQAAAB4AAAAAAAAAAAAAAB8EAAAAAAAAAQAAAAMAAACGAAAAAAAAADYEAAAAAAAAAQAAAAMAAACAAAAAAAAAAFgEAAAAAAAAAQAAAAMAAABSAAAAAAAAAGwEAAAAAAAAAQAAAAEAAADmAgAAAAAAAKAEAAAAAAAAAQAAABMAAAAAAAAAAAAAALIEAAAAAAAAAQAAAAMAAACAAAAAAAAAAMMEAAAAAAAAAQAAAAMAAACRAAAAAAAAAM0EAAAAAAAAAQAAAAMAAACGAAAAAAAAANoEAAAAAAAAAQAAABYAAAAAAAAAAAAAAEoFAAAAAAAAAQAAAAMAAADVAAAAAAAAAFQFAAAAAAAAAQAAAAMAAACAAAAAAAAAAF4FAAAAAAAAAQAAAAMAAACGAAAAAAAAAGgFAAAAAAAAAQAAAB4AAAAAAAAAAAAAAHUFAAAAAAAAAQAAAAMAAAABAQAAAAAAAI4FAAAAAAAAAQAAACkAAAAAAAAAAAAAAKUFAAAAAAAAAQAAAAMAAAAmAQAAAAAAAK8FAAAAAAAAAQAAAAMAAACAAAAAAAAAALkFAAAAAAAAAQAAAAMAAACGAAAAAAAAAMMFAAAAAAAAAQAAAB4AAAAAAAAAAAAAANAFAAAAAAAAAQAAAAMAAABTAQAAAAAAAOIFAAAAAAAAAQAAACIAAAAAAAAAAAAAAPYFAAAAAAAAAQAAABMAAAAAAAAAAAAAAA0GAAAAAAAAAQAAAAIAAAAAAAAAAAAAAEkGAAAAAAAAAQAAAAMAAAB5AQAAAAAAAFMGAAAAAAAAAQAAACkAAAAAAAAAAAAAAH8GAAAAAAAAAQAAAA0AAAAAAAAAAAAAALsGAAAAAAAAAQAAAAMAAACCAQAAAAAAAMwGAAAAAAAAAQAAACIAAAAAAAAAAAAAAOMGAAAAAAAAAQAAABYAAAAAAAAAAAAAABoHAAAAAAAAAQAAAAMAAACZAQAAAAAAACsHAAAAAAAAAQAAACIAAAAAAAAAAAAAADwHAAAAAAAAAQAAABsAAAAAAAAAAAAAAF4HAAAAAAAAAQAAAAEAAADuBQAAAAAAAH0HAAAAAAAAAQAAAB0AAAAAAAAAAAAAAJUHAAAAAAAAAQAAACQAAAAAAAAAAAAAAMsHAAAAAAAAAQAAAAEAAAAJBwAAAAAAANcHAAAAAAAAAQAAABYAAAAAAAAAAAAAAAUIAAAAAAAAAQAAAAMAAACjAQAAAAAAABcIAAAAAAAAAQAAAAsAAAAAAAAAAAAAAHIIAAAAAAAAAQAAAAEAAAAmAAAAAAAAAI8IAAAAAAAAAQAAAAEAAAAJBwAAAAAAAJsIAAAAAAAAAQAAABYAAAAAAAAAAAAAAMcIAAAAAAAAAQAAACUAAAAAAAAAAAAAANkIAAAAAAAAAQAAAAEAAAAmAAAAAAAAAPIIAAAAAAAAAQAAAA4AAAAAAAAAAAAAACUJAAAAAAAAAQAAAAEAAADuBQAAAAAAADsJAAAAAAAAAQAAACAAAAAAAAAAAAAAAEoJAAAAAAAAAQAAABYAAAAAAAAAAAAAAGIJAAAAAAAAAQAAACAAAAAAAAAAAAAAAHEJAAAAAAAAAQAAABoAAAAAAAAAAAAAAJAJAAAAAAAAAQAAACkAAAAAAAAAAAAAAK4JAAAAAAAAAQAAACAAAAAAAAAAAAAAAOYJAAAAAAAAAQAAABYAAAAAAAAAAAAAAAYKAAAAAAAAAQAAAA0AAAAAAAAAAAAAABIKAAAAAAAAAQAAABYAAAAAAAAAAAAAAA8LAAAAAAAAAQAAAB0AAAAAAAAAAAAAADQLAAAAAAAAAQAAAAkAAAAAAAAAAAAAAEsLAAAAAAAAAQAAACQAAAAAAAAAAAAAAIILAAAAAAAAAQAAAA0AAAAAAAAAAAAAAKYLAAAAAAAAAQAAACQAAAAAAAAAAAAAANALAAAAAAAAAQAAAAkAAAAAAAAAAAAAAHUMAAAAAAAAAQAAAB8AAAAAAAAAAAAAAIkMAAAAAAAAAQAAABYAAAAAAAAAAAAAAK0MAAAAAAAAAQAAAAMAAADIAQAAAAAAALcMAAAAAAAAAQAAACIAAAAAAAAAAAAAAOIMAAAAAAAAAQAAAB4AAAAAAAAAAAAAAOwMAAAAAAAAAQAAAAMAAADnAQAAAAAAAPYMAAAAAAAAAQAAAAMAAACAAAAAAAAAAAANAAAAAAAAAQAAAAMAAACGAAAAAAAAAAoNAAAAAAAAAQAAAAEAAAD0EAAAAAAAAFwNAAAAAAAAAQAAAAEAAAA1BQAAAAAAAJcNAAAAAAAAAQAAABcAAAAAAAAAAAAAAOwNAAAAAAAAAQAAAAMAAAD AQAAAAAAAPYNAAAAAAAAAQAAAAMAAACAAAAAAAAAAAAOAAAAAAAAAQAAAAMAAACGAAAAAAAAAAoOAAAAAAAAAQAAAB4AAAAAAAAAAAAAACcOAAAAAAAAAQAAAAEAAAD5BAAAAAAAAF0OAAAAAAAAAQAAAAEAAACfAAAAAAAAALoOAAAAAAAAAQAAAAEAAACfAAAAAAAAAPcOAAAAAAAAAQAAABcAAAAAAAAAAAAAAEwPAAAAAAAAAQAAAAEAAAD0EAAAAAAAAG4PAAAAAAAAAQAAAAMAAAAjAgAAAAAAAHgPAAAAAAAAAQAAAAMAAACAAAAAAAAAAIIPAAAAAAAAAQAAAAMAAACGAAAAAAAAAIwPAAAAAAAAAQAAAB4AAAAAAAAAAAAAAKwPAAAAAAAAAQAAAAEAAAD5BAAAAAAAAMsPAAAAAAAAAQAAAA0AAAAAAAAAAAAAAEgQAAAAAAAAAQAAAA0AAAAAAAAAAAAAAK0QAAAAAAAAAQAAABcAAAAAAAAAAAAAANIQAAAAAAAAAQAAAAEAAACfAAAAAAAAAAIRAAAAAAAAAQAAAB4AAAAAAAAAAAAAAEERAAAAAAAAAQAAAAMAAAA/AgAAAAAAAEsRAAAAAAAAAQAAAAMAAACAAAAAAAAAAFURAAAAAAAAAQAAAAMAAACGAAAAAAAAAJoRAAAAAAAAAQAAAAMAAABYAgAAAAAAAKYRAAAAAAAAAQAAAAMAAACAAAAAAAAAALURAAAAAAAAAQAAAAMAAACGAAAAAAAAAC4SAAAAAAAAAQAAAAEAAAAVDAAAAAAAAKASAAAAAAAAAQAAAAMAAACFAgAAAAAAAKoSAAAAAAAAAQAAAAMAAACAAAAAAAAAALQSAAAAAAAAAQAAAAMAAACGAAAAAAAAAMESAAAAAAAAAQAAAAMAAACWAgAAAAAAAOISAAAAAAAAAQAAAAMAAAC1AgAAAAAAAOwSAAAAAAAAAQAAAAMAAACAAAAAAAAAAPYSAAAAAAAAAQAAAAMAAACGAAAAAAAAAAMTAAAAAAAAAQAAAAMAAADLAgAAAAAAAA8TAAAAAAAAAQAAAB0AAAAAAAAAAAAAACITAAAAAAAAAQAAABYAAAAAAAAAAAAAAEETAAAAAAAAAQAAAAEAAAD0EAAAAAAAAF4TAAAAAAAAAQAAACQAAAAAAAAAAAAAANETAAAA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AQAAAAAAACAnAAAAAAAAAQAAACQAAAAAAAAAAAAAAEYnAAAAAAAAAQAAAAEAAAD0EAAAAAAAAF4nAAAAAAAAAQAAAAMAAADBBgAAAAAAAHInAAAAAAAAAQAAACIAAAAAAAAAAAAAAL0nAAAAAAAAAQAAAAEAAAC3IgAAAAAAAN4nAAAAAAAAAQAAABAAAAAAAAAAAAAAAFwoAAAAAAAAAQAAABwAAAAAAAAAAAAAAHIoAAAAAAAAAQAAAAgAAAAAAAAAAAAAAKAoAAAAAAAAAQAAACQAAAAAAAAAAAAAALkoAAAAAAAAAQAAAAMAAADeBgAAAAAAABYpAAAAAAAAAQAAAAEAAAAVDAAAAAAAAH8pAAAAAAAAAQAAABgAAAAAAAAAAAAAAK8pAAAAAAAAAQAAAAEAAAAVDAAAAAAAANIpAAAAAAAAAQAAAAEAAAD5BAAAAAAAAPIpAAAAAAAAAQAAACQAAAAAAAAAAAAAABMqAAAAAAAAAQAAAB0AAAAAAAAAAAAAADIqAAAAAAAAAQAAABYAAAAAAAAAAAAAAFEqAAAAAAAAAQAAAAEAAAD0EAAAAAAAAGoqAAAAAAAAAQAAACkAAAAAAAAAAAAAAMsqAAAAAAAAAQAAACkAAAAAAAAAAAAAAPYqAAAAAAAAAQAAACQAAAAAAAAAAAAAABQrAAAAAAAAAQAAAAMAAAACBwAAAAAAAB4rAAAAAAAAAQAAACIAAAAAAAAAAAAAAEYrAAAAAAAAAQAAACQAAAAAAAAAAAAAAFgrAAAAAAAAAQAAAAEAAAAOIgAAAAAAAIYrAAAAAAAAAQAAAAgAAAAAAAAAAAAAAJwrAAAAAAAAAQAAAB0AAAAAAAAAAAAAAOErAAAAAAAAAQAAAAEAAAC3IgAAAAAAABAsAAAAAAAAAQAAAAgAAAAAAAAAAAAAADIsAAAAAAAAAQAAAA0AAAAAAAAAAAAAAGYsAAAAAAAAAQAAAAEAAAARIQAAAAAAAKwsAAAAAAAAAQAAAAEAAAAVDAAAAAAAABAtAAAAAAAAAQAAAAEAAAD0EAAAAAAAACctAAAAAAAAAQAAACQAAAAAAAAAAAAAAHEtAAAAAAAAAQAAACQAAAAAAAAAAAAAAI8tAAAAAAAAAQAAAAMAAADuBgAAAAAAAJktAAAAAAAAAQAAACIAAAAAAAAAAAAAAOQtAAAAAAAAAQAAACQAAAAAAAAAAAAAAAYuAAAAAAAAAQAAAAMAAAAfBwAAAAAAABAuAAAAAAAAAQAAACIAAAAAAAAAAAAAACMuAAAAAAAAAQAAACQAAAAAAAAAAAAAAFQuAAAAAAAAAQAAAAEAAAAJBwAAAAAAAH4uAAAAAAAAAQAAABYAAAAAAAAAAAAAAKcuAAAAAAAAAQAAAAEAAAARIQAAAAAAANEuAAAAAAAAAQAAAAEAAADYJwAAAAAAAO4uAAAAAAAAAQAAAAEAAAAmAAAAAAAAAAQvAAAAAAAAAQAAAAMAAAA9BwAAAAAAAA4vAAAAAAAAAQAAACIAAAAAAAAAAAAAADMvAAAAAAAAAQAAAAEAAAAOIgAAAAAAAE0vAAAAAAAAAQAAAAEAAAAmAAAAAAAAAIIvAAAAAAAAAQAAAAEAAAAJBwAAAAAAALAvAAAAAAAAAQAAABYAAAAAAAAAAAAAAM8vAAAAAAAAAQAAAAEAAAARIQAAAAAAAPgvAAAAAAAAAQAAAAEAAADYJwAAAAAAABQwAAAAAAAAAQAAAAEAAAAmAAAAAAAAACowAAAAAAAAAQAAAAMAAADeBgAAAAAAADQwAAAAAAAAAQAAACIAAAAAAAAAAAAAAEUwAAAAAAAAAQAAAAEAAAAVDAAAAAAAAIMwAAAAAAAAAQAAAAEAAAAmAAAAAAAAAMMwAAAAAAAAAQAAAAEAAACYHwAAAAAAAA8xAAAAAAAAAQAAACQAAAAAAAAAAAAAAB8xAAAAAAAAAQAAAB0AAAAAAAAAAAAAADIxAAAAAAAAAQAAABYAAAAAAAAAAAAAAE4xAAAAAAAAAQAAAAEAAAD0EAAAAAAAALcxAAAAAAAAAQAAABcAAAAAAAAAAAAAAM8xAAAAAAAAAQAAABYAAAAAAAAAAAAAAGoyAAAAAAAAAQAAABYAAAAAAAAAAAAAAIIyAAAAAAAAAQAAAAEAAAAOIgAAAAAAALgyAAAAAAAAAQAAAAEAAACYHwAAAAAAAN4yAAAAAAAAAQAAACQAAAAAAAAAAAAAAPcyAAAAAAAAAQAAAAEAAAAmAAAAAAAAAB4zAAAAAAAAAQAAAAQAAAAAAAAAAAAAACgzAAAAAAAAAQAAABkAAAAAAAAAAAAAADIzAAAAAAAAAQAAACgAAAAAAAAAAAAAAEIzAAAAAAAAAQAAAAQAAAAAAAAAAAAAAEwzAAAAAAAAAQAAACMAAAAAAAAAAAAAAFszAAAAAAAAAQAAAAUAAAAEAAAAAAAAAGwzAAAAAAAAAQAAAAUAAAAAAAAAAAAAABAAAAAAAAAAAQAAAAMAAACAAAAAAAAAABgAAAAAAAAAAQAAAAEAAAB8LwAAAAAAACAAAAAAAAAAAQAAAAEAAABOLgAAAAAAACgAAAAAAAAAAQAAAAEAAACpJwAAAAAAADAAAAAAAAAAAQAAAAEAAACGAAAAAAAAADgAAAAAAAAAAQAAAAEAAACJCAAAAAAAAEAAAAAAAAAAAQAAAAEAAADFBwAAAAAAAAAuc3ltdGFiAC5zdHJ0YWIALnNoc3RydGFiAC5ub3RlLmdudS5wcm9wZXJ0eQAucmVsYS50ZXh0AC5yb2RhdGEALnJvZGF0YS5zdHIxLjEALnJlbGEuZGF0YQAubW9kdWxlX2xpY2Vuc2UALmJzcwAubW9kZGVwcwAubW9kbmFtZQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGwAAAAcAAAACAAAAAAAAAAAAAAAAAAAAQAAAAAAAAAAgAAAAAAAAAAAAAAAAAAAACAAAAAAAAAAAAAAAAAAAADMAAAABAAAABgAAAAAAAAAAAAAAAAAAAGAAAAAAAAAACTQAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAAuAAAABAAAAEAAAAAAAAAAAAAAAAAAAACgQgAAAAAAANAgAAAAAAAADAAAAAIAAAAIAAAAAAAAABgAAAAAAAAAOQAAAAEAAAACAAAAAAAAAAAAAAAAAAAAgDQAAAAAAAAgAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAEEAAAABAAAAMgAAAAAAAAAAAAAAAAAAAKA0AAAAAAAAUAcAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAQAAAAAAAABVAAAAAQAAAAMAAAAAAAAAAAAAAAAAAAAAPAAAAAAAAFAAAAAAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAAAAAAAAUAAAAAQAAABAAAAAAAAAAAAAAAAAAAAAcGMAAAAAAACoAAAAAAAAAAwAAAAGAAAACAAAAAAAAAAYAAAAAAAAAFsAAAABAAAAAwAAAAAAAAAAAAAAAAAAAFA8AAAAAAAADwAAAAAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAAAAAAABrAAAACAAAAAMAAAAAAAAAAAAAAAAAAABgPAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAAAAAAAAcAAAAAEAAAAAAAAAAAAAAAAAAAAAAAAAYDwAAAAAAAAaAAAAAAAAAAAAAAAAAAAAAQAAAAAAAAAAAAAAAAAAAHkAAAABAAAAAAAAAAAAAAAAAAAAAAAAAHo8AAAAAAAABgAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAABAAAAAgAAAAAAAAAAAAAAAAAAAAAAAACAPAAAAAAAAPADAAAAAAAADQAAAAgAAAAIAAAAAAAAABgAAAAAAAAACQAAAAMAAAAAAAAAAAAAAAAAAAAAAAAAcEAAAAAAAAAtAgAAAAAAAAAAAAAAAAAAAQAAAAAAAAAAAAAAAAAAABEAAAADAAAAAAAAAAAAAAAAAAAAAAAAABhkAAAAAAAAggAAAAAAAAAAAAAAAAAAAAEAAAAAAAAAAAAAAAAAAAA=[/IMG]btrfs.mod, so you may need that to boot from Ubuntu's grub. Even if you do not plan to use Ubuntu's grub, probably worthwhile to configure it, so a major grub update that reset Ubuntu to first in boot order, still lets you boot other installs.

---

