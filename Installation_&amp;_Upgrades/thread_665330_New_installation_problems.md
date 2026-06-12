---
title: "New installation problems"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Xolo on 2008-01-12
Hello all,

It seems that I am having problems with a new Ubuntu installation.

I have received my CD through the mail, version 6.06 LTS. I am able to boot to the live CD session. I start the installation process and make it to step 5/6 partitioning of the HDD. It starts looking for the available HDD's and just hangs indefinitely without being able to find anything. I then have to cancel the installation process.

Here's my system specs (if this could help);

Asus P3V4X MoBo
2 Gig Ram
eGeforce video card
LSI Logic MegaRAID SATA 150-6 w/
6 x 500 Meg HDD's

I have already loaded the LSI config utility and created a RAID 5 partition of all 6 HDD's (it actually creates 2 partitions automatically) and initialized them both. But for some reason Ubuntu can't see the drives at all.

I have tried going;
System > Administration > Gnome Partition Editor
on the live CD, but it can't see any drives either.

I have been able to install Ubuntu on this PC previously, but not with the LSI MegaRAID card installed. I was using an IDE HDD on the primary set as Master. The only IDE drive I have on it now is the optical drive that's allowing me to load the live CD.

Does anyone have any suggestions or help that may get me past this point? This is a fresh installation on brand new HDD's, so I have no fear of loosing any information at all. This will hopefully be able to act as an NAS file server once I can get the OS loaded.

Please add COMPLETE step-by-step instructions for me to follow as I am a complete noob too. Any missing switch (/ or \) or space that I will need to type at the terminal window will not allow me to get any further, so please, take your time in responding.

Links to multiple different web sites that require me to read for 6-8 hours to find a single nugget of information isn't the type of help I am looking for. That just makes a person want to give up and use MS products.....I would prefer to try to learn Ubuntu and Linux instead.

Every search that I have done for a solution has only lead me to links where people have such poor grammar that trying to understand what they are saying is too much of a challenge. Hence my posting here.

Thanks in advance for any help.

====================================================

Well, I have been searching through the forums for a while and have come across this post;
[http://ubuntuforums.org/showthread.php?t=447894&highlight=LSI](http://ubuntuforums.org/showthread.php?t=447894&highlight=LSI)
At the last post on that page it suggests using 7.04 to install. So right now I am downloading the iso. I'll give it a try one I have it burnt. I'll try to keep you all up-to-date with my findings.

Cheers.

---

### Post by Partyboi2 on 2008-01-12
I am not sure if this will help
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by Xolo on 2008-01-14
Party,

That suggestion isn't working for some reason. I can not get a connection to the internet either, so getting the mdraid isn't possible.....unless there's a way that I can put it onto a flash stick or maybe a floppy and I can run it that way. But like I said in my post, I'm a total NOOB, so I would have no idea how to transfer the file, or run it to allow it to enable the RAID.

Any step-by-step help would be appreciated.

Thanks

---

### Post by Partyboi2 on 2008-01-14
If you have access to another pc with internet you can download the dmraid package from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=dmraid&searchon=names&subword=1&version=all&release=all") and stick it on a usb stick or floppy and boot the ubuntu live cd and  copy the package over to the live cd Desktop and then to install, double click on the package  and the deb installer will open. Then under > "package" you will see > "status" If it says > "All dependencies satisfied" then click on > "Install Package" and it will install the package.
If > "status" says something like > "requires the installation of (number of packages)" click on > "details" and install those packages by going [here]("http://packages.ubuntu.com/")  and doing a search for them and downloading them and installing them the same way. Then continue with the instructions. Unless of course you have find another option :)

---

### Post by Xolo on 2008-01-14
Ok,

I've gotten to the end of your procedure. I have jumped back to the other procedure;

System->Administration->Gnome Partition Editor

but the RAID array does not show still. Is there anything else that I may need to get this up and running? It's funny, the flash stick shows in the drop down list on the top right hand side of the gParted window.....not the RAID array though.

Could it be that my array size is too large? (6 * 500MB = 3 Tb)

Thanks again for the help.

=============================================

Ok,

I have installed Ubuntu onto a new hard drive that I have added onto the IDE channel from the MOBO. I have loaded the gParted and am still unable to see the RAID array to partition it at all. I can see the RAID card if I go to System > Administration > Device Manager, so I know Ubuntu has detected it..............does anyone have any idea how to get this thing working?

Thanks.

Like I had mentioned before, I am able to access the array through the BIOS. I'm able to set up the array and set it to active. It's just not showing up in the OS, even in the Gnome Partition Editor.

---

