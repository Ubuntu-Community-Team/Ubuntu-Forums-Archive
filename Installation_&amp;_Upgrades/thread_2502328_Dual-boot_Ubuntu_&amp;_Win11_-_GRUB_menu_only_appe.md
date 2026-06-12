---
title: "Dual-boot Ubuntu &amp; Win11 - GRUB menu only appears on 2nd restart"
date: 2024-11-10
forum: Installation &amp; Upgrades
---

### Post by uacnt83982803 on 2024-11-10
Maybe hard to explain - I have a PC with Ubuntu installed on one partition, and on the other partition I installed Windows 11 (replacing a Windows 10 install that was there originally).  The Ubuntu partition had been an unused partition before.

Anyway, both OSs run fine.  The issue I'm having is, I seem to have to hard restart the machine twice in order to get the GRUB boot selection menu to appear so that I can select Windows to boot.

I am using legacy BIOS.  I have the BIOS set to display boot options (hard drive, network and one other).  This menu always appears.  I select the hard drive option and initially, the machine proceeds to immediately booting Ubuntu.  I have to force a shutdown then repeat this sequence, then on the 2nd round the GRUB menu appears, I can arrow down to select Windows, and boot it.

I am wondering if the GRUB menu is actually appearing on the first try but so briefly that I can't see it (or change the selected line item)?

I have never messed with GRUB before, so I'm not sure where to start.  My hunch is to boot off a Ubuntu bootable USB then see if I can view the GRUB file on the hard drive?

---

### Post by grahammechanical on 2024-11-10
BY default Grub has several seconds delay to allow selection of boot options. The configuration file does not get rewritten after every boot.

My guess is that you have Grub boot files in two different locations. In one location Grub only has Ubuntu as a boot option. Whereas the Grub in the second location has both Ubuntu and Windows as boot options. It is only when Grub detects more than one operating system that the Grub boot menu appears.

When Ubuntu loads without a Grub menu run this command in the terminal.

```
sudo update-grub
```

What does the printout show you? Is Windows detected? If it is see if that solves the problem. I do not know what to advise if you really do have Grub boot files in two locations.

Regards.

---

### Post by oldfred on 2024-11-10
If above suggestion does not work.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by uacnt83982803 on 2024-11-10
So executing sudo update-grub seemed to help.  It updated the Windows entry at the bottom from Windows 10 to Windows 11.  It completed normally.
  ```

Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-48-generic
Found initrd image: /boot/initrd.img-6.8.0-48-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 11 on /dev/sda1
Adding boot menu entry for UEFI Firmware Settings ...
done

```

I updated the BIOS to remove the boot device display (still leaving the boot order with USB first before hard disk if needed for other updates later).  

Via testing, I have proven that if I boot Windows, shut down, then restart (hard power down and power on), it reliably presents the GRUB menu each and every time and it boots whichever OS I select.  I tried this a lot and I'm very confident that this works perfectly.

If however I select Ubuntu in the GRUB menu, it boots it but then upon power off, the next power on it will not display the GRUB menu.  I have to boot and shut down Ubuntu multiple times (3-4) before  I get the GRUB menu.

---

### Post by uacnt83982803 on 2024-11-11
Ok here's the results from the BootInfo summary report:

[http://paste.ubuntu.com/p/mjcFjhMmYp/](http://paste.ubuntu.com/p/mjcFjhMmYp/)

---

### Post by oldfred on 2024-11-11
Grub only boots working Windows. That also means Windows fast startup must be off, bitlocker must be off & chkdsk not required.
you show bitlocker, not sure about other.

You have to use your Windows repair/recovery flash drive to restore a Windows boot loader to MBR and boot Windows to make fixes.
Then restore grub boot loader to MBR to dual boot. 

You have the old BIOS/MBR configuration used primarily with Windows 7.
When Microsoft released Windows 8 in 2012, it required vendors to install in UEFI boot mode to gpt partitioned drive.
But now conversion from MBR to gpt, usually totally erases entire drive. Or total reinstall & restore from backup required.
With UEFI, you can boot all installed systems directly from UEFI boot menu, without reinstalling boot loaders. Both Windows & grub share one ESP without issue.

---

### Post by uacnt83982803 on 2024-11-11
> **oldfred said:**
> Grub only boots working Windows. That also means Windows fast startup must be off, bitlocker must be off & chkdsk not required.
you show bitlocker, not sure about other.

You have to use your Windows repair/recovery flash drive to restore a Windows boot loader to MBR and boot Windows to make fixes.
Then restore grub boot loader to MBR to dual boot. 

You have the old BIOS/MBR configuration used primarily with Windows 7.
When Microsoft released Windows 8 in 2012, it required vendors to install in UEFI boot mode to gpt partitioned drive.
But now conversion from MBR to gpt, usually totally erases entire drive. Or total reinstall & restore from backup required.
With UEFI, you can boot all installed systems directly from UEFI boot menu, without reinstalling boot loaders. Both Windows & grub share one ESP without issue.

Thanks for your input, but I am having difficulty in understanding which of your comments are facts that you've discerned by looking over the report, and which if any are steps you suggest I take to resolve the issue.

As of right now, if I boot Windows I get the GRUB menu every time upon next power up.  If I boot Ubuntu I generally have to shut it down a few times in order to get the GRUB menu to appear again (so I can select Windows if that's what I want to bring up).

Should I proceed with the automated repair that the boot repair has identifed?

---

### Post by oldfred on 2024-11-11
With BIOS, you have boot loader in MBR or first sector of drive.
And with only one drive/MBR, you can only have one boot loader in MBR.
Windows will not dual boot. Grub will dual boot if Windows has no issues.

Boot-Repair is just suggesting to reinstall grub boot loader to MBR.
If Ubuntu now boots, then reinstalling grub will not fix anything, issue is with Windows.

To fix Windows you have to boot into it or use a Windows repair/recovery flash drive to repair it.

Generally Boot-Repair is only to fix Linux/grub issues. 
But since you have old BIOS install, Boot-Repair in advanced mode can install a Windows type boot loader (syslinux) to MBR to boot Windows.
Then after you fix Windows you can use Boot-Repair to restore grub to MBR.
But better to have Windows repair tool to fix Windows & Ubuntu live installer/Boot-Repair to fix Ubuntu issues.

And you need really good backups of both Windows & Ubuntu.

---

### Post by uacnt83982803 on 2024-11-11
Ok.  So I don't have an install disk for Windows.  I just have a Windows 11 ISO image on a USB stick.  Is there a way to fix the Windows issue from within Windows?

If I go into the Windows system settings and look at the Boot tab, there's only the one OS listed (Windows 11).  I should see Ubuntu if everything was 100%, correct?

Update: I found that if I hold down the shift key when I power up the machine, the GRUB menu always appears as expected.  Is that indicative of some specific issue that I can remedy?

---

### Post by tea for one on 2024-11-11
> **uacnt83982803 said:**
> Update: I found that if I hold down the shift key when I power up the machine, the GRUB menu always appears as expected.  Is that indicative of some specific issue that I can remedy?
I would suggest that you edit /etc/default/grub

Boot into Ubuntu and open a terminal
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]# change hidden to menu[/COLOR]
GRUB_TIMEOUT=10 [COLOR="#0000FF"]# change 0 to 10[/COLOR]
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"]# add this line[/COLOR]
```
Ctrl o to save and Ctrl x to exit
```
sudo update-grub
```
Power off and power on
Any good?

---

### Post by tea for one on 2024-11-11
Can you tell us which files and folders are contained in /dev/sda1  
```
              Avail Use% Mounted on
/dev/sda1    69.7M  30% /mnt/boot-sav/sda1
```

---

### Post by uacnt83982803 on 2024-11-11
That did the trick!  Thank so so very much!

---

