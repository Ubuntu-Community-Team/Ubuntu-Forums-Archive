---
title: "After installation and upgrate Ubuntu crashed"
date: 2018-02-04
forum: Installation &amp; Upgrades
---

### Post by jfmoura on 2018-02-04
Hi everyone!

I'm a old user of Ubuntu and recently buy a HP Omen 15-ce016ns.
I made space in my hard drive for Ubuntu(dual boot W10/Ubuntu 16.04.3 LTS) then updated and reboot it, everything looks good until I enter my login, the laptop don't do anything but I still can move the mouse.
I installed Ubuntu again but this time the laptop chashes just booting with the errors below, Windows 10 work well:

[    0.034366] ACPI Error: [GPLD] Namespace lookup failure, AE_ALREADY_EXISTS (20170531/dswload-378)
[    0.034371] ACPI Exception: AE_ALREADY_EXISTS during name lookup/catalog (20170531/psobject-252)
[    0.034371] ACPI Exception: AE_ALREADY_EXISTS (SSDT:838F    ) while loading table (20170531/tbxfload-228)
[    0.035600] ACPI Error: 1 table load failures, 13 successful (20170531/tbxfload/246)
[    1.535411] ACPI Error: [DSSP] Name space lookup failure, AE_NOT_FOUND (20170531/psargs-364)
[    1.535417] ACPI Error: Method parse/execution failed \_SB.PCIO.SATO.PRT2._GTF, AE_NOT_FOUND (02170531/psparse-550)
[    1.537033] ACPI Error: [DSSP] Name space lookup failure, AE_NOT_FOUND (20170531/psargs-364)
[    1.537036] ACPI Error: Method parse&execution failed \_SB.PCIO.SATO.PRT2._GTF, AE_NOT_FOUND (02170531/psparse-550)
/dev/sda3> recovering journal
/dev/sda3> clean 229615/29810688 files, 3213228/119239424 blocks
[    7.107013] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed 4087f flag0x201] vs feed40080 f80
[    7.107054] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed 4087f flag0x201] vs feed40080 f80
[    8.059382] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170531/dsopcode-235)
[    8.059415] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059348] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059499] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170531/dsopcode-235)
[    8.059525] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059551] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059598] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170531/dsopcode-235)
[    8.059625] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059560] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059797] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170531/dsopcode-235)
[    8.059825] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059852] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059899] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170531/dsopcode-235)
[    8.059926] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[    8.059591] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170531/PSPARSE-550)
[   40.084001] watchdog: BUG: soft loup - CPU#2 stuck for 23s! [plymouthd:409]
[   68.084001] watchdog: BUG: soft loup - CPU#2 stuck for 23s! [plymouthd:409]
[   74.132001] INFO: rcu_sched self-detected stall on CPU 
[   74.132043] |2-...: (15000 ticks this GP)
[   74.132062] | (t=15001 jiffies g=580 c=579 q=998)
[  100.084001] watchdog: BUG: soft loup - CPU#2 stuck for 23s! [plymouthd:409]
[  128.084002] watchdog: BUG: soft loup - CPU#2 stuck for 23s! [plymouthd:409]


I had a hard time transcribing that :-/ :-D

Help me please!

---

### Post by Jay_E on 2018-02-04
Hi,
general suggestions:
   At the grub boot - select the memory test if you have it and let it run 2 full passes. 
       If you don't have it installed, you can make a memtest boot USB stick using LiLi running on windows
    This will rule out a memory problem.

   
  Having the right video driver may be a more likely problem
   It sounds like the basic driver works during boot, but there are problems when Ubuntu starts up the more advanced driver..

   Can you get to the advanced Ubuntu startup selection an get to a root prompt? 
    That should run from a more basic video driver.
     sudo lshw | more
      should find the hardware for the video.  (Nvidia, Radeon, etc and chipset.)
       You can reboot Windows and then search for the Ubuntu package name for that driver
      Reboot; got to the advaced startup and drop to a root prompt.
        search for the package and see if it is installed. Install or re-install....

        Try a fresh boot
        If problems persist, drop back to the root boot and check logs in /var/log

I hope this is helpful.
Jay

---

### Post by cruzer001 on 2018-02-04
> ACPI Error: Namespace lookup failure

If you google that, you will get several hits.

The most promising one I see is to use only UEFI when installing linux.  Assuming thats a option for you.

Updating bios and noacpi are other possibilities.

[https://www.linuxquestions.org/questions/linux-hardware-18/acpi-error-what-means-4175605357/](https://www.linuxquestions.org/questions/linux-hardware-18/acpi-error-what-means-4175605357/)

[https://askubuntu.com/questions/953666/acpi-errors-when-booting-cant-boot](https://askubuntu.com/questions/953666/acpi-errors-when-booting-cant-boot)

Edit
Ok, got sidetracked on a matter of high importance (breakfast).

> watchdog: BUG: soft lockup

Best hit:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1530405)

Some have solved this with a kernel upgrade, others by changing the graphic driver and yet others with different fixes.  The launchpad ticket remains "high importance", probably waiting for a upstream fix.

---

