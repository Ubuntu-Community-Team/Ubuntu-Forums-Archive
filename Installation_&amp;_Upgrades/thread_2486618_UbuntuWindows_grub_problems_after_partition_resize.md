---
title: "Ubuntu/Windows grub problems after partition resize+move"
date: 2023-05-06
forum: Installation &amp; Upgrades
---

### Post by lp0404 on 2023-05-06
Hello. 
I have dual boot system, and after my newbie act of shrinking Windows partition (by Windows analog of GParted) and resizing+moving Ubuntu partition to unallocated space, I feel like something is wrong with this picture: 

1) Manual boot (F12) sees only USB drive with live Ubuntu
2) Grub screen of course disappeared and there are tons of text with errors
3) Boot Repair recommends me unfamiliar action (at least Google search brings controversial results and I fear it will complicate reparations): *GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag*[I]). 
[/I]4) Trying to recover previous configuration (as I suspect was on sda2) brings: *mount: /mnt: can't read superblock on /dev/sda2*

Here is Boot-Info [https://paste.ubuntu.com/p/qgTVqSQFhH/](https://paste.ubuntu.com/p/qgTVqSQFhH/) from Boot Repair.
I understand more or less what happened, but I'm not that proficient in this area. It will take me days to find appropriate solution and to restore what can be restored. Please, help.

---

### Post by ajgreeny on 2023-05-06
As I assume you have not yet managed to boot your Ubuntu installation which you appear to have installed in the legacy BIOS manner rather than UEFI, the best way forward may be to start again by hooting to the UEFI install medium but this time making sure you choose the UEFI option from the devices shown in the list.

That will ensure that the live system runs in UEFI mode which is then the way the Ubuntu install will run, essential for dual booting from grub.

It may be possible to boot to your installed Ubuntu simply by creating that bios-boot partition mentioned but it will I believe be best for both systems to be in UEFI boot mode.

---

### Post by lp0404 on 2023-05-06
Thank you so much for such a quick answer. Please, let me check if I understand you correctly:
1) I start installation from Live Ubuntu USB
2) I choose "unmount partitions" from the installation menu 
3) I choose "the UEFI option from the devices shown in the list" (I don't remember this option, but I will do my best to find it)
4) The installation chooses how and where to manage UEFI mode
5) I have some chances to preserve data files from previous Ubuntu and Windows installations
Beforehand grateful

---

### Post by tea for one on 2023-05-06
> **lp0404 said:**
> 5) I have some chances to preserve data files from previous Ubuntu and Windows installations
Your first priority is to backup your Ubuntu and Windows personal data via a "Try Ubuntu" live session.

Line 91 - OS#2:   Windows 7 on sda5
Windows 7 is now unsupported and should be replaced with Windows 10/11.

When you are satisfied that you have restorable backups, you should seriously consider installing Windows 11 and Ubuntu 22.04 in UEFI mode with GPT.

---

### Post by yancek on 2023-05-06
When you resized the windows partition, you used the windows Disk Management tool, correct?  Always best to use windows tools on a windows system.  Did you reboot windows after doing this and run chkdsk to check for any problems? 

Boot repair, beginning at line 29 shows an EFI partition with only windows files on it so you have windows installed in EFI mode while Ubuntu is installed in Legacy mode.  If you do this, you will only be able to boot/use one of the systems.  If you set the BIOS to UEFI, it will boot windows and not Ubuntu.  If you set it to Legacy, it will boot Ubuntu and not windows.  Grub installed in Legacy mode will not boot windows in UEFI mode.

> resizing+moving Ubuntu partition to unallocated space, I feel like something is wrong with this picture:  

How did you do this?  Was it using a 'live' USB?  If you moved the entire Ubuntu system, you also moved the boot files so the computer will not know where to look for them.  I'm not really sure if this is what you did?

The boot repair recommendation is because you have a Legacy install of Ubuntu on a GPT drive and do NOT have a bios_boot partition which is needed.  It will not be needed if you install Ubuntu in UEFI mode which would be the best solution since windows is already UEFI.  You should have an option to boot the USB in UEFI mode in your BIOS firmware boot options.

Your Ubuntu is now on sda7 and if you moved it from sda2, there is nothing to recover on sda2.  Did you actually use move or copy?

---

### Post by lp0404 on 2023-05-06
Thank you very much, will write about the result.

---

### Post by lp0404 on 2023-05-06
1) I used not Disk Management tool, but a tool called EaseUS Partition Master 14.0. (I tried it before, there were no problems). 
2) No I did not reboot and run chkdsk
3) "*Boot repair, beginning at line 29 shows an EFI partition*" - this part I did not understand, my bad
4) After resizing Windows partition (by EaseUS), I switched by grub to installed Ubuntu and moved sda6 partition (that contains my Home directory) to newly created unallocated space (that was before sda6 partition space)
5) No, I did not move anything from sda2 to sda7, I just followed procedures (understanding the potential dangerous consequences and backing up all vital data to external hard drive before any experiments with ubuntu)
6) As a result - I somehow damaged windows bootloader and Ubuntu grub system
7) I suspect sda2 contains only grub related system, but now [I]"can't read superblock"
8) [/I]Since I didn't have any problems with these aspects of computer management, I didn't have any reason to learn how it work properly. So, I'd like to try the most efficient way to preserve both systems, before I do something ultimate. There are always chances I forgot something important to backup

---

### Post by oldfred on 2023-05-06
Some important things to understand.
Drives can be MBR or gpt partitioned. 
Boot can be UEFI or old  BIOS boot. BIOS really for older systems.
Microsoft has required UEFI/gpt for all installs by vendors since 2012. So most hardware is UEFI/gpt.

Ubuntu is flexible, maybe too much so.
It will install in BIOS mode to gpt drive, but need the bios_grub partition. That is the error message from Boot-Repair. But real issue was that you booted live installer in BIOS mode, not UEFI mode.

Since Windows is UEFI/gpt, you have to install Ubuntu in UEFI boot mode is on same drive. And best to always have all systems in UEFI boot mode using gpt drives if system is UEFI or newer than 2012.

When booting Ubuntu live installer you should see two boot options One clearly UEFI : XXX and one XXX where XXX is name or label of flash drive.
It is possible to make live installer in UEFI only or BIOS only. But most tools make live installer, so it can be booted in either mode.

Future will be better as vendors are now making UEFI only systems. No old BIOS/MBR.
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

