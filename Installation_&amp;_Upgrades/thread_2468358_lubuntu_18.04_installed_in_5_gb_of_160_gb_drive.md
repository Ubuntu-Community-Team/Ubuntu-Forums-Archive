---
title: "lubuntu 18.04 installed in 5 gb of 160 gb drive"
date: 2021-10-26
forum: Installation &amp; Upgrades
---

### Post by indianajo on 2021-10-26
lubuntu 18.04 installed in only 5 gb of 160 gb drive. Partition 5  I told it to use whole disk. It left insecure lubuntu 14.04 in partition 1 consuming 155 gb.
Tried to do a unix sudo wipe dev sda command.  Downloaded ubuntu 8.04.4 which will run from cdrom.  Did so.  activated terminal . There is no wipe command listed in help.   Platform is intel dual core 2.73 ghz 2 mb ram.  lubuntu14 got where it wouldn't talk to internet anymore, every site was insecure. 
Is there a downloadable unix with wipe or scrub command that will run from cdrom?

---

### Post by grahammechanical on 2021-10-26
First of all you should not be installing Lubuntu 18.04 as it reached end of life 30 April 2021. Download and install Lubuntu 20.04

[https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

Second, did you really tick Erase disk and install Lubuntu? That should have worked.

Third, If you are able to run the Lubuntu installer then try running the Lubuntu Live/Try session and load the GParted utility. That utility will let you delete partitions and create partitions and format them. GParted will also let you create a new partition table and that will effectively "wipe," as you call it, the whole disk.

Your present partition table might be Master Boot Record (MBR). The MBR partition table will let you have four primary partitions and no more. To have more than four partitions we have to use one of the allocated primary partitions as an Extended partition into which we can create additional Logical partitions.

With GParted you can choose GUID Partition Table (GPT). That lets us have any number of partitions. GPT is modern and more flexible than MBR partition table. And it is backwards compatible with motherboards that have a BIOS settings utility and not a UEFI settings utility.

[https://gparted.org/display-doc.php?name=help-manual](https://gparted.org/display-doc.php?name=help-manual)

I have a Core2 DUO CPU. It is not as fast as your one but I do have a little more RAM and the motherboard works with both MBR and GPT hard disks. I have one of each.

Regards

---

### Post by GhX6GZMB on 2021-10-26
I'm not certain I understand what you are doing. Do you have several partitioons with different old Lubuntu versions?

More important, what do you want to achieve? A machine just running Lubuntu 20.04? (older versions make very little sense).

---

### Post by guiverc on 2021-10-26
Lubuntu 18.04 LTS media would run in *live* mode; all except the not-updated *alternate* ISO which was built for hardware with 700MB of RAM or less and thus couldn't run a *live* system of installation media & run the installation program `ubiquity`.

(*If you have only 2MB of ram as you state; nothing will run; but I'm betting that was a typo and you intended 2GB.  I tested releases up to Lubuntu 19.04 on boxes with 1GB of RAM, and the minimum since then has been 2GB up to and including impish or 21.10*)

Some of your details do not make sense - Lubuntu discourages use of the *alternate* media (*it's outdated & won't run on modern equipment anyway as without many fixes*) but it's intention was really old hardware where its all that works (*with very limited RAM*) thus later uEFI/SHIM fixes don't matter.

My guess from what you provided, and mention of releases, is that you're not going to legitimate sites & basing details off 3rd party or non-official sites. Be careful.

---

### Post by GhX6GZMB on 2021-10-26
What guiverc said. The correct site for Lubuntu is [www.lubuntu.me](www.lubuntu.me)

---

### Post by indianajo on 2021-10-26
Downloaded lubuntu 18.04 I386 iso from lubuntu.org which bounced to lubuntu.net 
 main download button of that downloaded 18.04 I386 but managed using "old dist" icon to download lubuntu 20.04.3 to dvd
Have that loaded on DVD running right now from dvd. lubuntu control screen came up.  Trying to use whole disk, 160 gb, for ubuntu20.  got kde partition manager up, there is a /dev/sd1 of 143 gb and a /dev/sd2 of 5.5 gb.  sd5 dangles off sd2.  apparently lubuntu 18.04 went into sd5.  too small.  tried to resize sd1 to zero, didn't work.  tried to delete sd1 didn't work went "pending".   undid that.  No terminal facility to use unix commands like gpartu 
previously got a bsd unix download from perdue, CD70,  onto cd.  was no sudo command.  tried to run "dd if=/dev/zero of=/dev/sda bs=16m" best result was "no space left on device"  ???? want to erase hard disk so lubuntunew will use the whole disk. Lubuntu14 is of no use anymore, half the internet is "insecure and cannot connect"  All my old data is on 9 dvd's to be loaded after op system install.

---

### Post by guiverc on 2021-10-27
Lubuntu[.net] is **NOT** a Lubuntu or Ubuntu affiliated web site; so did you verify your download was correct?

If you're unsure of where to go, don't ask google - it'll offer up official Lubuntu web site, plus *fan* sites & *fake* sites; so you need to check out which is correct before you know you can trust it.

If you go to ubuntu.com & search for *flavors*/*flavours* you'll end up at [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will take you to the official web sites for Ubuntu affiliated sites; ie. [https://lubuntu.me/](https://lubuntu.me/) for Lubuntu; after all it's a Canonical/Ubuntu controlled web site; with control handed over to the Lubuntu team.

Did you verify what you downloaded as being correct from a Ubuntu web site (*esp. given you didn't start at a Lubuntu controlled site*). Your not using a Lubuntu site does explain why you've basing detail on *outdated* or *incorrect *information; but I'd ensure your system is legitimate.

FYI:  This is an Official Ubuntu web site; you can click on the **Ubuntu Community **tab  on the top of the page, and you'll go to the official site for Lubuntu;  where you'll notice it's not where you said you went.

---

### Post by yancek on 2021-10-27
Read through post 7 and follow the instructions so that you get the correct iso download.  Do an md5 checksum on the downloaded iso file.  The purpose of this is to verify that there were no problems in the download process between the server and your computer.  There is nothing wrong with the iso on the server site for Lubuntu but all kinds of things can go wrong during the download process.

Is your computer that old that you need the i386 iso?

>   there is a /dev/sd1 of 143 gb and a /dev/sd2 of 5.5 gb.  sd5 dangles off sd2.   

It would actually be sdd1, sdd2 and sdd5.  2 letter d's.  That tells us that sdd1 is a primary partition of 143GB, sdd2 is an Extended partition which can not hold data.  sdd5 is a logical partition which can contain data and is inside the Extended partition of sdd2.  This indicates that you have a Legacy/msdos partitioned drive on which you can have only 3 primary partitions which will be sdd1-sdd4.  Any partition sda5 and higher is a logical partition contained within an Extended partition which in your case is sdd2  

>  tried to resize sd1 to zero, didn't work.

How did you try to resize it?  Use GParted which is on the Lubuntu iso/DVD?  "didn't work" isn't information that is going to help anyome to help you.  What exactly are your intentions here?  You indicate that you have an old (14.04) version of Lubuntu installed.  Do you want to install the new (20.04) Lubuntu on that drive, overwriting everything currently there?  The simplest way to do this is to boot your Lubuntu DVD and select the Install Lubuntu option and take care to select the correct drive (sdd) to install to which would indicate that you have several other drives attached.  There is no need to resize and partitions as if you select the correct drive to install to, this will be done by the installer.  You can manually unmount and delete the logical, Extended and primary partitions but there is no need to do that.

You can use gparted (typo "gpartu" in your post) from the booted Lubuntu by simply holding down the Ctrl+A;t+t keys simultaneously but there is really no need to do this.

I'm not sure what you were trying to accomplish with the dd command you posted above?i

---

### Post by indianajo on 2021-10-27
With dd command, wipe command, hdsomething command was trying to fill 160 gb hard disk with zeros to erase multiple partitions and obsolete op systems.  Is a hardware erase on pata drives accessible from unix hdsomething command but wikipedia wouldn't tell me how to do it.  
Ubuntu20.04.3 had verified its checksum after boot from dvd.  Control screen allowed no option to install on whole disk.  Gave up waiting after an hour and pressed install option where it did give me the option of installing lubuntu20.04.3 in the 145 gb partition where lubuntu14 was.  This is not ideal, but acceptable. Lubuntu18.04  is still on 5 gb partition sdd5 and I can't get rid of it.  grub comes up at every boot and gives me the option of choosing lubuntu18.04 i386 if I want it. I don't
The only downloadable op system on lubuntu.org on hot buttons was lubuntu18.04 I386. The amd64 was not on server. lubuntu19 was not on server.   I don't have an amd processor,I have an intel dual core 2.73 ghz processor, so it is not obvious that amd64 is a version I could use.  I got the url lubuntu.org from en.wikipedia when I abandoned windows2000 and have been using lubuntu.org for downloads since lubuntu8.04 twelve? years ago .  ubuntu community needs to get control of standard urls like org & net as lubuntu.me is non-obvious and arcane. The first time I heard of it was 10/26/21.   We are in agreement lubuntu.org/lubuntu.net website is badly updated & managed.  
Thanks for answers, signing off.

---

### Post by yancek on 2021-10-27
The fact that an iso shows as AMD does not mean that you need to use an AMD processor, Intel processors run it too, just do the research.

The various Ubuntu derivatives have several options to install including Erase Disk and install Ubuntu/Lubuntu.  You should see this if you select Install Ubuntu after booting or Try Ubuntu after booting then selecting Install Ubuntu.  If you don't want anything else on that drive, that is the option to select verifying that you have the correct drive.

Another option is to boot Ubuntu with the Try Ubuntu option and open a terminal from the Desktop by simultaneously holding down the Ctrl+Alt+t keys.  Then type in sudo gparted and when the gparted window open, click the Device tab at the top of the window and click on Create Partition table.  You will have 2 options, msdo or gpt.  Select one.  This will destroy all data on the drive and you will get a warning telling you that so make sure you have the correct drive.  At this point, exit gparted and terminal window and click on the Install Ubuntu ico and proceed.

If you had 18.04 installed on sdd5 and installed 20.04 on sdd1, you did not allow the default install for the Grub bootloader because that will always be to the device (sdd) not the partition (sdd1) which is why you are still having it boot to 18.04.

The correct site to download your Lubuntu from is shown in post 7.  You are still referring to incorrect sites in your last post.  Wikepedia is not the site you want to use for something like this, use the links suggested in post 7. 

>   ubuntu community needs to get control of standard urls like org &  net as lubuntu.me is non-obvious and arcane. The first time I heard of  it was 10/26/21.   We are in agreement lubuntu.org/lubuntu.net website  is badly updated & managed.
 
  
The Ubuntu community is not in charge of the entire internet and is not in charge of the 2 sites you reference above.   Looking for official documentation for software is usually a good first step.  I use Wikepedia and don't mean to criticize it but there is no realy verification to it as you will often see when the people running the site suggest that more verifiable information is needed.  It's a little like Youtube (not as bad) in that anyone can post anything, acuurate or not, particularly on Youtube.

>   I got the url lubuntu.org from en.wikipedia when I abandoned  windows2000 and have been using lubuntu.org for downloads since  lubuntu8.04 twelve? years ago .  

I don't douobt that, it's what is commonly referred to as good luck.

---

### Post by grahammechanical on 2021-10-27
> Tried to do a unix sudo wipe dev sda command.  Downloaded ubuntu 8.04.4  which will run from cdrom.  Did so.  activated terminal . There is no  wipe command listed in help

Nor is there an entry for wipe in the man pages. You have to install wipe in order to use it and to get a man page information about wipe.

[https://linuxhint.com/completely_wipe_hard_drive_ubuntu/](https://linuxhint.com/completely_wipe_hard_drive_ubuntu/)

> The author, the maintainers or the contributors of this package can NOT be held responsible in any way if **wipe**  destroys something you didn't want it to destroy. Let's make this very clear. I want you to assume that this  is a nasty program that will wipe out parts of your files that you  didn't want it to wipe. So whatever happens after you launch **wipe** is your entire responsibility. In particular, no one guarantees that **wipe** will conform to the specifications given in this manual page. 

[https://linux.die.net/man/1/wipe](https://linux.die.net/man/1/wipe)

Likewise, don't blame me for giving you these links.

Regards

---

### Post by GhX6GZMB on 2021-10-27
If you're just trying to set up a Lubuntu 20.04.3 LTS machine, you're making it difficult for yourself.
The installer will do all the necessary things for you. There's absolutely no need to preformat the HDD/SSD, there's no need to use gparted first for partitions, etc.

Just boot into the installation media and take it from there (this is normally the most diffult part: getting the BIOS/EUFI settings right).

When you get to partitioning, select manual partitioning. Then you can set up and format everything as you like.

---

### Post by MAFoElffen on 2021-10-27
About Versions of and why NOT 20.04.x: 

Unless... Your machine was only capable of, because of it only being 32bit, which then your ONLY option of going on in any Ubuntu Flavor was Lubuntu 18.04 LTS and dead-ends there at that version...

---

### Post by yancek on 2021-10-28
>  If you're just trying to set up a Lubuntu 20.04.3 LTS machine, you're making it difficult for yourself.  The installer will do all the necessary things for you. There's  absolutely no need to preformat the HDD/SSD, there's no need to use  gparted first for partitions, etc.

Yes, correct as was pointed out in the first response to the original question by another member shown below

> Second, did you really tick Erase disk and install Lubuntu? That should have worked. 

Reading through the posts by the OP, there are so many things wrong in the posts I am amazed s/he ever got any Ubuntu installed.

---

