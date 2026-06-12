---
title: "Manual Full System Encryption has been updated and simplified"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2018-08-21
I have updated the documentation for [Manual Full System Encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), and vastly simplified it in the process.

For those who don't know, this allows you to encrypt everything including [FONT=lucida console]/boot[/FONT], excluding the EFI System Partition for obvious reasons, and it plays nicely with other systems, e.g. Windows.

If you choose to try it, please let me know (in this thread) if it works for you and if you find any bugs in the documentation or the process.

Whether or not it works, it would be helpful to know which flavour and version you use.

Please **read the warnings and caveats** before deciding whether or not to use it. Ignoring them could leave you disappointed.

If you like it, and want Canonical to officially implement it or something like it in the Installer, please [support the request]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457") (log in and select the green writing at the top left).

Thank you :)

**EDIT:** Jernej Jakob has created instructions to [convert an unencrypted installation to an encrypted one]("https://github.com/jjakob/wiki/wiki/Migrating-an-unencrypted-PureOS-Debian-install-to-fully-encrypted"). I have not tested it, but Jernej says that it works on Ubuntu.

**EDIT:** Tj has created an [alternative how-to]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019") that might supersede this method (I haven't tested it, but it looks good).

---

### Post by DuckHook on 2018-08-21
Wow Paddy,

You put a ton of work into this. Thank you.

---

### Post by tpa76000 on 2018-08-22
Hi Paddy,

Congratulations for such a huge work! You help us so much.

Just want to submit a (little) bug on your script. Modern laptops (SSD with PCIExpress) have their partitions named /dev/nvme* (and not /dev/sd* anymore).

I think you should only require "/dev/" on your prompt, and not "/dev/sd"

Thanks again for all this work!
Paul

---

### Post by Paddy Landau on 2018-08-22
Thanks for the report, Paul. I had thought that Ubuntu was fixed in the matter, but clearly I had thought wrong!

Would the equivalent of, say, [FONT=courier new]/dev/sda2[/FONT] be [FONT=courier new]/dev/nmvea2[/FONT]? I need to be clear on the syntax for error-checking.

---

### Post by shelln00b on 2018-08-22
The guide explains how to encrypt the boot partition, but EFI is still  unencrypted and it looks like there's no difference in pwning the OS, as  explained at [https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/](https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/): instead of working on /boot beacuse it's encrypted, work on EFI to maliciously changing it, right?

You  commented there confirming that EFI should be signed to prevent this.  Is this the final solution to prevent this type of attacks? How about  other Distro that have not a signed bootloader to enforce Secure Boot,  like Debian?
(I know this forum is for Ubuntu only, but I will apreciate any help, especially beacuse this is the only guide on the topic.)

A big thanks for your work,
shelln00b

---

### Post by j.folwer on 2018-08-22
> **shelln00b said:**
> The guide explains how to encrypt the boot partition, but EFI is still  unencrypted and it looks like there's no difference in pwning the OS, as  explained at [https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/](https://twopointfouristan.wordpress.com/2011/04/17/pwning-past-whole-disk-encryption/): instead of working on /boot beacuse it's encrypted, work on EFI to maliciously changing it, right?

You  commented there confirming that EFI should be signed to prevent this.  Is this the final solution to prevent this type of attacks? How about  other Distro that have not a signed bootloader to enforce Secure Boot,  like Debian?

The EFI partition must be left unencrypted and it's used for other systems too. The efi is protected by SecureBoot: That is, every boot loader is signed and verified by the UEFI boot process before being launched. Also, each bootloader verifies in turn the files it loads in something like a "chain of trust" where each additional piece (boot loader -> kernel -> initramfs) is verified by the previous piece.

Now, the keys used to verify each piece come from various places. There's a built-in key from Microsoft in all new computers. There's also a secondary key, still owned by Microsoft, but which is used to sign third party loaders. 

The common way of booting linux on a secureboot system is using the shim bootloader, which loads grub2 (verifying that it has been signed itself). In ubuntu, the installer will create and "enroll" what is known as MOK (machine owner keys). These keys can be generated and verified by the computer owner and once installed they can be used to sign bootloaders, kernels and, more importantly, third part drivers (like nvidia) which would never be available without (i.e. you cannot install a third party driver and load it into the kernel if it's not signed).

Speaking of which, I'm still having issues booting my full disk encrypted dual-booting (Win+Ubuntu) notebook when I enable secureboot enforcing in the bios. This means somewhere in the chain of command something is not properly signed and it just won't boot. If I disable the secureboot eforcement, everything is OK and ubuntu boots.

The whole point of signing the efi binaries (and rest) is to prevent that somebody can modify the efi and trick the owner into typing their password in a keylogger.

---

### Post by j.folwer on 2018-08-22
> **Paddy Landau said:**
> Thanks for the report, Paul. I had thought that Ubuntu was fixed in the matter, but clearly I had thought wrong!

Would the equivalent of, say, [FONT=courier new]/dev/sda2[/FONT] be [FONT=courier new]/dev/nmvea2[/FONT]? I need to be clear on the syntax for error-checking.

I can answer that. The naming scheme is a little more complex. The tipical disk is named /dev/nvmeXnYpZ where eX is the nvme channel (supposedly) starting from 0, nY is the number of nvme disk on that channel and pZ is the partition. Nvme channel start at 0 and disk and partition both start at 1 (that is the first nvme disk is /dev/nvme0n1 and the first partition is /dev/nvme0n1p1). My EFI partition is /dev/nvme0n1p1 (not sure if efi is fixed by some agreed standard or not).

---

### Post by Paddy Landau on 2018-08-23
> **shelln00b said:**
> The guide explains how to encrypt the boot partition, but EFI is still  unencrypted…
> **j.folwer said:**
> The EFI partition must be left unencrypted…
@j.fowler, thank you for answering the question far more competently than I could have! I'm not terribly technically au fait, having put together the process through sheer dogged persistence and plenty of help from others.

> **j.folwer said:**
> I can answer that…
Thank you. I shall change the process to be as flexible as possible. It will, unfortunately, remove some of the robustness, which I had wanted for the newcomers, but that's the price we pay for lack of standards, I suppose.

I'll update this thread once I have succeeded; today, I hope, but cannot promise.

---

### Post by Paddy Landau on 2018-08-23
I have updated the process and the documentation to allow for other naming conventions, so if you use (say) [FONT=lucida console]/dev/nvme0[/FONT]…, you can use it.

The change was good, because it has also made the scripts more robust against errors.

Thank you for your behind-the-scenes help and for your patience.

---

### Post by j.folwer on 2018-08-25
> **Paddy Landau said:**
> I have updated the process and the documentation to allow for other naming conventions, so if you use (say) [FONT=lucida console]/dev/nvme0[/FONT]&#8230;, you can use it.
The change was good, because it has also made the scripts more robust against errors.
Thank you for your behind-the-scenes help and for your patience.

I apologize, I stand corrected. I wrote the disk details from memory, but memory is not good as it used to be. I've updated my post with the nvme numbering, and precisely: "The tipical disk is named /dev/nvmeXnYpZ where eX is the nvme channel  (supposedly) starting from 0, nY is the number of nvme disk on that  channel and pZ is the partition". BTW, I see you caught that mistake ;)

j.fowler

PS: I'm now digging in the details of shim loading / mok signing and grub signing it's own config and modules via openpgp. I found some documents about signing initrd and grub.cfg with opengpg keys (not mok keys) and perhaps enabling custom keys in the secureboot env, which could enable us to have the boot unencrypted but still signed and checked, in case unlocking boot/lvm with cryptomount is not a viable option. I was really hoping not to have to read shim's and grub's source code and hoping to understand how to debug the key validation, and why GRUB_CRYPTED_DISK=y loads cryptomount module only with secureboot disabled. No eta on that tough.

---

### Post by Paddy Landau on 2018-08-25
> **j.folwer said:**
> I apologize, I stand corrected…
No problem. Thanks to your previous comments, I discovered that VirtualBox allows me to create a NVMe controller, which let me see how it worked. So it was all good — I learned something (always good to do); and I made the script both more robust and more flexible.

> **j.folwer said:**
> … which could enable us to have the boot unencrypted but still signed and checked…
That's not necessary, because the full-system encryption includes /boot within LVM, which is in turn within LUKS. It all works. The important point is the next one that you make:

> **j.folwer said:**
> I was really hoping not to have to read shim's and grub's source code and hoping to understand how to debug the key validation, and why GRUB_CRYPTED_DISK=y loads cryptomount module only with secureboot disabled. No eta on that tough.
That's the big one. We need to have proper signing on the EFI System Partition, because that's the only vector for malware on a locked machine. Unfortunately, it is way beyond my level of competence to even comment on how.

I refer you to the bug's [comment #25]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457/comments/25") by Jonathan Polom, who explains a bit more about the signing flaw. I'd love to raise a bug report for this shortcoming, but I have insufficient knowledge to even begin to frame the report.

---

### Post by flyffies on 2018-08-27
Hi,

I tried to install Ubuntu with the tutorial on a portable usb drive I could use on my travels, so I am not bound to any hardware other than the drive. 

I ran into the issue that on boot the drive definitions could change, and if they do the system is unable to find the excrypted partition and decrypt it. 

Has anyone a solution to this or could think of any? What I found and tried didn't work sadly...

Big thank you in advance

---

### Post by Paddy Landau on 2018-08-28
> **flyffies said:**
> I tried to install Ubuntu with the tutorial on a portable usb drive I could use on my travels, so I am not bound to any hardware other than the drive.
The first thing to check is that you used the portable drive, not the internal drive, as your bootloader. So, after your installation, what you should have is:
[LIST]
[*]Your internal hard drive, which is probably /dev/sda, containing its ESP (EFI System Partition) and its own bootloader.
[*]Your external portable USB drive, probably /dev/sdb, which contains its own ESP, and its own bootloader.
[/LIST]
So, you should have a situation where each drive is completely independent of each other. The internal hard drive's setup should be blissfully unaware of the external drive's ESP and system. The external drive will know about the internal drive, but you can safely ignore that — the important thing is that it has its own ESP and its own bootloader.

I hope that I've explained myself clearly.

I emphasise that I actually haven't tested this, because my hardware is a bit old and clunky, but if you still have problems with this, I'll test it myself anyway.

Let us know if you've already done this, or if not, what happens if you try it. It "should" work because the drive access is via the UUID rather than the symbolic /dev/sdb; the former won't change, but the latter might.

This situation didn't occur to me previously, so I should add this into the documentation. Let's wait until you get it working, though.

---

### Post by flyffies on 2018-08-29
Hi, 

thanks for the response.

Yea, I installed the bootloader onto the external drive (in my case /dev/sdc, the install usb-stick took /dev/sdb, internal /dev/sda) it worked on the first reboot, where I didn't change anything.
On the second reboot I remove the usb-stick and still grub could not find the correct partition to decrypt. I could choose ubuntu from its menu, but it wouldn't ask for the password...

I will do a clean install later and try it again, maybe I messed up somewhere else.

---

### Post by Paddy Landau on 2018-08-29
> **flyffies said:**
> I will do a clean install later and try it again, maybe I messed up somewhere else.
Yes, that sounds like a good idea.

I felt a little uncertain what exactly you were saying about the first reboot and the second reboot, sorry.

Assuming that your reinstallation again puts your external USB drive on /dev/sdc: Take great care, when you reinstall, to use no drives or partitions other than on /dev/sdc. There are two places where you note the bootloader: one, in the script in the terminal, and two, in the Installer. Please mark them both as /dev/sdc.

If the reinstallation still doesn't work, let us know and I'll run a test.

---

### Post by flyffies on 2018-08-29
So... I tested and made sure to install everything on the correct disk, my external USB Disk (Was sdb this time). 

I changed the refreshgrub script to point to the correct disk by using the /dev/disk/by-id/ link. It started, I updated the system and rebootet. And sure enought, it booted, I put in my system password and Ubuntu loaded.

After trying to install steam (and failing) and the AMD Pro drivers I tired to reboot and was unable to boot.

I could select my drive in the bios boot menu, but it didn't say ubuntu anymore as before, it was just the Drive name. 
I selected it and was only greetet by 3 lines of text:

Press F1 key to retry boot.
Press F2 key to reboot into setup.
Press F5 key to run onboard diagnostics.

I wasn't able to boot anymore. I had variations where I could see the grub menu and select ubuntu, but after entering the password it would complain, about not being able to find the partion with the specified UUID.

I really appreciate you helping me. Thanks a lot!

---

### Post by Paddy Landau on 2018-08-29
Hm, all right. That is not what I expected, but then, as I explained in the instructions, I'm not exactly a technical boffin (almost everything that I did was merely putting together what other people discovered or told me).

I'm going to test this &#8212; I might not have time until next week &#8212; and I'll get back to you in this thread.

---

### Post by em93jgm on 2018-08-29
Hi Paddy,

Thank you for the hard work!

I have solved one issue with the install that was due to my specific environment: I had a working dual boot Windows + Ubuntu 18.04 but wanted to encrypt Ubuntu. To make a back up, I cloned all my working partitions to a second drive and then followed your instructions, leaving my EFS partition alone with the windows bootloader and old ubuntu grub. When it came to booting, grub could not find the grub.cfg because it now searches for a partition UUID in EFI/ubuntu/grub.cfg. I believe grub found my cloned partition which was obviously out of date and did not have the linked grub.cfg. When I changed the clone's UUID, the system now booted ok.

My second issue is unsolved. I can boot into my fresh 18.04 installation but it takes 40 seconds to decrypt the system partition and show the login screen. Most of that time is spent with the fan running high, so I assume the CPU is in use, doing the decrypt. However, when I was debugging the system before using manual chroot from a live disk, cryptsetup open felt almost instantaneous to decrypt the partition and mount the volumes. Any idea how to figure out why it is slow? Anyone else have slow bootup? I'm on an nvme disk with recent core i7, so no hardware reason I can think of.

Cheers,

Jonathan

---

### Post by Paddy Landau on 2018-08-30
Thanks for sharing your solution, Jonathan.

> **em93jgm said:**
> &#8230; it takes 40 seconds to decrypt the system partition
I also see this (as [noted in the instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessCheckAndFinalise#System_passphrase_prompt")). Obviously, something is going on in the background &#8212; perhaps loading all sorts of startup apps, drivers and data?

I'm not entirely sure that this is a problem, because on my (unencrypted) working computer (it's too old to use the encryption process), it takes about a minute to get to the login prompt. But maybe your computer is newer and significantly faster than mine?

I'm not skilled technically. So, if you still require an answer, may I suggest that you raise a new thread in either one of the [Security]("https://ubuntuforums.org/forumdisplay.php?f=338") or [Installation and Upgrades]("https://ubuntuforums.org/forumdisplay.php?f=333") forums, and post the link here so that we can follow it? The key point to mention is this:

After entering the LUKS passphrase at the Grub prompt, the boot process takes nearly a minute to get to the login screen. Both root and /boot are held in LVM, which is in turn in a partition encrypted by LUKS. If you also have a swap partition, also mention it as being in LVM.

The question is whether or not this process can be shortened.

---

### Post by flyffies on 2018-08-30
> **Paddy Landau said:**
> Hm, all right. That is not what I expected, but then, as I explained in the instructions, I'm not exactly a technical boffin (almost everything that I did was merely putting together what other people discovered or told me).

I'm going to test this — I might not have time until next week — and I'll get back to you in this thread.

Thanks, I greatly appreciate it!

---

### Post by Paddy Landau on 2018-09-05
> **flyffies said:**
> &#8230; install everything on the correct disk, my external USB Disk &#8230; I wasn't able to boot anymore.
I've tested this, and I admit defeat.

Here is what I've managed.

[FONT=arial black]When I have a computer with something already installed on the hard drive[/FONT]

I install Ubuntu onto the USB. Thereafter, the only way that I can boot into the USB drive is to remove the hard drive (!), and even then it takes some fuss to get the USB to boot. After booting, it goes to the Ubuntu logo, and nothing more happens. However, if the hard drive is in the machine, it boots normally to the hard drive.

[FONT=arial black]When I have a blank computer to start with[/FONT]

I install Ubuntu onto the USB. This works normally.
Then, I install something else onto the hard drive, ignoring the USB.
Thereafter, if the USB is in the machine, it installs normally onto the USB, and if the USB isn't in the machine, it installs normally onto the hard drive.

So, it seems that it works if you install onto the USB drive first, and then onto the hard drive.

You might have different results, of course, depending on hardware and the specifics of your installation.

Unfortunately, at this point, my lack of technical knowledge lets me down and I cannot take this any further. I don't understand why this happens, sorry.

---

### Post by flyffies on 2018-09-06
Thank you very much for testing this.

I, also admited defeat.
I installed ubuntu with the ubuntu Installer, enabling the encryption provided by the installer. That worked, so my data on my traveling disk is (somewhat) safe, should I loose it.


I noticed the installation also doesn't showup correctly on most boots. Though it creates an EFI entry for the bootloader and then I can select that one and it works.

Maybe that is missing in the full encryption setup?

Thank you again for investigating this :)

---

### Post by Paddy Landau on 2018-09-07
> **flyffies said:**
> … it creates an EFI entry for the bootloader and then I can select that one and it works.
Specifically, which installation creates the new EFI entry — the original one on the disk or the one on your USB? I haven't been able to replicated it.

---

### Post by flyffies on 2018-09-09
The installation from the USB Drive. 

I let the Ububtu installer install Ubuntu on my external drive. I disabled the internal SATA controller so only the install stick and the 2 Tb Drive would show up and let the installer just run. I mean by that, I didn't select "Something else" when asked where to install it. 
I activated the check boxes for encryption and LVM. 

Sometimes when I boot, the ubuntu boot option is not there, only the USB drive itself. When I boot it, it shows a message about creating the efi entry and reboots. 
After that the ubuntu entry is back and I can boot without any problem. Tried it across 3 machines and it worked every time like that.

---

### Post by Paddy Landau on 2018-09-09
> **flyffies said:**
> … I didn't select "Something else" when asked where to install it.
Ah, that's something else. That's the default installer, which works fine on a blank disk. It has a couple of significant [disadvantages]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Background#The_problems"), namely that it deletes anything already on the disk (not a problem for you) and it doesn't encrypt /boot.

In other words, what you did was not the manual full system encryption discussed in this thread. So, it's useful to know if you are using a blank disk and don't care about encryption of /boot. I'm glad that you managed to sort it out, and I suspect that if you had left the SATA enabled, there is a chance that you would have had a problem.

---

### Post by flyffies on 2018-09-10
Yes, I had to have a working Ubuntu for traveling, so I settled with the default installer. Not happy with it, but the best I can currently have on my portable USB Drive, because the manual full encyption does loose the EFI entry for ubuntu, if the Drive is plugged into another pc or just another port (its very strange).

Thought the thing that the default installer does, where it creates the missing EFI entry could fix it for the manual method, but I am not experienced enough to figure that out...

I only disabled the internal SATA controller so my windows disk could not be accidentally be written to.

---

### Post by Paddy Landau on 2018-09-10
> **flyffies said:**
> Thought the thing that the default installer does, where it creates the missing EFI entry could fix it for the manual method, but I am not experienced enough to figure that out...
You're probably right, but I too have no clue how to do this.

> **flyffies said:**
> I only disabled the internal SATA controller so my windows disk could not be accidentally be written to.
That was a good idea, because the default Ubuntu installer might have wiped it. The default full-encryption option is rather poor, reminding me of the earlier Windows versions that also went ahead and wiped the entire disk without asking.

---

### Post by 3-david-o on 2018-09-13
Hi Paddy,
I appreciate all the work you've put into getting this working, and making it easy to install. Unfortunately, things arent working out for me. I'm installing on a new machine, alongside Windows 10, with secure boot enabled. Everything goes smoothly until the "Check and finalise" part. When I reboot my machine, I get the blue MOK management screen. I follow the menus to enrol the key, which all goes smoothly. Then I reboot again. I do not get the EFI screen shown in your instructions, I just get the standard Grub menu. When I select Ubuntu, I do not get prompted for a passphrase, I get the error message:

No such device: ec61b9bf-6895-43fd-84fb-c018e117e17f. 
No server is specified. 
You need to load the kernel first

  I have been through the Troubleshooting process - it didnt help. I have spent a long time trying to understand the problem. The UUID quoted is that of the boot partition inside the encrypted container. I've examined the grub.cfg file in detail. It seems to me that cryptomount is silently failing. I found that the UUID given to cryptomount doesnt have any hyphens in it. I tried adding them back in, and also using "cryptomount -a", but neither made any difference. I've tried using the grub command line to try out cryptomount manually - but it just does nothing: whatever parameters I pass to cryptomount or insmod I get a success exit status, so this gives me no clues about which commands will work successfully, and there's certainly no prompting for a passphrase.

I've gone back and done the whole installation process again, just to be sure I didnt make a mistake. Everything is exactly the same as before (though with a different UUID, obviously) (though I notice your instructions have changed a little - no more refreshGrub I see.)

I'm wondering what else I can do to troubleshoot this situation. Any ideas?

---

### Post by Paddy Landau on 2018-09-14
> **3-david-o said:**
> … When I reboot my machine, I get the blue MOK management screen.
Unfortunately, my lack of technical expertise gets in the way here. I didn't know what a MOK management screen was until I looked it up.

I wonder if this has anything to do with the [secure-boot bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532")?

I found a [troubleshooting guide]("https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS"). I have absolutely no idea whether or not it would work with you, and whether or not it would disable secure boot on your machine.

Is this a new machine? If so, it likely does adhere to standards, so that's probably not the problem.

I'm sorry that I can't be of more help; I really am clueless as to *how* the process works. I only documented what it does with extensive help from other people.

By the way, it still uses [FONT=lucida console]refreshgrub[/FONT], but it now runs automatically behind the scenes.

Can I confirm that you are using Ubuntu 18.04 64-bit, rather than one of the derivatives?

---

### Post by 3-david-o on 2018-09-17
Hi Paddy,
The MOK screen was behaving as expected (it only appears on the first boot after installing Ubuntu). Yes, its a new machine (Lenovo x380), and I'm installing Ubuntu 18.04.1.

I did some more exploring with grub and (to cut a long story short) discovered [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950"), which clearly explains that "Ubuntu cannot boot from an encrypted volume with Secure Boot enabled" because the required grub modules (luks and cryptodisk) are not included in the distributed signed grub binary, and, for security reasons, grub will not load them subsequently (so the "insmod" commands fail - though they return a success exit status nevertheless).

So, I disabled UEFI Secure Boot, and found that I now get
[INDENT]Attempting to decrypt master key...
Enter passphrase for hd0,gpt5 (1ee8a2ca...):  
[/INDENT]
 
  All well and good. Except that after I enter the passphrase, nothing happens for 60 seconds. Then I get the Ubuntu startup screen, and then after another 65 seconds, I get the Busybox ... (initramfs) screen. "Exit" then tells me: "ALERT! /dev/mapper/system-root does not exist.", and I'm taken back to the initramfs prompt again. If I then do "ls /dev/mapper", I find that the only thing listed is "control". So, it seems that the boot process hasnt completed properly and found the (unlocked?) partitions with Ubuntu on.
 
I havent yet started searching for solutions to this, but I wondered if you had come across this yourself?

---

### Post by Paddy Landau on 2018-09-18
> **3-david-o said:**
> I did some more exploring with grub and (to cut a long story short) discovered [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950")…
Thank you for the information. I have upvoted the bug, and I've now included it in the documentation.

It seems that Ubuntu has a little way to go still until the process works fully. It's a shame that it's not being taken more seriously.

If you find a solution, please let us know. In the meantime, we rely on Canonical to take this up seriously.

---

### Post by 3-david-o on 2018-09-22
Hi Paddy,
I re-ran the encrypted installation process again, this time with Secure Boot turned off at the outset. At last I have a system that works successfully! But, I still find that there is a 60 second delay after I enter my passphrase before Ubuntu begins to boot. Is this something you've observed? Do you know if there's anything I can do about it?

It's good that you've put a reference to the Secure Boot bug in your documentation. I think you should make it more explicit, though, to stop people falling into the same problem as me:
[INDENT]Warning: You must disable Secure Boot before you carry out this installation procedure. If you install with Secure Boot enabled, your computer will *not* be able to boot (due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950")). Even if you subsequently turn off secure boot, your computer will *still not boot*!
[/INDENT]

---

### Post by Paddy Landau on 2018-09-22
> **3-david-o said:**
> I still find that there is a 60 second delay…
As mentioned earlier, I suspect that what is happening is that some of the boot process is happening but being hidden behind the screen, because Grub and the kernel need to be loaded once the partition has been decrypted. I could be wrong, but I get this delay even when my computer isn't encrypted.

> **3-david-o said:**
> I think you should make it more explicit…
Good idea. I've amended the documentation accordingly. Have you visited the bug to give your support? (Log in and select the green writing near the top right.)

---

### Post by 3-david-o on 2018-09-23
Hi Paddy,
A number of people have reported long delays in decrypting LUKS containers when they need to be decrypted by Grub. The cause of this is largely explained [here]("https://unix.stackexchange.com/questions/369414/grub-takes-too-long-to-unlock-the-encrypted-boot-partition") and [here]("https://bbs.archlinux.org/viewtopic.php?id=217193"). Essentially, cryptsetup "scrambles" your passphrase before it is stored (by hashing it many times, know as iterations). (This is to guard against brute-force attempts to guess the passphrase.) This scrambling must be repeated each time your passphrase is entered and used to unlock the encrypted device. By default, cryptsetup will spend 2 seconds scrambling your passphrase when it is first created. But when booting, in a grub environment, the scrambling can take 10-20 times longer, so it may take 20-40 seconds.

On top of this, the encrypted installation uses *two* decryption keys - one for the passphrase the user enters, and one that's used by the machine in the second half of the boot process. When you enter a passphrase, it is checked against each key in turn. Guess what - the machine key is stored before the user's passphrase key, so time is wasted checking against that key, and so this doubles the delay.

Fortunately, it is easy to change the ordering of the keys (so that the user's passphrase key is checked first, not second), and to change the amount of work the machine has to do to scramble the passphrase (specified using: cryptsetup --iter-time). The basic approach is described [here]("https://unix.stackexchange.com/questions/101343/how-to-change-the-hash-spec-and-iter-time-of-an-existing-dm-crypt-luks-device"), but it isnt explained very clearly. I can provide you with more detailed instructions of how I did this if you wish.

On my machine (a Lenovo x380), I did some experiments, and found that the first boot phase (when grub is doing the work)  takes 8 seconds, plus the time taken to scramble the passphrase. The second boot phase (when grub has passed control to Ubuntu) takes 2 seconds, plus the time taken to scramble the machine key. During the second phase, the scrambling is about 20 times faster than in the first phase. I have adjusted the way my keys are stored so that only a couple of seconds are added to each of the boot phases.

There are potential security implications of reducing the amount of "scrambling" done to the passphrase, but so long as a sufficiently long/complex passphrase is used, there's no problem. This topic is well discussed [here]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects").

I think that your encryptinstallation script could easily be improved so that the key for the user's passphrase is stored *before* the machine key - which would halve the delay. It would also be fairly easy to provide users with instructions (or, better still a utility script) that allows them to easily adjust the key "scrambling" time, in case they want to reduce the time taken during boot. I'm happy to help if I can.

---

### Post by Paddy Landau on 2018-09-23
@3-david-o Thank you for all of that information. When creating the LUKS partition, the user's key is used, while the system key is added afterwards. Are you saying that this order causes Grub to try the system key first? Or something a little different?

If you can help me with an adjusted procedure, or tell me what commands you used to change the key order, I'll see if I can incorporate that into the encryption script. If it reduces the boot time, that will benefit everyone.

Thanks again.

---

### Post by archphoenix on 2018-09-23
Hello, i'm not sure I understand the purpose of the **reapplyGrubUpdates** function, is that because boot is encrypted and we have to rely entirely on efi partition to boot while we usually rely mostly on a simple efi file that delegate the rest to content in **/boot**?

If having **/boot** in a separate unencrypted[SUP]1[/SUP] partition (ideally on a removable storage), is this function still necessary?

[SIZE=1]1) Encrypted, but data made clear for current runtime before calling grub.

[SIZE=2]Your script calls **wget** to obtain other scripts from remote location, this is usually considered not secure, cannot the script be hosted on a [/SIZE][/SIZE]**g**[SIZE=1][SIZE=2]**it**[/SIZE][/SIZE][SIZE=1][SIZE=2] and have the user do one **git clone** instead of a **wget** that will call **wget** again later ? (Plus easier collaboration if someone can and want to share improvement made to your script).

Script would then **cp** to **/sbin** instead of **wget.**

Thank you for your contribution, I hope this will get popular enough to have something similar backed in officially with fancy passphrase files right into the installer's GUI.[/SIZE][/SIZE]

---

### Post by Paddy Landau on 2018-09-24
> **archphoenix said:**
> … the purpose of the **reapplyGrubUpdates** function
When any update changes the Grub or initramfs (e.g. a kernel update), Grub is incorrectly updated. This causes the next boot of the computer to fail. The script [s][FONT=lucida console]reapplyGrubUpdates[/FONT][/s] [FONT=lucida console]refreshgrub[/FONT] detects this and then automatically runs, re-updating Grub and initramfs correctly.

> **archphoenix said:**
> … is that because boot is encrypted…
Sorry, I don't have the answer to that. I'm not technically competent enough to understand why :(

> **archphoenix said:**
> If having **/boot** in a separate unencrypted[SUP]1[/SUP] partition (ideally on a removable storage), is this function still necessary?
I haven't tested what will happen if you have an unencrypted [FONT=lucida console]/boot[/FONT]. However, if [FONT=lucida console]/boot[/FONT] is encrypted, you don't need it on removable storage.

> **archphoenix said:**
> [SIZE=1][SIZE=2]Your script calls **wget** to obtain other scripts from remote location, this is usually considered not secure, cannot the script be hosted on a [/SIZE][/SIZE]**g**[SIZE=1][SIZE=2]**it**[/SIZE][/SIZE][SIZE=1][SIZE=2] and have the user do one **git clone** instead of a **wget** that will call **wget** again later ?[/SIZE][/SIZE][SIZE=1][SIZE=2]
Ah, you're the first person to answer my question of where we could host the scripts! I asked elsewhere, had no answer, so decided on Dropbox.

I have absolutely no idea how to use git. If you, or someone else, would guide my hand with this, I'd be happy to do so.

[/SIZE][/SIZE]> **archphoenix said:**
> [SIZE=1][SIZE=2]… I hope this will get popular enough to have something similar backed in officially with fancy passphrase files right into the installer's GUI.[/SIZE][/SIZE]
If you haven't already done so, please upvote the four bugs that the [instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption") list: [bug #1401532]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532"), [bug #1514120]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1514120"), [bug #1565950]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950"), and [bug #1773457]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457"). Canonical won't bother unless it is persuaded of the need.

---

### Post by archphoenix on 2018-09-24
Hello,
> [COLOR=#000000]Ah, you're the first person to answer my question of where we could host the scripts! I asked elsewhere, had no answer, so decided on Dropbox.[/COLOR]

[COLOR=#000000]I have absolutely no idea how to use git. If you, or someone else, would guide my hand with this, I'd be happy to do so.[/COLOR]
I didn't notice you asked for this, sorry.

If using fancy git hosting providers such as [github]("https://github.com/"), you have a full web GUI where you can add, remove or modify text files (script) without knowing how the git command works.
In addition, such git host would allow you to review changes proposed by other before merging them or rejecting them and you will have a modification history allowing easy reverse of problematic changes.

Since your project isn't closed source, most would probably tell you [gitlab]("https://gitlab.com/explore") public git is the best place to host your work.
As for my personal opinion, all major host works well, but you will have to dig into their documentation as they all have their own GUI take the one you feel the easiest to use for you as they're basically all free for open source projects. Most are really straightforward to use without reading the documentation as long as you interact only with the GUI.

There's also [bitbucket]("https://bitbucket.org/product"), [sourceforge]("https://sourceforge.net/p/forge/documentation/Git/") and many others I would not list.

> [COLOR=#000000]When any update changes the Grub or initramfs (e.g. a kernel update), Grub is incorrectly updated. This causes the next boot of the computer to fail. The script [/COLOR][COLOR=#000000][FONT=&quot]reapplyGrubUpdates[/FONT][/COLOR][COLOR=#000000] detects this and then automatically runs, re-updating Grub and initramfs correctly.[/COLOR]Does it happen when full disk encryption isn't used too ?

> [COLOR=#000000]I haven't tested what will happen if you have an unencrypted [/COLOR][COLOR=#000000][FONT=&quot]/boot[/FONT][/COLOR][COLOR=#000000]. However, if [/COLOR][COLOR=#000000][FONT=&quot]/boot[/FONT][/COLOR][COLOR=#000000] is encrypted, you don't need it on removable storage.[/COLOR]That's for paranoid users, required when you hold certain type of data.

> [COLOR=#000000]If you haven't already done so, please upvote the four bugs that the [/COLOR][instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption")[COLOR=#000000] list: [/COLOR][bug #1401532]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532")[COLOR=#000000], [/COLOR][bug #1514120]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1514120")[COLOR=#000000], [/COLOR][bug #1565950]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1565950")[COLOR=#000000], and [/COLOR][bug #1773457]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457")[COLOR=#000000]. Canonical won't bother unless it is persuaded of the need.[/COLOR]Have marked i'm affected, unsure if it is what you are calling upvote.

---

### Post by Paddy Landau on 2018-09-24
> **archphoenix said:**
> If using fancy git hosting providers such as [github]("https://github.com/")…
Thanks. When I have some time, I'll look at both GIT and SourceForge.

> **archphoenix said:**
> Does it happen when full disk encryption isn't used too ?
[FONT=&amp]refreshgrub[/FONT] is used with full-system encryption (the process that encrypts everything including /boot but not EFI, obviously, or any other OS on the disk). If you use the Ubuntu installer, it wipes the entire disk and uses its own method that does work, so [FONT=lucida console]refreshgrub[/FONT] isn't required. I think that that answers your question. Ask again if I misunderstood.

> **archphoenix said:**
> That's for paranoid users, required when you hold certain type of data.
Understood, although if [FONT=lucida console]/boot[/FONT] is encrypted along with the rest of the system and data, there's no need to hold it separately, because it's as safe as the data itself.

> **archphoenix said:**
> Have marked i'm affected, unsure if it is what you are calling upvote.
Thanks; your wording is correct and mine is incorrect. :)

---

### Post by 3-david-o on 2018-09-26
> **Paddy Landau said:**
>  ... When creating the LUKS partition, the user's key is used, while the system key is added afterwards. Are you saying that this order causes Grub to try the system key first? Or something a little different?

Hi Paddy,
I may have been wrong about the key order (it isnt immediately obvious which key is stored in which slot), and just jumping to conclusions.

Here are the steps that I used to ensure the keys are in the optimum order, and also to adjust the number of iterations done on each key - which influences how quickly the device can be unlocked. The steps are fairly simple and quick, but you do have to enter your passphrase *many* times!

# 1. specify your encrytped device (subtitute your device name)
[FONT=courier new]device=/dev/nvme0n1p5[/FONT]
# 2. check what's in the encyption header - note the iterations for each key
[FONT=courier new]sudo cryptsetup luksDump $device
[/FONT]# 3. create an extra passphrase as a back-stop. Enter your passphrase when prompted (3 times)
[FONT=courier new]sudo cryptsetup --key-slot 7 luksAddKey $device[/FONT]
# 4. delete existing user key slot
[FONT=courier new]sudo cryptsetup luksKillSlot $device 0
[/FONT]# 5. delete existing machine key slot
[FONT=courier new]sudo cryptsetup luksKillSlot $device 1
[/FONT]# 6. Create a new key slot for your passphrase, with required iter-time:
[FONT=courier new]sudo cryptsetup --iter-time 500 --key-slot 0 luksAddKey $device
[/FONT]# 7. Create a new key slot for the machine key,  with required iter-time:
[FONT=courier new]sudo cryptsetup --iter-time 1000 --key-slot 1 luksAddKey $device /etc/crypt.system
[/FONT]# 8. check what's in the encyption header - note the iterations for each key
[FONT=courier new]sudo cryptsetup luksDump $device
[/FONT]# 9. Reboot, and check to see how fast the startup is. 

If you'd like to reduce the boot time, repeat steps 1, 4, 6 & 8, choosing a lower value for iter-time (the iter-time is the amount of time, in milliseconds, that the encryption process spends "hashing" (scrambling) your passphrase before it is stored. It would take the same amount of time to repeat this process each time you decrypt the device - but only if your processor can operate at the same speed during boot. That's not always the case - in my case it was 10 times slower.)
You can also repeat steps 5 & 7, choosing a lower iter-time, to speed up the second part of the boot process, but this will make less of a difference.
When you've finished, you can optionally delete the "back-stop" key in slot 7 (but there's no harm in leaving it).

In my case, I found that an iter-time of 200 for my passphrase gave 185000 iterations, which took about 2 seconds during boot. For the machine key, I found that an iter-time of 1000 gave 900000 iterations, which took about 1 second during boot. The default iter-time is 2000. The relationship between iter-time and number of iterations depends on how fast your machine is. As I mentioned previously, there are potential security implications of reducing the number of iterations, but so long as a sufficiently  long/complex passphrase is used, there's no problem. This topic is well  discussed [here]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects").

I hope that the above proves to be useful for anyone suffering agonisingly long boot times.

---

### Post by Paddy Landau on 2018-09-26
Thanks, 3-david-o. That was useful information indeed.

The default iteration time for cryptsetup is 2 seconds. On my machine, for SHA512, this works out at 0.9 to 1.5 million iterations (depending, I suppose, on what was happening on the machine at the time).

If the decrypt time is, like yours, ten times slower, my decryption of roughly half a minute fits your observations.

I could allow the iteration time to be specified as part of the encryption script, although I worry that doing so would reduce security if people chose (as you have) just ½ second or even less.

---

### Post by 3-david-o on 2018-09-26
> **Paddy Landau said:**
> ... I could allow the iteration time to be specified as part of the encryption script, although I worry that doing so would reduce security if people chose (as you have) just ½ second or even less.

There's certainly an impact on security, which is why I mentioned that, and linked to a [more authoritative document]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects") on the matter. But reducing the iter-time by a (mere) factor of 10 can be more than compensated for by making the passphrase 1 character longer - and typing one more character is likely to be quicker than waiting 20 seconds for a million hashing iterations.

According to the aforesaid document, if you have an iteration count of 100K (which is what I get on my machine with an iter-time of 100ms), and a 12-character passphrase composed of randomly-chosen letters, digits and punctuation, then a brute-force attacker would need to spend $20 TRILLION to find your passphrase. I think that's pretty secure.

I think that the bigger problem with allowing the iter-time to be specified as part of the encryption script is that people wont know, in advance, what would be a suitable value to specify. It so much depends on their hardware. So, it isnt until you've completed the encrypted installation and rebooted that you'll find out how long you need to wait when you boot. And, if you discover it is unreasonably long, then it would be daft to go though the whole installation process all over again simply to revise the iter-time. A much simpler approach would be to provide a utility script that allows it to be adjusted, following the steps I mentioned before (and providing suitable warnings about security). Obviously the process could be improved by prompting for the passphrase just a couple of times to begin with, and then passing it in as an argument to the other commands as required.

---

### Post by Paddy Landau on 2018-09-27
> **3-david-o said:**
> There's certainly an impact on security…
Thanks for the link to the article. It's already a bit outdated (such is the speed of technology change!), but a good article nonetheless.

I understand what you say about the importance of the quality of the passphrase, and using SHA512 rather than the default SHA256, thereby allowing the iterations to be decreased. (The encryption script uses SHA512.)

When I have time, which might not be for a long while, I'll look at adding iteration-time to the script.

---

### Post by archphoenix on 2018-10-09
Hello, looking at your scripts, it looks like you create an encryption keyfile (everything okay there) but copy it to initramfs later on.
What will protect the keyfile once stored on initramfs? Did I miss an initramfs encryption part? If so, how do it gets decrypted?

---

### Post by Paddy Landau on 2018-10-09
> **archphoenix said:**
> &#8230; it looks like you create an encryption keyfile (everything okay there) but copy it to initramfs later on.
If I'm doing that, it's a big mistake! Can you point out where exactly this happens, please, because it certainly isn't intentional.

**EDIT:** I presume you specifically mean that it's copied to the EFI partition, because everything else is encrypted.

---

### Post by C.S.Cameron on 2018-10-09
Does this mean that Full disk encryption is now working with Full installs to flash drive?
That would sure be a boost for bootable pendrive security.

---

### Post by archphoenix on 2018-10-10
> **Paddy Landau said:**
> If I'm doing that, it's a big mistake! Can you point out where exactly this happens, please, because it certainly isn't intentional.

**EDIT:** I presume you specifically mean that it's copied to the EFI partition, because everything else is encrypted.

"cp /etc/crypt.system "${DESTDIR}"/etc/"
line 1481
Part of "/etc/initramfs-tools/hooks/loadinitramfskey.sh"

If this is only copying to EFI partition, then EFI partition must be on removable media, but I don't see mentions of EFI in this part.

---

### Post by Paddy Landau on 2018-10-10
> **C.S.Cameron said:**
> Does this mean that Full disk encryption is now working with Full installs to flash drive?
That would sure be a boost for bootable pendrive security.
It has worked in my test. However, because of varying hardware and lack of support from Canonical, I can't guarantee that it will work for you. I wish that I could guarantee it!

---

### Post by Paddy Landau on 2018-10-10
> **archphoenix said:**
> "cp /etc/crypt.system "${DESTDIR}"/etc/"
line 1481
Part of "/etc/initramfs-tools/hooks/loadinitramfskey.sh"

If this is only copying to EFI partition, then EFI partition must be on removable media, but I don't see mentions of EFI in this part.
That's fine. The folder [FONT=lucida console]/etc[/FONT] is on the system partition, so to access [FONT=lucida console]crypt.system[/FONT], you would have had to decrypt the system partition anyway. It's not on the EFI System Partition (ESP).

---

### Post by archphoenix on 2018-10-10
Then i fail to understand why one would copy a file from etc to itself, as the source of the copy is already there.

---

### Post by C.S.Cameron on 2018-10-10
Thanks Paddy: I will give it another try as soon as I get a chance.

---

### Post by Paddy Landau on 2018-10-11
> **archphoenix said:**
> Then i fail to understand why one would copy a file from etc to itself, as the source of the copy is already there.
I hadn't noticed that. I didn't write the script; I got it from someone else who understands this way, way more than I do!

I'm going to test this to find out if it's a redundant line. I'll post back here once I have the results.

---

### Post by Paddy Landau on 2018-10-11
> **Paddy Landau said:**
> I'm going to test this to find out if it's a redundant line.
I don't pretend to understand it, but the line is required. Without it, the system is unable to get past the cryptsetup screen. So, leave it in.

---

### Post by archphoenix on 2018-10-14
Hello, it looks like indeed the encryption key is copied to initramfs, meaning we're basically leaving the keys under the "welcome" carpet when leaving home.
[https://www.pavelkogan.com/](https://www.pavelkogan.com/) > Don&#8217;t forget that since the keyfile is stored on the ramdisk unless initramfs is encrypted, is it ?

You may also want to use /etc/kernel/postinst.d/ scripts to reduce your script's dependency on other tools.

---

### Post by Paddy Landau on 2018-10-15
> **archphoenix said:**
> … it looks like indeed the encryption key is copied to initramfs
I think that this is only temporarily on the RAM disk, not on permanent disk. On my test machine, I searched the entire hard drive (including the ESP) for a copy of [FONT=lucida console]crypt.system[/FONT], and it was only in its correct place. Unless you show me otherwise, I'm treating this as a false alarm. But, I shall run another test in case I missed something.

> **archphoenix said:**
> You may also want to use /etc/kernel/postinst.d/ scripts to reduce your script's dependency on other tools.
I haven't come across this folder before. Could you tell me more about it, and how you envisage my using it, please? Remember that I'm no expert, and I've simply put together what others have created. I suspect that you would like [FONT=lucida console]zz-update-grub[/FONT] to contain the update process — if that would work, it would be a far better workaround than I currently have in place.

---

### Post by C.S.Cameron on 2018-10-15
Paddy: Thanks, very useful. 
Installation to Full install flash drive went smoothly, once I gave up trying to install from desktop and used a Live USB instead.
Also want to encrypt the usbdata partition, (NTFS), which is importantish on a portable drive.
The more computers a portable drive can boot the better. 
Any plans to include BIOS systems?
Home encryption seemed to work OK, BIOS and UEFI, with a traditional install.
I tried Sudodus' basic mkusb setup, which usually works for both.
It worked for booting an unencrypted install on one partition on a BIOS system and booting the encrypted OS on a different partition with UEFI.
As you warned encryption did not work on a BIOS boot.

---

### Post by Paddy Landau on 2018-10-16
> **C.S.Cameron said:**
> Installation to Full install flash drive went smoothly, once I gave up trying to install from desktop and used a Live USB instead.
That's interesting. I don't know enough to comment on this, though.
> **C.S.Cameron said:**
> Also want to encrypt the usbdata partition, (NTFS), which is importantish on a portable drive.
You can overwrite the existing NTFS with a LUKS partition, and decrypt it after booting. It is possible to automate the decryption by adding it to [FONT=lucida console]/etc/crypttab[/FONT] and using a file-based key, which you might name (say) [FONT=lucida console]/etc/crypt.ntfs[/FONT]. You'd need to use the UUID instead of the partition name (e.g. [FONT=lucida console]/dev/sdb2[/FONT]), as that could change from computer to computer.
> **C.S.Cameron said:**
> Any plans to include BIOS systems?
I wouldn't know how to do this, sorry! I guess that the information is out there somewhere.

Thank you for sharing your results.

---

### Post by C.S.Cameron on 2018-10-23
Paddy:
I have managed to get your full disk encryption working both BIOS and UEFI.
Instructions: [https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314)
I will give encrypting the NTFS partition a try as you suggest.
When in Something else I noticed one of the "data"  partitions at the top was about the same size as my NTFS partition, Is there any relation.

---

### Post by Paddy Landau on 2018-10-23
> **C.S.Cameron said:**
> I have managed to get your full disk encryption working both BIOS and UEFI. Instructions&#8230;
Brilliant! I've added a reference to your solution in the [Advanced section]("https://help.ubuntu.com/community/ManualFullSystemEncryption#Advanced_features") of the instructions. Thank you for this.
> **C.S.Cameron said:**
> When in Something else I noticed one of the "data"  partitions at the top was about the same size as my NTFS partition, Is there any relation.
The data partitions list shows (or should show) everything connected to your computer apart from the Live DVD or USB itself, so your NTFS partition would be included. If the partition is encrypted with VeraCrypt, it won't know the type of file system (because VeraCrypt hides this. LUKS partitions show that they are LUKS but not the contents), but if it's unencrypted, it should show that it is NTFS.

---

### Post by condorview on 2018-11-06
Hello, Paddy Landau

I'm inexperienced ubuntu user but thanks to your great instruction I managed to run ubuntu 18.04 with dual-boot and full system encryption. I've been working without any issues for almost one month. Sadly, yesterday's software update messed up the booting menu. Instead of boot menu I get black screen with minimal  BASH-like line. Fortunately, I can boot Windows 10 after typing 'exit' command. What is strange, I cannot use a basic commands inside this minimal BASH-like, for example 'ls' shows the error: "file /grub/x86_64-efi/ls.mod not found".

Of course, I've tried to apply all steps from "Computer fails to boot after upgrade or new installation" paragraph on the page [https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting) but with no effect. BTW, I don't know if warnings about "no matching swap device is available" are important.

```
ubuntu@ubuntu:~$ sudo cryptsetup open --type=luks /dev/sda4 system
Enter passphrase for /dev/sda4: 
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/mapper/system-root /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/mapper/system-boot /mnt/root/boot
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/root/boot/efi
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/root/run
ubuntu@ubuntu:~$ sudo chroot /mnt/root
root@ubuntu:/# mount --types=proc proc /proc
root@ubuntu:/#  mount --types=sysfs sys /sys
root@ubuntu:/# update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.15.0-38-generic
W: initramfs-tools configuration sets RESUME=/dev/mapper/system-swap
W: but no matching swap device is available.
update-initramfs: Generating /boot/initrd.img-4.15.0-36-generic
W: initramfs-tools configuration sets RESUME=/dev/mapper/system-swap
W: but no matching swap device is available.
root@ubuntu:/# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Found linux image: /boot/vmlinuz-4.15.0-36-generic
Found initrd image: /boot/initrd.img-4.15.0-36-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

My devices are:
```

/dev/sda1  EFI System
/dev/sda2  Microsoft reserved
/dev/sda3  Microsoft basic data
/dev/sda4  Linux filesystem

```

I feel lost.  I will be very grateful for any clue or a piece of advice about how I can cope with it. I'm sorry for my ignorance and thanks in advance.

---

### Post by Paddy Landau on 2018-11-06
Hello condorview

You are brave, doing this as an inexperienced Ubuntu user!

I'm sorry that you're having trouble, and I confess that I'm also somewhat mystified.

Regarding the "no matching swap device", this should not be a problem, as Ubuntu will run just fine during this process without swap.

Please will you repeat the troubleshooting process, except that when you get to step 7 ("Fix Grub"), do the following.
[LIST]
[*]Don't issue the commands [FONT=&amp]update-initransfm[/FONT] and [FONT=&amp]update-grub[/FONT].
[*]Instead, enter the following command:
[FONT=lucida console]refreshgrub
[/FONT]This command might take a minute or two to run.
If you see errors saying, "File descriptor … leaked on vgs invocation…", ignore them.
[*]Continue with steps 8 and 9.
[/LIST]
Please let me know what happens.

---

### Post by condorview on 2018-11-06
Great! It works! :)

Thank you, very much.  FYI, I wouldn't be so brave unless your instruction was so professional and easy to understand :) Ubuntu is my extra OS now but I expect it will be the first one in the near future. Many hard days ahead of me although with helpful community I am going to make it. 

BTW, I was thinking about applying "grub-install /dev/sda". Would it be a good idea?

Edit: I had to run "fsck /dev/mapper/system-root" because boot process dropped to the BusyBox shell after restarting. So maybe some problems with my disc caused troubles with grub.

---

### Post by Paddy Landau on 2018-11-07
> **condorview said:**
> Great! It works!
Fabulous! I've adjusted the troubleshooting instructions to do this instead.

And, thank you for your kind words.

> **condorview said:**
> I was thinking about applying "grub-install /dev/sda". Would it be a good idea?
Probably not. Grub installation has already been done, otherwise you wouldn't have been able to boot.

> **condorview said:**
> I had to run "fsck /dev/mapper/system-root" because boot process dropped to the BusyBox shell after restarting. So maybe some problems with my disc caused troubles with grub.
There's no BusyBox on Ubuntu :) It's the command line, also called CLI (command line interface), the console, or the terminal.

Your system should automatically run [FONT=lucida console]fsck[/FONT] on boot if it spots any inconsistencies; every 30 boots or something like that; or if it sees the file [FONT=lucida console]/forcefsck[/FONT]. However, it doesn't hurt to run it manually. I would add a couple of options to the command, as follows (note the capitalisation):
```
fsck -CMf /dev/mapper/system-root
```
[LIST]
[*][FONT=lucida console]-C[/FONT] — Display a progress bar
[*][FONT=lucida console]-M[/FONT] — Don't run if the file system is already mounted (to prevent data corruption).
[*][FONT=lucida console]-f[/FONT] — Force a full check even if no inconsistencies were spotted.
[/LIST]

---

### Post by condorview on 2018-11-07
Thanks again :) 

As to BusyBox I came across a similar issue as descibed in the answer [https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox/817660#817660](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox/817660#817660)

---

### Post by Paddy Landau on 2018-11-07
> **condorview said:**
> As to BusyBox…
Oh… maybe I'm wrong! It looks as though BusyBox is attached to initramfs.

---

### Post by Zythyr on 2018-11-14
> **Paddy Landau said:**
> I have updated the documentation for [Manual Full System Encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), and vastly simplified it in the process.

For those who don't know, this allows you to encrypt everything including [FONT=lucida console]/boot[/FONT], excluding the EFI System Partition for obvious reasons, and it plays nicely with other systems, e.g. Windows.

If you choose to try it, please let me know (in this thread) if it works for you and if you find any bugs in the documentation or the process.

Whether or not it works, it would be helpful to know which flavour and version you use.

Please **read the warnings and caveats** before deciding whether or not to use it. Ignoring them could leave you disappointed.

If you like it, and want Canonical to officially implement it or something like it in the Installer, please [support the request]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1773457") (log in and select the green writing at the top left).

Thank you :)

Paddy, thank you very much for updating the documentation. However, I would like to suggest some constructive feedback regarding the documentation. 

I noticed you made significant revisions to the [original  ManualFullSystemEncryption/DetailedProcess guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess?action=recall&rev=1") (and the sub-pages) which was originally written by @slickymaster. The original guide has manual step by step guide which also explained the commands on the exact process for setup/installation of Ubuntu with encrypted partition. Your revision replaced the step by step guide with an "_automated_" script. I think the new guide no longer holds the spirit of the original guide showing how to "_manually_" encrypt. I think the manual steps and commands in the guide was very usefully and taught the readers on the exact process. The automated script you created is very helpful, however, I think we should append it to the original guide instead of replacing it. 

I think the original [ManualFullSystemEncryption guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption") was one of the few very well written guides on partition encryption in Linux I have found online. I often referred to this guide very frequently to get all the commands and refresh my memory on the manual encryption process. Just like you, I believe encryption is important and Canonical should support full system encryption. However, meanwhile, it is important we _teach _the readers step by step and the commands required to manually encryption. This creates _high value by investing in "teaching"_ instead of directly feeding an automated script which the user has no idea what it does. 

I hope my feedback would be considered and the that the bulk of the original guide written by @slickymaster can be reverted back.

---

### Post by Paddy Landau on 2018-11-14
> **Zythyr said:**
> I noticed you made significant revisions to the [original  ManualFullSystemEncryption/DetailedProcess guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess?action=recall&rev=1") (and the sub-pages) which was originally written by @slickymaster…
The entirety was written by me :). Slickymaster moved my documentation from a development area to the main area, which is why it had his name.

Yes, there were significant revisions.

The reason why I removed the detailed explanation was that maintaining it had become a time-consuming burden for me — I am struggling with a long-term illness on top of everything else, so time is not something that I have much of. Had I left the explanations, they would quickly have become out of date.

Maintaining the script is much faster than maintaining a detailed description of how it works, and the script itself contains (I hope) understandable documentation.

If I were to have a volunteer to maintain the pages, of course, that would be great…

One volunteer has offered to put the script into GIT, which I know little about. When it's done, it will be better than its current location in Dropbox.

> **Zythyr said:**
> I think the original [ManualFullSystemEncryption guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption") was one of the few very well written guides on partition encryption in Linux I have found online…
Thank you. I'm sorry that those pages have gone now.

Yes, teaching is important. On the other hand, not only did I understand just a little of what was done (the discoveries and inventions were done by people much cleverer that I am, so my explanations were not really explanations but just a description of what to do), but also what I have been pushing for is for Canonical to take this on board and put it into the default installer (which, to my knowledge, has no user documentation on how it works).

The system was never intended for beginners, although I tried to make it accessible to such.

> **Zythyr said:**
> I hope … that the bulk of the original guide … can be reverted back.
I don't know how to do that — sorry. But, as I said, even if I were to do so, it was already out of date! The difference between the system for Ubuntu 16.04 and for Ubuntu 18.04 was surprisingly large. I have no idea if the future Ubuntu 20.4 will create an even wider gap.

---

### Post by absolute512 on 2018-11-26
Hi,

At first let me thank you for your efforts in creating this guide. Regrettably I was not able to make it work on my system. I have tried several times and the last two I did the troubleshooting with the chroot as well.
My system is a Dell XPS 13 9370 'Developer Edition' (came with Ubuntu 16.04 preinstalled).
Once I complete all the steps in the guide and reboot, I get to the GRUB menu where I am able to select between the choices of Ubuntu (comes preselected), Advanced options for Ubuntu and finally System setup.
When selecting the first entry I get the following three errors:
error: no such device: <device-id>
error: no server specified
error: you need to load the kernel first
finally I get a 'Press any key to continue...'
I can either press any key or wait for about ten seconds, both actions take me back to the GRUB menu.

The regular Ubuntu installer with and without encryption do work on this machine but I require suspend to disk.

Thank you in advance for your help,
abs512

---

### Post by Paddy Landau on 2018-11-27
@absolute512 — Can I confirm that you installed 18.04, not any other version? The process doesn't work with any other version.

I can't see your screen, obviously, so I have to make a bit of a guess here. I wonder if your computer has something that the script doesn't correctly understand.

Might I suggest that you install 18.04 using the default installer with full encryption (it won't encrypt [FONT=lucida console]/boot[/FONT] though).

Then, post-installation, get suspend-to-disk working. To do this, first create a swap partition and enable it (the default 18.04 uses swap files instead of a swap partition). Please ask in a new thread how to do this (or maybe it has already been answered on either this forum or [Ask Ubuntu]("https://askubuntu.com/")). Remember that the swap partition must be at least the size of your RAM, and you need it encrypted.

Once the swap partition is working, do the following.
[LIST=1]
[*]```
sudo apt install pm-utils
```
(It might already be installed.)
[*]Find the [FONT=lucida console]/dev/[/FONT] definition of the swap partition. You'll need this in step 6.
[*]Create the file
[FONT=lucida console]/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla[/FONT]
[*]In the file, put the following code.
```
[Re-enable hibernate by default in upower]Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultActive=yes
```
[*]Create the following file.
[FONT=lucida console]/etc/initramfs-tools/conf.d/resume[/FONT]
[*]In the file, put the following code.
[FONT=lucida console]RESUME=[/FONT]*[the /dev/ definition that you found in step 2]*
e.g.
[FONT=lucida console]RESUME=/dev/dm-0[/FONT]
[*]Edit the file
[FONT=lucida console]/etc/systemd/logind.conf[/FONT]
[*]In this file, append the following two lines.
```
HandleSuspendKey=hybrid-sleep
HandleLidSwitch=hybrid-sleep
```
[/LIST]
[SIZE=3]**Warning**[/SIZE]

I cannot guarantee that this will work. Every system and every hardware is different, and I have read that not all manufacturers support suspend-to-disk. Also, I'm no expert; everything that I did was put together from other people's excellent work.

---

### Post by absolute512 on 2018-11-27
Hi again,
I have tried as you asked and after resizing swap and stuff and other troubles (see: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230)) I was able to get the hibernation working.
Now I just wish I could do it with encrypted boot partition...
Thank you anyway!

---

### Post by Paddy Landau on 2018-11-28
> **absolute512 said:**
> I have tried as you asked and after resizing swap and stuff and other troubles (see: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230)) I was able to get the hibernation working.
Thank you for that bug report, which I believe that is relevant to this process. Useful to know!

> **absolute512 said:**
> Now I just wish I could do it with encrypted boot partition...
Does that mean that you still don't have an encrypted system? If so, you can work around it with the [guide for 18.04]("https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html") from Linux Uprising. Using eCryptfs is deprecated, but until Canonical fixes Ubuntu, it will have to do for many people.

---

### Post by thrdroom on 2018-11-28
Hello there :)

This is my first post in this forum, as im not familiar with the rules please have patience with me.

First of all i wanna thank you Paddy! Your contribution on this topic is really awesome and the "old" detailed "pre-script"-guide helped me to get a better understanding on certain mechanisms.
I greatly appreciate your work, you rock :guitar:

The first thing i did after the registration was to support/vote the bugs you have mentioned in this post [https://ubuntuforums.org/showthread.php?t=2399092&p=13803281#post13803281](https://ubuntuforums.org/showthread.php?t=2399092&p=13803281#post13803281) [check!]
You are totally right about the fact that Canonical should implement and maintain this officially! In this times, it shouldn't be that hard for an average user to get a proper full-encrypted system imho.

I used this guide a year ago to setup my station and was really thrilled about how smooth everything was going because of the detailed description.
As i have now decided to make the switch from Kubuntu to KDE Neon i revisited your guide. To be honest i was amazed and at the same time a little bit unhappy about the fact that the detailed steps were replaced in favour of a script. Don't get me wrong, the script is really well. It is at the same time convenient for beginners and a little annoying/restrictive for someone who knows exactly what he needs.
Let me give you some examples for problems i came across with the current script compared to the detailed manual-process before:

    
[LIST=1]
[*]The script forces me to choose two different passwords for system and data-drives. As i don&#8217;t want to overcomplicate things(in case of dataloss or crash), i want to have the same password for both drives and only one single keyfile. I think the user should have the choice to choose what he want's. 
[*]The script don&#8217;t give me the option to choose NOT to delete/format the home-partition. As in my case where i just wanted to reinstall/switch the distribution while keeping(choose and mount) my existing encrypted home-partition on the second drive. 
[*]The script don&#8217;t give me the option to choose an already existing swap-partition(no matter which drive). 
[*]The script only gives a user the option to place the swap partition on the system-drive. In my case, the system-drive is a small SSD and the data-drive a big HDD. Therefore i do want to place the swap partition on the bigger data-HDD to reduce io-workload from the system-SSD. Assuming i don&#8217;t already have a swap-partition. 
[*]The script don&#8217;t give me the option to choose/change the hash, and the key-size of the luks-container and the block-size of the encryption-key(s). The default value of 512 is too low for me. 
[/LIST]
 
I think Zythyr has a good point in saying > ManualFullSystemEncryption guide was one of the few very well written guides on partition encryption in Linux and that by switching from instructions to the script, the learning-process has degraded. You might argue that everyone could read the source-code of the script to understand the process, but not everyone understands the use of variables, functions etc. especially not users without coding-skills.


As archphoenix has pointed out before, the dropbox-hosting/wget stuff is kinda insecure an i also had a bad feeling about getting some scripts hosted on dropbox.
Also the fact that the "encryptinstallation" script does download and execute the "encryptinstallationchroot" and "refreshgrub" script later on, without the users consent is a little no-go for me, sorry ;)

Therefore i have setup an git repository for this project on Github. I hope that Paddy is ok with that? If you are not ok with that please let me know.
Also please let me know how you would like to handle the maintenance of the script(maybe also the wiki/manual) on Github, i would suggest you create an Github account. Lets discuss this via Private Message paddy.

You can find the repository right here:
[https://github.com/thrdroom/ManualFullSystemEncryption](https://github.com/thrdroom/ManualFullSystemEncryption)

As you are new to git, and maybe dont want loose much time i would suggest you should use a gui for git.
You could use SmartGit [https://www.syntevo.com/smartgit/](https://www.syntevo.com/smartgit/) for example.

I hope that this will help to get this script more popular and further developed. :)

I already have some changes/pull-requests for your original-script which fixes most of the 5 issues listed above, but i haven't committed them to the git-repo without your consent paddy. Please pm me :)

Im sorry to hear that you are struggling with a long-term illness. I wish you the best and send you some positive energy! As you have stated before that the maintenance of the documentation had become a time-consuming burden for you, i may suggest you/we could also switch the documentation to a git-hosted markdown-wiki. Then everybody who has time could work on the project and send you pull-requests. You and maybe other mods you choose then would only have to pick pull-request from other users. So this would give others the option to work on the project, which would take time of your shoulders while you still would be in control of what gets in and what not. Hosting the guide as a wiki also via a git-repo would also give option of versioning and going back in time in the future (like requested by 
Zythyr).

I am looking forward to a feedback from you guys.

---

### Post by Paddy Landau on 2018-11-29
> **thrdroom said:**
> … support/vote the bugs you have mentioned in this post [https://ubuntuforums.org/showthread.php?t=2399092&p=13803281#post13803281](https://ubuntuforums.org/showthread.php?t=2399092&p=13803281#post13803281)[check!]
Those are correct.

> **thrdroom said:**
> … a little bit unhappy about the fact that the detailed steps were replaced in favour of a script.
As explained in [post #67]("https://ubuntuforums.org/showthread.php?t=2399092&page=4&p=13816132&viewfull=1#post13816132"), I didn't have a reasonable choice: "The reason why I removed the detailed explanation was that maintaining it had become a time-consuming burden for me — I am struggling with a long-term illness on top of everything else, so time is not something that I have much of. Had I left the explanations, they would quickly have become out of date. Maintaining the script is much faster than maintaining a detailed description of how it works, and the script itself contains (I hope) understandable documentation."

> **thrdroom said:**
> The script forces me to choose two different passwords for system and data-drives. As i don’t want to overcomplicate things(in case of dataloss or crash), i want to have the same password for both drives and only one single keyfile. I think the user should have the choice to choose what he want's.
Having the same passphrase is unnecessary, because once the system has been decrypted, it will automatically decrypt the data drive. However, if it's really what you want, all that you need to do is to replace the existing passphrase with the new one.
```
sudo cryptsetup luksChangeKey /dev/sda3   # Replace /dev/sda3 with the correct partition name.
```


> **thrdroom said:**
> The script don’t give me the option to choose NOT to delete/format the home-partition. As in my case where i just wanted to reinstall/switch the distribution while keeping(choose and mount) my existing encrypted home-partition on the second drive.
That's true. Sorry.

> **thrdroom said:**
> The script don’t give me the option to choose an already existing swap-partition(no matter which drive).
In such a case, when you install, don't use a swap partition. After installation, you can add the swap partition manually to [FONT=lucida console]/etc/fstab[/FONT]. You will need to ensure that the swap partition is correctly encrypted, which means that you'd have to also add it to [FONT=lucida console]/etc/crypttab[/FONT].

> **thrdroom said:**
> The script only gives a user the option to place the swap partition on the system-drive. In my case, the system-drive is a small SSD and the data-drive a big HDD. Therefore i do want to place the swap partition on the bigger data-HDD to reduce io-workload from the system-SSD. Assuming i don’t already have a swap-partition.
See the previous point.

> **thrdroom said:**
> The script don’t give me the option to choose/change the hash, and the key-size of the luks-container and the block-size of the encryption-key(s). The default value of 512 is too low for me.
You are correct. I have used sha512 as being the best encryption available for this particular setup. As for the key size, my investigations showed that anything greater than 512 was pointless. Maybe my investigations were incorrect; if so, please let me have the details.


> **thrdroom said:**
> I think Zythyr has a good point in saying  and that by switching from instructions to the script, the learning-process has degraded. You might argue that everyone could read the source-code of the script to understand the process, but not everyone understands the use of variables, functions etc. especially not users without coding-skills.
As I already explained, I simply don't have time to maintain a complex set of instructions. This was never intended to be for a beginner, anyway. That's something that I'm hoping that Canonical will fix, which will render this process redundant.

> **thrdroom said:**
> Therefore i have setup an git repository for this project on Github. I hope that Paddy is ok with that? 
I am absolutely happy with this, and thank you for taking the initiative! Thank you also for the instructions.

> **thrdroom said:**
> I already have some changes/pull-requests for your original-script which fixes most of the 5 issues listed above, but i haven't committed them to the git-repo without your consent paddy. Please pm me :)
Please go ahead! I am most grateful for the help. Let me know how to change the documentation, specifically the [download instruction]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPrepareInstall#Download_the_application"). I'll change it accordingly.

> **thrdroom said:**
> I wish you the best and send you some positive energy!
Thank you :)

> **thrdroom said:**
> As you have stated before that the maintenance of the documentation had become a time-consuming burden for you, i may suggest you/we could also switch the documentation to a git-hosted markdown-wiki. Then everybody who has time could work on the project and send you pull-requests. You and maybe other mods you choose then would only have to pick pull-request from other users. So this would give others the option to work on the project, which would take time of your shoulders while you still would be in control of what gets in and what not. Hosting the guide as a wiki also via a git-repo would also give option of versioning and going back in time in the future (like requested by 
Zythyr).
Feel free to go ahead with this!

Thank you again.

---

### Post by Dáire Fagan on 2018-12-25
Paddy, first of all, Merry Christmas, and thank you very much for authoring your guide on the Community Help Wiki.

When I first attempted dual booting Windows and Ubuntu with LUKS and LVM some years ago, I do not remember having the benefit of it, and wish I had. At the time I had planned to then encrypt Windows with TrueCrypt, until I learned about the concerns that had been raised about it. Despite this, I did manage to configure LUKS and LVM, though I will not be surprised to learn I missed something when I have finished reading your guide. I have reinstalled since after a broken upgrade, and I did not employ LUKS and LVM, and had thought I might remedy that today.

I am posting now, as the Overview Partition Preparation section drew my attention to something on my system that may cause an issue when I am actually carrying out the steps. You display your existing Windows partitions that look very similar to my own, but I wonder if my drive is in a state that would cause problems later. I still have that existing non LUKS LVM Ubuntu installed, which I am happy to wipe, but as Grub was already installed during the Ubuntu install, will this cause an issue? Also, today I completed a very interesting guide, [Using VeraCrypt with a UEFI dual boot setup]("https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b") to encrypt Windows 10 on the same drive, and it occurred to me if any of that might have changed something that would cause an issue?

Before finding your guide today, reviewing my old posts on this forum when I struggled through my last LUKS LVM setup, I was thinking I would just wait until I have some new larger SSD in the future. If I am able to still apply your guide to my system I am very happy to, but I thought I would run my concerns by you before I delete my current Ubuntu install!

---

### Post by Dáire Fagan on 2018-12-28
> **dusf said:**
> Paddy, first of all, Merry Christmas, and thank you very much for authoring your guide on the Community Help Wiki.

When I first attempted dual booting Windows and Ubuntu with LUKS and LVM some years ago, I do not remember having the benefit of it, and wish I had. At the time I had planned to then encrypt Windows with TrueCrypt, until I learned about the concerns that had been raised about it. Despite this, I did manage to configure LUKS and LVM, though I will not be surprised to learn I missed something when I have finished reading your guide. I have reinstalled since after a broken upgrade, and I did not employ LUKS and LVM, and had thought I might remedy that today.

I am posting now, as the Overview Partition Preparation section drew my attention to something on my system that may cause an issue when I am actually carrying out the steps. You display your existing Windows partitions that look very similar to my own, but I wonder if my drive is in a state that would cause problems later. I still have that existing non LUKS LVM Ubuntu installed, which I am happy to wipe, but as Grub was already installed during the Ubuntu install, will this cause an issue? Also, today I completed a very interesting guide, [Using VeraCrypt with a UEFI dual boot setup]("https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b") to encrypt Windows 10 on the same drive, and it occurred to me if any of that might have changed something that would cause an issue?

Before finding your guide today, reviewing my old posts on this forum when I struggled through my last LUKS LVM setup, I was thinking I would just wait until I have some new larger SSD in the future. If I am able to still apply your guide to my system I am very happy to, but I thought I would run my concerns by you before I delete my current Ubuntu install!

I decided to opt for a complete reinstall of both operating systems, and so far I have filled the HDDs with dd using /urandom, and executed a hdram --secure-erase-enhanced on the SSD before filling with urandom also. I have just reinstalled Windows 10 with a custom EFI partition of 600MB, as the guide mentions at least 577MB is the recommended size, and I am letting Windows 10 update.

The next issue I am trying to work out, is should I apply Veracrypt to Windows 10 first before following the ManualFullSystemEncryption guide, or use Veracrypt afterwards? Perhaps either will work? I know Veracrypt will make some changes to the EFI partition...

---

### Post by Paddy Landau on 2018-12-28
Thanks for the link to the VeraCrypt guide, @dusf.

I have never used VeraCrypt to encrypt an operating system (although I'm well familiar with using it for data partitions and virtual partitions). This means, unfortunately, that I'm unable to answer your question.

As this is a brand new installation, might I suggest that you try? From what I can gather, according to the link that you posted, you should:
[LIST=1]
[*]Install Windows
[*]Install Ubuntu (using the guide)
[*]Use VeraCrypt to encrypt Windows
[*]Follow the guide to repair Grub
[/LIST]
Don't bother running updates on Windows until you are sure that everything works.

If your hardware is powerful enough, and you don't need a superfast Windows (e.g. for gaming), might I suggest that you install Ubuntu on the entirety of your computer, and then install Windows in a virtual machine (e.g. VirtualBox or VMWare) within Ubuntu? That way, you don't have to encrypt Windows as it will be already encrypted through LUKS, and you can run both systems simultaneously.

Sorry that I can't give you a straight answer to your question.

By the way, the size 577 Mb is sufficient for the EFI System Partition, according to the relevant documentation.

---

### Post by Dáire Fagan on 2018-12-29
Hi Paddy, thanks for the input.

I have completed the Windows 10 install, and I did let it update as I know some of the major releases make changes to at least the recovery partition.

I have successfully completed the Manual Full System Encryption Guide, although to login for the first time I had to use recovery, enable networking, install lightdm, set nomodeset in Grub, login, and then install my nvidia-415 driver (this is something I encountered on my last normal install, I think due to my using an Nvidia GTX 970). I am now logged in to my desktop, without nomodeset, after entering the master key and my password, but in the Ubuntu *launcher panel*, top left, I have a hard drive icon arrow with an arrow pointing over it, and when I mouseover it displays the tooltip 'Install Release'. Is this something you have seen? It is almost like some of the Live CD came across with my install? I am certain I am logged into my desktop and not the Ubuntu Live USB :D

Also, I cannot open GParted. When I pressed the superkey and searched for it nothing was found, but then when I tried to install it the terminal output it was installed already, when I tried to launch it from terminal it took my login password, but then nothing happened. There were also some errors also displayed. I uninstalled and reinstalled GParted but there was no change. Please see the errors, and some of the commands I have been trying to fix this in the pastebin: [https://paste.ubuntu.com/p/6tJW4P9sHj/](https://paste.ubuntu.com/p/6tJW4P9sHj/). I am just hoping I did not do something wrong during the install that has caused this, as I am not sure I can face another re-installation of any OS (though I will if I have to as I want to see this through) as I am at all of this several days already! :D

Also, just to draw your attention to the error:

```
U[COLOR=#000000]nit tmp.mount does not exist, proceeding anyway.[/COLOR]
```

in case this should concern us.

On my laptop (18.04, desktop which I used your guide for is 18.10), when I launch gparted from terminal it mentions 'Unit -.mount does not exist, proceeding anyway'.

=======

On my first attempt following the guide, I did close the Ubuntu installer and start over, first when I discovered the separate data partition referring to /home (I have a separate data hard drive but I wanted /home encrypted on my primary SSD) not a separate data non-home partition, and I closed it and started again discovering that the 'system' partition would not split part of itself into a separate /home partition. When I tried the third time the script failed, giving an error about system being resized. So I deleted all partitions, and rebooted, and started again, redownloading the script etc. I was able to get through the guide that time - just mentioning in case relevant to the issue with GParted and Install Release visible.

---

### Post by Paddy Landau on 2018-12-29
> **dusf said:**
> … in the Ubuntu *launcher panel*, top left, I have a hard drive icon arrow with an arrow pointing over it, and when I mouseover it displays the tooltip 'Install Release'.
I presume that you installed Ubuntu 18.04. This is not something that I've seen, sorry. I suggest that you post a new thread, with a screenshot, in the forum [Desktop Environments]("https://ubuntuforums.org/forumdisplay.php?f=329").

> **dusf said:**
> … I cannot open GParted. I uninstalled and reinstalled GParted but there was no change.
Usually, uninstalling and reinstalling a program does nothing. Unlike Windows, there isn't a spaghetti-like Registry. To clear a program's settings, you need to delete its configuration file or folder. However, I don't believe that this is your problem, because…

From my personal tests, GPartEd is unable to cope with LVM over LUKS. (At least, that's what I believe; I might be wrong! [As I wrote]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartition#Create_the_data_partition") in the documentation, "Close gparted now, because it has done its job and cannot correctly handle encryption.") That shouldn't explain why GPartEd crashes, though.

I suggest that you start a new thread. I don't know the best forum; maybe [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331") or [Hardware]("https://ubuntuforums.org/forumdisplay.php?f=332")? In your new thread, explain that GPartEd crashes (include the pastebin link) and that your system is installed on LVM over LUKS.

Please would you post the links to both of your new threads here, so that I can follow them.

---

### Post by Paddy Landau on 2018-12-29
> **dusf said:**
> &#8230; your guide for is 18.10
Sorry, no, my guide is for 18.04 LTS.

EDIT: I think that I misread your post. But the guide is untested on 18.10.

---

### Post by Dáire Fagan on 2018-12-29
> **Paddy Landau said:**
> Sorry, no, my guide is for 18.04 LTS.

EDIT: I think that I misread your post. But the guide is untested on 18.10.

The question now is whether to keep going with 18.10, or start again with 18.04...

It is crucial for work and study that my desktop (and my laptop which I will work on next) are working, and if something goes wrong I will not have this sort of time available during term (not just to follow your guide, but the days I spent preparing my 4 drives, opening up PC case to securely erase SSDs, get Windows 10 installed with custom diskpart partition scripts etc) so I am leaning towards reinstalling 18.04, as like you have mentioned it is tested.

To undo everything so far, can I just delete sd5 where I created system, and sd6 where I created the data-home partition, or have the installer or your script made any changes to the EFI partition that need to be undone some how?

Or I can keep going as is, keep up with releases, and if I do encounter an issue in the future just reinstall normal encrypted Ubuntu and reassess my options when I have more time.

The following code removed the install release icon, and whatever was causing it:

```
sudo apt-get remove ubiquity
```

I will post about GParted a bit later.

[18.10 custom LVM over LUKS, GParted will not start]("https://ubuntuforums.org/showthread.php?t=2409202&p=13826731#post13826731")

---

### Post by Paddy Landau on 2018-12-29
> **dusf said:**
> The question now is whether to keep going with 18.10, or start again with 18.04…
It is crucial for work and study that my desktop (and my laptop which I will work on next) are working…
You should always stick to the LTS versions if you can't afford to experiment.
[LIST]
[*]All even-numbered .04 releases are LTS, so this would include 16.04, 18.04, 20.04, and so forth. These are the ones that you should stick to.
[*]Version 18.10 is an experimental version, as will be 19.04 and 19.10.
[*]In fact, if it's that important to you, don't upgrade an existing installation until at least three months after the release of an LTS version. Definitely avoid all other releases.
[*]Version 18.10 will become redundant in June 2019, and 19.04 in December 2019.
[*]On the other hand, version 18.04 will be supported at least until April 2021, so you won't have to upgrade until then.
[/LIST]
> **dusf said:**
> To undo everything so far, can I just delete sd5 where I created system, and sd6 where I created the data-home partition, or have the installer or your script made any changes to the EFI partition that need to be undone some how?
There are changes to the EFI System Partition, but a reinstallation will redo the changes, so that's OK. Delete and recreate the relevant partitions (system and data-home), and reinstall Ubuntu 18.04 from scratch.

> **dusf said:**
> Or I can keep going as is, keep up with releases…
Well, you can take that risk. But, what if 19.04 doesn't work?

> **dusf said:**
> The following code removed the install release icon, and whatever was causing it…
Thanks. Ubiquity is the installer. I have no clue how it was installed on your 18.10 release!

> **dusf said:**
> [18.10 custom LVM over LUKS, GParted will not start]("https://ubuntuforums.org/showthread.php?t=2409202&p=13826731#post13826731")
Thanks, I'll follow this.

---

### Post by Dáire Fagan on 2018-12-30
Thanks for the info. I downloaded 18.04 LTS last night, created the USB stick with Rufus, deleted my system and data partitions, filled both with /urandom, and followed the guide again verbatim.

There is a delay of ~15 seconds after entering the system passphrase, this is not a big deal, but is this normal?

Also, the 'Install RELEASE' icon is again present at the top of the left hand panel. Same issue with gparted:

```
dusf@contraption:~$ sudo apt install gparted
[sudo] password for dusf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version (0.30.0-3ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

dusf@contraption:~$ gparted

Command 'gparted' not found, but can be installed with:


sudo apt install gparted




```

I have not yet attempted to correct these issues, in case there is some diagnostics you would like me to run?

I also want to wait for input before I do anything, and I have asked for help here:

[18.04: Install RELEASE icon visible in launcher after install?]("https://ubuntuforums.org/showthread.php?t=2409235")

[18.04: 'Command 'gparted' not found... gparted is already the newest version']("https://ubuntuforums.org/showthread.php?t=2409234")

Paddy also, and this probably is very inconsequential, but I did re-open/leave open GParted during the installation just to confirm partition locations when selecting them with the installer.

---

### Post by Dáire Fagan on 2019-01-15
Both issues on my desktop were resolved, the method is in each thread linked in my previous post. I can confirm both issues also occurred when I followed the guide to install 18.04 on my Dell XPS 9360.

---

### Post by Paddy Landau on 2019-01-15
@dusf Thank you for the update. In your previous post, you mentioned GPartEd being left open. To the best of my knowledge, that shouldn't have caused any problem.

---

### Post by Dáire Fagan on 2019-01-23
> **Paddy Landau said:**
> @dusf Thank you for the update. In your previous post, you mentioned GPartEd being left open. To the best of my knowledge, that shouldn't have caused any problem.

Thanks for that.

Paddy, I am trying to make a permanent change to my Windows 10 grub menuentry, so that it boots to \EFI\VeraCrypt\DcsBoot.efi instead of EFI\Microsoft\Boot\Bootmgfw.efi. I am getting some help with it at LinuxQuestions, but they are a bit confused by my setup so I if I could run their concerns by you, and the steps they advise I take, could you please confirm none of it will undo or mess up my install from following your guide?

Although I did edit the menuentry for VeraCrypt/Windows 10 when I installed everything a few weeks ago, and it has been working fine, it has been changed, I am guessing due to an update. This change leads to Windows 10 trying to repair itself, although thankfully Windows 10 boots fine when I press F12 on boot and manually select the VeraCrypt Bootloader. Trying to change the menuentry again now I used grub-customiser as below and saved:

[ATTACH=CONFIG]282284[/ATTACH]

I can see this change is reflected in /boot/grub/grub.cfg as:

```
menuentry "Windows Boot Manager (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-efi-E625-C979' {    insmod part_gpt
    insmod fat
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  E625-C979
    else
      search --no-floppy --fs-uuid --set=root E625-C979
    fi
    chainloader \EFI\VeraCrypt\DcsBoot.efi
}
```

I also input sudo update-grub, but despite this when I reboot and press 'e' with the Windows 10 grub menuentry selected I can see it is still set to try and boot from EFI\Microsoft\Boot\Bootmgfw.efi.

On my thread at LinuxQuestions, [Making permanent change to grub boot menuentry?]("https://www.linuxquestions.org/questions/linux-general-1/making-permanent-change-to-grub-boot-menuentry-4175646731/#post5952429"), following advice I:

> I copied from /boot/grub/grub.cfg this:

```
menuentry "Windows Boot Manager (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-efi-E625-C979' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  E625-C979
    else
      search --no-floppy --fs-uuid --set=root E625-C979
    fi
    chainloader \EFI\VeraCrypt\DcsBoot.efi
}
```


to a new file I created, /etc/grub.d/40_custom, saved it, added GRUB_DISABLE_OS_PROBER=true to /etc/default/grub, and ran sudo update-grub.

But this did not help, and I then responded to a query with the following info:

> [QUOTE]Could the issue perhaps be with the permissions of this new file (40_custom), as below?

```
dusf@contraption:~$ ls -la /etc/grub.d/
total 112
drwxr-xr-x   5 root root  4096 Jan 22 18:21 .
drwxr-xr-x 152 root root 12288 Jan 23 08:46 ..
-rwxr-xr-x   1 root root  9783 Jul 17  2018 00_header
-rwxr-xr-x   1 root root  6258 Jul 16  2018 05_debian_theme
-rwxr-xr-x   1 root root 12693 Jul 17  2018 10_linux
-rwxr-xr-x   1 root root 11298 Jul 17  2018 20_linux_xen
-rwxr-xr-x   1 root root  1992 Jan 28  2016 21_memtest86+
-rwxr-xr-x   1 root root   197 Jan 22 16:37 30_os-prober_proxy
-rw-r--r--   1 root root   451 Jan 22 18:21 40_custom
-rwxr-xr-x   1 root root   194 Jan 22 16:37 40_custom_proxy
-rwxr-xr-x   1 root root  1418 Jul 17  2018 42_uefi-firmware
-rwxr-xr-x   1 root root   194 Jan 22 16:37 43_custom_proxy
-rwxr-xr-x   1 root root   216 Jul 17  2018 44_custom
drwxr-xr-x   4 root root  4096 Jan 22 15:41 backup
drwxr-xr-x   2 root root  4096 Jan 22 15:41 bin
drwxr-xr-x   2 root root  4096 Jan 22 16:37 proxifiedScripts
-rw-r--r--   1 root root   483 Jul 17  2018 README
-rw-r--r--   1 root root   206 Jan 22 16:37 .script_sources.txt

```

I just manually edited the Windows 10 grub menuentry - when in grub at boot - to /EFI/VeraCrypt/DcsBoot.efi and I can confirm it also boots fine that way.

> **colorpurple21859 said:**
> What is in your /boot/efi/EFI?
what is the ouput of ```
fdisk -l
```


```
dusf@contraption:~$ sudo fdisk -l
[sudo] password for dusf: 
Disk /dev/loop0: 89.5 MiB, 93835264 bytes, 183272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 93.7 MiB, 98205696 bytes, 191808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 7.5 MiB, 7811072 bytes, 15256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 134509C8-DD29-4256-B479-DCB8771F5F73


Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1230562   1228515 599.9M EFI System
/dev/sda2    1230848   1263615     32768    16M Microsoft reserved
/dev/sda3    1263616 210978815 209715200   100G Microsoft basic data
/dev/sda4  210978816 211900415    921600   450M Windows recovery environment
/dev/sda5  211900416 342878207 130977792  62.5G Linux filesystem
/dev/sda6  342878208 488396799 145518592  69.4G Linux filesystem


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 927AF0D2-1B52-466B-ADEB-894574941E98


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 3907028991 3907026944  1.8T Microsoft basic data


Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BBB14604-211B-2D46-AA3D-9162A99E1410


Device     Start        End    Sectors   Size Type
/dev/sdc1   2048 1953525134 1953523087 931.5G Linux filesystem


Disk /dev/sdd: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AFF53512-C54B-644B-99B1-69BDF4A5D175


Device     Start       End   Sectors   Size Type
/dev/sdd1   2048 625142414 625140367 298.1G Linux filesystem


Disk /dev/mapper/system: 62.5 GiB, 67058532352 bytes, 130973696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/system-boot: 512 MiB, 536870912 bytes, 1048576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/system-swap: 32 GiB, 34359738368 bytes, 67108864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/system-root: 30 GiB, 32157728768 bytes, 62808064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 202.3 MiB, 212099072 bytes, 414256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/veracrypt1: 1.8 TiB, 2000397533184 bytes, 3907026432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x73736572


Device                       Boot      Start        End    Sectors   Size Id Type
/dev/mapper/veracrypt1-part1      1920221984 3736432267 1816210284   866G 72 unkn
/dev/mapper/veracrypt1-part2      1936028192 3889681299 1953653108 931.6G 6c unkn
/dev/mapper/veracrypt1-part3               0          0          0     0B  0 Empt
/dev/mapper/veracrypt1-part4        27722122   27722568        447 223.5K  0 Empt


Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.


Disk /dev/mapper/data: 69.4 GiB, 74503421952 bytes, 145514496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/data-home: 69.4 GiB, 74499227648 bytes, 145506304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/liberty: 931.5 GiB, 1000201723392 bytes, 1953518991 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```


> **colorpurple21859 said:**
> 
AT the grub menu prompt hit c and post the output of ```
set
```


[ATTACH=CONFIG]282285[/ATTACH]
[/QUOTE]

The response is the following, can you please tell me if the loops mounts fdisk displays are normal from following your guide, and confirm that the steps advised will not interfere with my ManualFullSystemEncryption setup?

> **colorpurple21859 said:**
> Are you running ubuntu from a live iso? It appears to be with all the loop mounts. You have an unusual setup, ubuntu grub set normally uses /boot/grub/grub.cfg file not /EFI/ubunut/grub.cfg.
assuming your efi partition is mounted at /boot/efi, run ```
sudo grub-update -o /boot/efi/EFI/ubuntu/grub.cfg.
```
If your efi partition isn't mounted then first mount with ```
sudo mount sda1 /boot/efi
``` If /boot/efi/doesn't exist them creat it with ```
mkdir /boot/efi
``` you will have to this with any update that involves grub changes.

---

### Post by Paddy Landau on 2019-01-23
@dusf This system has not been tested with VeraCrypt.

There is a significant problem in that every time Ubuntu releases a kernel update, it doesn't play nicely, and it overwrites Grub.
That's why we have the script [FONT=lucida console]/usr/local/sbin/refreshgrub[/FONT], to refresh Grub and [FONT=lucida console]initramfs[/FONT] properly.

I don't know enough about Grub to give you sensible advice, sorry.
All I know is that the file [FONT=lucida console]/etc/default/grub[/FONT] is involved.

Maybe, if you figure out what needs doing, you can amend [FONT=lucida console]refreshgrub[/FONT] to implement that?

I don't think that what you are being advised to do will mess up the installation. But, in case I'm wrong, simply back up every file that you change prior to changing it. You can restore the files, if necessary, using a Live CD.

---

### Post by Dáire Fagan on 2019-01-23
Thanks Paddy, I will follow that advice.

And about the loop partitions, are they anything to do with a ManualFullSystemEncryption setup?

Also, is there a way to force the refreshgrub script to run, perhaps by inputting *./usr/local/sbin/refreshgrub* and is it safe to do so?

---

### Post by rmendal on 2019-02-08
Hi Paddy, I've encountered an issue with partitioning the disk and the script. I'm using 18.04.1 LTS and I'm using the entire disk here so I've created the ESP partition, 550 MiB in size, labelled and flagged it per the instructions. The rest of the disk is to be "system" so when I format it as cleared in gparted and apply the change it erases the "system" label which prevents me from using the encryptinstallation script properly as there is no "system" label that it can see so the script just loops asking for my system partition.

Since the partition is marked as clear I cannot add a label to it. I've also tried with fdisk, e2label and tune2fs and the result is the same.

---

### Post by jon54 on 2019-02-23
First off, thank you Paddy for all the work you have put into this.  I find it ridiculous the amount of resistance you have faced in trying to get this implemented.  

I went through your documentation and, like everyone else, ran into the SecureBoot bug.  As it is not an option for me to disable SecureBoot on my dual-boot system, Ubuntu is not usable for me. 

That having been said, is there a good, working guide on installing Ubuntu 18.04 with encrypted root partition and unencrypted boot that works with SecureBoot?  I can set up LUKS and the volume/logical groups and install the OS, it's the post-installation crypttab and grub2 installation that's hanging me up right now.
------------------------------------------------------------------

Okay, I figured it out today (system encryption without boot encryption).  For future reference, here are the steps I took:

First, create your unencrypted boot partition with gparted, use ext4. I used 1GB for mine. 

Follow Paddy's guide through to where you install Ubuntu, and install Ubuntu (select your unencrypted boot partition as /boot).  When it is installed, close the installer (don't reboot!), and CTRL-C the terminal window. 

Remove the logical volume boot (lvremove system-boot) since we created our own unencrypted /boot directory. 

Then you do these things as root (sudo -i):

1.  chroot into the newly installed system
```

mount --bind /dev/ /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /run /mnt/run
mount /dev/<YOUR_BOOT_PARTITION> /mnt/boot
chroot /mnt

```

2.  remove and reinstall grub-pc  (choose to install grub into the unencrypted boot directory you created)
```

apt purge --auto-remove grub-pc
apt install grub-pc
```

3.  create /etc/crypttab  (UUID is the UUID of the filesystem (/dev/sda*) of the physical volume - do NOT use quotes)
```
 system UUID=xxxxx-xxxx-xxxxxx-xxxxxx-xxxxxx none luks,discard,loud 
```

4.  add GRUB_ENABLE_CRYPTODISKS=y to /etc/default/grub (I don't know if this is necessary but I did it anyway)

5.  run update-grub

6.  run update-initramfs

Exit multiple times until you are back at a user account and reboot the system.

---

### Post by mike-freeman-3832 on 2019-03-03
I believe there's an error in section “5.1. Software compatibility” of the wiki page for [ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption").

> 6. Dropbox has terminated support for all Linux systems unless you use unencrypted ext4 or ext4 on plain LUKS. This method uses ext4 and LUKS, but it also uses LVM, so, you won't be able to use Dropbox on your encrypted system.


Dropbox is not incompatible with LVM stacked on LUKS.  Multiple people are reporting that LVM on LUKS works with Dropbox.  If you could please update the page, I think it may save people from needlessly trying to install encrypted systems without using LVM.  Re: [LUKS without LVM (for Dropbox)]("https://www.reddit.com/r/linuxquestions/comments/awcp5f/luks_without_lvm_for_dropbox/").

Thanks.

---

### Post by ralph-bariz on 2019-03-04
Hi,

I tried you procedure and ended up doing stuff manually.

1. modules getting copied via grub.d script was already handled here
2. copying all modules might be a security issue
3. copying grub.cfg to efi partition for sure is a security issue
4. crashed installer of 18.04.2 leaves a broken system requiring to reinstall packages

I ended up doing it manually installing to an unencrypted lvm and copying stuff over to encrypted lvm. I've added a 42_mod doing the copy stuff which i will also modify to only copy needed modules. 

Br
Ralph

---

### Post by Dáire Fagan on 2019-03-04
Paddy, I did sudo apt upgrade, and at one point there was a message about a new version /etc/default/grub being available, but my local version being modified, and I backed up local version to ~, and selected to use the maintainers version. After that there was an error, and when I tried rebooting grub gives the error in the screenshot I am going to paste. Cannot get into recovery either. I also see the commands look different when I press 'e', as per screenshot. 

Can you please tell me how to fix this please?

[ATTACH=CONFIG]282693[/ATTACH]

[ATTACH=CONFIG]282692[/ATTACH]

---

### Post by Dáire Fagan on 2019-03-05
I was hoping maybe it could be fixed with the live USB, maybe running the script, or completing one of the final installation steps to fix grub? 

It took a lot of time to get my system working as it was, even beyond what the guide covered, so if there is anyway to save it so I do not have to wipe everything and start over and you can help me with this I would really, really, appreciate it. [-o

---

### Post by Dáire Fagan on 2019-03-12
I have booted into a 16.04 live USB, and mounted the container containing boot and root. I open in a terminal the dir */media/ubuntu/root/usr/local/sbin* and then input *sudo ./refreshgrub *but this outputs the following error:

```
cp: cannot stat '/boot/grub/x86_64-efi': No such file or directory
Failed to copy boot modules to EFI.
```

Is there a way I can mount this somehow from the live USB so that the script will repair it for me?

---

### Post by Dáire Fagan on 2019-03-12
I have also asked for help here: [16.04: Mount existing boot partition from live USB to repair grub?]("https://ubuntuforums.org/showthread.php?t=2414561&p=13844051#post13844051")

---

### Post by Dáire Fagan on 2019-03-13
So after boot-repair did not resolve the issue, which was not surprising as it is a complex setup, I properly read the description of the [fix-grub.sh]("https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b") script, which is designed to resolve issues when a ManualFullSystemEncryption system fails to boot after upgrade or new installation, and I ran it while logged in from a Live USB. On rebooting, there was now a grub menu again, although with many entries:

[ATTACH=CONFIG]282762[/ATTACH]

None of the Ubuntu entries worked, giving the same or similar errors as before. I contacted the developer of the fix-grub.sh script, and he noticed that I was missing a line from */boot/grub/grub.cfg*, and so for my Ubuntu menuentry, I manually edited the file to now include above [FONT=Arial]the line beginning '*set root=':* [/FONT]
```
[FONT=Arial]cryptomount -u fd9f3d69ea4d40e28f9944cfe0a830[/FONT][FONT=Arial]7c[/FONT]
```

[FONT=Arial]The string in the command after -u is just the UUID of sda5, which in my case contains my system-boot, system-root, and system-swap partitions[/FONT]:

The author of fix-grub.sh also noticed my */etc/default/grub *was missing the following line, so I added it to the end of that file:

```
GRUB_ENABLE_CRYPTODISK=y
```

The top of the file */boot/grub/grub.cfg* warns it should not be edited directly, but I did not know how to edit the config from a Live USB (I am guessing this might be the kind of thing 'chrooting into a system' might allow), so I tried it. As expected, when in grub I pressed e with Ubuntu selected, I could see that the cryptomount -u line was not there, so very carefully I manually typed it in, and thankfully I was prompted for the passphrase and I was able to boot normally at last.

Once logged in I opened */usr/local/sbin/* in a terminal and input

```
sudo ./refreshgrub
```

This seemed to add the *cryptomount -u *line the correct way to all of the Ubuntu entries, recovery etc, in /etc/default/grub.

With everything in grub still working properly on reboot, all that remained was to remove the extra entries boot-repair had added, and I did this by manually removing them with *grub-customizer*, though I discovered the only way to make the changes apply after saving is to run *refreshgrub* again - not *sudo update-grub*.

This issue is now resolved, many thanks to the author of the *fix-grub.sh* script.

---

### Post by pj.connect on 2019-03-18
Hi,

I'm quite a newbe with Linux/Debian/Ubuntu. I'm doing an offline installation of Ubuntu18.04.01 on a laptop with secure boot and UEFI. 

Up until this point, I have successfully modified the encryptinstallation script so it can use offline the TWO other scripts (encryptinstallationchroot and refreshgrub) that needed to be downloaded. I see that the scripts also installs packages (libnotify-bin, yad, incron), so I'm actually proceeding to use apt-offline and modify the scripts so they can use them (packages) offline. 

But I wonder, I see in grubrefresh script that it uses grub-install with --target=x86_64-efi --uefi-secure-boot, but I feel that the boot file used by the computers UEFI/Secure boot wont be properly signed. Checking this will be my next step after using apt-offline.

So! Do I need to download/use grub-efi-amd64 package to ensure that the grub will boot with secure boot, and does the scripts needs to download other packages, scripts or stuff. Help me speed up the process.

UPDATE: The thing is, for the --uefi-secure-boot flag for the grub-install command to work, the grub-efi-amd64-signed package must be installed, and this packages is not included in the ubuntu ISO, and is not downloaded by the encryptioninstallation scripts, and the MKUSB drive does not boot in secure boot, unless one uses the ISO partition (thus not the bios or uefi partitions). My problem is that my box is not only UEFI, but also secure boot (I cannot disable it). Thus, theses scripts seems not to work on hardware with secure boot engaged, unless grub-efi-amd64-signed and dependencies are loaded and installed, which for some reason not yet determined, cannot be installed.

UPDATE 2: I get an "icrontab command does not exists" error in line 142 of encryptioninstallationchroot, even tough I launch encryptioninstallation with sudo on live usb, and even tough I specify root and ubuntu in the /etc/incron.allow before launching encryptioninstallation.

Thanks and Regards

---

### Post by d0006 on 2019-05-07
I am trying to do this manually with no success.
Can anyone state if it matters to mount /dev, /sys, /proc, and /run before or after chroot?
Thanks

---

### Post by Paddy Landau on 2019-05-08
> **d0006 said:**
> Can anyone state if it matters to mount /dev, /sys, /proc, and /run before or after chroot?
They need to be loaded exactly as explained in the instructions.

Unfortunately, all you've said is "with no success", which doesn't give us any clue as to what the problem might be.

I should add that Canonical has just implemented some new patches and fixes to Grub and initramfs, and I don't know whether or not that will affect the process.

---

### Post by d0006 on 2019-05-08
> **Paddy Landau said:**
> They need to be loaded exactly as explained in the instructions.

Unfortunately, all you've said is "with no success", which doesn't give us any clue as to what the problem might be.

I should add that Canonical has just implemented some new patches and fixes to Grub and initramfs, and I don't know whether or not that will affect the process.

Thanks for your reply.

Can anyone list the patches and compatible distros?
I know about this diff for cryptsetup in 18.04:
[https://launchpad.net/ubuntu/+source/cryptsetup/2:2.0.2-1ubuntu1.1](https://launchpad.net/ubuntu/+source/cryptsetup/2:2.0.2-1ubuntu1.1)
[diff from 2:2.0.2-1ubuntu1 to 2:2.0.2-1ubuntu1.1]("http://launchpadlibrarian.net/385008688/cryptsetup_2%3A2.0.2-1ubuntu1_2%3A2.0.2-1ubuntu1.1.diff.gz") (1.1 KiB)
18.10 uses cryptsetup_2.0.2-1ubuntu2                  
I don't recall if there any patches for initramfs.

I have been trying to do this for a long time and I am a little burnt out. I will put together a detailed report and post it on pastebin soon.

BTW: this guy has some good info:
[https://hamy.io/post/0009/how-to-install-luks-encrypted-ubuntu-18.04.x-server-and-enable-remote-unlocking/](https://hamy.io/post/0009/how-to-install-luks-encrypted-ubuntu-18.04.x-server-and-enable-remote-unlocking/)

Thanks

---

### Post by rothen93 on 2019-05-22
Hi, 
thank you very much for your detailed guide! I finally managed to get a fully encrypted installation of Linux Mint 19.1, and want to share a few additional tricks I used (that might be interesting for the troubleshooting section). 

During installation, I faced a system that boots fine without secure boot, but fails to do so if secure boot is enabled. The error appeared after selecting "Ubuntu" in the grub bootloader, message was:
```
error: no such device: <some uuid>
error: no server is specified.
error: you need to load the kernel first.

Press any key to continue...
```
This error is triggered by a bug in the version of grub that ships with Ubuntu 18.04 LTS (including Linux Mint and derivates). Solution is to update grub2 to the newest version (from Ubuntu 19.04 Disco in my case). 
[LIST=1]
[*]Disable secure boot and boot into the system 
[*]Go to [https://packages.ubuntu.com/de/disco/grub2](https://packages.ubuntu.com/de/disco/grub2) and download the "amd64" package. Do the same for these packages: grub2-common, grub-common, grub-gfxpayload-lists, grub-pc, grub-pc-bin. Possibly you'll also need grub-efi-amd64, grub-efi-amd64-bin, grub-efi-amd64-signed. 
[*]Go to the folder where you downloaded the packages and install them (in terminal): sudo dpkg -i *.deb 
[*]Update grub (in terminal): update-grub2 && refreshgrub 
[*]Reboot and enable secure boot again. 
[/LIST]


Next hint: If you want dual boot, install Windows before Linux. Create the partitions, then let Windows do its installation, then create the encrypted drive and install Linux. Reason: Windows installation destroyed my LUKS header and made the partition unusable - Linux needed a fresh installation. 


Best regards
Markus

---

### Post by yrn2 on 2019-05-25
Hi Paddy,
first thank you so much for your hard work with your guide. I finaly thougth to have found the solution for my troubles but unfourtunaly I get stucked in you script at the point were i am asked to enter the drive for the boot partition.
Here I get the following error message:

"I'm having trouble finding the drive's partition table.
Are you sure that it's /dev/nvme0n1?"

In the PC I have three hard drives. 
nvme0n1 - for EFI and the system. The whole drive is used.
nvme1n1 - which later should have all the specialised software to run on. So this will be outside the normal system.
sda - for the data.

All three drives should be encrypted.

Gparted, fdisk and the installer do recognize the disks ant the Partitions... 

I tried just to check the two other disks - any of the partition tables is recognized by your skript. I did follow your instructions to that point, beside the fact that I run Ubuntu 19.04 on that system for installation. Could taht be the reason? I will try 18.04 to be sure.
If its not a problem of the version - Is there a walk around to get past that check? So your script just accept my answer without checking it.

Thank you.
Best regards
Yann

---

### Post by yrn2 on 2019-05-25
Hallo Ich bin es nochmal. anbei die Listung durch gdisk:

GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/nvme0n1: 1000215216 sectors, 476.9 GiB
Model: ADATA SX8200PNP                         
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 5126D6AC-36A8-41F4-A1A6-906D00F82599
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1000215182
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1128447   550.0 MiB   EF00  EFI System Partition
   2         1128448      1000214527   476.4 GiB   8300  system

Vielleicht, kann man den Fehler ja sehen. Ich bin nicht sehr bewandert und weiß mir daher leider nicht zu helfen.

---

### Post by Paddy Landau on 2019-05-26
Hello yrn2

I don't know if it's because of 19.04 instead of 18.04. The other thing is that Canonical has fixed a bug regarding booting in secure mode, and I don't know if that will affect the script!

I'll see what I can do to override the script; I'll post back here later.

---

### Post by Paddy Landau on 2019-05-26
@yrn2

When you get that error with the script, please would you:

[LIST=1]
[*]Press [FONT=lucida console]Ctrl[/FONT]+[FONT=lucida console]C[/FONT] to terminate the script.
[*]Enter the following command into the terminal.
[FONT=lucida console]sudo fdisk --list /dev/nvme0n1[/FONT]
[*]Look for the line that begins with "Disklabel type:"
[*]Let me know what the line reads.
[/LIST]
Thank you

---

### Post by yrn2 on 2019-05-26
Hi Paddy, 
thanks for your quick reply. I did try the Installation via Ubuntu 18.04 TLS. However I did Hit the same Error message. So this is probably not an issue due to the used Version. What was surprising is that my Harddrives did switch in Ubuntu 18.04 so nvme0n1 became nvme1n1 and vice versa.
I will try your request at once and send you te resulats. POlease give me around 30 minutes for that.
Best Regards
Yann

Post scritum:
I will check, that secure mode is off to be sure.

Hi Paddy, restrated the PC wit Ubuntu 19.04. Didn do any changes to the Bios CMS was already disabled. HDs were still like I left them when I wrote u my frist message. 
This time your script went through without any error messages. Right now I am at the point to start the installer.
However I would be pleased if you could help me getting my third Harddrive encrypted and implemented in my system.
Thanks a lot.
I wonder did you change something in the script?
Best regrads Yann

Hi Paddy,
I got through Installation and to restart thecomputer. But I get stuckes in the Boot screen. My Passphrase is not asked however I do get an error messages stating: 
error: no such device: "Device Adress"
error: no server is specified
error: you need to load the kernel first

I will try the grub fixing part to see if that works. And come back to You with the results.
Best Regards
Yann

Unfourtunaly fixing Grub did not do the trick... Now I am at the End of my ideas.
Mybe someone has a clue what the error messages mean.
During the Trouble shooting I did have an uncerteinity:
under 6. Enter something called chroot (don't worry about what it means). typing just chroot gives an error of a missing argument. So i skipped that line and just went on with the rest.
Everything else went through smothely.

Best regards
Yann

---

### Post by yrn2 on 2019-05-26
Hi Paddy,
I restarted the whole procedure with ubuntu 18.04 TLS - this time it  went through and I have a running and encrypted system. I will now try  to update to 19.04 to see if this goes through. if not well, then I  stell can redo all in 18.04. I will let you know of the result. Maybe  other persons have the same issue.
If you could give me some hint how to add my third hard disk in the encrypted system I would be very greatfull.
Best regards 
Yann

---

### Post by yrn2 on 2019-05-26
Hi Paddy, 
I went through update ubuntu 18.10 with any troubles. It went through like a charme. However updating to 19.04 seems to be a major change in grub. So I get stuckes in GRUB version 2.02. I will check if I can make it work like described above by rothen93.
I will keep you updated. 
A list of the configured files that has to be handeled carfully would be much apriciated.
Thanks.
Best regards
Yann

---

### Post by yrn2 on 2019-05-26
Hi so here the final update. 
During Update 18.10 to 19.04 my systemdrive was realocated again... so nvme0n1 became nvme1n1 and vice versa. And during boot up I supose there was a mix up and that was the reason why my system didn't boot anymore. I went through your troubleshooting script.
Now I have a fully encrypted 19.04 running.
Now I just need to add the third Harddrive which is now nvme0n1 :-D
If anyone can give me a hand there that would be grest. Thanks
Bests 
Yann

---

### Post by Paddy Landau on 2019-05-27
@yrn2 Thank you for the update and your feedback.

I suggest that you do **not** upgrade from 18.04 to 19.04. I say this because Canonical treats 18.04 as LTS (long-term support), meaning that Canonical supports it until 2023. But Canonical supports 19.04 only until next year, and then you'll have to upgrade to 19.10, and then to 20.04 (which Canonical will also make LTS, supported until 2025).

Given that I tested this process only on 18.04, and it might stop working on 19.10 and 20.04, this means that you could find that you have problems again with the upgrade to 19.10 or 20.04 (or both).

To add your extra drive, you'll need to go through these steps:

[LIST=1]
[*]Encrypt your extra drive with LUKS.
[*]Add it to [FONT=lucida console]/etc/crypttab[/FONT].
[*]Add it to [FONT=lucida console]/etc/fstab[/FONT].
[/LIST]
For the first two steps, you can look at the script [FONT=lucida console]/usr/local/sbin/encryptinstallation[/FONT] to see how it works.

You might find the the [Arch Linux Full-Disk Encryption Installation Guide]("https://gist.github.com/huntrar/e42aee630bee3295b2c671d098c81268") useful, because it contains some further information. I haven't gone through the guide in detail because I don't have time.

I've started to think that the only practical solution will be for manufacturers themselves to build encryption into the drives at the hardware level.

---

### Post by Franz_Ziereis on 2019-05-30
When I first started mucking around with getting a Windows 10 and Ubuntu 18.04 full system encryption dualboot setup on my HP17 laptop by running 18.04 as the live DVD, it wouldn't allow WiFi. Turning off secure boot remedied the problem.  Still I decided to try the 18.10 version and I got WiFi and secure boot automatically with that live disk. I haven't installed anything yet, still waiting for a model of encryption that suits my skill levels.

I did try something that I read about yesterday, about encrypting Windows with VeraCrypt and then booting a live Ubuntu medium and installing Ubuntu. It sounded reasonable, Ubuntu would overwrite the VC loader and you would use the rescue disk to mount Windows when needed, otherwise a default boot to Ubuntu. The VC encryption went fine but afterward I couldn't boot a live DVD or thumb for the Ubuntu installment and encryption.

I have a "boot from an EFI file" in my UEFI setup (f9) that recognized the 18.10 live thumb drive but, even if it were possible, I had  no clue as to how to navigate the file if it could be booted.

Now I want to try a "something else" installation (after I decrypt Windows partition) and install an encrypted Ubuntu to a separate internal SSD. Before finishing installing, I know that I have to direct the loader to sdb (or whatever it may be). I recall that "something else" allows you to set mount points.  Do I have to install separate unencrypted /EFI and /boot mount points along with intended encrypted /root or a single mount point labeled /boot/EFI or something similar?  

BTW, when I installed VC, I use "system partition" encryption only, not "system full disk", to allow the Windows EFI to accommodate the Ubuntu setup that I'd hoped to install on the Windows drive.

---

### Post by Paddy Landau on 2019-05-31
> **Franz_Ziereis said:**
> … I decided to try the 18.10 version and I got WiFi and secure boot automatically with that live disk.
That's interesting, Franz.
> **Franz_Ziereis said:**
> … encrypting Windows with VeraCrypt
VeraCrypt is an excellent product, but I've never used it to encrypt an operating system. What would happen, I wonder, if you were to use VeraCrypt to encrypt Windows *and* Ubuntu?
> **Franz_Ziereis said:**
> … Before finishing installing, I know that I have to direct the loader to sdb (or whatever it may be).
I don't know quite how it would work with VeraCrypt. Typically, you want to put the bootloader onto your primary drive, so it would usually be [FONT=lucida console]/dev/sda[/FONT], even if Ubuntu goes on [FONT=lucida console]/dev/sdb[/FONT]. That's because Grub has to intercept the boot process before Windows gets hold of it.
> **Franz_Ziereis said:**
> I recall that "something else" allows you to set mount points.  Do I have to install separate unencrypted /EFI and /boot mount points along with intended encrypted /root or a single mount point labeled /boot/EFI or something similar?
The process used in Manual Full System Encryption encrypts everything Ubuntu, including [FONT=lucida console]/boot[/FONT], except for the EFI System Partition. The ESP has to remain unencrypted because the firmware needs to be able to access it prior to decryption.
> **Franz_Ziereis said:**
> BTW, when I installed VC, I use "system partition" encryption only, not "system full disk", to allow the Windows EFI to accommodate the Ubuntu setup that I'd hoped to install on the Windows drive.
Unfortunately, I don't know the details of how VeraCrypt works, so I can't answer this. If you have the time to play, it would be a great experiment to install both Windows and Ubuntu unencrypted, and then use VeraCrypt to encrypt the entire drive, to see what happens. Also, is VeraCrypt compatible with Secure Boot? I'd love to know!

---

### Post by yrn2 on 2019-06-06
Hi Paddy, sorry that I took so long to reply. Thank you a lot for your time and help. I was on a business trip so I didn't have any possibility to get back to you. 
I will go through the steps you told me and keep you informed how it went. Especially the part of having the extra drive mounted directly at boot.

Best Regards
Yann

---

### Post by yrn2 on 2019-06-06
@Franz
Veracrypt was updated to support UEFI full system disk encryption under Windows. I did Encrypt my fuul system disk prior UEFI with TrueCrypt having Windows and Ubuntu installed. When booting Grub started from there you decided which OS to boot. Booting Windows started the trucrypt bootloader. In my knowledge this should now work the same with veracrypt and UEFI. In my setup however I never encrypted Ubuntu. But this might also be possible, with the presented setup by paddy. If you get it to work please let us know.
This link might be helpfull for you.

[https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b](https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b)

Best regards
Yann

Another Point that might be from interest for you, in that setup above I always got rid of the Bootpartition from Windows. Tot do that you have to Partition your Hardrive before installing Windows. Don leave any unused space, that windows could use for it.

---

### Post by airilsra on 2019-06-19
Hi, 

I'm reading the guide. And it mentions that having a separated /home partition is recommended to use the snapshot feature. But in the installation guide I don't see how if users want to have separated /home. I don't think the data partition mentioned in the guide is /home, isn't it?

Edit: I searched through the install script and found out that data partition mention is indeed /home partition. I think it worth to add that detail to the guide, or probably I missed it? Thanks for this great guide Paddy.

---

### Post by peelos on 2019-07-19
Hi Paddy,


Firstly many thanks for this guide, it is really clear and works well for installs on local disks.


I am trying to implement this full disk encryption so that is also loads on a bootable external USB SSD drive and leaves my windows install and EFI partition on the main disk completely untouched.


I am merging your instructions by adding some of the instructions from here: [https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/](https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/)


notably in the chroot environment I am trying to install Grub in a way suitable for a removable device :
sudo chroot /mnt/root
grub-install -d /usr/lib/grub/x86_64-efi --efi-directory=/boot/efi/ --removable /dev/sda


when booting from the external USB SSD I get to the basic command line of grub but the bootloader fails to load.


Do you know how I can resolve this please? feel like I am very close but stuck!


any help very much appreciated


Andrew

---

### Post by Paddy Landau on 2019-07-20
Hello Andrew
> **peelos said:**
> I am trying to implement this full disk encryption so that is also loads on a bootable external USB SSD drive and leaves my windows install and EFI partition on the main disk completely untouched.
Does this mean that you want to create a separate system on your removable drive only? In other words, your removable drive is a system on its own, completely distinct from what's on your computer's hard drive?

If that's the case, I suspect that your problem lies specifying [FONT=lucida console]/dev/sda[/FONT], which might be your computer's hard drive. Please double-check that you have the right drive in the following line.
```
grub-install -d /usr/lib/grub/x86_64-efi --efi-directory=/boot/efi/ --removable **/dev/sda**
```
You should be able to see all the drives, whether SSD, hard or USB, with either Gparted or Disks.

Other people have reported problems with using a removable drive; see [posts #21–27]("https://ubuntuforums.org/showthread.php?t=2399092&p=13798266&viewfull=1#post13798266"). I know that Grub has been updated since I last updated the instructions, and I have not tested the process on a removable drive.

If you manage to resolve this, please post your solution here for others to see.

Thanks

---

### Post by peelos on 2019-07-22
> **Paddy Landau said:**
> Hello Andrew

Does this mean that you want to create a separate system on your removable drive only? In other words, your removable drive is a system on its own, completely distinct from what's on your computer's hard drive?


That is correct Paddy, I am trying to create a separate system on a removable drive that is encrypted.. this solution of yours is the best description online about how to achieve that.

I have now found and followed the instructions that you linked to in advanced settings: [https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/)

I created the drive using mkusb persistent install settings to achieve that.. it now works.. many thanks!

For the record I am only able to boot from the portable drive with secureboot disabled in the BIOS of the machine I am booting it from, but for my purposes this is sufficient.

---

### Post by catman2 on 2019-07-28
> **Paddy Landau said:**
> I have updated the documentation for [Manual Full System Encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"), and vastly simplified it in the process.
If you choose to try it, please let me know (in this thread) if it works for you and if you find any bugs in the documentation or the process.


Its really a very nice piece of documentation and skillfully linked with intro overview and procedure phases, even a troubleshooting section is there. Since when testing it and anything goes wrong, likely internet connection might be gone as well. 

It there any way get an offline copy of this guide, like a pdf or epub I could put on a reader?

---

### Post by Paddy Landau on 2019-07-29
> **catman2 said:**
> It there any way get an offline copy of this guide, like a pdf or epub I could put on a reader?
Sorry, I don't think that the site provides such an option. You can use your browser to "Print" as a PDF, but it works only one webpage at a time, so you'd have to choose which pages to save. You can use a suitable PDF program to merge the pages into a single document; suggestions for this include [FONT=lucida console]pdfchain[/FONT] and [FONT=lucida console]pdfshuffler[/FONT], both available from the standard Universe repositories.

---

### Post by no95typem on 2019-08-05
Hello! Could you tell me please, why is there two enabled key-slots? First (0) slot contains my password, but what about second slot (1)?

---

### Post by NovHak on 2019-09-15
> **no95typem said:**
> Hello! Could you tell me please, why is there two enabled key-slots? First (0) slot contains my password, but what about second slot (1)?
I think the subject has been addressed (see quotation below) : one key is for the first-stage decryption and corresponds to your password, and the other is for the rest and is automatically retrieved during first-stage decryption.
> **Paddy Landau said:**
> [QUOTE=thrdroom;13819593]The script forces me to choose two different  passwords for system and data-drives. As i don’t want to overcomplicate  things(in case of dataloss or crash), i want to have the same password  for both drives and only one single keyfile. I think the user should  have the choice to choose what he want's.
Having the same  passphrase is unnecessary, because once the system has been decrypted,  it will automatically decrypt the data drive. However, if it's really  what you want, all that you need to do is to replace the existing  passphrase with the new one.
```
sudo cryptsetup luksChangeKey /dev/sda3   # Replace /dev/sda3 with the correct partition name.
```[/QUOTE]
I could be wrong however, since I was only reading this out of curiosity and don't intend to use it right now, so I may be missing something...

---

### Post by blaxpot on 2019-09-21
Thanks for this! I found it very helpful while setting up a new install of ubuntu-19.04.


One issue I ran into, however, was that I couldn't seem to get GRUB to open the LUKS volume at boot time. Turns out the LUKS volume was being created as LUKS2 by default, and GRUB doesn't support LUKS2 volumes.


I resolved this by modifying encryptinstallation to force it to use LUKS1:

```
echo -n "${PASSPHRASE}" | sudo cryptsetup luksFormat --type=luks1 --hash=sha512 --key-size=512 --key-file=- ${PARTITION}
```

---

### Post by raif on 2019-10-24
I had this problem too when trying to install with Ubuntu 19.10 on a dual boot system with Windows 10.

The Luks1 tweek above fixed it, though I did get an error about the grub-efi-amd64-signed package not installing that I didn't get before making the tweek, but it didn't hinder booting.

Otherwise great instructions, can't believe Canonical haven't made this the default yet.

---

### Post by Paddy Landau on 2019-10-24
Sorry for not replying to messages earlier. For some reason, Ubuntu Forums doesn't send me notifications to this specific thread until weeks afterwards.

Thank you NovHak, blaxpot and raif for your responses.
> **no95typem said:**
> … why is there two enabled key-slots? First (0) slot contains my password, but what about second slot (1)?
The first passphrase is for your system partition, and the second for your data partition.

---

### Post by ersatz-logins on 2019-12-07
@Paddy -- I just want to join on the well-deserved praise and thanks for all of the effort you've put in to this. It really is tremendous -- I've been using Ubuntu for 12 years now, and this is one of the best, most thorough guides I've seen. Cheers!

I just had the dreaded grub/kernel update causes failure to boot, and the steps in your troubleshooting guide [1] saved my bacon! Phwew, what a huge relief that is! I'm really in awe of the work you've done on all of this!

One minor suggestion on the troubleshooting page -- I wasn't able to get it to work initially, because I wasn't reading carefully enough and the string "PARTITION" is used in two places to mean two things... I kept putting my system partition in the slot where I should have been putting my EFI partition. So my suggestion, which of course you can take or leave, would be to disambiguate those strings in steps 4 and 5 by specifying SYSTEM_PARTITION and EFI_PARTITION, as follows:

4. To unlock your partition, enter the following command. Replace /dev/SYSTEM_PARTITION with your system partition, e.g. /dev/sda5 or /dev/nvme01n1p5. You will be prompted for your system passphrase. 


[LIST]
[*]    sudo cryptsetup open --type=luks /dev/SYSTEM_PARTITION system
[/LIST]
5. Mount your system partition. Replace /dev/EFI_PARTITION with your EFI System Partition (ESP), e.g. /dev/sda2 or /dev/nvme01n1p2. 


[LIST]
[*]    sudo mkdir /mnt/root
    sudo mount /dev/mapper/system-root /mnt/root
    sudo mount /dev/mapper/system-boot /mnt/root/boot
    sudo mount /dev/EFI_PARTITION /mnt/root/boot/efi
[/LIST]

Again, thanks so much! 


[1] [https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)

---

### Post by Paddy Landau on 2019-12-07
> **ersatz-logins said:**
> … disambiguate those strings…
Thanks for kind words and your suggestion. I like your suggestion. I've also bolded the names in [the instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation").

I have a feeling that these instructions won't work on 20.04 (the next LTS). I do wish that Canonical would take this issue seriously!

---

### Post by elgo2 on 2020-01-03
Is the below procedure something I can do once the system has already been encrypted, or do I need to modify Paddy's script beforehand?

Also could you elaborate on > # 3. create an extra passphrase as a back-stop. Enter your passphrase when prompted (3 times) as I don't understand what it's intended for? Do I delete this back-stop passphrase later on (it's not detailed in the steps)?

Also:

> If you'd like to reduce the boot time, repeat steps 1, 4, 6 & 8
it doesn't mention step #3? Step #3 seems to really confuse me! :)

> **3-david-o said:**
> Hi Paddy,
I may have been wrong about the key order (it isnt immediately obvious which key is stored in which slot), and just jumping to conclusions.

Here are the steps that I used to ensure the keys are in the optimum order, and also to adjust the number of iterations done on each key - which influences how quickly the device can be unlocked. The steps are fairly simple and quick, but you do have to enter your passphrase *many* times!

# 1. specify your encrytped device (subtitute your device name)
[FONT=courier new]device=/dev/nvme0n1p5[/FONT]
# 2. check what's in the encyption header - note the iterations for each key
[FONT=courier new]sudo cryptsetup luksDump $device
[/FONT]# 3. create an extra passphrase as a back-stop. Enter your passphrase when prompted (3 times)
[FONT=courier new]sudo cryptsetup --key-slot 7 luksAddKey $device[/FONT]
# 4. delete existing user key slot
[FONT=courier new]sudo cryptsetup luksKillSlot $device 0
[/FONT]# 5. delete existing machine key slot
[FONT=courier new]sudo cryptsetup luksKillSlot $device 1
[/FONT]# 6. Create a new key slot for your passphrase, with required iter-time:
[FONT=courier new]sudo cryptsetup --iter-time 500 --key-slot 0 luksAddKey $device
[/FONT]# 7. Create a new key slot for the machine key,  with required iter-time:
[FONT=courier new]sudo cryptsetup --iter-time 1000 --key-slot 1 luksAddKey $device /etc/crypt.system
[/FONT]# 8. check what's in the encyption header - note the iterations for each key
[FONT=courier new]sudo cryptsetup luksDump $device
[/FONT]# 9. Reboot, and check to see how fast the startup is. 

If you'd like to reduce the boot time, repeat steps 1, 4, 6 & 8, choosing a lower value for iter-time (the iter-time is the amount of time, in milliseconds, that the encryption process spends "hashing" (scrambling) your passphrase before it is stored. It would take the same amount of time to repeat this process each time you decrypt the device - but only if your processor can operate at the same speed during boot. That's not always the case - in my case it was 10 times slower.)
You can also repeat steps 5 & 7, choosing a lower iter-time, to speed up the second part of the boot process, but this will make less of a difference.
When you've finished, you can optionally delete the "back-stop" key in slot 7 (but there's no harm in leaving it).

In my case, I found that an iter-time of 200 for my passphrase gave 185000 iterations, which took about 2 seconds during boot. For the machine key, I found that an iter-time of 1000 gave 900000 iterations, which took about 1 second during boot. The default iter-time is 2000. The relationship between iter-time and number of iterations depends on how fast your machine is. As I mentioned previously, there are potential security implications of reducing the number of iterations, but so long as a sufficiently  long/complex passphrase is used, there's no problem. This topic is well  discussed [here]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#5-security-aspects").

I hope that the above proves to be useful for anyone suffering agonisingly long boot times.

---

### Post by elgo2 on 2020-02-05
Please help!

I must have done something because now I don't get a password prompt on boot, only `grub>` and I get stuck on that. Booting from a LiveCD I can mount the encrypted partitions (boot and root) by entering the password, so they work fine. So something must have gone wrong withe bootloader? Can I fix that without having to reinstall everything again i.e. without losing my current Ubuntu installation?

---

### Post by Paddy Landau on 2020-02-06
@elgo2 — First, which version of Ubuntu are you using? This system has been tested on 18.04 and I don't know if it will work on later versions (it should, but I can't guarantee that).

Second, have you followed the [troubleshooting guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation")?

---

### Post by elgo2 on 2020-02-06
Thank you Paddy! The [troubleshooting guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation") worked perfectly! You are a lifesaver!

Yes, I am using Ubuntu 18.04. The issue arose when I tried to restore a backup done with Timeshift.

NB: As for newer versions of Ubuntu I did try your guide on 19.10 but it didn't work for me.

A question - isn't grub located on /boot and /boot is encrypted - so how does it work prior to me entering the password? Or is there another grub on /efi and that's the grub that I refreshed following your troubleshooting guide?

---

### Post by Paddy Landau on 2020-02-07
> **elgo2 said:**
> A question - isn't grub located on /boot and /boot is encrypted - so how does it work prior to me entering the password? Or is there another grub on /efi and that's the grub that I refreshed following your troubleshooting guide?
I don't know. I created this guide after frustration with the lack of progress from Canonical, by following the advice of several internet-based sources. I'm not really a technical person, so much of what I did was just trail and error, and I understand barely anything about how Grub works.

---

### Post by elgo2 on 2020-02-08
> **Paddy Landau said:**
> I don't know. I created this guide after frustration with the lack of progress from Canonical, by following the advice of several internet-based sources. I'm not really a technical person, so much of what I did was just trail and error, and I understand barely anything about how Grub works.

Do you know if there is a way we can suggest (petition) this feature to Canonical?

Another question - I have /home on a separate partition from /boot and /root. In case I need reinstall Ubuntu (which will format the partition) is there a way to leave the /home partition untouched? I would think I would need to preserve the keyfile, but how would I tell your script not to format /home and use an existing keyfile?

---

### Post by Paddy Landau on 2020-02-08
> **elgo2 said:**
> Do you know if there is a way we can suggest (petition) this feature to Canonical?
The main document lists four bug reports under [Important Notes]("https://help.ubuntu.com/community/ManualFullSystemEncryption#Important_notes_.2BIBQ_Please_read_first.21") > Bug requests. You can vote for the reports. For each report:

[LIST]
[*]Go to the bug report.
[*]Log in (top-right corner) if not already logged in.
[*]Press on the green writing that says, "This bug affects *nn* people. Does this bug affect you?", and select "Yes, it affects me".
[/LIST]
Other than that, I'm unsure how else you can raise this to Canonical. If we can get many people to vote on the reports, it will raise their profile (the "bug heat", as shown by the little fire symbol on the right-hand side). I find it baffling that Canonical is trying to make money from selling their services for Ubuntu to businesses, but they treat fundamental security with an apathetic attitude.
> **elgo2 said:**
> I have /home on a separate partition from /boot and /root. In case I need reinstall Ubuntu (which will format the partition) is there a way to leave the /home partition untouched? I would think I would need to preserve the keyfile, but how would I tell your script not to format /home and use an existing keyfile?
It is possible. **Warning:** I haven't tested this, so please back up your home partition in case of problems! (You should be backing up your home partition anyway on a regular basis.)

**EDIT: As reported by @elgo2, this won't work!**

[LIST=1]
[*]Boot from a Live CD.
[*]Unlock your partitions as explained in [Computer fails to boot after upgrade or new installation]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation"), steps 1&#8211;5 only.
[*]Delete all files on your root with the following command.
```
rm --one-file-system --recursive /mnt/root
```
[*]Follow the [Ubuntu installation instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu").
[*]Continue with [Fix broken pieces]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces").
[*]Complete [Check and finalise]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessCheckAndFinalise").
[/LIST]
I repeat that I haven't tested this, so I can't guarantee that it will work.

---

### Post by elgo2 on 2020-02-08
> **Paddy Landau said:**
> The main document lists four bug reports under [Important Notes]("https://help.ubuntu.com/community/ManualFullSystemEncryption#Important_notes_.2BIBQ_Please_read_first.21") > Bug requests. You can vote for the reports. For each report:

[LIST]
[*]Go to the bug report. 
[*]Log in (top-right corner) if not already logged in. 
[*]Press on the green writing that says, "This bug affects *nn* people. Does this bug affect you?", and select "Yes, it affects me". 
[/LIST]
Other than that, I'm unsure how else you can raise this to Canonical. If we can get many people to vote on the reports, it will raise their profile (the "bug heat", as shown by the little fire symbol on the right-hand side). I find it baffling that Canonical is trying to make money from selling their services for Ubuntu to businesses, but they treat fundamental security with an apathetic attitude.

Perhaps they provide a "secure" version to businesses?

I gave my vote on all 4 bugs.

But maybe we should start a petition to request a "true" Full Disk Encryption from Canonical. I believe it would have a higher impact since it would be easier for people to vote and more people would vote.

> **Paddy Landau said:**
> It is possible. **Warning:** I haven't tested this, so please back up your home partition in case of problems! (You should be backing up your home partition anyway on a regular basis.)

[LIST=1]
[*]Boot from a Live CD. 
[*]Unlock your partitions as explained in [Computer fails to boot after upgrade or new installation]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation"), steps 1&#8211;5 only. 
[*]Delete all files on your root with the following command.
```
rm --one-file-system --recursive /mnt/root
``` 
[*]Follow the [Ubuntu installation instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu"). 
[*]Continue with [Fix broken pieces]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces"). 
[*]Complete [Check and finalise]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessCheckAndFinalise"). 
[/LIST]
I repeat that I haven't tested this, so I can't guarantee that it will work.

A couple of things that I'm missing...

1. How do I continue with [Fix broken pieces]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces")? If I run your script it would start from the beginning - i.e. asking for passwords, partitions, etc.? Do I start it with some parameter that tells it to skip the initial part?

2. How would /home be auto-mounted? Wouldn't it need the current keyfile for that? So do I have to backup the current keyfile and then copy it to the newly installed Ubuntu on /root?

---

### Post by Paddy Landau on 2020-02-09
> **elgo2 said:**
> But maybe we should start a petition to request a "true" Full Disk Encryption from Canonical. I believe it would have a higher impact since it would be easier for people to vote and more people would vote.
Nice idea, but I wouldn't know how to do that. Also, as Canonical is a private company based in the UK, they can just ignore petitions, and it's not possible to put shareholder pressure on them.

If you have a good idea of how to get Canonical to take this issue seriously, I'd love to hear.

The only option that Canonical currently supports is full-disk encryption, which means erasing *everything else* on the hard drive, including Windows. It also means, as far as I understand, that reinstalling Ubuntu without wiping your home folder isn't possible. It also doesn't encrypt boot.
> **elgo2 said:**
> 1. How do I continue with [Fix broken pieces]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces")? If I run your script it would start from the beginning - i.e. asking for passwords, partitions, etc.? Do I start it with some parameter that tells it to skip the initial part?
2. How would /home be auto-mounted? Wouldn't it need the current keyfile for that? So do I have to backup the current keyfile and then copy it to the newly installed Ubuntu on /root?
Ah, yes, you're absolutely correct. I missed that. My bad, sorry.

I've been looking at the script. I tried to figure out a workaround for this, but it would be awfully complex. I think that you'd have to manually follow the process, which (as warned in the documentation) is only for advanced people; specifically, for people who thoroughly understand both LUKS and LVM.

If this is not you, your best way forward is to reinstall afresh, and then restore your home folder from your backups.

Sorry that I can't be of better help.

---

### Post by elgo2 on 2020-02-11
I could create a petition that asks Canonical to create FDE that includes /boot and works with Secure Boot. That's a start and should be fairly easy for them to implement. Here's an [example discussion]("https://discourse.ubuntu.com/t/can-we-get-real-full-disk-encryption/8802"). Any suggestions on the wording of the petition - i.e. is what I said technically correct and specific enough?

---

### Post by Paddy Landau on 2020-02-18
> **elgo2 said:**
> I could create a petition that asks Canonical to create FDE that includes /boot and works with Secure Boot. That's a start and should be fairly easy for them to implement. Here's an [example discussion]("https://discourse.ubuntu.com/t/can-we-get-real-full-disk-encryption/8802"). Any suggestions on the wording of the petition - i.e. is what I said technically correct and specific enough?
For some reason, Ubuntu Forums frequently fails to notify me of new posts, so sorry that I'm responding only now.

I am feeling somewhat disillusioned, because every time that this issue is raised on the official channel, some person comes in and says that full-disk encryption is not worthwhile because there are some ways to hack a system. The argument makes no sense.

Here is a suggestion, but please feel free to amend as you see fit.
____________________________________

**Title**

Ubuntu needs full-system encryption plus Secure Boot that doesn't interfere with existing partitions (e.g. Windows)

**Body**

Today's malware, regulations including GDPR, and threat of lawsuits and fines require the best security available to business large and small, governments, NGOs and other organisations, and to individuals. As we have seen in the news more than once, losing an unencrypted laptop or having its operating system unencrypted (even when data is encrypted) can have severe consequences.

Ubuntu needs to step up to the challenge by encrypting not just the data partition but also the operating system. It should look at encrypting as much as is possible, including /boot. Secure Boot should be supported as an integral part of this.

The instructions at the following link offer proof-of-concept.
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

The entire Ubuntu system, including swap (if used), root, /home and /boot, is held on a single LUKS-encrypted partition using LVM. (The system can be modified to allow multiple logical partitions and physical disks, whether or not joined with LVM.) It even permits hibernation. This creates a powerful level of encryption. Only the EFI System Partition (ESP) is left unencrypted for obvious reasons.

This system respects other already-existing systems such as Windows, and does not overwrite them.

This proof of concept shows that nothing prevents this from being done. By including this by default into the standard Ubuntu installation, Canonical will be able to boast one of the most secure implementations of an operating system, using Secure Boot and full encryption of everything.

Understandably, the ESP cannot be encrypted, but that is the whole point of using Secure Boot to mitigate that problem.

Some people have argued that because ESP is unencrypted, that means that there is no point in encrypting anything, but that is a spurious argument with no merit (otherwise no one would bother to encrypt anything) and an argument that regulators, among others, would dismiss out of hand.

---

### Post by Dáire Fagan on 2020-03-13
Paddy, I would love if I could use Gnome 3.2 with this setup, not least because alt+tab for me very often freezes my system, but I understand with 18.04 we are locked in to 3.28.2 with this setup. 

There is a work around here: [How to install gnome 3.29.92 or 3.30 in Ubuntu 18.04?]("https://askubuntu.com/questions/1072096/how-to-install-gnome-3-29-92-or-3-30-in-ubuntu-18-04") 

I am hesitant to implement that just yet in case it breaks something not easily reversible.

Have you any plans to update your script and guide so that it supports a more recent version of Ubuntu, and if you do, will you provide a script that allows those of us who have already followed it to setup 18.04 to upgrade?

---

### Post by Paddy Landau on 2020-04-17
Jernej Jakob has created instructions to [convert an unencrypted installation to an encrypted one]("https://github.com/jjakob/wiki/wiki/Migrating-an-unencrypted-PureOS-Debian-install-to-fully-encrypted"). I have not tested it, but Jernej says that it works on Ubuntu. I have amended the first post to include this information.

---

### Post by EuclideanCoffee on 2020-04-17
Thank you for sharing this. I will be testing this soon.

---

### Post by Paddy Landau on 2020-04-18
Yet another alternative, which looks promising. If you try it, please report back on this [alternative how-to by Tj]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019"). I have also added this to the first post.

---

### Post by metal450 on 2020-05-16
Just gave this a try on Kubuntu 20.04.  The steps were all perfectly clear, no confusion or hangups anywhere.  The only differences from the instructions were that the script didn't auto-launch the installer (I launched it by hand), and the installer didn't have any errors at the end (i.e. no warning about the grub installation failure, no crash, no error report).

Unfortunately though, it didn't work.  I tried it thrice, completely from scratch, just to make SURE I didn't do anything wrong.  After finishing the 2nd part of the script & rebooting, I never saw the "EFI screen" mentioned on [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessCheckAndFinalise](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessCheckAndFinalise).  Instead, it went straight to "OS selection prompt" (aka the grub menu).  Selecting the Ubuntu entry shows "error: no such device: xxxxx."

I tried the troubleshooting steps (refreshgrub), but it didn't change anything.

---

### Post by metal450 on 2020-05-16
Solved it.  You just need to add --type=luks1 to the invocation of cryptsetup luksFormat.

The clue came from [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

[I]"The default LUKS (Linux Unified Key Setup) format used by the **cryptsetup** tool has changed since the release of 18.04 Bionic. 18.04 used version 1 ("**luks1**") but more recent Ubuntu releases default to version 2 ("**luks2**").  GRUB only supports version 1 so we have to be explicit in the commands  we use or else GRUB will not be able to install to, or unlock, the  encrypted device. "

[/I]Also, you might consider merging the changes from here, which allows you to use btrfs instead of ext4: [https://github.com/sgebbie/encryptinstallation.btrfs](https://github.com/sgebbie/encryptinstallation.btrfs)

---

### Post by Paddy Landau on 2020-05-17
@metal450 &#8212; Thank you for this! I've included your page in [the notes]("https://help.ubuntu.com/community/ManualFullSystemEncryption"). If only Canonical took encryption seriously, it would save all this hassle!

---

### Post by metal450 on 2020-05-18
I agree. It's completely absurd that it's so difficult & time-consuming to do something that should be so simple, and that they've known about for literally years & years...

---

### Post by metal450 on 2020-05-21
So I just installed a new kernel, & refreshgrub always reports: 

> 
update-initramfs: Generating /boot/initrd.img-5.4.0-26-generic
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.4.0-26-generic with 1.
Failed to prepare initrafms.
refreshgrub: Grub update failed
Grub update failed.

Please do not restart or shut down until you have manually run the following command, even if the Software Updater asks you restart.

sudo refreshgrub

I've run it like 10 times. It always fails. And the message makes me afraid to reboot.  What should I do?

---

### Post by metal450 on 2020-05-22
Solved.  Apparently that's what it does when /boot fills up (so you need to remove old kernels).  Perhaps a user-friendly message about why it failed & how to solve? :)

---

### Post by Paddy Landau on 2020-05-22
> **metal450 said:**
> Solved.  Apparently that's what it does when /boot fills up (so you need to remove old kernels).  Perhaps a user-friendly message about why it failed & how to solve? :)
Thanks for posting the solution. How large is your [FONT=lucida console]/boot[/FONT] partition? Ideally, it should be at least 500Mb (½Gb).

---

### Post by sudodus on 2020-05-25
Hi Paddy,

Have you noticed that the installer Calamares in Lubuntu 20.04 LTS can create a system with 'encrypted disk' without any unencrypted boot partition? I suggest that you test it and let us know what you think about it (in comparison to your system).

At [this link](https://discourse.lubuntu.me/t/fresh-lubuntu-20-04-with-encrypted-disk-boot-takes-its-time/1204) there is a discussion and description of the Lubuntu encrypted disk.

---

### Post by metal450 on 2020-06-10
> **Paddy Landau said:**
> Thanks for posting the solution. How large is your [FONT=lucida console]/boot[/FONT] partition? Ideally, it should be at least 500Mb (½Gb).

df -h shows 488M. It was created automatically by this script - I didn't manually change it. Looks like the script does:

setUpLogicalVolume Boot boot system 512M    # Create /boot.

---

### Post by metal450 on 2020-06-10
Question: when using this form of /boot encryption, rebooting is agonizingly slow - easily an order of magnitude slower than "normal" encryption (ie. encrypting just /, but not /boot).  I understand that this is because grub doesn't have any hardware optimization at all, and so it takes forever to do the encryption with grub.  I also dual boot with Windows (encrypted via VeraCrypt) & Linux.  Booting into Linux takes ten times longer than Windows.  Is there no way to improve this, or is it just a choice between "unencrypted /boot," or "rebooting takes forever?"

---

### Post by Paddy Landau on 2020-06-11
> **metal450 said:**
> df -h shows 488M. It was created automatically by this script - I didn't manually change it. Looks like the script does:
setUpLogicalVolume Boot boot system 512M    # Create /boot.
That's interesting. Default Ubuntu updates automatically remove older kernels, so it should have been dealt with.

---

### Post by Paddy Landau on 2020-06-11
> **metal450 said:**
> when using this form of /boot encryption, rebooting is agonizingly slow…
I didn't get this problem during my tests, so I can't comment on what's happening with you. Unless there is a clash between VeraCrypt and Grub? I've never used VeraCrypt for an operating system, so I don't know how it works.

As you are using VeraCrypt, have you considered using it as the encryption method for Linux? It's something that's worth testing, and if I get some time, I'll test it myself.

---

### Post by metal450 on 2020-06-11
> **Paddy Landau said:**
> That's interesting. Default Ubuntu updates automatically remove older kernels, so it should have been dealt with.

I was having driver compatibility issues, so I installed some other ones myself.

---

### Post by metal450 on 2020-06-11
> **Paddy Landau said:**
> I didn't get this problem during my tests, so I can't comment on what's happening with you. Unless there is a clash between VeraCrypt and Grub? I've never used VeraCrypt for an operating system, so I don't know how it works.

As you are using VeraCrypt, have you considered using it as the encryption method for Linux? It's something that's worth testing, and if I get some time, I'll test it myself.

Nope, definitely not a clash - this is just the amount of time taken for grub to decrypt, which I've since read about all over the web. Apparently grub's encryption implementation is extremely un-optimized & slow.  Bummer.

I did some research about using VeraCrypt vs LUKS on Linux, & the conclusion I came to was that LUKS is the better approach, since it's kernel/native, widely supported, and much faster.  Reference: [https://superuser.com/questions/1019673/how-would-i-encrypt-my-whole-linux-filesystem-with-veracrypt](https://superuser.com/questions/1019673/how-would-i-encrypt-my-whole-linux-filesystem-with-veracrypt)

---

### Post by metal450 on 2020-06-14
Question: on boot, I keep seeing the message:

     ln /tmp/mountroot-fail-hooks.d//scripts/init-remount/lvm2: no such file or directory
        Volume group "system" not found
        Cannot process volume group system

Is that related to this script?  Everything seems to be working otherwise.

---

### Post by thrdroom on 2020-09-20
> **metal450 said:**
> So I just installed a new kernel, & refreshgrub always reports: 



I've run it like 10 times. It always fails. And the message makes me afraid to reboot.  What should I do?

Im having the same problem, like metal450. But freeing up the /boot/ partition by removing old kernels did not help. What should i do?

> $ sudo refreshgrub
refreshgrub: Grub update required
Grub update will be done automatically.

Do not restart or shut down until you receive another message telling you that this has been done, even if the Software Updater asks you restart.

Depending on your system, it could take several minutes.
                                                                                
                                                                               
refreshgrub: Grub update will be done automatically.\n\nDo not restart or shut down until you receive another message telling you that this has been done, even if the Software Updater asks you restart.\n\nDepending on your system, it could take several minutes.
                                                                               
x86_64-efi wird für Ihre Plattform installiert.
Could not delete variable: Invalid argument
grub-install: error: efibootmgr failed to register the boot entry: Block device required.
Failed to reinstall Grub.
refreshgrub: Grub update failed
Grub update failed.

Please do not restart or shut down until you have manually run the following command, even if the Software Updater asks you restart.

sudo refreshgrub
                                                                                
refreshgrub: Grub update failed.\n\nPlease do not restart or shut down until you have manually run the following command, even if the Software Updater asks you restart.\n\nsudo refreshgrub


@Paddy
How should one uninstall/remove your script "Manual Full System Encryption"? Are there uninstall instructions?
How should one transition from your method "Manual Full System Encryption" script to [TJ's method?]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019")

Thanks in advance

---

### Post by Dáire Fagan on 2020-09-20
I'm on my phone so I will have to format properly another time.

Not sure if it will help you or not but when I was still using this setup and ran into issues booting running this fix-grub.sh script from a live USB saved me a few times: [https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b](https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b)

Further, I considered Tj's setup but then I found this: Ubuntu 20.04 with btrfs-luks full disk encryption including /boot and auto-apt snapshots with Timeshift

[https://mutschler.eu/linux/install-guides/ubuntu-btrfs/](https://mutschler.eu/linux/install-guides/ubuntu-btrfs/)

This setup is way forward. Ignore the swap partition and just set up the swap file so you can resume from hibernate or suspend-then-hiberbate. I have not managed to set up true hybrid suspend, or suspend-and-hibernate yet.

Warning: I tried this first on Ubuntu Mate 20.04.1 but restoring timeshift snapshots broke things. It works perfectly with Ubuntu 20.04.1

As far as I know the guide is based on HOWTO - GPT/UEFI install with full disk encryption: BTRFSonLUKS with separate root, home and pkg subvolumes; hibernation with a swapfile; auto-snapshots with easy system rollback (GUI); boot into snapshots

[https://forum.endeavouros.com/t/howto-gpt-uefi-install-with-full-disk-encryption-btrfsonluks-with-separate-root-home-and-pkg-subvolumes-hibernation-with-a-swapfile-auto-snapshots-with-easy-system-rollback-gui-boot-into-snapshots/3782](https://forum.endeavouros.com/t/howto-gpt-uefi-install-with-full-disk-encryption-btrfsonluks-with-separate-root-home-and-pkg-subvolumes-hibernation-with-a-swapfile-auto-snapshots-with-easy-system-rollback-gui-boot-into-snapshots/3782)

---

### Post by Paddy Landau on 2020-09-21
I can't understand why I don't get notifications for posts on this thread.

Sorry for not having replied sooner &#8212; I only now got a notification for posts on this thread since I last posted.
> **metal450 said:**
> Question: on boot, I keep seeing the message: &#8230;
This is quite an old post. Did you resolve your problem?
> **thrdroom said:**
> How should one uninstall/remove your script "Manual Full System Encryption"? Are there uninstall instructions?
It's not something that you can uninstall. It's how you installed your Ubuntu system, not an add-on after installation.
> **thrdroom said:**
> How should one transition from your method "Manual Full System Encryption" script to [TJ's method?]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019")
The best way is to ensure that your backups are fully up-to-date, and then reinstall from scratch. It's a pain, I know, but converting would probably drive you crazy and take a week. While you're about it, I would instead go for the method that [@dusf pointed to]("https://ubuntuforums.org/showthread.php?t=2399092&page=8&p=13987675&viewfull=1#post13987675").
> **dusf said:**
> &#8230; I found this: Ubuntu 20.04 with btrfs-luks full disk encryption including /boot and auto-apt snapshots with Timeshift
[https://mutschler.eu/linux/install-guides/ubuntu-btrfs/](https://mutschler.eu/linux/install-guides/ubuntu-btrfs/)
That's excellent, as it's updated to version 20.04. Thank you. I have put both of your links into the current instructions.

---

### Post by arcticbox on 2020-12-16
I followed the guide and was met with success (thank you so much!).  There are however a few things I had to change in the refreshgrub script  before automatic refreshgrub notifications would work (at least for me,  using Kubuntu 20.04.1).

```

# The line:
    w --short --no-header            |
# had to be changed to:
    PROCPS_USERLEN=32 w --short --no-header            |

```
This is because w truncates my username to 8 characters. The replacement   line will still truncate to 32 characters, so consider using `who`   instead if that works. The FROM column of the w command (containing the user's display) is also potentially truncated (defaults to 16 in my case), but in practice it might not make any difference.

```

# The line:
        DISPLAY=${WHODISPLAY} sudo --user=${WHOUSER} notify-send  --urgency=critical --icon=${MESSAGE_TYPE} "refreshgrub: ${TITLE}" "$(  date +'%F %T' )\n\n${MESSAGE}" 2>/dev/null
# had to be changed to the following:
        DISPLAY=${WHODISPLAY} su ${WHOUSER} -c "notify-send  --urgency=critical --icon=${MESSAGE_TYPE} \"refreshgrub: ${TITLE}\" \"$(  date +'%F %T' )\n\n${MESSAGE}\""  2>/dev/null &

```
This is because for me, notify-send invoked as another user with sudo will fail after hanging for a minute, but it seems to work fine with su. I also  added  a & at the end so that any such hangs by notify-send would  not  cause the entire script to pause at that point.

---

### Post by Paddy Landau on 2020-12-17
Thank you for the report, @arcticbox.
> **arcticbox said:**
> ```
PROCPS_USERLEN=32 ...
```
You have a long username! I've made this change as you suggest.

For future note, some systems and apps limit the username to a shorter length, so for safety, you might want to stick to 8 characters for the username.
> **arcticbox said:**
> ```
DISPLAY=${WHODISPLAY} ...
```
Something has definitely changed. In fact, on my machine, I get problematic results with both types.

In any case, I've changed the line as you suggest (with a couple of minor modifications), and applied the same change to the following line to be consistent.

---

### Post by EuclideanCoffee on 2020-12-28
Why is encryptinstallation located on DropBox rather than Ubuntu PPA or GitHub? If you need these resources, I could provide them. I think a PPA would likely be easier to implement... also sudo wget command is not a good solution. You should only run wget in non-elevated environments.

[https://tserong.github.io/sudo-wget/](https://tserong.github.io/sudo-wget/)

I'll be happy to help out here. It's not a problem. Please just let me know if you prefer PPA or GitHub. And also please explain why it's a DropBox link (perhaps legal issue, I can write new source then to comply with legal if needed).

---

### Post by arcticbox on 2021-01-14
> **Paddy Landau said:**
> You have a long username! I've made this change as you suggest.
...
In any case, I've changed the line as you suggest (with a couple of minor modifications), and applied the same change to the following line to be consistent.

My username isn't *quite* that long, 32 is just the largest value it will accept. In any case, thank you for keeping the script up-to-date!

One other thing I've run into:
So the script created a Volume Group with two volumes, /dev/system/boot and /dev/system/root. Unfortunately, I'm finding 512 MiB is not large enough for /dev/system/boot. Nowadays I get an error from refreshgrub because it runs out of space when it hits 4 kernels. At first, it was enough to run `sudo apt autoremove` to clear out my old kernels, but now that isn't working, so I have to manually uninstall the old kernels before refreshgrub can run successfully. (Or I don't know, maybe 512 MiB *is* supposed to big enough but some automatic cleanup of old kernels isn't working as intended on my system? Who knows.)

---

### Post by Paddy Landau on 2021-01-15
I don't know why this thread often fails to send me notifications of new posts.

I've only just seen your post, so sorry for the tardy reply.
> **EuclideanCoffee said:**
> Why is encryptinstallation located on DropBox rather than Ubuntu PPA or GitHub? … explain why it's a DropBox link (perhaps legal issue…)
Because I've tried to use Github and  failed. I have no clue how to use Ubuntu PPA (I've tried to understand, but I'm not clever enough). There's no legal issue; the code is all 100% FOSS.
> **EuclideanCoffee said:**
> If you need these resources, I could provide them.
Yes, please! I would be immensely grateful.
> **EuclideanCoffee said:**
> … let me know if you prefer PPA or GitHub.
I will take your advice on this, because I'm the opposite of an expert :)

---

### Post by Paddy Landau on 2021-01-15
> **arcticbox said:**
> Unfortunately, I'm finding 512 MiB is not large enough for /dev/system/boot.
Hmm, 512Kb was supposed to be enough. The system uses LVM, which means that it should be reasonably easy to expand /boot. Unfortunately, I no longer remember how to use LVM, but the process would be as follows.

[LIST=1]
[*]Shrink /root by the required amount. That will leave unused space.
[*]Tell LVM to expand /boot into the freed space. One of the huge advantages of LVM is that a logical partition doesn't need to be contiguous, so this should work, unless I've misunderstood something.
[/LIST]
Unfortunately, I'm currently massively overwhelmed with "life" matters, so I don't have any time to look up how to do this or to test it before posting this, sorry.

---

### Post by Paddy Landau on 2021-01-15
I should add to this thread that by the time we get to Ubuntu 22.04 (the next LTS release), the system will probably (again) fail without further fixing.

As computers become more powerful, I have started to recommend an alternative route. I've done this with my new computer:

[LIST]
[*]Install Ubuntu using the default method to erase the entire disk. That means that you do **not** have dual-boot.
[*]Install other operating systems as required in virtual machines. I've installed Windows in VirtualBox. If your computer came with Windows, you'd use the Windows license key that came with the computer (usually provided with a sticker on the rear of the computer).
[/LIST]
The disadvantages are:

[LIST]
[*] if you started to use Windows before installing Ubuntu, you'd have to back up and restore your entire Windows data.
[*]This doesn't work on older computers; you need a modern computer with at least 16Gb. (Mine copes well with 16Gb, but I hardly use Windows.)
[/LIST]

---

### Post by keen36 on 2021-10-16
Hi,

first of all, let me thank you, Paddy, for providing this amazing guide and for the free and enduring support you provide to everyone! People like you are what makes the open source community great.

Let me provide some information about my usage of this system. I just checked and apparently I have been using this setup since December 2018. This is a Linux Mint Cinnamon installation which has been upgraded a few times over the years, running by now version 20.2 (current stable). I dual-boot with Windows 10 for gaming. 

During those years, there were two or three times when I was greeted with a grub console during boot and had to follow the troubleshooting instructions to re-setup grub. This worked without a hitch every time. One time occured when my boot partition was full (Linux Mint's updater had been configured to purge old kernels, but something had gone wrong there, I don't remember) and the script had failed because of that. Normally I would notice such a failure and clean up boot and rerun the script, but on that occasion I didn't. I think maybe there was a shutdown scheduled while I was asleep or maybe my girlfriend turned off the machine while I wasn't there, in any case: the troubleshooting instructions worked, as always. Since there is so much typing involved in that process, I thought about writing a script to automate it, but it happened so rarely that I was never motivated enough to do it. Luckily, skimming over this thread, I saw this:
[https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b](https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b)
I am now happy that I did not spend time to write it, because my script surely would not have been as good as that one c:    - Thanks, Lovro!  

I made some changes to my setup, too. When I added a new hdd, I returned here to find out how to generate another keyfile for it and how to set everything up in fstab and cryptfs so the new drive gets decrypted and mounted during boot, like the others. I resized the swap partition and later moved swap into a swap file on the encrypted LVM. A short while ago, I configured the swap file to use a random key generated at boot. I know that this is paranoid, but if we weren't paranoid, we would all not be here ;)

This brings me to the other reason (besides delivering a long overdue thank you) for my post: For a while now (possibly because of one or more of those changes listed above), I have had the problem that sometimes I was being greeted by the "Grub has been updated successfully, be advised to reboot" notification directly after booting up. A minor annoyance, but an annoyance nonetheless. Recently I have been getting both of refreshgrub's notifications reliably after every boot and after every resume from suspend. This made me look into how things actually work under the hood, which added another thing to the long list of things I learned about while using this setup: icron. What an amazing tool! Anyway: using systemd's (also amazing) journalctl I saw the IN_MODIFY event for /boot being fired for all the files in /boot/efi/efi/ubuntu/ on every boot and resume. This triggered refreshgrub needlessly. I have found a way to avoid this annoyance, and in case someone else has that problem, here is something you can try:

**DISCLAIMER:** Try this at your own risk, I am not responsible for nuclear war or refreshgrub not working etc.
Follow these instructions only if 
[LIST]
[*]you have the same problem (unnecessary refreshgrub notifications after boot or resume) 
[*]you do not use incron for other purposes 
[*]you have no problem following the troubleshooting instructions from the guide in case something goes wrong with refreshgrub 
[/LIST]

First, I configured the incron service to start its daemon only after boot is mounted:
[LIST]
[*]Add After and BindsTo directives 
[*]After -> Start only after boot.mount unit 
[*]BindsTo -> Stop when boot.mount unit stops 
[/LIST]
 /lib/systemd/system/incron.service
```
[Unit]
Description=file system events scheduler
Documentation=man:incrond(8)
After=boot.mount
BindsTo=boot.mount

[Service]
Type=forking
PIDFile=/run/incrond.pid
ExecStart=/usr/sbin/incrond

PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

After this, no notifications are sent following a cold boot. To fix the notifications upon resume:
[LIST]
[*]Add another service 
[*]This one stops the incron service before suspend and resumes after resume 
[*]The - in front of the command makes the unit register success even on fail exit codes 
[/LIST]
 /etc/systemd/system/icronsuspendresume.service
```
[Unit]
Before=sleep.target
StopWhenUnneeded=yes
[Service]
Type=oneshot
StandardOutput=syslog
RemainAfterExit=yes
ExecStart=-/bin/systemctl stop incron
ExecStop=-/bin/systemctl start incron
[Install]
WantedBy=sleep.target
```

Refer to these for more information:
[man page for systemd explaining unit options]("https://www.freedesktop.org/software/systemd/man/systemd.unit.html#%5BUnit%5D%20Section%20Options")
[URL="https://unix.stackexchange.com/questions/619987/stop-systemd-service-before-suspend-start-again-after-resume"]The suspend/resume service was inspired by this post
[/URL]
It may very well be that I am the only one that has this problem, possibly because I have some misconfiguration or because of some quirk of my ever-changing setup. I am also quite confident that the way I fixed it is not ideal and there must be a better one. But, even if both of these are true, this post still serves its most important purpose: to deliver a well-earned and very overdue thanks.

---

### Post by Paddy Landau on 2021-10-17
> **keen36 said:**
> Let me provide some information about my usage of this system…
This is fantastic first post :)!

Thank you so much for this information.

I was unaware of Lovro Mažgon's contribution, so I'll add it to the instructions (assuming that I can log in — the login process tends to fail an awful lot).

As mentioned before and in the [instructions for future versions]("https://help.ubuntu.com/community/ManualFullSystemEncryption#Future_versions_of_Ubuntu"), this system has passed its prime and will most likely be unsuitable to use in future.
> **keen36 said:**
> … another thing to the long list of things I learned about while using this setup: icron.
Linux is filled with amazing functions. In case you don't already know them, along with cron and incron are anacron, at, batch, and watch. There are also inotify, dnotify, inotifywait, and iwatch. (I don't know them as well as I could.)

Welcome to Ubuntu Forums, and thank you for your kind words!

---

