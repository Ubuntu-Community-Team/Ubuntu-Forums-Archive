---
title: "UEFI dual-boot grub/boot menu issues"
date: 2015-02-06
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2015-02-06
Probably not the best title but bear with me while I explain what's going on. I was recently gifted an Intel DB43LD mobo to perform UEFI dual/multi-boot iso-testing. It's a bit long-in-the-tooth (circa 2009) but it'll suffice until I can afford something newer.

So I started by installing Windows 8.1 Enterprise edition in UEFI mode on a GPT formatted drive:

[ATTACH=CONFIG]259775[/ATTACH]

I then installed Ubuntu GNOME Trusty in UEFI mode (or at least I think I did based on the live boot menu appearance - black background with white print):

[ATTACH=CONFIG]259776[/ATTACH]

But when I rebooted the box it went right into Windows without displaying any grub menu. I knew though from browsing the BIOS settings previously that pressing F10 would display a boot menu which is a new trick for me so I looked at that boot menu (sadly I didn't think of snapping a pic) but Ubuntu was NOT shown there either.

Next I decided to run Boot Repair using the Trusty live DVD and I was smart enough to grab a boot info summary before trying an actual repair:

[http://paste.ubuntu.com/10048056/](http://paste.ubuntu.com/10048056/)

I then ran Boot Repair which did end up working (at least partly) and I grabbed another post-repair boot info summary:

[http://paste.ubuntu.com/10048113/](http://paste.ubuntu.com/10048113/)

Sadly the box still booted straight into Windows but I rebooted again and pressed F10 to display the BIOS boot menu and Ubuntu was now there:

[ATTACH=CONFIG]259777[/ATTACH]

And if I select Ubuntu the GRUB menu appears and it will boot either Ubuntu GNOME or Windows:

[ATTACH=CONFIG]259778[/ATTACH]

So it's at least partly fixed but I'd like it to boot Ubuntu Gnome without having to hit F10 and selecting Ubuntu from the BIOS boot menu. Is that possible?

More importantly what went wrong? I thought after several hours of browsing and reading that it was this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)

But shortly after commenting there and reporting it on the QA iso testing tracker it was marked as a duplicate and I now have serious doubts. So I'm a bit lost.

Any help would be appreciated. I'm sure I'll have many more questions as I try to learn the whole UEFI process.

---

### Post by sudodus on 2015-02-07
I think you need help from *oldfred* to solve this case.

---

### Post by ventrical on 2015-02-07
@kansasnoob

As I posted in another thread [http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176](http://ubuntuforums.org/showthread.php?t=2259219&p=13200176#post13200176)  you have to read what OldFred has said about this. I think you can re-order the boot-sequence using efibootmgr.

Regards..

---

### Post by ventrical on 2015-02-07
> **kansasnoob said:**
> Probably not the best title but bear with me while I explain what's going on. I was recently gifted an Intel DB43LD mobo to perform UEFI dual/multi-boot iso-testing. It's a bit long-in-the-tooth (circa 2009) but it'll suffice until I can afford something newer.

So I started by installing Windows 8.1 Enterprise edition in UEFI mode on a GPT formatted drive:

[ATTACH=CONFIG]259775[/ATTACH]

I then installed Ubuntu GNOME Trusty in UEFI mode (or at least I think I did based on the live boot menu appearance - black background with white print):
.

To boot into Gnome Trusty UEFI you have to choose that option from the F10 Menu while the PC is booting up.  It will give you an option .. Boot UEFI USB 1.0 or something like that.  and it will go directly to a GRuB menu, otherwise it is booting in legacy mode.

This goes for all PCs (some F11) .. brand new or long-in-the-tooth:)

Regards..

---

### Post by grahammechanical on 2015-02-07
@kansasnoob

From what I have seen on this forum many others are experiencing the same problem. Which is why it is good that you are testing UEFI installs in this way. I do not have a UEFI motherboard and I do like to test advice on my own machine before I give it. Not only that but most of the information in the Boot Repair report goes right over my head. But anyway, I see this in both versions of the report.

> If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.

For example you can boot into Windows, [COLOR=#AA22FF]**then **[/COLOR][COLOR=#AA22FF]type [/COLOR]the following [COLOR=#AA22FF]command [/COLOR]in an admin [COLOR=#AA22FF]command [/COLOR]prompt:
bcdedit /set [COLOR=#666666]{[/COLOR]bootmgr[COLOR=#666666]}[/COLOR] path [COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\u**[/COLOR]buntu[COLOR=#BB6622]**\s**[/COLOR]himx64.efi

Please test to see if this advice is useful. Then I can be confident in advising others.

Regards.

---

### Post by oldfred on 2015-02-07
If it is an older motherboard, I did not think they had implemented the Windows only boot. 
And particularly Intel as it is one of the sponsors of UEFI.

Many new systems seem to only boot Windows by description which is not per UEFI standard.
         Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

There are several known work arounds. With the newer UEFI you can directly boot the hard drive entry. But if your UEFI is older it may not have that, as the direct device boot entry originally was only for external devices. You do show a hard drive UEFI boot entry, but it also says USB flash.

If you can boot into Ubuntu, you do not have to use live installer. If hard drive entry is really only the flash drive this may not work. General instructions for those that may or may not have /EFI/Boot and bootx64.efi. You already have that file & folder, so back it up first. Or better backup entire efi partition. Boot-Repair may have already copied it on drive in the log files.

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies. Yours is sda2.
sudo mount /dev/sda2 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi

---

### Post by kansasnoob on 2015-02-07
I'm going to document this as thoroughly as possible because I (a) want to fully understand what I'm doing, (b) hope to actually learn what went wrong during installation requiring Boot Repair, and (c) possibly be able to help someone else in the future. So bear with me while I ask some dumb questions.

I was not familiar with that BIOS boot menu so I started by finding out what that IBA GE slot entry was, network boot, so I disabled that:

[ATTACH=CONFIG]259803[/ATTACH]

That leaves the following boot options (followed by what they do):

SATA: WDC (the physical hard drive)  --> boots to a black screen w/blinking cursor

SATA: ASUS (the DVD drive)                --> obviously would boot DVD or CD if one is there

INTERNAL EFI SHELL: WDC              --> boots straight to Windows

Windows Boot Manager                        --> also boots straight to Windows

Ubuntu                                                    --> boots to the grub menu & both Ubuntu and Windows boot from there

So then I started studying a few things based on what olfred has said. I see that /boot/efi auto-mounts:

```
lance@lance-desktop:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       103G  5.4G   92G   6% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            1.1G  4.1k  1.1G   1% /dev
tmpfs           203M  1.3M  202M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  123k  1.1G   1% /run/shm
none            105M   58k  105M   1% /run/user
**/dev/sda2       101M   33M   69M  33% /boot/efi**

```

So I'm trying to familiarize myself a bit with the file structure:

```
lance@lance-desktop:~$ ls /boot/efi
boot-sav  EFI
lance@lance-desktop:~$ ls /boot/efi/EFI
Boot  Microsoft  ubuntu
lance@lance-desktop:~$ ls /boot/efi/EFI/Boot
bootx64.efi

```

That helps what oldfred said here make some sense:

> General instructions for those that may or may not have /EFI/Boot and bootx64.efi. You already have that file & folder, so back it up first. Or better backup entire efi partition. 

Now, I may have already messed up because I tried to open bootx64.efi with "cat" which was obviously a mistake. So I'm going to reboot and make sure everything is still happy. If so I'll copy the efi partition to a flash drive before doing anymore fiddling.

---

### Post by kansasnoob on 2015-02-07
Oh, I found the Boot Repair logs:

```
lance@lance-desktop:~$ ls /boot/efi/boot-sav
log  mbr_backups
lance@lance-desktop:~$ ls /boot/efi/boot-sav/log
2015-02-04__06h04boot-repair49  2015-02-04__06h09boot-repair24  boot-repair

```

---

### Post by oldfred on 2015-02-07
I thought that Boot-Repair's logs were in /var/log/boot-sav?
Or is the folder in the efi partition just the efi files?

But I have not run Boot-Repair on new UEFI system and I will not be able to for a couple of months until it warms up in Chicago. (Snowbird in FL).

---

### Post by kansasnoob on 2015-02-07
100% success :guitar:

I still don't 100% understand what I did but it worked.

So I guess I was not affected by the bug I thought I had been, eh?

Would it be correct to assume this was more of a firmware problem than an Ubuntu bug?

---

### Post by kansasnoob on 2015-02-07
One last question I may as well toss out here:

I'll be using that setup for testing re-installations of Ubuntu (various versions and flavors) so when replacing the existing Ubuntu install with a fresh one will I need to clean up a bunch of cruft in /boot/efi?

If so I'd appreciate knowing in advance what to plan on and how to do what I'll need to do :biggrin:

---

### Post by sudodus on 2015-02-08
It sounds like a good idea :-) And share the results, so if you have something to add or clarify to the following help texts, it would be valuable: a cook-book description how to 'clean up a bunch of cruft in /boot/efi'

This wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and this tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

---

### Post by kansasnoob on 2015-02-08
> **sudodus said:**
> It sounds like a good idea :-) And share the results, so if you have something to add or clarify to the following help texts, it would be valuable: a cook-book description how to 'clean up a bunch of cruft in /boot/efi'

This wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and this tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

Thanks, I hadn't seen this:

> UEFI menu clean up (UEFI saves entries)
If you cannot do change from UEFI menu, you can from command line with efibootmgr.
sudo apt-get install efibootmgr

You can add, change or delete UEFI entries:
[http://askubuntu.com/questions/63610...bios-boot-menu](http://askubuntu.com/questions/63610...bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

[http://linux.dell.com/cgi-bin/gitweb...README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb...README;hb=HEAD)

Remove Duplicate Firmware Objects in Windows BCD and NVRAM
[http://technet.microsoft.com/en-us/l...=ws.10%29.aspx](http://technet.microsoft.com/en-us/l...=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

Our oldfred did a great job here:

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

I'm going to mark this solved but I'd still like to know if the need for Boot Repair post-install, and the need to edit /boot/efi, are Ubuntu bugs or related to the manufacturers firmware. I'm betting on the latter and I should let them know at that bug report where I previously commented.

---

### Post by oldfred on 2015-02-08
Moved CortonaJ to his own thread. Not even sure if UEFI or not.

Best to backup efi partition. Of course oldfred has been saying that for several years, but only did his first UEFI install last fall. And soon wanted another install for testing and installed that to a second drive. I am almost positive I told grub to install to sdb, I had partitioned in advance to have a separate efi partition on sdb, but after rebooting it overwrote the (unbacked up) efi partition on sda. :(

One advantage of efi is that no install is required. I just copied efi partition on sda to efi partition on sdb. Then reinstalled grub on install in sda.
Only because grub may have been a slightly different version did I have to reinstall. Working install in sda is 14.04 and test install was 14.10. 
But grub uses a grub.cfg in the efi partition that is really just  a configfile entry to tell it where to find the correct grub.cfg in your main install. If I was sure grub was same version I could have just edited that to grub.cfg on sda.

A user filed a bug years ago that Kubuntu did not have a separate UEFI entry over his Ubuntu install. I then saw that the grub distributor setting is the name in efi folder & then UEFI.

 UEFI install broken when GRUB_DISTRIBUTOR!=Ubuntu (e.g. Kubuntu/UbuntuStudio) Mostly fixed in Saucy & Trusty
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417)
grub2 installs bootloader in \EFI\${GRUB_DISTRIBUTOR} directory, where
GRUB_DISTRIBUTOR is defined in /etc/default/grub.

Boot-Repair should not be required anymore for most installs. But is useful to fully document where everything is at. I use bootinfoscript as part of my rsync backup, and bootinfoscript is the first part of the Summary report from Boot-Repair. But Summary report has more info.
Before grub2's os-prober was updated to work with UEFI, Boot-Repair was essential as it was the only known work around for booting. But its method was the rename of the Windows file bootmgfw.efi to really be grub or shim. But then you could only boot Windows from grub menu and Windows updates would overwrite the grub/shim file and you had to recopy it again. Not recommended anymore.
Boot-Repairs current suggestion is the BCD entry. Vendors must then allow a ubuntu entry to work in UEFI for the one-time reboot. UEFI has the capability to create a one time boot entry.

Most systems with UEFI modified to only boot Windows will work with the hard drive entry or creating grub/shim as /EFI/Boot/bootx64.efi. I do need to update the efi Tutorial to emphasize that option. And if user has an old Boot-Repair fix with renamed Windows file to undo that. I think Boot-Repair also sees that, but many users do not know what they really did, just that Boot-Repair fixed booting.

---

### Post by ventrical on 2015-02-08
> **kansasnoob said:**
> 100% success :guitar:

I still don't 100% understand what I did but it worked.

So I guess I was not affected by the bug I thought I had been, eh?

Would it be correct to assume this was more of a firmware problem than an Ubuntu bug?

My opinion ... yes... (on your MoBo in particular you can change boot order in UEFI using efibootmgr) and I have newer UEFI BIOS and I am having a heck of a time with it.

Regards..

---

### Post by kansasnoob on 2015-02-09
> **ventrical said:**
> My opinion ... yes... (on your MoBo in particular you can change boot order in UEFI using efibootmgr) and I have newer UEFI BIOS and I am having a heck of a time with it.

Regards..

It's quite a learning curve, but it's all good clean fun ;)

---

### Post by ventrical on 2015-02-09
+1 :)

---

### Post by kansasnoob on 2015-02-09
> **ventrical said:**
> +1 :)

And I owe it all to you \\:D/

BTW I'm going to post some non-support, off-topic stuff regarding that mobo/pc build in your old thread here:

[http://ubuntuforums.org/showthread.php?t=2237765](http://ubuntuforums.org/showthread.php?t=2237765)

It may be a few days but if you subscribe to that thread you'll get to see what a "[Beautiful Mind]("http://ubuntuforums.org/showthread.php?t=2259720&page=6&p=13219026#post13219026")" I have :redface:

---

### Post by ventrical on 2015-02-10
> **kansasnoob said:**
> And I owe it all to you \\:D/

BTW I'm going to post some non-support, off-topic stuff regarding that mobo/pc build in your old thread here:

[http://ubuntuforums.org/showthread.php?t=2237765](http://ubuntuforums.org/showthread.php?t=2237765)

It may be a few days but if you subscribe to that thread you'll get to see what a "[Beautiful Mind]("http://ubuntuforums.org/showthread.php?t=2259720&page=6&p=13219026#post13219026")" I have :redface:

Take your time. You're on a  roll. :) You have a much better understanding of GRuB than I.  I am having some real wing-dingers with the new hdd on a newer MoBo and , yes, even  some of the things mentioned in this thread so i will be trying some of the procedures you have had success at. But as that thread mentioned (some links from oldfred about TPM)  TPM ver.2.0 REQUIRED for Win8 key.. or else ... BSOD ?

 Iv'e got this other 'project' I have to finish so I'll be in and out  for  a bit.

Regards..

---

