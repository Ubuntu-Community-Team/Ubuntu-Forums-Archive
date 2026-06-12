---
title: "efi SecureBoot not working after update of 18.04"
date: 2018-10-20
forum: Installation &amp; Upgrades
---

### Post by franknfurter2 on 2018-10-20
Hallo,

on my System I have dual boot installed. Fist I installed Windows 10 and afterwards Ubuntu 16 (Ubuntu Studio). Some weeks ago I did an upgrade to 18.04, where I had a trouble with the update of grub. So this was the message:

####################################
Your system has UEFI Secure Boot enabled in firmware, and the following kernels present on your system are unsigned:

 4.4.0-135-lowlatency


These kernels cannot be verified under Secure Boot.  To ensure your system remains bootable, GRUB will not be upgraded on your disk until these kernels are removed or replaced with signed kernels.

->installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
####################################

So I moved these kernal files to a different folder and grub update worked fine. I was still able to boot my system with SecureBoot on.

After a while, an update forces me to enter a password, to reboot, and enter the password again in my bios. That had something to do with MOK. Still my system worked fine.

At Okt, 13th I updated again and did a reboot. Since then, my system will not Secureboot anymore. I tried boot-repair, but nothing will help. It just run into a black screen when Secureboot is set in BIOS. As an evidence, I attached extracts from journal here showing the differences.

I really have no idea how to fix this.

So here it the journal extract: [ATTACH]281391[/ATTACH]

and here the boot-repair report

[http://paste.ubuntu.com/p/pgmvbFjG6d/](http://paste.ubuntu.com/p/pgmvbFjG6d/)

---

### Post by franknfurter2 on 2018-10-21
Ok, it's 22 hours ago since I posted this. So nobody can deal with this, is that true?

I have some further news to this. I found out, that the setting of CSM in bios had an effect. So if it is enabled, the system won't secureboot with the ubuntu boot loader but will do this with the windows loader. When I switch CSM in bios to "disabled" I am able to boot in secureboot with the ubuntu boot loader (shim).

But what is this? Before the ubuntu update I had CSM enabled, I have never touched that setting in bios.

Can somebody explain please?

---

### Post by ubfan1 on 2018-10-21
Did you use the signed version of the package? e.g. linux-signed-image-4.4.0-137-lowlatency

---

### Post by franknfurter2 on 2018-10-22
Dear ubfan,

sure I am using signed kernels, because otherwise I would not be able to SecureBoot. The Problem is to my opinion not the kernal, boot process does not start grub, it seems, when csm is enabled in bios. The new attachment shows the installed packages that are somehow signed. I think some of them are not necessary.

Again: 
[LIST]
[*]When rebooting with SecureBoot and CSM enabled, no GRUB menu, just blank, black screen 
[*]When rebooting with SecureBoot and CSM disabled, GRUB menu and Secure booted system 
[*]When rebooting with SecureBoot disabled and CSM on, Grub menu and not secure booted system (as expected) 
[/LIST]

see Attachment here
[ATTACH=CONFIG]281408[/ATTACH]

---

### Post by oldfred on 2018-10-22
CSM is BIOS boot.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

The only way you might be booting with CSM on, is that UEFI, tries that first, sees you have no BIOS boot loader in gpt's protective MBR and reverts to an UEFI boot.

Almost all systems will not let you turn on CSM, if Secure Boot is on. CSM is not secure as it is the old BIOS boot.
But a few BIOS, do seem to want CSM on to boot, but you have to select UEFI boot.

You are showing some signed kernels, but grub menu is not using them.
I might run the suggested repair:


```
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda5, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file  restore-efi-backups

```

If you have installed any proprietary drivers for video or WiFi, then you probably cannot turn secure boot on as they are not signed, so Ubuntu cannot fully say system is secure.

---

### Post by ubfan1 on 2018-10-22
I assume sdb is just a data disk, although it has a Windows boot block on it. With sda being gpt, you are booting Windows in UEFI mode (should  work with secure boot). Ubuntu on sda is installed in UEFI mode, BUT the kernels listed in grub are NOT the signed ones (they do not have "signed" in their names).  This would have actually worked when shim/grub allowed unsigned kernels (modules) to boot, but that changed several years ago -- I thought earlier than 16.04, but I may be wrong).  In any case, CSM is legacy support, and you don't seem to need that.  You do seem to need the kernel packages which have "signed" in their names -- which is what the error message stated.

---

### Post by franknfurter2 on 2018-10-22
Thanks everybody for reply and let us go further with this.

Signed or unsigned kernel:
-------------------------------------------------------
Last journalctl of booting with CSM disabled and SecureBoot enabled shows:

Okt 22 15:57:08 Zuse2016 kernel: efi: EFI v2.50 by American Megatrends
Okt 22 15:57:08 Zuse2016 kernel: efi: ESRT=0x8b1add98 ACPI=0x8a217000 ACPI 2.0=0x8a217000 SMBIOS=0x8b1ab000 SMBIOS 3.0=0x8b1aa000
Okt 22 15:57:08 Zuse2016 kernel: secureboot: Secure boot enabled
Okt 22 15:57:08 Zuse2016 kernel: Kernel is locked down from EFI secure boot; see man kernel_lockdown.7

What does this kernel_lockdown mean?

uname -a shows
Linux Zuse2016 4.15.0-36-lowlatency #39-Ubuntu SMP PREEMPT Tue Sep 25 00:16:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

And take a look at this new attachment showing, that the normal kernels are also signed and the kernels with "signed" in their name are transitional packages:



Note! I am using ubuntu 18.04. Are you really sure, that with SecureBoot on, unsigned kernels are loaded?

CSM:
-------------------------------------------------
First of all and again I have to say, that before the last update of Ubuntu, CSM was enabled and System was booting with SecureBoot enabled. After update booting hangs with not showing Grub menu. So if kernel_lockdown means that Grub loads an unsigned kernel, there has been misunderstanding on my site. But kernel comes into play when Grub has started and a Grub menu is showing up. Isn't it so?

So do i really have to clear every (legacy) boot entry in the GPT? If boot-repair has not done it, me myself didn't install legacy boot entries in GPT either.

Oh dear. Where will this all lead me to?

---

### Post by oldfred on 2018-10-22
I do not use Secure boot.
What does this say?
see 
man kernel_lockdown.7

I thought you had installed the signed kernels. You are just posting the synaptic list of kernels. You do need to install a signed kernel.

If not using signed kernel not sure then what is happening with your system. 
I did not think it really was UEFI Secure boot unless you had signed kernels.

---

### Post by franknfurter2 on 2018-10-23
Ok, I will have a look at man kernel_lockdown.7

The green icon in front of each row in synaptic means "installed".

---

### Post by ubfan1 on 2018-10-23
Do the signed kernels exist in the /boot directory?  If so, just run sudo update-grub.

---

### Post by franknfurter2 on 2018-10-24
Hallo ubfan, hallo oldfred

at the end of this post you'll see the entries in /boot (after I did update to kernel version 4.15.0-38. But didn't  the kernels come into play **AFTER **grub? shim as the 1.step bootloader, grub as the second that starts the kernel the user selected in the grub menu?

Dear oldfred, the command "man kernel_lockdown.7" does not work. There is no entry. I only found a draft of this manual in web.

I think today that there is a bug in grub and I will file it on launchpad. Evidence for me is, that on October, 13th, before I got the problems, there was a grub update. See this APT Log
```
----------------------------------------------------
Start-Date: 2018-10-13  10:46:15
Commandline: aptdaemon role='role-commit-packages' sender=':1.852'
Upgrade: git-man:amd64 (1:2.17.1-1ubuntu0.1, 1:2.17.1-1ubuntu0.3), grub-common:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), libptexenc1:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), git:amd64 (1:2.17.1-1ubuntu0.1, 1:2.17.1-1ubuntu0.3), grub2-common:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), flashplugin-installer:amd64 (31.0.0.108ubuntu0.18.04.1, 31.0.0.122ubuntu0.18.04.1), libxnvctrl0:amd64 (390.42-0ubuntu1, 390.77-0ubuntu0.18.04.1), gitk:amd64 (1:2.17.1-1ubuntu0.1, 1:2.17.1-1ubuntu0.3), ubuntu-drivers-common:amd64 (1:0.5.2, 1:0.5.2.1), grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), libtexluajit2:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), libwebkit2gtk-4.0-37:amd64 (2.22.2-0ubuntu0.18.04.1, 2.22.2-0ubuntu0.18.04.2), grub-efi-amd64:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), shim-signed:amd64 (1.34.9.2+13-0ubuntu2, 1.37~18.04.2+15+1533136590.3beb971-0ubuntu1), libsynctex1:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), code:amd64 (1.27.2-1536736588, 1.28.1-1539281690), grub-efi-amd64-signed:amd64 (1.93.5+2.02-2ubuntu8.4, 1.93.7+2.02-2ubuntu8.6), texlive-binaries:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), gir1.2-webkit2-4.0:amd64 (2.22.2-0ubuntu0.18.04.1, 2.22.2-0ubuntu0.18.04.2), libtexlua52:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), libjavascriptcoregtk-4.0-18:amd64 (2.22.2-0ubuntu0.18.04.1, 2.22.2-0ubuntu0.18.04.2), libwebkit2gtk-4.0-37-gtk2:amd64 (2.22.2-0ubuntu0.18.04.1, 2.22.2-0ubuntu0.18.04.2), gir1.2-javascriptcoregtk-4.0:amd64 (2.22.2-0ubuntu0.18.04.1, 2.22.2-0ubuntu0.18.04.2), libkpathsea6:amd64 (2017.20170613.44572-8build1, 2017.20170613.44572-8ubuntu0.1), shim:amd64 (13-0ubuntu2, 15+1533136590.3beb971-0ubuntu1)
Remove: linux-image-4.4.0-135-generic:amd64 (4.4.0-135.161), linux-headers-4.4.0-134:amd64 (4.4.0-134.160), linux-headers-4.4.0-135:amd64 (4.4.0-135.161), linux-headers-4.4.0-135-lowlatency:amd64 (4.4.0-135.161), linux-image-extra-4.4.0-135-generic:amd64 (4.4.0-135.161), linux-headers-4.4.0-135-generic:amd64 (4.4.0-135.161), linux-headers-4.4.0-134-generic:amd64 (4.4.0-134.160), linux-image-4.4.0-135-lowlatency:amd64 (4.4.0-135.161)
End-Date: 2018-10-13  10:48:10
--------------------------------------------------
```

 Her are the files (and dirs) in directory /boot.

```

abi-4.15.0-34-generic
abi-4.15.0-34-lowlatency
abi-4.15.0-36-generic
abi-4.15.0-36-lowlatency
abi-4.15.0-38-generic
abi-4.15.0-38-lowlatency
config-4.15.0-34-generic
config-4.15.0-34-lowlatency
config-4.15.0-36-generic
config-4.15.0-36-lowlatency
config-4.15.0-38-generic
config-4.15.0-38-lowlatency
efi
grub
initrd.img-4.15.0-34-generic
initrd.img-4.15.0-34-lowlatency
initrd.img-4.15.0-36-generic
initrd.img-4.15.0-36-lowlatency
initrd.img-4.15.0-38-generic
initrd.img-4.15.0-38-lowlatency
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
retpoline-4.15.0-34-generic
retpoline-4.15.0-34-lowlatency
retpoline-4.15.0-36-generic
retpoline-4.15.0-36-lowlatency
retpoline-4.15.0-38-generic
retpoline-4.15.0-38-lowlatency
System.map-4.15.0-34-generic
System.map-4.15.0-34-lowlatency
System.map-4.15.0-36-generic
System.map-4.15.0-36-lowlatency
System.map-4.15.0-38-generic
System.map-4.15.0-38-lowlatency
vmlinuz-4.15.0-34-generic
vmlinuz-4.15.0-34-lowlatency
vmlinuz-4.15.0-36-generic
vmlinuz-4.15.0-36-lowlatency
vmlinuz-4.15.0-38-generic
vmlinuz-4.15.0-38-lowlatency
```

---

### Post by oldfred on 2018-10-24
Please use code tags for longer terminal or text.
Easy to add in Forum's advanced editor with # icon.

If synaptic is saying signed kernels installed, you are not showing any signed kernels in /boot. So grub  will not find a signed kernel.

I would make sure UEFI Secure Boot is on. Boot live installer in UEFI boot mode with Secure boot still on.
Then in Boot-Repair's advanced options have it do a total reinstall of grub and latest kernel which should be a signed kernel.
Not sure then how to get low-latency, but first steps first.

---

### Post by franknfurter2 on 2018-10-29
Dear oldfred,

as mentioned [here]("https://github.com/slytomcat/UEFI-Boot/blob/master/keys/canonical-uefi-ca.crt") i tried after downloading the canonical certificate "sudo sbverify --cert canonical-uefi-ca.crt /boot/vmlinuz-4.15.0-36-lowlatency" i.e. and the output was "Signature verification OK". So I think the rule "signed kernel have the word 'signed' in their name" is not true any more.

Take a look at[ this thread]("https://askubuntu.com/questions/1039201/why-ubuntu-stopped-publishing-signed-linux-kernel-images-since-4-16-4") as well.

After all I opened [this bug]("https://bugs.launchpad.net/ubuntu/+source/shim-signed/+bug/1799767") at launchpad. Let us see what will happen.

---

### Post by oldfred on 2018-10-29
Originally they used the Microsoft signed key. That was a one time $100, from an independent signing source, not Microsoft.

But now it looks like they are using their own Canonical key and all kernels are now signed?
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

I know they changed MokManager.efi to mmx64.efi about a year ago which is related to key management.
[https://askubuntu.com/questions/903207/refind-shows-multiple-ubuntu-choices](https://askubuntu.com/questions/903207/refind-shows-multiple-ubuntu-choices)

---

### Post by ubfan1 on 2018-10-29
But your original error for an unsigned kernel was for a 4.4 kernel, not a 4.15.  The 4.4 kernel looks like it got removed (see your apt log), so the problem was fixed.  I still have a system with 4.4 kernels, signed and unsigned versions, and the one without ".efi.signed" in the name fails the sbverify, while the one with ".efi.signed" passes.  I'd guess the lowlatency kernel  (vs my generic) was not signed either.  The 4.15 kernel packages seem to be  defaulted to signed, with an "unsigned" package available (which I never noticed ).  One less thing to worry about, if everything from this point from Canonical is signed.

---

### Post by franknfurter2 on 2018-11-01
Dear ubfan1,

maybe because of the fact, that I'm an not an english native speaker, there is a misunderstanding. While I was upgrading (not updating!!) from Ubuntu 16.04 to 18.04 i got that warning about that unsigned 4.4 kernel but in the end, I did get my system upgraded to 18.04.

So 18.04 comes with the 4.15 kernel and as we could see above they are signed even if the don't have the word "signed" in their name. So the "unsigned" 4.4 kernel was left from the old 16.04 and is removed now. I have a ubuntu 18.04 LTS system that's running and this system (not the 16.04) has got the secure boot problem. (want my old 16.04 back, it was working without any problem :( ) 

Sorry for this misunderstanding.

---

