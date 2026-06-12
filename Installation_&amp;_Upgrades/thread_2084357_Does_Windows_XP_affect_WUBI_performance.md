---
title: "Does Windows XP affect WUBI performance?"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2012-11-15
My friend runs an XP system that runs very very slowly. This is despite my tuning his system with many software tools. I suspect that one or more drivers is deficient, especially the monitor driver.
I understand that WUBI runs as/on a virtual disk. So if I install WUBI on his XP system, when it runs, will it depend on any part of XP (for its performance)?

---

### Post by critin on 2012-11-15
If drivers are suspected, check the Window device manager and see if any have the yellow mark across them.  Upgrade them.   Has it been defragged lately?  It's generally recommended to defrag twice before installing wubi.

Try a live ubuntu cd and check the performance.   Go ahead and install wubi, if it doesn't work well it can be uninstalled.   It won't harm and it's the only way to find out for sure.

Install ubuntu over windows as a fresh single OS if windows can't be improved.

---

### Post by oldfred on 2012-11-15
One of the main reasons Windows gets slow is full partition. If you do not have 30% free, it then starts to slow and at 10% free is very slow.

Wubi depends on Windows to boot and uses the NTFS file system but none of the Windows drivers.  So if a full NTFS file system wubi may not even fit or will slow things down more, if a driver issue wubi should be ok.

---

### Post by coffeecat on 2012-11-15
> **welshmike said:**
> So if I install WUBI on his XP system, when it runs, will it depend on any part of XP (for its performance)?

No - it won't depend on XP, only on the NTFS filesystem. However, if the filesystem is badly fragmented it could mean that the wubi installer won't be able to create the virtual partition (which is a single file in the NTFS filesystem - \ubuntu\disks\root.disk) as a contiguous file and the virtual partition root-disk file will itself be fragmented, which will impact performance of the wubi installation. Hence critin's recommendation to defrag before installing.

---

### Post by welshmike on 2012-11-15
> **critin said:**
> If drivers are suspected, check the Window device manager and see if any have the yellow mark across them.  Upgrade them.   Has it been defragged lately?  It's generally recommended to defrag twice before installing wubi.

Try a live ubuntu cd and check the performance.   Go ahead and install wubi, if it doesn't work well it can be uninstalled.   It won't harm and it's the only way to find out for sure.

Install ubuntu over windows as a fresh single OS if windows can't be improved.

Thanks for your reply.
No yellow mark but the monitor driver is way out of date.
I have defragged the hard drive and run total care with System Mechanic.
I did run a live Ubuntu 10.04 CD and the PC performance was very good. So I believed that there was no PC hardware problem.
Also I'm quite familiar with WUBI because that was the trigger that converted me to run Ubuntu as my main operating system way back with 8.04 in 2008.
Oh what a revelation to have an operating system that never slowed down and ran, followed by upgrade to 10.04, for the last four years with no slowdown.

---

### Post by welshmike on 2012-11-15
> **oldfred said:**
> One of the main reasons Windows gets slow is full partition. If you do not have 30% free, it then starts to slow and at 10% free is very slow.

Wubi depends on Windows to boot and uses the NTFS file system but none of the Windows drivers.  So if a full NTFS file system wubi may not even fit or will slow things down more, if a driver issue wubi should be ok.

Again thanks for your help.
There is at least 10GB free on the smallest drive. So WUBI should not be a problem.

---

### Post by welshmike on 2012-11-15
> **coffeecat said:**
> No - it won't depend on XP, only on the NTFS filesystem. However, if the filesystem is badly fragmented it could mean that the wubi installer won't be able to create the virtual partition (which is a single file in the NTFS filesystem - \ubuntu\disks\root.disk) as a contiguous file and the virtual partition root-disk file will itself be fragmented, which will impact performance of the wubi installation. Hence critin's recommendation to defrag before installing.

Live and learn. Thank you coffeecat.

---

### Post by critin on 2012-11-15
> **welshmike said:**
> Again thanks for your help.
There is at least 10GB free on the smallest drive. So WUBI should not be a problem.

10 GB free with windows?  That's not enough room for windows to move, ubuntu will need at least 10GB to run smoothly after updates.  Or are you going to try to give wubi its own 10gb partition? 

Per oldfred's post, this is the reason, or one of them, that windows is so slow.

> Originally Posted by **oldfred**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12356171#post12356171")                 
                 One of the main reasons Windows gets  slow is full partition. If you do not have 30% free, it then starts to  slow and at 10% free is very slow.

---

### Post by welshmike on 2012-11-15
Critin,

The HDD is 40GB. 
XP including apps, personal data and the rest occupy some 25GB and thanks I've now rechecked and the remainder of the HDD (15GB) is free.

I think you'll find that WUBI 12.04 fits in less than 8GB.

---

### Post by coffeecat on 2012-11-16
> **welshmike said:**
> 
I think you'll find that WUBI 12.04 fits in less than 8GB.

A default fresh install of Ubuntu takes up only about 2.4GB, but with wubi you have to take into account the size of the root.disk file, the virtual partition. The default (smallest size) for this is 8GB. Whether your wubi install only has 2.4GB of files or whether it has more, the root.disk file stays the same size - 8GB - in the NTFS filesystem. You say XP takes up about 25GB. Add 8GB = 33GB, which leaves only 7GB breathing space. 33 of 40 used up leaves only 17.5% free which is less than the 30% that oldfred mentioned can cause XP itself to slow down.

But the situation is worse than that - those figures are not correct. The 40 GB is in gigabytes (base 10) which equals 37.25GiB (Gibibytes - base 2). The 8GB virtual partition is in fact 8 GiB and if you got the 25GB figure off XP's explorer that is probably also in GiB. 37.25 - 8 - 25 = 4.25 GiB left free which is only 11.4%. It will work, but you don't have much space to work in and XP will probably be slowed even more.

---

### Post by Wim Sturkenboom on 2012-11-16
Not a useful answer, I assume, but monitors don't have drivers [-X 

They might come with a disk with some files that specify their capabilities, but that is it. For windows, it's registry entries. For Linux, they are useful if you can't find the specs of your monitor (vertical and horizontal refresh rates); read them and place the parameters in xorg.conf.

---

### Post by welshmike on 2012-11-16
> **coffeecat said:**
> A default fresh install of Ubuntu takes up only about 2.4GB, but with wubi you have to take into account the size of the root.disk file, the virtual partition. The default (smallest size) for this is 8GB. Whether your wubi install only has 2.4GB of files or whether it has more, the root.disk file stays the same size - 8GB - in the NTFS filesystem. You say XP takes up about 25GB. Add 8GB = 33GB, which leaves only 7GB breathing space. 33 of 40 used up leaves only 17.5% free which is less than the 30% that oldfred mentioned can cause XP itself to slow down.

But the situation is worse than that - those figures are not correct. The 40 GB is in gigabytes (base 10) which equals 37.25GiB (Gibibytes - base 2). The 8GB virtual partition is in fact 8 GiB and if you got the 25GB figure off XP's explorer that is probably also in GiB. 37.25 - 8 - 25 = 4.25 GiB left free which is only 11.4%. It will work, but you don't have much space to work in and XP will probably be slowed even more.

I think that it is not correct that 30% of the HDD is needed by XP so that it does not slow down. I am running on this laptop a guest XP running under VirtuaBox with Ubuntu 10.4 as the host. VirtualBox allocated 10GB for XP, 8.5GB is used with just 1.5GB free.
It has goes like a rocket (even) with all the programs shown below installed.

[IMG]http://www.hantsnwa.org.uk/programs.jpg[/IMG]

---

### Post by welshmike on 2012-11-16
> **Wim Sturkenboom said:**
> Not a useful answer, I assume, but monitors don't have drivers [-X 

They might come with a disk with some files that specify their capabilities, but that is it. For windows, it's registry entries. For Linux, they are useful if you can't find the specs of your monitor (vertical and horizontal refresh rates); read them and place the parameters in xorg.conf.

OK I stand corrected re "monitors don't have drivers". It could possibly be a corrupted registry that is causing my friend's desktop XP system to run slowly and be painfully slow in bringing up application windows.

My plan now is 
1. To lend my friend my spare laptop. A 7 year old Toshiba that I used today to create a bare bones XP system. I've uninstalled all Toshiba bloatware and the only extra programs installed are Zonelarm Free - Firewall and Anti-Virus, Thunderbird, Firefox and LibreOffice. 
The 60GB HDD has 50GB free.
2. Remove the 40GB HDD from his Dell desktop. (It looks like it is an unknown manufacturer's HDD supplied with the desktop). Move his 150GB Maxtor/Seagate HDD from the middle to the end of the data cable and set its jumpers to be master if necdessary. Reinstall XP, etc and restore his data. If this does not produce an XP system that runs fast enough he will at least have my Toshiba laptop to use and can decide if he will buy a new PC which will if possible have W7 installed on it.

---

### Post by Paddy Landau on 2012-11-16
> **Wim Sturkenboom said:**
> Not a useful answer, I assume, but monitors don't have drivers
I imagine the OP is referring to the graphics drivers. (But my monitor *does* have a driver; it is the subject of a bug, because it worked with 11.04 but no 12.04.)

> **welshmike said:**
> I think that it is not correct that 30% of the HDD is needed by XP so that it does not slow down. I am running on this laptop a guest XP running under VirtuaBox with Ubuntu 10.4 as the host. VirtualBox allocated 10GB for XP, 8.5GB is used with just 1.5GB free.
That is not comparing like-for-like. Not only are you using a different machine, but also the guest machine uses the resources of the host machine, especially if you have allowed the guest to use the host's caching.

> **welshmike said:**
> … the only extra programs installed are Zonelarm Free - Firewall and Anti-Virus…
It is my experience that [Microsoft's Security Essentials]("http://windows.microsoft.com/en-GB/windows/security-essentials-download") works as well as the other free anti-malware products, and does not slow down Windows. You may want to try it instead of ZoneAlarm.

---

### Post by welshmike on 2012-11-16
Thanks Paddy,

I had suspected that the guest machine uses the resources of the host machine.

I have to admit that I am prejudiced against Microsoft's stuff (oh how I appreciate not only Linux distros but the revelation [I'm a retired mainframe System Software developer] of the FSF, FOSS and especially LAMP that I studied and used to create a CMS system in the early 2000s) but I will give Microsoft's Security Essential a go instead of ZoneAlarm.

---

### Post by Paddy Landau on 2012-11-16
> **welshmike said:**
> I have to admit that I am prejudiced against Microsoft's stuff…
Years of a badly-bugged OS can do that. However, MS seems to have been pulling up its socks lately (especially with Windows 7), and the Security Essentials product works well.

Unfortunately for the other companies, Security Essentials may put their personal desktop editions out of business unless they concentrate on Mac OS and Linux (including Android).

---

### Post by welshmike on 2012-11-16
Paddy,

I (reluctantly) agree that Window 7s from the start appears to be a significant improvement over XP maybe thanks to lessons learned from Vista. 
A while ago I installed the last pre-release of W7 on my 7 year old Toshiba laptop that used to have XP on it. My brief experience with it was pleasing.
Today I have been using my Toshiba, removed a Linux distro I was trying out and installed just XP for my friend to use. The IE8 windows update was a bit of a scare when the Toshiba appeared to freeze for a long time. It has just now turned out to be W8 being installed, a reboot and W8 continuing installation with an icon and taskbar free desktop backround showing for along time again until completed.

I'd like to think that Security Essentials was created my Microsoft to overcome Windows operating systems' poor security and not a drive to put AV and Firewall companies out of business. However I've seen Microsoft hit or takeover some independents' software such as video editors and buying out Skype.

---

