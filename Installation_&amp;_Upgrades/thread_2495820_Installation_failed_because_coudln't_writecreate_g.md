---
title: "Installation failed because coudln't write/create grub on /dev/sda"
date: 2024-03-02
forum: Installation &amp; Upgrades
---

### Post by jfca283 on 2024-03-02
Hello, 
I tried installing Ubuntu on my PC.
I already have W10 on It. It's a bit old, using the legacy mode on BIOS.
I could partition, format. and write some files on the extf4 filesystem.
But at the last minute, I received the warning:
[FONT=Arial Black]Executing 'grub-install /dev/sda' failed. This is a fatal error[/FONT]
What can I do about it?
This is the first time I encounter an error like this.
Many times I've installed Ubuntu on a system with Windows.
Thanks for your time and interest.

---

### Post by TheFu on 2024-03-02
Search other threads here for how to gather data so you can get some help.  **Boot-Repair** or **system-info** are the two most popular methods to gather the information needed for the experts to help.

BTW, I'm not a booting expert, so my post here is just so you can go do one of those things the smart way, do no harm, and post information. Don't actually do anything and certainly don't attempt to repair (using boot-repair) until someone specifically ask you to. It might wipe your system, including MS-Windows.

---

### Post by oldfred on 2024-03-02
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012. So did you install Windows yourself to have it in old BIOS/MBR mode?
Note vendors may call it BIOS, but it probably is UEFI and gives option to boot installer in UEFI or BIOS/CSM/Legacy mode.
But new systems starting in 2020 may be UEFI only. My Dell says BIOS, but once in "BIOS" it says UEFI only.

What brand/model system? What video card/chip?

---

### Post by jfca283 on 2024-03-05
It's a Intel Q87 express.
The model computer is a HP Elitedesk mini g1.
I installed W10 using Rufus and I was forced to using the MBR mode.
The first time I tried using UEFI on Rufus and the PC didn't let me move on.
Besides, I can't access the BIOS in order to change the boot sequence or mode.
I really want to use Ubuntu and not W10.

By the way, I don't know if the whole Ubuntu is installed and only the GRUB needs to be configure.
I mean, the message was fatal...
My thoght is that the MBR needs to be repaired.

---

### Post by TheFu on 2024-03-05
Intel Q87 express is the motherboard, not the CPU.  There's a reason we asked for specific tools to be used to gather information. All the data they provide is needed to provide advice. **Please provide it.**  Not providing doesn't help you boot/install Linux.

Some of the older and cheaper computers from HP and Acer had very limited BIOS options, which is really too bad, since they effectively lock people into 1 OS only.  I don't know about this specific model, but when my LUG did installfests with 50+ people each semester getting help with their Linux installs, the HP and Acer laptops tended to be the only ones with restricted access to BIOS.  Of course, that definitely doesn't apply to most HP or Acer systems.  I had an Acer chromebook that I was able to wipe ChromeOS off and run Linux. I understand some people even got MS-Windows to run.

As a workaround, you can probably run Ubuntu - or a flavor of Ubuntu - inside a virtual machine under Win10 using virtualbox. Whether this is possible depends on the CPU and the BIOS allowing VT-x to be enabled, which is required for 64-bit OSes to run in a virtual machine.

---

### Post by oldfred on 2024-03-05
That system should be UEFI as specs say it supports Intel Core i3,i5,i7 4 series chips.
HP is not particularly UEFI friendly.
You have to access UEFI to change boot order settings to have Ubuntu as first in boot order once installed.

If drive is gpt and you install in BIOS boot mode, you need a bios_grub for grub to install.
If drive is gpt and install in UEFI mode you must have an ESP - efi system partition for grub to install.

Really need Boot-Repair's report to really suggest anything more.

If you have issues getting in UEFI/BIOS, you may need to "cold" boot or full power down.
Then turn off fast boot setting in UEFI as that assumes no system changes & automatically boots.
With fast boot off, system scans hardware for what you have & writes to drive, giving just enough time to press correct key to get into UEFI settings or boot menu.

HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios settings

---

### Post by jfca283 on 2024-03-05
As you say, when I boot using F2 or F12, I can't access anything related to the BIOS in the HP elitedesk.
I have an old Optiplex in which I can switch UEFI or LEGACY as boot option.

---

### Post by oldfred on 2024-03-05
HP does not use f2 or f12. They have to be different.

---

