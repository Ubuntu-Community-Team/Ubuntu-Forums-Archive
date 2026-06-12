---
title: "Lost grub and access to Ubuntu after Windows 10 upgrade"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by dwhite0519 on 2020-04-24
Hi All -
I realize this is probably a common topic, but I've tried every solution I've been able to find over the last few hours. I have been dualbooting with no issue, I have Windows and Ubuntu on separate drives on my machine. Windows did an update, and to my horror a "BIOS Guard" install, and now everything but Windows is unreachable. I have done the normal steps, used a USB stick to "try Ubuntu" and try to run boot-repair, I have run commands on Windows as administrator to point it towards the grub, nothing is working. Here is my pastebin:

  [https://paste.ubuntu.com/p/cMcXmyRXkJ/](https://paste.ubuntu.com/p/cMcXmyRXkJ/)


I love Ubuntu, and whenever I boot into Windows and it upgrades, having it destroy the entire boot sequence is incredibly annoying. How do I fix this and avoid it in the future? Any help would be greatly appreciated. thanks.

---

### Post by dragonfly41 on 2020-04-25
[COLOR=#000000]> and now everything but Windows is unreachable

Do you mean that *Ubuntu* is unusable which title of your post suggests?

[/COLOR]Reading line 50 in boot-repair
SecureBoot maybe enabled.

Windows in its wisdom has enabled Secure Boot. Try disabling this at next boot.

I have similar setup, Windows 10 on internal, Ubuntu on external SSD and I now use rEFInd.
But this does not guard against Windows changing Secure Boot option during upgrades.

---

### Post by oldfred on 2020-04-25
You booted Boot-Repair in old BIOS mode. Then it does not see all the UEFI settings.

But it looks like you have a fast NVMe drive with one NTFS partition?

---

### Post by dwhite0519 on 2020-04-25
Interesting, not sure why it says that. I have the 'Secure Boot Enable' checkbox unchecked.

I'm sure we're on the right track, but that doesn't seem to be the culprit.

---

### Post by dwhite0519 on 2020-04-25
> **oldfred said:**
> You booted Boot-Repair in old BIOS mode. Then it does not see all the UEFI settings.

But it looks like you have a fast NVMe drive with one NTFS partition?

So that is the drive that Windows is installed in. It's like it's not recognizing my other 1 TB SSD that has the Ubuntu OS installed.

This is the output of a list volume on diskpart in windows:


DISKPART> list volume


  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 0                      FAT32  Partition    512 MB  Healthy    System
  Volume 1     C                NTFS   Partition    238 GB  Healthy    Boot
  Volume 2     D                       Removable       0 B  No Media
  Volume 3     E                       Removable       0 B  No Media

---

### Post by oldfred on 2020-04-25
It looks like you had sda, the HDD set as default boot when you installed Windows to SSD.
So Windows put its UEFI boot files into the HDD, not the SSD.

I prefer to have all of one system on one drive and other all on that drive.
Or if you only have one fast SSD, put both systems on fast drive and have data on slower drive.
But that depends on you expected use & just what you may prefer.

---

### Post by dwhite0519 on 2020-04-25
They're both SSDs, so I was keeping Ubuntu on the 1 TB sda, and Windows on the nvme. I'm trying to follow, do you mean you think Windows overwrote the boot files on sda?

And is there a way to fix this?

---

### Post by oldfred on 2020-04-25
The report showed /EFI/Microsoft folder in ESP on sda drive. So it installed its UEFI boot files into sda, not on an ESP on NVMe drive.
Since UEFI boot system & installs, do not boot in old BIOS mode.
So reboot live installer in UEFI boot mode and rerun Boot-Repair report.

---

### Post by dwhite0519 on 2020-04-25
Ok, thanks so much. I'll report back. Hopefully it works!

Thanks for your help!

---

### Post by dwhite0519 on 2020-04-25
Ok, here's the result of running the boot-repair in UEFI boot mode. 

[https://paste.ubuntu.com/p/9KY4cY4T5Z/](https://paste.ubuntu.com/p/9KY4cY4T5Z/)

---

### Post by dwhite0519 on 2020-04-25
Wait, now I'm in and able to boot to Ubuntu. Somewhat hilariously Ubuntu is now listed as "Windows Boot Manager" in the boot menu, but it does work.

Now I just need to repair grub and I'm good to go.

Thanks for your help!

---

### Post by oldfred on 2020-04-25
You will get into more trouble.

Years ago renaming grub or shim to have Windows name was a work around for UEFI that would not boot Ubuntu.
But grub only boots working Windows and Windows updates will reset it to be the Windows entry so you cannot then boot Ubuntu. And Windows updates will turn fast start up back on and grub will not boot Windows. Or Windows needs chkdsk and grub will not boot Windows.

First see if you can boot Windows from grub and if so make a Windows repair flash drive.
Keep your Ubuntu flash drive for Boot-Repair or manual repairs.

This is why Windows entry is booting Ubuntu. You should have Windows entry to boot Windows & Ubuntu entry to boot Ubuntu. Or the hard drive entry. It looks like you hard drive entry UEFI:Micron may boot Windows.
sudo efibootmgr -v
> Boot0000  Windows Boot Manager    HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(EFIubuntu[COLOR=#ff0000]grubx64.efi[/COLOR])WINDOWS
Boot0005* UEFI: Micron_M550_MTFDDAK1T0MAY, Partition 1	HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(EFI[COLOR=#ff0000]MicrosoftBootbootmgfw.efi[/COLOR])


---

### Post by dwhite0519 on 2020-04-26
You are sadly correct, I've made a total mess of things. I can now boot Windows, but if I try to boot Ubuntu I'm greeted with the GNU Grub 2.04 screen, and any attempts I've made have not fixed this. I've booted into Ubuntu using a live USB and tried to run boot-repair, and there is no "recommended repairs" button visible. Here is the log: 

[https://paste.ubuntu.com/p/6nwGKDxnNh/](https://paste.ubuntu.com/p/6nwGKDxnNh/)

and the output from sudo efibootmgr -v

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 000B
Timeout: 0 seconds
BootOrder: 0006,000A,0000,0005,0007,0009,0001,0002,0003,0004,000B
Boot0000* Windows Boot Manager    HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0002* USB Storage Device    BBS(USB,SanDisk,0x0)..BO
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0004* Onboard NIC    BBS(Network,Realtek PXE B3C D00,0x0)..BO
Boot0005* UEFI: Micron_M550_MTFDDAK1T0MAY, Partition 1    HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0006  ubuntu    HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)
Boot0007* Onboard NIC(IPV4)    PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(3c2c30bc61b0,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0008  Onboard NIC(IPV6)    PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(3c2c30bc61b0,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0009* Onboard NIC(IPV6)    PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(3c2c30bc61b0,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot000A* UBUNTU1    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,65535,0)/HD(1,GPT,5e33dd8e-edea-4ece-95ac-13ee01495715,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)
Boot000B* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(1,MBR,0x9135d,0x800,0x1dcf800)..BO

```



Sorry for reopening this, I've quite made a mess of things as you can tell.

---

### Post by oldfred on 2020-04-26
Currently it looks like 0000 windows boots grub
0006 ubuntu also boots grub
000A ubuntu1 boots grub, but style of entry is a bit different?
0005 UEFI: Micron boots a Windows entry 

I would delete the Windows entry that boots grub and create a new Windows entry that boots Windows.
Usually the hard drive entry is /EFI/Boot/bootx64.efi. But that file is a copy of Windows originally, grub makes a new one, and Boot-Repair backs that up to make a bkpbootx64.efi. But then not sure which file is which. You may be able to check sizes. Boot-Repair often makes then the bkpbootx64.efi another Windows boot entry by adding it to 25_custom in /etc/grub.d/25_custom

Are these new installs?
Or you seem to not using the much faster NVMe drive as much as you could.
I have no Windows but normally put two or three Ubuntu installs on my SSD & have all data on HDD.
Ubuntu / (root) does not have to be large and then can fit on NVMe drive in a 25 or 30GB partition. My new 20.04 is currently using just over 8GB and my old 16.04 and 18.04 installs grew to about 12GB with lots more apps installed over the two years. Have not installed all those into 20.04, yet? But all my data normally in /home is in a data partition on HDD. I do have /home inside / on SSD, but mostly the hidden . configuration files for user.

Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

Generic examples, your ESP is in sda1, so default entry or first example should work as is without adding drive & partition.
see also
man efibootmgr
New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 1

With multiple drives, I do not recommend using Boot-Repair's auto fixes. Better to use Boot-Repair's advanced mode and choose exactly what you want to update or re-install.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dwhite0519 on 2020-04-27
Hi oldfred. Thanks for your help. Unfortunately, I've tried everything, and I'm still not able to boot anything resembling Ubuntu at this point, only the windows boot is working. Anytime I boot into Ubuntu I'm welcomed to the GNU Grub 2.04 screen, and if I set root, I'm still sent to initramfs.  

I've tried every solution I can find and are running into walls. Incredibly frustrating a Windows update is the cause of all this headache, and now multiple days lost without my preferred OS.

Should I start a new clean thread, or what's the best way to start fresh on troubleshooting my completely borked system?

---

### Post by dragonfly41 on 2020-04-27
As a last resort I would try installing [rEFInd]("https://www.rodsbooks.com/refind/").
This adds boot option to your /boot rather than scrubbing existing /boot.
It is safe to use in my opinion. I use it daily.

[Here is PPA link]("https://launchpad.net/~rodsmith/+archive/ubuntu/refind")


sudo add-apt-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

[More guides here]("https://www.rodsbooks.com/refind/installing.html"). At installation you will be asked where to install rEFInd (i.e. location of vfat ESP partition - with boot flags - which can be on internal drive or external drive or indeed both).  You will see a new installation in /boot/efi/EFI/refind next to /boot/efi/EFI ubuntu (and other folders such as ubuntu).
Later you can tweak options in refind.conf such as theme (as I did recently). But that is cosmetic.

===============================================================

It might be helpful to explain further the boot workflow. Remember that I have been installing multiple Ubuntu on various devices so my workflow may not match yours.

I boot up and i see a menu (as you expect with Ubuntu)

Menu item ..

ubuntu
Advanced boot options
Boot UEFI bkpbootx64.efi
Boot UEFI fbx64.efi
EFI/refind/refind_x64.efi

and a host of other menu items ..
[B]
Now the important item to choose is  EFI/refind/refind_x64.efi

[/B]With four down arrows and Enter this primary takes me into the rEFInd sub  menu which is more graphic with icons. 
This can be customised as I wrote somewhere in another thread.

---

### Post by CelticWarrior on 2020-04-27
> As a last resort I would try installing [rEFInd]("https://www.rodsbooks.com/refind/").

Yes, nice suggestion, but the they would need to be able to boot Ubuntu, wouldn't they?
I know you like rEFInd and have been promoting it in a few threads. It's fine but please understand where such suggestion is applicable and where it clearly is not.

---

### Post by dragonfly41 on 2020-04-27
> [COLOR=#000000]I know you like rEFInd and have been promoting it in a few threads

I'm not "promoting" rEFInd. I'm just fed up with the chaos created and reported in countless threads when Windows acts as the cuckoo in the nest.
And I take it that OP can still use LiveUSB to install rEFInd?

My intuition is that we need an "expert system" which troubleshoots such scenarios which are bound to increase and I'm not referring to boot-repair.[/COLOR]

---

### Post by CelticWarrior on 2020-04-27
> **dragonfly41 said:**
> I'm not "promoting" rEFInd. I'm just fed up with the chaos created and reported in countless threads when Windows acts as the cuckoo in the nest.
And I take it that OP can still use LiveUSB to install rEFInd?

My intuition is that we need an "expert system" which troubleshoots such scenarios which are bound to increase and I'm not referring to boot-repair.[/COLOR]

**The vast majority of the cases are due to users' ignorance about UEFI.** We already know that in the old days of BIOS/MBR any Windows major update would reinstall its own bootloader and then we'd need to reinstall Grub. Now with UEFI/GPT the same Windows major updates just change the UEFI boot order - for convenience, supposedly, because it needs several reboots -, so all the users need to do after those updates are finished and Windows boots correctly, is to open UEFI settings and change the boot order back to "Ubuntu" (Grub).

Another typical consequence of those Windows major updates is it re-enabling Fast Startup and that causes obvious problems. But again, although Windows is to be blamed for making those unwanted changes, users dual-booting SHOULD know that and act accordingly while running Windows after those updates.

Among family and friends I've been managing several dual-boot systems for years with ZERO issues after several major Windows versions updates.

---

### Post by oldfred on 2020-04-27
I had to use rEFInd when my Asus system got too many UEFI entries. I typically had to disconnect every drive, reinstall UEFI, houseclean all UEFI entries and add one drive at a time.  I had 3 drives & multiple UEFI entries as I was experimenting with trying to get separate UEFI entries for each install. (Did not work, I got entry, but they all used /EFI/ubuntu/grub.cfg).

But then I used rEFInd and it worked. It is booting kernel, so boot still has to be configured correctly.
I keep several old small flash drives with working copies of rEFInd. 

I might suggest using Boot-Repair's advanced mode, and total reinstall of grub and latest kernel.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dragonfly41 on 2020-04-27
Pursuing my quest for knowledge of this kraken I learn that this command tests if Secure Boot is enabled.

sudo mokutil --sb-state

I don't know if there is a similar command to test for Fast Boot enabled.

Such small snippets might make it easier for boot forensics rather than the full boot-repair.

---

### Post by dwhite0519 on 2020-04-27
CelticWarrior - neither the boot sequence nor FastBoot are my issues.

dragonfly41 - I have run that, Secure Boot is off. I have also installed rEFInd, and it presents the same issue - when I boot into ubuntu it presents me with the GNU Grub version 2.04 command line. I've tried to follow instructions on [https://askubuntu.com/questions/883992/stuck-at-grub-command-line](https://askubuntu.com/questions/883992/stuck-at-grub-command-line)

When I follow all steps, it brings me to (initramfs), which messages that the files cannot be located. I'm definitely using the right partition, as it does at least attempt to boot into windows after those commands, prompts me to enter the pw for my encrypted partition, etc


oldfred - I've tried boot-repair and it doesn't seem to have affected the issue. I've used the advanced options and tried to repair the filesystems, but the other tabs such as 'grub location' are greyed out.

---

### Post by oldfred on 2020-04-27
If grub location not shown, then you do not have an install?
Did you delete /boot partition or /boot folder in / (root). As that is what it searches for.
Or cannot it not mount / as it is encrypted?

---

### Post by dwhite0519 on 2020-04-27
That's the thing - when I'm in the GNU GRUB command line, if I ls on my partition - in my case "ls (hd2,gpt2)" - I see the /boot folder. This has grub inside as well.

---

### Post by dragonfly41 on 2020-04-27
[This post wriiten by the author of rEFInd]("https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub") might help later if you decide to retain it (after sorting the apparent underlying problem).

---

### Post by oldfred on 2020-04-27
Boot-Repair cannot find your boot partition as it is inside your encrypted volume.
You have to also decrypt that for boot repair to see fstab and find /boot.
Then see if Boot-Repair will reinstall grub.

---

### Post by dmp2010 on 2020-05-02
This worked for me: 1. Used Super Grub Disk to load Windows (you’ll have option to choose from available OSs.) 2. Turned Fast Boot off. See elsewhere for instructions. 3. Turned Restore off. See elsewhere for instructions 4. Used the command below with Admin privilege at command prompt:

bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi.

Always Shut Down Windows, not Restart.

---

