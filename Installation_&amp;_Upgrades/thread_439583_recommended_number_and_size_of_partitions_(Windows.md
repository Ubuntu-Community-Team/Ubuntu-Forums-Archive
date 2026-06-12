---
title: "recommended number and size of partitions? (Windows dual boot)"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Finch75 on 2007-05-10
Hello everybody,

I have read a lot of howtos and documentation, but I haven't found any "recommendations" for number and size of partitions. The only thing I've seen so far is "at least 10 GB for Ubuntu". Ok, but... only one partition?!

For Windows, I've usually created at least four partitions:
1) System partitions
2) partition for swap file and temp folders
3) applications
4) my precious data :-)

How does that translate to Ubuntu? I think there MUST (?) be a swap partition, but apart from that?
I've read "somewhere" that putting your /home on a separate partition is a good idea in case you need to reinstall - that makes sense for the same reasons it did in Windows... ok. Does it make sense to put applications on a separate partition? (if so, how do I do it?) The idea is to make "system backups" faster (and smaller) and also to keep some application settings in case I have to reformat the system partition. Where are all the applications installed by default? /etc?
What do you think about that? How large should the partitions be? I need to install "lots" of stuff...

Now to make things even more complicated, I want to dual-boot with Windows. And share data.
Is NTFS write access "safe"?!

So what does that mean in combination?
1) primary: Windows
2) primary: swap/temp Windows (close to system partition for faster seek times)
3) primary: Ubuntu
4) extended:
4a) Ubuntu swap (close to Ubuntu system partition for faster seek times)
4b) Ubuntu applications (???)
4c) Windows applications
4d) data partition (NTFS)
4e) Ubuntu /home (ext3)
4f) FAT32????! Or I could just make #2 a FAT32...

Uhh... doesn't look like too much fun...

What do you think?! :confused:

---

### Post by starcraft.man on 2007-05-10
> **Finch75 said:**
> 

So what does that mean in combination?
1) primary: Windows
2) primary: swap/temp Windows (close to system partition for faster seek times)
3) primary: Ubuntu
4) extended:
4a) Ubuntu swap (close to Ubuntu system partition for faster seek times)
4b) Ubuntu applications (???)
4c) Windows applications
4d) data partition (NTFS)
4e) Ubuntu /home (ext3)
4f) FAT32????! Or I could just make #2 a FAT32...

Uhh... doesn't look like too much fun...

What do you think?! :confused:

HOLY COW!!!!!!!!!!!!!!!!!!

Thats a lot of partitions, don't do all that. REALLY!!!! Thats just a mess.

Ok, your first three are right. You would have...

1) Windows partition
2) swap - at your discretion, I've never done this... I can't vouch as to significant speed improvements, you may consider removing it if you must have another partition from your 4 list.
3) Ubuntu - This is your root directory (mounted to /, all of your OS and applications should be here)
4a) swap partition for ubuntu here is fine.
4b) Forget ubuntu applications and put them in 3 (a total Ubuntu install is less than 4 GB, and I don't think theres any speed boost to separating your programs in Ubuntu.
4c) Uh, I have actually done this, I guess you can keep that since moving windows programs is a pain with registry.
4d) Data: In your case, you don't have the ability to make any more partitions past this one (i always forget if its 3 or 4 extendeds), so I guess your best bet is to use your NTFS partition as your data folder and share it between Ubuntu and Windows. The ntfs-3g drivers for Ubuntu are stable now and acceptable for writing to NTFS partitions.

If you remove one of the above, make the /home partition. Thats all you really need I guess. You got a very partitioned set up just for that one disk. You do know that internal HDDs are cheap? You could get a 40GB/80 internal drive cheap just for ubuntu, might be a good solution

Most users don't have a swap/seperate application for windows, you might consider getting an external drive since your really out of space on that HDD, I use one for all my data so i can take it on the go.

Hope that helps.

---

### Post by rsambuca on 2007-05-10
Wow - I think I agree with starcraft.man here.  That looks unnecessarily complex to me.  I have six different OS's on my rig and it doesn't look as confusing as yours!!!

Anyways, here is a [[COLOR="Red"]link[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning") to a decent guide to start you off on what you require for partitioning a dual boot system.

---

### Post by starcraft.man on 2007-05-10
> **rsambuca said:**
> Wow - I think I agree with starcraft.man here.  That looks unnecessarily complex to me.  I have six different OS's on my rig and it doesn't look as confusing as yours!!!

Anyways, here is a [[COLOR="Red"]link[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning") to a decent guide to start you off on what you require for partitioning a dual boot system.

YAY!!! HI rsambuca, ANOTHER CANADIAN!!! Good to see another person from maple country :D

Another recruit for the great Canadian Linux army :p

---

### Post by stmiller on 2007-05-10
> **Finch75 said:**
> Hello everybody,

I have read a lot of howtos and documentation, but I haven't found any "recommendations" for number and size of partitions. The only thing I've seen so far is "at least 10 GB for Ubuntu". Ok, but... only one partition?!

For Windows, I've usually created at least four partitions:
1) System partitions
2) partition for swap file and temp folders
3) applications
4) my precious data :-)

How does that translate to Ubuntu? I think there MUST (?) be a swap partition, but apart from that?
I've read "somewhere" that putting your /home on a separate partition is a good idea in case you need to reinstall - that makes sense for the same reasons it did in Windows... ok. Does it make sense to put applications on a separate partition? (if so, how do I do it?) The idea is to make "system backups" faster (and smaller) and also to keep some application settings in case I have to reformat the system partition. Where are all the applications installed by default? /etc?
What do you think about that? How large should the partitions be? I need to install "lots" of stuff...

Now to make things even more complicated, I want to dual-boot with Windows. And share data.
Is NTFS write access "safe"?!

So what does that mean in combination?
1) primary: Windows
2) primary: swap/temp Windows (close to system partition for faster seek times)
3) primary: Ubuntu
4) extended:
4a) Ubuntu swap (close to Ubuntu system partition for faster seek times)
4b) Ubuntu applications (???)
4c) Windows applications
4d) data partition (NTFS)
4e) Ubuntu /home (ext3)
4f) FAT32????! Or I could just make #2 a FAT32...

Uhh... doesn't look like too much fun...

What do you think?! :confused:

I think you also need about 5 HFS+ partitions, 3 more NTFS partitions, and a couple of Reiser partitions for good measure.

---

### Post by Finch75 on 2007-05-11
Hi starcraft.man,

thanks a lot for your answer ;-) Some comments and a few more questions:

> **starcraft.man said:**
> HOLY COW!!!!!!!!!!!!!!!!!!

Thats a lot of partitions, don't do all that. REALLY!!!! Thats just a mess.

Well, I think it looks worse than it is. It's actually just two OSes with 4 partitions each. By default (with very very rare exceptions), Windows wouldn't have any need to "see" the Ubuntu root, swap and application partition and Ubuntu wouldn't have any need to "see" the Windows system, temp and application partition. So "whereever I am" (Windows or Ubuntu), I'd only see four (or five) partitions and would really only care about one (data) or two (data + shared data?) of them... That's not tooo bad...

> **stmiller said:**
> I think you also need about 5 HFS+ partitions, 3 more NTFS partitions, and a couple of Reiser partitions for good measure.

ok, thanks for the hint. I'll have those on my additional hard disks.
;-)

> **starcraft.man said:**
> Ok, your first three are right. You would have...

1) Windows partition
2) swap - at your discretion, I've never done this... I can't vouch as to significant speed improvements, you may consider removing it if you must have another partition from your 4 list.

Yeah, that was my top candidate (for removal) as well. The main point was reducing fragmentation in the long term, because there's a lot of repeated and small read/write/delete both in the temp files and in the swap file. It also gave me a very easy way to see the total size of "temp stuff" and an easier way of removing all of it. However, there's probably no real impact of *not* having that partition any more. It's also a leftover from times when disks had speeds of 3 MB/s and avg. seek times of 50 ms.
It's probably not an issue any more today, my system speed is just fine overall ;-)

> **starcraft.man said:**
> 
In your case, you don't have the ability to make any more partitions past this one (i always forget if its 3 or 4 extendeds)

oh, sorry, take a look at the numbering: 1-3 are three primary partitons, 4 is ONE extended partitions with logical volumes in it. Is there any reason this is not possible? Can the Linux swap partition be a logical volume or does it HAVE to be a primary partition? If not, my setup would be possible.

> **starcraft.man said:**
> 
3) Ubuntu - This is your root directory (mounted to /, all of your OS and applications should be here)
4a) swap partition for ubuntu here is fine.
4b) Forget ubuntu applications and put them in 3 (a total Ubuntu install is less than 4 GB, and I don't think theres any speed boost to separating your programs in Ubuntu.

ok.
I've never used Linux (except from ssh logins to servers) so far and I might be applying some "Windows workarounds" to Linux although they are not necessary?
Let me explain, though: In Windows, you cannot easily copy the system partition for several reasons: locked files, file permissions, boot sector, ... That's why I regularly make a system backup with Acronis TrueImage and it works GREAT. I just wanna keep that image small so I can make and restore it quickly.
As a matter of fact, I've been using Windows since 1991 and Windows NT/XP since 1997 and it's only since I've started using that system that I'm not in constant fear of a system crash (corruption) ;-)
I actually have two Windows installations and can switch between them. They share the data partition and I have different desktop colors to tell me which one I'm using because I wouldn't otherwise see a difference right after cloning :-) :-) :-)

If anything goes wrong, I can reinstall my complete Windows installation within 20 minutes! And that's a Windows installation that took about two days (full (!) days!) to do initially. Among others, I use it for
software development: Java 1.4, Java 5, Java 6, Eclipse, JBuilder, Tomcat 5, 5.5, 6, Borland Delphi, MySQL with several administration tools
remote access: VNC (client + server), SSH (server), OpenVPN (server) and all the other ssh/ftp stuff
servers: Apache, subversion, Tomcat
communication: fax machine, answering maching (phone)
media: Hauppauge PVR-350 and lots of related software (and of course about 2 TB of video files on some additional disks *g*), music library: I've grabbed > 500 CDs in the last 10 years and got some stuff from personal friends ;-)
oh - and some other "standard stuff" (office, browser, email, scanner, image editing...) of course ;-)

ok, I digress. Of course this is not *directly* related to the partitioning question, but I guess I need a bit more of a system for organizing things than the standard Windows user. I know where my "important stuff" is and I do make regular backups.
You can probably imagine that I was really worried about switching some of it to Ubuntu. After some experiments last weekend, I was really thrilled. I really hadn't expected to see the PVR-350 MPG2 capture card work "out of the box". Amazing. The fax and answering machine will actually be the trickiest part. There are official drivers for my ISDN card (yay! wow!), but apparently no software that does what I'm looking for... I actually think Feisty is the first Ubuntu that I can possibly use and of course I'll try that ;-)



> **starcraft.man said:**
> 
> (application partition for Windows)
4c) Uh, I have actually done this, I guess you can keep that since moving windows programs is a pain with registry.

Yes. Actually you could say it's close to impossible for some programs. 

> **starcraft.man said:**
> 
4d) Data: In your case, you don't have the ability to make any more partitions past this one 

I think I do. Am I missing something?

> **starcraft.man said:**
> 
so I guess your best bet is to use your NTFS partition as your data folder and share it between Ubuntu and Windows. The ntfs-3g drivers for Ubuntu are stable now and acceptable for writing to NTFS partitions.

I sure hope so. I'm a little bit scared because the entire web is full of warnings :-(
Now I do realize what a version of 1.0 means in the Unix/open source world, but still... It's been released when? Not even three months ago. Very first appearance 10 months ago? Hmm... I like to be optimistic, but a corrupted partition would be really really bad!


> **starcraft.man said:**
> 
If you remove one of the above, make the /home partition. Thats all you really need I guess. You got a very partitioned set up just for that one disk. You do know that internal HDDs are cheap? You could get a 40GB/80 internal drive cheap just for ubuntu, might be a good solution

I'll consider that. I actually do have *several* drives here ;-) I think I've broken 3 TB ;-)
The main thinking is different: The PC is in my room (yeah, just one room (+bathroom + kitchen + hallway), Munich is such an expensive place to live *sigh*). Nevertheless, it's almost "always on" for the answering machine, the PVR and sometimes the web server. I want to keep that as silent as possible and I have one hard disk that's really not audible at all. It's incredible - even when it's right in front of you on the table, you cannot really tell if it's running without touching it. It's also almost 5° C cooler than any of my other drives (two of them are the same model!). I just really like that one! ;-) I have my drives spin down when not in use (except for the system drive), but for some reason, Windows keeps accessing the system, temp and application areas all the time so those partitions never go to sleep.

The other reason for having "the whole system" (except for data) on one drive is: I keep connecting and disconnectiong hard drives (e.g. for backups - no, my backup drive is not usually connected to the computer), and that just seems to be easier / more stable with everything on one fixed drive.
Actually, since I've found out how drive letter assignments work in the Windows registry and how to change them on a system that's not running (!) (mount remote registry from file!), that doesn't cause many headaches any more... It still seems easier to have that stuff on one drive...

> **starcraft.man said:**
> Most users don't have a swap/seperate application for windows, you might consider getting an external drive

I consider that (just ONE Windows partition) for my notebook where I can only have one (internal) disk and which I have to reinstall anyway (just bought a new disk for that yesterday). For the desktop, that is not an option. Reinstalling from my "stable image" takes 30 minutes "all in all" (!), doing a clean install would take more than two days. Really, I've tried it. Installing Windows means just soooo much clicking and pointing even when you know *exactly* what you're doing. And I keep forgetting how to set up those SSH + VPN keys... *sigh* They cannot even be "easily copied" because they require restrictive file permissions...

> **starcraft.man said:**
>  since your really out of space on that HDD, 

Huh?! Out of space? I think this is really a matter of "logistics" more than space. None of the partitions mentioned "has to be" larger than 10 GB, right? swap partitions only ~ 2 GB. So the "required total" is less than 50 GB with > 100 GB left for data. Apart from music and video stuff (which will probably be on a separate disk), that's enough for "typical daily use" ;-)
I know everybody will start *rofl*ing at this: I just don't want to make it more complicated than necessary *gg*. My Windows setup is pretty much fixed except for the temp/swap partition, but I don't know much about Linux. With everything I've done, I've never resized a partition. Tried it once, didn't work, lost some data (not much, I DID have a "recent" backup), never tried that again ;-)

So you're saying that I really don't need separate system/application partitions for Linux? What happens if the system partition is full? That has happened to me on Windows and it's a *real* PIA! ;-)

> **rsambuca said:**
> I have six different OS's on my rig and it doesn't look as confusing as yours!!!
You have six different OS on less than eight partitons? Cool ;-) (or is it?) So what does your drive look like? :curious:

> **starcraft.man said:**
> Hope that helps.

Yeah, thanks a lot ;-) Any more comments about my comments? ;-)

Finch

P.S.: What?! I'm not allowed to smile more than 8 times in one posting?! How sad :cry:

---

### Post by rsambuca on 2007-05-11
I actually have the six OS's split on two drives.  The original IDE drive that came with my PC has XP and Vista with a common data partition.  There is also a little recovery partition that came with the machine.

The linux OS's are on my newer SATA drive.  I have it set up with one large extended partition for the OS's with a shared swap, and a large partition for data.  I have space for one more OS and am trying to decide which one I am going to test.

I have attached images from gParted so you can see what I am talking about.

---

### Post by Finch75 on 2007-05-20
> **rsambuca said:**
> Wow - I think I agree with starcraft.man here.  That looks unnecessarily complex to me.  I have six different OS's on my rig and it doesn't look as confusing as yours!!!

Oh please... it doesn't look as confusing to YOU, because you know what you did. My idea doesn't look all that confusing to me either ;-)

> **rsambuca said:**
> I actually have the six OS's split on two drives.  The original IDE drive that came with my PC has XP and Vista with a common data partition.  There is also a little recovery partition that came with the machine.

The linux OS's are on my newer SATA drive.  I have it set up with one large extended partition for the OS's with a shared swap, and a large partition for data.  I have space for one more OS and am trying to decide which one I am going to test.

I have attached images from gParted so you can see what I am talking about.

ok, so if I counted correctly, you have 11 partitions. Basically, you have one Windows drive and one Linux drive. Of course each of them is less "confusing" than my combined Windows/Linux drive because yours can always easily share swap/temp and data...

ok, whatever... 
Thanks everybody for posting. In case you care about the outcome, here's what I did: I got rid of the "Windows temp/swap" partition and of the "Ubuntu applications" partition for a total of 6 partitions:
1) primary: Windows system
2) primary: Ubuntu system
3) extended:
3a) Linux swap
3b) Windows applications
3c) Linux /home
3d) shared data

At the moment, this seems to work fine without being overly complex, but I just need more Linux experience to know if that's good. What if I need to / want to reinstall Ubuntu? All the applications will be gone. Oh well, we'll see. I'm still in the "evaluate and play" phase anyway. My Windows setup was the result of > 10 years of experience with Windows, so I should just be a little patient with my Linux expertise... :-)

---

### Post by Corfy on 2007-08-24
Maybe I shouldn't jump in, but I have a similar set of questions as to what was answered before, and it seemed easier to tack on to this thread than to start a new one.

{**if you don't want background information, skip this section**}

I have been given a new harddrive, and in order to take complete advantage of the new space, I need to completely rework my system at home, which means a complete reinstall of all software. And as much as I would love to wipe Windows completely from the system, my wife isn't comfortable enough to let me do that yet (besides, I have several Windows games that I may want to play, although I haven't played them in a long time).

I plan on taking an 80 GB harddrive and, essentially, divide it into two (this isn't referring to partitions, but to resources). Half the drive will be for Windows, the other half for Linux. The plan is for both OSes and all programs being on the 80 GB drive.

My new 200 GB harddrive will have all our documents and settings (I will put the Linux home directories, plus two Fat32 partitions that Windows and Linux can both see, one for each user, on that harddrive, and I am going to move both "My Documents" folders in Windows to those partitions).

(A 40 GB drive currently in my system will be wiped and given to a friend so he can install Ubuntu on his computer, and in case you are wondering, all these harddrives are IDE, and I have a CD burner and a DVD player also installed, tapping out my IDE limit without more hardware, which I'm not getting at this time).

The Windows partitions I can deal with. Creating the partitions in general I can deal with. It is just the number and size of the Linux partitions that I am asking for recommendations on.

{**Background information over, on to the real questions**}

In essence, I have a 40 GB harddrive for the install of the Linux OS and applications. I know I need a swap space (double my memory is 1 GB, but I am thinking of going with 2 GB since I have the space, unless that will cause a problem), and home will be on another harddrive.

Beyond that, I have read conflicting reports of what I need/don't need.

Should boot, bin, usr, etc, lib, opt, tmp, root, var, sbin, dev, and/or mnt have their own partitions or not? Some places say "It is safer to divide some of these up" and some say, "Just leave everything together". About the only thing everyone agrees on is I need swap, /, and home partitions.

If I do divide some of these up, how big do you recommend for these partitions? I have seen some recommend /, swap, and home, some recommend /, swap, home, and usr, some recommend /, swap, home,and  boot, some recommend /, swap, home, usr, and boot. and some recommend /, swap, home, usr,and usr/local.

And other than the rule of thumb of doubling the memory to determine the swap partition, I haven't seen any rules of thumb or recommendations on how to size any of these. But I do like installing new software and checking it out, so I want to be sure I don't run out of space.

On the one hand, I have the space, but I don't want to back myself into a corner, either.

On a side note, if I reserve 10 GB of that 40 GB space for a second distro to be named later, can the two Linux distros share the same swap partition, or do I have to have separate swap partitions for each?

Thanks in advance for your help.

---

### Post by Finch75 on 2007-08-24
Hi Corfy,

you're welcome to "jump in" - although I'm not sure I'd even call it that after 3 months without new posts :-)

With all the "extensive background" information you've given, I think a few pieces of information are still missing:
- What's your level of Linux experience? Ubuntu experience? You said you'd like to get rid of Windows completely, so I'm guessing you're not a Linux newbie :-)
- Do you currently have a "working" Linux installation? How much space does/did it use? How much space does your Windows-installation currently use (System + programs, excluding data)
- What are you DOING with your computer? (type of applications)

Yes, 80 GB is PLENTY enough for just two operating systems without data. Side note: The 80 GB drive probably is somewhat (!) slower than the 200 GB so I'd reconsider putting the OS and programs on that drive. It's really the only thing that matters for a system's "perceived speed". Unless you're doing mostly video editing, disk speed is not so much of an issue for loading data. If "double your memory" is 1 GB, I'm guessing you have 512 MB of memory *g* - that's not so much nowadays... You will most probably need some swap space and it would be *much* better to put it on a "separate" (from system + apps) drive (that goes for both the Linux swap partition and the Windows swap file).

Sorry if that makes things more complicated :-)

For the other questions: I am NOT a Linux expert (see my other posts above), but unless you are, I'd recommend keeping all the other "mount points" (except home, that is) in one partition for the beginning. I really don't see an advantage in separate partitions unless they are on separate drives as well. Just separate partitions on the same drive might actually hurt performance (a little).
And the other thing is: Which sizes would you choose? Unless you reserve a lot of extra space for each one, you'll sooner or later end up with one partition that's too small while the other one has a lot of free space. I've been there lots of times :-) Of course these problems can be solved - but it's a lot of extra work that could've been avoided in the first place.

For the "shared swap": as far as I know, you can share the swap partition as long as you always shut down one OS before using the other one. Do *not* use Hibernate with a shared swap partition.

So, to sum up:
- I cannot answer all your questions.
- We need some more information before anybody can recommend useful sizes for your partitions. 80 GB should be plenty for 2 - 3 OS, though.
- I recommend putting at least the swap partition/file on the second drive. I also recommend doing (and considering) a speed comparison among your drives before installing your OS on the slower one :-)
- I recommend keeping things simple at the beginning. After a while, you can find out the sizes for certain mount points quite easily :-)

Hope that helps a litte :-)

Finch

P.S.: You might also want to consider NTFS for your shared partitions. FAT32 really sucks, I don't think Windows will even let you format 200 GB with it (although it's possible - maybe no problem in Linux) and NTFS for Linux has reached stable status last year. I'm using it and haven't had problems so far.

---

### Post by Corfy on 2007-08-24
OK, my background.

I tried my first install of Linux about two and a half years ago. It was a disaster installing it, but once it was successfully running, I loved it. Later that year, right after Ubuntu 5.10 was released, I switched to it (from a Linux standpoint). I spent more and more time with Linux, and finally switched to Linux as my primary OS around June or July of last year, and have been using Linux almost exclusively at home since around November or so. My wife has been a lot slower to convert, but she is coming along.

There are a lot of things that still elude me, however, and so I would consider myself a very advanced newb or a moderate user with occasional blips of advanced system admin skills. I understand a lot of the concepts, but in practice, either I don't know how to do them, or (like these partitions and sizes) I can do them, but am not sure what should be done.

I do have a fairly strong Windows background dating back to DOS 5.2/Win 3.11 (although, as you might have guessed, I currently prefer Linux). And I am currently the IT manager at my office, although that has more do to with a) me knowing more about computers than anyone else in the building, which isn't saying much, and b) it was cheaper to move me over than hire someone who knew what they are doing. We are entirely Windows based at the office, although I am working on that.

And yes, I know my hardware is somewhat limited and old. I built (or rather, rebuilt) the computer a few years ago, right before my wife and I bought a house, and I don't have a whole lot of money for upgrades right now (my switch to IT Manager did not include a significant raise). I got the 200 GB harddrive as a gift, but it is brand new and I want to use it. And I want to take this opportunity to start with a clean slate, software wise.

I don't remember how fast either harddrive is. I can look at the box of the 200 GB when I get home. I assume the speed on the 80 GB is on the drive somewhere. But right now, the 80 GB drive runs Ubuntu just fine, although I am running low on home space (that shouldn't be a problem for a while with the new drive).

But right now, I have a 40 GB harddrive that is divided up into five partitions, about 7.4 GB each (there is a long story behind that, but I won't bore you with those details unless you really want it). That is our Windows harddrive (OS, apps, and files).

The 80 GB is divided between Linux (which is where K/Ubuntu is installed now, OS, apps, and home) and media files. I originally wanted those media files accessible from both Linux and Windows, but I think I will move them to just Linux. (Some people have extensive MP3 collections, I collect movie trailers.)

I just figured if we are dividing up the / and home into separate partitions, it makes sense to separate them onto separate drives. And if it works for Linux, it should work for Windows.

My other hardware specs are as follows (from what I can remember, I'm still at the office, although I should have gone home before responding)

AMD Athlon XP 1600+ processor
Gigabyte GA7-400L motherboard (or something like that)
512 MB RAM
16x DVD drive
32x CD-RW drive
floppy
SoundBlaster Live! Value soundcard
Currently: 40 GB and 80 GB harddrive
Planned: 80 GB and 200 GB harddrive
ATI Radeon 9000 video card (it was a decent card at the time, and I haven't bought any games recently)
21" CRT monitor (picked that up used from work, nice picture, but the thing weighs a ton)
Windows XP Home and K/Ubuntu 7.04

Believe me, if I could afford some hardware upgrades, I would. But computer parts aren't as important right now as eating. So I have to make due with what I have.

And I am still a little leary of the NTFS support in Linux. I don't mind using it in a pinch (and I have used it at work occasionally to rid some computers of viruses and/or spyware), but I don't know if I trust it full time. But only a small portion of the 200 GB drive will be partitioned as FAT32 (two partitions witha combined total of no more than 40 GB). More of a "DMZ" space than an actual workspace. The remainder of the drive will be formatted either ext3 or reiserfs (although I will probably use your suggestion of the swap on the second harddrive).

As for what I do on it, I do a bit of everything: web browsing/email, word processing, spreadsheets, audio/video playing, photo editing, graphics design, video editing, web design, desktop publishing, games. And as I said, I like to experiment (which is really easy with the Ubuntu repositories). Although things like video editing have been very restricted due to the fact that I am running out of home space.

I just figured, since I am starting with a clean slate on my desktop, I might as well do it right.

---

