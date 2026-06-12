---
title: "Computer not working after failed installation"
date: 2019-07-13
forum: Installation &amp; Upgrades
---

### Post by whynony on 2019-07-13
I'm new to linux , actually I've just bought a computer with linux for the first time and it had ubuntu 16.04 I tried upgrading after I got the computer , I used [https://tecadmin.net/upgrade-ubuntu-16-04-to-ubuntu-18-04-lts/](https://tecadmin.net/upgrade-ubuntu-16-04-to-ubuntu-18-04-lts/) this as a refrence and after the sudo do-release-upgrade it just overflew text , and did nothing , I terminated the console , then I redid the steps after sudo dist-upgrade it started downloading and installing and then it just failed at the display manager part, I tried restarting and it's just stuck in a black screen booting cycle , i'm kinda panicking , what should I do?

---

### Post by TheFu on 2019-07-13
Linux has a very steep learning curve when something bad happens.

I would restore from the full system backup I made before starting and stick with 16.04 for a few months as I learned more about Linux.  Expecting Linux to work like Windows is a bad idea.  Linux expects responsible users - users who make backups that can be restored.

Doing a release upgrade is like pulling the engine from your car.  Would you do that without a plan to put it back?

Were there any issues with the update/upgrade process?  If there were, fix those first.

I have no idea what *sudo dist-upgrade* is. Being 100% accurate with what you post here is very important.  Details matter greatly.

On Linux, you'll need to check log files (most are in /var/log/)  and for some commands like *do-release-upgrade*, you should create log files so if anything bad happens, you can show EXACTLY what happened.

Just a wild thought - If you just bought the computer, perhaps the seller could do the 18.04 upgrade for you?

---

### Post by TheFu on 2019-07-13
I completely forgot .... to get a working computer again, you'll probably need to boot from installation media. That would mean doing these steps:
* download the ISO for the specific release you want.
* follow instructions to create a flash boot USB drive or burn it to a CD or DVD.  There are specific instructions for whatever desktop you have - Windows, Linux, OSX.  [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0) has links for Linux and OSX too.
* take the boot media and put it into the new laptop and boot it.
* on the first screen, in theory, you should see "Try Ubuntu" or something similar for any non-Server install. Choose that.  If you don't get any menu of options, it is likely a GPU incompatibility that needs a few boot options.  I've never had this issue, but some hardware does.

From inside the "Try Ubuntu" environment, we can fix any software/OS issues.  It is smart to have a flash drive setup just for this reason.  We can also troubleshoot most hardware issues without worrying about whether the installed OS settings are causing the issue.  Very handy.

---

### Post by whynony on 2019-07-14
Sorry I didn't respond for a long time , had to get a working computer and an USB, which took a while.


The USB doesn't seem to be booting, even though I installed it with rufus like the guide said , what should I do , the computer is a laptop , that doesn't have a CD/DVD drive...
PS:The booting looks like flashing black screen every 5 seconds.

Right so I used the rufus tool to create a flash drive that uses GPT partition scheme , target system UEFI (non CSM) ,file system NTFS and it kinda worked, this time I booted a windows 10 iso , it brought up a console (I think , I can type there)
it says the following:

[0.118969] ACPI Error: Method parse/execution failed \_SB.PCI0.RP12.PXSX. AE_NOT_FOUND (20170531/psparse-550)
[0.121896] ACPI Error: [\_SB_.PCI0.RP05.PXSX.HIST] Namespace lookup failure, AE_NOT_FOUND (20170531/psargs-364)
[0.121896] ACPI Error: Method parse/execution failed \CNDP. AE_NOT_FOUND (20170531/psparse-550)
[0.121896] ACPI Error: Method parse/execution failed \. AE_NOT_FOUND (20170531/psparse-550)
[0.274137] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274151] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274163] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274173] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274184] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274195] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274205] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[0.274216] ACPI Exception: AE_NOT_FOUND. Evaluating _PRS (20170531/pci_link-176)
[[B

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium cointaining a live file system


Oh and before this pops up, I can choose either 
Dell recovery or Dell (safe graphics mode)

---

### Post by pascua28 on 2019-07-22
You may also try to create a fat32 partition on your hard drive. Give it about 4GB. And then open the iso file in windows and copy all the contents to the newly created fat32 partition. On hp, there is an option to select a boot device, so you may have to find it on your computer too. Also, disable secure boot from the bios settings

---

