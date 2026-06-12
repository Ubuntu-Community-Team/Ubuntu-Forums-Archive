---
title: "will NOT install alongside windows 7"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by theHands on 2012-03-28
I thought I'd try ubuntu 11,10 alongside my faithfull windows 7.

I previously tried ubuntu 10 about a year or two ago, but didnt get on with it much.

So, wanted to give 11 a go, to see if it improved enough for a common user to use.

Well....

Ive tried installing it about 5 times, following intructions..
but it will not install.
I tell it to install along side windows 7...
but after it restarts, i get:


'error: no such partition.''


im once again sick and tired of half baked ubuntu.

and no im not flaming..
im just flaming disgusted how shoddy ubuntu STILL is.

why wont it install alongside windows 7, and create the boot menu, like its advertised as being able to do??

then again.. why do i care..
ubuntu has failed me for the last time.

note to whoever designs this stuff:
feel free to keep your wonderfull os..

and i'll use mine, that works



You may ask, as you often do  'why use it if its no good for u then'

ever heard of suchna  thing as TESTING?
how do i know til i try?

and it looks interesting.. at least worth tinkering with every now and then..
BUT
when the very first thing i try to do.... installation, fails..
im disgusted once again.


thanks

---

### Post by darkod on 2012-03-29
You can investigate if you want to. If not, your choice.

There are many things that can happen, and not all of them connected to ubuntu. Sometimes it is up to how windows has configured your disk, for example if it's Dynamic and not Basic. Although it doesn't sound like that in this case.

---

### Post by mastablasta on 2012-03-29
so is there a support question or just ranting?
 
you can first try the system by booting it into live session (from CD or USB) without install and if it all works work from there on...
 
but "my computer is not working" won't help any troubleshooting: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
for starters we need to know if your computer is Linux compatible or a Windows only kind of mashcine.

---

### Post by theHands on 2012-03-29
> **mastablasta said:**
> so is there a support question or just ranting?
 
you can first try the system by booting it into live session (from CD or USB) without install and if it all works work from there on...
 
but "my computer is not working" won't help any troubleshooting: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
for starters we need to know if your computer is Linux compatible or a Windows only kind of mashcine.

ta,

its not ranting.
how else do i get my message across?

Yes my computer is linux compatible, as i say, i had ubuntu 10 running in there before.

As i remember, that also screwed up my booting procedure, and its never been the same since.


But i did a full wipe, removed my other hard drive, so the computer was only working with one, installed windows 7 fresh, then installed ubuntu (from the live session screen one one occasion, so yes, the live session works) next to it, chose my partition size for ubuntu, waited, but got that error everytime it booted up.

Windows 7 booted up ok until i added linux, then neither worked.

ive tried this with two different ubuntu 11 iso's, and from a usb, and from a burnt cd....
it just fails.

why would i bother 'trying' something out that gives me so much grief??

yes it looks interesting, but as i say...
who would bother when it cant even sort out the fundamentals like booting??


I've installed a fresh windows 7 for about the 5th time now..
and im highly dubious about risking ubuntu  with it again.

After ubuntu messed up the boot, even the windows 7 repair boot disc failed to fix it.

again, why would i keep wasting my time, and risking my fresh installation?

if you cant give me a solution thats guaranteed to work before I try it, i will just use windows (which does all  need it to anyway) and save myself the grief.
As i say, i just wanted to have a small linux os so i can use it sometimes & try to feel my way around it at my LEISURE.
but its just to much bother.. again.

again, its NOT a rant, just a statement.

---

### Post by darkod on 2012-03-29
If you want advice you must provide information instead of just making long posts with no actual information. You can run the boot info script from the link in my signature. Post the results as explained there. You can do all that from ubuntu live mode.

That will show more details about your setup. Run the script with all disks connected, if you have more than one.

---

### Post by theHands on 2012-03-29
> **darkod said:**
> If you want advice you must provide information instead of just making long posts with no actual information. You can run the boot info script from the link in my signature. Post the results as explained there. You can do all that from ubuntu live mode.

That will show more details about your setup. Run the script with all disks connected, if you have more than one.

Thanks, i didnt see that link..
 thought it was your signature..

I will have to try to run the test from the session cd later.

---

### Post by darkod on 2012-03-29
No problem. Unfortunately any OS install can run into problems. We need to see if we figure out something from the details of your system.

When dual booting things sometimes don't work as expected by default. Think of it this way. If you had linux installed first and then install windows, it will never detect it and it will boot only windows, right? So in a way, it will not create a dual boot menu for you too.

But this is not a competition between windows and ubuntu, lets try to figure out why it doesn't work as expected for you.

---

### Post by theHands on 2012-03-29
> **darkod said:**
> No problem. Unfortunately any OS install can run into problems. We need to see if we figure out something from the details of your system.

When dual booting things sometimes don't work as expected by default. Think of it this way. If you had linux installed first and then install windows, it will never detect it and it will boot only windows, right? So in a way, it will not create a dual boot menu for you too.

But this is not a competition between windows and ubuntu, lets try to figure out why it doesn't work as expected for you.


I cant follow the directions to run the boot info script..
its linux fault yet again..


there is no .exe file.
So i have to work out how to extract it..
I exctracted it to my ubnuntu desktop..
then managed to find the terminal, and added that code... but it said 'no such file or directory'
I have no idea what the path to my ubntu desktop is called..
so i cant find it...
WHY cantlinux just be simple??
gos it madness

WHAT is wrong with an .EXE file?

---

### Post by darkod on 2012-03-29
The file is executable, the extension .exe is used in windows.

If the .sh file is extracted on the desktop, the path to execute it in terminal is:

sudo bash ~/Desktop/boot_info_script*.sh

Make sure to type everything exactly, linux makes difference between capital letters and small caps.

---

### Post by theHands on 2012-03-29
> **darkod said:**
> The file is executable, the extension .exe is used in windows.

If the .sh file is extracted on the desktop, the path to execute it in terminal is:

sudo bash ~/Desktop/boot_info_script*.sh

Make sure to type everything exactly, linux makes difference between capital letters and small caps.

if its executable, why do i need to use terminal at all??

its madness to me..

i'll give it one more go..
if it doesnt work..
im done with it.


thanks

---

### Post by theHands on 2012-03-29
I manged to do it.. i think.

here are my results:

''                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   488,394,751   488,187,904   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        4EAE67B0AE678EF1                       ntfs       
/dev/sdb2        822E6C922E6C8151                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

''

hope thats correct.

I just have to add..
i dont want to learn that terminal code..
i just dont.
people keep telling me using the terminal isnt neccesary, yet i keep being told to go there to do stuff.

can you verify, is it needed or not?
i have no intention or desire to learn the terminal coding just to get stuf done.

thanks

---

### Post by mastablasta on 2012-03-29
> **theHands said:**
> if its executable, why do i need to use terminal at all??

 
you can also use run programme in "run" window if that makes you happier. the point is you need to elevate yourself to root first that's the "sudo command" and the bash command enables to run a script. 
 
you probably don't know but there are programmes in windows that also need command line.

---

### Post by darkod on 2012-03-29
Sometimes things are executed faster and easier in terminal, sometimes it is needed. It depends.
Even in windows sometimes you need to run things in the command prompt. Depends how you use your computer. I work as System Administrator and need to run things in the command prompt in windows too, not everything is designed for double-click.

But if you only use the internet and write documents, you never need manual commands both in windows and ubuntu.

Anyway, here is why it didn't install properly:
```

Drive: sda __________________________________________________  ___________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

[COLOR=Red]Invalid MBR Signature found.[/COLOR]
```

One of your disks has invalid Master Boot Record.

Since you are so big enemy of the terminal, I can't be sure what is the best way to fix this. There are programs to fix it, but in terminal. And this has nothing to do with ubuntu, the hdd MBR is corrupted.

If you have no important data on that disk /dev/sda, and don't want to touch the terminal, then you can try in ubuntu live mode, open Gparted, select /dev/sda, make sure it is the correct disk selected, and then from the menu Device select Create Partition Table... That will create new msdos partition table by default. I think that should fix the invalid error. Note that this will erase all data on that disk, so don't do it if you have data to save.

If you decide to do that, after you are finished you can run the script again to see if the invalid message is gone, or a faster way is to try in terminal:
sudo fdisk -l (small L)

That will show just that part of the results and again you will need to see if the invalid message is present or not.

If it is gone, installing ubuntu on that disk should work fine.

---

### Post by theHands on 2012-03-29
> **mastablasta said:**
> you can also use run programme in "run" window if that makes you happier. the point is you need to elevate yourself to root first that's the "sudo command" and the bash command enables to run a script. 
 
you probably don't know but there are programmes in windows that also need command line.

i dont know what or where the run window is either.

all i know is, if i need 'elevated rights' in windows 7.. i just have to click my mouse to get it.

im sorry, but as far as im concerned, you have to understand this.

whether you like it or not, windows has probably 99% OS userbase.
So if linux want to become more popular, they have to adopt some things that windows users are used to.
using the MOUSE to do things is pretty much on top of the list.

They cannot expect people to waste thier time re-learning 'sudo's' and 'grubs' just to get elementary things done..
things they could have done instantly in windows

Im just telling u from my experience.
I'm not biased, i will use what works..
and boy, i can tell you..
linux is riddeld with problems for the 'common' user.
absolutely riddled.

---

### Post by mastablasta on 2012-03-29
It's correct.
 
you have two hard disks inside which means you need to put the grub boot loader on the correct disk during linux instal.
 
Since it works well in live mode it will work well in install too. you just need to install it correctly.
 
> **theHands said:**
> I just have to add..
i dont want to learn that terminal code..
i just dont.
people keep telling me using the terminal isnt neccesary, yet i keep being told to go there to do stuff.
 
can you verify, is it needed or not?
i have no intention or desire to learn the terminal coding just to get stuf done.
 
thanks
you don't have to learn it you can copy paste it to terminal. you porbably dont' know this but linux uses various desktop enviroments (DE) and each DE has stuff in different places. however commandlines work in all of them. even servers thta are CLI only (usualy). so if someone else has the same problem using Kubuntu instead of Ubuntu or maybe even Debian they can use same commands.
also it's faster for you to copy &paste one command instead of doing a number of clicks.
 
FYI i am not a command line fan or expert either. but i udnerstand it's use.
 
If you just want to use linux for tinkering and to discover it i suggest this kind of install: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
it has many shortcomings of real install but for toying a bit with it it's an easy, safe and good way in my opinion.
 
this is also a good place to start before attempting any install: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
 
just to see how system actually works and what are the differences.
 
 
in the end, why bother with linux if Windows works just fine for you? I too am using it on one of computer. and since it works ok and does what i need i don't need to replace it yet.
 
yes you can test it and this is good because it means you want to expand your knowledge. but at the moment you are testing it with trial and error which is also good, but time consuming as you've found out. i really suggets to try and read a bit about the OS first. at leats to get some basic understanding of how it works. plenty of oyur quesitons will be answered. trust me. afterall you weren't born with windows 7 knowledge either. someone had to teach you or you read a book about it.):P

---

### Post by theHands on 2012-03-29
> **mastablasta said:**
> It's correct.
 
you have two hard disks inside which means you need to put the grub boot loader on the correct disk during linux instal.
 
Since it works well in live mode it will work well in install too. you just need to install it correctly.
 

you don't have to learn it you can copy paste it to terminal. you porbably dont' know this but linux uses various desktop enviroments (DE) and each DE has stuff in different places. however commandlines work in all of them. even servers thta are CLI only (usualy). so if someone else has the same problem using Kubuntu instead of Ubuntu or maybe even Debian they can use same commands.
also it's faster for you to copy &paste one command instead of doing a number of clicks.
 
FYI i am not a command line fan or expert either. but i udnerstand it's use.
 
If you just want to use linux for tinkering and to discover it i suggest this kind of install: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
it has many shortcomings of real install but for toying a bit with it it's an easy, safe and good way in my opinion.
 
this is also a good place to start before attempting any install: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
 
just to see how system actually works and what are the differences.
 
 
in the end, why bother with linux if Windows works just fine for you? I too am using it on one of computer. and since it works ok and does what i need i don't need to replace it yet.
 
yes you can test it and this is good because it means you want to expand your knowledge. but at the moment you are testing it with trial and error which is also good, but time consuming as you've found out. i really suggets to try and read a bit about the OS first. at leats to get some basic understanding of how it works. plenty of oyur quesitons will be answered. trust me. afterall you weren't born with windows 7 knowledge either. someone had to teach you or you read a book about it.):P

Thanks,

well, i can tell you absolutely, i have installed it correctly over 5 times..
and it will not work.

I have installed ubuntu before, and its not hard to do.

I can gurauntee you it will not work if i install it again..
and im not going to ruin my windows yet again to prove my point.

there is a problem, and that log clearly didnt pick it up.

nevermind..
this has become far to much of an issue to bother with, i agree.



im also not sure i agree with your '''you werent born witrh windows 7 knowledge either'' comment.
heres why:

Google android is pretty easy and intuitive, as is apples tablet software.
(and yes, i know android is linux, but its a different ball game compared to linux pc os's)

my point is, both android and apple are intuitive and user friendly.
like windows 7..
but not like ubuntu.

linux reminds me of msdos.. something i never learned, and never wanted to learn.

i can only go by common user experience as i say.
yes, all os's can take a while to learn.
but ever since msdos became a thing of the past, none have been as frustrating or daunting, just to do simple things , as linux.


thanks for the  suggestions.

p.s.. no idea what a 'cli' is, but im not that fussed.
i can see the use for the termninal for the cross section of linux os's.. but where does that leave the common non-hobbyist user?
exasperated.

Thanks

---

### Post by mastablasta on 2012-03-29
> **theHands said:**
>  
all i know is, if i need 'elevated rights' in windows 7.. i just have to click my mouse to get it.
 
im sorry, but as far as im concerned, you have to understand this.
 
whether you like it or not, windows has probably 99% OS userbase.
So if linux want to become more popular, they have to adopt some things that windows users are used to.
using the MOUSE to do things is pretty much on top of the list.

 
yes that is true. and malware creators know this and exploit this. clickety click and malware is running. can't do that in linux. also in windows any .exe file is automaticly executable. though it needs admin password these days to execute it is still already marked as executable and admin password can be overridden. while in linux any file can be executable if administrator says so. if no password is given for that, file can't be run. additionally the true root password in Ubuntu is hidden and unknown. only users password with elevated privileges is known. so user could in theory get infected but not core system files (as i understand it). 
more reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
also undertsand that linux is server software moved into desktop. while windows is desktop os moved to do server stuff. as a result it is much more secure than windows. though 7 i hear is quite good in this respect.
 
like i said if you want to have more windows like environment (where all or plenty options are out there in GUI) use Kubuntu. Gnome (default ubuntu) deliberatelly hides settings from user so as to not overwhelm them. since like you i intend to otuch comman line as little as possible i use Kubuntu where i do most (like 99% things) in GUI not terminal.
 
also i think to run with root you could use right click and then run as root (with elevated privileges), but in the casse of bootinfoscript you owuld still need to tell it to run bash script.

---

### Post by mastablasta on 2012-03-29
> **theHands said:**
>  
my point is, both android and apple are intuitive and user friendly.
like windows 7..
but not like ubuntu.
 

 
really? have you ever installed android and apple from scratch in dual boot?
 
you should try a PC with Ubuntu preloaded. they say it's great.
 
CLI = Command line interface
GUI = Graphic user interface
 
boot info script doens't show anything wrong (my opinion but someone more experienced in script will tell you more) as there is no linux install there.

---

### Post by theHands on 2012-03-29
> **mastablasta said:**
> yes that is true. and malware creators know this and exploit this. clickety click and malware is running. can't do that in linux. also in windows any .exe file is automaticly executable. though it needs admin password these days to execute it is still already marked as executable and admin password can be overridden. while in linux any file can be executable if administrator says so. if no password is given for that, file can't be run. additionally the true root password in Ubuntu is hidden and unknown. only users password with elevated privileges is known. so user could in theory get infected but not core system files (as i understand it). 
more reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
also undertsand that linux is server software moved into desktop. while windows is desktop os moved to do server stuff. as a result it is much more secure than windows. though 7 i hear is quite good in this respect.
 
like i said if you want to have more windows like environment (where all or plenty options are out there in GUI) use Kubuntu. Gnome (default ubuntu) deliberatelly hides settings from user so as to not overwhelm them. since like you i intend to otuch comman line as little as possible i use Kubuntu where i do most (like 99% things) in GUI not terminal.
 
also i think to run with root you could use right click and then run as root (with elevated privileges), but in the casse of bootinfoscript you owuld still need to tell it to run bash script.

but linux is trying to  make more things accesible by just using mouse.
putting them in the same 'harms way'  as windows.?

so i was thinking it starts to sound like an excuse.
satying 'oh, we dont use executable files, cos its risky'
then later proudly saying 'we are getting more and more executable files into linux!'

trying to sound 'best' either way..

again, i could be wrong.. but makes me wonder.

also.. as i say, people are just used to thing working a certain easy way.
they dont like  feeling like theyve taken a step backwards into the early 90's.
even if its for 'security' reasons i guess.

im drawn to linux because its nice looking, supposedly 'safer' but im not sure about that.. perhaps its safer because its just not popular enuff for hackers to bother with as much.

and im also drawn to it for its 'free as the wind' approach
i like this style..
but its just to much of a hairpulling nightmare just to use it as a simple OS i can relax with.


bottom line..
hairpulling half empty and frustrating.

in my  'commmon' user opinion

---

### Post by theHands on 2012-03-29
''really? have you ever installed android and apple from scratch in dual boot?''

dunno bout that..
but as a common user experience, you tell me whats easier to learn and simply USE on a day to day basis.

---

### Post by darkod on 2012-03-29
In all your heated exchange to bash linux, I guess you didn't even see my post #13 that you have an invalid MBR signature on the hdd. That's why it doesn't work.

Especially if you are only replying here by email, it's easy to miss a post because you only get notification about the first post after your visit. Visit the forum and read all posts, not only by email.

In case you are interested repairing your disk at all, I see you are more interested doing something else here...

---

### Post by theHands on 2012-03-29
> **darkod said:**
> In all your heated exchange to bash linux, I guess you didn't even see my post #13 that you have an invalid MBR signature on the hdd. That's why it doesn't work.

Especially if you are only replying here by email, it's easy to miss a post because you only get notification about the first post after your visit. Visit the forum and read all posts, not only by email.

In case you are interested repairing your disk at all, I see you are more interested doing something else here...




i think the 'damaged' disc is the one i took out.
but you said to put them all in anyway, so i did.

actually the linux install would not work even when i just had one disc in there as i said.

unless of course its my healthy one thats 'damaged'
but how?
windows 7 is running from it ok..and it  goes wrong when linux is installed on it.

'doing something else here' eh?
expressing my opinion??
oh god forbid that in a linux forum. lol

thanks for the help

p.s.

i think the damage also came from me trying to install linux a while back.
as i said, it screwed it up.
so if you know a fix for that also, please let me know.
The disc wont allow me to choose it as a bootable option in my bios.
even though ive  formatted it many times, even with kill disc.
god knows what happened to it.

oh well..
i have my windows 7 in ok.. and i can use my other hard drive just for storing data on.

will do i guess

---

### Post by darkod on 2012-03-29
You expressed your opinion in the first post, no need to repeat it in every. Focus your posts in solving your problem, if that's what you want to do. If not, don't waste my time please. That's all I am asking, I'm not trying to make you love linux. Just don't waste our time if you have no intention to fix this.

Know of a fix? Did you read that post?

If you have no data on the 160GB disk did you try writing a new partition table on it? Did you check if the invalid signature message still exists after that? This is the information we need, not your constant complaints. Without even getting into whether they are justified.

And if you tried to install on the 250GB disk, I have no idea how you did it but there are no linux partitions on that disk, you can see that yourself. It has two ntfs partitions taking up the whole disk. So where is the unallocated space where you tried to install ubuntu and where are the partitions it would create? Even if it did not create any partitions, you would still have the unallocated space right? Windows is taking up that whole disk and there is no clue that ubuntu was ever attempted to be installed there.

---

### Post by theHands on 2012-03-29
> **darkod said:**
> You expressed your opinion in the first post, no need to repeat it in every. Focus your posts in solving your problem, if that's what you want to do. If not, don't waste my time please. That's all I am asking, I'm not trying to make you love linux. Just don't waste our time if you have no intention to fix this.

Know of a fix? Did you read that post?

If you have no data on the 160GB disk did you try writing a new partition table on it? Did you check if the invalid signature message still exists after that? This is the information we need, not your constant complaints. Without even getting into whether they are justified.

And if you tried to install on the 250GB disk, I have no idea how you did it but there are no linux partitions on that disk, you can see that yourself. It has two ntfs partitions taking up the whole disk. So where is the unallocated space where you tried to install ubuntu and where are the partitions it would create? Even if it did not create any partitions, you would still have the unallocated space right? Windows is taking up that whole disk and there is no clue that ubuntu was ever attempted to be installed there.

its not constant complaining.
its was a discussion. i get replies, then i answer with another'

i was consdering running another check, now i have formatted and allocated the 160gb 'faulty' drive.

i will do it then..



as for the 250 gb..
of course there is no linux on there!
it wont install, i told you
if i do install it, then it fails, and i cant even acess my windows 7 from it.
at present, windows 7 is on it and seems healthy. but if i install linux on it, even with the 160gb disc REMOVED,  it still wont work.

nevermind, im personally fed up witrh being accused of 'bashing' something, when im just giving my user experience of it.

i thought feedback may actually help people to realize what needs to be improved..

'bashing'
yea..  ok


thanks

---

### Post by CharlesA on 2012-03-29
Polite note: Be respectful of other members.

---

### Post by mastablasta on 2012-03-30
> **theHands said:**
> of course there is no linux on there!
it wont install, i told you

 
you need to create an empty disk partition first (unformatted disk space) to do that propperly. if you installed it to existing partition or worse to NTFS you will get porblems. however if this is done to empty disk partition and if the install is done propperly it will never affect or touch windows.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
another option is to simply use Wubi which will install it in large virtual disk space.
 
a 3rd option is to use virtual box where you would cretae virtual system within your windows and install it there. you can then toy with it, mess it up completelly, yet it will not touch your windows install. once it's messed up beyond all recognition, you can simply delete it and reinstall.
 
regarding executable files - In ubuntu software is usually installed from repositories. just like smartphones have their appstore (which is not their invention), Ubuntu has software center (i.e. package manager).  so executable files are actually not needed. only in rare occasion you would need to go out of repositories. 
 
for example i upgraded a supertuxcart game using repositories. didn't work for some reason on my graphics card. so i downloaded the latest version form the site, right click on it market it as executable, entered a password for that and then double clicked it. easy peasy.
 
windows has similar thing and it calls it attributes (command is attrib), however it is not as usefull as it doesn't prevent executing files. but you can make them read only etc.

---

### Post by theHands on 2012-03-30
Sorry, but im telling you, in my experience, windows is easier to use.
there is far less need to type stuff in a terminal type situation.

i think most people know this.. if only they would admit it.

Its simple -  the EXPERIENCE ive had.
what more proof do i need than that?.

people often advising me to go into terminal and type commands i have no idea what they mean..
i hardly ever - if ever get that with windows.

Is my own experience wrong?


plus the volume of software that doesnt even work properly on linux is staggering also.

I wont go on.. i will be accused of bashing again..
even tho im just replying to you.

As for installing.. well... I followed the installation instruction on the linux installer.
It let me resize me very new windows 7 partition.
a 250gb drive, with a fresh windows 7 on it, and i allocated just 25gb to ubuntu, so the windows partition really wasnt much disturbed.

but when booting up.. i get the error i posted.
neither windows nor ubuntu will work.

I know i didnt do anything wrong.
I actually managed - after some time - to get windows 7, xp, linux mint, and pingEee  quad booting on my netbook, and it works ok.

Ive got a new and updated windows 7 on my pc now, and im simply too dubious to ruin it by installing ubuntu on it again.

hope you understand, thanks

p.s.

I've noticed when linux does work , it works so well.

I enjoy zipping around the web on my netbook on linux.
It really does zip around.

Maybe thats why i get so dissapointed.
I see a lot of unrealized potential.

---

