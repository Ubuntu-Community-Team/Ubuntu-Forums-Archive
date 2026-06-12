---
title: "Repair boot configuation"
date: 2020-04-02
forum: Installation &amp; Upgrades
---

### Post by somath1 on 2020-04-02
Hi,

I bought a SSD card for my laptop where I installed Lubuntu 19.10 using a bootable USB. The installation process went fine (just followed the instructions on internet) but unforthunatly I couldn‘t see Lubuntu as an option on my BIOS menu. When trying to solve this proble I booted again to the USB and installed Gparted....That‘s were things got worse, when trying to solve the issue, I deleted the boot partition that was on my Primary Disk need to boot Windows 10..As a result I can‘t boot now neither my Windows or the installed Lubuntu on the SSD because I can‘t see both of them on the BIOS menu.

I have read many posts and tried diffrent solutions but I still didn‘t manage to solve the problem. I‘m completely new to Ubuntu/Linux and thus having more issues understanding what to do. I have tried Boot-Repair but when launching the test I get an error saying that I need to creat a GPT boot partition first. I also tried under advanced options to repair the GRUB did not solve the problem (may be wrong options ?).
The Windows partiton with all my data seems to be fine. 
I would be very grateful if you could help.
Ideally I would like to get windows running again with my current data and have lubuntu running on the SSD card.

P.S: wasn‘t sure which system information to include into my post.

---

### Post by oldfred on 2020-04-02
Post the link to the summary report from Boot-Repair.
If Windows is UEFI, you need an ESP - efi system partition with Windows UEFI boot file.
Normally when you install Ubuntu in UEFI mode it will use that same ESP.

If Boot-Repair is suggesting a bios_grub partition, you have booted in BIOS/Legacy/CSM boot mode. And drive is gpt. Windows only installs in UEFI boot mode to gpt drives. So Windows just about has to be UEFI unless on another drive.
Unless you have old Windows or manually installed it yourself in old BIOS mode, always boot in UEFI mode.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by somath1 on 2020-04-03
Hi !

Here is the summary: 
[https://paste.ubuntu.com/p/CXyNkfC48M/](https://paste.ubuntu.com/p/CXyNkfC48M/)

I tried to switch back to UFI  and install GRUB on the boot partition of windows...now I get a black screen when booting (GRUB Screen) when I type ls I don‘t see my SSD.

---

### Post by oldfred on 2020-04-03
Grub in UEFI boot mode installs to the ESP - efi system partition, not to Windows. Although Windows will use same ESP for booting.

Are you reformatting ESP? 
You show many mounts of the ESP in your fstab. Hope you backed that up first as Windows would have its boot files in the ESP.

I do not see any SSD, just the MMC device (which is not an SSD).

---

### Post by somath1 on 2020-04-03
Thank you, I did now fixed Windows by adding the BOOT64x.efi file to the windows ESP (Used a bootable USB with windows and did it through the prompt command).

I also deleted All other mounts on the ESP.
So my windows is booting proberly. 

Now I tried going back to Lubuntu through the Bootable USB and I did formated the SSD (it‘s a mSATA SSD 240GB Trascend) and tried to install again Lubuntu, this time using these instructions: 

[https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives](https://askubuntu.com/questions/726972/dual-boot-windows-10-and-linux-ubuntu-on-separate-hard-drives)

So current state is:
I can see an option on my boot orders called UEFI-OS (along withe the windows one)
When I do try to boot through it, I get a GRUB2 screen and again GRUB2 doesn‘t seem to find the /root partition on the SSD.

I don‘t get what is here causing an issue

---

### Post by oldfred on 2020-04-03
What brand/model system?
What video card/chip?

Some do require extra boot parameters or settings.

It could be that you are trying to boot from previous grub and you new install did not update that version of grub. So then it is not looking for the correct UUID for / (root)?

Have you posted latest summary report from Boot-Repair?
Since MMC, post the grub.cfg in /EFi/ubuntu/grub.cfg. Should be 3 lines and refer to UUID of your install.
If not booting you can mount ESP partition and drill down to that file.

---

### Post by somath1 on 2020-04-04
Here is the last summary:
[https://paste.ubuntu.com/p/JmjqsyvRmQ/](https://paste.ubuntu.com/p/JmjqsyvRmQ/)

The grub.cfg is in the directory you mentioned and has the following lines:
search.fs_uuid 6ba6f5ad-26d6-4586-b306-98888e32ec32 root hd1,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

I have a Jumper EZBook 3 Pro
and the SSD is: Transcend 240GB SATA III 6Gb/s MTS420S 42 mm M.2 SSD 420S SSD TS240GMTS420S

---

### Post by oldfred on 2020-04-04
Not showing SSD.
I would see if you can update firmware on SSD, many have had to do that to have SSD seen or seen correctly.
If you can update UEFI on system I would update that also.

You do not show a typical UEFI boot entry for Ubuntu.
The one entry is like when you have disconnected a drive & it defaults to some settings.

If you boot the UEFI OS entry what does it boot.
That is using the fallback entry /EFI/Boot/bootx64.efi.  Systems originally have that as a copy of Windows boot file and grub now installs that as a copy of its shimx64.efi. Boot-Repair will also copy shim to bootx64.efi, so fallback entry will also boot Ubuntu. But you should have Ubuntu entry also.

---

