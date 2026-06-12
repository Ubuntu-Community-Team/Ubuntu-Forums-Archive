---
title: "Gusty ruined my PC"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by oomar on 2007-10-20
I was living happily in ubuntu when the upgrade to 7.10 came out. I upgraded and waited it out. NOW MY PC WONT BOOT!!!! When I go in tthe GRUB menu i cant boot any of the "Generic" ones or the latest recovery one. Currently im in CLI of the second latest. I need to find out how to either fix this or downgrade my system from CLI. PLEASE HELP!!! I need my computer for a school paper on there!!! DUE ON MONDAY!!! PLEASE!!!!!!!!!!!!!!!!1

---

### Post by LaRoza on 2007-10-20
> **oomar said:**
> I was living happily in ubuntu when the upgrade to 7.10 came out. I upgraded and waited it out. NOW MY PC WONT BOOT!!!! When I go in tthe GRUB menu i cant boot any of the "Generic" ones or the latest recovery one. Currently im in CLI of the second latest. I need to find out how to either fix this or downgrade my system from CLI. PLEASE HELP!!! I need my computer for a school paper on there!!! DUE ON MONDAY!!! PLEASE!!!!!!!!!!!!!!!!1

If you need the paper, use the live disk to remove it to a storage media. 

If you are using the cli, it did boot, please explain more of what happen, especially error messages.

---

### Post by gpilkay on 2007-10-20
I am not sure how best to fix the boot (I am a linux newb, I admit) but one thing that has worked for me both in Ubuntu or Windows, is to take the Ubuntu Live-CD, boot up with it, then go to your drive, find your files, and copy them to a USB stick.  This will let you reload if needed, then just copy them back or take them to another computer.

I also have a Dell laptop that does NOT like Ubuntu installed, but runs the CD fine.  I actually have used a USB drive and the Ubuntu CD to do my papers in OpenOffice as a temp fix when I needed Ubuntu and didn't have the whole install.  Worked great, for such a non-standered system.  I still keep a Live-CD in my laptop bag.

---

### Post by oomar on 2007-10-20
when i boot it givers this error:

[13.956650] Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


What i did was click on upgrade in the software update program thing.... ubuntu screwed itself over.... is it possible that my computer is just too old? its like 7 or 8 years old

---

### Post by oomar on 2007-10-20
my computer is a VERY old sony/VAIO computer

does that help?

---

### Post by oomar on 2007-10-20
help me!!!!!!@

---

### Post by jackmc on 2007-10-21
> **oomar said:**
> when i boot it givers this error:

[13.956650] Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


What i did was click on upgrade in the software update program thing.... ubuntu screwed itself over.... is it possible that my computer is just too old? its like 7 or 8 years old

is that when you boot from a live cd, or from your hard drive?

Live CD should be fine. I ran a live CD for a few days when my HDD failed once :)

---

### Post by oomar on 2007-10-21
thats from the hard drive

how would i downgrade my pc from the live cd?

---

### Post by Nero_Flint on 2007-10-21
Gutsy didn't ruin your computer...you did (I know that's hard to admit). Take a deep breath and look back at the steps you took to try and find out where you made the mistake. Yelling and screaming on a forum isn't going to help matters any it's only going to turn people off of helping you. 

As LaRoza and gpilkay said use the live disk and take it from there. Once you have saved your paper then worry about what happened....

Lessons learned (hopefully?): Don't upgrade to an unknown OS without first finding out if your computer is capable of handling it. 

I hope it works out for you, I am also a noob when it comes to Linux. I'll be watching this thread with interest.

---

### Post by click4851 on 2007-10-21
short term fix....live cd +1 to that idea....once you have time, reinstall 7.04?

---

### Post by bluedragon436 on 2007-10-21
I agree with click.... safe mode it, and save the paper that you need, also while you are there download the full 7.10 if you have the ability to do so, or use another computer if you got one.  And just do a full reinstall.  I had a very similar issue with my desktop that I was upgraded to 7.10 and I ended up just reinstalling 7.10 fully from scratch and it hasn't had an issue since.  I am not going to say you did anything wrong cause although I am also a Linux newb, I followed the directions as they came up and ended up with this issue.  So now as big of a pain in the *** as it is to reinstall and have to set everything back up the way you want it, it may be your best bet to start from scratch again.

---

### Post by heldal on 2007-10-21
> **oomar said:**
> when i boot it givers this error:

[13.956650] Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)


What i did was click on upgrade in the software update program thing.... ubuntu screwed itself over.... is it possible that my computer is just too old? its like 7 or 8 years old

You mean the upgrade was aborted?

I had the same problem on a computer, but was able to boot the old kernel in recovery-mode. During boot a kernel needs a ramdisk image with the basic drivers (disk, filesystem, input-devices etc) required to get started. Without that you'll end up with a kernel unable to mount the harddrive like you indicate above. The build of these ramdisk images are done late in the install/upgrade process to be able to incorporate 3rd-party drivers in other packages. Previously the ramdisk was rebuilt multiple times during install, but now it seems to be deferred to the end of the process.

(Note: all commands below should be executed by root. If logged in by a regular user either put "sudo" in front of the command or start a root-shell first using "sudo sh")

If you can get the system booted with an old kernel or establish a chroot-environment from a live CD or DVD, you should be able to rebuild the initial ramdisk (initrd) using the command: "update-initramfs -c -k 2.6.22-14-generic". It is also possible to rebuild for all installed kernel using the word "all" instead of the specific kernel-version in the command. Then your new kernel should be able to boot.

How well things work from here depends on how far in the upgrade process you got. If X hasn't been sorted you might find yourself restricted to the character-terminal in recovery-mode until you can get all packages sorted. First try the obvious by grabbing anything marked for upgrade using the commands "apt-get update", "apt-get dist-upgrade" and "apt-get upgrade". The upgrade process does however remove some packages in the process and re-install them much later. Some packages might thus still be missing, but can be recovered as follows:
The upgrade process has written log-files in /var/log/dist-upgrade. In a file there called main.log you will find information about packages that were ment to be installed, upgraded or removed. Extract the information about things to install and upgrade into a new file. Ex:
```
grep "Install:" /var/log/dist-upgrade/main.log > /tmp/pkglist
grep "Upgrade:" /var/log/dist-upgrade/main.log >> /tmp/pkglist

```

If you make the system try to install all these packages with apt-get it will only install the packages that are either new, or not yet upgraded to the last version:
```
for pkg in `cat /tmp/pkglist`
do
apt-get install $pkg
done
```

Then follow instructions from apt-get on how to remove packages that are no longer necessary. You should then have an upgraded system that is complete except from what is supposed to be done in the "cleanup-phase" at the end of the install/upgrade process whatever that might be.

--

There is unfortunately no easy way to recover an aborted/failed upgrade so most people might find it easier to re-install.

---

### Post by oomar on 2007-10-21
I understand how i may sound but all i did was click the 'ok' button when it wanted to upgrade. anyway....


What happened was it upgraded with NO errors that showed up. Then it restarted. And came up with that panic error.

Is there anyway to DOWNGRADE without completely reinstalling? I am currently using the live cd. I Have like 70 gigs of stuff and my computer seems to have the slowest EVER transfer speed. So I really dont want to back that up on my PHDD....

---

### Post by RTrev on 2007-10-21
> **oomar said:**
> I was living happily in ubuntu when the upgrade to 7.10 came out. I upgraded and waited it out. NOW MY PC WONT BOOT!!!! When I go in tthe GRUB menu i cant boot any of the "Generic" ones or the latest recovery one. Currently im in CLI of the second latest. I need to find out how to either fix this or downgrade my system from CLI. PLEASE HELP!!! I need my computer for a school paper on there!!! DUE ON MONDAY!!! PLEASE!!!!!!!!!!!!!!!!1

There is, in my experience, no way to convince people to keep backups of important data without having them go through what you're going through right now.  Too bad it has to be that way.

Try the Live CD recovery options others have mentioned.

And then... well, you get the idea.  I have everything I *care* about on multiple media, always.

In fact, on multiple machines, separated by hundreds of miles, and on USB sticks, and on CDs, and so on.  I FTP things up to my web server, into a hidden and password-protected directory.

If you don't have backups, you'll lose your data.  Period.  End of lecture.  :(  Sorry, and I hope you get it back, but in any event take away from this the lessons you've learned the hard way.

Bob

p.s.  Tell your teacher that you're a computer noob, and maybe he/she will remember when he/she did the same thing and will take pity on you.  :)

---

### Post by gpilkay on 2007-10-21
Don't worry, there are always ways around things.  Personally, I use all CD-RW's and USB, as I don't like my important stuff on-line, but the solution proposed previously, using an on-line backup, does work quite well.  Just set up an account at one of the backup sites, use the Live-CD to boot up and transfer everything, then re-install and send back.  It's a long process but still doable.  One huge advantage fo the Ubuntu CD is that it gives you a fully working system right off the bat.  Try to use a computer with no viable Windows install with just a CD and see how well it works.  You can't even open a doc format file.

There isn't really a 'downgrade' without re-install.  Not that I know of anyway.  I'm not installing 7.10 till my semester's over in December, that way if I nuke everything, I don't have to care, I can just pop in a CD and re-start (I have separate hard drives for Windows and Linux, so I can nuke half the machine and still have the other half).

Later on, though, just keep full backups of everything (I do mine at least onece a week while in college) and then, when these things happen, just use the re-load as a quick disk cleanup.

It's nice to know that I'm not the only one who uses Live-CDs for weird reasons.

---

### Post by jacob01 on 2007-10-21
wow it didnt ruin you computer, it still boots up to the grub menu, if your computer was ruined then it would not post at all, but still then that doesn't mean that you computer in a whole is ruined, you would still have some working components. the correct way to say it would be that you messed up the current install of your os,

---

### Post by RTrev on 2007-10-21
> **gpilkay said:**
> 
It's nice to know that I'm not the only one who uses Live-CDs for weird reasons.

lol.. no you certainly aren't!

My backups to an off-site server are always to domains that I own..

This is handy and quick.  Just pop up gFTP, copy the files up, and I'm done.  They're in a directory which requires a username and password to access.  But it's only one of the backups.  USB and CD are always included.

---

### Post by oomar on 2007-10-21
RTrev: what recovery options?

and for those who suggested me uploading to an ftp: Its 68 gigs of stuff. My offsite ftp is like 50gb. my regular ftp IS this computer. And I have most of it backed up but the way i organized it on this pc took me a LOng long time.... i may just get a new hard drive and install on that and then copy so as not to copy it off and then BACK to this one.... and who ever posted on my word choice of ruined pc vs os: good but ultimatly irrelevant point. 


Thanks for yall who helped... still not quite there tho


ps - oh and RTrev: im not a complete noob (intermediate in fact) and everyone knows im not. so the teacher wont buy that :(

---

### Post by RTrev on 2007-10-21
> **oomar said:**
> RTrev: what recovery options?

Well, what I think we were all suggesting was to boot from the live CD, at which point you have the ability to get a terminal command line environment.  At that point you should be able to create a directory, mount the drive in question, and access the files you need.  You should then be able to copy them to a USB, or to another drive if you have one to mount, or to another machine if you install an ftp program, and so on.  Make sense?

> and for those who suggested me uploading to an ftp: Its 68 gigs of stuff. My offsite ftp is like 50gb. my regular ftp IS this computer. And I have most of it backed up but the way i organized it on this pc took me a LOng long time.... i may just get a new hard drive and install on that and then copy so as not to copy it off and then BACK to this one.... and who ever posted on my word choice of ruined pc vs os: good but ultimatly irrelevant point. 

Oh, I didn't know that. 68 GB would take a while to upload!  Just fyi, for $10/month I have 250GB of disk space available from my 1&1 hosting provider.  Plus 100 MySQL databases, 2500 mailboxes, and so on.  I thought that was typical.  If all else fails, I can give you an FTP account on my server so that you can upload your material temporarily until you can find a place to put it.  All you have to do is get access to the file(s), and from the Live CD install an FTP program.  Would that work for you?  Albeit slowly?  <g>

Not making light of your situation, just trying to find a way to help....

> ps - oh and RTrev: im not a complete noob (intermediate in fact) and everyone knows im not. so the teacher wont buy that :(

Okay, so much for that idea. <grin>

Bob

---

### Post by RTrev on 2007-10-21
Just a quick p.s.

Even experienced users sometimes forget to make backups, or make them but don't test that they are restorable.  I'd still ask the teacher for a break.. I'll bet he/she has made the same mistake at some point in their life!

---

### Post by RTrev on 2007-10-21
One more quick p.s.

I'm on the East Coast of the U.S., and it's about 11:40 PM here.  I'll help you out if I can, but I'll be going to bed soon, so if you want an FTP account on my server I'd better hear back quickly.

Maybe someone else will step in with a better rescue idea.  Anybody??  This poor guy needs help!

---

### Post by oomar on 2007-10-22
TRev: I also use 1 &1. and i have a server its just small and rather than waste my time AND yours uploading im just goin to have to copy it to my PHDD. im just gion to figure out what was installed before i screwed it up and then reinstall... i might reinstall feisty or gusty... im not sure... tho so far gusty is sounding EXTREMLY buggy... anyway. thank you for all of your help.... looks like i couldnt find a quicker way than this....

---

### Post by RTrev on 2007-10-22
> **oomar said:**
> TRev: I also use 1 &1. and i have a server its just small and rather than waste my time AND yours uploading im just goin to have to copy it to my PHDD. im just gion to figure out what was installed before i screwed it up and then reinstall... i might reinstall feisty or gusty... im not sure... tho so far gusty is sounding EXTREMLY buggy... anyway. thank you for all of your help.... looks like i couldnt find a quicker way than this....

Well, soon-to-be Doctor, I hope it all goes well.  If I were going to step back to an earlier version, I think it would be Edgy.  I think Feisty was the absolute low point in Ubuntu's history, and I seem to recall Edgy as being fairly stable.  Either way, good luck.. and I'm standing by if there's anything I can do to help.

It must be *awful* to reach the point of a Ph.D. dissertation, and then *lose* the thing!  :(

---

### Post by oomar on 2007-10-22
lol... portable hard drive disk? lol... not sure if u were serious with the PHD thing or not...

---

### Post by RTrev on 2007-10-22
> **oomar said:**
> lol... portable hard drive disk? lol... not sure if u were serious with the PHD thing or not...

Portable Hard Disk Drive, PH.D. Dissertation..  too many acronyms for me to handle.

Seriously, I thought you were talking about losing your dissertation.  Not sure quite how I got *that* idea in my head, but I did.  <g>

I  think it was the fact that it was 68G in size, or something like that, that led me to think it wasn't your average term paper.  :)

But it doesn't really matter.. it's important to you, so I hope you can get it back!

---

### Post by PARO on 2007-10-23
When you do reinstall Ubuntu, you should probably set a partition to use for personal data in the future so you wont have to worry about deleting all those files every time you do a clean install, then you can back up your program settings and stuff in your home folder too and not have to worry about losing anything important in a situation like this in the future.

---

### Post by PARO on 2007-10-23
Oh, and i agree with RTrev, Edgy was much more stable for me.  Feisty has been oddly unpredictable for me... one might even say it's been "feisty" ;)

---

### Post by oomar on 2007-10-23
lol thanks guys... and im 14 in my freshman year in high school... soooo im WAY FAR AWAY from a Ph.D... lol and good idea PARO.

---

