---
title: "Installing, need instructions."
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by umanzor on 2005-12-04
I currently have a NTFS XP partition (40GB). I want to install Ubuntu in that hd, so I was thinking on creating a 4GB partition for it. Small, since I just want to ty it installed. I read you can create the partition from the installer, but I don't wan't to make 10GB (the free space left), but 4GB instead. I'm new to Linux, so I need some help here.

Thanks

---

### Post by invalid on 2005-12-04
I suggest partition magic, to use within windows.

Cheers,
Cb

---

### Post by aysiu on 2005-12-04
Follow these instructions--and you can make the partition as big or small as you want: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by umanzor on 2005-12-04
[QUOTE=aysiu]Follow these instructions--and you can make the partition as big or small as you want: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)[/QUOTE]

Thanks for the link. Got a couple of questions;

1. How common is the failure of GRUB? (where you can't boot windows or linux), because I don't have my XP CD handy.
2. If I later want to delete that linux partition, will I be able to without formating the whole drive?

oh and..
3. What if I don't install GRUB?

---

### Post by aysiu on 2005-12-04
> **umanzor]Thanks for the link. Got a couple of questions said:**
>  In the past seven months, I haven't seen that much of it in these forums. In the past two days, a lot of it, for some strange reason.

Personally (i.e., on my computer), it's never been an issue.

Neither is terribly easy, but both Ubuntu and Windows have ways to repair the MBR. For Ubuntu, you can reinstall Grub. For Windows, there's a utility called fixmbr.

> 
2. If I later want to delete that linux partition, will I be able to without formating the whole drive? You can, but then you'd have an empty partition.

[quote]
oh and..
3. What if I don't install GRUB? Then, you're going to have to do some electronic backflips to get Windows' boot.ini to recognize Ubuntu. Grub, however, will automatically add Windows to its boot menu.

---

### Post by umanzor on 2005-12-05
Ok, but in case Windows boot fubars, and I don't have the XP CD handy, how would I be able to run the fixmbr? ----> And running it wouldnt make me reinstall GRUB?

I guess I could format the empty partition as NTFS, and then merge it with the XPs one?

---

### Post by aysiu on 2005-12-05
You can read up a bit more on fixmbr [here](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

### Post by umanzor on 2005-12-05
Yeah, but I can't access the Repair Console without the XP CD... so I'd be kinda screwed.

---

### Post by Herman on 2005-12-05
Hello umanzor, Herman here, I read your post and was curious about something. I had an idea that I remembered reading somewhere that a WIndows 98 boot disk would be just as good for restoring a Windows XP MBR as a Windows XP CD. But I wasn't sure, so I decided to test it and see for myself. I have a perfectly good computer here, with Windows XP home edition installed triple boot with two installs of 'Breezy'. My PC came with  XP 'recovery CDs', rather than 'install' CDs, (so I can't likely use the 'fxmbr' command either). However, as I have already done maybe one hundred or more dual boot installs and never once had any problems with GRUB at all, this is just for an experiment. (For fun.) Well I can report that it all went very well and Windows XP has rebooted without any sign of GRUB, announced it had 'found new hardware' and wanted to re-boot once more to install it. Now it has re-booted again, once again with no sign of GRUB.
I used a Windows 98SE OEM boot disk  which I downloaded for free off the internet somewhere.  You can get one from:   [http://www.bootdisk.com/](http://www.bootdisk.com/)
I typed     fdisk /mbr    at the A:\>_  prompt after booting with the boot floppy in.
It worked when I tried it! :D 
For my next trick I'll install Lilo boot loader to my two Ubuntu partitions using:
[http://ubuntuforums.org/showthread.php?t=96920](http://ubuntuforums.org/showthread.php?t=96920)
and then I'll configure a GAG floppy disk and boot all three OS's again, then I'll re-install GRUB to MBR again,using: [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)  and be able to boot off either GAG or GRUB for all three systems. 
Booting OS's is not a problem, there are lots of ways to do it. :D

---

### Post by Herman on 2005-12-05
Okay, I've done all that. I did a few other experiments and learned a few other new things also.
For those people who understandably do not feel comfortable taking the risk of even the slightest possibility of GRUB not installing correctly to their MBR, a GAG boot floppy disk and/or a GAG CD would be good insurance. GAG is only a small download and it's free (open source). GAG will boot Windows even if the MBR is messed up. You download it as a compressed file and extract it, then install it to a CD or a floppy from either Windows or from Ubuntu (or other Linux). Then it is ready to use in an 'emergency'. (Well, you still need to configure it, but that doesn't take long).
[COLOR="Sienna"]The GAG bootloader can run off the CD or floppy disk without disturbing whatever is on the MBR already.[/COLOR] [http://gag.sourceforge.net/](http://gag.sourceforge.net/)
The Windows 98  boot disk is another free download. If people had these tools ready beforehand they would be prepared in case GRUB did fail to go in correctly, they could fix GRUB later in a calmer state of mind. Just knowing they have other ways to boot their system ready 'just in case' should be comforting.
I still believe GRUB is the best bootloader of all, but when people could be using their computers for very important work I can understand them being worried it might not go in correctly for them. (Herman)

---

### Post by umanzor on 2005-12-05
Ok harman, thanks for the info! cookies...

Thats some nice tool, with GAG, I just need a floopy to boot either of the OSs installed? That makes me feel more confortable. And in case of any eventuality I can use the 98 boot disk.

Just out of curiosity... I guess after you fix your mbr with fixmbr, you would have to reinstall GRUB right?

If I install GAG, using a floopy, what happens if I don't use the floopy, will it load directly to windows?

Im sorry for being such a newb and for making lots of questions. Thanks!

---

### Post by umanzor on 2005-12-05
wtf? my last post didn't seem to be posted...

Anyway, thanks for the info harman! Cookies...

I can use GAG to load to Ubunto partition from a floppy disk? That makes me more confortable. I guess I just have to skip the GRUB installation during the Ubuntu install.

Got another question, later, can I format the linux partition in NTFS and merge it with the XP one, so I can have the HD as I did before installing linux?

---

### Post by Herman on 2005-12-05
Okay, umanzor, it's good when you ask lots of questions, it might help to make it clearer to someone else following you with the same worries.
I will explain a little bit more. 
When you use the fdisk /mbr command at the A:\>_ prompt, (Win98 boot disk), or the fixmbr command with the XP CD-ROM, either should, we hope, restore computer's MBR to boot Windows. The MBR is very tiny, from what I have read, and is only big enough to point to another device to boot an operating system with. The one most people have originally just points to  a file called 'boot.ini', which boots Windows. But Windows 'boot.ini' does not know of any other operating systems you may wish to boot later on, it will only boot Windows. 
When we install GRUB, the MBR is changed to point to our Ubuntu partition instead, and I guess it finds our 'menu.lst' file for instructions and we see our GRUB splash screen and can choose which operating system we will hopefully be able to boot. So the message to boot something gets sent from there to Windows 'boot .ini' file and boots Windows, or else it goes to the Ubuntu kernel and boots Ubuntu. (Whichever one we chose). I'm still learning these details myself. My explanation might not bear strict scientific scrutiny, but it should be near enough to help a little, I hope.

Now when I restored the MBR, to it's former condition with fix/mbr, it of course will only refer only to the boot .ini file to boot Windows. 
I'd normally have to re-install GRUB then, to have the choice of booting Ubuntu or Windows when I want to. That would cause the MBR point to my Ubuntu partition again.
GRUB will boot as many operating systems as you like, (Well I don't know what the maximum number is actually), as long as the MBR points to the last Linux operating system to be installed, with the most up to date 'menu.lst file'. You do not have to worry about that because the installer will do that automatically for you.
GAG can also boot Windows and up to nine other operating systems if you like. It can be run from a floppy disk, and configured on the floppy to boot all your operating system while leaving your MBR untouched, or installed to the MBR if you wish. (Well, they say that, but I don't think it really installs to the MBR, I think it installs somewhere eIse, but they say the 'MBR' for short, I think they really mean they change the MBR to point to it). It can also be run from a CD to boot any operating system you like. Some computers have no floppy drive. You can't configure it on a CD and write the changes to a CD, so you have to set up the OS you want to boot each time you use the CD. 
GAG seems to have no problem booting Windows at least, regardless of the state of the MBR on the hard disk.
GAG needs something special done in order to boot Ubuntu though. I installed Lilo
to my Ubuntu partition because that's easy for me, the Ubuntu installer provides the option for that. if it provided an option for installing GRUB to the Ubuntu partition, I would have chosen GRUB rather than Lilo. 
The first person to post about GAG didn't recommend that, 'linuxlizard' recommended making a seperate /boot partition and installing GRUB to that and using GAG to boot Ubuntu through GRUB.
Yet another option is to install GRUB to a floppy disk. I have tried that too. But if you want to use a floppy disk then GAG is best in my opinion because you can re-configure it as many times as you like if you re-install often, or even reconfigure it for another computer and use the same floppy disk.
Of course you have to have your BIOS boot order set for booting from CD, floppy and hard disk. 
Perhaps a more advanced Ubuntu enthusiast can correct me on a few points, but this is how I think things work from the reading I've done, I hope it's fairly accurate information. (Herman).

---

### Post by Herman on 2005-12-05
> I can use GAG to load to Ubunto partition from a floppy disk? That makes me more confortable. I guess I just have to skip the GRUB installation during the Ubuntu install.
 I would recommend the option to 'install GRUB to MBR', that's what I always do and if it doesn't work out for you, then use one of the other options as an alternative. GRUB is still the best. It is a great boot loader, I prefer it by a long shot! :p 

If you are really sure you want to use GAG, then when it offers to install GRUB to MBR, say no and it will take you back to the Ubuntu installer Main Menu, and you go down one line and choose 'Install Lilo to a hard disk', and then in the next panel, choose to install Lilo to your new Ubuntu partition, (the middle option in the list).
Well it's your PC, it's up to you. If you do that, it will leave your MBR alone, but then the installer needs something to reboot with during the installation, and you'll need your GAG boot floppy or a GAG CD already prepared in order to re-boot with during the installation. For an experienced person doing the install that's alright, but it's an extra worry if it's your first time. I wouldn't really recommend you put yourself through any extra worries you don't need to. You'll need to do your homework before trying that. Make a GAG floppy and practice little first to get used to it.

> Got another question, later, can I format the linux partition in NTFS and merge it with the XP one, so I can have the HD as I did before installing linux?
You can You can delete the Ubuntu partition if you don't like Ubuntu, and reformat it as NTFS,or FAT32. I sure you can do that from Windows XP. I'll check the exact details later.
You will always have two partitions though, you can't make it back into one partition unless you do a complete Windows re-install. I used to re-install Windows a lot anyway, it's good for Windows, it gets rid of a lot of spyware and things like that that Windows accumulates. It's okay to leave it as two partitions though, the spare partition will show up as another drive in 'My Computer', and you can still use it. You can store files it it where they will be safe from any virus that might destroy your main system. (Herman) :D
Edited 23/12/05: You can use Gparted on the Ubuntu 'Live' CD, or QTParted on a Knoppix or System Rescue CD to resize a Windows partition to make it fill up the free space after deleting the old Ubuntu partition, if you want to have the hard disk the same way as it was before installing Ubuntu. (Herman).

---

### Post by umanzor on 2005-12-05
Well, I'll try with GRUB then. Thanks for the info, you sure know a lot.

note: he, didn't see page 2, thats why I thought my post wasnt posted.

---

### Post by jimrz on 2005-12-05
Actually as much a a question as a reply...am going to do a dual boot install next weekend. What about BootMagic (comes on the PowerQuest PartionMagic cd) as an option should grub fail to operate properly? Seems could repair problem and get a workable boot manage all in one shot...maybe?

---

### Post by Herman on 2005-12-06
umanzor,> Well, I'll try with GRUB then. Thanks for the info, you sure know a lot. Grub should be the best for most people's computers, I am pretty sure it works fine in the great majority of instances, but not many post in to say 'hooray, I installed GRUB and it works!' People post in more when something doesn't work and can be (understandably perhaps), quite upset and worried. That can make other people afraid to try things. But if you know how to fix it if it does go wrong or at least ways to cope it isn't so scary.
 thanks for the compliment, but actually, I'm just another beginner who has been here a bit longer than you. There are more knowledgeable people around here than me who might disagree with many of my thoughts and assumptions and would be able to teach me a lot. Hang around these forums, it's a great place to learn!:smile:

---

### Post by Herman on 2005-12-06
jimrz; > Actually as much a a question as a reply...am going to do a dual boot install next weekend. What about BootMagic (comes on the PowerQuest PartionMagic cd) as an option should grub fail to operate properly? Seems could repair problem and get a workable boot manage all in one shot...maybe?
Well it does no harm to have an alternative handy just in case, it would probably work okay, but GRUB is still my favourite first choice. Let us know all about it if you do need to use it. I'm always interested to learn more.:D

---

### Post by jimrz on 2005-12-06
[QUOTE=Herman]jimrz; 
Well it does no harm to have an alternative handy just in case, it would probably work okay, but GRUB is still my favourite first choice. Let us know all about it if you do need to use it. I'm always interested to learn more.:D[/QUOTE]

Thanks...will do if have to try...was just kinda thinking out loud about alternatives...hopefully will not need to find out

---

### Post by Herman on 2005-12-06
I don't think you'll need it, I'll bet GRUB will go in fine. I would be very interested to see some real statistics about how many times GRUB goes in successfully compared with the number of instances where people have trouble with it.
And even then, most of the time GRUB can be easliy repaired as long as it will boot Ubuntu.
There could be some computers or types of hardware that have more instances of GRUB not working. It seems to me to be more common with more complicated set-ups like multiple hard drives and greater numbers of partitions. And maybe SATA as opposed to regular ATA (IDE). It would be interesting to know for sure.
I think it's 'fear of the unknown' that makes people's emotions come into play so much when they have trouble with GRUB. 
I have added a new MBR page to the website in my signature link. But I still have a lot to learn myself and I need to be sure I'm giving the correct information first, so I have only made a start on it, there's still a long way to go. Maybe if people understand things from reading it explained in a simple way they won't be so nervous.
Aysui has also done a great job with a new .pdf document that will help lots of people. It includes some information on editing the menu.lst file for GRUB, plus lots of other topics as well! I think it's great, I learned a lot from it too! People should try to get ahold of that, from aysui, it's called 'ubuntu_user_guide_05.11.pdf. It's great! So is the rest of aysiu's work, all new people should pay a lot of attention to aysiu.:D  (Herman)

---

### Post by foolosophy on 2005-12-09
Herman, I have a question.

My 40GB hard-drive is installed with:

hda0: Win98SE  (aprox. 10GB) (FAT32)
hda5: Win2000 (aprox. 23GB) (NTFS)
hda7: Ubuntu Breezy (aprox 7GB) (ext3)

I use GRUB to dual boot between Ubuntu & Win2k. When I select W2000, I have a prompt (that was installed with w2000) to choose between W98 & W2000.

What I want to do is this:

Format the w2000 partion and MERGE it with my ext3 partition. And, once done this, format the Win98 partition and install w2000 there. In the end, if things work, I'd have: hda0 with w2000 10GB, and another partition with 30GB for linux.

Is it possible to do this?

This is the mountpoints info:

```
pablo@Pablo:~$ sudo fdisk -l /dev/hda
Password:

Disco /dev/hda: 40.0 GB, 40038211584 bytes
255 cabezas, 63 sectores/pista, 4867 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        4867    28852740    f  W95 Ext'd (LBA)
/dev/hda5            1276        4208    23559291    7  HPFS/NTFS
/dev/hda6            4209        4221      104391   83  Linux
/dev/hda7            4222        4835     4931923+  83  Linux
/dev/hda8            4836        4867      257008+  82  Linux swap / Solaris

```

---

### Post by Herman on 2005-12-09
Olay,foolosophy!:D , so you have Windows 98 on a primary partition which you want to delete, and one big extended partition housing Windows 2000, (on NTFS), Ubuntu, (on ext3), and swap. For your Windows 2000 NTFS to be included inside your 'Extended' partition, that means it must be a 'logical' partition? Is that correct?
Also, you have GRUB booting both Ubuntu, and Windows 2000, and boot.ini in Windows 2000 configured to bring up NTLDR to choose between Windows 2000 and Windows 98!
Wow! I'm extremely impressed! :D  You should be teaching me! I've yet to learn how to do most of those things myself! :D  I am studying hard though! :D 
I'm a bit pushed for time right at the moment, I'm working the weekend but hoping for time off next week.
Fast answer: if you enjoy re-installing completely and starting again fresh that is the simplest; and install Windows 2000 first, then Ubuntu, so GRUB will be installed last, and boot both systems.

The above answer I'm fairly certian will work, the below anwser could turn out more complicated and I haven't got enough time to give a proper answer, but here's a crude, rushed, attempt anyway:

It's no challenge doing everything the simplest way, and I am very interested in describing exactly how I would do a whole lot of things like delete the Windows 98 partition, and move the Windows 2000 NTFS to the beginning of the drive with QTParted on a Knoppix CD. However, it is NTFS, and I cannot tell you for sure if this is safe because my own experience is limited to FAT32 only. 
I would make a GAG boot disk just in case, too, before doing anything. And of course, needless to say, back up all my data!
Then I would suggest making the free space in the middle between the two partitions into a FAT32 partition, (where Windows 2000 used to be).
I don't think you can really make the ext3 partition larger or 'merge' it with your old WIndows 2000 partition. At least not without re-installing.
I thought I could remember some way I did that once but now I have forgotten, or am I remembering incorrectly? Last time I tried I couldn't do it.
I will have time to give you a better answer later on, I just wanted to let you know I am very interested in your question and I want to try some things out on my test computer for you and give exact info, but I haven't got the time to test things today. Maybe tomorro or the day after. I'm sorry I can't do much right away though, regards, (Herman)

---

### Post by foolosophy on 2005-12-11
Yep, you got it right. 

As you said, formatting all the disk is no challenge. And also, it will take me a long time to re-configure Ubuntu as I now have it. 

You say it's impossible to merge an ext3 partition with "free space"? Mhh.. I'll try to search the web for that info. And, QTparted will work if I run it with the Ubuntu Hoary Live CD? (I don't have a Knoppix CD)

Well, thanks a lot!:D

---

### Post by Herman on 2005-12-11
Sorry to say this, foolsophy, but I just fired up my test computer and I was going to delete one Ubuntu partition out of the middle of it and create a new one there, format it as ext3 or reisrefs, choose the partition and choose 'edit the partion','copy data from another partition'. The I was thinking of deleting the old partition, then re-sizing the new one bigger to fill up the rest of the disk space. I was just getting started when my boss called and needs another customer taken care of, that will take me several hours again. Sorry, I have to go again.:( . I am really interested, but I need some continguous spare time without too many interrruptions to concentrate properly or I'll go crazy! :D  (LOL). I'll try again later. Let me know if you have any sucess in the meantime, I want to know too. (Herman)
> And, QTparted will work if I run it with the Ubuntu Hoary Live CD? (I don't have a Knoppix CD)
No, gparted, I think is our partitioner on Ubuntu install CDs. QTParted can move Windows partitions arouind and grow and maybe 'merge' windows partitions, (I'm not sure yet if it can 'merge', but maybe. But it couldn't do so much with ext3 or reiserfs last time I tried, but I'll try harder as soon as I get home again, for you. QTParted is on 'System Rescue CD', Knoppix, and I think Knoppix STD edition too, all of which are free, if you can download them without internat useage charges from your ISP that is.
Gparted can do some pretty good tricks too, but we need to experiment with it to find out the secrets of it, as it doesn't have too many instructions that I know of.  (Herman)

---

### Post by Herman on 2005-12-12
foolsophy, my progress so far: 
I had a 30.0 GB hard disk with Windows 98SE (10.0GB), Breezy (10.0 GB) and Breezy (10.0 GB).   I deleted the middle 'Breezy', install but was unable to do anything with the other breezy install with the Ubuntu installer partitioner. (As far as re-sizing goes).
QTParted on my Knoppix CD had no problems with Windows, I could move it, shrink it or grow it any way I liked, but bear in mind, mine's only FAT32. I did everything to it and have finished off with it shrunk to 3.0 GB, and it has re-started 100% 'A-okay'. I'm not sure how NTFS will be, but I think QTParted has NTFS support, no guarantees though.
 I couldn't do anything with Ubuntu using QTParted, the options in the right-click menu become 'greyed out' when the Ubuntu partitions were chosen.
Right now I am up to experimenting with the Ubuntu Install CD again, and doing as I said I would do and using the 'copy data from another partition' option. I tried first to create minimal sized temporary new Ubuntu partitions, hard against the 'Windows' side of the hard-disk, the plan being for them to be just large enough for the data, leaving maximum room left on the disk. That way I can create new partitions for Ubuntu which are larger than before, and  then transfer the data back again. 
I am still working on a few problems with this method of doing things. One slight disappiontment was that I got an 'not yet implemented' sign for trying to copy a larger partition to a smaller one, even though it was large enough to hold the data easily. Apparently this function is still being worked on, maybe in a future release it will be perfected. So I had to go back and make equal sized partitions or larger. That's still okay, because I made a lot of room when I shrunk Windows. I will still be able to delete all my old Ubuntu partitions, and then create even larger ones again, transfer the data back to them, delete the temporary (middle) partitions, re-grow Windows back to it's old size, and I'm done! Of course this would involve removing a lot of data from Windows, for most people. I actually have no data there at all, it's just a test computer. But this is maybe about as close as I can get so far for a method for 'growing' Ubuntu bigger. I'm not finished testing yet, so I cannot recommend it as 'safe' or suggest anyone begin doing it yet at this stage. I still need to experiment some more before I'll have a technique 'ironed out'. Just so you know I am working on it.:D Regards, (Herman).

---

### Post by foolosophy on 2005-12-12
So, what you're saying is.. you CAN'T move the mountpoint of the "/" Ubuntu partition?


I've just had an idea! First, let me show you all my data disk (a printscreen of QTparted):

[http://photos1.blogger.com/blogger/6038/1111/1600/Pantallazo.png]("http://photos1.blogger.com/blogger/6038/1111/1600/Pantallazo.png")

Ok: My idea is: use a Knoppix cd or something similar (maybe the Ubuntu install CD) so as to use a partition software.

First, I would backup my data to the fat32 partition (the one I am not changing).

I would delete "ntfs" and "/boot" partitions, and then make a "/boot" one where the "ntfs" used to start. So then I'd have free space between the "boot" partition (which would be of.. dunno.. 100MB) and my Ubuntu partition. And THEN, I'd try to merge the Ubuntu partition with the free space. I hope that this works. Two problems may come up: 1st) maybe QTparted doesn't allow me to resize the ext3 partition "backwards" (that is, to change the initial mountpoint); 2nd) It may happen that even if QTparted allows me to do so, then Ubuntu gets screwed up and cannot boot (even if I load it with GAG, or a boot disk (because I'd also have to re-install GRUB).

Did you understand my theory? I haven't done any partitioning yet, because first I have to finish backing up all my data (it's taking a long time, I had like 20GB in music).

Thanks a lot, Herman, you've been really wonderful. It's great to have this kind of support from the other end of the world.

Pablo

---

### Post by foolosophy on 2005-12-22
'walking' partitions bigger -  1 Week Ago
Hello, Pablo, it's Herman
I don't know why, but I tries\d to post to our thread several times and couldn't.
Anyway, I wanted to let you know I have had some positive results with our project. I have not yet found a way to actually 'merge', or grow a Ubuntu partition yet. But what I am finding is that I can use the 'copy data from another partition' function in the installer, to transfer the data from a smaller partition to a larger one. I have 'cloned' a Ubuntu installation from one end of some free space on my hard drive to the other and succesfully booted it.
It should work for ext3, but reisrefs file systems are not supported yet for this feature in the install disk.
So it seems to me if you want to delete your Win98 partition with QTParted and see if that can move your Win200 to the beginning of your drive, that's how I'd begin. Then, remove some files from Win2000, and use QTParted to shrink it temporarily, just to give yourself some extra hard-drive room.
Then put in the Ubuntu disk and go through all the motions 'till you get to disk partitioning. Create a new partition equal to or slightly bigger than 7.0 GB (the size of your old one) now imagine you got a lot of files out of Win 2000 (you still have all your settings and software intact, just remove as many files as you can), and have Win 2000 shrunk down to say maybe 7 or so GB. That means you could move Ubuntu into a temporary 7 GB partition right behind it. Then, delete your old 7 GB Ubuntu partition at the other end of the drive. That means you'll have: 40GB-14GB of free space. Then make a new ext3 partition, (bootable) as big as you want up to 26 GB !
Then 'copy data from another partition' back into that one, and delete the 7 GB temporary one. Expand Windows again, put your data back in Windows and you'll be all done!
'Copy data from another partition' option can be seen by going to the illustrations named: 10th ntfs, 19 ntfs, 21 ntfs and others, on my 'Ubuntu Dual Boot' website.
I hadn't tried out that option until I started thinking about your question, so I have learned a lot by this and have enjoyed it very much!
Thanks, Pablo, and all the best, from Herman.
PS, anything you're not sure about, please ask, I'll be lurking around. I know I was a bit brief here, you may need to know more.

[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)

---

### Post by foolosophy on 2005-12-22
(by Herman)
Hello again, Pablo,
I had a bad day today, I cloned one Ubuntu install three times and one problem is GRUB doesn't get updated that way, so I had all these identical partitions I was trying to boot into to see if I could or not and find ways to boot them, but since they were all identical, it was hard to tell which one I was actually in each time. I think I kept getting back into the same one. So I tried re-installing GRUB, (on a different one), but that wouldn't install for some reason. It normally does. So I tried Lilo instead, and that wouldn't install either. So in the end I got sick of it and deleted them all and started again. This time the electricity went off. They must be working on the lines. I have been trying all day now and each time I almost get an install completed, the power company cuts the electricity on me, and I leave it installing until my UPS runs out, and then they turn the power back on a few minutes too late. AHHHHH!!!
Anyway, this time I'm installing Lilo, so when I clone it, it will have Lilo already in it. That means (I hope), GAG should be able to find it and boot it, and I can do whatever I like after that. I don't understand what I did wrong to begin with. I wonder if not being able to 'after-install' GRUB or Lilo had something to do with making logical partitions rather than primary. Maybe GRUB and Lilo don't like being installed on logical ones, but if you do it during the install, it's okay.
I remember yours is logical, so I hope it won't be a problem. Maybe it's something else I did.
Well, back up all your stuff first, anyway. I'm still testing here and it looks like it'll take me a lot longer than I thought before I'll have all this down pat. Or maybe I just had a bad day and everything will go alright tomorrow. (Herman)

[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)

---

### Post by foolosophy on 2005-12-22
Ok. It's been a long time. I've made some improvements.

(I'm trying to remember all I did)

First of all, I backed up all the data I wanted to keep to the hda1 (vfat - win98) partition, which was almost filled with it (10GB aprox). Then, I used the Ubuntu Install CD to format the hda5 (22GB, NTFS, with Win2k) and I used the option "Copy from another partition" (thanks for the tip, it saved me a lot of time), so as to copy my hda7 (Ubuntu ext3 "/") to hda5. That was successful. I rebooted and everything worked well. I only had to edit GRUB's menu.lst, in order to boot from hda5 instead of hda7.

(NOTE: You can use Knoppix instead of Ubuntu Install CD for this. With ```
sudo parted /dev/hda
```
you can edit the partitions, and there's a menu inside of parted called "cp" -if I remember well- that is the same as "copy from another partition".)

Later, I booted from Knoppix, deleted hda6 and hda7 (old "/boot" and "/") and created a new small partiton in the end of that free space to make my new /boot partition, and then resized my hda5 all I could (Now it's near to 30GB). I did all this with QTparted, but, somewhy sometimes the disc appeared as "busy", or "readonly" and it wouldn't let me make any change. Luckily I got away with it using "sudo parted" in the terminal. It also has resize support -in fact, I found it more powerful than QTparted.

What problem did I bump into? Now that I had deleted my /boot partition, GRUB wouldn't load, and my PC would crash after BIOS check. I hadn't made a GRUB boot disk, so I had to use Knoppix to copy the backup I had made of "/boot" in hda5, copy that into the new boot partition, and re-boot. Still, that didn't work, because apparently the MBR wasn't pointing to that partition. Knoppix does not have GRUB in it's packages, so I couldn't run "grub-install /dev/hda". I booted once again the Ubuntu Install CD, marked "/" for hda5, "/boot" for hda6, and "swap" for "hda7". WITHOUT formatting. I then skipped the packages copy and jumped to the option "Install GRUB". At this point I can't remember if this really worked or not. There were some explanations on GRUB recovery in this forum. 

But take this two pieces of advice into consideration: 
1) Keep a GRUB BOOT DISKETTE. To do it, format a diskette and then
```
sudo cd /boot/grub
sudo dd if=stage1 of=/dev/fd0 bs=512 count=1
sudo dd if=stage2 of=/dev/fd0 bs=512 seek=1

```
 When you boot from this floppie, you have a command line that says "grub>". In order to boot your OS, you need to
```
root (hd0,6)
configfile /grub/menu.lst
```
(you can replace "(hd0,6)" for your actual "/boot" partition. Mine is this, maybe yours is hd0,5 or hd0,7)


2) Don't do as I did, and DON'T DELETE "/boot" partition. First I should have deleted hda7, then created a new partition in the end of that free space, "copy form another partition" /boot into that new partition, and THEN delete the old "boot" partition so as to be able to resize the root partition.


Next problem: /etc/fstab was not updated, so when I booted Ubuntu in the new partition, it couldn't mount the swap, the "boot" nor my old "ntfs". If this happens, probably you'll be prompted during the boot sequence to login as root so as to fix this. You only need to ```
nano /etc/fstab
``` and correct the mountpoints and types. If you are not sure of which device is which, use fdisk -l to list the partitions (I had to do this in my case, because the partition names were somewhy not physically ordered).


Once done this, everything worked.


My next problem was that I wanted to install W2k in my hda1 partition (where Win98SE was running) but once I finished the MS-DOS installation step (started from a dos boot disk), and re-booted, the PC would crash. I haven't found solution to this yet. It also happens when I install Win98, or Win95. Even when I do ```
fdisk /mbr
``` before installing. No idea how to solve it. We'll see the solution in another chapter :P . If you mess up your MBR, just boot from your GRUB boot disk to Ubuntu, and then ```
sudo grub-install /dev/hda
```.

Thanks for all your help, Herman, you're great!

---

### Post by Herman on 2005-12-23
Hello, foolosophy, I'm glad you were able to get all that done, it looks like you are quite capable yourself! :D
I actually did complete a How-To on the subject of re-sizing and moving ext3 partitions around with the Install CD, someone else wanted to know too.
[http://www.ubuntuforums.org/showthread.php?t=105255]("http://www.ubuntuforums.org/showthread.php?t=105255")
Right after I finished that though, I learned a lot more from azz. He's the one to pay attention to, not me. I'm learning easier ways to do these things now, you still use the installer CD, let it detect your hardware, etc, then press CTRL+ALT+F2, and run parted. Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=96694]("http://www.ubuntuforums.org/showthread.php?t=96694")
The Parted manual is here: [http://www.gnu.org/software/parted/manual/html_mono/parted.html#sec73]("http://www.gnu.org/software/parted/manual/html_mono/parted.html#sec73")
I have read the manual and I'm about to begin practicing doing some of these things to learn it better myself. It's 'dry' reading, but it is very good information.
Already the things I was thinking I knew only a week ago look a little bit silly to me, I'm going to keep on learning things and practicing though. One good idea is to watch for posts by azz and bookmark the ones you like, if you want to learn how to do things better, particularly partitioning.
Another thing I 'didn't know I didn't know' a week ago, is that we have a great 'GUI' partitioner: Gparted, that was getting mentioned often in the forums, but it took me a long time to wake up and realise they weren't talking about 'parted' in the installer, until I saw a screencap of 'Gparted' recently, and then the penny dropped. All this time I has the 'Hoary' live CD, not the 'Breezy' one with Gparted on it, so I didn't know that such a thing existed. I have the 'Breezy' live CD now, and Gparted installed in 'Breezy' also. I will be trying that out a lot in the very near future. It looks like I should just read more and learn more before posting too much. Gparted: [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")
Looks like you are already doing well. Keep up the good work, and all the best!:D
(Herman)

---

### Post by Herman on 2005-12-23
I just re-read your post once again, and it looks like you have a lot of good information there too, you are teaching me a lot. I'll try some of those things out now too, thanks! Very, very interesting...:D (Herman)

---

### Post by Herman on 2005-12-23
Thanks for your help, foolsophy! :D I used my new Breezy Live CD, and tried out that command you gave: sudo parted /dev/hda, and got into 'parted'. From there I typed 'p' for it to print out my disk geometry details.
Then, referring to the manual, I applied the 'resize' command to shrink my ext3 partition as small as practical, and used the 'move' command to shift it right up to the furthest end of the drive. I re-booted and everything's fine. Mine just has Ubuntu on one single partition, so I didn't have any GRUB problems.
That was all very easy! Your post gave me the right clues at the right time to get me started! That's a lot quicker and easier than the method I used. Thanks again, that's a good Christmas present! Now I can resize ext3 partitions, and do lots of other things much easier as well! :D (Herman)

---

### Post by foolosophy on 2005-12-24
I've been investigating what were the services started at boot time, and discovered LVM. I think I don't use LVM volumes, because I never configured that, but it seems that this service allows you to make virtual partitions in your hard drive, and then allocate free space along the way. So if you run out of space in your "/home" partition, for instance, you just make it bigger, because the free space of the disk is not allocated to any of the partitions.

Do you know anything about this?

PD: I still can't re-install windows. Probably my mbr is messed up.

---

### Post by Herman on 2005-12-24
Sorry ,but I don't understand LVM, here's a link for it though: [http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")
Maybe you'll be able to work that it out, it looks a little bit too complicated for me.

Here's a link for a blog about how to back up and restore your MBR:
[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")
I've tried that out and it seems to work just fine!

And here's a link for 'bootpart', which is a utility for copying Windows version of your MBR back temporarily until you get Windows re-installed (hopefully).
[http://www.winimage.com/bootpart.htm]("http://www.winimage.com/bootpart.htm")
I have not had time to try out bootpart yet, but it has been recommended by someone recently who used it for configuring boot.ini, and it's supposed to also be good for copying Windows version of the MBR back since 'fdisk/mbr' didn't work for you for some reason. I have downloaded it but haven't used it yet.

I hope something here helps. :D (Herman)

---

### Post by foolosophy on 2005-12-26
Surfing across the net I found a very useful software: Gpart. From a command-line you can recover your partitions if your partition table gets messed up.

[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

---

