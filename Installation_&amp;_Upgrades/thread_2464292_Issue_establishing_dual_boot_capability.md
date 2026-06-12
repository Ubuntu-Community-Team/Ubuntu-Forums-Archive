---
title: "Issue establishing dual boot capability"
date: 2021-06-28
forum: Installation &amp; Upgrades
---

### Post by him610 on 2021-06-28
No way to choose other OS on system with Win10 and Xubuntu 20.04.02 

After over a decade I am attempting to establish dual boot (Win10 + Xubuntu 20.04.2) on a laptop, and I am having issues getting it done.
Acer Aspire V3-572G0-543S, i5-5200u, nvidia Geforce 840m/2gb mem, 1TB HDD, 8GB RAM, Win10. Secure boot is enabled, boots EUVE , seems to be No fast boot setting in Euve/Bios. It is a very capable machine with low mileage.
Xubuntu 20.04.2 is installed on SDA-5. 

Do not care if my boot choices are with GRUB or Win Boot Manager, so long as I get the choices.

Boot Repair log at 
[http://paste.ubuntu.com/p/w38xdxPwVs/]("http://paste.ubuntu.com/p/w38xdxPwVs/")

Please advise. 
Thanks.

---

### Post by tea for one on 2021-06-28
[COLOR="#0000FF"]Line 340[/COLOR] - The boot of your PC is in Secure mode. You may want to retry after changing it to non-Secure mode.

Have you tried turning off [COLOR="#4B0082"]secure boot [/COLOR] in the UEFI set-up and see what happens?

---

### Post by him610 on 2021-06-28
Thanks for the rapid response. I did not think it made any difference if it Secure boot was enabled. Anyway, Acer seems to have really locked down the Secure boot setting. It can't be changed unless one switches from EUVE to Legacy then the Secure boot setting disappears.

New Boot Repair log: [http://paste.ubuntu.com/p/MxX3bjrn9z/]("http://paste.ubuntu.com/p/MxX3bjrn9z/")

---

### Post by tea for one on 2021-06-28
[COLOR="#0000FF"]Line 326[/COLOR] - The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting

I note your comments about Acer and locked settings in the UEFI firmware.
There have been a number of threads about this (something to do with supervisor or admin password)?

---

### Post by him610 on 2021-06-28
Again, thanks. Setting it from Legacy back to Euve enables Secure boot.

Latest Repair Boot log: None, must have made mistake copying URL

I tried the suggested repair - each one of them - none worked. I will keep at. Not going anywhere until maybe October; just the normal yard/garden chores until then.

---

### Post by tea for one on 2021-06-28
Not wanting to interrupt the yard and garden chores, do you have the latest UEFI firmware for your ACER laptop?

[COLOR="#0000FF"]oldfred[/COLOR] will be pleased that I mentioned this. ;)

---

### Post by him610 on 2021-06-28
yes, I had *oldfred* in mind when, I went to the Acer website last night; however, I found no information on Uevi upgrades on Aspire V3-572G-543S. Earlier tonight when I attempted the shim file from admin command, I made a couple of typos. Eyes getting bad, mistook curly braces for parens.
I will continue this thread to success, or towel thrown.

Update:
Went back to the Acer website; this time I found an update to the BIOS dated 2018/11/15. Things are looking up.

---

### Post by oldfred on 2021-06-29
People are talking behind my back. :)

Older Acer often needed UEFI update, there seemed to be some versions that would not let you update "trust".
Some old posts suggested downgrade UEFI, but then newer posts said even newer UEFI worked.

Newer Acer have now required Control-S to get into additional UEFI settings.

 It looks like you were able to rename the unknown entry in UEFI to Ubuntu.
And you still have three more "unknown" entries.

You can delete those unknown as long as you have working Ubuntu entry..
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

I save by brand references to issues. Do not have any v3, but these may be similar:
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.p?t=2176273](http://ubuntuforums.org/showthread.p?t=2176273)

---

### Post by him610 on 2021-06-30
Updated the Uefi/Bios yesterday; still no sucess with recommended actions. Performed the edit shimx64.efi routine from admin Command; results indicated it completed.  One can not select EUVE and disable Secure Boot; if one selects Legacy there is no Secure Boot option available. 

Changing the UEVE boot order and plugging in a bootable USB SSD gives me a Grub menu with choices of booting to LTS 20.04.2, or Win10 Boot Mgr on the primary disk, or to LTS 20.04.2 on the USB SSD.

It's as if the Acer V3-572G was diabolically designed to discourage hardware upgrades/fixes and the capability to dual boot with other non-Win operating systems. A good reason to NOT consider Acer laptops in the future.

The suggestions by oldfred are welcome. I will try them.

Thanks to 'tea for one' and oldfred for advice from both of you.

---

### Post by tea for one on 2021-06-30
> **him610 said:**
> Changing the UEVE boot order and plugging in a bootable USB SSD gives me a Grub menu with choices of booting to LTS 20.04.2, or Win10 Boot Mgr on the primary disk, or to LTS 20.04.2 on the USB SSD.

That's a clever work around.

Acer is a bit naughty not to allow UEFI without secure boot.
Do you not have this [COLOR="#000080"]trust[/COLOR] setting mentioned by [COLOR="#0000FF"]oldfred[/COLOR]?

There is another avenue to consider although I haven't used it myself. However, I know other forum members have experience of [COLOR="#0000FF"]rEFInd[/COLOR].

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

---

### Post by oldfred on 2021-06-30
It was my understanding that Microsoft required vendors to allow users to turn off UEFI Secure Boot.
So Acer must have a way or it is in violation of its contract with Microsoft on installing Windows.

Most UEFI also allow boot of a fall back or drive entry. I do not see that entry in your UEFI.
Fallback or drive boot entry for internal drive is same as for an external drive or /EFI/Boot/bootx64.efi. 
You show that in your ESP, but no entry in UEFI to boot it. Not then sure if you have some way to get it to work in UEFI settings, to add it to UEFI menu.

I have used rEFInd as emergency boot and it does work. Not sure if then it works with Secure Boot on?

---

### Post by him610 on 2021-06-30
This Acer V3-572G does not have 'Trust' capability.

Have not been able to use Control-S to get to additional EUVE settings.

Boot EUVE Enabled, Secure Boot **Enabled **- 
Pastebin: [http://paste.ubuntu.com/p/YC9MHyqJ6K/]("http://paste.ubuntu.com/p/YC9MHyqJ6K/")

In menu EUVE -> Security there is a line, Set Supervisor Password: There is an explanation that reads, "Supervisor Password controls access to the whole setup utility. It can be used to bootup when Password on boot is enabled.
I set an Admin password and was allowed to Disable Secure Boot. Wow, how devious!
There are two additional settings for User and Disk that can enabled in EUVE setup. I wonder if I should set passwords for those and see what additional privileges will open up. Once set, they can be disabled also, or returned to default state.

> Changing the UEVE boot order and plugging in a bootable USB SSD to get a Grub menu wit all operating systems
 - I can not get consistent results with this method. 

Boot EUVE Enabled, Secure Boot **Disabled** - 
Pastebin: [http://paste.ubuntu.com/p/TrwnMVTqp2/]("http://paste.ubuntu.com/p/TrwnMVTqp2/")

Will wait for additional suggestions before proceeding.

---

### Post by tea for one on 2021-06-30
> **him610 said:**
> Boot EUVE Enabled, Secure Boot **Disabled** - 
Pastebin: [http://paste.ubuntu.com/p/TrwnMVTqp2/]("http://paste.ubuntu.com/p/TrwnMVTqp2/")

From this report UEFI and Secure Boot Disabled

[COLOR="#0000FF"]Lines 334 - 339[/COLOR] look promising:-
> Suggested repair: 
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda5,
using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix use-standard-efi-file  restore-efi-backups
In the previous reports, I haven't seen anything this positive yet.

However, there is one thing a bit mysterious in [COLOR="#0000FF"]Lines 90 - 98[/COLOR] - a number of unknown devices containing [COLOR="#0000FF"]ubuntu\shimx64.efi[/COLOR]

Possibly left over from previous boot fix attempts? . On second thoughts, they are probably the entries when booting the USB SSD, I'm not completely sure.

Anyway, I'm a bit bullish about these thing and I would give the boot repair a shot with Secure Boot Disabled in UEFI mode.

Keep your back-ups safe ;).

---

### Post by oldfred on 2021-06-30
The unknown is typical and unique of Acer as it defaults to that until you enable "trust" and manually in UEFI rename the entry. 
Not sure why duplicates, but they can be deleted. Perhaps just from multiple installs of grub.

---

### Post by him610 on 2021-06-30
A couple of days ago I ordered a a 2-1/2 inch HDD/SSD caddy to place in the empty DVD/CD bay - it actually had a spacer in it. The caddy arrived today so I installed the 120GB SSD I had been using as a USB SSD which explains the SDB entries. SDC is the Boot Repair device.
Here are latest results -

Boot Repair EUVE Enabled, Secure Boot Disabled -
Pastebin: [http://paste.ubuntu.com/p/ZkYmzC6bCX/]("http://paste.ubuntu.com/p/ZkYmzC6bCX/")

Attempted to boot the laptop after repairs.
Checked the EUVE settings. All settings are as before; although, boot priority list does not show either 20.04.2 installation. Pressed the F12 key on reboot - the only option listed was Windows Boot Manager.

In Win10, ran from admin command  #
bcdedit /set/{bootmgr} path \EFI\ubuntu\shim64x.efi
Response: The operation completed successfully

Shutdown completely, waited awhile, rebooted system; system booted straight into Windows.

I think I will call it an evening; will begin tomorrow with clear mind and renewed vigor.

---

### Post by oldfred on 2021-06-30
First issue is Windows fast start up is on. Windows turns it back on with updates.
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Windows is hibernated, refused to mount.

You now have many more "unknown" devices. You need to delete them all, re-install grub once with Boot-Repair's advanced mode, and then using UEFI settings enable trust and rename the one new entry.

---

### Post by tea for one on 2021-07-01
Now that you have solved the dilemma of UEFI with Secure Boot Disabled and added a second disk, you have better additional options.

Original disk for Windows 10
New disk for Ubuntu
Both installations UEFI mode with GPT
Boot from UEFI is then possible via respective boot managers even if Grub is misbehaving.
Easier to manage when each OS has its own disk.

As mentioned by [COLOR="#0000FF"]olfred[/COLOR], Windows fast start up needs attention.

Also, you may have noticed in the report that, since you added the second disk, you have 3 OS installations.

[COLOR="#0000FF"]Line 245[/COLOR] OS#1:   Ubuntu 20.04.2 LTS on sda5
[COLOR="#0000FF"]Line 246[/COLOR] OS#2:   Ubuntu 20.04.2 LTS on sdb5
[COLOR="#0000FF"]Line 247[/COLOR] OS#3:   Windows 10 on sda4

---

### Post by him610 on 2021-07-01
1 July 2021 (09:13 am EDT
Accessed EUVE, just in case access is needed for these two settings, set the User and Disk passwords. Now the Acer boot process asks for the password when the system is booted. Still no option to turn off Fast Boot as recommended by oldfred. There must be a way to disable Fast Boo;  just need to discover it. 

Running the Boot Repair diagnostics
Boot Repair EUVE Enabled, Secure Boot Disabled -
Pastebin: [http://paste.ubuntu.com/p/9kGQDc6Syr/]("http://paste.ubuntu.com/p/9kGQDc6Syr/")

I will see if I can delete excess shimx64.efi files.

---

### Post by tea for one on 2021-07-01
> **him610 said:**
> 1 July 2021 (09:13 am EDT
Still no option to turn off Fast Boot as recommended by oldfred.

Fast Boot is a UEFI setting 
fastboot can be a grub parameter

[COLOR="#0000FF"]oldfred[/COLOR] was referring to Fast Start Up, which is a hibernation setting within Windows.

---

### Post by oldfred on 2021-07-01
Fast boot is an UEFI setting. Best to have that off as system will boot using previous configuration, even if you are changing it.

Fast start up is a Windows setting that sets hibernation flag, so Windows can boot faster.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by him610 on 2021-07-01
Glad to see ubuntuforums.org is back up again; it wnet down earlier this morning.

Discovered how to turn off Fast Boot.

Searched 'how to disable Fast Boot on Acer V3-572G'
>  Acer disable fast boot
More videos on YouTube
Press the Windows ( ...
Type Power Options.
Click the Settings tab and select Choose what the power buttons do.
Click on [COLOR="#0000FF"]Change settings that are currently unavailabl[/COLOR]e. ...
On the System Settings window, go to Shutdown settings and uncheck the Turn on fast startup option.
Click the Save changes button. 
It works. One needs to explore a little bit, this is where you get to the part that turns off Fast Boot, * Change settings that are currently unavailable * - the font is really blue

---

### Post by him610 on 2021-07-01
One more attempt at Boot Repair
After Boot Scan is complete, in the advisory box, there is an Advanced capability one can access that shows the recommended repairs, and there is an unchecked box to back up the windows.efi file then renaming it. I checked the box it to enable the backup/rename. Let's see what happens.

Boot Repair EUVE Enabled, Secure Boot Disabled, Fast Boot Disabled
Pastebin: [http://paste.ubuntu.com/p/t53JD5gvVd/](http://paste.ubuntu.com/p/t53JD5gvVd/)

---

### Post by him610 on 2021-07-01
When booting after the repair,
The SSD (SDB) shows up in the boot choices when F12 is pressed; although, the choice is Windows Boot Manager on SSD (something Like that)
when choseit actually the grub prompt which means I need to figure out what filespecs to give it. I expect it is one of these...
```

 ls -Al /boot/efi/EFI/ubuntu
total 4264
-rwx------ 1 root root     108 Jun 22 17:22 BOOTX64.CSV
-rwx------ 1 root root     117 Jun 22 17:22 grub.cfg
-rwx------ 1 root root 1734528 Jun 22 17:22 grubx64.efi
-rwx------ 1 root root 1277024 Jun 22 17:22 mmx64.efi
-rwx------ 1 root root 1341560 Jun 22 17:22 shimx64.efi

```
Which one would it be? I think I will try shimx64.efi first. If that doesn't work, second will be grubx64.efi. After that, ????

Added - that did not work, response was *error: can't find command '/boot/efi/EFI/ubuntu'*:(

Added-more - Rebooted at F12, selected the other option, Windows Boot Manager - Surprise, surprise! (as Gomer Pyle would say) Boot menu appeared with choice to boot into Windows on SDA or Ubuntu on SDB SSD.

Even though, I never got the Acer V3-572G to boot Ubuntu from a partition on SDA (primary disk), I did get it to boot from SDB which basically addresses my issue of no dual boot. I shall mark this as Solved.

@oldfred - I found where one sets 'trust' and 'untrust'. It is from the grub command line. At *grub help* both show up as commands/options.

Many thanks to *tea for one* and *oldfred* for the advice, and for sticking with me through the end.

---

### Post by oldfred on 2021-07-01
Your unknown devices seem to keep growing.
Best to houseclean. Years ago, too many entries crashed systems and bricked them. Blamed Linux, found same issue in Windows, so really UEFI issue. And mostly fixed with fixes to UEFI.
But still do not let too many unknown get added.

The Ubuntu boot entry should be /EFI/ubuntu/shimx64.efi. That works for Secure Boot on or off. But only with Secure boot on, if all other boot programs are also signed, so secure.

You do show one typically correct entry, but it is not in the boot order at all.
```
Boot000C* ubuntu	HD(2,GPT,a1def4b3-0ef5-4e34-ac11-d4a5450e2dad,0x12c800,0x96000)/File(EFIubuntushimx64.efi)
```

---

### Post by him610 on 2021-07-01
@oldfred
How does one go about purge the unknown devices? 
I went to that directory when running the Boot Repair utility, there were no multiple shimx64.efi files there - only one.

---

### Post by oldfred on 2021-07-01
You should only have the one /EFI/ubuntu/shimx4.efi that you showed above in post #23.

In Post #8, I have the commands to remove UEFI boot entries.

I think each install of grub into UEFI creates new unknown entry. That only gets changed by the "trust" setting procedure to whatever name you want.

---

### Post by him610 on 2021-07-01
@oldfred, thanks
I went back and reread your advice in Post #8. It works just like you said. I did not fully understand the process when I first read it. When, two days ago? I think I have definitely  learned something here, and maybe this thread will help others too.
After deleting the excess shimx64.efi entries, I discovered I could boot into the LTS 20.04.2 residing on SDA5 after all
I think I read somewhere that when Windows gets updates, the existing Windows Manager file gets overwritten, and the system reverts to booting only Windows. Do you know if that is true or not? 
If true, I assume one would need to run Boot Repair again.

---

### Post by oldfred on 2021-07-01
Both Windows & grub with major updates reset boot order, so they are first.
Often all you have to do is change boot order using efibootmgr or from within UEFI.
In some cases you may need to reinstall grub. Boot-Repair is one way to do that.
Best to always have current versions of a Windows repair/recovery flash drive and Ubuntu live installer. 

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

