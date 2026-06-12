---
title: "Multi drive install but will only boot XP"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Paul-Devon-UK on 2009-11-13
I had been using a WUBI 9.04 install for some time but upgraded to 9.10. I gave up on the multiple issues and decided to bite the bullet and do a 'proper' install.

I have 4 drives so I cleared the 3rd and created 3 partitions. 1 to mount /, 1 for SWAP, 1 to mount /usr. I then booted from the 9.04 CD and selected Install. I followed the steps but stumbled at the partitioning stage. This is from memory so please excuse any inaccuracies. Initially the drive selected made a message similar to "This computer has no operating system installed" appear at the top. I tried each till I found the one with XP installed, The message changed appropriately. So far so good but if I selected the multi boot option (can't remember the wording) the selected drive changed and was not the XP one. I reselected the drive and selected the manual option and XP stayed selected. The next step was to select the partitions, file system and mount points which seemed easy enough. The rest of the install seemed simple enough and did not take too long at all.

Reboot. Windows boot loader - no GRUB.

So, I now have a shiny new 9.04 install but no way of getting to it.

Suggestions/solutions?

Paul.

---

### Post by darkod on 2009-11-13
Sorry but I lost you. :)
So on which drive did you install?

My recommendation also as newbie. No need to prepare partitions in advance, just have a plan in your head/on paper how you want them. During install you have to select manual partitioning anyway to use existing partitions. Why not create them at that moment.

What I think happened is grub got installed on the drive where Ubuntu is. And your BIOS is looking at your XP drive as first choice for booting. Hence, XP booting straight away, it doesn't have a clue about Ubuntu.

---

### Post by Paul-Devon-UK on 2009-11-13
> **darkod said:**
> Sorry but I lost you. :)
So on which drive did you install?

My recommendation also as newbie. No need to prepare partitions in advance, just have a plan in your head/on paper how you want them. During install you have to select manual partitioning anyway to use existing partitions. Why not create them at that moment.

What I think happened is grub got installed on the drive where Ubuntu is. And your BIOS is looking at your XP drive as first choice for booting. Hence, XP booting straight away, it doesn't have a clue about Ubuntu.

I installed on the 3rd drive and XP is on the 1st.

The partitions were created during my 1st attempt so already existed on this try.

OK so GRUB is installed on my 3rd drive instead of the 1st where XP is. Now what do I need to do to enable booting into Ubuntu? Can I chain boot from the XP boot loader or do I need to, some how, install GRUB on the 1st drive?

---

### Post by efflandt on 2009-11-13
There is likely a key you can press during your BIOS splash screen to select an alternate boot drive.  I do that when booting from live/install bootable USB.  You BIOS might put the drives in a different order when you do that, which might be a problem with /etc/fstab if you mount things by /dev ID or LABEL instead of UUID.

I am not very familiar with chain loading from Windows, but from the little I know from dual booting XP Home and XP64 beta a while ago, you might need to put grub on a partition on the 3rd drive instead of the mbr.

To reinstall grub on a partition see[COLOR=Blue] [[this]]("http://ubuntuforums.org/showthread.php?t=224351")[/COLOR]. But note that you if your root is on something like sdc1, that would be grub **root (hd2,0)** and to put grub on that partition would be **setup (hd2,0)** [instead of setup (hd2) in sdc1 mbr].

---

### Post by darkod on 2009-11-14
First of all, did you confirm grub is on the 3rd drive or you are assuming? I am asking because grub should have detected XP and it should be as an entry in grub menu next to Ubuntu already.
In that case the question would be how drive number 3 to be you first choice boot drive and that is all up to the BIOS.
Mostly new BIOSes you would still want to have HDD as first choice boot device (or second if CD-ROM is first for example), but there is another menu choice, for situations with multiple drives like yours, which of the hard drives to be first choice from all of them. Usually these settings are next to each other. Look around in BIOS and try to set drive number 3 as first choice from the hard drives while keeping HDD device as first choice boot too (or second as above).

If that shows up grub with entry for just Ubuntu and not XP, come again and ask or look around other posts how to add XP to grub2. Plenty of posts here and tutorials on the web. Cheers.

---

### Post by Paul-Devon-UK on 2009-11-14
Thanks for the responses.

darkod - I am assuming the location of grub as windoze can not access the drive and I can not run Ubuntu. I tried the boot option but that did not work, it just caused more confusion. I am ready for editing grub to chain boot XP as I saw that one coming.

efflandt - As you might gather from the following, most of that went WAY over my poor little NooB head LOL! I looked at the link but it seems that you need a working *nux install to start with, which I don't have yet.

OK, I hold my hands up to being "just a little bit confused" by the multiple naming conventions used to identify drives in Linux.

I wanted screen shots of the various relevant screens but until now could not work out how to do it. Thinking outside the box (PC) I realised I could use my phone camera so below are the relevant screens.

BIOS drive list - XP is on Primary IDE Master
Ubuntu will be installed on SATA 5 
[IMG]http:///thestoreindevon.com/forum_files/BIOS-drives.jpg[/IMG]

This is the partitioner as it first started
[IMG]http://thestoreindevon.com/forum_files/ubuntu-part-1.jpg[/IMG]

Manual selection of the Primary IDE Master recognised an XP install
[IMG]http:///thestoreindevon.com/forum_files/ubuntu-part-2.jpg[/IMG]

I left the selected drive and also selected the manual option
[IMG]http:///thestoreindevon.com/forum_files/ubuntu-part-3.jpg[/IMG]

I selected the partitions from a previous attempt and set the mount points as shown
[IMG]http:///thestoreindevon.com/forum_files/ubuntu-part-4.jpg[/IMG]

This is where it all started to go wrong. What is hd0?
This what I mean about the confusing naming conventions used. /dev/sd?, hd?, scsi? No consistency as name formats chop and change from screen to screen hence lots of confusion.
[IMG]http:///thestoreindevon.com/forum_files/ubuntu-part-5.jpg[/IMG]

Due to the confusion I left the above screen as was and installed.

Maybe I should have picked one from the list below but which one? I guess it might be /dev/sdd but could it be /dev/sdd1?
There is no help available and to a relative NooB it isn't obvious at all.
[IMG]http:///thestoreindevon.com/forum_files/ubuntu-part-6.jpg[/IMG]

Am I close to a solution?

---

### Post by darkod on 2009-11-14
It seems you did great. You installed (mounted) Ubuntu on Maxtor 6V160E0 (or dev/sdb) just where you wanted.

If you still want to have grub on the drive and leave the XP drive with it's own bootloader, you want grub installed also on 6V160E0 dev/sdb which is shown as choice in your last screenshot. Just select it.

My recommendation: Don't be afraid grub to be installed on the XP drive. It will offer choice for Ubuntu and XP and it's much better to select OS like that then entering BIOS every time you want to boot and remembering with which setting you left BIOS last time.

In case you want to install grub on the XP disk you need dev/sdd. Also, choose the whole disk dev/sdd as opposed to just a partition dev/sdd1. That will install it on the MBR.

It even shows you the disk models, you want the 80GB if grub goes over XP bootloader.

If not, you want dev/sdb the 160GB disk.

PS. With so many drives you can choose to have grub where ever you want. In order not to need to change anything in BIOS, and since XP boots first from the 80GB obviously, hence my recommendation to install grub there.

---

### Post by Paul-Devon-UK on 2009-11-14
darkod - That wast fast - thanks.

I am trying to get the machine to boot with an option to load either Ubuntu or XP so I believe I need to install grub on the same drive as XP (dev/sdd) as it is the primary boot device on this machine. I will give that a go.

I was so close it is frustrating. I am not blaming *nux BUT all those different names for the same device is so wrong and confusing.

If all goes well it may take me a while to respond to this thread as I will be in Ubuntu land and may take a while to get back here.

Another step closer to finally dropping windoze? Could be :D

Paul.

---

### Post by darkod on 2009-11-14
OK then, hope NOT to hear from you for a while. :)
Just for reference, hd0 should be sda, hd1 - sdb, etc.
Also, sda is name for the whole disk, sda1 the first partition on it, sda2, etc.
sdb the second disk, etc.

Not too complicated once you start using them regularly. :)

---

### Post by Paul-Devon-UK on 2009-11-14
> **darkod said:**
> OK then, hope NOT to hear from you for a while. :)

Good and bad news.

Good news - grub appears to have loaded onto the correct drive.

Bad news - it doesn't quite boot as can be seen below

[IMG]http:///thestoreindevon.com/forum_files/grub-boot.jpg[/IMG]

It just rapidly repeats GRUB. No keyboard input appeared to do anything.

Fortunately I made a drive image a couple of days ago which got me back up and running.

Now totally stumped.

---

### Post by darkod on 2009-11-14
I'm puzzled. I personally haven't installed on multi drive systems but it's not big deal really. It least shouldn't be. :(
Sorry, I really thought it would work, that's the way it should be really.

---

### Post by Paul-Devon-UK on 2009-11-14
> **darkod said:**
> I'm puzzled. I personally haven't installed on multi drive systems but it's not big deal really. It least shouldn't be. :(
Sorry, I really thought it would work, that's the way it should be really.

I agree. It SHOULD work but it doesn't.

I am searching the web for "grub grub grub" and the consensus seems to be a BIOS drive parameter sensing issue. Unfortunately I need to exit XP, install Ubuntu again, see if the error is still there. If so I need to play with the BIOS drive settings.

Either way, I will update this.

B.R.B. I hope.

---

### Post by Paul-Devon-UK on 2009-11-14
Oh the pain! GRUB GRUB GRUB GRUB

What is worse is that the repetitive nature causes me to sing the [Badger song]("http://www.badgerbadgerbadger.com/")!

Again the drive image came to the rescue.

I tried every option and combination in the BIOS for the primary boot drive. Access mode, Parameters, DMA mode etc. but no luck.

I still have one option up my sleeve - load grub on the same drive as Ubuntu and set that as the primary boot device in the BIOS. MAYBE the BIOS will treat the SATA drive differently to the IDE drive. A long shot but worth a try. If it works I can chainboot back to hd0,0 for XP (as a secondary boot option of coarse).

Unfortunately there are 4 things stopping me.

[LIST=1]
[*]It is approaching 01:00 here
[*]I opend a bottle of Red and am half way down it ;-)
[*]I rolled a phat one and am RATHER chilled!
[*]The wife is making seductive suggestions about a rug in front of the fire - nuff said
[/LIST]

As life is somewhat busy this end even though I am supposed to be retired (over 30 years working my way up the IT ladder) I doubt if I will get back to this for a few days.

---

### Post by Paul-Devon-UK on 2009-11-16
WooHoo!!! Writing this from within 9.04!

As I suspected, installing Ubuntu AND grub on /dev/sdb then set the BIOS to boot from that drive first.

I am glad it worked as my only remaining option was another WUBI install.

OK - the next hurdle :confused: Attempting to boot into XP failed with the following on the screen
> Starting ...
BOOTMGR is misssing
Press Ctrl+Alt+Del to restart
Could that be because hd0,0 is now the disk Ubuntu is on?

DooH. Typing this made me realise that I changed the BIOS boot order after the install completed. I expect I need to edit the grub startup file to run XP from a different drive.

fdisk - l was no help as the usual "which naming convention to use" problem arose.

> me@Paul-PC-Linux:~$ sudo fdisk -l
[sudo] password for me: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2d54bec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22cf0037

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+  83  Linux
/dev/sdb2            6375        6860     3903795   82  Linux swap / Solaris
/dev/sdb3            6861       19457   101185402+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
63 heads, 46 sectors/track, 337050 cylinders
Units = cylinders of 2898 * 512 = 1483776 bytes
Disk identifier: 0xd78c45cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      337051   488384512    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41b6ed0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9729    78148161    c  W95 FAT32 (LBA)


If /dev/sdb is now hd0,0 what hd?,0 is /dev/sdd ? Or am I barking up the wrong tree yet again?

/boot/grub/menu.list has the following at the end
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		XP Pro
rootnoverify	(hd3,0)
savedefault
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

I am guessing that hd3,0 is wrong.

---

### Post by Paul-Devon-UK on 2009-11-17
All working now.

I changed all hd3 occurrences to hd1 and now XP boots.

I wonder if I will ever understand the nonsense of the multiple device naming conventions randomly used?

---

### Post by darkod on 2009-11-17
Glad you got it going. :)

As for the naming, it's not that difficult.

sd stands for sata usually, older ide was hd. Then a,b,c are the disks. Then comes the number of the partition. So it becomes, sda1, sdb1, sdc1, sda2, etc.

When it comes to grub things get rough. :)
hd0 is the first drive regardless whether it's sata or ide. hd1, hd2 etc.

In pointing to the correct partition, grub starts counting from 0 but the new grub2 from 1.

So your XP is on the second disk, hd1, on the first partition (hd1,0). You have the older grub and the best way to tell is that you have /boot/grub/menu.lst present. Grub2 has different file structure and menu.lst does not exist. Just for example, in grub2 you XP partition would be (hd1,1).

After you've been doing this a while you'll know them by heart. :)

PS. Although by the look of your fdisk -l your XP is really on the fourth disk, hd3 or sdd. Strange it worked with hd1 but since it's working leave it as it is. :)

---

### Post by Paul-Devon-UK on 2009-11-17
I have already begun to see how the /dev/??? works and even the hd?,? but what is TRULY bugging me is that for example, fdisk will list /dev/??? but grub uses hd?,? while the install partitioner uses SCSI?. 

Why the feck don't they all use just one naming convention? Maybe it is the open source 'built by a committee' influence.

The reason XP boots as hd1,0 is because even though the physical drive is the fourth in order, I changed the BIOS boot order to put it second with my Ubuntu drive first. That makes for even more confusion as fdisk still lists the physical sequence which conflicts with the logical one.

If my MoBo did not have issues with chainloading to the XP drive I would not have been forced to introduce this confusion. I just hope I remember all of this if I trash it all and start again for some reason.

Now all I have to do is stop the bloody thing asking for a password every 10 seconds but there are plenty of available solutions to that one.

---

