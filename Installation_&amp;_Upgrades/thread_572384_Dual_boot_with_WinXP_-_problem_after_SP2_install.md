---
title: "Dual boot with WinXP - problem after SP2 install"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by cmacdo on 2007-10-10
Hi everyone,

I am a relative newbie to all this...here is the sequence of events that have led me to post here...
This is all happening btw with a Toshiba Satellite A200-AH7 btw

1. got the new machine with Vista, wiped Vista
2. partitioned 160 GB drive as follows:
Partition 1 - ext3, 100GB
Partition 2 - FAT32, 30GB
Partition 3 - swap, 16 MB
Partition 4 - FAT32, 30GB

3. installed Ubutnu 7.04 on partition 1 - success!
4. installed Windows XP on partition 2 - success!
5. resolved dual boot issue by creating shared mount point, etc etc
6. dual boot fully operational with shared FAT32 D: drive for both - awesome!
7. updated WinXP to SP2
8. update successful (supposedly)
9. reboot machine
10. Windows will no longer boot - missing files like ntldr and others can't remember....
11. tried replacing these files from my other XP machine - still can't boot
12. made the mistake (I assume) of going back in with Ubuntu boot CD and reformatting partition 2 to try a fresh Windows install
13. cannot reinstall WinXP on this drive - get "this disk does not contain a Windows XP-compatible partition"
14. used recovery console to try many things over about a week long period including
-reformatting the C drive (partition 2), format c:
-installing XP on D drive (partition 4)
-fixmbr
-fixboot 
-chkdsk - no errors until i ran fixmbr, now i get "unrecoverable errors" message :(
15. Ubuntu is still working fine btw, but I would really like to get XP on here as well.

So this is where I'm at - considering reformatting the entire machine and beginning this old process over again, perhaps begin with XP and then install Ubutnu on a secondary partition.

If anyone has any further suggestions that might get me out of this mess I would really appreciate it!!

cmac

---

### Post by Herman on 2007-10-10
> considering reformatting the entire machine and beginning this old process over again, perhaps begin with XP and then install Ubutnu on a secondary partitionSimple solution: Delete all partitions and start again, with Windows in partition1. 
Slightly more advanced solution: learn how to edit boot.ini.
 
Most of us find it a lot less complicated when you begin with XP installed first and then add Ubuntu. 

I performed a few experiments with this and I found out that (at least with my computer) it doesn't actually matter which end of the disc partition number1 is situated, as long as it's number1, Windows XP will work okay.

I also found out it's not too difficult to run Windows XP in any other primary partition number too, but you need to be aware that your boot.ini file in Windows XP might need editing if you want to do that.
Once you learn how to access and edit your boot.ini file, you'll be okay no matter what partition number Windows is given.

```
Windows will no longer boot - missing files like ntldr and others can't remember....
``` When Windows tells you it has files that are missing or corrupt, it's just to scare you and throw you off. Error messages in Windows seem to be worded so as to discourage ordinary people (hobbyists) from easily learning  how to do anything with it.
Actually the message 'NTLDR is missing (or corrupt), and dozens of similar error messages just mean Windows can't find NTLDR or whatever file it mentions. Usually all it takes is a simple edit of the boot.ini file to fix it.

You may need to make yourself a special floppy disk with an editable boot.ini file (you can edit the floppy disk from Linux) or a CD with an multipartition capable boot.ini file to boot into your Windows in the fist place so you can edit your boot.ini file to fix the problem.

Here's a link to further links about how to do that and about how to cope with some of the most common Windows booting error messages, [Error messages from Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_Booting_errors")
That link, (and links off it), should help you to get your existing Windows install working.if that's what you decide to do.
> used recovery console to try many things over about a week long period including
[COLOR=Red]** -reformatting the C drive (partition 2), format c:**[/COLOR]
-installing XP on D drive (partition 4)
-fixmbr
-fixboot 
-chkdsk - no errors until i ran fixmbr, now i get "unrecoverable errors" message :( If you really reformatted drive C then you'll probably have to re-install Windows, but you might not need to re-install Ubuntu as well (unless you want to), if you can edit your boot.ini file. I'm not sure if it's too late for that or not. Where is Windows now? In partition 4? Well you should be able to get it booting there now if you want.


Regards, Herman :)

---

### Post by roastgarlic on 2007-10-10
for WIN XP -  boot.ini just holds the partition info as to where the WIN OS is located.

So,
1. Install WINDOWS to a "small" FAT32 partition (this will be drive C).
2. It is then possible to, for example, boot from a WIN98 OS off a floppy disk and then edit anything in the C drive.
3.  After booting to drive C: type this,
   a. attrib  -r  -a  -s  -h     (this will "unhide" hidden files
   b. edit boot.ini, etc

4. It is possible to make a WIN XP boot disk too - needs a boot.ini, ntldr etc

---

### Post by cmacdo on 2007-10-10
thanks for the quick replies! 
the feedback is such a relief after hours of solitary staring at the monitor....

i did actually edit my boot.ini file in windows to add the ubuntu option for the dual boot, and that seemed to work fine until i installed SP2 but maybe my editing of boot.ini is what spawned some of the subsequent problems. 

anyway, even if i end up starting from scratch that's ok....live and learn

---

### Post by Herman on 2007-10-11
Oh, okay, I'm glad you got it working somehow anyway, that's good, all's well that ends well! :)
The boot.ini file is kind of a finicky file to edit, just an extra gap where it doesn't belong is enough to cause serious problems, although from now on you should know now that you can always boot if you can make yourself one of those floppy disks or CD-ROMs with the NTLDR, NTdetect.com and boot.ini on it, so you should never (or rarely ever) be really stuck without a way to boot Windows for long.

Regards, Herman :)

---

### Post by eendoe on 2007-10-11
Ill' take grub over boot.ini any day.

-Install xp first to primary partition
-Install linux onto some of the remaining space

---

