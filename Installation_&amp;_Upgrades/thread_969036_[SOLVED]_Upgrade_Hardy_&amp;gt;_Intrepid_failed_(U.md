---
title: "[SOLVED] Upgrade Hardy &amp;gt; Intrepid failed (Used the Update manager)"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Noxn on 2008-11-03
I am now booting into the CLI, and it seems like EVERY program i ever had is gone (Thanks cleaning funktion in the upgrade).

And i heard that some ati grafik cards arent supported anymore or something, i think i got an Intel. At least thats what sysinfo and some command sez.

Is there anyway of getting it to work AND somehow get back my programs?


If that is not possible i will reinstall (backing up my home before of course).


Any help is apreciated!:KS




PS: Developers: Can you fix the "cleaning" thing in the upgrade please? Many people got all their programs removed because it thought they where "obsolete", it even removed some thing the system needed (i think).
Thank you.

PPS: Sorry to everyone if my english is bad, or if i didnt explain it good. My tool that fixes my spelling where in linux, not windows.

---

### Post by scragar on 2008-11-03
If you are talking of cruft remover it is currently being discussed in the bug report related to it, lots of people are unhappy with it since it doesn't do what is says and has a nasty side effect at that.

Anyway, if you still have a command line try running:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```to see if you can reinstall the desktop packages.


[Link to bug report if you're interested](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746)

---

### Post by Noxn on 2008-11-03
Im talking about the Upgrade thing in the Update manager, its "Cleaning" part just removed every "Obselete packages" (Wich means: EVERY PROGRAM I HAD).


Will that install firefox, nautilos, etc etc`?


BTW: Im in INTREPID now, but only CLI. Every program is gone.(Even gnome things)

---

### Post by lukjad on 2008-11-03
How about fortune? I know it sounds silly, but I just would like to know if only the essentials are there or if you have some "fluff" left. 

```
fortune
```

---

### Post by Noxn on 2008-11-03
Hmm, didnt test that.

But i think i dont have that too.

I will test later.

---

### Post by lukjad on 2008-11-03
If you don't, there probably is something seriously wrong. Just:

a) Reinstall 8.10
b) Reinstall 8.04

---

### Post by Noxn on 2008-11-03
Im waiting for scragars reply, and my plan B is reinstalling 8.10 after backing up my home.

---

### Post by lukjad on 2008-11-03
Good idea Backing up the /home folder. Make sure not to save the /home folder, just make sure not to save them as root.

PS scragar has replied, in The BUMP Thread.

---

### Post by Noxn on 2008-11-03
> **scragar said:**
> I think if apt-get is ubable to install the desktop then the only thing you can do is reinstall, sorry to hear about the bad experience.

EDIT: having now read your post, yes, it will(if it works) reinstall everything seen as a dependency to ubuntu-desktop, which includes firefox, gnome, evolution etc(all the stuff that comes on a freshly installed system).


BUMP

Yeah, okay.


Thank you all.
If that thing scragar said doesnt work, i will reinstall intrepid. but i will Backup *anyway*, just in case. ):P


THANK YOU ALL

---

### Post by lukjad on 2008-11-03
Yer welcome. ;)

---

### Post by Noxn on 2008-11-03
fortune doesnt work...

---

### Post by lukjad on 2008-11-03
can you tell me if
```
man apt
```
works?

---

### Post by lukjad on 2008-11-03
can you tell me if
```
man apt
```
works?

---

### Post by sisco311 on 2008-11-03
do you have a live cd?

---

### Post by Noxn on 2008-11-03
i can burn one.

and man works, and apt-get too.

> 
**FROM BUMPY THREAD:**
If i copy my entire home folder, with my damn hard drive mounted on that Usb folder in my home, wouldnt that like copy everything i have on the harddrive?.........

ALSO:
MY USB DRIVE -ISNT- MOUNTED.
Im in the CLI.

I mounted my HARDRIVE on instead of the USB..... On that folder that i just called USB because i wanted.


Damnit i feel so dumb, nobody understands me, or i dont understand you.


EDIT:
So my status is this:
Im in the cli.
I want to install that ubuntu-desktop package.
I want to backup first.
I failed to mount my usb stick and mounted my hard drive instead in a folder in my home, and now i want to know how i undo that/exclude USB folder from the backup, and FINALLY save my backup on my stick.

edit2:
This is what some command said about my mounted things:
/dev/sda1 > / (sda1 is my harddrive, i think, looks like it.)
/dev/sda1 > /home/noxn/usb
Something like that.


---

### Post by sisco311 on 2008-11-03
oh, ok you are in the cli.

post:
```
sudo fdisk -l
```
and
```
mount
```

---

### Post by lewac on 2008-11-03
one thing we do is an image of the ubuntu partition before any upgrading. thus if the upgrade fails in any way we can restore the partition to its exact state prior to the upgrade attempt. the easiest tool we've found for this is "partimage" which can be found here: [http://www.sysresccd.org/Download.en.php](http://www.sysresccd.org/Download.en.php)

---

### Post by Noxn on 2008-11-04
Lewac, i already upgraded, and i dont want to go back to the cli if it fails...

Yes sisco, did you read the whole thread? and at least the post before you?

What does you command do.



EDIT:
> **scragar said:**
> Morning everyone, did Noxn solve his problem?

Either way:
To exclude a directory(s) from tar use: ```
tar -cvf /homeBackup.tar . --exclude=**dir1** --exclude=**dir2**
```
And to umount your USB drive I think you can run```
umount /home/noxn/usb
```but honestly if it's not umounting I'd go mad and force it```
sudo umount -a -fl
```but that's not recomended.

BUMP
That just like solved all my problems...
Gonna do that, but i cant right now.

---

### Post by scragar on 2008-11-04
> **sisco311 said:**
> oh, ok you are in the cli.

post:
```
sudo fdisk -l
```lists storage devices and partitions> 
and
```
mount
```lists currently mounted partitions.

---

### Post by Noxn on 2008-11-04
okay, i made a list for me where i copied all commands i need:
(got it here in a TXT)
```
#Internet:
sudo ifconfig eth0 up
sudo dhclient

#umount 
umount /home/noxn/usb

#Backup:
cd ## go to home dir if not already in it
sudo tar -cvf /home/Backup.tar . ## back up current folder(the .) to a file called Backup.tar in /home
#with exclude.
sudo tar -cvf /homeBackup.tar . --exclude=dir1 --exclude=dir2

#FIX (I HOPE):
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Only thing i need to know now:
Where do i put the backup? if i dont find out what my usb stick is...
Couldnt i burn it with the cli or something?
I want to do backup even before installing ubuntu-desktop, just in case

---

### Post by scragar on 2008-11-04
Make the back-up first, then check it's size:

```
ls -l **/home/Backup.tar**
```
Then, provided it's small enough for your pen copy it over:
```
cp **/home/Backup.tar** /home/nozn/usb/
```
I have no idea about how to burn things from the command line unfortunatly, I've always used nautiluses built in option to do it. Sorry I can't help you with that.

---

### Post by Noxn on 2008-11-04
yeah, but, i still need to mount my usb...

i got no idea which sda to choose

---

### Post by Noxn on 2008-11-04
IDEA:
Make the backup and copy it on the stick with a live CD.

EDIT:
Not sure if that would work and i cant find my live cd.

---

### Post by Noxn on 2008-11-06
Hmm, my system doesnt seem to like my usb stick.
Cant mount it, or een find it.

Where could i copy my backup, then?
I mean, if the ubuntu-desktop package doesnt works as good as needed, i maybe need to reinstall... that would delete everything on the HD, so i cant save the backup there...


Any ideas?

---

### Post by sisco311 on 2008-11-06
> **Noxn said:**
> Hmm, my system doesnt seem to like my usb stick.
Cant mount it, or een find it.

Where could i copy my backup, then?
I mean, if the ubuntu-desktop package doesnt works as good as needed, i maybe need to reinstall... that would delete everything on the HD, so i cant save the backup there...


Any ideas?

i can help you to mount the usb stick if you post the output of:

```
sudo fdisk -l
```
```
dmesg | tail
```
and
```
mount
```

plug in the stick(and wait a few seconds) before you run the commands.

---

### Post by scragar on 2008-11-06
There is a lot to be said for running a liveCD to copy the information, and if all else fails you can always make a new tiny partition to throw the home folder on, which you can later set as your /home partition(really good idea BTW).

---

### Post by Noxn on 2008-11-06
Sisco, i already tried fdisk once as you said that one time.
and the only thing it listed was my hard drive (yes, the usb stick WAS pluged in)

---

### Post by Noxn on 2008-11-10
Okay, after days of doing nothing (bad noxn, you are very bad, *Slaps himself*) i finally tried with the ubuntu livecd... i couldnt copy my files.
But i could acces the harddrive.


Any linux distribution that ignores that?


OR IDEA 2:

Could i make the TAR file in the CLI in a way its not in my home? and with acces rights? so i could copy it later fromt the livecd...



Thank you all.

---

### Post by lukjad on 2008-11-10
Have you tried Slax?

---

### Post by Noxn on 2008-11-10
No, i wanted to try DSL now... or later...

Gonna try now.

---

### Post by Noxn on 2008-11-10
OOookaaaay... this is weird...

startx in DSL wont work... some error about X server or some file missing...
And on the second try on startx, i got a kernel panic, interrupt handler or something, and not syncyng.

System not responding, had to reset.


I think DSL just bluescreened me...

---

### Post by lukjad on 2008-11-11
I have two questions. 
1) Did it try to write pagefiles or write to a swap partition?
2) Did you check the CD for defects? (MD5sum)

---

### Post by Noxn on 2008-11-11
?

Umm, the ubuntu livecd worked fine, except i had no right to get my
files.
And DSL (Damn Small Linux) gave the kernel panic.


didnt understand 1 question

---

### Post by Noxn on 2008-11-11
UBER GOOD IDEA:

I Make a backup in the CLI, then i CHown (or something) my home folder so anyone can acces it, i boot into the livecd (ubuntu) and copy the backup to the stick, chown my home back to original state (just in case it works without reinstall) and then try the ubuntu-desktop package!


Now... how do i do that?

Could anyone tell me the required commands for the chown etc?
(Home/noxn)

---

### Post by Noxn on 2008-11-14
Solved.


Made backup and moved it to /home/, so i could copy it via lan to another PC.
I reinstalled.



/Thread

---

### Post by lukjad on 2008-11-14
Don't forget to mark this thread as solved.

---

