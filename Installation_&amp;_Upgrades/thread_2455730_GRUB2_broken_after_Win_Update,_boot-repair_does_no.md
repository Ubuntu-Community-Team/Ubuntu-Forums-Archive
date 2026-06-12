---
title: "GRUB2 broken after Win Update, boot-repair does not work"
date: 2020-12-26
forum: Installation &amp; Upgrades
---

### Post by tj-average on 2020-12-26
Hi everyone,

I have a dual boot on my PC, with Win10 and Ubuntu.
After an Windows update, my PC would not go to my GRUB2 selection menu any more.
Instead, I receive the message:
```

error: failure reading sector 0x654c380 from `hd0'.
error: failure reading sector 0x654c380 from `hd0'.
error: failure reading sector 0x654c380 from `hd0'.

```

and after a few minutes it goes to the GRUB command promt:
```

GNU GRUB version 2.02~beta2-9ubuntu1.17
grub >

```

To fix this, I created a bootable USB stick with Ubuntu. 
I booted from that stick, choose 'try ubuntu' and installed [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

After running boot-repair, it gave me this summary:
[https://paste.ubuntu.com/p/ShX4SZtChx/](https://paste.ubuntu.com/p/ShX4SZtChx/)
but my boot was not repaired and the problem remained the same.

I'd appreciate any idea on how to proceede from here, I am very new to this.
Happy holidays to everyone reading this,
TJ

---

### Post by tea for one on 2020-12-26
[COLOR="#0000FF"]Line 52 - 54[/COLOR] Windows is in hibernation mode
[COLOR="#0000FF"]Line 170 - 172[/COLOR] One Operating System Windows 10 on sda4

It is true that sometimes Windows 10 updates prevent Grub2 from operating correctly but these updates wouldn't completely destroy your Ubuntu partition.
Was your Ubuntu partition originally sda6?

It appears that something else happened recently to create this unusual situation, can you let us know what that may be?

Two key questions:-

Do you have back ups of your Windows and Ubuntu data?
Do you have a Windows repair disk (or even a Windows 10 iso)?

I think that you will probably need Windows tools to repair the Windows bootloader?

---

### Post by oldfred on 2020-12-26
Since UEFI, you should be able to directly boot Windows from UEFI boot menu and turn fast start up off.
But better to also have Windows repair/recovery flash drive in addition to good regular backups.

That Linux partition not seen as ext4 (was it ext4 and not some other format?), may indicate abnormal shutdown, drive corruption or drive failure where sectors with Linux partition are damaged.
I might first try full fsck or e2fsck from Ubuntu live installer.

To see all the ext4 partitions, if sda6 not seen as ext4 then this will not work. That has to be fixed first.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

You can try testdisk to see it it recovers sda6 if not seen as ext4, and will probably still need above fsck after recovery.
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

---

### Post by tj-average on 2020-12-26
[FONT=arial]Hi tea-for-one,

thanks for the reply!
I think I managed to fix the windows in hybernating by running:
[/FONT][FONT=arial][FONT=courier new]sudo ntfsfix /dev/sda4[/FONT]

After this, I run boot-repair again, this is the resulting summary:
[https://paste.ubuntu.com/p/7vmxQcr8rk/](https://paste.ubuntu.com/p/7vmxQcr8rk/)
as you can see, the error of Windows being in hybernating mode has disappeared.

To give you a context/ a timeline of what happened:
Usually when I started my PC, it would give me the GRUB2 menu where I could choose weather I want to boot in Ubuntu or Windows.
After the Windows update, my PC would suddenly boot straight into Windows, not giving me the option to go to Ubuntu any more.
I was surprised by this, but not too worried (little did I know...)
Windows was very slow, so I decided to restart the PC, and since then it would give me the error: failure reading sector 0x654c380 from `hd0'

To answer your questions:
I don't know what partition Ubuntu was originally on, from what I've seen so far I assume Windows is on 
[/FONT][FONT=arial]/dev/sda4 and Ubuntu is on [/FONT][FONT=arial]/dev/sda6
No, I don't have any backup of my data neither from my Windows or my Ubuntu.
No, I don't have a Windows repair disk or Windows ISO :(

Right now, I managed to mount the partition [FONT=arial]/dev/sda4 which allows my to extract all my valuable data to a hard drive.
Then I will try to restart again.[/FONT][/FONT]

---

### Post by oldfred on 2020-12-26
The NTFSfix does very little. 
It primarily turns on the chkdsk flag, so when Windows is rebooted, it will run chkdsk.

Best to make Windows repair/recovery flash drive & backups while Windows is working.
Then once Linux is fixed, back that up.

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive) & 
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by tea for one on 2020-12-27
[COLOR="#0000FF"]Line 14[/COLOR] - error: cannot read `/dev/sda': Input/output error.
[COLOR="#0000FF"]Line 163[/COLOR] - 1 OS detected (Windows 10 on sda4). No mention of Ubuntu
[COLOR="#0000FF"]Line 341[/COLOR] - Unknown BootLoader on sda6

The boot-repair report is not promising.

Back up your Windows data (inc sda8 and sda9 if they contain data) - Please confirm when done
Boot into a live Ubuntu session and see if you can access partition sda6 
If you can access sda6, then back up your data

My gut feeling is that Boot-Repair will not really help you so it is better, quicker and more reliable to:-
[LIST]
[*]Re-install Windows and restore back up (or possibly fix Windows 10 boot with Windows tools)
[*]Re-install Ubuntu followed by restoring your Ubuntu data back ups.
[/LIST]
If i were in your position, I would back up, re-install Windows using UEFI mode with GPT and then double check as much as possible.
Then, I would re-install Ubuntu in the same mode.

Ubuntu is more co-operative with sharing a drive than Windows, hence Windows is re-installed first (just an opinion not a fact)

---

### Post by oldfred on 2020-12-27
Boot-Repair's main fix is reinstall of grub and/or update of grub menu.
And the report then can show us other issues.

---

