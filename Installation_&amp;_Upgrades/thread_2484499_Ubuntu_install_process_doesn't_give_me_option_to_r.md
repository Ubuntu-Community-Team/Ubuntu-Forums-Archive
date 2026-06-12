---
title: "Ubuntu install process doesn't give me option to remove windows partitions"
date: 2023-02-28
forum: Installation &amp; Upgrades
---

### Post by coolpontiac on 2023-02-28
I just upgraded my old. HP dm1z to latest version of lubuntu "lubuntu-22.04.1-desktop-amd64.iso"

during the install process I was ONLY  giving the "replace" partion option" and custom portion option
I wanted to remove all the old windows files...  
I was afraid to do custom partition 

so now I see 2 partitions (or folders?) with windows stuff still on my disk.   do I need to redo install or can I free up that space of these windows folders?

---

### Post by SeijiSensei on 2023-02-28
If you want to blow away everything Windows-related during installation, choose the "use entire disk" option from the disk management page. Ubuntu will then create a single partition, format it as ext4, and install everything to that. 

You can merge the two remaining Windows partitions into one and create a single ext4 partition using Ubuntu's native disk management tools. You'd then have to create a "mount point" (essentially an empty directory) in the filesystem tree. You could create it under /media, e.g., /media/data, or somewhere else like /data. Personally I'd just reinstall with the "use entire disk" option.

---

### Post by coolpontiac on 2023-02-28
thanks but that is what I was trying to say.. the install program didnt give me a 'use entire disk' option.
  UPDATE... I followed your advice and remade the iso usb and reinstalled and now I am getting the option to erase entire disk so that it can all be used by Lubuntu

Thanks!

---

### Post by guiverc on 2023-02-28
The *latest* release of Lubuntu is the 2022-October release.

The *last* release we had was Lubuntu 22.04.2 LTS, but it was just a re-spin (*with upgraded packages & the HWE kernel stack*) but of the earlier releases 2022-April release.  It is the LTS option, and not the latest STABLE release.

The manual for Lubuntu 22.04 LTS can be found here - [https://manual.lubuntu.me/lts/1/Installing_lubuntu.html](https://manual.lubuntu.me/lts/1/Installing_lubuntu.html)

If a partition is marked as UNCLEAN (*eg. contains a system on it such of windows, but file-system is unclean due to fastboor, hibernate etc being used on it*), that space can be IGNORED by the installer as the* UNCLEAN flag *is treated as a warning; your own setup may not be default with data spread across multiple partitions etc.  The Erase Disk option I would expect to show though (*but I've encountered times where it won't show either; alas I forget the reasons for that*).

If you can't get `calamares` (the installer used by Lubuntu) to do what you want, I'd suggest just restarting your *live* session (ie. reboot) & use [KDE Partition Manager]("https://manual.lubuntu.me/lts/3/3.1/3.1.6/kde_partitionmanager.html") to delete partitions you don't want, create what you do want, then when you have what you need, exit the KDE Partition Manager, and then start the `calamares` installer... this time just selecting the partitions you've created (*no need to format as you'll have done that I bet already*).

The reboot I mention is mostly optional, but the reason I state it is I've encountered cases where `calamares` has left '*data in the stack*' that can throw itself or KDE Partition Manager *'a little off*'  which result in a confusing error. It only happens rarely (*but could if you're exploring around looking for an option, trying different things, there is a higher chance of this occurring thus my suggestion to reboot*).  The installer provided with 22.04.1 & 22.04.2 is improved over what we released with the initial 22.04 media (*alas not as good as on the later 22.10* *release*).

---

### Post by ne29914 on 2023-02-28
Just select "Manual partitioning" and take it from there. As you're doing a new install and want to get rid of old Windows stuff, it's no big deal.
Click "New partition table" and start adding your partitions.
Add the first partition with size 30000 (MB), file system ext4, select format, mount point /, boot.
Then add whatever other partitions you need (eg, /home).
Nothing dangerous about it. But back up your data first, of course.

---

### Post by SeijiSensei on 2023-03-01
I just booted up a virtual machine under KVM and installed Lubuntu 22.04.2 to it. (22.04.1 was not available.) By default it came up with a desktop with an icon to "Install Lubuntu 22.04 LTS". I clicked on that icon to run the installer, and when I got to the Partitions screen, there is an "Erase disk" option. If you choose that, your Windows partitions will disappear.

---

### Post by ne29914 on 2023-03-01
> **SeijiSensei said:**
> and when I got to the Partitions screen, there is an "Erase disk" option.
I just did the same, and somehow this "Erase disk" option is very elusive. I'm not able to find it anywhere. Please show us where you found it. It's certainly not there on the standard install (and not on 20.04 either).

---

### Post by BBQdave on 2023-03-01
> **ne29914 said:**
> ...this "Erase disk" option is very elusive.

The Ubuntu (and various flavors) goes thru selecting language keyboard language and layout and area zone. Then you have a choice of how to install: along side another distro (usually names the distro) or install Ubuntu (something like entire disk) or manually partitioning. After you select install Ubuntu (to disk or to entire disk - something) you will get a warning: Warning - this will erase all partitions, files, data and so on.

That warning should indicate you are about to blow away everything on the drive.

---

### Post by MAFoElffen on 2023-03-02
A picture says a thousand words... I spun up one of my ISO Tester VM's and took a screenshot for you. That should be a good visual aid to what is being discussed.

---

### Post by yancek on 2023-03-02
If you no longer want the windows partitions, another option is to use the Try Lubuntu selection and open the partition manager and simply format the windows partitions.  If you are using UEFI, be sure to NOT format the EFI/vfat partition.

---

### Post by ne29914 on 2023-03-02
> **BBQdave said:**
> The Ubuntu (and various flavors) goes thru selecting language keyboard language and layout and area zone. Then you have a choice of how to install: along side another distro (usually names the distro) or install Ubuntu (something like entire disk) or manually partitioning.
No. Lubuntu uses the Calamares installer which has different options compared to the other flavours.
There is no "Erase disk" option.

---

### Post by ne29914 on 2023-03-02
> **yancek said:**
> If you no longer want the windows partitions, another option is to use the Try Lubuntu selection and open the partition manager and simply format the windows partitions.
The Calamares installer option is "Start Lubuntu".
It seems a lot of people are answering a Ubuntu question, when the issue is about Lubuntu. There are differences.

---

### Post by MAFoElffen on 2023-03-02
@ne29914 --
Did you not look at the attachment? Yes, it has different Options, but... The attachment of Post #9 is the Lubuntu 22.04 LTS Calamares installer with an "Erase Disk" option... You see that there right?

I believe guiverc 
[quote=guiverc]
The Erase Disk option I would expect to show though (*but I've encountered times where it won't show either; alas I forget the reasons for that*).
[/quote]
...in that sometimes, depending on the hardware, there may be different options presented in that installer.

---

### Post by guiverc on 2023-03-02
> **MAFoElffen said:**
> @ne29914 --
I believe guiverc 

...in that sometimes, depending on the hardware, there may be different options presented in that installer.

I can't recall any issues like that recently, and all issues where options were not shown were *somewhat* quickly able to be worked out and I ruled out as being *operator error* (*ie. a used swap, unclean file-system where by the installer treated part of the disk as in-use & refused to let you install to all of disk*). In many cases it was after using the *live* session rather than starting the installer before mounting anything (*either purposely or as consequence of user action*).

The Lubuntu QA testing checklist still has 22.04.2 details on it - [https://phab.lubuntu.me/w/release-team/testing-checklist/](https://phab.lubuntu.me/w/release-team/testing-checklist/) but only lists the *last* of each type. I performed maybe 5 *alongside* windows 10/11 during February & may have seen it there, but if I did I'd have just booted windows & disabled fastboot etc then re-started the *live* media and installed then (*ignored as operator error*). 

I have no details of what was on the disk before hand, though my prior reply listed my thoughts anyway.

I mentioned the restarting of the *live* session, it's documented [here]("https://discourse.lubuntu.me/t/calamares-rare-failure-to-create-partition-mkfs-errors/2774") too and elsewhere, but your description didn't sound like you got far enough for that to be an issue, your issue maybe you opening `pcmanfm-qt` to explore your disk, `KDE Partition Manager` likewise and forgetting to `umount` the partition(s) that were mounted as consequence of your exploration... but I'm only guessing here based on issues I quickly recognized as '*operator (me) error*' & thus ignored.

---

### Post by ne29914 on 2023-03-02
Interesting...
I just did a live boot and running the installer. Image is a Lubuntu 22.04.2 .ISO downloaded yesterday.
As I don't run LVMs, the picture is not as nice as yours:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291853&stc=1[/IMG]

---

