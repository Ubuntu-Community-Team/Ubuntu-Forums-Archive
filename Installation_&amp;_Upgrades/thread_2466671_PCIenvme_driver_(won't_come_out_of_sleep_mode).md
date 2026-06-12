---
title: "PCIe/nvme driver (won't come out of sleep mode)"
date: 2021-09-02
forum: Installation &amp; Upgrades
---

### Post by matt-hammond on 2021-09-02
Hello Kind People,

Just joined the forum...so...Hello. I recently bought a new HP laptop because my old dinosaur struggled with music production. It has a Samsung SSD PCIe/nvme drive. I put Ubuntu on it but then realised that when I press the power button to put it to sleep, the computer goes to sleep but won't come out of sleep when I repress it. I went to a computer repair shop today and the guy said I needed to install a driver to solve this issue. I have no idea what to do. I am capable of etching .iso files to make a bootable USB but I don't know how I would add the driver. Any advice appreciated.

Best Wishes

Matt Hammond

---

### Post by grahammechanical on 2021-09-02
Are you pressing the physical power off button? Or, are you pulling up the Power Off/Log Out menu from the power button icon at the top right of the screen.

If we open system settings>Power we see options there. You may have options I do not have because I am using a desktop machine. The options I have are for Automatic Suspend when idle. I can set a time interval. And then there is the option for the Power Button Action. It can be set to Suspend, Nothing or Power Off.

I may be wrong but I think that this action refers to the power button icon and not the physical power button of the machine. If it is possible to put the hardware into sleep mode when pressing the physical power button then I suggest putting Ubuntu into suspend mode before putting the hardware into sleep mode. I have no idea if this suggestion is any good.

Suspend and hibernation are complicated things. There is suspend to RAM where the state of the OS is saved in memory and much of the electronics is powered down but not the memory chips. And then there is suspend to disk where the state of the OS is saved on the hard drive and almost all of the electronics is powered down including the memory and hard drive.

Machines pre-installed with Microsoft's Windows will work according to the claims of Microsoft and the manufacturer otherwise they will not be fit for sale. The same will be true if we purchased a machine pre-installed with Linux/Ubuntu. When we self-install Linux we are happy with what we get.

Regards

---

### Post by matt-hammond on 2021-09-02
Thanks for getting back to me. I am talking about the physical power off button. I am used to just pressing it when I go out and pressing it again when I come back. The button puts the laptop to sleep but doesn't bring it back to life. It just annoys me. I didn't have this problem with the other machine with the same OS. The computer repair guy told me to it's a problem with the Samsung PCIe nvme drive and that I need to add a driver. But how to add this driver?

---

### Post by tea for one on 2021-09-02
> **matt-hammond said:**
> I am talking about the physical power off button. I am used to just pressing it when I go out and pressing it again when I come back.
Is that a Windows 10 feature?
> **matt-hammond said:**
> It just annoys me.
Windows 10 features do not automatically transfer to Ubuntu.
Rather than getting annoyed, why not just power off the laptop when you go out?
> **matt-hammond said:**
> The computer repair guy told me to it's a problem with the Samsung PCIe nvme drive and that I need to add a driver. But how to add this driver?
What is this driver?
Have you downloaded it?

---

### Post by matt-hammond on 2021-09-02
I don't what the driver is. I haven't downloaded it. I don't want to switch off the laptop completely until the night. I might come back half an hour later after going out and just bring it back to life...It not a Windows feature. It should just work. The problem is the lack of this driver. I am looking for advice as to how to get the driver and how to install it.

---

### Post by Dennis N on 2021-09-02
Instead of using the Power Button, try the "Suspend when laptop lid is closed" setting in Tweaks. Maybe that will work better.

---

### Post by oldfred on 2021-09-02
Have you updated UEFI firmware.
And then updated SSD firmware?

My Samsung NVMe drive has an ISO with the firmware update. I just booted it and it looked like an old DOS screen with just my model & update file.

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

You can see exact model & firmware (FW Rev) version, if you install nvme-cli:
sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

---

### Post by tea for one on 2021-09-02
Have you changed the setting as this attachment?

---

### Post by matt-hammond on 2021-09-03
I want to be able to do it using the power button. Call me OCD but there it is.

---

### Post by matt-hammond on 2021-09-03
Hey Guys. Thanks. For the advice. I think you might be on to something old Fred. I will try it. And 'tea for one' I've got avlinux installed at the moment but I will look into the settings when I get Ubuntu back on again (it's the same problem). Can I only reply to everyone or is there a reply to individual option too here?

---

### Post by oldfred on 2021-09-03
Its a forum where we all try to help.

And best to see what others have suggested, so as not to duplicate effort or confuse a new user. Sometimes you have to try multiple things, but best to try one at a time.

---

### Post by matt-hammond on 2021-09-03
Hello Again. I managed to enter the sudo command into the terminal and got the model listed. But i wasn't able to correlate this with those links you sent. I am not that advanced so you need to explain it to me as you would to a 5 yr old child. At the moment, I am running mx linux but I have another laptop. The computer repair guy said that I have to download a driver for the PCIe nvme drive. I know how to create a bootable USB flash drive. I have installed several distros since I bought this brand new laptop a week or so ago. Maybe I have screwed up something in the bios. All I am trying to do is install the Ubuntu based Elementary OS and have the power off button work as it should (goes into and out of sleep mode on a short press). Maybe I need to repair the EUFI. I am tempted to take it back to the computer repair guy myself but it would give me enormous satisfaction if I could do this on my own so next time I need to install an OS on this machine I know how to proceed. So to recap I want to make sure the EUFI works as it should, get the driver for PCIe nmve disk, and then install a fresh copy of Elementary OS and then have the power button work as it should.

---

### Post by oldfred on 2021-09-03
Post what you got, if more than a couple of lines, include in Code Tags.
Code tags are easy to add in Forum's Go Advanced editor and the # icon. Highlight & click on icon.

If you have not downloaded your vendor or motherboard's manual do that first. 
The manual should have details on how to update UEFI. Most default to Windows update, but should also have other methods.

---

### Post by matt-hammond on 2021-09-03
I succesfully used the 'sudo apt install nvme-cli' command and then when I entered 'sudo nvme list' I got the model 'WDC PC SN730 SDBPNTY-5126-1006'.

Since buying this brand new laptop about a week ago, I have installed several distros out of curiosity. One of which made me do some partitioning during the install. I don't know if I have screwed up the EUFI.

Why should I have to update the firmware on a brand new laptop.

The problem I am experiencing is that the 'power off' button puts the computer to sleep but does not wake it back up. I passed a computer repair shop without my laptop and asked the guy about it. He told me that I need a driver because there is a problem with Samsung PCIe-nvme disks. I have no idea how to get this driver. In the past on my old BIOS laptop, I just used to etch an iso file to usb and install with no issues but now things are more complicated.

I am not particularly tech savvy but willing to listen and learn and follow the necessary steps to get the laptop working as it should.

---

### Post by oldfred on 2021-09-03
Quick Google search on your model & firmware update gave me this.
I would download manual & firmware.
[https://kb.sandisk.com/app/answers/detail/a_id/22618/~/western-digital-pc-sn730-nvme-ssd-support-information-page](https://kb.sandisk.com/app/answers/detail/a_id/22618/~/western-digital-pc-sn730-nvme-ssd-support-information-page)

Often new systems were not just built, or vendors even have fixes available.
Best to check your UEFI version in UEFI menu & compare to latest available.

---

### Post by matt-hammond on 2021-09-03
OK, thanks a lot! How do I check my UEFI menu?

---

### Post by oldfred on 2021-09-03
You open your UEFI, many systems use f2 or del key. Again you need to review manual to understand your system.
Some show correct key as you boot on UEFI/BIOS screen. But if fast boot is on, that screen may not appear for enough time to even read it.

---

### Post by matt-hammond on 2021-09-03
Hello, It's the esc key on this HP laptop. So I got into the UEFI diagnostics and it all seems to work ok. It's version 2.2.0.0

---

### Post by matt-hammond on 2021-09-04
But I am still at a loss as to how to update the UEFI and SSD firmware. I spent hours on it yesterday but couldn't figure it out. I need spoonfeeding on this one as I am not that tech savvy and have never dabble in the BIOS/EUFI before other than to set up a boot.

---

### Post by oldfred on 2021-09-04
Did you download the manual?
That usually had good explanation and often photo/drawings showing lots of details.
I do not have an HP, so do not know details on HP systems.

Often bigger differences if AMD or Intel based. Some HP threads.
HP ENVY Notebook - 15-ah151sa AMD ended up BIOS not dual boot
[https://ubuntuforums.org/showthread.php?t=2465857](https://ubuntuforums.org/showthread.php?t=2465857)
HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)
HP Envy - use UEFI to change boot order
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)

HP 4540s laptop 20.04.1 UEFI install
[https://ubuntuforums.org/showthread.php?t=2452483https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios?noredirect=1#comment2125560_1257230](https://ubuntuforums.org/showthread.php?t=2452483https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios?noredirect=1#comment2125560_1257230)
HP UEFI menus New UEFI 
[https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237](https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237)
HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)

---

### Post by matt-hammond on 2021-09-04
I downloaded the hard drive manual yes but there was nothing in it about updating firmware.

---

### Post by matt-hammond on 2021-09-04
Actually there was some firmware to download. A .fluf file. Have no idea what to do with that.

---

### Post by rbmorse on 2021-09-04
> **matt-hammond said:**
> I succesfully used the 'sudo apt install nvme-cli' command and then when I entered 'sudo nvme list' I got the model 'WDC PC SN730 SDBPNTY-5126-1006'.

(omitted)

...I passed a computer repair shop without my laptop and asked the guy about it. He told me that I need a driver because there is a problem with Samsung PCIe-nvme disks. I have no idea how to get this driver. In the past on my old BIOS laptop, I just used to etch an iso file to usb and install with no issues but now things are more complicated.


According to the nvme-cli output you posted, you don't have a Samsung nvme storage device.  It shows you have a Western Digital (WDC) device.

---

### Post by matt-hammond on 2021-09-04
Aha! Yes! Well spotted!

---

### Post by oldfred on 2021-09-04
Did you ever tell us what model HP?

---

### Post by matt-hammond on 2021-09-04
It's a HP 15s-eq1125nw machine...Just can't wake it up from suspend without having to hold down the power button to shut down completely. Got the system up and working but there is this annoying fault

---

### Post by oldfred on 2021-09-04
I could not get into HP's support site.
USA HP does not have that system.
General Google search found system, but HP wanted serial number to get into support area.

Similar system showed that you had to log into support area to get UEFI/BIOS updates.

---

### Post by rbmorse on 2021-09-04
What happens when the machine is asleep and you press one of the regular typing keys (other than the start button)?

---

### Post by matt-hammond on 2021-09-05
Nothing happens. The HP website doesn't recognise my serial number. The issue remains unresolved.

---

### Post by matt-hammond on 2021-09-06
Hello,

Ok, in the end I installed a trial version of Windows and updated the BIOS that way. The power button works fine with Windows so it is not a hardware issue. But then I installed Ubuntu Studio and the issue has come back. Computer won't come out of sleep mode. So that's the state of play right now.

---

### Post by tea for one on 2021-09-08
Ubuntu Studio 20.04.3 LTS uses Xfce now, therefore:-

Settings > Power Manager > When Power Button Is Pressed > Suspend

Is there something about this option that still troubles you?

---

### Post by rbmorse on 2021-09-08
This article popped up on Phoronix today. May be related to your issue. 

[https://www.phoronix.com/scan.php?page=news_item&px=AMD-S2idle-Fix-Linux-5.15](https://www.phoronix.com/scan.php?page=news_item&px=AMD-S2idle-Fix-Linux-5.15)

Your computer has an AMD CPU and chipset

[https://support.hp.com/us-en/document/c07067317](https://support.hp.com/us-en/document/c07067317)

---

### Post by matt-hammond on 2021-09-12
Hello. Sadly this issue remains unresolved. Apparently it's an ACPI issue. I tried to modify the GRUB file but it didn't work. It seems some hardware just doesn't work well with Linux so do some research before you buy a laptop and don't just assume that it will all work perfectly. For me this is a small issue. I can't put the computer to sleep so I just have to shut it down. But it boots very quickly so it's not the end of the world. Maybe they will update the linux kernel to resolve this in the not too distant future.

---

### Post by edneville on 2022-07-21
Hi matt-hammond

I think we have similar computers. Have you tried this as it solved the issue for the HP here:

Add iommu=soft to your kernel arguments, (I use pleaseedit /etc/default/grub, but you can use what you like):

  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft"

Then run

    update-grub

and reboot

---

