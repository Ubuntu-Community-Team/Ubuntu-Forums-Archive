---
title: "Installation difficulties"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2016-09-15
Hi everyone,

I've been trying to install Ubuntu onto a new Acer desktop computer and am having difficulty getting it to work. Despite changing the boot order in BIOS, the computer was refusing to boot from CD or USB and took me about an hour of mucking around before it finally allowed me to manually force it to boot from USB.

I did a custom install and found the 1TB hdd is divided into two 500GB partitions and when I shrunk them I ended up with two partitions of free space that I couldn't combine. I installed Ubuntu on one of those partitions, the install completed and required a restart, but after restarting it keeps going straight into windows.

Could it be that later model computers are being designed so that you can't change the OS on a whim or is there something I'm doing wrong? I'm under strict instructions to leave windows with 200GB the other 800GB can be used for Ubuntu. So please don't advise me to erase the entire thing and start from scratch.

The two 500GB partitions have thrown me a bit as has the fact that the free space collected from resizing them can't be merged so I have 1x 800GB partition instead of 2x 400GB ones.

As always and help is greatly appreciated and I thank you in advance for any advice that you may offer.

Thanks

---

### Post by ajgreeny on 2016-09-15
I suspect a UEFI/BIOS problem here.  See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) for lots more info.

If the machine is new and came with Windows pre-installed it will most probably be using UEFI, not BIOS, though you may have installed Ubuntu in BIOS mode if you were unaware of this potential difficulty.

So we know the current situation go to Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by MibunoOokami on 2016-09-15
> **ajgreeny said:**
> I suspect a UEFI/BIOS problem here.  See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) for lots more info.

If the machine is new and came with Windows pre-installed it will most probably be using UEFI, not BIOS, though you may have installed Ubuntu in BIOS mode if you were unaware of this potential difficulty.

So we know the current situation go to Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

Hi AJ,

I didn't know of this before even though UEFI seems to have come out in 2010 and the last computer I installed Ubuntu on was a 2012 model.

Here is the pastebin link [http://paste2.org/xzXIjDtd](http://paste2.org/xzXIjDtd) 

Now that Ubuntu is installed somewhere, will the LiveUSB let me reassign the other 400GB to the first partition? Admittedly I haven't read all the info in the first two links you provided.

---

### Post by ajgreeny on 2016-09-15
I am no expert in UEFI and definitely not in dual boot systems which I've not used for about 9 years, nor can I read and fully understand the report you linked to, but from what I read I wonder if you have made sure that secure-boot is disabled in your UEFI setup, which incidentally is what your computer is using, not legacy BIOS.

It is probably safest to wait until someone else who knows more that I do answers, but I think my suggestion at this stage is to disable secure-boot and then perhaps run the boot-repair again, this time accepting the default repair.

---

### Post by westie457 on 2016-09-15
Besides ajgreeny's suggestion to disable secure-boot in the UEFI settings pages, something else that has to be done is

1, go to the security page
2, set a supervisor password (to change currently unavailable options or similar)
3, select an UEFI file as trusted for executing.

Usually this is as simple as hitting Enter 3-times highlight Ubuntu, hit Enter.
Then hit F10 to save the settings.

If this does not work then run Boot Repair again and post another report.

---

### Post by MibunoOokami on 2016-09-15
I disabled secure-boot, set a supervisor password then rebooted before using boot-repair. That didn't work. Now I just finished boot-repair and am about to restart. Here's the pastebin [report]("http://paste2.org/XADZL73k") in case something happens. 

@westie457, I'm not sure where to find a UEFI file to make it executable.

---

### Post by MibunoOokami on 2016-09-15
It booted straight into windows, boot-repair gave a code to put into an admin command prompt which I wrote down and then used. The computer can now boot into Ubuntu straight away as it should. Now it's just a matter of working out how to join those 2 partitions.

---

### Post by MibunoOokami on 2016-09-15
I’m really confused by the original paritioning before I installed Ubuntu.
 Rather than having 1 recovery partition of  XXGB and 1 partition with all the leftover space, there was 2x tiny partitions and 1x nearly 500GB partition followed by 1x recovery partition and another nearly 500GB partition.
 
 
 I resized the two big ones hoping I can merge them later on but now I have read that the unallocated  slots need(ed) to be adjacent in order to merge them. That just seems impossible from the get go with the recovery partition being between the two large ones.  
 
 
 Am I to understand I may have to reinstall windows then delete the recovery partition and one of the 500GB ones so that the partitions will merge properly?

---

### Post by oldfred on 2016-09-15
Its not just the supervisory password but the "trust" on the .efi files. In UEFI you have to drill down and set the trust.

Some older threads also mention downgrading UEFI, but newer ones say newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by ajgreeny on 2016-09-16
With no real information on your partition layout it is impossible to help you rearrange them, or even tell you if it is worth doing; it may be a lot simpler to create new NTFS partitions which can be used by either OS.

Install gparted in your running Ubuntu OS, run it and show us a screenshot of the gparted window.  We may then be able to give you some ideas about what best to do.

---

### Post by MibunoOokami on 2016-09-16
Latest update, I used some windows program to clone the recovery partition to a different partition closer to windows, then I deleted the one that was preventing me from merging partitions and now everything seems to be fine. Thanks for the help with the boot repair.

---

