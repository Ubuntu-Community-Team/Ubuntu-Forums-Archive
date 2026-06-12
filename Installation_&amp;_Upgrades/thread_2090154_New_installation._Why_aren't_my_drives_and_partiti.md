---
title: "New installation. Why aren't my drives and partitions available"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2012-12-01
Hi!  I just installed 12.04LTS.  My machine has multiple problems.  

1. Neither of my DVD R/W drives appear on the desktop, in the launcher, or in the file manager when I put media in them.   Where are they supposed to appear?    I know the drives are physically recognized, because if I put a video in either drive, and run the VLC media player, I can open the disk by selecting /dev/dvd1 or /dev/dvd2.

2.  Where are my thumb drives?  They don't appear anywhere either.    

Any assistance with this is appreciated.

---

### Post by dino99 on 2012-12-01
which kind of session are you using ? (unity/shell/gnome-classic/other)
which kind of installation ? (real or wubi)
which ubuntu ? (32/64 k/x/lubuntu)
which format ? (ext3/4 raid lvm)

that said, you can set your preferences via mount/disk-utility/fstab/dconf

---

### Post by Engineeringtech on 2012-12-01
> **dino99 said:**
> which kind of session are you using ? (unity/shell/gnome-classic/other)
which kind of installation ? (real or wubi)
which ubuntu ? (32/64 k/x/lubuntu)
which format ? (ext3/4 raid lvm)

that said, you can set your preferences via mount/disk-utility/fstab/dconf

Unity I guess.  The way the installer did it.      I don't even know how I would go about changing the shell. 

Real or wubi?  If you're asking if I'm running under Windows, NO.  

32 bit ubuntu 12.04LTS

Installation was to a EXT4 partition.  This is a multi-boot system.  Although I have not used Windows in over a year.  (XP broke.  Part of my motivation on going with Ubuntu.)

I'd send you a screenshot of my partitions as shown in GParted, but I don't know how to attach a picture here.

---

### Post by Bucky Ball on 2012-12-01
> **Engineeringtech said:**
> I'd send you a screenshot of my partitions as shown in GParted, but I don't know how to attach a picture here.

Click 'Go Advanced' when creating a post and you will find the paperclip icon for attachments there. ;)

---

### Post by SeijiSensei on 2012-12-02
> **Engineeringtech said:**
> 1. Where are [my DVD R/W drives] supposed to appear?

2.  Where are my thumb drives?  They don't appear anywhere either.

Usually they are all under /media.  Sometimes the thumb drive will appear as a serial number.

I don't think an empty DVD drive will appear anywhere.  Linux usually only pays attention to mounted filesystems.  I use KDE rather than Unity, and I only see my drive when it has a non-blank disk in it.  I can see a blank disc from within the burning program, K3b, but not from the file manager Dolphin.

---

### Post by Engineeringtech on 2012-12-03
> **Bucky Ball said:**
> Click 'Go Advanced' when creating a post and you will find the paperclip icon for attachments there. ;)

Thanks.  Here is screenshot of my partitions.

---

### Post by Engineeringtech on 2012-12-03
> **SeijiSensei said:**
> Usually they are all under /media.  Sometimes the thumb drive will appear as a serial number.

I don't think an empty DVD drive will appear anywhere.  Linux usually only pays attention to mounted filesystems.  I use KDE rather than Unity, and I only see my drive when it has a non-blank disk in it.  I can see a blank disc from within the burning program, K3b, but not from the file manager Dolphin.


Thre is a folder under /media called CDROM.   Nothing for a DVD R/W drive.   CDROM always has zero items in it, no matter what I put in either of my DVD drives.      I have no doubt the drives are hooked up  properly and communicationg, as I can put a movie in either drive, and play it with VLC media player by opening /dev/dvd1 or /dev/dvd2 from within VLC. 

I don't care if an empty DVD drive appears.  I just want to be able to see / access my data, and audio CD's and DVD's.   when I put media into the drives.  The same is true with my USB drives.  I'd like to be able to read the data on them.

---

### Post by Engineeringtech on 2012-12-29
I have marked this case as SOLVED.   In case you're wondering, my solution is gong to be to stop using Ubuntu and go back to Windows!  

The reason I installed Linux in the first place, was I was sick of Window's "Automatic Updates" failing, or damaging the OS or my applications.  I was sick of Microsoft forcing me to upgrade (Win 98 to 2000 to XP ) - especially since these upgrades only made my machines slower and less productive.     Each week brought new security bugs.  If I wasn't constantly on alert, my antivirus protection would fail and my machine would be compromised.  I spent more time patching and repairing Windows than I did USING the system.   (But at least all my drives and partitions were usable.  At least if I wanted to find the data I created last week, my partition was right there.  If I wanted to backup my machine, I had an optical drive or external drive to do it with.)

I finally tried Linux - Ubuntu 9.04!     Initially,  I thought it was great!   My system multibooted.    I could use Ubuntu to safely browse the net, or reboot into Windows and do my CAD work.   Ubuntu was fast, and I had  no hassle with viruses.   My drive partitions, optical drives, thumb drives, and USB and Firewire devices still worked.    

Then after a few months a popup message from the update manager announced that I had to upgrade to a newer version of Ubuntu, or the security updates would stop coming.   So I reluctantly upgraded.   The upgrade went smoothly, and without error messages, but my machine became unbootable!   

I borrowed another machine, and found this forum.   I was deluged with advice on updating and reinstalling GRUB.  Some  members  insisted I had done something wrong with the installation.   They didn't like the idea that I was still using the Windows boot manager.    (I soon eliminated that.)     I couldn't follow everyone's advice at the same time, so I focused on the advice of one or two forum members.    And some people got pissed off at me for that.  (The majority of forum members were very patient ).     I was entering cryptic commands into the terminal.  Things I didn't understand.   They didn't work.     Nor did re-partitioning, reformatting, and reinstalling Ubuntu from scratch.    I can't tell you how many times I did that!     Some people got impatient with me, because they didn't understand that this stuff took a lot of time.    I was dealing with health problems and work problems, and I rarely had a backup machine to communicate with while doing the changes.    I complicated the problem by opening a new thread whenever an open thread seemed to "go dry".  

I was told my hardware was defective.   So I got new drives and a new hard drive controller.  Eventually, I even replaced the motherboard.    Yet well over a year after my forced upgrade, I was still looking at a black screen and flashing cursor.  My $2400 hardware was about as useful as a boat anchor without a rope.   THAT GETS OLD!    I stopped trying to fix it.    I ignored the box.

Then one day, I went back to the boat anchor, and tried a tool called "Boot repair".  And behold, I got a bootable computer.    But where were my data partitions, thumb and external drives?   How come they wouldn't mount?  Why didn't the media I put in either optical drive mount?   What good is a computer if you can't save anything?  The IRS and state tax office wanted me to do my returns on my computer.   Yeah right....    I returned to this forum and listened to more advice, I was instructed to "reformat and reinstall". 

GRUB is currently allowing me to boot into either OS.  But only Windows is accessing my drive partitions and optical drives.   So which system do you think I'm going to use?    I don't like my "solution",  but it's the only way I will keep my sanity.  I may use Ubuntu from time to time to browse the net, or when Windows acts up, but I'm not going to keep any important data on it. 

Anyway, you might think I don't appreciate the efforts of the people who tried to help me.  You'd be wrong!   I do.    So THANK YOU.     I also apologize for opening so many threads on what basically was the same issue. 

Before I leave this forum, I'm going to try and find  my other posts and mark them "solved".   I know people don't like it when the threads are open forever.

Again, I am sorry if I wasted the time of people here.  I really wanted this to work.

---

### Post by ronparent on 2012-12-29
I am so sorry to hear your frustrations. Even worse, your complaints are probably valid! I myself have literally spent weeks over a period of years trying to sort out my own particular set of problems. If the developers get it right for one release I often see it regress by the next. 

Unfortunately you need to learn many explicit linux processes to be completely comfortable using Ubuntu (or any other linux distro). The community labors hard to find and remove any OS glitches, but, some of us are still left hanging. I am old and retired myself and am often able to lavish the time and effort to work things out but even at that I can't commit to depend of an often quirky work environment.

In that respect MS doesn't get enough credit for what they do get right. They do have the advantage of having most of the hardware designers catering to making their systems so that they will work with Windows. Also beginning with Win7, Win7 & 8 will automatically report back any glitches detected and eventually fix them (my experience). In any event each and every system will have problems sooner or later regardless of your OS.

I can sympathize with your frustration and with some regret agree with your decision to fall back on Windows. Be assured you have not been wasting the communities time. Getting any Linux distribution to work reliably is an ongoing learning exercise and input from all users contributes to the ultimate success of the community. Go with our best wishes and know that you would be welcome back anytime!

---

### Post by oldos2er on 2012-12-29
> **Engineeringtech said:**
> Before I leave this forum, I'm going to try and find  my other posts and mark them "solved".   I know people don't like it when the threads are open forever.


Going back to Windows isn't a solution, although it worked for you. Marking a thread 'Solved' is a flag to others having the same problem, who're looking for help with Ubuntu and don't necessarily want to have to install Windows to solve their problem.

That said, I'm sorry you had so many problems. If you wish to try Ubuntu in the future, I'd suggest you stick with LTS versions; fewer upgrades, hence fewer potential upgrade problems. Good luck to you whichever OS you're running.

---

### Post by Bucky Ball on 2012-12-30
> **oldos2er said:**
> ... If you wish to try ubuntu in the future, i'd suggest you stick with lts versions; fewer upgrades, hence fewer potential upgrade problems. 

+1

---

