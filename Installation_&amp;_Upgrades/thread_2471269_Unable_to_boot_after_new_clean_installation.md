---
title: "Unable to boot after new clean installation"
date: 2022-01-25
forum: Installation &amp; Upgrades
---

### Post by stortall on 2022-01-25
Hi members,
I am new to the world of Ubuntu. I have some experience from working on it with already installed OS. But this is my first attempt to actually install it on a laptop myself. My laptop is a ~10 years old Asus U500V with good specs. It has been running win8 and win10 previously. Now I have installed Ubuntu 20.04 in it using a 16 BG usb stick. Installation went well with no errors I could see. I made the choice to erase all content on disk and install only Ubuntu. I dont want to keep windows. 

But after installation and reboot I was never able to boot into the OS. My computer stopped in BIOS. And I could not see any Ubuntu boot alternative in bios. So I followed the instructions on this page to repair boot. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

After boot repair i was actually able to boot once after selecting "Advanced options.." in GNU GRUB menu and selecting "Ubuntu with Linux 5.11.0-27-generic". In Ubuntu I did a "sudo apt update" and then decided to reboot. But after that reboot I have never again been able to boot into Ubuntu. I did another boot repair with no luck...

First attempt to repair:
[https://paste.ubuntu.com/p/Drn74hx8x6/](https://paste.ubuntu.com/p/Drn74hx8x6/)
[https://paste.ubuntu.com/p/nSfCXqRfcg/](https://paste.ubuntu.com/p/nSfCXqRfcg/)


secound repair
[https://paste.ubuntu.com/p/dYC39hFwFc/](https://paste.ubuntu.com/p/dYC39hFwFc/)

I get stuck in ash shell regardless what I do....
Please help /Johan

[https://ubuntuforums.org/attachment.php?attachmentid=289902&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=289902&stc=1)

---

### Post by Impavidus on 2022-01-25
At least it attempts to boot Ubuntu...

Is this BIOS/legacy mode or UEFI? If it came with Windows 8 preinstalled (released 9.5 years ago), it must have been UEFI and your boot-repair log confirms that, but you may have changed that setting. Many computers from those days have UEFI systems that don't really conform to standards, which makes it harder to install Ubuntu. I'm on a 10.5 year old laptop myself, running Xubuntu in legacy mode. Also, the hard drive appears to be in some sort of raid configuration. I don't know about that, but it could complicate matters.

---

### Post by stortall on 2022-01-28
> **Impavidus said:**
> At least it attempts to boot Ubuntu...

Is this BIOS/legacy mode or UEFI? If it came with Windows 8 preinstalled (released 9.5 years ago), it must have been UEFI and your boot-repair log confirms that, but you may have changed that setting. Many computers from those days have UEFI systems that don't really conform to standards, which makes it harder to install Ubuntu. I'm on a 10.5 year old laptop myself, running Xubuntu in legacy mode. Also, the hard drive appears to be in some sort of raid configuration. I don't know about that, but it could complicate matters.

Thanks for the reply Impavidus,

Im not sure if I have Bios Legacy mode or UEFI. I will attach two pictures of my situation. When I press power button I initially get to the GNU Grub window. From there I can choose UEFI Firmware Settings. And if I do, I get into BIOS. I believe that this is a Legacy BIOS? Because it looks old. How can I tell if I have UEFI? And if I dont have UEFI, how to I get it? Please, see my attached pictures.

BR
Johan
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289906&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289907&stc=1[/IMG]

---

### Post by tea for one on 2022-01-28
As you can reach the firmware set-up pages via Grub, I'm sure that you have UEFI.
From the screenshot, you have Secure Boot enabled.

If you disable Secure Boot, can you boot into Ubuntu?

---

### Post by stortall on 2022-01-28
> **tea for one said:**
> As you can reach the firmware set-up pages via Grub, I'm sure that you have UEFI.
From the screenshot, you have Secure Boot enabled.

If you disable Secure Boot, can you boot into Ubuntu?


Thanks tea for one for your suggestion. 
No, disabling Secure Boot did not solve it.  Im still ending up in Ash shell.
But I noted that my computer have some kind of RAID setting for the hard drives. Can this be a reason for my issues? In BIOS Advanced tab i can access SATA Configuration. And from there I can choose from IDE, AHCI and RAID. I think i have installed using the default RAID. But now, when I change this setting to either IDE and AHCI and reboot I can no longer get to GNU Grub menu. And the boot options for ububtu is telling me Drive Not Present. Is this a clue?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289911&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289912&stc=1[/IMG]

---

### Post by tea for one on 2022-01-28
Quite probably, the RAID setting is causing the problem.
My knowledge of RAID is limited.

Therefore, after 3 days, I would back up my data (if any) and re-install

_UEFI settings_

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to [COLOR="#0000FF"]AHCI[/COLOR] where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

_Ubuntu _

Boot into a live session in [COLOR="#0000FF"]UEFI[/COLOR] mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, keypad etc
Use gparted to create a GPT (GUID Partition Table)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Grub will find the EFI partition created by the installer
Sometimes (although very rare) internet connection prevents clean installation

---

### Post by stortall on 2022-01-28
> **tea for one said:**
> Quite probably, the RAID setting is causing the problem.
My knowledge of RAID is limited.

Therefore, after 3 days, I would back up my data (if any) and re-install

_UEFI settings_

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to [COLOR=#0000FF]AHCI[/COLOR] where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

_Ubuntu _

Boot into a live session in [COLOR=#0000FF]UEFI[/COLOR] mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, keypad etc
Use gparted to create a GPT (GUID Partition Table)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Grub will find the EFI partition created by the installer
Sometimes (although very rare) internet connection prevents clean installation


Thanks tea for one!

It finally boots now!!!!! Problem solved!


[LIST]
[*]I used your suggested settings above, exept the ones I could not find in my BIOS (Disable Legacy mode, Disable TPM or PTT, Disable Optane memory and storage). 
[*]I created a new USB of Ububtu 20.04 using Rufus on one of my Win10 machines. I configured Partition scheme as GPT and Target system as UEFI (non CSM). 
[*]Booted on the USB and selected Try Ubuntu 
[*]Started gparted and fiddled around with setting Device>Create Partition Table and selecting gpt on all my drives. At this stage I still had two drives called something like "/dev/mapper/isw_bjcceijahe_RAID0" but also one "/dev/sda". And I dont remember exacly, but i had some starge errors when trying to create partition table for /dev/sda. 
[*]I started installing Ubuntu, initially I tried selecting /dev/sda as my drive, but it was unsuccessful. So I went for one of the "/dev/mapper/isw_bjcceijahe_RAID0". 
[*]After installation I could still not boot. 
[*]So I booted into Ubuntu from the USB to try to make a Boot repair using [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). But it failed due to "RAID is not active". 
[*]So I started all over again from the beginning. And luckely this time when I entered gparted I had only two drives avalible /dev/sda and /dev/sdb, 128 GB each. So finally the strage RAID drives had disappeared. 
[*]I created Partition tables "gpt" for both drives, and installed Ubuntu on /dev/sda. 
[*]Everything boots perfectly and problem is solved! 
[/LIST]

Thanks for all help! Im so happy I can run ubuntu now without having to buy a new laptop! :-)

---

### Post by tea for one on 2022-01-28
That's good news.
Please mark the thread as solved, other forum users/searchers may find the info helpful.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

