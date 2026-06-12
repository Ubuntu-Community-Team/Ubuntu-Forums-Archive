---
title: "[ubuntu] multibooting UFD w/ GNU GRUB 2.04, any concern with updates?"
date: 2022-02-13
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-02-13
Hi! Long time no see, y'all.

So, I'm a little different, and I prefer to use a UEFI bootable UFD (USB flash drive) to house GNU GRUB 2.04 and it's /EFI/boot/grub.cfg and /EFI/boot/bootx64.efi files. So, obviously the PC uses UEFI firmware (AMI circa 2014). I used the option to "Boot Other OS" in the Secure Boot to make things easier. I prefer to select the boot order in the UEFI firmware, making the UFD EFI the first boot item, and Windows 10 second. This works just fine, unless I remove the UFD and boot, then it swaps the boot order back, but that's not a big deal to me, since I mostly leave the UFD inserted for every boot. I manually added menu entries for Windows 10 and the kernel that came with Ubuntu 21.10 Desktop to the grub.cfg.  Basically I used Windows disk management GUI to shrink a drive and give myself 100 Gibibytes for GNU/Linux and other OS. I installed 21.10 Desktop version (minimal install option)  using the ubiquity -b command, and manually partitioned and assigned mount points to a /boot and / (root) primary partitions on a different HDD than the GPT one Windows 10 uses for C:, EFI and recovery. Boot is 250 Mb and root is the rest. RedHat advises using a separate /boot, but I guess this wasn't strictly necessary. Maybe I should have made a separate /home, but I didn't.

Anyway, I'm mostly using ssh to remote in. To get the system up and running I attached it to a monitor and used the GUI updater to get the latest updates (the mounted Ubuntu iso is also used as a source). Also in the shell I ran 'sudo apt update' and then installed some stuff with 'apt-get install' such as openssl-server.

Now, here's my question! In this desktop distro, are there any automatic updates, or any updates that would alter the way I'm booting? It's been a while since I messed with this stuff, but I don't want GNU GRUB to be automatically updated (to the wrong place) or anything like that.

So far, so good, and the system works fine. I'm mostly going to use it to build software (coreboot hopefully), and I suppose I didn't really need a desktop, but I like Ubuntu. It should work fine for building software, I would assume, with the correct packages installed. I suppose the server version of Ubuntu would have worked.

Thanks, and have a great day!

---

### Post by oldfred on 2022-02-14
Windows updates typically make Windows first in UEFI boot order.
Grub updates typically make Ubuntu/grub first in UEFI boot order.

If you do not have the mount of the ESP in your fstab, not sure if updates would run or not.

External drives boot from /EFI/Boot folder. The /EFI/Boot/bootx64.efi file/folder for an internal drive is a fallback boot entry and bootx64.efi may a copy of Windows efi boot file or shimx64.efi boot file.

---

### Post by MAFoElffen on 2022-02-14
Two other caveats... that are related.

Windows sets itself as the first to boot, because during updates, if it needs to reboot to complete an update, it needs to get back to the Windows Boot to complete the update. That does not mean that it won't work, just that if you have Grub / Ubuntu as the first boot, that if doing a Windows update, that you need to be there watching it, to interact, went it boots, to select "Windows" to boot into from the Grub boot menu, to complete the "Windows update".

Next, if you have multiple Linux Installs present, whichever was installed last, controls the Grub Boot menu you see (&& when after you do update-grub) during a boot. Unless one of Grub updates, updates the EFI files... If the later, an update of Grub, where there are multiple versions of Linux Installed, could and can change "which" Grub Menu you see on Boot.

On update-grub, if multiple versions of Linux installed, if you do not see update-grub menu changes on bootup, it could just mean that "that" installation may not be controlling the 'primary' Grub Menu shown on bootup...

Same answer as oldfred. Just expanded.

---

### Post by breakdaze on 2022-02-14
Thanks! The caveat about Windows makes perfect sense. I currently have Ubuntu first, so the timeout ends and automatically boots to it, so that's a good point.

So, basically, I can just choose to not use update-grub, I guess. I installed Ubuntu using the ubiquity -b so it didn't install grub, because I already had grub installed. So, basically I could install more versions of Linux, and just not have them install grub, and make my own menu entries manually, like I did here.

---

### Post by MAFoElffen on 2022-02-15
Yes. Manually, or turn OS_Probe back on, for it to find other OS'es.

I rarely use update-grub unless I have made some changes that I want to renew or implement. It's not something someone uses everyday on the same machine.

Always good to do backups before doing something that could be risky... LOL. From experience.

---

### Post by breakdaze on 2022-02-15
Thanks! Wow, I first registered in 2005!? I forgot how long it has been, ha ha. I used Linux Mint for a time, then I didn't have a computer for a few years. Getting back in the saddle over the last few years.

---

### Post by oldfred on 2022-02-15
Some more info on creating you own grub entries so you do not have to maintain them as much.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)

---

### Post by breakdaze on 2022-02-15
Thanks. Helpful. It has been some time, but now I remember I started making partition labels like that. I don't think I need to do the sudo update-grub in my experience. I'm not sure why the guide says you need to. It seems to work fine making manual entries. And yes, as soon as you add another drive or partition, then the order can change. So, yes, sometimes I use the grub shell with ls command to ferret out what drive is what. I guess I should do grub-mkconfig - o /mypath/ because I have it somewhere else than /boot/grub

Currently I don't use the search nor --set=root for my menu, and I do like putting a background picture and all of that. Certainly there is a benefit of the search function, as I said before, if things change order. I used to hose things up all the time, so that's why I shy away from putting grub into the EFI partition, and the grub.cfg in the boot partition and just use the USB flash drive for it.

I will certainly play with it some more, thank you kindly.

---

### Post by breakdaze on 2022-02-16
I suppose the best way for the custom menu entries is to edit the /etc/grub.d/40_custom file, eh? I guess that is the way I used to do it. Also I can add grub variables to /etc/default/grub then run the grub-mkconfig -o /media/USB/EFI/boot (configuration path for grub.cfg based on Clonezilla Live, native path when not mounted /EFI/boot/grub.cfg).

---

