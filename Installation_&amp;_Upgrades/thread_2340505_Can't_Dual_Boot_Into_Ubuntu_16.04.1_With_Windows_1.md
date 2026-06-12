---
title: "Can't Dual Boot Into Ubuntu 16.04.1 With Windows 10 Pre-install"
date: 2016-10-19
forum: Installation &amp; Upgrades
---

### Post by hapkiyusul on 2016-10-19
Hi all. I've spent a few days now trying many options to get Ubuntu to dual boot on my new Windows 10 machine.


Here is my Boot Repair URL : [http://paste2.org/yxppympx](http://paste2.org/yxppympx)


I've also emailed [email]boot.repair@gmail.com[/email] as suggested but no response yet.


Any help would be greatly appreciated!


Thanks very much.
Andrew

---

### Post by Bucky Ball on 2016-10-19
Welcome. You have no Ubuntu installed. You need to create free space to install Ubuntu. Have you?

You have got an entry for Ubuntu in the EFI file somehow, though. Any idea how? Did you run a recommended repair with Boot Repair with no Ubuntu installed?

You have a much better chance of support by giving a detailed description of how you're trying to install, what happens when it doesn't install, and what you've tried to fix it.

Can you boot from your install media and 'Try Ubuntu'? Does that work fine?

---

### Post by yancek on 2016-10-19
> Hi all. I've spent a few days now trying many options to get Ubuntu to dual boot on my new Windows 10 machine.

Your windows partition takes up the entire drive and you have nowhere to install Ubuntu.  You need to first shrink that partition from windows Disk Management tool.  I would suggest defragmenting and running chkdsk on windows after shrinking the partition. 

You installed the Ubuntu EFI files which can be seen on sda1 at the top of your output.  Unfortunately, you don't have any windows EFI files there.  With an EFI boot, you will need both Ubuntu and windows files in separate folders on that partition (sda1).  Ubuntu won't overwrite windows EFI files, it creates a separate folder and installs it's EFI files there.  You don't have any boot code in the MBR which would be correct for an EFI install and your system shows GPT partitions which means windows would have been an EFI install.  Also, you do not have any Ubuntu/Linux partition, just the files on the EFI partition so obviously the installation did not complete..

You can't boot Ubuntu because it isn't installed, you just have it on the flash drive.  Can you boot windows?  Do you have a windows installation DVD?  I would suggest you read the information at the link below on dual booting windows 10/Ubuntu and compare what they say to what you did.  It would have been a lot more useful to have read before you tried the install but...?

   [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2016-10-19
While you show a large NTFS partition it is not a standard Windows UEFI configuration.
       [https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by hapkiyusul on 2016-10-20
Thanks for your feedback everyone. I'll flip the approach and just install Ubuntu clean as this is my preferred OS (aka erase Windows 10 altogether) and then later attempt to install Windows 10 as the dual-boot option.

---

### Post by Bucky Ball on 2016-10-20
MUCH easier route to install Windows 10 first. You are going about face. It can be done the other way but save yourself some time and a possible migraine and go Win first, Ubuntu second.

In my experience (and that of many others), best to make sure Win is installed, working and happy before going anywhere near the Ubuntu install media. Ubuntu is robust in comparison and is a straightforward install second if you do the preparation and get it right because its designed to have to play with Windows idiosyncracies (it plays second fiddle to Win while Win prefers to find ways of preventing other OSs installing). oldfred can no doubt add more specifics about and pros and cons of installing Win second. :)

Good luck and please mark this as solved from Thread Tools at top right (or see link in my signature). This will not close the thread to further discussion, but if you are after support with another issue, improve your chances by posting a new thread.

---

