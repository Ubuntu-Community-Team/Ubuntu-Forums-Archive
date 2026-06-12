---
title: "Roms &quot;cd/dvd&quot; stop read'n after installation"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by cowboy.squeeze on 2010-07-26
I donate my time for an organization that rebuilds old discarded PC's from either person upgrading or replace due to PC failure and business for same reason. At one time we used to load Windows XP as the OS. Due to licensing problems we have started loading Ubuntu 10 as the OS. We have noticed an increasing amount of rom's that after installing Ubuntu 10 the rom's stop reading installation disc, data and music disc. We never experienced this problem when we installed Win XP. We have for a couple of PC's reinstalled XP over Unbuntu to see if rom's are bad,and after installation roms played all types of disc.**[SIZE=2][COLOR=Red] My question is why or what is causing such an increasing amount of roms "cd/dvd" to stop working after installation of Ubuntu and what can we do to correct this problem?[/COLOR][/SIZE]** We realize there are some that were bad and didn't work even under XP installation that didn't work even from the beginning of installation those we replaced then stopped working after Ubuntu installation. Thanking you in advance for any help anyone can provide.

---

### Post by dv3500ea on 2010-07-26
What type of CD/DVD ROMs are they? (Software, Music, Video?)
When you insert a disk, a disk icon should appear on the desktop does this happen?
Note that Windows Software CDs probably won't be installable on Ubuntu.
Also, you need to install extra software to play some commercial video DVDs.

---

### Post by cowboy.squeeze on 2010-07-26
[dv3500ea]("http://ubuntuforums.org/member.php?u=906606") thank you for your reply but you need to re-read my post. I mentioned all types of disc fail to be read under ubuntu after installation. Rom reads during install but fails to read ANY DISC after installation including installation disc used to install. The same PC we have installed win xp rom reads same type of disc without a problem after installation.  You don't need to load extra software to read or play any of the type of disc mention. Unbuntu comes with preloaded video, music software and with open office preloaded as we have selected it will open any MSO type file etc.

---

### Post by dv3500ea on 2010-07-26
What exactly do you mean by fails to read?
What happens when you insert a disk?
Can you go to Places -> Computer -> CD/DVD drive and browse the content?

---

### Post by cowboy.squeeze on 2010-07-26
Thank you for your reply but all other please read. I doesn't read it, just what fail means, "FAILS TO READ". If you put a disc in a rom be it CD/DVD it should ask what you want to do with it, if its music you should get Rhythmbox asking if you want to play it. If rom fails to read you don't get anything at least for most cases.

---

### Post by dv3500ea on 2010-07-26
Have you tried going to Places -> Computer -> CD/DVD?
Do you get any error messages?
What happens (after entering disk) if you go to Applications -> Accessories -> Terminal and enter:
```

sudo mount /dev/cdrom /media/cdrom

```?

---

### Post by cowboy.squeeze on 2010-07-26
Thank you again [dv3500ea]("http://ubuntuforums.org/member.php?u=906606") for your input,  but after reading your replies you truly haven't read what I wrote  in my original message explaining problem. If I got an error I would have said so what I wrote and explained is what happens nothing more nothing less. I also take it from your reply's you're shooting in the dark about how to solve my problem or at least have a better understand as to why when a rom fails after installation of Ubuntu and why if I reload win xp they don't and am able to read cd/dvd according to rom type. Now I'm sure that it has to do with the drives of the rom drive, but since I don't know where one can load drivers separately like under windows is why I'm confused. Am sure there is a simple solution to fix this, but not having me go here, go there. When I said rom doesn't read the disc I'm not kidding.

---

### Post by dv3500ea on 2010-07-26
If you don't answer the questions, it makes it very difficult to help you. I'm trying to get information that could help me, or someone else, to solve your problem. It may be that I don't have a solution but I'm going through some simple steps to see if there is a simple solution. What I am trying to establish is whether the disks are being mounted at all.

---

### Post by cowboy.squeeze on 2010-07-26
I did answer that question many times your refusing to read it or ignore it. that why I said reread what I wrote. Matter fact in the last reply I answered it. Again where I said if I reinstall windows over top of ubuntu rom works fine! Some drivers are not loading when ubuntu is installed rom. I've even reinstalled ubuntu in hopes that re-istall will fix but doesn't.

---

### Post by dv3500ea on 2010-07-26
You have answered that there are no error messages, fine. I have asked a number of questions - could you possibly answer the unanswered ones? I have reread what you wrote but I haven't gained any more information from that. That is why I have asked questions.

---

### Post by cowboy.squeeze on 2010-07-26
The only simple step I want to go to that makes any logical sense is where can one see what drivers are loaded, just like in Windows for each peace of hardware installed on PC. With in windows you have options for each peace of hardware to uninstall , reinstall Etc. I don't know where those feature are hiding in Ubuntu. As for me go to program apps type stuff have been there done that also.  Ubuntu's equivalent to windows explore I've done also and it show a disc but nothing is there showing on disc other then disc inserted in rom drive. I have a question for you dv3500ea how many years have you been playing, repairing, etc with computers and to be specific ubuntu "linux"? thank you

---

### Post by dv3500ea on 2010-07-26
Linux tends not to have 'drivers'. Instead, everything is handled by the kernal - including optical disk drives. CDs/DVDs *should* be supported out of the box.

From what you have said, it sounds like the disk is being mounted but the files aren't showing up. To clarify, could you please post the output of the command I gave earlier?

I have been using Linux + Ubuntu for 1 year now and before that I used Windows (mainly XP) ever since I was very young, though I'm not sure of the relevance of this question.

---

### Post by cowboy.squeeze on 2010-07-26
I won't be able to run "sudo mount /dev/cdrom /media/cdrom" till this 
Friday and if I come across one of the PC's that has a rom that will install
Ubuntu from installation disc but not read it after installation or any other
disc say mp3 type.

---

### Post by dv3500ea on 2010-08-03
There is a thread with a similar problem here:
[http://ubuntuforums.org/showthread.php?t=1544152]("http://ubuntuforums.org/showthread.php?t=1544152")

---

### Post by robert shearer on 2010-08-03
Using the Menus...

**1)** System=>Administration=>Synaptic Package manager

a)Settings (top)=>Repositories=>Ubuntu software then make sure the first 4 boxes are ticked.
Next tab 'Other Software' tick the first box. close that window.

b) 'Reload' (top left)

c) in the 'quick search' box type **Ubuntu-restricted-extras**

When it is found then right click on that line and select 'Mark for installation' then apply and install all the packages it marks (tick 'mark' and it will download and install them in one hit.

**2)**Places=>Home folder=>Edit (at the top) =>Preferences=>Media
  and configure as required.

**3)** Reboot and media should load.

Note that we ask questions and output from terminal commands so we can better diagnose and help.
It helps us to help **you** when you supply that info.

Forum members are all volunteers just like you.

Some reading may help, 
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by anivegmin on 2010-08-03
Similar problem here.

Although quite often the cd drive and dvd drive will both mount discs immediately after booting the system. But then after some random length of time they will either unmount or wont mount a newly inserted disc.

As I write this post both my drives are inaccessible.

sudo mount /dev/cdrom /media/cdrom

mount: mount point /media/cdrom does not exist

Both drives are listed in Disk Utility -

TSSTcorp CDRW/DVD TSH492B
HL-DT-ST CD-RW GCE-8320B

Both drives work fine with Windows XP.

I have had this problem since installing 10.04 in April. I have posted on various threads on this forum and still not solved it.

---

### Post by robert shearer on 2010-08-03
What is the physical connection set-up ie do they share a cable, or if on separate cables are they masters or slaves ?.

What cables, ide, sata, or combination ?.

Are there sata hard drives present with ide drives ?.

can you run 
```
sudo lshw
```
save as a text file then right click on it and compress with Create Archive before posting it with Manage Attachments.

---

### Post by anivegmin on 2010-08-05
Sorry to butt in on this thread again but I have solved my long standing CD/DVD drive mounting problems.

A while back on another thread someone suggested installing the latest kernel (2.6.34). I tried this but no luck.

Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. This has solved my mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

---

