---
title: "Dual Boot 1 HD to 2HD's Have No Access to Ubuntu"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2007-03-02
I thought I had educated myself to make it all work. I had a Single dual boot Edgy and XP. Both Harddrives are IDE, Primary Master, Ubuntu and Primary Slave XP. My xp boots fine, I used the Super Grub Disk to fixmbr. Did the Edgy Live CD to install Grub setup (hd0) all went well.
On the first boot I had my Grub Screen with all the operating systems available, I wanted to checkout XP and everything was fine. I re-booted to check out Edgy, and Grub did not show up and I was booting back to XP. 

During my computer transformation, I forgot to add the three partitions from the XP on hda1,
hda2, and hda3 which were copied from hda to hdb. If the partition #'s are off from my original root (0,5) this would explain why I can not get access to Edgy. I tried the Super Grub Disk, no luck. I went back to Gparted and adder 3 Primary partitions to see if this would correct the Issue?  

Here is my fdisk -lu  My original config was hda4 - hda7, 
How can I get or Mount to change my Fstab and Grub menu.lst???????
Also, I did use the ## to comment out the old mount points for my WINXP
Can I get back into my Edgy???
Can you assist

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    22426739    11213338+  83  Linux
/dev/hda2        22426740    44949869    11261565   83  Linux
/dev/hda3        44949870    68774264    11912197+  83  Linux
/dev/hda4        68774265   156248189    43736962+   5  Extended
/dev/hda5        68774328   111989114    21607393+  83  Linux
/dev/hda6       111989178   154143674    21077248+  83  Linux
/dev/hda7       154143738   156248189     1052226   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63       96389       48163+  de  Dell Utility
/dev/hdb2   *       96390   101000654    50452132+   7  HPFS/NTFS
/dev/hdb3       101000655   106767989     2883667+   b  W95 FAT32

---

### Post by Herman on 2007-03-02
Hello Chazall1,
I would like to help, but trying to understand what you are talking about is going to give me a migraine headache. can you please clarify your post, and avoid using so many contradictory statements. :confused:
>  I had a Single dual boot Edgy and XP. Both Harddrives are IDE, Primary Master, Ubuntu and Primary Slave XP.Please have another try at telling your story one step at a time as clearly as you can, someone will try to help you when they can understand what happened and what you want.

Regards, Herman :)

---

### Post by Chazall1 on 2007-03-02
Sorry. I went from Dual Booting on a single IDE Harddrive. XP , 3 partitions, 1 Fat 32, NTFS and Fat32. Extended partition, / /home and swap.
I have read all your Info before I installed over a year ago and I use you guides very frequently. I came up with a game plan to dual boot with 2 hardrives (both IDE) The wife has to have Windows. I got the new version of G-parted to copy my 3 Win partitions to the new HD. Primary slave. I checked before I copied the partitions to see if I installed Grub to the MBR of the original HD. In the live Edgy CD, I sudo grub, find /boot/grub/stage1, and I got 
(hd0,5) This would be my /root which confirmed all the info in my grub menu.lst root hd0,5)
So I thought maybe during my original install of Dapper, I chose other than the default install tp the MBR. All went well, windows can boot and boot. No Edgy!!

But New Info, Using Super Grub it was showing my kernel list that I had in grub, but it would not boot, I was editing the kernel root (hd0,5) is what first stage indicated, I 
Booted into Edgy with (hd1,5) where XP is, but xp only has 3 partitions. Supergrub indicated that it fixed MBR. I dont get it!!

Any advice??
Thanks

---

### Post by Herman on 2007-03-02
Okay then Chazall1, thanks for clarifying,
It seems like you have several problems here, all at the same time. Let me see if I can begin at the start and break it down into one problem at a time.

You had a single hard disk, dual booting Windows XP and Ubuntu.  Your Ubuntu installation was made up of three separate partitions,  /   /home and swap, and you had two FAT32 partitions for sharing data.

You added a second hard disk and copied your Windows XP and two FAT32 partitions to the second hard disk.

First, I think you should check to make sure that's legal. I'm sure you can copy and paste Ubuntu or any Linux without any hassles at all, but there is a lot of confusing fine print in the Windows EULA that you click on to say you agree to. Not very many people can understand it, but basically I think your Windows installation is registered to the hard disk it was installed on. They can detect you hard disk's ID number when you do a Windows update and see if you have changed hard disks or not. They will probably not bother to sue you, but they might let your copy of Windows 'time out' and expire in around three months time when you have a lot more important data in it and you have forgotten you did this. You will get a loggin screen with no place to log in, it will just sit there staring back at you. You will be able to rescue your data with Ubuntu and re-install, but you'll have to re-install on the disk you have Ubuntu on, or your Windows will time out again in another three months.
I'm not sure about that because I haven't tried it myself, but to be on the safe side, I'd re-install Windows on the disk it was registered on, or talk to Microsoft tech support and get their advice.

---

### Post by Herman on 2007-03-02
As for installing a bootloader to MBR, that's not really a correct thing to say at all.
When you 'install Grub to MBR', all it means is a very small 446 byte code is written to MBR to make the MBR 'point to' the Ubuntu partition where the main part of grub is. The MBR is far to small for grub to really fit in it. 
The same thing happens when we do 'FIXMBR'. It writes a 446 byte 'pointer' in the MBR to point to the Windows NTLDR bootloader.

The simplest thing to do for now is just re-install Grub to MBR again, just to make sure,                                                        [Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

### Post by Chazall1 on 2007-03-02
I will worry about the conflicts, and or legal issues. I just want My grub working. If the Kernel boot from the Super grub CD as root (1,5) does this mean that my XP MBR is using grub? and not the windows boot loader ?  I would like my Ubuntu on Primary Master to Use Grub as my boot loader. I have a Reinstallation CD for XP, should I see if it has a recovery mode to fixmbr?  Will you help?

Thanks

---

### Post by Chazall1 on 2007-03-02
I have done this and I still have the same issue. my root indicates (hd0,5)
In Super Grub I can get into Ubuntu by editing the kenel root to (hd1,5)  What mbr XP or Ubuntu should I start. XP is booting fine without the grub page showing?

Iam getting lost I think

---

### Post by Herman on 2007-03-02
Okay, I'm helping you, :) , but slow down a bit so I can keep up... :)

---

### Post by Herman on 2007-03-02
> If the Kernel boot from the Super grub CD as root (1,5) does this mean that my XP MBR is using grub? There is no such thing as an 'XP MBR'. The MBR belongs to the hard disk.
Windows partition begins with a boot sector, and so does the Ubuntu partition.
The MBR is not part of the Windows filesystem. :)

EDIT: Well, not unless you mean you installed Windows bootlaoder to MBR on your second hard disk and you are able to boot that somehow. Usually you would need Grub to do that, but there is a way to boot it from BIOS during start-up, by pressing your F8 or F12 key for a list of bootable devices.

EDIT: Anyhow, let me know when you have grub installed to MBR in your first hard disk, and we'll continue. I'll stand by until you get that far....
[                                                       Re-install Grub with a GRUB shell eg; with Live CD ]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")(or you can use SuperGrub Disk to 'fix the boot of grub').

---

### Post by Chazall1 on 2007-03-02
Had to get something to eat! I did use the live cd to install grub to (hd0) it indicated it was successful. I did this 3 times and there is no change. I understand the MBR at least the concept. If windows is booting correctly, I have done nothing to my MBR on disk 2 where the windows is at. When I type, (find /boot/grub/stage1) I still get (hd0,5) If I installed it to (hd0)
should it indicate this in the first stage boot?

---

### Post by Chazall1 on 2007-03-02
I also did the F12 to select OS. I picked the primary, secondary and got an indication that it could not boot F1 to retry and same thing. In my BIOS I can only have the cd and the Primary Master to have in boot sequence.

Thanks

---

### Post by Herman on 2007-03-02
You BIOS should boot the MBR in your first hard disk, which should be the one with Grub in it, but it seems like there is a difference of opinion here somewhere as to which is your first hard disk (Primary Master), and which is your second hard disk (primary slave).

Are you using jumper setting or cable select? Have you got those plugged in correctly?

Does the BIOS (CMOS) have the disk that has Ubuntu in it set as the first hard disk?

If you want, as an experiment you can try booting from the second hard disk's MBR to see if Grub is installed there.  I can think of several ways to do that, use SuperGrub Disk and boot off the second hard disk's MBR by going 'English Super Grub Disk'-->'Advanced'-->'Boot & Tools'-->'Boot Master Boot Record (MBR)'-->(and then choose which hard disk, either hda or hdb). That's one way to boot a non-first MBR.

Another way is to press 'F8' or 'F12' during bootup for a list of bootable devices, then select the device (hard disk 2),  you want to boot.
EDIT: Oh, you tried that already.

See if one of those methods helps you find the MBR that has Grub in it. :)

---

### Post by Chazall1 on 2007-03-02
Super Grub does not work, I get the error 22 no such partition at root (hd0,5) I cant even boot directly into linux. Its these small things that get you. I think my family hates me!!!!
Just kidding

---

### Post by Chazall1 on 2007-03-02
HD 1 Primary Master = cable select, HD2 Primary Slave = Slave for jumper settings.
Edgy is the 1st HD Primary Master

If I boot Master MBR in Super Grub my Windows boots!

New Info!
If I hit F12 and Choose Primary Master, I get Grub Screen with my OS selections.
I can boot into Edgy, However, when I choose my Windows, which I have added the
title 		Microsoft Windows XP  
map (hd0,0) (hd1,0) 
map (hd1,0) (hd0,0) 
rootnoverify (hd1,0) 
savedefault 
makeactive 
chainloader +1
It does to a Dell Dianogistic Screen, I clase the screen and windows boots.

If I hit F12 and choose Primary Slave, I get Windows to boot

I think we are narrowing it down.????
Thanks

---

### Post by confused57 on 2007-03-02
> **Chazall1 said:**
> Super Grub does not work, I get the error 22 no such partition at root (hd0,5) I cant even boot directly into linux. Its these small things that get you. I think my family hates me!!!!
Just kidding
You have the best person possible helping you with Herman...I understand your system, because it's very similar to my Dell Dimension 4550...when I set up my dualboot with 2 hard drives, Ubuntu master, Windows slave...I set both hard drives to "cable select", and had to go into bios to set my slave drive controller to "auto", I definitely understand how F12 is used to select boot device(has only master hd listed).
I was wondering what all the Linux partitions are on your Ubuntu drive?

Just saw your last post...use root (hd1,1)...I did the same thing you did when I first installed.
Here's the "howto" I wrote up, describing how I set up my system:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Herman on 2007-03-02
[CENTER][LEFT]Thanks, confused57 :)

Chazall1, I don't think you can have one drive working as cable select and the other jumpered as slave, can you? 

Either you have a special 'cable select' IDE cable with one end colored blue which plugs into the MBR, one end black that plugs into your master hard disk, and a grey plug for your slave drive. or you have a non-cable select IDE cable. If you have a cable-select IDE cable then you should have jumpers on both hard disks set to cable select position.

The non-cable select cable will have all plugs the same color, mine are all black for non-cable select IDE cables. You will need to set the jumpers for one of your hard disk as master and the other as slave.

Try sorting that out and make sure that's right first and see if it helps. :)

Regards, Herman :)

[/LEFT]
[/CENTER]

---

### Post by Chazall1 on 2007-03-02
I do have a blue end that connects to the MB, Black End for the Primary Master and a gray end for the 2HD Slave. I just thaught that this was just a standard cable? I got this cable after I first used the Original cable that came with the computer. I had it set up HD 1, connected to the MB, Connection 2 on the MB to HD 2 and the cd-rom. My fdisk -l showed my secon HD as hdd, and I was looking for hdb. If I change my jumper setting on my 2 HD to cable select, will I get hdb ?

I was trying to figure that out!
Confused57, I know Herman's knowledge in this area, He is one of the best!
and thanks for your support, I have read many of your postings.

Thanks,

---

### Post by Herman on 2007-03-02
Check out this film by Scott Mueller, I have his book 'Upgrading and Repairing PCs', and I am registered at the website there where there are quite a lot of good videos about installing hardware. I hope everyone can see this, I am not sure if you need to register first, but try this link anyway, [isdn21.asf]("http://www.quepublishing.com/content/downloads/upgrading/videos/High/isdn21.asf")

Regards, Herman

---

### Post by Herman on 2007-03-02
Sorry, I forgot you probably can't see that from the LiveCD, you need a hard disk installed Ubuntu with codecs to see the video.
> I do have a blue end that connects to the MB, Black End for the Primary Master and a gray end for the 2HD Slave. I just thaught that this was just a standard cable? I got this cable after I first used the Original cable that came with the computer. I had it set up HD 1, connected to the MB, Connection 2 on the MB to HD 2 and the cd-rom. My fdisk -l showed my secon HD as hdd, and I was looking for hdb. If I change my jumper setting on my 2 HD to cable select, will I get hdb ?You should have any drives that your cable-select cable is plugged in to jumpered as cable-select.
Any drives that your other (plain IDE) cable is plugged into should be jumpered as master and slave.

If you have both hard disk drives plugged in via the cable-select cable, and you have the jumper settings for both drives set to cable select, then you should have /dev/hda and /dev/hdb.

Regards, Herman :)

---

### Post by Chazall1 on 2007-03-02
Thanks for the Video, I will jump my HD 2 to cable select tomorrow and I will let you know what is happening, it may solve some of my issues. I am on my ununtu and not the Live CD.
Thanks for being patient with me, I get a little impatient, I am a perfectionist and in the computer world, that could spell disaster!!!!  I love to learn.

Thanks Herman!

---

### Post by Herman on 2007-03-03
Okay, I will keep an eye on this thread tomorrow and see how you are getting along. I think it will be a big help to have the drives plugged in and jumpered correctly. Then you will still probably have some fiddling around to do with your MBRs and menu.lst, but that should be a lot simpler now too when the drives are set up right.

I like learning too, and it's always good to keep reviewing what I already know in case I forget things, so helping you helps me as well.

If you happen to see that book for sale somewhere, '[Uprading and Repairing PCs]("http://www.quepublishing.com/promotions/promotion.asp?promo=1626&rl=1")', by Scott Mueller, i recommend it. 
There are quite a lot more short films like that at his website too. After watching them all enough times and reading the book I was able to build myself a new PC from scratch (well I recycled a few old parts), for half the cost and double the hardware capabilities as what I could buy factory made for the same  money. That way we can have a new computer that doesn't come with Windows pre-installed too, which is an added savings. 

Regards, Herman :)

---

### Post by Chazall1 on 2007-03-03
Thanks for the Book Info. I set my HD2 to cable select and I have hda and hdb. My Windows boots First on each reboot. I must hit F12 and choose Primary Master to get to my Grub OS selection Page. I can boot into Edgy this way. I also checked /boot/grub/stage1 from the live cd and it still indicates (hd0,5). If Windows is booting on HD2, can I assume that HD 2 does not use Grub to boot, but uses the windows boot loader. Maybe I should keep what I have using the F12 to select The Linux options?

---

### Post by confused57 on 2007-03-03
> **Chazall1 said:**
> Thanks for the Book Info. I set my HD2 to cable select and I have hda and hdb. My Windows boots First on each reboot. I must hit F12 and choose Primary Master to get to my Grub OS selection Page. I can boot into Edgy this way. I also checked /boot/grub/stage1 from the live cd and it still indicates (hd0,5). If Windows is booting on HD2, can I assume that HD 2 does not use Grub to boot, but uses the windows boot loader. Maybe I should keep what I have using the F12 to select The Linux options?
As long as you don't mind hitting F12 each time and it's working, you might want to leave it set up that way.
I may just order the book Herman suggested...1608 pages(current edition April 2006 on Amazon.com), so it must be quite comprehensive...I believe the video is fairly old, just mentioned PATA drives & ATA66; however, it was a great explanation of the basics of installing a hard drive.

I don't know about your IDE hard drive cable, but I'm pretty sure the end connector is for the master drive on my computer.

---

### Post by Herman on 2007-03-03
Hello confused57, 
Probably there will be a newer edition of that book in April, I think it comes out every year. Some of the videos are a little old, but I think they're great. Try navigating around in that website, '[Uprading and Repairing PCs]("http://www.quepublishing.com/promotions/promotion.asp?promo=1626&rl=1")', and see if you can find some more videos. It's possible to get a lot of information from watching the videos, but it's good to have the book to look things up in. That book is great for anyone who likes getting involved with the hardware side of things, and of course, even if we are only interested in software, better knowledge of hardware can help sometimes. 


Hello Chazall1,
It's up to you, I understand if you don't want to spend an entire weekend fiddling with your bootloader. You probably want to get on with something more fun for now. That's okay, the main things for now is, it boots okay. Later if you get tired of booting it that way you can always come back to it and set it up a different way. There are even some people here who actually recommend setting their computer up the way you have it now.

If you want to keep going then it would be best to have a fresh copy of sudo fdisk -lu and a look at your /boot/grub/device.map file. Maybe we'll try editing device.map. Or did you plug in the hard disk with Windows on it as master? Probably we just need to install Grub to (hd0) and you should be okay then. 

Regards, Herman :)

---

### Post by confused57 on 2007-03-03
> **Herman said:**
> Hello confused57, 
Probably there will be a newer edition of that book in April, I think it comes out every year. Some of the videos are a little old, but I think they're great. Try navigating around in that website, '[Uprading and Repairing PCs]("http://www.quepublishing.com/promotions/promotion.asp?promo=1626&rl=1")', and see if you can find some more videos. It's possible to get a lot of information from watching the videos, but it's good to have the book to look things up in. That book is great for anyone who likes getting involved with the hardware side of things, and of course, even if we are only interested in software, better knowledge of hardware can help sometimes. 
Regards, Herman :)

Thanks Herman,
     The book received a 5 star rating from 43 reviewers on Amazon.com and  think I'll wait until the new edition comes out in April to order...when I first installed Ubuntu back in December '05, I didn't even know what a partition was...I've since built a couple of computers, one of which I have installed an IDE and SATA drive that I'm booting 10 distros on...I find it fun and satisfying to learn as much as I can(or my abilities allow) about computers & OS...can't have too many  resources such as your site(& sites from other members of the forum), as well as an informative "howto" book or 2.
Thanks again for the info,
           Jim

---

### Post by Chazall1 on 2007-03-03
Thanks for all the Info. I think I will use the F12 option at this point. My system is obscured from everyone and when I shut down Edgy it automaticly boot to windows for my wife and my two teenagers! At this point its time to move on. I have informed allot of people and have directed many people wanting to look into linux to look at your post for the great resources that you have put together. 

Thanks Herman.

---

### Post by Herman on 2007-03-03
Okay Chazall1, welcome to Ubuntu and keep spreading the word to all your friends. :)
There are lots of others besides confused57 and I here who can help you and your friends with all you want to do in Ubuntu. confused57 and I and several others are particularly interested in helping people with booting and bootloaders, especially the grub bootloader. We know a little about lots of other subjects too.
There are all kinds of others around the Ubuntu Web Forums who are experts in the other subjects, and know a little about grub and bootloaders, so whatever help you or your friends are looking for you'll find someone here that will enjoy helping. :)

My own website is just one of many, and there are some other other websites you can link your freinds to that they should also see to help them get started with Ubuntu. Here are a couple of them, 

aysiu's website, excellent, [COLOR=#3333ff][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[/COLOR]
Some great video how-tos, [ubuntuclips.org | video howtos for human beings]("http://ubuntuclips.org/")

 [Official Ubuntu Wiki Front Page]("https://wiki.ubuntu.com/")

[Edgy Eft Starter Guide]("http://ubuntuforums.org/showthread.php?t=322396")

That's just a small sample. You can do anything with Ubuntu.

Enjoy, 
Regards, Herman :)

---

