---
title: "Lubuntu 18.10 install problem at grub2: efibootmgr failed to register the boot entry"
date: 2018-12-25
forum: Installation &amp; Upgrades
---

### Post by madani1982 on 2018-12-25
I had a working install of Kubuntu 18.04 and tried to install Lubuntu  18.10 on another partition (something I've done successfully before,  when transitioning from Ubuntu to Kubuntu about a year ago). In the  Lubuntu LiveUSB installer, I chose the option to replace an existing  partition. the install failed with the following error message:


  INSTALLATION FAILED
  Boost.python error in job "bootloader"
  Command 'grub-install --target=x86_64-efi --efi-directory=/boot/efi  --bootloader-id=ubuntu --forcd' returned non-zero exit status 1
  Installing for x86_64-efi platform. Could not delete variable:  interrupted system call. Grub-install:error:efibootmgr failed to  register the boot entry: block device required.


  I launched boot-repair. After making me manually reinstall grub2, it  failed with its own error message.  I tried with several install configuration. I also tried with Ubuntu  18.04. In the end I tried a brand new install by creating a whole new  GPT table. I still got the same error message (I tried with or without  creating a FAT32 boot partition mounted at /boot/efi).


  What could possibly be the problem ?

  
Another thing to note: my EFI "bios" is set to Secure Boot = disabled  and Legacy mode = disabled. Actually I can't set Legacy mode to  "enabled" and make it stick: if I do it and reboot, the Legacy mode  setting will revert back to "disabled".


  **EDIT:** 

  
[LIST]
[*]I tried a bios update following the procedure described on the HP  website. It failed after a couple of write/verify cycles. The logfile  ends with the very ominous "Failed RetryBlocks Call Status (Device  Error)". 
[*]I can manually boot into the newly installed Lubuntu 18.10 by  pressing F9 at startup and then choosing  to boot from EFI file:  /EFI/ubuntu/shimx64.efi (this is not the only file that I can boot from  though) 
[*]the EFI boot order is set to the following (which I can change,  but the changes won't be saved at next reboot): USB / OS boot manager /  Internal CD/DVD / USB CD/DVD / Network adapter 
[*]even when I choose the option to "load factory settings" in the EFI bios, no change will actually be saved at the next reboot 
[*]the F9 "manual boot" menu has the other following options, which  all lead to the computer saying "The selected boot device failed" and  freezing: "ubuntu"/"internal HD"/"CD/DVD". As I said before, only "boot  from EFI file" allows me to boot. 
[*]here's the very latest boot-repair report: [https://paste.ubuntu.com/p/qPkDdvNdbQ/](https://paste.ubuntu.com/p/qPkDdvNdbQ/) (again it ended with a failure) (do not mind the entries concerning the /dev/sdb disk, it's an external hard drive) 
[*]My computer is a HP Pavilion 14-n249nf, bought in 2014.

The symptoms look very similar to this bug report:  [bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147"). 
[/LIST]

---

### Post by oldfred on 2018-12-25
What brand/model system?
What video card/chip?

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2018-12-28
Did not realize this was the same.
[https://askubuntu.com/questions/1104515/problem-with-grub-install-when-installing-ubuntu-18-04?noredirect=1#comment1822760_1104515](https://askubuntu.com/questions/1104515/problem-with-grub-install-when-installing-ubuntu-18-04?noredirect=1#comment1822760_1104515)

Best just so others can also help to summarize issue again and post the latest link to Summary Report from Boot-Repair.

Back up current partitions with sfdisk, and save to another device.
sudo sfdisk -d /dev/sda > backup_sda.txt

We will try to change the GUID that your UEFI has to find the ESP. Not sure if it has to be partition 3 or not. 
Post showed GUID that UEFI expects to be:
30576485-1be6-4ad6-9772-7a982dae6950
(from sudo efibootmgr -v)

To change GUID of current ESP (which now is partition 1, and may be another issue).
We will use gdisk from live installer and get to its expert commands:
[https://www.rodsbooks.com/gdisk/walkthrough.html](https://www.rodsbooks.com/gdisk/walkthrough.html)
sudo gdisk /dev/sda
Lets do a v command just to verify current table.
Then x to for extra functions and ? to display commands

c	change partition GUID

Not sure of details, but expect it to ask partition number (or 1) and then GUID and you want to copy & paste the number from your UEFI as posted above.

You then have to save & exit with w.

---

### Post by madani1982 on 2018-12-29
Thanks !
One question though before I go about and try that: how will I use the backed up partition table if this messes up my current install ?

---

### Post by oldfred on 2018-12-29
You should always have full back up of everything that is important. What if hard drive totally fails tomorrow?

You can use sfdisk to restore the old partition table.
See also and -d or --dump parameter
man sfdisk

If using newer gpt partitioning with UEFI boot, be sure to only use newer versions of sfdisk that support gpt.

---

### Post by madani1982 on 2018-12-29
Yes of course, I always backup my important files, but I've never backed up a partition table before !
I'll try your solution. If it fails I'll try repartionning with the boot/esp partition as sda3.

---

### Post by oldfred on 2018-12-29
Some info on renumbering partitions, But does it in order on drive.
[https://askubuntu.com/questions/919072/how-to-fix-the-partitions-number-on-gpt-disk-dev-sdax](https://askubuntu.com/questions/919072/how-to-fix-the-partitions-number-on-gpt-disk-dev-sdax)
Always requires re-install of grub.

---

### Post by madani1982 on 2019-01-05
Hey oldfred,
Thanks for your help.
In the end I applied the repair method outlined int the bug report and it worked like a charm. My bios can now be modified again. Since Grub wasn't working properly I had to go and install Refind to boot the patched kernel but in the end it worked ! (your link to rodsbooks.com helped a lot)

---

### Post by oldfred on 2019-01-05
You can change to [Solved].

I keep an old small,now tiny flash drive with rEFInd for emergency boot.

---

