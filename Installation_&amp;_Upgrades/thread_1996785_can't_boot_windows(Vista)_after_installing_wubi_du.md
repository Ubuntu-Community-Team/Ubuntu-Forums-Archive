---
title: "can't boot windows(Vista) after installing wubi dual boot on F Drive"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Neuralgen on 2012-06-04
Yesterday I installed wubi on my vista system (custom built desktop) and all seemed to go perfectly. The first reboot gave me the option of going to Vista or Ubuntu and I chose Ubuntu.  Every time I reboot now it goes straight to Ubuntu with no option screen appearing.

I have two identical 150G hard drives.  The first (C is single partition and is where Vista was installed.  The second was my D: drive under Vista which I shrunk to 125G and then created a 25G partition. Thus I had C:(150) D:(125) E:(dvd) F:(25).

I told wubi to install ubuntu on F: and life was beautiful, even wireless was a snap which is usually a pain.  But now I can't go back to Vista.

When I try to repair Windows with my recovery disk it says there are no problems found (tried 3 times)

I also found a suggestion on these forums to try:

bootrec.exe /fixboot
bootrec.exe /fixmbr

but that didn't help.

UPDATE
I appear to be in death spiral.  The system (Ubuntu/Wubi) is getting much slower.

I ran boot-repair and tried to upload the generated url:  'paste.ubuntu.com/1025288' to this post in the manage attachments for creating posts but got message that it is an invalid file.  However, if you go to that link you will see the bootinfo for my system so the link is correct.

I also found a lot of strange looking folders in my windows partition and have included here a screenshot of the ProgramData folder where you  can see several examples.

UPDATE 2

I just learned (thanks megaptera) that these windows files are probably not Wubi related.  See : [http://ask-leo.com/can_i_delete_thes...d_folders.html]("http://ask-leo.com/can_i_delete_these_randomly_named_folders.html")


GOAL
I just want to recover windows and never ever again touch Wubi.  Next  time I install real Ubuntu on external drive.  Please help me reach the  promised land....

---

### Post by Neuralgen on 2012-06-05
I installed Wubi a couple days ago and can no longer boot into Windows(Vista). Reboots go straight to Ubuntu.  I just looked at Window's partition and noticed very suspicious folders scattered all over and wondered if this is abnormal and might be a clue.  See screenshot of Program Data folder:

---

### Post by Megaptera on 2012-06-05
They could be related to Windows updates as described here: [http://ask-leo.com/can_i_delete_these_randomly_named_folders.html](http://ask-leo.com/can_i_delete_these_randomly_named_folders.html)

Hope this helps?

---

### Post by Neuralgen on 2012-06-05
Many thanks, first piece of good news since Wubi fiasco...

---

### Post by bcbc on 2012-06-05
> **Neuralgen said:**
> I installed Wubi a couple days ago and can no longer boot into Windows(Vista). Reboots go straight to Ubuntu.  I just looked at Window's partition and noticed very suspicious folders scattered all over and wondered if this is abnormal and might be a clue.  See screenshot of Program Data folder:

Please can you give some feedback on this please. When you install Wubi with Vista/7 it is supposed to boot straight into Ubuntu **only the first reboot** following the install. After that you are supposed to see the Windows Boot Manager. 

If this is not the case, in other words, multiple reboots went straight into Ubuntu, [please file a bug]("https://bugs.launchpad.net/wubi/+filebug").

The reason I am asking is that I've seen reports of this, but it's unclear whether it's more a 'panic' when the first reboot goes straight into Ubuntu or if it's really the case that Ubuntu boots multiple times, which is a problem obviously - and the only way to address this is through a bug report.

Thanks

---

### Post by Neuralgen on 2012-06-05
I was given the option to choose Windows or Ubuntu only once just after  install of Wubi.  I honestly can't remember whether the sequence was:

1)install Wubi->given option & chose ubuntu->reboot(s)->never again given option

or 

2)install Wubi->ubuntu->reboot->given option & chose ubuntu->reboot(s)->never again given option

The only thing I can say for sure is that after installing Wubi I never again went back to Windows but on at least one occasion (I think only once) among the first few reboots (believe it was first) I was given the option but chose Ubuntu and since then haven't been given option

---

### Post by bcbc on 2012-06-05
So you still cannot access Vista? Try hitting the F8 key, or arrow keys, when it boots, this could interrupt the Windows boot manager. If it doesn't work then you'll probably need a windows repair CD to fix it. 

Please file a bug report as well and provide as much detail as you can recall. Thanks

---

### Post by bcbc on 2012-06-05
Thinking about it some more, it's probably that this is a windows bug. The Wubi code that sets Ubuntu to boot one-time only hasn't been modified so there is nothing to explain it suddenly not working. Also, if it was a wubi issue it would affect all Vista/7 installs.

But, it's still a good idea to raise a wubi bug. If it affects a number of people, it might be safer just to revert to always let the user decide rather than booting straight into Ubuntu the first time. This way it brings it to the developers' attention.

---

### Post by oldfred on 2012-06-06
You have a folder that says flexnet. That is drm software used to lock down some application you installed in Windows. It writes into the sectors just after the MBR.

You show one 500GB drive and two 150GB drives. Are you booting from sdb? That seems to be the one with your Windows install. It has the syslinux boot loader which works for most and would be from the Boot-Repair, but your flexnet may then cause issues. I would use a Windows repair CD to install the Windows boot loader.

Some of the commands to fix Windows my overwrite the wubi settings you have added.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

With 3 drives and a separate partition for wubi, why not a full partitioned install of Ubuntu with its boot loader on the sdc drive. You can then leave the Windows boot loader on sdb and boot that directly from BIOS if need be, but grub in the MBR of sdc will let you boot both systems.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Neuralgen on 2012-06-06
Sorry Sorry Sorry

When I ran bootinfoscript I forgot that because of all my problems  I had attached an external 500G drive to copy my entire C: and D:  windows files to it.  It is odd that it shows up as sda; I would have expected sdc but who knows.  I have rerun bootinfoscript w/o external drive  and the output is attached to the next post (max 5 attachments used up by pictures for this post).

In any case I have disconnected the external drive and now have only two 150G drives as described in my original post.  The BIOS is configured to boot off sda (primary drive?).  I have used F8 to switch booting between the two drives and always end up in Ubuntu.  The images attached show each screen during a typical bootup.  The error message on last screen is apparently not a concern from what I can determine on these forums.

I have also booted with my Vista installation dvd and it detects Vista but not Ubuntu. 

I told it to perform the startup repair but it just says it "could not detect a problem".

---

### Post by Neuralgen on 2012-06-06
bootinfoscript output attached...

---

### Post by oldfred on 2012-06-06
Are you booting from the correct 150GB? I have two 160GB drives and it took a while for me to know which one I was really booting from. Mine always matched SATA port number and last couple digits were different, but otherwise they looked the same on boot menu.

Your sdb has a Windows boot loader but no install nor boot flagged partition on that drive. That may give that type of error.

If you have two drives, why wubi. It is intended to test Ubuntu for a longer test than a liveCD and avoid the issues of partitioning. But with two drives you can easily add the extended and logical partitions for a full partitioned install.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)


Windows will never see Ubuntu. Wubi is just a file inside the NTFS partition. Wubi just adds an entry to boot.ini for XP or the BCD for Vista/7 to boot from.

Did you add the wubi entry above the Windows entry or as the default entry  in the BCD and then set timeout to 0 or very small number so it choose first choice & immediately boots. 
With grub I have hit down arrow and it does pick that up, not sure if arrow keys would work in Vista or not before it shows menu.

---

### Post by Neuralgen on 2012-06-06
> Your sdb has a Windows boot loader but no install nor boot flagged partition on that drive. That may give that type of error.I gather you mean the "prefix" error?

> If you have two drives, why wubi. It is intended to test Ubuntu for a  longer test than a liveCD and avoid the issues of partitioning. But with  two drives you can easily add the extended and logical partitions for a  full partitioned install.I thought, naively, it would be safer.  Once I get over this hump I'll do a "true" installation.  I'm not sure what drive I will use though, because my two  Vista 150G's are much faster than the external 500G which was always intended for backups and such.   Another benefit of going with Wubi was it  allowed me to delay this wrenching decision.

> Did you add the wubi entry above the Windows entry or as the default  entry  in the BCD and then set timeout to 0 or very small number so it  choose first choice & immediately boots. I believe I accepted all defaults when installing Wubi except to tell it to install in the F: drive which was the 25G partition that I had formatted clean for that purpose.  I'm certain I didn't take any steps to specify which entry it should be nor what timeout interval to use.

I will try rebooting now and using down arrow to see if  it intercepts a menu.  I doubt it because I video'ed entire boot sequence to look for missed messages and you would think the menu would flash up for an instant.

I'm not sure where this is all headed though I appreciate your help.

---

### Post by Neuralgen on 2012-06-06
I rebooted several times trying down-arrow to catch possible menu.  No dice.

Went into bios and set disk 2 to be primary (disk 1 is currently P) and tried booting.  Got expected error message to insert a bootable device.  Swapped disks back and booted fine but as usual went straight to Ubuntu.

This is sooo frustrating.  Is there a windows utility on the repair disk that I can invoke  to repair the booting sequence.  I don't care if I'm unable to boot into Ubuntu because I intend to do a reinstall of it.  I just want to get back to Vista for my tax records, games, emails, ...

---

### Post by Neuralgen on 2012-06-06
This thread is essentially a sidebar to a more serious problem that I've posted in:

[http://ubuntuforums.org/showthread.php?t=1996785](http://ubuntuforums.org/showthread.php?t=1996785)

I made the spurious files issue a separate thread because it seemed to be a topic all it's own.

---

### Post by Mark Phelps on 2012-06-06
Sorry, don't know of any free solutions, but if you're willing to spend some money, what has generally worked for me in the past is using the boot repair features of a WinPE CD made from the Macrium  Reflect (MR) windows app.

You have to purchase the Standard version of MR to get the feature to create a WinPE Boot CD.  But once you have done that, you can use it to repair the Windows Boot.

The advantage is has over the Windows CD is that it does it all in one pass.

Your PC ... your money ... your choice.

---

### Post by sffvba[e0rt on 2012-06-06
*Threads **merged**.*


404

---

### Post by oldfred on 2012-06-06
I do not know if f8 works with Vista or not, but as soon as you boot try f8 to see if you can get into the repair console.

If you do any of the automatic repairs it may delete the wubi entry & you have to manually add it again.

Use BCDEDIT.exe to modify Windows Vista boot options.
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Neuralgen on 2012-06-06
I'm sorry to keep taking your time but I don't understand your last post.

> I do not know if f8 works with Vista or not, but as soon as you boot try f8 to see if you can get into the repair console.If you boot a system and try F8 I thought you were normally given the option of what device you want to boot off of.  In any case that happens for me and I am given option of booting off primary or secondary hard drive or CD.  Only primary HD boots and it takes me direct to Ubuntu.  Vista not an option.

> Use BCDEDIT.exe to modify Windows Vista boot options.
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php...05&postcount=5]("http://ubuntuforums.org/showpost.php?p=11927905&postcount=5")

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php...32&postcount=4]("http://ubuntuforums.org/showpost.php?p=5726832&postcount=4")
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBC...r+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")Am I misunderstanding how BCDEDIT works?  From what I've read I thought you needed some version of windows running because it is a windows based program.

Now I do have my installation dvd for Vista so I could tell it to do a repair but fear that if I clobber Unbuntu boot I could find myself unable to boot into anything.  Under the repair startup option of the installation (Vista) you can choose what repairs to attempt.  Would you recommend I try any of these?

---

### Post by oldfred on 2012-06-06
The auto repairs may overwrite the BCD, but you should be able to restore that. But you may be able to use manual repairs.

The f8 is usually not a BIOS key but a Windows preboot key to get to recovery mode from the install.

If you can get to BCDedit then you may be able to see if Ubuntu is set to boot first.

---

### Post by Neuralgen on 2012-06-06
Can anyone suggest something?  I'm getting desperate to reboot into my Vista.

I have my Vista installation disk and so can use the programs available there but I'm at a loss as to what could help.  I tried the repair startup option and that seemed to have no effect.

I can boot into Ubuntu and use any programs there.  Again I don't know what would help.  I ran boot-repair and told it to carry out recommended repairs and that did not seem to have any effect.

I cannot, repeat cannot boot into my original Vista installation so presumably BCDEDIT is not an option.

I sent bootinfo summary to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] and have my fingers crossed but so far have not received any reply.

Running Wubi to see what Ubuntu looked like seemed like such a simple thing.  Ironically, everything else under Ubuntu (wireless, setting up email, wireless printer, etc.) has been almost ridiculously easy and worked immediately.

---

### Post by Neuralgen on 2012-06-06
[SIZE=2]**First new development!**[/SIZE]

Just for grins I booted up the repair disk again and told it to repair startup and this time it found a problem.  Of course it said:

Windows cannot repair this computer automatically

but now at least Vista thinks something is amiss.  I checked the repair log and the various tests all seemed successful except at the very bottom there was:

Root cause found
No OS files found on disk
Repair action: Partition table repair
Result: Failed Error code=0x490


I'm speculating that perhaps boot-repair might have contributed to this because it is the only program I've run related to booting since the last time I booted up Vista repair disk and it told me all was fine.

---

### Post by Mark Phelps on 2012-06-07
> **Neuralgen said:**
> Can anyone suggest something?  I'm getting desperate to reboot into my Vista...

I already DID that.  Go back and read my previous post.  I've used the MR WinPE CD successfully to repair Windows boot problems that the Windows DVD was unable to fix.

---

### Post by YannBuntu on 2012-06-08
Hello,
 
> **Neuralgen said:**
> Root cause found
No OS files found on disk
Repair action: Partition table repair
Result: Failed Error code=0x490

I'm speculating that perhaps boot-repair might have contributed to this

I don't think so, because Boot-Repair did not modify Windows system files, nor the partition table. These are items that may have been modified by the Windows disk.
Here is what B-R did:
- create a backup of your MBR and partition tables (they are in the ZIP that you sent me by email)
- generate a generic MBR and make it boot on sda1
- open a file browser to allow you access and backup your Wubi files
- after user confirmation that backup was done, [fsck the Wubi filesystem]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") (root.disk)


If i were you, i would try Mark's suggestion. If still not good, reinstall Windows. Then reinstall Ubuntu (outside Windows, =without Wubi).

---

### Post by Neuralgen on 2012-06-09
reply-to-Yann: I reran Vista repair disk and the error I showed above no longer appears.

I'm  still reading online documentation (Wubi MegaThread and MultiBooters per OldFred's suggestion)) trying to understand how Wubi works but have just about thrown in the towel.   Can anyone suggest where the boot "chain" is broken.  To see if  the bcd is being read I set the timeout to a large value to see if the boot would act differently but it didn't.

Does anyone know if Macrium is good about refunds?  By now it would be well worth the $45 to recover my system but I don't want to throw away the money if their tool doesn't help.  My suspicion would be that if the the people on these forums can't help it is unlikely someone else can.

---

### Post by Neuralgen on 2012-06-09
Would it be a waste of time, or more importantly foolish/dangerous, to try carrying out the steps given by [SIZE=3][COLOR=Red]Manual  Repair of the Vista Boot Loader
[/COLOR][/SIZE]of the following post?

[http://ubuntuforums.org/showpost.php?p=5726832](http://ubuntuforums.org/showpost.php?p=5726832)

---

### Post by oldfred on 2012-06-09
I would not hesitate to run those steps. 

meierfra was one of the creators of the bootinfoscript and he understands the details of systems more than most.

He is replacing the bootmgr & manually updating the BCD.

---

### Post by Neuralgen on 2012-06-10
Before I carry out meierfr's steps and replace bootmanager and bcd, I was wondering what would happen if I just used my Vista installation disk and opened a cmd.exe and then cd'ed to c:\Windows\system32 and ran winload.exe.   It seems that the booting sequence bios->mbr->[boot manager reads bcd] just ends up with windload.exe being executed.  

Would it be dangerous to do this?

If it worked I would try creating the full system image on my external  drive (which I clearly should have done before installing Wubi...) and then reboot the repair disk and try to do a restore and if that failed reinstall Vista and then try a restore.

---

### Post by Mark Phelps on 2012-06-11
> **Neuralgen said:**
> ... Does anyone know if Macrium is good about refunds?  By now it would be well worth the $45 to recover my system but I don't want to throw away the money if their tool doesn't help...

As far as I know, they have no "trial period" for the retail version you need in able to make the WinPE disk.

You could try sending an email to [email]support@macrium.com[/email] and asking them if they would refund if the WinPE disk did not work.

However, I would be surprised if they would.

---

