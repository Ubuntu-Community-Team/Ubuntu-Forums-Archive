---
title: "advice on grub, multiboot ubuntu/debian"
date: 2022-10-18
forum: Installation &amp; Upgrades
---

### Post by bitrat2 on 2022-10-18
Hi, 

apologies for this portfolio topic, but I'm looking for a strategy rather than tactics.

I currently have Ubuntu 18.04 LTS installed on HDD.  I'd like to upgrade to 20.04.5 LTS or 22.04 LTS.

I'd like to have the new OS running before I delete the old one.  I can back up all my data, but I need my system to be operational, not bricked while I back out of failed experiments.

I'd expect to use the same /home directory for all installations, on it's own partition.

**Q1:** Should I prefer the latest LTS?

**Q2:** What's the best way to install  and multiboot a second Ubuntu OS on a HDD?

**Q4:** Can I install one or more bare linux distros using the same approach?

**Q5:** What disk resources (eg /swap) can installations share?  How do I do that?

**Q6:** I'd like to follow standard installation procedure, but also retain some control over boot options.  Is grub the best boot manager to use?  What are the options?

This is probably a familiar task for many, but I've only used multiboot for Windows/Linux installations, and not for a few years, so some general pointers would be appreciated!

Cheers,
bitrat

PS: I have a 120GB SSD on hand, which I may yet use for the primary OS.  Any comments/advice on this?

---

### Post by grahammechanical on 2022-10-18
> apologies for this portfolio topic, but I'm looking for a strategy rather than tactics.

In my opinion, topics like this are better put in the Ubuntu, Linux and OS chat section of the forum. We all have different views.

> **Q1:** Should I prefer the latest LTS?[QUOTE]

Yes. Without a doubt. 

> **Q2:** What's the best way to install  and multiboot a second Ubuntu OS on a HDD?

In my opinion there is not a best way but just two different ways. A) the install alongside option. B) Something Else Where we tell the installer which partitions to use. 

What happened to question 3?

> **Q4:** Can I install one or more bare linux distros using the same approach?

Of course. We do need to take into account any differences in installation procedures that different distributions may have.

> **Q5:** What disk resources (eg /swap) can installations share?  How do I do that?

Disk resources will depend on the minimum specifications of each distributions. I would not advise having different distributions use the same /home partition. Configuration files will become messed up. As we can only run one distribution at a time then the /swap partition can be shared. 

> **Q6:** I'd like to follow standard installation procedure, but also  retain some control over boot options.  Is grub the best boot manager to  use?  What are the options?

Grub is not the only Linux bootloader but it is the one used by Debian and Ubuntu based distributions. Using Grub for one distribution and an alternative for another distribution on the same machine might cause complications, in my opinion.

What control over boot options do you think exist? 

Regards

---

### Post by oldfred on 2022-10-18
I have always had multiple Ubuntu installs. 
I keep latest LTS as main working install. Usually install next LTS and keep older partition working until 4 years old.
I often install interim, just to see what has changes & make update to next LTS a bit more understandable.

Best not to share /home. You normally can upgrade. Software usually designed to update any necessary files to work with new versions. But down grade not usually supported. So some apps may not like newer data files. For example, I used to be able to share Firefox's profile across different Ubuntu installs, now it complains.

I keep /home inside each install, have copied it to new install on occasion, but also have scripted many settings. Often want to experiment and do not want to modify my default install's settings.
And then I have common data partition for all data normally in /home. So /home is actually small.

---

### Post by bitrat2 on 2022-10-18
Thanks both.

On versions, I see Ubuntu 21.10 uses a snap version of firefox.  I don't like snap and would like to eliminate all snap installs from my system and (where possible) use traditional builds or an AppImage.  Will this be more difficult with 22.04?

Sorry about Q3.  I added a new Q1 and forgot to increment the other Q's...

[B][I]What control over boot options do you think exist?
[/I][/B]Never mind.  It's well out of date, but I read something about multiple Ubuntu installations trying to install their Grub instance on the same EFI location, and that there are other EFI boot loaders that are easier to manually maintain.    I'd like to learn (in principle) how to modify GRUB to boot another OS and I want to know in advance if there are any fish hooks.  
[B][I]
common data partition for all data
[/I][/B]I agree, although I have more than one.  I'm typically the only user and ideally I only use the system 'users' as profiles, so config info and WIP on the Desktop are mostly all that's ever in /home.  I want my data to be as isolated from the underlying OS as possible.  Actually, this has been very helpful to think about, even though I though I already had!  :D


Anyway, sounds like I should just buckle up and get on with it.

---

### Post by grahammechanical on 2022-10-18
Here you can download the Grub manual

[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)

> I read something about multiple Ubuntu installations trying to install their Grub instance on the same EFI location

I do not think that is an issue. The EFi System partition is usually between 500 and 600 MB. My EFi partition is 537 MB and it is only 1.2% full. I have two installs of Ubuntu. There is room in this partition for Windows EFI boot files and Ubuntu EFI boot files. Another install of Ubuntu will not add any more EFI boot files. It most likely will overwrite the existing Ubuntu EFI boot files with it own versions. I do believe that all Linux distributions will have to have the same EFI boot files. They are all open source and not limited to a particular distribution. They have also been verified and certified by Microsoft so that Secure Boot does not block the running of this boot code. Ubuntu developers early on approached Microsoft to get these EFI boot loader files signed by Microsoft.

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

Regards

---

### Post by oldfred on 2022-10-18
Last install is the version of grub that will boot by default.
Then grub menu will offer to boot all other installs.
But with grub 2.06 they want to turn off os-prober for security reasons. Scanning every partition may not be secure.
Often they suggest just running once, then turn os-prober off.

I suggest leaving os-prober off and copying any boot stanzas for other installs into 40_custom. 
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by ActionParsnip on 2022-10-19
If you are asking if you should use the latest LTS then you should probably use the latest LTS. It is supported for 5 years so will be supported until April 2027

---

### Post by bitrat2 on 2022-10-19
Thanks everybody.  Great links thanks grahammechanical and oldfred.  :smile:

One more question: I'd like to experiment with Ubuntu for headless  servers and Docker images, and also try some alternative window  managers, such as icewm or fluxbox.

If anyone has any advice and/or links on this, that would be great.

I'll give it a day then mark this solved.

---

### Post by yancek on 2022-10-19
You might install some virtual software such as VirtualBox on one of your other installs.  No probolem with modifying the bootloader in that case and you can experiment without causing problems with the permanent installs.

---

### Post by bitrat2 on 2022-10-19
> **yancek said:**
> You might install some virtual software such as VirtualBox on one of your other installs.  No probolem with modifying the bootloader in that case and you can experiment without causing problems with the permanent installs.

I've never tried multiboot on a VM and wasn't sure it would work the same, but I guess it does.  Thanks!

---

