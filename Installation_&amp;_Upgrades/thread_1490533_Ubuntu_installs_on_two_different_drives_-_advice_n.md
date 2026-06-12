---
title: "Ubuntu installs on two different drives - advice needed"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by earther on 2010-05-22
Here's a screenie of partitions where Ubuntu is currently installed:

[http://www.eartherdesigns.com/ss/partitions.jpg](http://www.eartherdesigns.com/ss/partitions.jpg)

sda1 is the partition where Windows used to reside - that's why it's flagged as 'boot'.  When I nuked Windows, I just left it flagged that way as I figured that's where Grub is installed and didn't want to screw anything up.

I'm about to add a new 1TB drive for Lucid (most likely). I want to move this current drive to the second drive bay so it will become sdb 1,2,3 but keep it functional (at least until I'm convinced that Lucid will work for me).

Here are my questions:

Will Lucid find the old Ubuntu install on sdb automatically and give me a choice of dual boot?

Will the old Grub legacy be overwritten?

Should I remove the old 'boot' flag or leave it like it is?

Do I even need a boot flag on sdb since BIOS is set to boot from sda?

Any other tips before I start mucking around in a perfectly functioning system?

Many thanks.

earther

---

### Post by dino99 on 2010-05-22
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-05-22
I'm not sure about this drive becoming sdb when you move it. I can't be sure linux will change the name. But that wouldn't matter anyway, even if this drive remains sda and the new one is sdb.

You didn't specify what version are you running now, but you seem sure you have grub1. It will be overwritten if you put grub2 from Lucid on this hdd, but why would you do that? If Lucid goes to the new disk, just make sure and double check with the Advanced button in the last screen in the installer, that grub2 also goes to the same disk.

Yes, it will see your other ubuntu and offer a grub menu where you can select.

Boot flags are usually not important for linux and have to be correct on the windows partition if dual booting. But when you have only ubuntu it shouldn't matter.

However, it doesn't hurt leaving the boot flag on the root partition because that's where the boot files are (unless you have separate /boot).

Your 'operation' should go fine, regardless how the drives are called after you add the new one.

---

### Post by earther on 2010-05-22
> **dino99 said:**
> mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)
Thanks for the refresher.  I'm used to using Gparted.  I will also be using the live disk and choosing the advanced option to point to the proper partitions.  Before I install Lucid, I'll disconnect the second drive so it should be pretty straight forward.  Once Lucid is up and running, I'll connect the old Ubuntu drive, reboot and see what happens.  I'm hoping that Lucid will find it.

---

### Post by earther on 2010-05-22
> **darkod said:**
> I'm not sure about this drive becoming sdb when you move it. I can't be sure linux will change the name. But that wouldn't matter anyway, even if this drive remains sda and the new one is sdb.
The old drive will be disconnected when Lucid is installed so the new one should be named sda.

> You didn't specify what version are you running now, but you seem sure you have grub1.
Gutsy Gibbon (with a Hardy kernel) listed under my LH profile is correct.

> Yes, it will see your other ubuntu and offer a grub menu where you can select.
Keeping fingers crossed.

> Boot flags are usually not important for linux and have to be correct on the windows partition if dual booting. But when you have only ubuntu it shouldn't matter.

However, it doesn't hurt leaving the boot flag on the root partition because that's where the boot files are (unless you have separate /boot).
Thanks for the info.

---

### Post by darkod on 2010-05-22
> **earther said:**
> Before I install Lucid, I'll disconnect the second drive so it should be pretty straight forward.  Once Lucid is up and running, I'll connect the old Ubuntu drive, reboot and see what happens.  I'm hoping that Lucid will find it.

IMHO, that's the perfect situation for confusion to happen. Don't forget that not only the /dev/sda, /dev/sdb reference is important, but also for grub hd0, hd1 is important to get right.

When you install the new ubuntu on the new disk, it will be hd0 because it's only one. When you connect the old disk, it's enough if it gets the hd0 mark, and grub will be looking at the wrong disk.

Of course, it doesn't mean it will happen for sure. Just a possibility.

Your drives aren't even the same size, what are you going to do, format the wrong one??? Why disconnecting at all?

At the end of the day, it's up to you. Just don't come back blaming ubuntu if you are tampering with the hardware. :) My opinion is: when installing an OS it needs to know all the hardware you got inside.

Unplugging is for troubleshooting, not for regular installs. :)

---

### Post by earther on 2010-05-22
> **darkod said:**
> IMHO, that's the perfect situation for confusion to happen. Don't forget that not only the /dev/sda, /dev/sdb reference is important, but also for grub hd0, hd1 is important to get right.
I thought Grub2 didn't use hd0?

> When you install the new ubuntu on the new disk, it will be hd0 because it's only one.
Shouldn't it be hd1 in Grub2? 

> Why disconnecting at all?
BIOS boots from sda so I'm putting the new drive in that slot and moving the old one to the second bay.  I figured I'd do it after I know Lucid is functioning properly.  Current backup drive will go into an external enclosure.

> At the end of the day, it's up to you. Just don't come back blaming ubuntu if you are tampering with the hardware. :) My opinion is: when installing an OS it needs to know all the hardware you got inside.
I wouldn't blame Ubuntu but I might be back asking for help if there's a problem. :)

---

### Post by darkod on 2010-05-22
Sorry, it sounded more harsh than intended. :) But I do think you're asking for trouble. No need to be so nervous about the install.

Back to the topic. Grub2 still uses (hdX,Y) format. Also, the disks still start counting from 0, only the partitions from 1.

Adds to the confusion right? :)

So, the first partition on the first boot disk that was hd0,0 in grub1, is hd0,1 in grub2.

In BIOS you would usually tell apart the disks by the model number (unless really identical). And just for reference, first slot, second slot doesn't mean much especially with SATA.

When I was assembling my PC, the board has 6 sata slots. I put my hdd in sata0 and dvd-rw in sata5. My logic was same as yours.

When it booted up, imagine what. :) The dvd-rw is channel0 slave, the hdd is channel1 master.

They made the last two sata ports, sata4 and sata5 as channel0 and raid capable. If not running raid, that is actually your primary channel. :)

So don't bother too much with that. You can easily tell your disks apart in BIOS. Leave both in, and set the new one as first option if that is your plan. Job done.

---

### Post by earther on 2010-05-22
Yes, reason to be nervous.  I am NOT a hardware person.  In fact, I'll be doing this at the local computer shop (my dialup would be pretty useless for updating) and I'll probably let them mess with the hardware.  Unfortunately, they're not Linux geeks so I'll be pretty much on my own.

Are you recommending that I drop the new drive into the current backup slot and install to there?  Then I'd have to change the BIOS to boot from that disk, right?  I don't like messing with the BIOS either.  *sigh*

Thanks for your help.

---

