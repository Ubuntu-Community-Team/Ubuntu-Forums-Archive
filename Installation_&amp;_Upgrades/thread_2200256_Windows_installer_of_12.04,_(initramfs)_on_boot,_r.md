---
title: "Windows installer of 12.04, (initramfs) on boot, repair-boot, kernal panic error"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by CaronMargarete on 2014-01-18
New laptop with Win7, ran Windows Installer to upload 12.04 - ran well, no issues. Rebooted laptop and checked windows booted successful, it did. Rebooted, selected ubuntu - got black screen with two lines of (initramfs).

Could press any key to get around it. Rebooted.

Using the live USB I had previously downloaded, ran through the terminal the boot-repair [instructions]("https://help.ubuntu.com/community/Boot-Repair"). All ran reasonably successfully until the end - got an error of some kind but didn't note it because the prompt that the repair was successful was also displayed. [http://paste.ubuntu.com/6773220/](http://paste.ubuntu.com/6773220/)

Now windows still boots successfully but still ubuntu doesn't - gives the following error on a black screen[INDENT]
[36.680293] Kernal panic - not syncing: Attempting to kill init! exitcode = 0x00000100
[36.680293]
[36.680342] drm_kms_helper: panic occurred, switching back to text console
[/INDENT]

Again, only rebooting the system would get me back to windows.

What the heck??? Kernal panic. Panic occurred. It's all a bit melodramatic. 
Ideas on a fix?

---

### Post by Bucky Ball on 2014-01-18
FYI: Wubi is not supported anymore, even though it's still available. Might be a better option to go for a dual-boot or try Ubuntu from a Ubuntu Live install disk/USB.

Few use Wubi, but hopefully someone will pop up with a fix. ;)

---

### Post by CaronMargarete on 2014-01-18
Truly? Damn. If it's not supported it shouldn't be available - or at minimum should come with a blazen warning that it's not supported. ****. How do I now uninstall to start again???

---

### Post by oldfred on 2014-01-18
You are showing SFS type partitions which are Windows dynamic not standard basic partitions. Linux does not work with the proprietary dynamic partitions. And Windows does not let you easily undo the conversion, but the conversion to dynamic is just one click.

Is your system also an Ultrabook with the 32GB drive as an SSD. That uses Intel SRT which is RAID and adds another level of complication.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)


  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by CaronMargarete on 2014-01-18
Oh dear me! What a pickle this is!!! If only there was a[ clearer warning]("http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows") about it's lack of support and functionality... ho hum! Right. Soooo has anyone got experience using the Seven Forums disk tute?

---

### Post by oldfred on 2014-01-18
I have also these links, but since you also have Intel SRT I am not sure what else may be an issue.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

### Post by CaronMargarete on 2014-01-18
Thanks oldfred, I appreciate your time. I'm not sure additional links are going to help me since I don't really know what I'm doing in the first instance. It used to be straight forward. Given that it is a notebook that had windows already installed I do not have windows cd's to do a complete reinstall if the seven forum tute goes awry - forget that, the laptop doesn't even have a cd drive so I wouldn't know how to reinstall windows even if I had to! 

Worse case scenario I have to pay someone to do the reinstall. That would suck but I don't see what else I can do if the Seven Forums tute (option 1) doesn't work... here goes nothing. Fingers crossed....

# Edit #

Ran it successfully. Windows is fine. Still cannot load ubuntu. Now I'm getting error:

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
Give root password for maintenance (or type Control-D to continue):

So I don't have a password set up and if I try to type Control-D or anything for that matter I get nothing except "Login incorrect Give root password for maintenance (or type Control-D to continue):" 

Right... so... next suggestion would be to???

---

### Post by oldfred on 2014-01-19
Where are you getting filesysem check error? Windows, Ubuntu or Ubuntu install media?
If Windows or another NTFS partition, you may need chkdsk from Windows. 
If install media it may not have been downloaded correctly or written correctly. 

Best to fully backup Windows and make a Windows repairCD or flash drive. Suggestions for alternative are in link in my signature for UEFI but applies for any system. You should have a repair CD or flash drive for the current version of every system installed. Ubuntu live installer works, but Windows has you make your own since they do not ship install media anymore.

---

### Post by CaronMargarete on 2014-01-19
Amazingly, oldfred, the fix I found was ridiculously simple. I was having a look through the installed programs and saw ubuntu listed. When I clicked on it, it prompted to uninstall it. Naturally, I followed though and low & behold - we're back to square one!!! Thank you for your support - simply knowing someone else with a lot more knowledge is aware is quite helpful.

---

### Post by oldfred on 2014-01-19
Was that then a wubi install? 
That does not work with UEFI as wubi does not work with UEFI. 

And 12.04 is last version supported of wubi.

---

