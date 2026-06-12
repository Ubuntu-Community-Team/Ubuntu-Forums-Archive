---
title: "Really Frustrating Partitioning/GRUB/Windows Problem"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by -iLluSiON- on 2006-09-08
Okay..

Well,my first problem was stated at [http://www.ubuntuforums.org/showthread.php?t=250226](http://www.ubuntuforums.org/showthread.php?t=250226)


Now, My 2nd problem is a little bit different. After trying to install Ubuntu on both the Live Disk and the Alternate one I kept getting GRUB hd0 errors at the very end of the installation. 

I decided to rerun the partioning program in the installation.  I deleted my "DELL UTILITIES" 36MB Partition on my drive and made it unallocated.  I wanted to merge it with my other unallocated space (8GB) but I could not figre out how to do this on the partitioner (is it possible?)

So, I went to reload Windows and try the Partition Magic merge feature. Windows wouldn't load. Blue screen right after the XP logo appears.
I went to the boot disc, went to the recover console and it was all messed up.  It said my windows was on drive H: and asked for the PW. WHen I accessed it, I did the "dir" command and it was just the Windows folder.

Everything else was on the C: drive where it should be. I can't seem to figure out how to get windows back into the correct space. When I start my computer up now, it tries to load windows and then says "No PT. Press any key to continue"

Back in Ubuntu live cd, it has the 32mb unallocated(formerly the dell partition), my 30GB NTFS partition (WINDOWS SHOULD be in here) and the 8GB unallocated space afterwards.

It's all jumbled up.

IF anyone read this whole thing and thinks they know how to fix it or help, PLEASE RESPOND! I do not want to lose/reformat my drive just yet, as I still want to back some files up before I decide to do that option.

What I want:
1.) Windows to work again
2.) No files lost
3.) GRUB to somehow work so I can finally have a dual system.


I'd give money if I had some to give.

Please. Help!


Oh yeah, and the Windows installer could not recognize my "H" drive, and it says it's an <EZDRIVE> which is Maxtor if I'm not mistaken.

One other thing: I noticed in the Linux partitioner, that it had said in the past that my NTFS partition was flagged as "boot." Right now, nothing is flagged as "boot". Could this be another problem?

Cheers
- illusion

---

### Post by ollienz on 2006-09-08
Windows is (I believe) trying to boot from the second primary partition. Now that you have deleted the utilities it is trying to boot from... well, nothing really. It's generally speaking a really bad idea to delete partitions....

I'd try creating another primary partition in that dell now-empty space and see what windows thinks of that first...

---

### Post by -iLluSiON- on 2006-09-08
Bump becuase the future of my life depends on this problem being fixed

---

### Post by refactored on 2006-09-08
Mount the NTFS partition when running Ubuntu from the live CD and backup all vital files before continuing.

/refactored

---

### Post by -iLluSiON- on 2006-09-08
> **refactored said:**
> Mount the NTFS partition when running Ubuntu from the live CD and backup all vital files before continuing.

/refactored

That's another thing...

It won't let me mount it because it say's I do not have access or it's in use (on the /tmp folder)

](*,)

---

### Post by Herman on 2006-09-08
Hello, -iLluSiON-, 
It said you don't have permission eh? Well did you try to mount it in a way that will work in Ubuntu, or did you follow instructions that you found on the internet for some other Linux distribution? :D
Did you use a 'sudo' command to mount it with? :D
Here's my web page on mounting other filesystems in case it will be of any help to you, [*Click here*]("http://users.bigpond.net.au/hermanzone/p10.htm")

I hope you can at least rescue your files. Have you got an LAN?, obviously you do at least have access to another computer. 
If you have a LAN, the easiest way to rescue your files is to copy them to another computer through your network. If you need help, I can help you with that, or someone else here can if I'm slow to respond.

If you don't have a LAN set up, and you can mount your NTFS (Windows) file system alright, you might want to rescue your files and copy them to either a USB disk if you have one, or to CD or DVDs. I can help you with that too if you need it, (or anyone here).

If you don't have a USB drive you either need two CD drives, or you can install Ubuntu again, but this time if you have a Super Grub Disk ready, you do not need to have Grub installed to MBR. Just boot it with your Super Grub Disk instead. Then you can rescue your files easily because the installed version of Ubuntu will probably automatically mount your Windows file system for you, if the MBR isn't too corrupted yet. That way you will have your CD drive free for making data CDs with and you won't need a LAN. In my opinion, the best [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") at the moment is this one, [             sgd_0.9462.iso.bz2]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=82") I can help you with that too if you need it.

I can give you more specific help if I know more about what you are able to do or want to do.

I don't recommend Partition Magic for messing with partitions if you want them to be recognized by Linux. 
Use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") instead, GParted has a new version out now, GParted 0.3-1, it is very good. :D

Regards, Herman

---

### Post by -iLluSiON- on 2006-09-08
Thank you Herman. I've used your excellent site and it worked in mounting my drive. I've now backed up all my C: data (except the WINDOWS folder) on my USB HD.

Now I'm going to try a few more things to see if I can get Windows up and Running again (don't want to reinstall/reformat yet -- don't want to reset the registry yet).

I'll post what happens in my experiments.

Thanks again.

---

### Post by Herman on 2006-09-08
Okay, but if you want help, it would be possible to begin helping you if you are able to do a couple of things with the Live CD.

One would be to mount your partition again and check whether or not all your Windows boot files are there like boot.ini and ntldr, and ntdetect.com and others, as pictured in this series of illustrations, [click here]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")
I don't know anything about the dell utilities partition you deleted, but if ollienz is correct, and that's the partition your Windows needed to boot from,  your troubles might be quite severe. 
But if you have Windows boot files in your Windows partition, I  think  there still could be hope.
You can make yourself a Windows boot floppy disk according to these instructions, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").
I have tested those instructions and they worked for me, in my computer, providing I formatted the floppy disk the exact way they said. Not just any way of formatting the floppy disk worked. See if it will boot that way, it should boot. That knid of floppy disk will boot Windows when nothing else will.  If not, you might need to edit your boot.ini file in the floppy disk, (if your partition numbers were changed somehow).

And, secondly, if you need more help, please post the output from  'sudo fdisk -lu' , from a terminal in your LiveCD. That will look strange to you, but someone who knows how to read that can tell quite a bit about your situation from that and might be able to help you. (Nothing guaranteeed though). Also, please try to keep accurate notes on any error messages you may see. That can be a big help too sometimes.

Good luck with it, Regards, Herman :D

---

