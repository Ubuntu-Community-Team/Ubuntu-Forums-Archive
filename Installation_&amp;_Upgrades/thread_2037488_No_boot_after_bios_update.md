---
title: "No boot after bios update"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by lmu on 2012-08-04
Hello
 
I installed successfully Ubuntu server 64 bits and everything worked fine before the bios update.
 
Now I have a message "Insert boot device and press a key"
 
I have two disk (one ssd with the operating system, database and another HDD with the data)
 
Before the update, in the bios boot order section, I had three options :
[Ubuntu]
[Corsair GT SSD] 
[HDD]
 
After the update the [Ubuntu] option is disapears. Think this have a link with my problem.
 
Thanks in advance to help me to boot my system.
Regards,
Laurent

---

### Post by oldfred on 2012-08-04
Welcome to the forums.

A reinstall of BIOS sets the BIOS back to defaults, so you lose any changes you made before.

Showing Ubuntu in BIOS is not common, but it is with UEFI. So do you have UEFI?

Even though you have server, you an use liveCD and run this. Server install is not a liveCD, so you have to download a desktop version.. Also if you have RAID or LVM, you need to install those each time you boot a liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

