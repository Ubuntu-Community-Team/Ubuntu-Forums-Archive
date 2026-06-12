---
title: "&quot;The volume &quot;boot&quot; has only 0 bytes disk space remaining&quot; error"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by leon.lain.delysid on 2014-08-12
Hi everyone! =)
I just woke up and found an error on my computer: 

> The volume "boot" has only 0 bytes disk space remaining

So I got it fixed in less than 5 minutes thanks to a small search resulting in someone prompting someone else to execute this command:

> **sudo apt-get autoremove**

This didn't work out for them but it reduced the allowed /boot space to 55% for me.
No wonder, it removed like 4 unused kernel versions, so, phew! ^^

However, my question is, how come this did happen in the first place? This is just a prompt for general discussion about what happened here.
Let's talk about my system:
It's a **fresh 14.04** install because I got a new computer in april, coinciding on purpose with the new LTS 14.04 version so I'd have a fresh clean install.
I certainly didn't mess with /boot, which is **236M** in total size.
My total / partition space is 212G.

I have a fair knowledge of IT, and I had the reflex of making a web search. My computer was also already turned on, so all I had to do was open a terminal and let autoremove work its solution for my issue.
But the average person might just dismiss the error and then reboot at some point in the future, and then I guess they wouldn't be able to boot back into Linux? I'm guessing a full /boot partition is a serious problem, isn't it?
If it happened to me, who didn't have any kind of special characteristics in my system, would it not happen to everyone else also?

Is my /boot partition too small? How did I have so many kernel versions that it got my /boot completely full?
How can such an issue come up? Somewhere in the update process, this ought to have been thought of, oughtn't it? If the kernel is so heavy and so little space is partitioned for it, why just leave so many old versions on /boot? Or maybe my /boot partition is too small?

---

### Post by TheFu on 2014-08-12
Most people will be caught by this problem, eventually, if they use either LVM or encrypted partitions. /boot is not encrypted and needs to be boot-able.  I don't allow /boot partitions to be smaller than 600M, but I've been pre-creating my partitions pre-install for many years.

If folks used aptitude, the older kernels would be removed automatically. 

The real problem happens when the partition fills late in a kernel update - grub has been updated, but the new initrd isn't built - now the machine will not boot.

For most simple, 1 partition installs, /boot is on / and has 20G+ of storage, so average Ubuntu users don't see this issue.

---

### Post by leon.lain.delysid on 2014-08-12
Oh, I see. I guess I shouldn't have encrypted my partition then.

How can I make sure that the kernel that will be used when I reboot is complete and bootable? I guess I shouldn't reboot before I'm sure that it will work.

Maybe I'll take some time to make a clean reinstall without the drive encryption feature. Or, could I maybe increase the boot partition now? Is it safe to do without breaking the whole system?

---

### Post by TheFu on 2014-08-12
Nothing replaces a solid, versioned, backup system - at least weekly, if not daily.  Then you don't worry so much about these little things.

I don't know of any method to know any kernel update will work before a reboot. Did the install finish? Are you sure?  Have you tried to update again?

---

### Post by leon.lain.delysid on 2014-08-13
Well, since there was 0 bytes left on /boot, I think we can assume the kernel update didn't finish.
I tried to run
> sudo apt-get update
But nothing was updated.
Do you know how I could force a kernel update to run or re-run?

Couldn't I also just tell grub to load the previous kernel version by default (the one that I'm using right now on my booted machine and that we know to work)?
I'll just use that version until the next one comes out and the updater tells grub to use this next one.

Still, I'll probably need to reinstall my whole system because /boot might fill up again. I think I'll just leave everything unencrypted.

Fortunately, I do backup my data. =)
I put in place an ownCloud backup system for all my data when I switched completely to Linux at the beginning of the year. (My life feels so healthier since then... I feel great. =D )

---

### Post by TheFu on 2014-08-13
**sudo aptitude upgrade** - the update just gets the package lists updated, it doesn't actually install anything new. Also, replace apt-get with **aptitude**. May need to add  the force option on an empty install too.  **sudo aptitude -f install**

I wouldn't reinstall an OS over a minor issue that has been solved and you know how to address it going forward. Why did you choose to encrypt? There must have been a reason.

Data mirrors are NOT a backup. Backups let you rebuild the system to be almost identical as it was before an issue, whether that issue happened yesterday, last week or last month.  Smart, incremental, daily backups have solved that issue for a very long time.  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) Using **dpkg &#8212;get-selections ** means not having to backup the OS, just the settings and configs - that saves between 2G and 5G of backup storage, plus the time it takes to check those files every backup process.  Most of my daily backups take 30 seconds and modify less than 50MB of storage. We keep between 60 and 120 days of backups for each system, since it doesn't require much storage.

Perhaps I've missed something about ownCloud - does that retain versioned files?

---

### Post by leon.lain.delysid on 2014-08-20
Well, I executed the *sudo aptitude upgrade* command. And by the way, *aptitude* is great! I also tried *sudo aptitude reinstall*, which reinstalled my supposedly broken linux-headers kernel package.
But then I remembered I saved the *autoremove* command result in a text file. I looked through it again and found this:
> 0 upgraded, 0 newly installed, 16 to remove and 16 not upgraded.
2 not fully installed or removed.
After this operation, 881 MB disk space will be freed.
Do you want to continue? [Y/n] y
After that, I guess it repaired what wasn't finished.
Running *autoremove* again shows no problem with "not fully installed packages".
> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
All was done automatically. These programs are awesome! You've gotta love Linux... ^^

About the backup comments. Yes, you are completely right. I guess this is the direction I would want and need to follow. I already started that with ownCloud but I will have to continue building myself a better backup system in the future. I'm sure there probably are programs that will extract the setting, configs, and packages to be stored into a file that can be backed up...

---

### Post by coffeecat on 2014-08-20
@leon.lain.delysid, as you have discovered, when you opted for the encrypted/LVM install the size of the boot partition created by the installer is far too small. Please would you do something for the community by marking this bug as affecting you?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

You need a launchpad account which is easy to set up. Once you have logged into LP, you can click the link to say it affects you, which will help raise the heat on the bug and hopefully lead to serious attention. Please don't post any comment on the bug thread unless you really need to - let's try to keep this bug free of unnecessary background noise.

---

### Post by leon.lain.delysid on 2014-08-20
I'll be glad to. And it's done. ;)
This is a very recent report. "6 people affected"... I guess we'll have to wait for more people to give this more attention.
I'm guessing there must be many other people in my situation. The situation simply being having a new Trusty installation with disk encryption enabled and letting kernel updates happen as they will. I don't know if kernel updates are automatic by default, but it's safe to say that many other people were affected as well.
To clarify again, I woke up one morning and found a warning window that /boot was lacking space. *df -h* showed 0 byte left free on that partition. I don't know how the update daemon would react to encountering such a problem, but if there is no space, there simply is no space left for the update to finish.
I didn't try to reboot with /boot being full and the update left unfinished, so I don't know what will happen (or already has happened) to people dismissing the warning and leaving the issue as is. My guess is, the kernel doesn't boot, end of the story. (It might be eligible for rescue with a live CD? Maybe one could select a less recent kernel in GRUB?)
I don't even know what rebooting will do to me who has -supposedly- repaired the error. I still haven't rebooted yet. I haven't found the time to close my applications and do it. (Even if it wouldn't so much time... Maybe I'm a little scared too... ^^' )

---

### Post by coffeecat on 2014-08-20
@leon.lain.delysid,  thanks for marking the bug as affecting you. The more heat we get on that bug the better.

Yes, it is a recent bug. Another forum admin, Elfy, and I were discussing this a little while ago, looking into why threads about the problem you encountered were cropping up regularly. We both did test installs, Elfy with a VM and myself with a spare 500GB HD, and confirmed for ourselves what was happening, and Elfy raised the bug report. The problem with the small boot partition is not so much with encryption as with having LVM. If you opt for whole system encryption, you get LVM as well. Whether or not you install with encryption, with LVM you get the separate boot partition. 

With regard to kernel updates, they won't be installed unless you OK them. The software updater in 14.04 will automatically tell you about updates and will list kernel updates if they are available, but you have to approve the updates before they are applied. For most updates, you do not have to approve with your password, but with kernel updates you do. That is a useful pointer: if the software updater is asking for your password, then it is likely that a kernel update is included, and you would be wise to check whether you need to uninstall one or more old kernels once the update is finished. Always keep 2 kernels installed, the latest and the immediately previous one, but all the others can be uninstalled.

---

