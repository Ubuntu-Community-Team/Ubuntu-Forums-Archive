---
title: "Install on fake RAID w/Win 7"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by amyoosme on 2013-05-10
After a couple of days of failure, & another couple of reading forums, I'm reaching out for help. I was able to find the following sentence, but I DO want to operate U side by side w/Win7 on my RAID.
[I]" Unless you are trying to operate side by side with windows installed to a raid the raid should be turned off in bios, raid meta data should be erased and dmraid uninstalled or the system booted with 'nodmraid'. Post if you have further question. "
[/I]I have U version 13.04, Win 7 SP1, going on an Asrock Z77 Extreme4, Intel I7 3770. I have 3 TB drives set up as RAID 5 with Win7 installed. After blowing it all away the first time, I tried several more times choosing different options each time. I ran accross one thread ([http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device)) that helped me to figure out I needed to remove or move my BRD during the U install, which I did. I currently am installing Win7 from DVD, & then U from USB with the BRD disconnected, & at least I'm getting the Live version up now.
However, NOW my problem is the install keeps choking out....I don't know if it's because of UEFI, because I'm installing on the RAID, or something else. I really want to install Ubuntu so we can adjust to it, but man, after several days of just trying to install, I'm having a hard time pressing forward. Currently, when I attempt the install from the screenshot, the installation completed (this time) but Ubuntu does not present itself for install. I've been through a couple of tutorials on editing the bootloader via bcdedit, but I haven't scored yet.
Any suggestions, other than giving up & removing my RAID array?
[ATTACH=CONFIG]242432[/ATTACH]

---

### Post by darkod on 2013-05-10
It looks good. What is the problem exactly?

Since instaling on uefi system, you have to make sure you boot the ubuntu cd in uefi mode first of all. This is very important.
You seem to have created partitions for ubuntu root and swap. Simply reuse them by selecting them and the Change button below.

The bootloader destination should be _Volume0 without any pX in it.

Grub install can still fail since that's what usually happens on fakeraid with the live cd. But usually the rest of the installation is correct and with uefi the bootloader on _Volume0 is not important anyway.

---

### Post by amyoosme on 2013-05-13
Thanks for your reply!
Yep, I'm booting in uefi, & am re-using them.
At this point, it looks like I'm doing something wrong w/Windows loader while trying to point it to Linux...What I see now, is 

File: \ubuntu.bin
Status: 0xc0000001
The selected entry could not be loaded because the application is missing or corrupt.

I apologize for my ignorance...is that not where I want to point the loader?

---

### Post by oldfred on 2013-05-13
I do not know RAID, but all UEFI systems boot from the efi partition. 
Each folder is equivalent from a UEFI boot standard point. It is somewhat like having many MBR's as each efi folder functions as the old MBR, but is larger and can have more boot code.

Generally best to boot with grub as it will multi-boot, but grub2's os-prober has a bug and does not create correct chain load entries to Windows or other efi boot loaders. Several versions of correct examples in bug report.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Boot-Repair normally adds correct efi chain load entries into 25_custom like the examples in the bug report above. Not sure with your RAID it will work or not.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I think someone posted a BCD entry using EasyBCD, but I do not know how that works.

---

### Post by amyoosme on 2013-05-15
My only regret, is that I didn't cave earlier & ask for help. Boot-repair did the trick. Had I came earlier, I would have avoided wiping my windows installation & having to do a complete rebulid of that. 
I wonder now, if I have a hdd fail, how the RAID will handle it with U on the array....it shouldn't matter. Should it?
Many many thanks guys!!!!

---

### Post by amyoosme on 2013-05-18
Ok, well I don't know if I should start a new thread since I *thought* this was solved, but it's not.
Booting today brought me another failure, & when I try to use boot repair, I get this log:

[http://paste.ubuntu.com/5676108/](http://paste.ubuntu.com/5676108/)

My Win7 install still boots, but when I try to hit my U build, it just hangs on the purple. :(
Help again?

---

### Post by oldfred on 2013-05-18
I do not know RAIDs. But is not fakeRAID dmraid. And you told Boot-Repair not to use dmraid but to use mdadm which is Linux RAID? 
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Often boot to purple screen is a video issue. Did you change any video drivers or update them? Do you get grub menu and have you tried recovery mode? Should be second line in menu or under the sub menu.

---

### Post by amyoosme on 2013-05-20
When boot repair comes up, it says to re-try boot repair after installing the mdadm packages...so I did do that, but you're right, that obviously didn't work. :)
When boot comes up & I don't do the mdadm attempt, it just says "Wanring, no acitve RAID! & then brings up a summary...oh wait, here is that summary:
[http://paste.ubuntu.com/5683615/](http://paste.ubuntu.com/5683615/)

I guess I posted the wrong summary earlier. 
Regarding the video drivers, I flashed the BIOS...

---

### Post by oldfred on 2013-05-20
Just do not know enought about RAID to help.
It does not show much of drives, but sdb does not have any partitions? The others at least show the one main partition.

---

### Post by amyoosme on 2013-05-20
I guess I could try a reinstall, I'm not that deep into the current build. Thank you for all of your help!

---

### Post by amyoosme on 2013-05-20
I tried the reinstall, it won't love me either. It only shows /dev/sda devices....sooooo, I ran gpart, & it gives the message "liparted bug found!" "invalid argument during seek for read on /dev/sda". When I ignore all of that, it shows the 931GB as unallocated. How do I get it to recognize & not overwrite the Win partition? I'm only seeing my only option as wiping the entire drive again, & starting over....again.
Thoughts??

---

