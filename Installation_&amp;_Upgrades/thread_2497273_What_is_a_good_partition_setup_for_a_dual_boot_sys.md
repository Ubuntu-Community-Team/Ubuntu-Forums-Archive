---
title: "What is a good partition setup for a dual boot system on a 1TB SSD"
date: 2024-04-28
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2024-04-28
Hi what is a good partition setup for dual booting using a 1TB ssd hard drive. I am thinking of shrinking my Windows partition to about 286GB or 386GB as current windows storage usage is around 88GB. So wondering what is a good safe size for system / and possibly the rest for /home.

---

### Post by ian-weisser on 2024-04-28
What's best for you may be very different from what's best for us.

If this is your first install, just follow the installer defaults. Someday, when you have a good understanding of your real-world needs, you can reinstall differently. Many, many folks later reinstall with different settings.

---

### Post by Omnios on 2024-04-28
> **ian-weisser said:**
> What's best for you may be very different from what's best for us.

If this is your first install, just follow the installer defaults. Someday, when you have a good understanding of your real-world needs, you can reinstall differently. Many, many folks later reinstall with different settings.

I know how to install Ubuntu but have not played around with Linux in like 10 years now. So ssry was doing the Windows gamming thing but now learning Python programming language and want to get into playing with Linux again. Planning on learning advanced terminal and bash scripting etc.

So is 30Gb still good for / ?

---

### Post by oldfred on 2024-04-28
I use Kubuntu and no snaps.
I am using about 16GB of a 30GB partition.

Since Ubuntu now defaults to use a lot of snaps, I have seen users with 20Gb of snaps only. So now larger / is often required.
Only you may know how much data you have.

I prefer to keep / & /home in one partition (my 16GB used) and have data in other partition(s), but like to have some unallocated for future use. I normally have space for at least one more / as I use each LTS as main working install. So using 22.04 but have already installed 24.04 which will in a few days will be my main install. From RAM to NVMe drive it only took less than 10 minutes to install 24.04 and about an hour to reconfigure using mostly scripts to semi-automate updates & changes.

---

### Post by ActionParsnip on 2024-04-29
What will you be using Ubuntu for? Without this we cannot advise any kind of layout.

---

### Post by Omnios on 2024-04-29
> **ActionParsnip said:**
> What will you be using Ubuntu for? Without this we cannot advise any kind of layout.

Will be using as a daily driver for web surfing light gamming, but focus on learning Python programming, advanced terminal usage and bash scripting. Linux is like a toy its fun to play with.

---

### Post by ActionParsnip on 2024-04-29
> **Omnios said:**
> Will be using as a daily driver for web surfing light gamming, but focus on learning Python programming, advanced terminal usage and bash scripting. Linux is like a toy its fun to play with.

OK and what is the Windows side for?

---

### Post by Omnios on 2024-04-29
> **ActionParsnip said:**
> OK and what is the Windows side for?

The windows partition will just be there in case I need it for something like a game or something. So generally it will not be used.

---

### Post by ActionParsnip on 2024-04-29
> **Omnios said:**
> The windows partition will just be there in case I need it for something like a game or something. So generally it will not be used.

A game? Singular? Then I'd say 400Gb NTFS leaving the rest unpartitioned. Then boot to Ubuntu installer. Setup an LVM for the rest, then 50Gb for /, 1xRAM for swap and the rest for /home

Just how I'd do it. There is no single answer

---

### Post by Omnios on 2024-04-29
> **ActionParsnip said:**
> A game? Singular? Then I'd say 400Gb NTFS leaving the rest unpartitioned. Then boot to Ubuntu installer. Setup an LVM for the rest, then 50Gb for /, 1xRAM for swap and the rest for /home

Just how I'd do it. There is no single answer

Thanks for the help. So thinking I will shrink my windows partition to 386GB, 64GB for / and the rest for /home. But still not sure about a swap file size as I have an m.2 SSD and 16GB 2667 MHz ram.

---

### Post by ActionParsnip on 2024-04-29
> **Omnios said:**
> Thanks for the help. So thinking I will shrink my windows partition to 386GB, 64GB for / and the rest for /home. But still not sure about a swap file size as I have an m.2 SSD and 16GB 2667 MHz ram.

I thought this was for a new install? Planning partitions means you don't have to shrink anything. 16Gb swap will be plenty but you could probably get away with 8Gb. It's small potatoes on a 1Tb disk

---

### Post by ActionParsnip on 2024-04-29
> **Omnios said:**
> Thanks for the help. So thinking I will shrink my windows partition to 386GB, 64GB for / and the rest for /home. But still not sure about a swap file size as I have an m.2 SSD and 16GB 2667 MHz ram.

I thought this was for a new install? Planning partitions means you don't have to shrink anything.
Another way is to have an NTFS partition mounted to something like /data which would be seen as "D:" in Windows. You can keep your casual user data on there and both OSes can access the files. With 16Gb RAM I'd go for 8Gb swap. You'll barely touch it

---

### Post by Omnios on 2024-04-29
> **ActionParsnip said:**
> I thought this was for a new install? Planning partitions means you don't have to shrink anything.
Another way is to have an NTFS partition mounted to something like /data which would be seen as "D:" in Windows. You can keep your casual user data on there and both OSes can access the files. With 16Gb RAM I'd go for 8Gb swap. You'll barely touch it

? the install is a new install of Kubuntu with an existing windows 10 install.

---

### Post by Omnios on 2024-05-01
So played round with Windows 10 using Create and partition hard disks program and spent a while to get the actual size showing in This PC C drive to be exactly 286GB with is big enough as I am only using 80GB and have 200 GB free. Now for my next step is what partition size do I need to use for a 64GB / partition to have the actual size show as 64GB in Kubuntu? Kind of sounds stupid but having phun.

---

### Post by ActionParsnip on 2024-05-01
> **Omnios said:**
> So played round with Windows 10 using Create and partition hard disks program and spent a while to get the actual size showing in This PC C drive to be exactly 286GB with is big enough as I am only using 80GB and have 200 GB free. Now for my next step is what partition size do I need to use for a 64GB / partition to have the actual size show as 64GB in Kubuntu? Kind of sounds stupid but having phun.

Set 64Gb. You can use the "something else" option in the installer for setting file systems up. The dual boot will be managed for you. I'm guessing your Windows OS was preinstalled or installed before you started venturing into Ubuntu

---

### Post by Omnios on 2024-05-01
> **ActionParsnip said:**
> Set 64Gb. You can use the "something else" option in the installer for setting file systems up. The dual boot will be managed for you. I'm guessing your Windows OS was preinstalled or installed before you started venturing into Ubuntu

 Yes Windows 10 is installed already and will be dual booting with Kubuntu as I like KDE. So the question is based on that I had to shrink the Windows partition to 286.01 to show it as 286 in windows C: partition size. So will choosing 64GB for / during install show as 64GB in Kubuntu disk info?

---

### Post by TheFu on 2024-05-01
In over 30 yrs of setting up Unix and Linux systems, I've never, ever, guessed the correct amount of storage needed for any specific system.  

Long ago, I never had enough. Every byte would be filled with junk.  As I learned more and more, I became better as putting things where they belonged and not installing hundreds of programs/applications to be used 5 times, then never again. Since around 2010 (10.04), I've been anti-bloat and strive to avoid bloat not just with the data I keep, but with the programs installed.

For about 10 yrs, I've decided that I'll never actually guess correctly, so I setup storage for maximum flexibility.  That's a little more complex than doing an install with Next-->Next-->Next-->Next-->Next-->Next accepting all defaults, but it makes any mistakes in storage layout much easier to fix later when those mistakes become clear in 3-24 months.

Of course, we all start trying to have the easiest storage layout possible. Turns out that is also usually the least flexible.  So, only you know your skill level and your ability to deal with hassles and your desire for flexibility.  For many people, when they make a mistake, it isn't THAT hard to backup their data, then wipe everything and start over with slightly different allocations that solve the last issue.  I think this is probably best, since you'll learn from your own mistakes and will be more likely to avoid them in the future.

There are plenty of storage layout threads in these forums.  Take a look at those. Find the suggestions that make the most sense to you. Try one out, expecting to redo it in a month if it doesn't work out.  Perhaps everything will be fine and you'll revisit it in 6 months or a year or 2 years?  If it works for you, then I call that a "success" and no need to fret over it too much.

You'll pick the best choice for your needs and skill.

---

### Post by MAFoElffen on 2024-05-02
Windows 10 or 11?

Windows 10 had a recent cumulative update where it crashed the systems... They increased the size of what was needed for the recovery partition, so the recovery partition needed to be resized to get around that...

My needs have changed for sizes of partitions on new installs.

It used to be 500MB to 750MB for EFI partitions. I recently bumped my sizes for those to 1GB. I use more EFI applications and scripts these days, which were bumping my limits of 750MB.

My sizes for Linux /boot partition used to be 1GB. With ZFS, I bumped those initially up to 2GB, then later to 3GB, so I had more room for snapshots. 

I used to allocate 40GB - 60GB for OS Root (with separate /home). Now 60-80GB. Just 40 GB, I was bumping into problems for updates and it a user did a do-release-upgrade, where they would get space errors. 

I do separate home and data partitions...

For playing with python code, you might also look into KVM, to setup test environments on VM's. *** Good to do testing on something that is isolated from for daily driver.

For me, I like using Eclipse PyDEV as an IDE.

---

### Post by Omnios on 2024-05-02
> **MAFoElffen said:**
> Windows 10 or 11?

Windows 10 had a recent cumulative update where it crashed the systems... They increased the size of what was needed for the recovery partition, so the recovery partition needed to be resized to get around that...

My needs have changed for sizes of partitions on new installs.

It used to be 500MB to 750MB for EFI partitions. I recently bumped my sizes for those to 1GB. I use more EFI applications and scripts these days, which were bumping my limits of 750MB.

My sizes for Linux /boot partition used to be 1GB. With ZFS, I bumped those initially up to 2GB, then later to 3GB, so I had more room for snapshots. 

I used to allocate 40GB - 60GB for OS Root (with separate /home). Now 60-80GB. Just 40 GB, I was bumping into problems for updates and it a user did a do-release-upgrade, where they would get space errors. 

I do separate home and data partitions...

For playing with python code, you might also look into KVM, to setup test environments on VM's. *** Good to do testing on something that is isolated from for daily driver.

For me, I like using Eclipse PyDEV as an IDE.

 Would you recommend upgrading to Windows 11 before installing Ubuntu or Kubuntu? Other than possibly playing a game like Path Of Exiles probably will not use Windows.

---

### Post by MAFoElffen on 2024-05-04
Upgrade from Win 10 to Win 11 first? Yes.

Remember to do good backups, between the different stages of that journey. Have a good fallback point.

Back a few months ago there was a Win 10 upgrade error, where it you installed Win 10 from a build number some time ago... A recent update tried to rewrite the Windows Recovery partition and filled it up, causing an update crash loop. The size of it needs to be 550MB or larger. Microsoft, even today, says it can't fix this error, or get around it though it's update system. That it can only be corrected by manual intervention. The fix is to resize the WIN OS partition from the start of it (which can be done from Win RE, but not the GUI Storage management toolset), delete the old Windows Recovery partition, recreate and format it... Then reapply the update, for it to recreate/rewrite it.

You would have thought they they would add a hot-patch to first check the minimum size of the Win Recovery partition, before it writing to it, to ensure it doesn't do that... But that makes too much sense right?

So yes, if you are keeping Windows, and installing Ubuntu alongside of Windows... Get the Windows issues straightened out first. That way, there is less of a risk of Windows ignoring whatever else is there on the machine, before it tries applying some crazy updates and fixes to it's own problems. It has an ego, and could care less what else is there that is not Windows. I do support Windows OS'es to my customers, but in that respect, I compare it to being a "Narcissistic Psychopath". Making it play well with others, is not (directly) how Microsoft makes money.

But then again, that gives me a niche, showing people how, despite that, they can play well with each other, if you do it in certain ways...

A few tips, when you make the jump between fixing Windows, and installing Ubuntu (or any other Linux based OS):

[LIST]
[*]Turn off SecureBoot in the BIOS. My machines here have SecureBoot enabled... And Ubuntu installs fine, BUT-- (And a big but) Some machines (example HP) do not like that at all, and tries to prevent anything beside Windows from booting with that enabled. Know 'the fight' before it starts. 
[*]If your machine has Intel RST/Optane, disable it and completely remove the module(s). That type of disk caching does not work for multi-boot systems. 
[*]If the BIOS SATA Mode is set to RAID instead of AHCI, boot from Windows to Safe Mode, on the way, interrupt the boot sequence into the BIOS setting to reset, the SATA mode to AHCI, save and exit... In Safe Mode, just that process of doing that will load the AHCI drivers into Windows, then close it down or reboot. 
[*]If you are using Windows BitLocker, suspend it before installing Ubuntu. Then turn it back on after the install. 
[/LIST]

---

### Post by Omnios on 2024-05-16
> **MAFoElffen said:**
> Upgrade from Win 10 to Win 11 first? Yes.

Remember to do good backups, between the different stages of that journey. Have a good fallback point.

Back a few months ago there was a Win 10 upgrade error, where it you installed Win 10 from a build number some time ago... A recent update tried to rewrite the Windows Recovery partition and filled it up, causing an update crash loop. The size of it needs to be 550MB or larger. Microsoft, even today, says it can't fix this error, or get around it though it's update system. That it can only be corrected by manual intervention. The fix is to resize the WIN OS partition from the start of it (which can be done from Win RE, but not the GUI Storage management toolset), delete the old Windows Recovery partition, recreate and format it... Then reapply the update, for it to recreate/rewrite it.

You would have thought they they would add a hot-patch to first check the minimum size of the Win Recovery partition, before it writing to it, to ensure it doesn't do that... But that makes too much sense right?

So yes, if you are keeping Windows, and installing Ubuntu alongside of Windows... Get the Windows issues straightened out first. That way, there is less of a risk of Windows ignoring whatever else is there on the machine, before it tries applying some crazy updates and fixes to it's own problems. It has an ego, and could care less what else is there that is not Windows. I do support Windows OS'es to my customers, but in that respect, I compare it to being a "Narcissistic Psychopath". Making it play well with others, is not (directly) how Microsoft makes money.

But then again, that gives me a niche, showing people how, despite that, they can play well with each other, if you do it in certain ways...

A few tips, when you make the jump between fixing Windows, and installing Ubuntu (or any other Linux based OS):

[LIST]
[*]Turn off SecureBoot in the BIOS. My machines here have SecureBoot enabled... And Ubuntu installs fine, BUT-- (And a big but) Some machines (example HP) do not like that at all, and tries to prevent anything beside Windows from booting with that enabled. Know 'the fight' before it starts.
[*]If your machine has Intel RST/Optane, disable it and completely remove the module(s). That type of disk caching does not work for multi-boot systems.
[*]If the BIOS SATA Mode is set to RAID instead of AHCI, boot from Windows to Safe Mode, on the way, interrupt the boot sequence into the BIOS setting to reset, the SATA mode to AHCI, save and exit... In Safe Mode, just that process of doing that will load the AHCI drivers into Windows, then close it down or reboot.
[*]If you are using Windows BitLocker, suspend it before installing Ubuntu. Then turn it back on after the install.
[/LIST]


 Hi I upgraded to Windows 11 and when I did I had blank HD area of 600GB and windows put the windows recovery partition right after Widows 11 partition in the middle of the Hard Drive. I am wondering if this will screw up my dual boot install and I think I heard windows looks at the end of the hard drive for the recovery partition. If this is the case might just stop using windows and just install Ubuntu. Any suggestions?

---

