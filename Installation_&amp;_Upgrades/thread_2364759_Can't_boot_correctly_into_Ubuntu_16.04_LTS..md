---
title: "Can't boot correctly into Ubuntu 16.04 LTS."
date: 2017-06-27
forum: Installation &amp; Upgrades
---

### Post by 1jarwolf on 2017-06-27
Alright guys. I am running Ubuntu on an old rig. I literally fell down four stairs going into the basement, where I live. Okay, okay, get the laughs out! Haha. Anyhow, I am using an old bulky Gateway EV700 monitor, and an old tower in which is called  HP 110-243w Desktop PC. If you need the specs on this tower, here is the link. [https://support.hp.com/us-en/document/c04108287/](https://support.hp.com/us-en/document/c04108287/)


     i managed to install Ubuntu using a USB flash drive, however it does not boot up. It keeps saying no Operating System installed on this hard drive. So, I had to reboot with USB, I then at the menu pressed the "c" or "e" key, in which brought me to the grub menu. I managed to look up a solution on my phone and got it to boot up. The problem is, if I shut down the computer, it will then repeat the process, and I have to go through all that hassle every single time I want to boot up my computer. Is there ANY other solutions to fix this permanently? As a side note. the wifi is terrible on here,even with a wifi adapter. It says it takes an hour just to download th Google Chrome browser, so I am using the default one in which is Mozilla Firefox.

I have attached three screen shots using my phone. The first two screen shots, are what I did to at least manage to boot into Ubuntu. The last one is just the process. After that picture I took of th third one, I booted up and went to Terminal right away and typed in update-grub. Here is what I got back...Now I am completely lost and not sure how to fix this. It also seems like I can't connect to my wifi adapter and I don't see it in the network settings.

Error of update-grub:
```
oneofour@Luc1fur:~$ sudo -i
[sudo] password for oneofour: 
root@Luc1fur:~# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Adding boot menu entry for EFI firmware configuration
done
```

P.S:The third image was taking way too long to upload, the ones in the attachments are really what is needed. it is the process in which I did until you get to the error in the update-grub. I want to thank this wonderful community for helping one another on the issues that they're having, and that is a main factor in which I chose Ubuntu. Thank you!

---

### Post by CatKiller on 2017-06-27
It seems possible that you've installed Ubuntu in UEFI mode, but your computer isn't set to boot in UEFI mode? That would probably show the symptoms you're seeing, and is where I would start looking.

---

### Post by 1jarwolf on 2017-06-28
Hmm. All I see is Legacy mode but I Enabled it and I moved Ubuntu to where it is first to boot, I save and reboot, does the same thing. I look into the BIOS again and it appears that the Ubuntu is moved back down the list as it was before for some odd reason.

---

### Post by CatKiller on 2017-06-28
> **1jarwolf said:**
> Hmm. All I see is Legacy mode but I Enabled it and I moved Ubuntu to where it is first to boot, I save and reboot, does the same thing. I look into the BIOS again and it appears that the Ubuntu is moved back down the list as it was before for some odd reason.

This
> **1jarwolf said:**
> 
```
Adding boot menu entry for EFI firmware configuration
done
```

implies to me that GRUB thinks it's a UEFI install. For UEFI to work you need a FAT32 /boot partition, the OS to be installed UEFI-aware, and the BIOS to be booting the device in UEFI mode.

For non-UEFI ("Legacy") to work you need the BIOS to be booting the device in Legacy mode and a bootloader in the MBR of the device you're booting from.

It seems to me that you've got some things from one method and some things from the other method, which is why it isn't working. I'm afraid my experience in this area is limited, though.

---

### Post by 1jarwolf on 2017-06-28
I tried :D. Worst comes to worst, I leave my PC on 24/7, or just reboot and do that coding.

---

### Post by efflandt on 2017-06-28
External 65 watt power supply? A laptop in a tower case.

Do you still have Win8.1 (or Win10) on the PC trying to dual boot, or did you wipe that and using Ubuntu only? If trying to dual boot, you would need to leave it in UEFI mode. But if Ubuntu is the only OS, I would think you could switch UEFI to Legacy BIOS mode, repartition your 1 TB drive to msdos partitions instead of gpt, then try reinstalling.

But first, if Ubuntu was installed in UEFI mode and you switched UEFI to legacy BIOS mode, you might be able to get it to work by switching back to UEFI mode, tap Esc key while booting, and see if you can select ubuntu from the UEFI menu. Although, not sure if that would work if something got mixed up and put grub in the mbr of the drive.

I have an HP laptop with Win10, so I used Window's own Disk Management to shrink its partition and free up space for Ubuntu (and also disabled fast boot). When I first installed Ubuntu (in UEFI mode), it rebooted to grub, but since then it defaults booting into Win10. To get to Ubuntu I have to tap Esc key, then F9 I think, and once I select ubuntu in UEFI menu, it brings up the grub menu and I can get into Ubuntu. There is a way to change that, to have grub first in UEFI, but I have not tried that yet. I don't have any other computer with UEFI, my main PC is from 2010.

---

### Post by 1jarwolf on 2017-06-28
Okay. I installed Gparted, and here is how it shows. In the boot menu, Ubuntu or "Hard Drive" is under UEFI mode, however, it is saying it is installed on EFI (I do believe if I am reading it right.) Now, how would I go on at changing it without having to reinstalling Ubuntu again? I attached a screenshot of Gparted below. Also, in the code section, I wrote what I had to do in order to boot this system up.

```
grub> ls
(memdisk) (hd0) (hd0,msdos1) (hd1) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (hd2)

     Now, I did ls on each of these and it so happened that (hd1,gpt2) is the file that has the initrd and the file that starts with a v in it, so I went with that one.

grub> root=(hd1,gpt2)
grub> configfile /boot/grub/grub.cfg

*Ubuntu finally loads up in UEFI mode, I think...*

```

---

### Post by CatKiller on 2017-06-28
OK, so Ubuntu seems comfortable being in UEFI mode, and the partitions look right from your screenshot, so it should just be a case of booting it in UEFI mode. Exactly how to do it will depend on the settings that are available in your BIOS. You'll want to turn off Legacy mode in the BIOS, and you may need to change the hard drive entry too.

---

### Post by oldfred on 2017-06-28
That is an UEFI install.

But HP is not Ubuntu friendly. 
It modifies UEFI to boot only "Windows Boot Manager" by description. That also is a violation of UEFI spec to use description as part of boot. 

But it does not check which file it actually uses to boot, just description. Since not dual booting Windows.
We can make a new Windows boot entry that really uses grub or shim boot files, you can boot Ubuntu.

More details in link in my signature.
See also 
man efibootmgr

If you have a Windows entry you may want to delete it to avoid confusion on which entry is really for booting Ubuntu. To see current entries and details on what it boots.
sudo efibootmgr -v

       
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
     
Most systems also allow boot of the fallback or hard drive entry at /EFI/Boot/bootx64.efi. I normally copy shimx64.efi and rename to be that file.

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

---

### Post by 1jarwolf on 2017-06-28
oneofour@Luc1fur:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
** Warning ** : Boot0000 has same label Windows Boot Manager
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0007,0000,0001,0002,0006,0003,0004,0005
Boot0000* Windows Boot Manager[/CODE]
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0003* UEFI: IPv4 Realtek PCIe FE Family Controller
Boot0004* UEFI: IPv6 Realtek PCIe FE Family Controller
Boot0005  Fake Legacy Option
Boot0006* UEFI: Lexar USB Flash Drive 1100
Boot0007* Windows Boot Manager[\CODE]

For some reason, I can not find the /EFI folder in Files or on the Terminal. I'm a noob.

---

### Post by 1jarwolf on 2017-06-28
Hmm. How should I edit the hard drive entry if I may ask?

---

### Post by oldfred on 2017-06-28
If you look for the ESP in your installed system from inside your installed system you will see it mounted in fstab.
cat /etc/fstab

You should see an entry like this:
```
# /boot/efi was on /dev/sda1 during installation
UUID=FD76-E33D  /boot/efi       vfat    defaults      0       1

```

So it is /boot/efi/EFI/ubuntu
fred@Asusz97:~$ ls -l /boot/efi/EFI/ubuntu

If you get permission issues it is how it is mounted:

It may show a umask setting that prevents all writing or editing.
```
 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1 


```

It may be restricted for secuity reasons, but I want to be able to edit my ESP folders. So I change back to defaults. If you run Boot-Repair from flash drive, it also changes entry so it can updated and move files in the ESP.

---

### Post by johndough2 on 2017-06-29
Hi

I gotta ask...

old rig?

Is the CMOS battery still active?

To save any BIOS settings changes you make?

---

### Post by CatKiller on 2017-06-29
> **oldfred said:**
> If you get permission issues it is how it is mounted:

I would actually recommend ```
gksudo nautilus
``` in all cases rather than changing permissions. A graphical file manager is familiar, so fewer mistakes from unfamiliarity will be made, and you're less likely to completely break everything from simply moving files around than you would be changing permissions with imperfect knowledge. It wouldn't necessarily make any difference at all in this case, but habitually changing permissions on things is a Bad Plan.

---

### Post by 1jarwolf on 2017-06-29
> **johndough2 said:**
> Hi

I gotta ask...

old rig?

Is the CMOS battery still active?

To save any BIOS settings changes you make?

LOL! That is a good question. I do believe it is active.I disabled secure boot and it saved. Okay CatKiller, i will try to use nautilies. Hopefully this will work.

---

### Post by 1jarwolf on 2017-06-29
> **CatKiller said:**
> I would actually recommend ```
gksudo nautilus
``` 

Dang.... here is what i'm getting now.

```
root@Luc1fur:~# gksudo nautilus


(nautilus:27850): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (nautilus:27850): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
```

---

### Post by oldfred on 2017-06-29
Normally gksudo nautilus gave various errors when run from command line, but it worked.

---

### Post by 1jarwolf on 2017-06-29
So, after I run these commands, do I just reboot and hope it works? :D

---

### Post by oldfred on 2017-06-29
What have you changed?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by 1jarwolf on 2017-06-29
> **oldfred said:**
> What have you changed?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have went into my BIOS / firmware (before the pc boots up) and I then disabled secure boot as well as Legacy boot. Once I did all of that grub commands to actually boot in, I did gksudo nautilus and I got some errors. I have not tried to reboot yet. If I can't seem to fix this, I guess I can use this extra step as a security measure so that way I know no one will be able to power it on unless they have an ubuntu installation on a USB only then to press "c" and insert the grub commands lol. I am going to reboot and check. I have been trying to ride a little short story for shits and giggles. I will read up on these links you have provided and do the best to my knowledge.

Alright, it is not giving me a link to provide, so I am going to manually upload it to pastebin. I am also going to try to fix boot problems via Boot-Repair.

Well, now I am screwed. Nothing can be ran it gives me errors. i guess I have to reinstall Ubuntu...again.

---

### Post by CatKiller on 2017-06-29
gksudo nautilus just opens a file browser as root. You still need to actually do the things that oldfred has said; being in the habit of using a file browser rather than changing permissions willy-nilly is just safer.

---

### Post by 1jarwolf on 2017-06-29
[COLOR=#00ff00][U][I][B][SIZE=5]SOLVED
[/SIZE][/B][/I][/U][/COLOR]I want to thank all of you personally for helping me fix this dang boot problem! I can finally boot up normally now without having to go through all of those issues! My personal thanks to each and every one of you![COLOR=#00ff00][U][I][B][SIZE=5]
[/SIZE][/B][/I][/U][/COLOR]

---

### Post by shridhar-kapshikar on 2017-06-30
I would request you to boot your pc in 2 different booting options at a time. 
 - UEFI
 - non-UEFI mode
When you press F9(for my case) I see hard drive options with and without UEFI mode. Try these options and let me know.

---

