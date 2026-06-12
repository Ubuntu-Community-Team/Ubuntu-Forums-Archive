---
title: "Fatal - minix not found"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by charles woodward on 2005-11-27
I've done something stupid - don't know what - but still.
Everything worked fine - but now I get message `fatal - minix not found`.  I get this in both main boot and recovery boot (I'm using grub)

Question is simple - I could completely re-install operating system - but can I bypass the routine that requires formatting/partitioning of disks - i don't want to lose what I've already got.

Is there any other solution  - linux itself seems to boot, but I don't seem to have any directories available such as /boot etc.

Any help would be appreciated.

---

### Post by bwog on 2005-11-27
I dont know if I can help you, but perhaps you could post more about your computer: partitions, filesystems, which OS is where. Maybe you have some exotic hardware specs that you want to share with us :)

Edit: I have read your post below, but I cant help you. I hope somebody else can, good luck.

---

### Post by charles woodward on 2005-11-27
Basically I have ubuntu 5.10 - it has been working perfectly since beginning of  October.

I was messing about yesterday looking at ways that I could run a couple of windows applications under Linux - unfortunately I was interrupted, and shut the system down without checking - and now the system does not boot. 

Well to be exact it does boot - it gets Linux up and running - but seems to fail on `load_modules`.  The reason it fails is that it cannot mount any of the disc partitions because it cannot find `/proc/filesystems`.  This is not surprising as the `/proc` directory is empty at this point.

I've been playing around with the `live` CD and notice that the `/proc` directory has a large number of entries in it - does this directory get regenerated every time Linux boots (I know some directories are).  

Basically I think that if I can get the `/proc` directory into good order I can work it out from there.    To be fair part of the problem is that I only have some kind of restricted shell - so I can't do things like `find` which is a great tool when you've lost something.

The full error texts are as follows:  (I'm having to do this on a windows PC  which isn't ideal)

Uncompressing Linux ... ok booting kernel
Loading :

 2 logical volumes in volume group Ubuntu now active
FATAL : Module Minix not found
mount: Mounting /dev/mapper/Ubuntu-root on /root failed - no such device
Mounting /root/dev on /dev/.static/dev failed:  no such file or directory
Mounting /dev on /root/dev failed : No such file or directory
Target filesystem does not have /sbin/init

As I say from digging around it looks like the mounts have failed because I don't have a `/proc` directory populated.

Hope this helps

---

### Post by jamyskis on 2005-11-29
Funny you should mention that, because I came into work this morning and found exactly the same thing had happened. I also tried an older kernel and that made no difference.

---

### Post by charles woodward on 2005-11-29
I  haven't been around for a while - as I had two drives I have re-installed linux on second drive (which used to have windows xp) - and I am having some problems mounting the original file system.

I have been looking at the manual entry for filesystems - and the first entry is for Minix -  it states that Minix was the filesystem used by Minix, which apparently was the first operating system to run under Linux.   It doesn't exactly help with solving the problem, but suggests to me that whatever I did corrupted the filesystem - although I have not yet confirmed this.

I am about to re-install the wireless network on my Linux box, which should allow me to be more pro-active in the near future. (i am using an old back up windows machine to file this post)  However the info above may be of help to anyone who is digging for info.

---

### Post by Topsiho on 2005-11-29
By shutting down Linux incorrectly Linux does not get a chance to save everything which needs to be saved. Usually it can at a next boot restore the information when a logging filesystem is used (ext3, Reiserfs) but there is no guarantee for this.

So you lost important information which in your case can not be restored.

/proc is a directory (and now I copy from a book for Fedora) that contains system information. The information in this directory is maintained directly by the operating system kernel.

So there you are.

You lost important information which is maintained by the kernel, and which the system can not retrieve at a reboot.

Which is bad luck and the risk of an irregular shutting down of the system.

I think you have to do a clean reinstall :(

If you do, create (if you haven't done so already) a /home partition in which come your personal files. You do not need to reformat that partition at a next install, and  so do not lose your files which are the most important on your system (though please do back these up)

I am surprised that Linux appears to contain some relics of it's predecessor, Minix (minimal unix). Linus started to create Linux because he was not satisfied with Minix. See [http://en.wikipedia.org/wiki/Minix)](http://en.wikipedia.org/wiki/Minix)).

Topsiho

---

### Post by charles woodward on 2005-11-29
I don't think I shut down the system incorrectly - I think the problem came from trying out ways of running Windows XP under Linux - combined with LVM.

I have restored the system from scratch - using the disk that used to contain Windows XP - and there are no problems.  While searching around I noticed that (somewhere) there is a suggestion that you do not use LVM to include the root directory - but I seem to remember that that was the default on the installation disc. (whenever I first install anything I use the defaults).  The suggestion is that some system software can mess up the root / boot areas if you have them in LVM.

Anyway I have restored the system, and can access my old system on the 2nd drive, and all of my data is there.  So fortunately it is not bad luck - I have lost no data whatsoever.

I knew that I had not lost anything - I did that the first time I installed a unix type system (it was Xenix - I had no manuals and it was 1984) - and I can assure you that I am very careful.  (I've installed Unix and Aix several hundred times)


Anyway I've solved the problem - but I hope that these notes may assist someone else with the same problem.:p

---

### Post by bwog on 2005-11-29
Good that you have things running again. I also had some bad luck recently: I resized the home partition and made a usr partition. I stll think that that should have worked. Anyway, reinstallation can be quicker than sorting out configuration problems with missing files (with unfamiliar names :) ).

---

### Post by austin on 2005-11-30
funny again - exactly the same problem occured on my box yesterday. And I don't run LVM. Moreover I did not shutdown in a bad way and I did no updates.

I think that doing a fresh install is not really like "problem solved".

---

### Post by charles woodward on 2005-11-30
I am inclined to agree that a fresh install does not solve the problem - but I was lucky in that I could do a fresh install on a second disc.  The main problem that I then had was accessing the original disc - which would not mount (the partition was /dev/hdb5)

After some investigation I found that it was a logical volume called `ubuntu` - if you want to know what you can do with logical volumes a starting point is `man lvm` from the command line prompt - it gives a lot of info on available commands.

To cut a long story short - I found that lvm creates a logical `item?` under dev,  in this case /dev/ubuntu - and under this the partitions within the logical volume are listed.  So whatt I had to do to get the data back was :

  mount -t ext3 /dev/ubuntu/root /old-system   

(ext3 was the partition file type - old-system is the mount point I created).

I had already re-installed Mozilla firefox and thunderbird - so all I had to do to get my email and web preferences back was to move the original files into  place - the command was :

 mv /old-system/home/username/.mozilla ~/
mv /old-system/home/username/.mozilla-thunderbird ~/

I still have some files and systems I have to recover, but all my emails are there, and all of my bookmarks - you really don't know how happy that made me.

I know it won't help everybody but it may help someone.  Also if you load either the Live CD or Install CD  you can get to a shell prompt (take expert boot option on Install) and you can check your hard disk - you never know you may be able to rescue something .:cool:

---

### Post by austin on 2005-11-30
Well, accessing my data from other systems is no problem, but I'd like my system back ...

jamyskis: do you have lvm?

---

### Post by austin on 2005-11-30
people that discuss backing up linux systems recommend not to backup /proc, e. g. here:

[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

That makes me think that an empty /proc is not the cause of the problem. I still wonder where to begin. The "mount failed" is strange, because the "uncompressing linux ok" makes me think that the kernel (that lies on that partition) has been read.

And: why should I need a minix module?

---

### Post by azumafuji on 2006-01-19
I just wanted to post that I have experienced the same problem.  I didn't do anything out of the ordinary on my laptop, but Ubuntu will no longer boot.  I'm getting the same error, "FATAL: Module minix not found.",  and I'm dumped to a shell prompt (busybox).  I booted up with an Ubuntu live CD and poked around a little, reinstalled grub, but no luck.  Also, I couldn't find anything wrong with the disks or partitions.  Everything checked out OK.  

This is a little disturbing as I'm using this machine for work.  I didn't lose any data, but the time to fix this is killing me.  Other than this problem, I love Ubuntu.

---

### Post by jimkim on 2006-02-02
Hi everyone,

I'm new to Ubuntu (kubuntu, 5.10) and encountered exactly the same problem after changing the KDE screen resolution. Normal shutdown, reboot impossible. Started the system with a linux live cd (knoppix), hd was ok and mountable. I then went through the directories, cd to /root and by chance found two files, @.DCOPserver_ubuntu__0 and .DCOPserver_ubuntu__0; the first was unreadable. I deleted the first file (@.DCOP*), rebooted, and - everything was ok! Don't know the reason why, but who cares? Maybe someone knows or this can be of some help...

jimkim

---

### Post by dwkreutzer on 2006-02-09
I also had this problem.  My neighbor (who seems to know everything about all operating systems) suggested loading an older kernel.  During the boot process there is an opportunity to choose a different GRUB by hitting esc.  The window of opportunity is about 3 seconds.

I loaded the next newest version and it didn't work any better, but when I tried the third newest (also my oldest) it worked fine.

---

### Post by FuzzyUnicorn on 2006-03-01
I've been running Ubuntu on my laptop for the last few months, and absolutely loved it.  It is the first Linux I've tried that worked right out of the box. Until this morning that is... I started it up this morning and got this Fatal: minix not found error.  I shut it down propperly last night, so I have no idea why it happened.  I didn't install any updates or change any settings.

I searched the forum and found this thread, but none of the suggestions helped.  It seemed that the only thing most of the systems having this problem had in common was a corrupt file of some sort.  I looked around, but couldn't figure out which file might be corrupt.  I decided to try every command this minimal shell had available, and magically it started working again.

I'm not sure which commands I did caused the system to start working again, but I will list them incase they can help someone else:
mount -t ext3 /dev/hda2 /root (my Ubuntu is on hda2, WinXP on hda1)
cp /root/vmlinuz.old /root/boot 
cp /root/initrd.img /root/boot (as suggested in a page I found on Google)
run-init /root /sbin/init 1
after the last command, ls and every other command stopped working.  I rebooted, and Ubuntu started working again.

I really love Ubuntu, and I'm glad to have my system running again.  But if a system can go down like this for no apparent reason, there's a lot of work to be done in crash prevention.  Even if the computer was shut down impropperly (which it wasn't) it shouldn't take the whole system with it.  Impropper shutdown are going to happen in real life (power outages, battery failure, system freeze requiring a hard reset)  We need to build some sort of mechanism that lets the system boot, even if important files get corrupted.

Ok, I think this is getting a little long for my first post.  I hope it helps someone if they find themselves in the same position I was.

Chris

---

### Post by sandok on 2006-03-02
I've the same problem. I'll try what you have said. 
I´m surprised that there is not an "official" explanation of this.
If anybody discovers anything, please tell me. :)

---

### Post by Zelut on 2006-03-17
I've got this same issue on  a machine I'm working on.  I've tried 'grub-install /dev/hda & /dev/hda1' but none of those solve the issue.

I suppose I could re-install Ubuntu on the machine but that really doesn't solve it or tell me what caused it.

---

### Post by oneth on 2006-03-27
Clean shutdown last night and same error on startupd. None of my grub entries booted.

[QUOTE=FuzzyUnicorn]I'm not sure which commands I did caused the system to start working again, but I will list them incase they can help someone else:
mount -t ext3 /dev/hda2 /root (my Ubuntu is on hda2, WinXP on hda1)
cp /root/vmlinuz.old /root/boot 
cp /root/initrd.img /root/boot (as suggested in a page I found on Google)
run-init /root /sbin/init 1
after the last command, ls and every other command stopped working.  I rebooted, and Ubuntu started working again.[/QUOTE]

I checked (booting with a live cd that partition were correct and no important file was modified on last night shutdown.

I mounted ubuntu partition by hand (mount -t ext3...) and rebooted (without doing anything else) and it started without problems :)

---

### Post by Ulf Karlsson on 2006-03-31
My friend just got this problem and I figured out what the cause was. Basically you just need to create a new file and you will be OK (until you have bad luck next time). I reported this to the bug tracker:

In the fstype tool there is a problem if the lower 16 bit of number of free inodes in a ext3 filesystem happens to match minix filesystem magic.

This will cause the system not to boot since ubuntu will attempt to mount the filesystem as a minix filesystem.

This problem has been discussed before, but the cause was never investigated, e.g.:

[http://www.ubuntuforums.org/archive/index.php/t-95729.html](http://www.ubuntuforums.org/archive/index.php/t-95729.html)

Stupid workaround:

mount /dev/sda1 /root
touch /root/newfile
sync

---

### Post by Topsiho on 2006-05-14
I replied in this topic before, and now am a victim myself!!

Recently one day my computer refused to start up completely, telling me that it couldn't find minix and giving me a root-prompt and some commands available to me, none of which made any sense to me.

I ended up installing Ubuntu again on my computer, making sure I did not erase my /home partition.

I then discovered that some maps were intact, and some completely lost.
My mailboxes (KMail) had disappeared, exept that my inbox now contained some messages I had recently deleted and so were in the how do you call it, the wastebasket.

I thought my hard disk was about to give it's pipe to Maarten, as we Dutch say, but after rereading this topic I think it might be still going strong :)

It's sad that Linux (or Ubuntu?) is not yet as stable as it [is said,ought] to be.

I have copied the solution of Ulf Karlsson's but it's to late to try it out now...

Topsiho

---

### Post by tabletopJunkie on 2006-10-08
With the information fuzzyunicorn gave, I was able to get the information on /root (mount -t ext3...)
With the fix she offered it did not work with my system, however on the same train of thought, /root had an initrd.img.old which i renamed to initrd.img (mv initrd.img.old initrd.img)
reset the system and it worked out fine.

Cause??? something happened to the initrd.img.
I am new to Linux and don't know that much about it.

---

