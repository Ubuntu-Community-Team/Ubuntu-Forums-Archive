---
title: "&quot;No bootable media&quot; after installation of Ubuntu 15.04"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by arendvanderkolk on 2015-10-21
Hello world,

On my new Acer Aspire R11 I have only installed Ubuntu. I removed Windows 8

I have a blank disk(ATA Kingston 120gb SSD) and i first partitioned according to the instruction in this thread: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
See attachment-1. (Secure boot is already disabled in Bios)

When pressing "Install Now" i saw this message "The partition table format in use on your disks normally requires you to create s separate partition for boot loader code". So then i went back and added the "/dev/sda4 (efi) and selected that as "device for bootloader installation".

But it keeps saying "No Bootable device".

Also with /dev/sda it shows the error "No Bootable device".

The SDD drive is the first option in the boot order

Any idea?

---

### Post by grahammechanical on 2015-10-21
May I suggest what seems to be a more complicated way to do this but might in fact be easy?

As Ubuntu is to be the only OS on sda why not use the Erase Disk and Install Ubuntu option. You will not have a separate /home partition but you will have a working Ubuntu with the required efi boot partition. Then, create a partition for /home and re-install using the Something Else option giving all the partitions the correct mount points.

The two images do not show sda4 being present and I do not think that the efi boot partition (sda4) should be selected as the location to install the boot loader. I would guess that partition sda4 should be mounted as efi boot and the boot loader installed in sda (it is the default location). Then the installer when it installs the boot loader (Grub) will put the necessary boot files into sda4.

I say that this is my guess as I do not have a UEFI boot system just a BIOS boot system and with that I do not need a efi boot partition. So, I have no experience in this matter.

Regards.

---

### Post by arendvanderkolk on 2015-10-23
Hi G,

thx for your input. As you mentioned i have re-installed Ubuntu with the option 'Erase disk and Install Ubuntu', then i got the warning 'Force UEFI installation', and continued installing in UEFI mode.
It then gave me the partitioning as in attachment 'partitioning'.

Then it finishes with 'restart system'. When it restarts it reads "Please remove installation media and close the tray (if any) then press ENTER:. But on 'Enter' nothing happens so press power button 3 seconds.

When i turn it on i get again 'No Bootable Device'. It makes me think there is something in the newest laptops that prevents Ubuntu from installing properly.

Any idea?

---

### Post by Bucky Ball on 2015-10-23
Just throwing this in: why don't you start by installing 15.10 as you are going to need to upgrade to it anyway in January 2016, or 14.04 LTS which has five years support until 2019 and can be upgraded to the next LTS release, 16.04 LTS in April 2016?

While 15.04 is still supported for another three or so months, it hardly seems worth installing at this stage. My two cents. :D

---

### Post by oldfred on 2015-10-23
All Acer require you to set a supervisory password and enable "trust" on the grub/ubuntu efi boot files.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by yawanathan_israel2 on 2015-10-23
Hello,

Thanks oldfred for letting us know this about acer laptops. I have never seen a laptop require you to set a password and then have to trust another OS. I won't be buying acer laptops ever.
It may not seem like a big deal, but being in tech support 18yrs, I have a disgust for any vendor that makes it hard to install any OS.

Thanks
Yawanathan

---

### Post by oldfred on 2015-10-23
Actually Acer is better than just about everyone except Dell (so far). My Dell SFF system just worked. And others have also with Dell.

Everyone else violates a specific UEFI spec and uses description as part of its boot. And only valid description is "Windows". We than have to do one of many work arounds.

---

### Post by arendvanderkolk on 2015-10-25
Hi,

Thx all for your input. The following thread by gennarof did work for my Acer Aspire laptop

[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by Bucky Ball on 2015-10-25
Good news. If the problem is solved please see the first link in my signature and mark as solved. Thanks. :)

---

