---
title: "Installing Ubuntu next to Windows 7"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by picassobrumm on 2013-12-28
Hello!

I have a laptop with 500gb harddrive. It was originally delivered with Windows 8, but I deleted it, formatted the harddrive, deleted all partitions and installed Windows 7 on a 250gb partition. I made two other partitions of 100gb each, one of them set aside for the thought of adding Linux to it.

I then made an Ubuntu 13.10 live CD and restarted my computer to boot from the disk. It works fine and I run Ubuntu from the Live CD. I can see all three partitions inside Ubuntu and reach and see all content on the drives, and if I use the GDisk tool I see all three partitions, but if I try to make some changes and delete a partition I get the following message:

[I]Error deleting partition /dev/sda5: Command-line `parted --script "/dev/sda" "rm 5"' exited with non-zero exit status 1: Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Partition doesn't exist.
 (udisks-error-quark, 0)[/I]

When I decide to install Ubuntu and want to keep files and install Ubuntu next to Windows all I see is 500gb drive /sda/ and no chance to do anything at all, except for destroying the entire partition. Any help on what to do?

It is important that I do not want to format or remove my Windows installation. I have downloaded fixparts, but do not really understand if that is the tool I need, and if so, what to do with it and how to use it. Thankful for all help!

---

### Post by coffeecat on 2013-12-28
Fixparts is what you need. Have you tried running it? According to the [Fixparts tutorial]("http://www.rodsbooks.com/fixparts/"), the first thing it does is to check for stray GPT data.

> The first check that the program performs is for stray GPT data. Such data can remain behind on a disk if it was previously used on a Macintosh or in some other ways, then re-used as a conventional MBR disk. Although such leftover data should not technically be a problem because the GPT specification clearly states that such disks are not GPT disks and should therefore be treated as MBR disks, some utilities can be confused by the presence of both MBR and GPT data. Thus, FixParts checks for this condition when it starts. If it finds leftover GPT data, it warns you of this fact and asks you what to do:

---

### Post by picassobrumm on 2013-12-28
I tried to run the Fixparts program in both Ubuntu and Windows. In Ubuntu I got an error message as I tried to run the Debian package (it would not let me install the program at all... is it possible to install as I run Ubuntu from the Live CD?). In Windows I can run it. I run "Command" and run Fixparts. The following text then shows up:
[I]Fixparts 0.8.0.
Type device filename, or press Enter to exit:[/I]

I then write: SDA (is that correct?) - I have also tried to write /dev/sda/

I then get the following message:
[I]Loading MBR data from /sda/
Problem loading /sda/ for reading!

Unable to read MBR data from /sda ! Exiting![/I]

This is running it in Windows. Am I typing the wrong text, or what should I do as I run the Windows application of Fixparts?

---

### Post by coffeecat on 2013-12-28
> **picassobrumm said:**
> In Ubuntu I got an error message as I tried to run the Debian package (it would not let me install the program at all... is it possible to install as I run Ubuntu from the Live CD?).

Yes, it is. Simply double-click on the deb package and it will be installed by the Software Centre. It will be installed to volatile memory, so it will be lost when you close the session down, but it will let you run it so long as the live session is running. If you are getting an error message, you need to post that so that someone can help you with it.


> **picassobrumm said:**
>  In Windows I can run it. I run "Command" and run Fixparts. The following text then shows up:
[I]Fixparts 0.8.0.
Type device filename, or press Enter to exit:[/I]

I then write: SDA (is that correct?) - I have also tried to write /dev/sda/

It is not correct. See the tutorial I linked to. The device naming convention varies according to the operating system. "sda" is for Linux only.

---

### Post by picassobrumm on 2013-12-28
Thanks a lot for your help! I tried to run FixParts in Windows again, but did not work as I wrote Fixparts 0: ... Then I noticed that I had to run the command as administrator and tried again, and at once it found the GPT mistake... I let the program fix it and that was all, and the next time I tried to install Ubuntu everything worked perfectly. Thanks a lot for the help!

---

