---
title: "Windows 7 boot disabled after I boot-repair Ubuntu's boot"
date: 2015-05-27
forum: Installation &amp; Upgrades
---

### Post by Werner_Wahanik on 2015-05-27
Hello ! 

When I installed Ubuntu it wouldn't boot and I decided to run the program boot-repair from a live-usb that I prepared with the program Unetbootin. When I runned Boot-repair I checked for the boot-repair only the partition where I had installed Ubuntu (because the Windows 7 booted correctly) and carried out the process succesfully. However now i'm not able to boot Windows. When I turn on my ASUS A45K I only have the option of booting Ubuntu. The record of my boot-repair is in [http://paste.ubuntu.com/11394210/](http://paste.ubuntu.com/11394210/). I runned Boot-repair again and the repair runs "succesfully" very fast and doesn't solve the issue. 

could you please help  me out with this ? I apreciate it ;);)

---

### Post by oldfred on 2015-05-27
Not sure why grub2's os-prober is not seeing Windows.
Is Windows hibernated, but normally there would be messgae on access?

Try this but it should be the same as Boot-Repair.
sudo update-grub

If not we can manually add a Windows boot stanza to match what os-prober would find.
But NTFS partition has to be bootable from grub or not hibernated nor needing chkdsk.

Do you have a Windows repairCD or flash drive? Best to have that.
With Boot-Repair you can temporarily restore Windows boot loader by using advanced mode and choose Windows and drive sda or MBR of sda.
Then once Windows works ok, then restore grub and run the update.

---

