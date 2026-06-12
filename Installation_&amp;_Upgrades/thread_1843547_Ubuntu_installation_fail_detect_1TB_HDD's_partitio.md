---
title: "Ubuntu installation fail detect 1TB HDD's partitions"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by Roobir on 2011-09-13
Hallo everyone!

If this question has been aswered in another thread, please forgive me and please direct me to the thread. :)

To get to my situation scenario, I currently have this hard drive setup in my machine:
[IMG]http://i.imgur.com/Trh1Z.jpg[/IMG]

I want to dual boot Windows 7 and Ubuntu 11.04 x64. The 38GB partition on the 250GB hard drive is intended for Ubuntu and the rest for personal space and Windows 7 operating system.

While installing Ubuntu from the CD, it prompted me that no other operating system has been detected. I stopped the installation at this point (as I did not want GRUB to take over my current Windows MBR) and booted the live CD, just to notice that Ubuntu cannot detect my whole Western Digital 1TB drive. Could this be due to anything I have done with the partitions?

Kind regards,
N

---

### Post by YesWeCan on 2011-09-13
Hi and welcome. There are some possibilities. Has that 1TB drive ever been used in a RAID array? The Ubuntu installer will not even see a drive that has Windows RAID signatures on it, although it ought to.
Try booting the live CD and "trying without installing"
Open a terminal and run
[COLOR=DarkSlateBlue]sudo sfdisk -luS[/COLOR]
You should find that this lists all your drives and partitions and gives them names of the form sdxy. Windows drive names like C: and D: are meaningless to linux. Please post the output.
Then run
[COLOR=DarkSlateBlue]sudo dmraid -r
[COLOR=Black]and this will list any Windows RAID devices detected.
To erase the RAID signature (or super-block) on drive /dev/sdx (x=drive letter for 1TB drive)
[COLOR=DarkSlateBlue]sudo dmraid -E -r /dev/sdx[/COLOR]
[/COLOR][/COLOR][COLOR=Black]

[/COLOR]

---

### Post by srs5694 on 2011-09-13
YesWeCan's suggestions are proper; however, instead of (or in addition to) "sfdisk -luS", I recommend:

```

sudo fdisk -lu

```

This has the advantage of providing the disk size in a more precise form, which can be important in properly diagnosing at least one possible cause of the symptoms you describe.

My [FixParts](http://www.rodsbooks.com/fixparts/) program can correct many of the partition table irregularities that can cause these symptoms. It won't do any good for RAID-related causes, though.

---

### Post by Roobir on 2011-09-14
Thank you for the replies gents!

Please find the pasted pictures of the various commands below this post. With the information I have given you, should I attempt sudo dmraid -E -r /dev/sdx ? Also, what will the command do to my partition on the hard drive? I hope I do not lose any data. Although backing up is an option at the moment.

sfdisk picture:
[img]http://i.imgur.com/PROSf.png[/img]

dmraid picture:
[img]http://i.imgur.com/tZG9P.png[/img]

fdisk picture:
[img]http://i.imgur.com/J65wD.png[/img]

Kind regards,
N

---

### Post by Roobir on 2011-09-14
Sorry for the unusual large pictures added. I did not think twice before adding the pictures this morning before I went to the office.
 
I think it is perhaps important to add that the 1TB drive I am using, is newly purchased (like 2 weeks ago) and only partitioned using the Windows 7 installation DVD. Could AHCI perhaps make the partitions look like some form of raid?
 
Kind regards,
N

---

### Post by YesWeCan on 2011-09-14
The dmraid -r shows that sda has raid signatures on it. That's your problem.

[COLOR=DarkSlateBlue]sudo dmraid -E -r /dev/sda[/COLOR]

to erase them

---

### Post by YesWeCan on 2011-09-14
> **srs5694 said:**
> This has the advantage of providing the disk size in a more precise form, which can be important in properly diagnosing at least one possible cause of the symptoms you describe.
Please elaborate.

---

### Post by srs5694 on 2011-09-14
(re: "fdisk -lu" being superior to "sfdisk -luS" for diagnosing some problems that can produce the OP's symptoms.)

> **YesWeCan said:**
> [quote=srs5694]This has the advantage of providing the disk size in a more precise form, which can be important in properly diagnosing at least one possible cause of the symptoms you describe.Please elaborate.[/QUOTE]

Consider Roobir's output for /dev/sda. This indicates that the /dev/sda3 partition ends on sector 1,953,521,663. Both "fdisk -lu" and "sfdisk -luS" provide this information. By itself, though, this information doesn't tell you if that partition is sized properly for the disk. For that, we need the disk size. The sfdisk output provides this via a cylinder/head/sector triplet -- 121601/255/63 in this example. Multiplying those three numbers, you get a disk size of 1,953,520,065 -- that is, smaller than the /dev/sda3 partition! If you'd done this check and didn't realize its limitations, alarm bells would be ringing and you might go to a lot of needless effort to correct this "problem."

Unfortunately, the CHS values provided by sfdisk are only ROUGHLY correct. The issue is that modern disks seldom have an integral number of cylinders; they're laid out using a more complex geometry than the antiquated CHS values permit, so there are usually sectors available for use after the final whole cylinder. You can learn the precise size of the disk -- and without having to do multiplication manually -- by using fdisk instead of sfdisk. Roobir's fdisk output reveals the true size of the disk to be 1,953,528,168 sectors -- significantly larger than the end point of the final partition. Thus, there is no problem with that partition's size.

Of course, if you're aware of this limitation, you could try adding 1 to the number of cylinders, and you'd find that the end point for /dev/sda3 would be less than this value -- but then, so is the true number of sectors on the disk. This test could therefore lead to a false sense that everything's OK.

Furthermore, the presence of the total disk size in the fdisk output facilitates this important comparison -- you can easily find the final partition and compare its end point to the disk size. With sfdisk, you've got to do the math first, which adds to the effort and increases the risk of human error causing a misdiagnosis.

All of this is important because there are tools that are known to produce partitions that are too big for the disk. TestDisk sometimes (but not always) does this with the extended partition it creates to encompass logical partitions. When parted encounters such disks, it reports them as being empty. Thus, to diagnose this problem, *precise* information on disk size is required, and "sfdisk -luS" just doesn't provide that information. Both commands do provide other useful diagnostic information -- they can both help you spot overlapping partitions, for instance. sfdisk shows empty partitions, which could conceivably be useful if stray data in such a partition table entry was causing problems -- but I have yet to hear of such a problem in the real world. Thus, "fdisk -lu" provides better diagnostic information for this problem than does "sfdisk -luS".

---

### Post by YesWeCan on 2011-09-14
In summary, fdisk -lu shows the total number of disk sectors and sfdisk -luS does not.

I knew that.

I would still use sfdisk -luS for these symptoms.

---

### Post by Roobir on 2011-09-14
> **YesWeCan said:**
> The dmraid -r shows that sda has raid signatures on it. That's your problem.

[COLOR=DarkSlateBlue]sudo dmraid -E -r /dev/sda[/COLOR]

to erase them

Will I lose any of the data on that drive by using the command?

Thank you both for the responses!

Kind regards,
N

---

### Post by YesWeCan on 2011-09-14
> **Roobir said:**
> Will I lose any of the data on that drive by using the command?
Not unless you are running a Windows RAID array that you haven't mentioned with a disk that is not connected to your system. So no. :)

---

### Post by srs5694 on 2011-09-14
> **YesWeCan said:**
> In summary, fdisk -lu shows the total number of disk sectors and sfdisk -luS does not.

I knew that.

I would still use sfdisk -luS for these symptoms.

Why? What information does "sfdisk -luS" provide that you believe is so critical?

---

### Post by Roobir on 2011-09-14
> **YesWeCan said:**
> Not unless you are running a Windows RAID array that you haven't mentioned with a disk that is not connected to your system. So no. :)

I see! Also, do you have any idea how this raid signatures planted itself on my drive? Could it perhaps be Windows installation yanking me around? :D

---

### Post by srs5694 on 2011-09-14
> **Roobir said:**
> I see! Also, do you have any idea how this raid signatures planted itself on my drive? Could it perhaps be Windows installation yanking me around? :D

This can happen automatically because of BIOS settings. To prevent a recurrence, you might want to check your BIOS settings and disable any options that refer to RAID. Details vary a bit from one BIOS to another, though, so I can't be more specific.

---

### Post by YesWeCan on 2011-09-16
> **srs5694 said:**
> Why? What information does "sfdisk -luS" provide that you believe is so critical?

> While installing Ubuntu from the CD, it prompted me that no other  operating system has been detected. I stopped the installation at this  point (as I did not want GRUB to take over my current Windows MBR) and  booted the live CD, just to notice that Ubuntu cannot detect my whole  Western Digital 1TB drive. Could this be due to anything I have done  with the partitions?In my experience it is rare for a last primary partition to exceed the disk size. There is no evidence of this from the Windows Disk Manager. Sometimes an extended partition end sector is wrong but there is no extended partition here and sfdisk would show this anyway. However, I have seen fdisk fail to detect GPT more than once but never sfdisk and the linux tools don't handle GPT header + MBR PT intelligently. So on balance I choose to use sfdisk as the first step as it would reveal more probable issues first. It's no big deal because fdisk -lu can always be used afterwards if the total sector size seems more likely to be an issue. And in this case the total sector size is not the problem.

---

### Post by srs5694 on 2011-09-16
> **YesWeCan said:**
> In my experience it is rare for a last primary partition to exceed the disk size.

Overall, yes, but when the disk is exhibiting the problems reported here, it's a common cause, at least judging by the reports I've seen here on this forum. (For instance, [here](http://ubuntuforums.org/showthread.php?t=1793735) or [here,](http://ubuntuforums.org/showthread.php?t=1771873) although these are hardly the only two -- just the first two I found in a quick search.) TestDisk is a common cause of this problem; under certain circumstances, it produces an overly-large extended partition.

> There is no evidence of this from the Windows Disk Manager. Sometimes an extended partition end sector is wrong but there is no extended partition here and sfdisk would show this anyway.

Windows' Disk Manager is notoriously unreliable. It frequently reports logical partitions as being primary, among many other flaws. Although that wasn't the case here, there was no way of knowing that -- at least, as far as I know.

> However, I have seen fdisk fail to detect GPT more than once but never sfdisk

I've never before heard of that, and I'm frankly a bit skeptical, because the code in both fdisk and sfdisk for GPT detection is nearly identical, and relies on an identical function in a file that's compiled into both programs' final binaries. That said, it's conceivable that some bug in fdisk is causing the GPT-detection code to not be called in some cases; I haven't tried to trace the execution path in enough detail to rule out that possibility.

Can you reproduce a case in which fdisk failed to detect the GPT header but sfdisk detected it? Did you actually test with sfdisk on the specific disks on which fdisk failed to detect the GPT header?

> and the linux tools don't handle GPT header + MBR PT intelligently.

This is imprecise, but it's certainly true of libparted. (I'm not a fan of libparted, but the popular GUI tools in Linux are all based on it.) Both fdisk and sfdisk are "Linux tools," and neither is based on libparted -- but with a caveat: There is a rarely-installed "GNU fdisk," which is libparted-based. Generally the version of fdisk that's used on Linux boxes is installed from the util-linux package and is not based on libparted. In fact, as just noted, fdisk and sfdisk share some code.

> So on balance I choose to use sfdisk as the first step as it would reveal more probable issues first. It's no big deal because fdisk -lu can always be used afterwards if the total sector size seems more likely to be an issue. And in this case the total sector size is not the problem.

In my experience a mis-sized (too big for the disk) extended partition is a very common cause of this type of problem, and I've never seen the util-linux fdisk fail to detect GPT data, so in my experience fdisk is the superior tool for this diagnostic task. Of course, you're right that other tools can always be run for further diagnostics, whatever the initial choice, and in this case (that is, Roobir's problem in this thread), the cause was stray RAID data, which neither fdisk nor sfdisk detects. If fdisk is less reliable than sfdisk in detecting stray GPT data, though, then that's certainly an important issue.

---

### Post by oldfred on 2011-09-16
To settle one part of discussion, I did find why my fdisk did not show gpt partition. Somewhere in the past someone recommended gnu-fdisk and since I add all the old packages in my new installs, I still had it. I uninstalled gnu-fdisk and fdisk then does show gpt warning info.

For whatever reason boot-script always used the correct fdisk or had extra logic to know my sdb is gpt. So I tend to rely on boot script. Sometimes it is too much data, but many times users really do not understand their system and boot script resolves all the issues. I just wish it also included UEFI/efi partition info.

---

### Post by YesWeCan on 2011-09-16
> **srs5694 said:**
> Can you reproduce a case in which fdisk failed to detect the GPT header but sfdisk detected it? Did you actually test with sfdisk on the specific disks on which fdisk failed to detect the GPT header?
I don't want to spend too much time debating this because I don't think it really matters. But we were both in a thread some weeks ago where this very thing occurred and it took a couple of pages of going in circles after the initial fdisk output to discover that GPT was the culprit. I can't recall immediately which thread it was. I think you made some comment about what the version number was of the fdisk or something. Anyhow, seeing as how it is possible for some versions of fdisk to miss this I like to use sfdisk. But I am not against fdisk per se and I often ask for fdisk -lu output instead depending on the situation as I see it.

---

### Post by srs5694 on 2011-09-16
> **YesWeCan said:**
> I don't want to spend too much time debating this because I don't think it really matters. But we were both in a thread some weeks ago where this very thing occurred and it took a couple of pages of going in circles after the initial fdisk output to discover that GPT was the culprit. I can't recall immediately which thread it was. I think you made some comment about what the version number was of the fdisk or something. Anyhow, seeing as how it is possible for some versions of fdisk to miss this I like to use sfdisk. But I am not against fdisk per se and I often ask for fdisk -lu output instead depending on the situation as I see it.

Fair enough. I suspect you're referring to a thread in which GNU fdisk was in play, as oldfred suggests, although I also vaguely recall a thread in which a very old installation was in use, so its was different enough from modern versions to be important. I don't recall if that involved leftover GPT data, though.

In my experience, GNU fdisk is very rarely installed, so it's seldom an issue; whereas a too-big extended partition is a recurring problem in threads that begin like this one, with a libparted-based tool showing no partitions whatsoever. Therefore, I favor fdisk for diagnosis, although I can respect sfdisk to avoid the possibility of using GNU fdisk and therefore missing leftover GPT data. Oldfred's suggestion of using Boot Info Script probably beats both for reliability, although it has the practical drawback of requiring a download, and people sometimes end up posting the script itself or its console output rather than the RESULTS.txt file. I guess no option is 100% perfect.

---

