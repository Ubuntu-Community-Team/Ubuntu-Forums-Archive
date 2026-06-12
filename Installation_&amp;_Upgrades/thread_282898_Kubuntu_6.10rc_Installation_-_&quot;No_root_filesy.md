---
title: "Kubuntu 6.10rc Installation - &quot;No root filesystem&quot;"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2006-10-23
I'm trying to install the Edgy Kubuntu release candidate and have run into a problem.

When I choose partitions to mount/format, on pressing "Continue", I get an error message, "No root file system" appear.  Odd, since I have selected to mount as / the partition /dev/hda3.

Can anyone think of a reason why this should be so?  Note that I have not actually created any new partitions, I'm just doing a fresh install into already-existing partitions.  I note that /dev/hda3 has a status of "Active" in the Prepare Partitions section of the installer.

Thanks in advance for any advice.

    -- Joe

---

### Post by msux on 2006-10-23
I'm seeing the exact same thing.

---

### Post by WebDrake on 2006-10-23
Well, this is a bit of a dodgy situation for a release candidate.  How many other people have had the problem?

Very annoying, because Edgy looks absolutely beautiful.

---

### Post by WebDrake on 2006-10-25
Has no one else observed this?

I'm rather concerned that tomorrow when Edgy proper is released, I will be faced with the same issue and unable to install it.

---

### Post by bulldog on 2006-10-25
Is your partition empty??

If not remove it and make it again I had the same experience and this helped me.

Don't ask why.........just try,maybe it works for you too.

---

### Post by tubasoldier on 2006-10-25
I have never used the Kubuntu install disks. I have never had good experiences with them. I always install Ubuntu and expand from there.

---

### Post by WebDrake on 2006-10-25
> **bulldog said:**
> Is your partition empty??

If not remove it and make it again I had the same experience and this helped me.

OK.  I will try out tomorrow's official release and if the same problem happens, I'll follow your suggestion.

Thanks very much! :)

---

### Post by WebDrake on 2006-10-25
> **tubasoldier said:**
> I always install Ubuntu and expand from there.
Always a possibility.  I didn't actually try Ubuntu itself since I wanted to start straight with KDE.  Thanks for the suggestion. :)

---

### Post by fsamir on 2006-10-26
I'm having the same problem, but when installing from Ubuntu disk.

I have 3 primary partitions, hda1 is a NTFS, hda2 is reiserFS and hda3 is swap. The formating process works fine on both hda2 and hda3, but the weird part is that the partitioner still saying "no space available" on hda3.

Any suggestions?

Thanks,
Franklin Samir

---

### Post by megamaced on 2006-10-26
I had exactly the same problem with the release candidate. I was upgrading and already had my partitions laid out. I choose the root partition and selected 'Reformat' but the error message wouldn't go away.

I haven't tried the official release yet but I would hope that the problem has been rectified

---

### Post by bristi on 2006-10-26
Exact same problem here using the official release - both ubuntu and kubuntu. My root partition wasn't empty and used the reiserfs filesystem. Reformating the partition (from the installer) to ext3 solved the problem.

 The partitioner wasn't able to format using reiserfs, so maybe support for this otherwise great operating system is currently lacking from the edgy installer?


--edit: Whoops.. Seems I mixed together two lines quite harshly while writing this post.. Of course reiserfs is a _file system_, not an operating system.. It must have been to obvious for everyone in here since noone has commented :)

---

### Post by vulpes on 2006-10-26
I see the same here on the final 6.10 build, and it does not matter whether I try to use ext3 or any other type of fs. I think the problem here is related to primary vs. secondary partitions, but I have no idea how to proceed and my machine is now toast since I tried to do some formatting of partitions. I'm extremely disappointed with poor quality of this release. Ridiculous. I've been using Ubuntu since Warty. Guess I need to download and install Fedora Core again. :-(

UPDATE: My install was on Ubuntu, not Kubutu. Anyway, here's the deal. The installer doesn't seem to be able to handle partitions that were formatted with "gparted" partitioner!! If you are going to manually partition, use fdisk and mkfs.ext3 (for example). If you're not an experienced user, I suggest that you do not install this release, but stick with 6.06. For me, once I formatted my root partition with mkfs.ext3, then told the installer to partitional manually, that eliminated the "No root file system" message. Canonical got "caught with their pants down" on this one!!

---

### Post by andyfraser on 2006-10-26
My situation: Ubuntu 6.06 / on /dev/hda7 and /home on /dev/hda8, both formatted ext3 and I got the same problem.

My solution: I tried deleting and recreating the two partitions but that didn't work. I noticed that gparted was saying the two partitions were unknown. I left the installer on the stage 5 screen and, using a terminal (thank God this is a live CD), used cfdisk and mke2fs -j to recreate the two ext3 partitions. The installation then continued to conclusion.

All I have to do now is reboot and hope it works.

---

### Post by ember on 2006-10-26
Ah, great - I even started to download the alternate install CD, because I experience the same problem (Edgy Final/Ubuntu). I already became suspicions when gparted created the partitions, but did not format them. I guess we can consider this a bug.

---

### Post by minty on 2006-10-26
I had the same problem with the official release, downloaded today (and I checked the md5 sums)

Previously had Kubuntu 5.10 installed (I skipped Dapper entirely).  It was Kubuntu 6.10 (finaly) I was trying to install.

Here is how I fixed it:

* I clicked "Go Back"
* I deleted my existing root (/) partition, and also my existing swap space partition
* I created a linux-swap partition, with no label
* I created a new root partition, ext3 with the label /

** WARNING ** Continuing beyond this point will ERASE ALL DATA on your harddisk.
If in doubt, power off, reboot (without the cd) and make a backup of your disk.
I'll say it once more - re-partitioning your disk will ERASE ALL THE DATA that was there.

Essentially I re-created the existing state by deleting the partition and then recreating them.  However initially the mount pointed was given as /dev/hda1 for the root parition, and manually setting it to / didn't work.  Having done the re-partition, it correctly identified the / partition for the label.

I'm now wondering if just returning the parition table, editing the partition in question and setting it's label to / there would then let the later stages proceed correctly?

In any event, having done this, I could then proceed past the next step without the "No root filesystem" error.

---

### Post by al_ac on 2006-10-26
Same problem here. Today I downloaded the desktop i386 edgy cd . When I try to install on my old root partition I got "no root filesystem" ](*,)

---

### Post by cobralgato on 2006-10-26
I get same error.

Deleted the partition and created again with gparted from live cd, no luck. 
Deleted the partition and created again with gparted from old dapper installation, no luck. 
Deleted the partition and created again with mkreiserfs from live cd, no luck. 

? huh

---

### Post by lusp00ky on 2006-10-26
i got the same problem, with the final release of ubuntu 6.10
i already have the partition with reiserfs filesystem and ubuntu 6.06

there are any official thing about this bug? it's very critical IMHO..

---

### Post by yyzyyz on 2006-10-26
I'm getting the same error with ubuntu 6.10 final release. Looks like a definite bug to me (Screenshot attached). 
This should work regardless of the partition type and whether it is an existing partition or a new partition, since I'm asking it to format it.
I'll try deleting and recreating root partition from the installer as some people suggested to see if that helps...

---

### Post by minty on 2006-10-27
> **cobralgato said:**
> I get same error.

Deleted the partition and created again with gparted from live cd, no luck. 
Deleted the partition and created again with gparted from old dapper installation, no luck. 
Deleted the partition and created again with mkreiserfs from live cd, no luck. 

? huh

No idea if this will work, but have you tried going back one step in the installer, using that *** and setting the label on the new partition to / at the partition stage (ie, the step before it fails) ***

Apologies if you have, I figured it was worth checking just in case.

---

### Post by Uuranor on 2006-10-27
> **yyzyyz said:**
> I'm getting the same error with ubuntu 6.10 final release. Looks like a definite bug to me (Screenshot attached). 
This should work regardless of the partition type and whether it is an existing partition or a new partition, since I'm asking it to format it.
I'll try deleting and recreating root partition from the installer as some people suggested to see if that helps...

Same problem here, with Kubuntu normal cd and Kubuntu alternate cd :\
The only thing I can do is to format all the disk but ... in this way I lose 100GB of data. :\

---

### Post by Uuranor on 2006-10-27
I think this is the bug in launchpad:
[https://launchpad.net/distros/ubuntu/edgy/+source/ubiquity/+bug/67130](https://launchpad.net/distros/ubuntu/edgy/+source/ubiquity/+bug/67130)

But I don't understand how to work around it, with alternate cd or kubuntu live cd. :\

---

### Post by WebDrake on 2006-10-27
> **bristi said:**
> Exact same problem here using the official release - both ubuntu and kubuntu. My root partition wasn't empty and used the reiserfs filesystem. Reformating the partition (from the installer) to ext3 solved the problem.

 The partitioner wasn't able to format using reiserfs, so maybe support for this otherwise great operating system is currently lacking from the edgy installer?
Looks like it.  Im my case as well the original root partition was in reiserfs.  When I deleted and recreated it, reiser was not an option.  However, the new partition (ext3) was accepted.

Still, I'm really very happy with Edgy aside from that, and I don't *so* much care what fs I use.  But it is a bug that should be fixed ASAP.

Incidentally, the other reiser partitions (one for /home, one for storing other files...) were accepted just fine.

---

### Post by ember on 2006-10-27
Yes - this bug is naster, but using the Alternate Install CD worked for me (Ubuntu). This has other bugs, though smaller ones (e.g. I have ath0 and wifi0, with the difference that wifi0 does not work, because the installer does not ask for wireless parameters, also the -restricted-modules part is not installed which broke my network until I noticed).

So basically, you just boot the alternate cd, use custom partitioning, assign the mount-points and that's it.

---

### Post by cobralgato on 2006-10-28
this bug seems too serious... how can a distro like ubuntu which aims to conquer users from the redmond devil provide an installation cd that doesnt work ? .... why would people change then ???

---

### Post by xor.be on 2006-10-29
Same problem here.
I solved it using hirens boot cd. Deleted and recreated partitions to ntfs. Then doing the same thing in the installer, but putting them on ext3 and swap, and idd /  seemed to work.
odly enough since i tried to do the same thing,without hirens boot cd, no root :s

i just hope my windoze partition isn't damaged :)

---

### Post by nnull on 2006-10-31
So what now? When will there be a fix for this?

---

### Post by GozzoMan on 2006-11-01
Same problem, with Ubuntu 6.10 Desktop CD.  

Resolved with "Install in text mode" on Alternate Install CD (without having to replace partitions or anything, on the Alt Install CD it simply worked as expected).

---

### Post by rsambuca on 2006-11-01
You can also quickly get around the "no root file system" error by changing the validation.py file.

When running the liveCD, but prior to installation:

```
gksudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

go to the end of the file, and edit the line that says 

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

Change to:

```
if not root:
  [COLOR="DarkRed"]pass[/COLOR]
```

Make sure you leave the indentation in before the word "pass".  Save the file, close it, and then you can run the installer.

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

---

### Post by psyduck170 on 2006-11-02
i had the same problem and solved it by closing the installer and opening gparted from the live cd.
i reformated the partition and started the install again and it worked.

maybe a warning for other ppl: i have had this problem before and deleted the partion n then created it again but this gave problems for my other distros cause it changed my partition numbers. changing fstab in my other distros + the grubmenu solved this again. but still for a beginner who likes to try out different distros this can be nerve wrecking.

so this time i just reformated the partition meant for my root system in gparted from the live cd and it worked!

---

### Post by squibbon on 2006-11-02
Has anyone tried the solution of rsambuca?

---

### Post by drslinky1500 on 2006-11-02
No, but it sounds reasonable. I have been trying to try it for the last hour, but I can't keep the system working. Either the CD refuses to boot, or it errors out while going through the install. ](*,)  Hopefully within the day I will be able to tell. 

This is not like Ubuntu. I wonder if this is a backlash from a disgruntled community member over the whole Hans Reiser thing. He may be guilty, but his file system rocks. I wish reiser 4 would catch on, I tried it in Yoper, it's pretty quick. 

Well, what do know, I need to reboot the installation media again. :mad: :confused:

---

### Post by squibbon on 2006-11-02
> **drslinky1500 said:**
> No, but it sounds reasonable. I have been trying to try it for the last hour, but I can't keep the system working. Either the CD refuses to boot, or it errors out while going through the install. ](*,)  Hopefully within the day I will be able to tell. 

This is not like Ubuntu. I wonder if this is a backlash from a disgruntled community member over the whole Hans Reiser thing. He may be guilty, but his file system rocks. I wish reiser 4 would catch on, I tried it in Yoper, it's pretty quick. 

Well, what do know, I need to reboot the installation media again. :mad: :confused:

Worry no more. rsambuca solution worked like a charm! I have just installed Edgy now and and i think it's good. First, i had doubts to his solution because i thought i can't modify files on the LiveCD (ROM) but hey i did.

Thanks for that one rsambuca and i hope this testifies for SOLVED problem of "No root filesystem"

---

### Post by rsambuca on 2006-11-02
I certainly didn't come up with the solution myself!  I just had the same problem and found the answer on one of these threads, but I can't find it anymore.  I happened to have written down what I did on the installation CD if/when I install again.  Your thanks should be redirected elsewhere!

note:  for this Edgy installation, I now had to use ide=nodma to boot the live CD, then re-turn on the dma on the CD drive and hard drives (or installation would take Hours instead of minutes), and also change the validation file in order to install the system.  For some reason I think it should be easier than this!

---

### Post by CraigRat on 2006-11-04
> **rsambuca said:**
> You can also quickly get around the "no root file system" error by changing the validation.py file.



Thanks rsambuca, worked for me.
:KS

---

### Post by chikebum on 2006-11-04
try "sudo mkfs.ext3 /dev/hdb2" ( without quotes )

/dev/hdb2 where you want to assign a root partition /

---

### Post by dtek on 2006-11-05
I was planning on doing a demostration of how easy it was to install Ubuntu on both home desktops and Laptops, on my College (Since the evil rules there :twisted: ), and taking advantage of the new Edgy i was willing to do it on it, but ](*,) , i couldn't install it even on my own PC due to this.

Imagine the reaction of my target audience (people with no prior Linux Experience, and surrounded by :twisted:  Devil Wizards :twisted: ) when in public i would get this "No root filesystem". :confused:  Sure, right after doing the workarounds posted here, the room would be empty.


Really Bad mistake for the "newbie-friendly Distro".

---

### Post by rsambuca on 2006-11-05
dtek,

I agree it is a pretty silly bug, however, keep in mind that this "no root file system" error only shows up when installing Edgy overtop of prexisting  partitions from earlier installations.

If you were showing this off to linux newbies, you probably shouldn't get this error.

---

### Post by bappi on 2006-12-11
> **rsambuca said:**
> You can also quickly get around the "no root file system" error by changing the validation.py file.

When running the liveCD, but prior to installation:

```
sudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

go to the end of the file, and edit the line that says 

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

Change to:

```
if not root:
  [COLOR="DarkRed"]pass[/COLOR]
```

Make sure you leave the indentation in before the word "pass".  Save the file, close it, and then you can run the installer.

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

i have tried doing that but it does not save because it says that i do not have the permission to change the file, it says that i am not the owner of the file, can u help me on that?

---

### Post by rsambuca on 2006-12-11
did you put "sudo" at the beginning of the instructions?

---

### Post by Mission on 2006-12-14
:) 

Thank YOU! This is what,I call a perfect solution. 
'Your are highly welcome!

Mission

> **rsambuca said:**
> You can also quickly get around the "no root file system" error by changing the validation.py file.

When running the liveCD, but prior to installation:

```
sudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

go to the end of the file, and edit the line that says 

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

Change to:

```
if not root:
  [COLOR="DarkRed"]pass[/COLOR]
```

Make sure you leave the indentation in before the word "pass".  Save the file, close it, and then you can run the installer.

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

---

### Post by prolix on 2006-12-23
I tried this solution. and got the same permissions error. I tried to use "sudo gedit", but it complained that it could not find the command "gedit". I used "edit" instead, but I'm shamefully unfamiliar with command line editors, so I don't know how to save it, if that is indeed possible.


> **rsambuca said:**
> did you put "sudo" at the beginning of the instructions?

---

### Post by rsambuca on 2006-12-23
gedit is simply the text editor that comes on the ubuntu live CD, so it should be there.

It is probably easiest if you enter the terminal and copy and paste the commands as listed in these prior posts.  I am sorry I can't help you further but I know that gedit is on the live CD.

Are you sure you are entering these commands in the terminal?

EDIT:  Actually, if you are using the kubuntu live CD, replace the word gedit with the word kate, which is the text editor for KDE.  Sorry I missed that.

therefore, try```
sudo kate /usr/lib/ubiquity/ubiquity/validation.py
``` and then follow the rest of the instructions.

---

### Post by Embiggens on 2007-01-05
rsambuca's solution worked for me, too.  Thanks rsambuca and whoever originally came up with this solution, as well as any potential intermediaries who passed the solution between those 2 points.  And thanks to the internet (and Al Gore) for facilitating this transfer of information.

---

### Post by aldin on 2007-01-06
> **rsambuca said:**
> You can also quickly get around the "no root file system" error by changing the validation.py file.

When running the liveCD, but prior to installation:

```
sudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

go to the end of the file, and edit the line that says 

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

Change to:

```
if not root:
  [COLOR="DarkRed"]pass[/COLOR]
```

Make sure you leave the indentation in before the word "pass".  Save the file, close it, and then you can run the installer.

Now, when you run the installer, it won't check for a "/" directory, so make sure you have one!

thanks, works for me

---

### Post by alanra on 2007-01-07
Hi,

I am totally new to Linux, in any form. I have been an avid windows user for over 10 years. I'm ready to expand my horizons and undersatand the world of Linux, Gnome, etc. I have partitioned space on a NTSF HD, and I am attempting to install Ubuntu using the Live Cd, and, of course, I discovered the same 'no root' issue. Now I am here. I see the info about changing the code, but I have no clue where to do this. With the live cd running and the desktop in plain view I am clueless about where to go next to edit the validation.py file. Having played around in DOS years back, I am somewhat familiar with command line editing. But right now I am lost!! Help please.  Much thanks.

---

### Post by rsambuca on 2007-01-07
I'm not on my linux box right now, but if my memory serves correct, in the top left corner of the screen should be the Applications menu.  Click on that, there will be things like Internet, Sound & Video, etc.  Find "Terminal" ( I can't remember where it was located off hand - I have moved it to my desktop).  Anyways, it should be easy to find in there, then click on it, and a terminal will open up where you can enter the instructions.

---

### Post by alanra on 2007-01-14
Ok I found the terminal and typed in the instruction. It opened up (or perhaps created) the validation.py file, but it is blank. Nothing to edit here.

---

### Post by rsambuca on 2007-01-14
I suggest you just copy and paste the commands into the terminal line, because the file is there.  It is part of the installer.

```
sudo gedit /usr/lib/ubiquity/ubiquity/validation.py
```

Keep in mind that the file names and directories are case sensitive in linux, so a file called Validation will be different than validation, etc.

---

### Post by alanra on 2007-01-15
That did it. I found the file, edited it, saved it and Linux did install. But it will not boot. I left settings as they were, formatting only the swap partition but not the main partition. Also I installed to the recommended "/" root folder. Installation was a success, but my settings may have been wrong. The partition I did not format (it was not checked) was NTFS. Is that the error? Rsambuca, you have been most helpful.  Thank you very much.

---

### Post by rsambuca on 2007-01-15
You'll have to do the install again and this time let the installer reformat the root partition "/" as ext3, which is the native format.  NTFS is a windows thing.

---

### Post by contadinoste on 2007-01-21
I have had exact the same problem: **Resolved** by formatting fromthe installer the sda3 partition _before_ assigning the /  and /home to the partitions. The it worked without problems.

I have sda1 /  with Kubuntu dapper 10GB
            sda2 swap
          sda3 / now with Kubuntu edgy 13 Gb
         sda4 /home

---

### Post by zba78 on 2007-02-22
**rsambuca**, editing /usr/lib/ubiquity/ubiquity/validation.py the way you described worked perfectly. Thanks for the guidance.

Bit of a show-stopper for any non-experienced Linux user giving Ubuntu a try for the first time. Not difficult to fix but perhaps a little disconcerting for some.

---

### Post by Nomad888 on 2007-03-27
I have found that if you use ext2 there are no errors as in ext3 or reiserfs. Can this be an issue related to the journaling fs?

---

### Post by mardawi on 2007-03-27
I faced this problem with ubuntu 6.10 official release. What i've done was:
[LIST]
[*]click back to the gparted
[*]right-click on each ext3 partition
[*]choose reformat to ext3
[/LIST]

that did the trick for me and everything went fine after that.

---

### Post by observative on 2007-12-31
Hi all this is my first post here on Ubuntu...had to say that ):P

I believe this is the original post about "no root file system" or "no root filesystem" with the validation.py solution...by [eurgain]("http://ubuntuforums.org/member.php?u=10986")
[http://ubuntuforums.org/showthread.php?p=1656061#post1656061](http://ubuntuforums.org/showthread.php?p=1656061#post1656061)

Here's a summary with some procedure for the pros and novices out there, or just not familiar with nix commands and apps:

1. Open a terminal (command prompt for the win user)
Applications->Accessories->Terminal

2. Type the following at the prompt:

sudo gedit /usr/lib/ubiquity/**ubiquity/**validation.py

and press the enter key. This will open the validation.py in the gedit text editor. Remember everything in nix is case sensitive, so be exact.

3. Make the following changes.
Replace:

if not root:
    result.add(MOUNTPOINT_NOROOT)

with:

if not root:
    pass

"For those not familiar with Python, the indentation is required!

This turns off the check for a root filesystem, so make damned sure that you allocate one in the installer! As I said, it is a kludge, so use at your own risk."

4. Save the file. Even if the file is on the cd it will be saved...at least until you reboot.
5. Start the Install. This seems to have worked for a lot of people on a lot of other threads.

However for me, in the latest U7.10, the "result add(MOUNTPOINT_NOROOT)" is not there. So I'm off to find the answer. I just wanted to add the credit and a more detailed procedure to sum up this thread.

---

### Post by observative on 2008-01-01
I got it to install! All I had to do was use the Alternate CD. If you read the fine print it clearly says that if you want a dual boot you need to use the Alternate CD...even though the desktop cd indicates it will do it.

Thanks for everyone's input.

---

### Post by rsambuca on 2008-01-01
> **observative said:**
> I got it to install! All I had to do was use the Alternate CD. If you read the fine print it clearly says that if you want a dual boot you need to use the Alternate CD...even though the desktop cd indicates it will do it.

Thanks for everyone's input.

Actually, you can very easily set up a dual boot system using the Live CD as well.

---

### Post by observative on 2008-01-03
Hi, I thought about it and decided to do a complete run down on my system and why it would not install with the live cd and more times than not, including after a successful install with the live cd, it was a hardware configuration issue. I'm amazed windows ever ran after Ubuntu pointed out all the MS "cover-ups". Makes me wish I pursued my driver writing career to include some nix variations.

So I concur, the Live CD does install and works like a champ, as does the Alternate CD, both of which I have successfully installed as a dual boot. I will say that until I did a pre-partition with a 3rd party software, the Live CD gave the "no root file system" error...which it did not after the pre-partitioning, and installed well like a champ:)

Thanks again, Chao!

Edit: Here's the forum thread I found all of the "pre-partition" info on. [http://ubuntuforums.org/showthread.php?t=654352](http://ubuntuforums.org/showthread.php?t=654352). Its perfect for ppl on win that want to try the dual boot before they jump feet first into the nix waters.

---

