---
title: "Turn IMGs of OSs into Multiboot USB with Grub2, inside KVM w luks? (lol sorry)"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by mikey93898 on 2016-06-01
Hi all,

I may be grossly over complicating things. Very simply put: I would like to make a multiboot USB stick, but with full installations, not the readonly "live" iso's.

**What I've done in the past, and have going right now**:
One operating system (Ubuntu, full install) installed directly to my thumb stick, fully encrypted OS using luks. I didn't do this by hand but basically just used the Ubuntu installer and customized the install layout. This is fine and useful for me to bring my customized OS everywhere, but I'd like to take it a step further.

**What I'd love to be able to do**:

[LIST]
[*]Take multiple IMG files for multiple installs (created from dd'ing an existing os install partition, or grab an IMG from a KVM vm), copy them each into their own partitions on my usb stick (sda2, sda3, etc), install grub2 to the first partition (sda1), then somehow be able to boot to that USB stick, see grub's little menu, and select the OS/partition of my choice.
[*]I'd like for each OS partition to be fully encrypted inside a luks container.
[*]If possible, I'd like to be able to do this inside KVM from start to finish, until the very last write of a final IMG file to my thumb drive. This way I can reduce the risk of borking my desktop system due to my extreme noobery
[/LIST]


**What I've tried**:

[LIST]
[*]First, I created a KVM vm, gave it a 20G hard disk image, and installed Centos 6 (it worked, and would boot)
[*]Second, I created a second KVM vm, and installed Ubuntu to another 20G disk image (also worked and booted)
[*]Next, I created a third KVM vm (yes, I am ridiculous) running yet another copy of Ubuntu (so I could work), and also gave it a 60G disk image (my thumb drive is 64G), and access to the first and second 20G images that I had just installed Centos/Ubuntu to
[*]Then I created (on the 60G image, which I *think* ended up being sdb at the time) three partitions: First an empty 1G partition with boot flag (to hold grub) on sdb1, then two more (sdb2, sdb3) to hold the Centos/Ubuntu installs I'd just done.
[*]Next, I used dd to copy both 20G images of my installs into the 60G partitions sdb2 and sdb3. Or rather, indirectly using crypt-setup's mapper as I had just mounted them as encrypted containers... but still
[*]Finally, inside that third VM, I attempted to run "grub-install" on the 60G image's drive (to sdb)
[/LIST]


It's at that point where I realize... I may have no idea what I'm doing. Sorry for being a n00b. On one attempt, Grub booted to recovery mode after complaining about a missing device. On another, Grub booted to a normal prompt, but with no menu. I feel like I should be somehow generating a grub configuration file, as it seems to be missing from the boot partition I created.

Any advice on how to proceed? I would love love love an automated tool to do this, if one exists. If not, I would love to be able to do this myself. The main things still puzzling me are:

[LIST]
[*]Is KVM the death of me? It would be so great to be able to do these things without worrying about screwing up my normal OS/bootloader... but maybe this is not possible
[*]Am I actually allowed to simply take an IMG of any existing OS partition, and copy it wherever I feel like, and somehow expect grub to be able to see it and go "Oh look, an OS! I can boot into that for you bro!" ... I mean - is that even the function of grub?
[*]Does putting an OS partition inside a luks container screw everything up? I was under the impression grub would just see it, and realize it needed to ask for a passphrase before continuing (I'm ashamed to admit - I just now realized I haven't actually tried doing this entire process without luks ... maybe I should while I'm waiting for replies)
[/LIST]


Thank you for reading, and I appreciate your suggestions!

~Mike

---

### Post by sudodus on 2016-06-02
Maybe it is enough to have one encrypted system, and in that case maybe the following method would work: Start by installing the encrypted system and leave space for the other systems. Install in BIOS mode, otherwise you have an additional problem with the EFI partition.

Then you install the other systems as dual boot, triple boot etc. Select ***Something else*** at the partitioning window of the installer, and write the bootloader into the partition of each new system. That way you will preserve the original grub which points to the encrypted system.

Finally boot into the encrypted system and run ```
sudo update-grub
``` in order to get grub menuentries for all installed systems.

-o-

Another alternative would be to use virtualization with a host system and encrypted guests (in the portable system). But that would require quite powerful computers and fast communication (USB 3 or eSATA) to the drive with the portable system.

---

### Post by mikey93898 on 2016-06-02
Hey man. Thanks for the reply. Yeah perhaps maybe, one encrypted system is enough. In theory I could just leave them all unencrypted and do the usual .Private folder thing for each important account. I just would feel better if I could get system level encryption down, and I feel like I should be able to figure this out somehow.

Re: Your second suggestion. Are you saying that the thumb stick would only contain 1 unencrypted OS, but multiple encrypted VMs, and that I would simply never work "on the host", and always boot directly into one VM? I suppose that's a valid idea. I would never be doing serious heavy lifting while using the USB thumb stick ... I'd mostly just be using it to be able to take over a computer every now and then, when I needed to, and when one was available (while visiting a friend's house with no laptop, or diagnosing my cousin's broken computer, etc). One wonderful side effect of doing it this way would be the KVM image files would be fully accessible both on windows/linux without admin access... and since qemu is so awesome, I could probably bring a portable folder install of qemu for both windows and linux, such that everywhere I go, I could run my virtual machine without admin approval (because again, qemu is awesome and you can literally just spawn a command line and blam... virtual machine with no install on local). That'd be pretty useful at school, too. Dang dude. Great idea.

I wonder if there are benchmarks for this exact scenario's performance penalty ... running a qemu encrypted guest.

Maybe I'll cry myself to sleep a little less if I end up failing to do the multiboot how I wanted it.

---

### Post by sudodus on 2016-06-02
The virtual machine will be slower, but how much slower depends very much on the hardware. In some too old or too weak computers it will not work at all with virtualization. But it should fairly well work in newer computers.

---

### Post by mikey93898 on 2016-06-03
Funny thing ... I just happen to have the world's oldest crappiest laptop in the other room still. It's a 32-bit toshiba satellite from like .... eight years ago. I was using it for school to minimize the financial hit if I ended up losing/breaking it (I have 2 newer ones... not great either, but more valuable to me).

Only problem is it's in 32 bit, and I've been setting up the stick for 64 bit OS's. Maybe I should do another run with all 32 bit though. That's probably more wise if I intend to run linux on random diseased computers, anyway.

So by the way ... I got past one of my major problems on this already: I did not understand fully how to chroot in order to run the commands "grub-install" or "grub-mkconfig". I apparently wasn't even running grub-mkconfig before at all, and just assumed it was somehow auto-handled, which may have explained why I got a blank grub prompt before. And then not using the chroot-trick may have been giving my grub installation an incorrect sense of the target disk layout. On top of that, I did not understand that each linux partition needed to maintain its own /boot directory; I was under the impression that was only for grub, and was installing /boot into its own partition specifically in order to discard it as I copied the OS over to my thumb stick drive.

So now what I'm doing is: Use a livecd to pre-partition the drive and chroot such that /dev/sda is the target for grub,  /dev/sda1 is a dedicated grub partition, and each linux installation takes exactly 1 partition and doesn't separate its /boot folder. All I have to do each time is run a script I wrote to re-chroot and re-run grub-mkconfig on the grub partition, and so far so good... I feel this is really starting to work now. All I need to do is figure out how to make each install's grub entry survive kernel upgrades with some linking trick I saw in passing.

How do you share code here? I'd like to share my shell script for feedback and in case anybody would like to use it in the future.

---

### Post by sudodus on 2016-06-03
If you have only some small scripts, you can write a new thread in the [Tutorials subforum](http://ubuntuforums.org/forumdisplay.php?f=100).

1. If they are very small, put them within [noparse]```
tags
```[/noparse] in clear text

2. If the scripts are a little longer (and not really easy to understand, copy and paste), compress the script files for example with ***gzip***

Click on the big red button 

[TABLE="class: cms_table"][tr]
[td="bgcolor: #dd5500"]
[color="#ffffff"]**Go Advanced**[/color]
[/td][/tr][/table]

under the editing window and then on the button **Manage Attachments** and attach the compressed script files. In this case you should also provide the md5sum(s).

3. And above all, please spend some time and effort to describe what you have made, and how to use your scripts.

Good luck :-)

---

### Post by oldfred on 2016-06-03
If directly booting kernels you can boot the link that Debian based systems put in /. Then you boot the link and that will be the newest kernel in that install.

Only one grub is in control of boot process and that should be the one you use the most. 

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[URL="http://ubuntuforums.org/showthread.php?t=2076205"]http://ubuntuforums.org/showthread.php?t=2076205


[/URL]

---

### Post by mikey93898 on 2016-06-03
> **oldfred said:**
> If directly booting kernels you can boot the link that Debian based systems put in /. Then you boot the link and that will be the newest kernel in that install.

Only one grub is in control of boot process and that should be the one you use the most. 

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[URL="http://ubuntuforums.org/showthread.php?t=2076205"]http://ubuntuforums.org/showthread.php?t=2076205


[/URL]

That's interesting; thank you. I'm going to check out those links. Is there a similar method for fedora/redhat systems?

Yeah I'm finally seeing the light regarding one grub partition, now that I finally understand how to install one.

---

### Post by mikey93898 on 2016-06-03
Wait... I think I misunderstood the previous idea. I was thinking I'd do 1 unencrypted OS, and put encrypted OS's inside of it... !!! but !!!, perhaps 1 host OS with full disk encryption would be awesome instead, because then all guests wouldn't need to be encrypted (as they'd all be encrypted already).

---

### Post by sudodus on 2016-06-04
Yes, this is possible, and maybe better than the opposite method. Anyway, avoid double encryption.

---

