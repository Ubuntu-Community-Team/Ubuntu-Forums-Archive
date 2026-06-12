---
title: "EFI issues with fresh install : 22.04 Server."
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by mrjeffmacdonald on 2022-10-13
Hi,

I'm doing a fresh install on a machine that previous had Rocky on it. It's a i5 machine with a 240 gig SSD. Installing from USB.

It gets thru asking all of the questions then towards the end of the process says there was an error with the installation. The fun thing is, if I then reboot the machine reboots and I can ping it (I have my router giving it a static ip via DHCP) however SSH is not running and my user did not get created.

The error is roughly "Invalid BootOrder order entry value 100E" and "efibootmgr: entry 100E does not exist". I've posted a photo of the entire error dump.

Thanks folks.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291123&stc=1[/IMG]

---

### Post by oldfred on 2022-10-13
Post these:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
Check partUUIDs match to ESP - efi system partition(s) you have.
sudo efibootmgr -v 

See also 
man efibootmgr

You can change boot order and delete obsolete or defective entries.
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2

Delete entries:
sudo efibootmgr -b XXXX -B

---

### Post by mrjeffmacdonald on 2022-10-13
Thanks I'll give that a try. However I cannot get into the system to run these :)

---

### Post by yancek on 2022-10-13
>  However I cannot get into the system to run these  

You don't need to get into the installed system you can use the USB device you are using to install Ubuntu with the Try Ubuntu option.  You can change the EFI entries and order in the BIOS firmware.

---

### Post by mrjeffmacdonald on 2022-10-13
@yancek you&#8217;re saying I can use the usb boot media to get a shell to run the commands that oldfred suggested?  How?

---

### Post by oldfred on 2022-10-13
I only installed server version years ago to test its differences.
I thought server installer (or one of them) was also a live installer like the desktop installer.
So you can boot in live mode & run commands.

Or download a desktop version.
I typically do not suggest to download the Boot-Repair ISO as it sometimes is not as up to date as using the ppa to install into a live installer or working system.  You can down load Boot-Repair ISO and make a live installer. Best not to make any auto suggested fixes until reviewed. You can post the link to the summary report, so we can see lots of details of your configuration.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mrjeffmacdonald on 2022-10-13
I have not tried the above options yet. However a friend lent me a spare SSD and well&#8230; I&#8217;m having the exact same errors (different device ID, same errors).

I tried to do an install using the legacy &#8220;not UEFI&#8221; loader and while it completed, every time I try to boot&#8230; something fails. 

Starting to think it&#8217;s the machine.

---

### Post by oldfred on 2022-10-13
What computer/motherboard?

My MSI z690 system with 22.04 Kubuntu desktop has i5-12400 with NVMe drive.

---

### Post by mrjeffmacdonald on 2022-10-14
It's a Dell Precision XPS 8910. In anycase, I switched it to Legacy Bios, and now I have a working system. As fun as it is, I'm not interested in debugging EFI any more :) It's a hobby / home machine not a work rig. Thanks for your time tho oldfred!

---

