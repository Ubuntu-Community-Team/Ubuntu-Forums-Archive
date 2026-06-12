---
title: "Windows 7 and Ubuntu"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by SlashHeist on 2009-12-01
Hey all. I have Windows7 64bit on a new Asus U50a notebook with a 500gb hard drive. I'd like to be able to dual boot Ubuntu and Windows, choosing which OS at start up prefferably. 

[LIST]
[*]What Ubuntu should I use? I have 64 bit windows 7
[*]Should I use 64 bit Ubuntu 9.10
[/LIST]

When I tried this last time I did something wrong and I'm not quite sure what. So if you could link me to a detailed site or give me detailed instruction that be awesome. I have dual boot on my MacBook Pro and it works fine. Maybe I just suck with Windows idk.

Thanks in advance.

---

### Post by darkod on 2009-12-01
I use both 64bit, works fine.
For the install, I'm not sure about any detailed guide, maybe check on ubuntu.com.
I can give you the basic steps but first tell me how many partitions you have and what size? How are the 500GB split right now?

---

### Post by Megafag on 2009-12-01
> **SlashHeist said:**
> Hey all. I have Windows7 64bit on a new Asus U50a notebook with a 500gb hard drive. I'd like to be able to dual boot Ubuntu and Windows, choosing which OS at start up prefferably. 

[LIST]
[*]What Ubuntu should I use? I have 64 bit windows 7
[*]Should I use 64 bit Ubuntu 9.10
[/LIST]

When I tried this last time I did something wrong and I'm not quite sure what. So if you could link me to a detailed site or give me detailed instruction that be awesome. I have dual boot on my MacBook Pro and it works fine. Maybe I just suck with Windows idk.

Thanks in advance.

Install windows first wiping everything and forming one partition (backing up might not be such a bad idea.) then simply install ubuntu.

the installer gives you the option to choose to put the operating systems side by side, and all you have to do is choose the one you want on startup. 

i would suggest the latest ubuntu "Karmic Koala".

EDIT: it is a very bad idea to install ubuntu first as restoring the bootloader can become a pain in the ***.

---

### Post by u.b.u.n.t.u on 2009-12-01
Download a copy of ubuntu-9.10-desktop-amd64.iso (or a variant of the desktop 64 bit) then either burn it to a CD or use a CD emulator to create a virtual drive.

Once you can see the contents of the CD click wubi.exe. When it requests internet access, agree.

Ubuntu will install, connect to the net (not sure why as they don't explain!) and then request a reboot. Do this. At boot Ubuntu will continue to install and the process is excellent.

At the end you will have Ubuntu 9.10 installed. If at any time you wish to remove Ubuntu 9.10, simply go to the add/remove software of Windows and uninstall as per any other program.

The default boot option structure is Windows first. You are given time to choose between that and Ubuntu.

---

### Post by darkod on 2009-12-01
> **Megafag said:**
> Install windows first wiping everything and forming one partition (backing up might not be such a bad idea.) then simply install ubuntu.


With all the respect to Megafag, if what you mean is create one partition on the WHOLE disk, that is a very bad idea. First of all, why create ntfs partition on the whole drive when you are planning to shrink it in order to have dual boot. On top of that, having a second ntfs partition (with larger size, depending on hdd size) is always a good choice first of all for keeping data in case you need urgent clean install of windows on the system partition. As added bonus, this ntfs can be read from ubuntu and it can serve for file transfer between the two OSs and ubuntu can write and read data on it too.

If it helps you get some idea, here's what I have on 250GB disk (233GB effective)
65GB ntfs primary win7 system
141GB ntfs primary data
15GB ext4 primary / ubuntu 9.10
extended
2GB logical swap
10GB ext4 logical /home

It all depends what do you need and how you use your computer. You can dedicate as little as 20-25GB for ubuntu if you need loads of space for windows. Or the other way around, give loads of space to ubuntu.

---

### Post by darkod on 2009-12-01
> **u.b.u.n.t.u said:**
> 
Once you can see the contents of the CD click wubi.exe. When it requests internet access, agree.



The OP wants to dual boot, not run wubi inside windows. Please don't confuse things additionally. Wubi is never recommended as long term install and should not be relied upon. The Ubuntu website itself says "wubi is easy way to TRY ubuntu" where the key word is TRY. Not to use it like that permanently.

---

### Post by Megafag on 2009-12-01
> **darkod said:**
> With all the respect to Megafag, if what you mean is create one partition on the WHOLE disk, that is a very bad idea. First of all, why create ntfs partition on the whole drive when you are planning to shrink it in order to have dual boot. On top of that, having a second ntfs partition (with larger size, depending on hdd size) is always a good choice first of all for keeping data in case you need urgent clean install of windows on the system partition. As added bonus, this ntfs can be read from ubuntu and it can serve for file transfer between the two OSs and ubuntu can write and read data on it too.

If it helps you get some idea, here's what I have on 250GB disk (233GB effective)
65GB ntfs primary win7 system
141GB ntfs primary data
15GB ext4 primary / ubuntu 9.10
extended
2GB logical swap
10GB ext4 logical /home

It all depends what do you need and how you use your computer. You can dedicate as little as 20-25GB for ubuntu if you need loads of space for windows. Or the other way around, give loads of space to ubuntu.

I believe when it installs ubuntu partitons the hard-drive anyway and is a far more noob-friendly way then using gparted ect

but listen to this man, he has been here longer than me.

EDIT: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

this isnt such a bad idea either.

---

### Post by Cavsfan on 2009-12-01
I am dual booting Windows 7 64 bit and Karmic Koala 64 bit.
I know more about windows than ubuntu right now, but
you need to get into (In windows 7)
disk manager (you can search for it just above the start button)
then you need to "shrink" the C: disk allowing enough room for Ubuntu 
to be installed. If you have files at the end of the drive, you cannot do it.
you will have to defragment it (I sugest Defraggler, which I use.
You will see if it defragments enough for you to "shrink" the volume.

You want to make sure you choose the bottom option when installing 
Ubuntu. I have 4GB ram and made my swap file twice the size of my ram, 
so I made my swap partition 8192 (1024 X4 X 2)
Then made by ext4 partition about 100GB with a "/".
Windows 7 has the rest.

Wow, finally something I might be able to help someone else with!

---

### Post by darkod on 2009-12-01
> **Megafag said:**
> I believe when it installs ubuntu partitons the hard-drive anyway and is a far more noob-friendly way then using gparted ect


You are right about that. Unfortunately the line between is very thin. :) I've seen loads of posts complaining how the shrinking corrupted windows, and it really can sometimes. Especially if doing it with the ubuntu installer in one go. It will shrink windows bit to make room for ubuntu, and proceed to install right away. Then you reboot and figure out windows isn't working and you blame ubuntu of course. :)

In lots of situations windows simply complains about it's famous disk checks after the shrink, and because ubuntu install was all one step, no opportunity to boot windows few times after the shrink.
That's why I avoid shrinking system partitions if I can. And clean install is perfect to avoid that, just create your windows partition with the size you want, and that's it.

---

### Post by darkod on 2009-12-01
> **Cavsfan said:**
>  If you have files at the end of the drive, you cannot do it.


This is another valid point to avoid shrinking if you can. Sometimes even non-movable system files are put at the back and windows disk management can't help you. I had 25GB free in vista and even after defragmenting it was offering to shrink 2GB. Great help. :)

Gparted might be new to windows users, but it can actually move data and because of that allows shrinking with the size of your free space, regardless where the data is. Of course, defragmenting helps the shrink to be faster.

---

### Post by OrangeCrate on 2009-12-01
> **SlashHeist said:**
> Hey all. I have Windows7 64bit on a new Asus U50a notebook with a 500gb hard drive. I'd like to be able to dual boot Ubuntu and Windows, choosing which OS at start up prefferably. 

[LIST]
[*]What Ubuntu should I use? I have 64 bit windows 7
[*]Should I use 64 bit Ubuntu 9.10
[/LIST]

When I tried this last time I did something wrong and I'm not quite sure what. So if you could link me to a detailed site or give me detailed instruction that be awesome. I have dual boot on my MacBook Pro and it works fine. Maybe I just suck with Windows idk.

Thanks in advance.

I too am dual booting Karmic and Windows 7, both 64 bit.

Here's a good explanation of how to do that (though these instructions mention Vista, it's the same for Windows 7):

> ** Dual-Booting Windows and Ubuntu**

Rarely, a user may experience problems dual-booting Ubuntu and Windows. In general, a Windows OS should be installed first, because its bootloader is very particular. A Windows installation usually occupies the entire hard drive, so the partition needs to be shrunk, creating free space for the Ubuntu partition. (You should clean up unnecessary files and defragment the drive before resizing.) The Windows partition can be resized from within Windows Vista using the shrink/resize option in the Administrative Tools --> Disk Management tool. If using Windows XP (or other Windows OS), use GParted partition manager to shrink the Windows partition and thereby leave free space on the hard drive for the Ubuntu partition.

After shrinking the Windows partition, you should reboot once into Windows prior to installing Ubuntu. This allows the Windows system to automatically rescan the newly-resized partition (using chkdsk) and write changes to its own bootup files. (If you forget to do this, you may later have to repair the Windows partition bootup files manually using the Windows Recovery Console.)

If done this way, there is no problem installing Ubuntu as the second operating system and it is done automatically from the Ubuntu LiveCD. Allow the Ubuntu LiveCD to install to "largest available free space."

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

I have a 250 GB hard drive. I cut out a 30 Gig chunk for Karmic, and Win 7 has the rest.

Good luck...

---

### Post by Cavsfan on 2009-12-01
to find disk management in Windows 7:
type in "disk man" in the search box above the "start button"
and you will see "Create and format hard disk partitions" at the top of the list.
**(if you type more than "disk man" the correct program will disappear)**
click on that and Disk management will open up.
You will see your disk along with any OEM backup 
(**do not touch this! or anything except C:**)
You right click on the C: drive and then "shrink".
It will show you how much room you can free up.
If it is not enough use degfraggler to defragment it until it looks contiguous and
there is a lot of "white" after the "blue" sectors.
then go back to Disk management and see if you can free up more space on C:.

---

### Post by Cavsfan on 2009-12-01
I am with you OrangeCrate!
I am on Windows 7, but did this myself on Vista before doing a fresh install of Windows 7 
and then a fresh install of Ubuntu.

The last post of mine is what has changed since Vista for Disk Management.

---

### Post by u.b.u.n.t.u on 2009-12-01
> **darkod said:**
> The OP wants to dual boot

A wubi install enables a dual boot. 


> **darkod said:**
> not run wubi inside windows

Wubi was not mentioned and so I mentioned it as an option to consider.

> **darkod said:**
> Please don't confuse things additionally.

My post was not confusing.

> **darkod said:**
> Wubi is never recommended as long term install and should not be relied upon.

Source?

> **darkod said:**
>  The Ubuntu website itself says "wubi is easy way to TRY ubuntu" where the key word is TRY. Not to use it like that permanently.

Your argument that "try" does not allow "permanent" (say 6 months in todays development cycle), is illogical.

I am not here to debate with you your views. I am here to offer my assistance for what it is worth to the OP and it is at their discretion what they decided to do with such.

---

### Post by Cavsfan on 2009-12-01
> **darkod said:**
> This is another valid point to avoid shrinking if you can. Sometimes even non-movable system files are put at the back and windows disk management can't help you. I had 25GB free in vista and even after defragmenting it was offering to shrink 2GB. Great help. :)

Gparted might be new to windows users, but it can actually move data and because of that allows shrinking with the size of your free space, regardless where the data is. Of course, defragmenting helps the shrink to be faster.

darkod, I had the same problem: I could not get the end of the drive clean. I found out 
that Vista stores it's user journal (whatever that means!) at the end of the drive and I had 
to use a fsutil command to delete the (C:\$Extend\$[I]UsnJrnl) file ([B]which was stored in the 
very last disk sector![/B]) Vista does not allow this file to be defragmented. The fsutil command 
I used deleted all of the restore points (which are so valuable in Windows OSs). 
But, I did it just to get the disk to where I could "shrink" the C: partition and install Ubuntu. 
Luckily, in Windows 7, MS fixed this problem. It apparently is a lot better and does not 
have any files that cannot be defragmented. :roll:
[/I]

---

### Post by OrangeCrate on 2009-12-01
> **u.b.u.n.t.u said:**
> 

<snip>

A wubi install enables a dual boot. 

Wubi was not mentioned and so I mentioned it as an option to consider.

<snip>


Wubi is certainly something for the OP to consider, but I believe that most people use it to evaluate Ubuntu, rather than use it as a long term solution for a dual boot.

(Why? Because if for any reason you lose Windows, Ubuntu is gone with it.)

In my opinion, it's not that much harder to do a classic dual boot, and if one operating system is borked, you at least have the other one to fall back on, until you can make repairs to the other partition/install.

---

### Post by u.b.u.n.t.u on 2009-12-01
Wubi has advantages and disadvantages like anything.

---

### Post by Cavsfan on 2009-12-02
> **darkod said:**
> [quote=Cavsfan]If you have files at the end of the drive, you cannot do it.
This is another valid point to avoid shrinking if you can. Sometimes even non-movable system files are put at the back and windows disk management can't help you. I had 25GB free in vista and even after defragmenting it was offering to shrink 2GB. Great help. :)

Gparted might be new to windows users, but it can actually move data and because of that allows shrinking with the size of your free space, regardless where the data is. Of course, defragmenting helps the shrink to be faster.[/quote]

darkod, running defraggler allowed me to see the physical sectors of the C: drive.
Which is why I used it. It also lets you click on a sector (like the last one) and see what it
contains. With Windows 7, the OP should have no problem defragmenting his C: drive 
enough to squeeze 110GB for his Ubuntu installation. He will be able to see that there is 
room at the end of the drive and when he attempts the shrink, he will be able to get the 
110GB. If it were Vista, he would probably have to deal with the fragmented $usnjrnl file.
On Vista this file keeps growing and growing and defies any defragmentation. Another 
reason Vista sucked!

---

### Post by darkod on 2009-12-02
> **u.b.u.n.t.u said:**
> 
I am not here to debate with you your views. I am here to offer my assistance for what it is worth to the OP and it is at their discretion what they decided to do with such.

I apologize if I sounded harsh. I consider myself still Ubuntu newbie first of all. But it's just that lately I've seen too many threads here about problems with wubi and tried to help, and by the look of them most problems would not have happened in non-wubi install. I even saw people giving up on ubuntu because of that. Of course, that can happen with the full install too.

And one of the most recent problems wuth wubi seems to be that update from 31-14 kernel to 31-15 (which pops-up for wubi users too), seems to be braking it. They end up with nonbooting system after that.

I repeat, I'm new to ubuntu myself (although I have used mandrake and fedora years ago), but IMHO I think the developers went too far in trying to please "windows" users. Yes, having options is great, but not at this cost. Not at the cost of kernel update braking it all up. And how does that look to the user deciding to give ubuntu a try? How many of them will turn away and ironically because you made a try to make linux work inside windows to make them happy, and some problems turned up?

IMHO the big step is the "fight" for people to start dual booting them side-by-side. And if someone has already decided to do that, sending him back towards installation inside windows, on ntfs, in a sort of VM, is contra productive. Plus with all the recent problems with wubi, I really can't recommend it if someone already asked for dual-boot.

And for users new to ubuntu it is greatly confusing them if both options (wubi and side-by-side) are advertised as equal. Yesterday on a thread here the OP is saying I have ubuntu installation. I asked him did you install trough wubi, because that's different, so we know what to advise you. He says, no, I have a full install. Then he gives the fdisk results, all partitions on all drives are NTFS. They actually start thinking it's the same.

You seem much more experienced then me in ubuntu. When I said dual boot I didn't mean just additional entry in the windows bootloader, but an actual side-by-side dual boot. You know what I mean. Also, for quoting sources, I was trying to keep things short, not write novels. :)

---

### Post by Mark Phelps on 2009-12-02
Just to throw in my 2-cents here as well ...

I too had read the Wubi-is-only-for-trials claims numerous times and assumed that these came from the Wubi documentation.  But in checking the two sources I could find (Wubi site and Wubi Wiki Guide) there really isn't any statement to the effect that it should ONLY by used for trying Ubuntu. So, I've been wrong in this claim as well.

However, I personally STILL recommend AGAINST using Wubi, especially when combining a new Win7 install (the one using the new recovery partition), Wubi, Ubuntu 9.10, and GRUB2.  This combination seems to be fraught with problems -- at least, if the high number of posts complaining about not being able to boot into Ubuntu after a Wubi install are any indication.

It would be a real shame if folks first (and probably LAST) impression of Ubuntu was negative due to Wubi/Win7/GRUB2 conflicts.

---

### Post by brhokla on 2009-12-02
Quick Question.  I like the person above have a windows 7 64bit on a new machine, HP laptop.  I have made my Ubunut 9.10 disk and would like to install it.  I have a laptop with a internal 320gb 7200rpm drive and I also have a WD External HD hooked up through a usb port.  Can I install Ubuntu to the external drive and partition only it ;eaving all my computers C drive for Windows 7 and half of the 320 external for backup and for Ubuntu?  Will I get an option to install to the second drive or will the install go directly to my C:  or drive 1?  I also wonder what this will do when booting up when the external drive is not connected?  

Thanks for any help.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **darkod said:**
> I apologize if I sounded harsh.

No need to apologise. Text communication is rather limited and thus easily susceptible to less than ideal and intended understanding.

I have the following two guiding principles here:

1) those asking questions are genuinely seeking knowledge (which includes me) and 

2) those providing answers are genuinely seeking to assist (which also includes me).

Upon the above there is bound to be mutltiple paths to outcomes and ways to getting there ... does the left or right leg step first, for example.

The person asking questions today is the person answering questions tomorrow.

Your experience of wubi is most interesting. I have had the exact opposite experience where I have described wubi as "brilliant". I have however perhaps found one bug, and that is the automated download of an ISO when such is not needed and merely an installation is required.

My experience with Ubuntu is superflicial outside of my own experiences. I have at best "monitored" Ubuntu since the start and found release after release in a word, unusable. However I see the rapid improvement and rather than complain, try to contribute as best I can.

I am ok on Windows but not formally qualified. Just experience and including being an IT newspaper journalist for a time. One of my "sponsors" was Microsoft!

I however believe in open source and equate that to egalitarianism, giving everyone a fair go. The Microsoft model does not allow for that.

Thank you darkod

&#1073;&#1083;&#1072;&#1075;&#1086;&#1076;&#1072;&#1088;&#1103; *

* Googled. It should say "thank you".

---

### Post by u.b.u.n.t.u on 2009-12-02
> **Mark Phelps said:**
> However, I personally STILL recommend AGAINST using Wubi

Fair enough. I would suggest that at present there exists two schools of thought on the matter.

I hope that Wubi will continue to be developed and in time address your concerns.

I recommend Wubi as a general principle and in particular as long as certain criteria exit. A case by case basis depending on what the question is.

Cheers.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **brhokla said:**
> Can I install Ubuntu to the external drive and partition only it ;eaving all my computers C drive for Windows 7 and half of the 320 external for backup and for Ubuntu?

Yes.


> **brhokla said:**
> Will I get an option to install to the second drive or will the install go directly to my C:  or drive 1?

Ubuntu 9.10 will install on the HDD selected by the user.


> **brhokla said:**
> I also wonder what this will do when booting up when the external drive is not connected?

Error message.

Oh and ...

> **brhokla said:**
> Quick Question.

All three of them! ;)

---

### Post by Cavsfan on 2009-12-02
> **u.b.u.n.t.u said:**
> 
[quote=brhokla]Can I install Ubuntu to the external drive and partition only it ;eaving all my computers C drive for Windows 7 and half of the 320 external for backup and for Ubuntu?

Yes.

[quote=brhokla]Will I get an option to install to the second drive or will the install go directly to my C: or drive 1?[/quote]

Ubuntu 9.10 will install on the HDD selected by the user.

[quote=brhokla]I also wonder what this will do when booting up when the external drive is not connected?[/quote]

Error message.

Oh and ...

[quote=brhokla]Quick Question.[/quote]

All three of them! ;) [/quote]

u.b.u.n.t.u and darko,
You two seem to know a lot about this, I don't, but I am a pretty fast learner.
I cannot answer this person's question about the external drive. I know nothing about it. 
But, if that does not work out, some of the stuff I have in this thread might be of use.
I know windows fairly well, I am not an expert, but I can figure out what I need to 
figure out.

So, here's to helping these dual booters out! Cheers!
I can offer my experience from Vista or Windows 7 and you guys 
can help with the Ubuntu. Maybe, one day I will be able to help too!

---

### Post by darkod on 2009-12-02
He also posted separate new thread, I replied there. Without slapping his wrist for dual posting. :) Of course, he might be she, just easier to type like this. :)

---

### Post by Cavsfan on 2009-12-02
> **darkod said:**
> He also posted separate new thread, I replied there. Without slapping his wrist for dual posting. :) Of course, he might be she, just easier to type like this. :)

Yes, I see that he gave up on the Ubuntu install up and went back to windows. Too bad because if he would
have made sure the windows 7 install was good before doing the Ubuntu install, I think everything would 
have been fine as he made available the space, etc. 
Thanks for pointing that out. :-({|=

---

### Post by SlashHeist on 2009-12-02
> **Cavsfan said:**
> Yes, I see that he gave up on the Ubuntu install up and went back to windows. Too bad because if he would
have made sure the windows 7 install was good before doing the Ubuntu install, I think everything would 
have been fine as he made available the space, etc. 
Thanks for pointing that out. :-({|=

Im not sure if you were referring to me in that post or not, but I tried installing Ubuntu using someones advice and a few things went array, not blaming anyone but myself, so I couldnt even boot into Windows or Ubuntu so I was trying to fix everything. 

Eventually I got Windows working again and just wanted to make sure everything was in order. Now that I have windows working properly I am ready to install Ubuntu again. 

Sorry if I posted to many new threads, as you can tell I am new to the threads. =D I'll try to keep my posts together if they are similar. 

...And to everyone that posted, thank you so much for the advice. I am still reading through everyones suggestions, once I am finished I will decide what to do and let you guys know how everything worked out. Feel free to use this thread to ask any other questions regarding Windows 7 and Ubuntu.

---

### Post by brhokla on 2009-12-02
I just realized that when I did this install it was with Wubi.  I don't see any other icon or install program in the Ubuntu files. Any Ideas?  maybe this is why it didn't want to boot right in the first place.  I got it working but every time you turn on the computer you have to go into the Bios and tell the computer to boot from the other drive in order to make Ubuntu work.  Did I do something wrong that i don't see a Ubuntu install?

---

### Post by u.b.u.n.t.u on 2009-12-02
> **brhokla said:**
> I just realized that when I did this install it was with Wubi.  I don't see any other icon or install program in the Ubuntu files. Any Ideas?  maybe this is why it didn't want to boot right in the first place.  I got it working but every time you turn on the computer you have to go into the Bios and tell the computer to boot from the other drive in order to make Ubuntu work.  Did I do something wrong that i don't see a Ubuntu install?

There are a few options for "installing" Ubuntu 9.10.

[IMG]http://img189.imageshack.us/img189/3995/20091203132239.png[/IMG]

Wubi provides for three options, the demo (live CD) with an optional full install or installation within windows.

So your first port of call is indeed wubi from the desktop version of Ubuntu 9.10.

The BIOS matter is separate. You need to correctly configure your BIOS so that it understands the hierarchy of your HDDs. 

With GRUB on the BIOS defined master HDD you can then boot to the operating system of your choice. Either the defined default or manually selected from a list of operating systems installed.

---

### Post by brhokla on 2009-12-02
Which do you recommend - Installing inside windows or the full installation?

---

### Post by u.b.u.n.t.u on 2009-12-02
> **brhokla said:**
> Which do you recommend - Installing inside windows or the full installation?

The best person to make such a decision is yourself.

---

### Post by brhokla on 2009-12-02
Thanks for all the help.  I have it up and running perfect and it's working now in dual boot.  All is well so far.  Anybody know how to increase the size of the partition for Ubuntu after the fact?  I made it only 20GB's and it looks like I should have allocated much more as i only show to have 3 GB left.

---

### Post by SlashHeist on 2009-12-03
OK so I backed up my info using the back up tool in windows. 

I used disk man and shrunk my C drive down. So now it says...

OS(C:) NTFS, 421.11GB total, 384.10GB free
RECOVERY (D:)FAT32 14.63 GB total, 5.37GB free

then at the little table section of disk man it says disk 0 then shows a square representation of each partition. Recovery, OS, and then the 30GB I made. But it just says Unallocated.

Am I on the right road? I hope so...

Also I was just wondering if there are any good burning software for free that can burn ISO images and/or bootable disks. I download Ubuntu 9.10 64bit version from the site. Just dont have burning software.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **brhokla said:**
> Anybody know how to increase the size of the partition for Ubuntu after the fact?  I made it only 20GB's and it looks like I should have allocated much more as i only show to have 3 GB left.

I think that question deserves a new thread.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **SlashHeist said:**
> Also I was just wondering if there are any good burning software for free that can burn ISO images and/or bootable disks. I download Ubuntu 9.10 64bit version from the site. Just dont have burning software.

For free? So you are referring to windows based systems I take it.

This is what I use: InfraRecorder

"Zip archive (portable x64 version, 3.79 MiB)"

[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

Actually used it today for a routine DVD data backup.

---

### Post by darkod on 2009-12-03
> **brhokla said:**
> Thanks for all the help.  I have it up and running perfect and it's working now in dual boot.  All is well so far.  Anybody know how to increase the size of the partition for Ubuntu after the fact?  I made it only 20GB's and it looks like I should have allocated much more as i only show to have 3 GB left.
Did you already start putting personal data on it? The desktop version installation is about 2.7GB by default, before adding new software and data. Are you sure it shows only 3GB free from 20GB?

---

### Post by Cavsfan on 2009-12-03
> **SlashHeist said:**
> OK so I backed up my info using the back up tool in windows. 

I used disk man and shrunk my C drive down. So now it says...

OS(C:) NTFS, 421.11GB total, 384.10GB free
RECOVERY (D:)FAT32 14.63 GB total, 5.37GB free

then at the little table section of disk man it says disk 0 then shows a square representation of each partition. Recovery, OS, and then the 30GB I made. But it just says Unallocated.

Am I on the right road? I hope so...

Also I was just wondering if there are any good burning software for free that can burn ISO images and/or bootable disks. I download Ubuntu 9.10 64bit version from the site. Just dont have burning software.

Download Infrarecorder from_ [here ]("http://infrarecorder.org/?page_id=5")_to burn the ISO. Select the 64 bit version. Worked great for me.
You will see smoke coming off the app when it is burning.
  
Yes, you are definitely on the right road!
All you have to do now is put in the Ubuntu install disk, reboot and select the bottom
option and choose that 30GB unallocated space for your swap and ext4 file system,
I was told to make the swap twice the size of my RAM 1024 being 1GB.
I have 4GB, so I made my swap file 8192K
Then I made the rest of it ext4 and at the bottom select "/" for the file system and
install it. It should go smooth.

---

### Post by Cavsfan on 2009-12-03
> **darkod said:**
> [quote=brhokla]Thanks for all the help. I have it up and running perfect and it's working now in dual boot. All is well so far. Anybody know how to increase the size of the partition for Ubuntu after the fact? I made it only 20GB's and it looks like I should have allocated much more as i only show to have 3 GB left.Did you already start putting personal data on it? The desktop version installation is about 2.7GB by default, before adding new software and data. Are you sure it shows only 3GB free from 20GB?[/quote]

If you just started with the Ubuntu, you may want to go back to windows and delete the volume 
you put Ubuntu on and free up some more HD for Ubuntu. I have a 500GB HD and I gave Ubuntu 
(swap and ext4 file "/" structures) 100GB of it. My windows 7 has almost 400GB. 
But, that is just me. I tried several different things and installed it a couple of times before
 I got it how I wanted it. But, I am happy with it and it doesn't run out of space 
(or probably ever will). Ubuntu doesn't need as much as windows does.

---

### Post by SlashHeist on 2009-12-03
> **Cavsfan said:**
> Download Infrarecorder from_ [here ]("http://infrarecorder.org/?page_id=5")_to burn the ISO. Select the 64 bit version. Worked great for me.
You will see smoke coming off the app when it is burning.
  
Yes, you are definitely on the right road!
All you have to do now is put in the Ubuntu install disk, reboot and select the bottom
option and choose that 30GB unallocated space for your swap and ext4 file system,
I was told to make the swap twice the size of my RAM 1024 being 1GB.
I have 4GB, so I made my swap file 8192K
Then I made the rest of it ext4 and at the bottom select "/" for the file system and
install it. It should go smooth.

Cool thanks Cavs. I'll be doing this when I get done with my classes today. 

Thanks to the other person that recommended InfraRecorder, always nice to see more than one person referring software.

---

### Post by Cavsfan on 2009-12-03
> **SlashHeist said:**
> Cool thanks Cavs. I'll be doing this when I get done with my classes today. 

Thanks to the other person that recommended InfraRecorder, always nice to see more than one person referring software.

You are most welcome! You will always find someone here to help with Ubuntu!
That is what is so great about this! 
u.b.u.n.t.u also is dual booting the 2 64 bit OS. He knows a lot more about Ubuntu
than I do, but I know a fair amount on the initial install. I also know windows pretty well.

---

### Post by SlashHeist on 2009-12-03
Oh man I feel like an idiot, this is really hurting my geek ego. 

So I downloaded Infrarecorder but when it starts to burn the iso of Ubuntu it says burning track 1 or something like that, then it it says input/output error and it wont burn. It says read log for more detail...

Heres the main stuff in the log...

 > Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd).
   > Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
   > Supported modes: PACKET SAO LAYER_JUMP
   > Drive buf size : 1376256 = 1344 KB
   > FIFO size      : 4194304 = 4096 KB
   > Track 01: data    44 MB         padsize:   30 KB
   > Total size:       44 MB = 22991 sectors
   > Current Secsize: 2048
   > Blocks total: 2297888 Blocks current: 2297888 Blocks remaining: 2274897
   > Reducing transfer size from 64512 to 32768 bytes.
   > Starting to write CD/DVD/BD at speed 4 in real SAO mode for single session.
   > Last chance to quit, starting real write in 5 seconds
   >  Operation starts.
   > Waiting for reader process to fill input buffer ... input buffer ready.
   > BURN-Free is OFF.
   > Turning BURN-Free on
   > Starting new track at sector: 0
CCore::ProcessEnded
  Process exited with code: 254.



Any ideas? lol thanks guys for being patient.

---

### Post by u.b.u.n.t.u on 2009-12-03
Within a windows operating system (Windows 7 or Vista or XP) start the latest version of InfraRecorder.exe.

You will see six buttons, bottom left, click "Write Image".

A browser window opens, and navigate to the ISO, eg ubuntu-9.10-desktop-amd64.iso. Make sure that there is a blank CD/DVD in the CD/DVD drive.

---

### Post by SlashHeist on 2009-12-04
Just thought I'd let you guys know that I am posting this from Ubuntu 9.10!!! Wooo! lol

Anyone got anyone have any good software recomendations?

---

### Post by u.b.u.n.t.u on 2009-12-04
> **SlashHeist said:**
> Just thought I'd let you guys know that I am posting this from Ubuntu 9.10!!! Wooo! lol

Cool!

---

### Post by OrangeCrate on 2009-12-04
Though I used InfraRecorder on Vista, you all are aware, that there's now a built in disk burner in Windows 7, right?

(Go to your Downloads file, and look in the top bar for "Burn". I've used it, and it works fine.)

---

### Post by Cavsfan on 2009-12-04
> **SlashHeist said:**
> Just thought I'd let you guys know that I am posting this from Ubuntu 9.10!!! Wooo! lol

Anyone got anyone have any good software recomendations?

I found Ripoff to be the best MP3 ripping software, but you have to select the mp3 
plugin to be installed too. They will both be listed in SPM (Synaptic Package manager).
It works well in Ubuntu 9.10 and can rip at 320 bits.

All I can say is it works for me. You will hear other opinions and that is good!:D

Glad you got everything to work and Welcome!

---

### Post by misterbk on 2009-12-04
Sorry to drag people back in to the discussion, but there were some things I couldn't follow or maybe weren't mentioned...

1:  Are there any actual differences, after the install is done, between using the Wubi or booting to the Ubuntu CD and installing that way?  (The Wubi screenshot seems to mention disabling hibernation, and reduced file system performance?)

2: Once the install is done, using either method, what is the bootloader - Windows or Grub?  The Windows bootloader has some features essential to Windows 7.  Does it stay?  

I want to have two separate hard drives: one Win7 and one Ubuntu.  I want the Win7 bootloader to run, and have an option to select Linux from within that.

My usual method for this is to unplug the Windows drive and install Linux.  Once done, plug the Windows drive back in and add the Linux drive to the boot.ini.  (which of course is gone now with Win7, but I have that covered.)

Thanks!

---

### Post by girishganesan on 2009-12-04
Hi everyone,

I'm using windows 7 64 bit. I have the ubuntu 9.04 (Jaunty Jackalope). I'm a noob to linux and i messed up the installation and did shoddy patchwork on it too.

Here's the situation (3 days back)
HDD capacity: 320 Gb  ( 282 Gb useable)
The whole of the 282 Gb is in ONE partition (Grr!)
I unknowingly tried installing ubuntu into the same partition. Then i thought that would give me "bad" results. I put in the live cd and just deleted the partiton into which ubuntu was installed, but this didnt remove the GRUB which kept crashing, and i couldnt login to win7. *PANIC* i reinstalled ubuntu again. and well, now i can login to windows. and linux.

what i want to do: 

1. Uninstall Ubuntu. ( properly, along with the GRUB)

- I shrank the partition in windows and i have 222 Gb of free space to (RE)install linux

2. Install ubuntu onto a different partition.

thats all, hopefully, when someone helps me out on this, i'll be able to learn linux....(soon).

P.S- also, whats the format on which linux is installed? (ext 2 / 3? (whats that mean?) and whats an extended partition mean ?

---

### Post by phillw on 2009-12-04
> **u.b.u.n.t.u said:**
> A wubi install enables a dual boot. 




Wubi was not mentioned and so I mentioned it as an option to consider.



My post was not confusing.



Source?



Your argument that "try" does not allow "permanent" (say 6 months in todays development cycle), is illogical.

I am not here to debate with you your views. I am here to offer my assistance for what it is worth to the OP and it is at their discretion what they decided to do with such.

As the OP asked for dual boot & there are quite a few issues with Wubi and Win7 having been reported - It'd be the last thing I'd recommend. Having a clean Dual boot has one other MASSIVE advantage -- it can rescue your Win from a nasty. It's why all the utilities to get rid of the likes of boot-sector nasties are in linux.  -- just my $0.02 worth.

Phill

---

### Post by phillw on 2009-12-04
> **girishganesan said:**
> Hi everyone,

I'm using windows 7 64 bit. I have the ubuntu 9.04 (Jaunty Jackalope). I'm a noob to linux and i messed up the installation and did shoddy patchwork on it too.

Here's the situation (3 days back)
HDD capacity: 320 Gb  ( 282 Gb useable)
The whole of the 282 Gb is in ONE partition (Grr!)
I unknowingly tried installing ubuntu into the same partition. Then i thought that would give me "bad" results. I put in the live cd and just deleted the partiton into which ubuntu was installed, but this didnt remove the GRUB which kept crashing, and i couldnt login to win7. *PANIC* i reinstalled ubuntu again. and well, now i can login to windows. and linux.

what i want to do: 

1. Uninstall Ubuntu. ( properly, along with the GRUB)

- I shrank the partition in windows and i have 222 Gb of free space to (RE)install linux

2. Install ubuntu onto a different partition.

thats all, hopefully, when someone helps me out on this, i'll be able to learn linux....(soon).

P.S- also, whats the format on which linux is installed? (ext 2 / 3? (whats that mean?) and whats an extended partition mean ?

Hi & welcome

So, you can boot into both systems.

Go into the ubuntu one, drop to the terminal (the little black thing on the top task bar with >_  in it and type
```
sudo fdisk -l
```

It will ask you for your password - please post back the results.

Phill.

---

### Post by misterbk on 2009-12-04
> **phillw said:**
> As the OP asked for dual boot & there are quite a few issues with Wubi and Win7 having been reported - It'd be the last thing I'd recommend. Having a clean Dual boot has one other MASSIVE advantage -- it can rescue your Win from a nasty. It's why all the utilities to get rid of the likes of boot-sector nasties are in linux.  -- just my $0.02 worth.

Phill

There seems to be a giant gap in information here as far as what exactly the Wubi does.  :confused:

What does the Wubi do that makes it not a full dual-boot install?

---

### Post by darkod on 2009-12-04
> **misterbk said:**
> Sorry to drag people back in to the discussion, but there were some things I couldn't follow or maybe weren't mentioned...

1:  Are there any actual differences, after the install is done, between using the Wubi or booting to the Ubuntu CD and installing that way?  (The Wubi screenshot seems to mention disabling hibernation, and reduced file system performance?)

2: Once the install is done, using either method, what is the bootloader - Windows or Grub?  The Windows bootloader has some features essential to Windows 7.  Does it stay?  

I want to have two separate hard drives: one Win7 and one Ubuntu.  I want the Win7 bootloader to run, and have an option to select Linux from within that.

My usual method for this is to unplug the Windows drive and install Linux.  Once done, plug the Windows drive back in and add the Linux drive to the boot.ini.  (which of course is gone now with Win7, but I have that covered.)

Thanks!

Maybe someone will correct me if I'm wrong but my understanding of wubi is that it's working as a sort of virtual pc. If you used software like that before you know what I'm talking about. Hence the performance drop mentioned but I can't tell you if it's serious drop. Also, a lot of fixes to problems posted here will not be applicable to wubi, but then the problems might be different too.
With wubi the win7 bootloader is in charge with small difference that you also get a grub menu after it, which I explain exactly with the virtual pc mode. Only you are working full screen and the ubuntu entry is embedded into win7 bootloader instead of starting windows, then starting virtual pc software, and then starting your vistual machine.
In the side-by-side install grub2 is the only bootloader you'll see, but it has no issues with win7. I don't know what you mean it has features essential to win7. I am running them like that on both my desktop and netbook, no problems. Grub2 is only chainloading win7 loader anyway.
If you want to use win7 bootloader and start ubuntu from that, it's possible but not a very straightforward process and depending how much you know about the matter. If you are asking me, you would be doing it backwards because you will be trying to add ubuntu to a bootloader that was designed to look only at windows, instead of using grub2 that was designed to look for and boot any other OS on your computer.
There are some options with software Easy BCD for windows, but haven't tried it and don't need it.
I never recommend unplugging any hardware when installing any OS. It needs to know what hardware it's got. The drive mappings might change when you replug windows back, and netiher win7 or ubuntu will boot, you are asking for trouble. Of course, it doesn't mean it will fail 100%. But why unplugging hardware that you plan to have in your computer? Ubuntu won't touch your windows drive anyway.

---

### Post by darkod on 2009-12-04
For me, the first sentence in the community wubi documentation says it all:
The **W**indows-based **Ub**untu **I**nstaller (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user **TRY** Ubuntu without risking any data loss due to disk formatting or partitioning.

The key word is TRY. They didn't say INSTALL ubuntu, TRY ubuntu. If you are after long term ubuntu install, that says enough for me. Of course, others might have different opinion about this sentence. :)

Yes, wubi is VERY easy to try especially for long term windows user, just double click and install like software in windows. But is it dual boot full ubuntu install? NO, not IMHO.

---

### Post by phillw on 2009-12-04
> **misterbk said:**
> There seems to be a giant gap in information here as far as what exactly the Wubi does.  :confused:

What does the Wubi do that makes it not a full dual-boot install?

Wubi is installed WITHIN windows - just like Microsoft office etc.

This means that if your Windoze instllation goes belly-up because of a virus, corruption - The new improved 'Black Screen of Death" - then Wubi will not be able to help you rescue your Win area. People have also reported no end of problems when trying to update from one version of ubuntu to the next via Wubi. Wubi is gr8 to have a play with - it runs faster than LiveCD - but should only be used for that. Yes, it can be used longer term & is stable - but supporting it is a nightmare - Simply put - there are not enough on the forums who use it regularly - we all switched to Dual Boot long ago.

So, if for no other purpose - Dual boot will find you more people familiar with it, than those familiar with Wubi.

Hope that helps clarify it.

Regards,

Phill.

---

### Post by misterbk on 2009-12-04
> **darkod said:**
> Maybe someone will correct me if I'm wrong but my understanding of wubi is that it's working as a sort of virtual pc. If you used software like that before you know what I'm talking about. Hence the performance drop mentioned but I can't tell you if it's serious drop. Also, a lot of fixes to problems posted here will not be applicable to wubi, but then the problems might be different too.
With wubi the win7 bootloader is in charge with small difference that you also get a grub menu after it, which I explain exactly with the virtual pc mode. Only you are working full screen and the ubuntu entry is embedded into win7 bootloader instead of starting windows, then starting virtual pc software, and then starting your vistual machine.
In the side-by-side install grub2 is the only bootloader you'll see, but it has no issues with win7. I don't know what you mean it has features essential to win7. I am running them like that on both my desktop and netbook, no problems. Grub2 is only chainloading win7 loader anyway.
If you want to use win7 bootloader and start ubuntu from that, it's possible but not a very straightforward process and depending how much you know about the matter. If you are asking me, you would be doing it backwards because you will be trying to add ubuntu to a bootloader that was designed to look only at windows, instead of using grub2 that was designed to look for and boot any other OS on your computer.
There are some options with software Easy BCD for windows, but haven't tried it and don't need it.
I never recommend unplugging any hardware when installing any OS. It needs to know what hardware it's got. The drive mappings might change when you replug windows back, and netiher win7 or ubuntu will boot, you are asking for trouble. Of course, it doesn't mean it will fail 100%. But why unplugging hardware that you plan to have in your computer? Ubuntu won't touch your windows drive anyway.

Thanks, that clears up a lot!

It seems really odd to me that a VM would be running at boot time, for the sole purpose of running a single OS (i.e. not inside another OS) on hardware that is capable of running said OS.

I suppose, would be more accurate to say, Win7 bootloader has features I want to have.  Some reasons I want the Win7 bootloader:  Supports booting to disk images stored inside the main Windows filesystem for testing purposes.  Deals with safe mode, hibernation files etc. and provides recover options.  Also simply wanting my main workstation OS (used for work) to stay as close to standards as possible.  I figure I might have a better chance scaring up strange issues if I deviate too far on a new OS.  I'm using Linux for testing purposes, finally have a systefm with spare drive slots at the same time I have spare drives.  :)  

EasyBCD is exactly the solution I've found.  Even has a specific choice labeled "Linux" when you add a new boot entry, so it seems to be aware of Grub.

Could the issues seen with Wubi be related to chainloading Grub from the Windows bootloader?  (I thought at that point, the Win7 bootloader has been completely "forgotten" and you may as well have just loaded Grub?)

---

### Post by misterbk on 2009-12-04
> **phillw said:**
> Wubi is installed WITHIN windows - just like Microsoft office etc.

This means that if your Windoze instllation goes belly-up because of a virus, corruption - The new improved 'Black Screen of Death" - then Wubi will not be able to help you rescue your Win area. People have also reported no end of problems when trying to update from one version of ubuntu to the next via Wubi. Wubi is gr8 to have a play with - it runs faster than LiveCD - but should only be used for that. Yes, it can be used longer term & is stable - but supporting it is a nightmare - Simply put - there are not enough on the forums who use it regularly - we all switched to Dual Boot long ago.

So, if for no other purpose - Dual boot will find you more people familiar with it, than those familiar with Wubi.

Hope that helps clarify it.

Regards,

Phill.

My impression from reading was that the Wubi is just an Ubuntu installer that has been made as a Windows app?  i.e. it's true you are running a Windows app to install, but it's really just doing the same thing the bootable CD would do?

I can certainly see issues supporting if it installs differently somehow than the bootable CD.

I'm pretty much convinced I should use the bootable CD at this point so my residual questions are just trying to figure out what the heck that Wubi thing really does.

And thanks for the replies, also apologies if I'm posting too fast...  seems I'm typing posts at the same time others are typing their replies to my posts. :-k

---

### Post by darkod on 2009-12-04
> **misterbk said:**
> 
Could the issues seen with Wubi be related to chainloading Grub from the Windows bootloader?  (I thought at that point, the Win7 bootloader has been completely "forgotten" and you may as well have just loaded Grub?)

Don't know really. I would say it has more to do with trying to make linux work inside windows. :) There is a line how far to go towards pleasing windows users. IMHO.

PS. With wubi you definitely will not end with the same system as with booting the cd and selecting Install. The main proof is that your windows partition are not changed. Wubi will be in one folder on your ntfs partition. That to me looks a lot like the VM images used earlier. I guess the technology for VM is improved, but still...

---

### Post by phillw on 2009-12-04
> **misterbk said:**
> Thanks, that clears up a lot!

It seems really odd to me that a VM would be running at boot time, for the sole purpose of running a single OS (i.e. not inside another OS) on hardware that is capable of running said OS.

I suppose, would be more accurate to say, Win7 bootloader has features I want to have.  Some reasons I want the Win7 bootloader:  Supports booting to disk images stored inside the main Windows filesystem for testing purposes.  Deals with safe mode, hibernation files etc. and provides recover options.  Also simply wanting my main workstation OS (used for work) to stay as close to standards as possible.  I figure I might have a better chance scaring up strange issues if I deviate too far on a new OS.  I'm using Linux for testing purposes, finally have a systefm with spare drive slots at the same time I have spare drives.  :)  

EasyBCD is exactly the solution I've found.  Even has a specific choice labeled "Linux" when you add a new boot entry, so it seems to be aware of Grub.

Could the issues seen with Wubi be related to chainloading Grub from the Windows bootloader?  (I thought at that point, the Win7 bootloader has been completely "forgotten" and you may as well have just loaded Grub?)

EasyBCD can, indeed, boot from iso's -as can VirtualBox the other Virtual Machine - The thing about *nix - is it gives choice - this can be a bit overwhelming to a user familiar only with Win - where the choice is Win ... or nothing.

[http://www.raiden.net/articles/living_life_without_windows_an_introduction_to_linux/](http://www.raiden.net/articles/living_life_without_windows_an_introduction_to_linux/)

Has an excellent view on how things differ. It's well worth a read.

And, of course, with choice - comes the all important cavaet -- IMHO, as that is what we express.

If you want see some really crazy stuff done with a usb memory stick and multi-booting -- head over to [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

Those people are certifiably mad with what they do to pen-drives !!!

REgards,

Phill.

---

### Post by misterbk on 2009-12-04
> **darkod said:**
> Don't know really. I would say it has more to do with trying to make linux work inside windows. :) There is a line how far to go towards pleasing windows users. IMHO.

PS. With wubi you definitely will not end with the same system as with booting the cd and selecting Install. The main proof is that your windows partition are not changed. Wubi will be in one folder on your ntfs partition. That to me looks a lot like the VM images used earlier. I guess the technology for VM is improved, but still...

Part of my interest in the Wubi is that I am giving Linux demonstrations at a local Visual Effects college.  Studios often use Linux as the core OS in their pipelines, but the school runs entirely Windows because there is not a comprehensive stable set of apps that covers everything in Linux.  (Mainly missing the Adobe software.)  Every workstation has to be capable of all tasks unfortunately, whereas in a studio the FX guys don't care about Photoshop as much.

My goal with the install I'm doing now is to go over the process for installing RedHat RPMs for our production packages in a Debian based system.  That's why I want to "perturb" the Windows install as little as possible.

For me, I've done too many Linuxes already and I can handle it for purposes of the demonstration.  For the audience, well, these are Windows people trying to get some hands-on with Linux for their resumes.  First they heard what a partition was, was in my last talk!

EDIT:
> The main proof is that your windows partition are not changed. 
I missed that the first time through but that really helps explain what's going on.  I thought the Wubi resized your partitions, from looking at the screenshots.  Thanks!

---

### Post by darkod on 2009-12-04
As long as you are aware what wubi is, and you don't expect to find ext4 partition on your hdd (because I've seen people doing that), it's fine. :)

---

### Post by phillw on 2009-12-04
> **misterbk said:**
> Part of my interest in the Wubi is that I am giving Linux demonstrations at a local Visual Effects college.  Studios often use Linux as the core OS in their pipelines, but the school runs entirely Windows because there is not a comprehensive stable set of apps that covers everything in Linux.  (Mainly missing the Adobe software.)  Every workstation has to be capable of all tasks unfortunately, whereas in a studio the FX guys don't care about Photoshop as much.

My goal with the install I'm doing now is to go over the process for installing RedHat RPMs for our production packages in a Debian based system.  That's why I want to "perturb" the Windows install as little as possible.

For me, I've done too many Linuxes already and I can handle it for purposes of the demonstration.  For the audience, well, these are Windows people trying to get some hands-on with Linux for their resumes.  First they heard what a partition was, was in my last talk!

EDIT:

I missed that the first time through but that really helps explain what's going on.  I thought the Wubi resized your partitions, from looking at the screenshots.  Thanks!

WINE - the emulator is upto Photoshop CS4, the last i checked (10 minutes ago) - If you're running a later edition of Photoshop, then you'll be best going with Wubi - IMHO. Get the latest (9.10) and STICK with it !!! - when you want (if you want) to update it - TEST it out on a machine you can afford to break !!!

Phill.

---

### Post by phillw on 2009-12-04
> **SlashHeist said:**
> Just thought I'd let you guys know that I am posting this from Ubuntu 9.10!!! Wooo! lol

Anyone got anyone have any good software recomendations?

Welcome to Ubuntu !!

Click on Applications --> Ubuntu Software Center & let your mind roam free !!!!

(And your wallet - lol)

regards,

Phill.

---

### Post by misterbk on 2009-12-04
> **phillw said:**
> WINE - the emulator is upto Photoshop CS4, the last i checked (10 minutes ago) - If you're running a later edition of Photoshop, then you'll be best going with Wubi - IMHO. Get the latest (9.10) and STICK with it !!! - when you want (if you want) to update it - TEST it out on a machine you can afford to break !!!

Phill.

I didn't want to go too far OT but I had to say I'm impressed by that!  I did not expect WINE to be able to handle the new graphics acceleration features for canvas rotation etc.  I've only had partial luck with it in the past, but that was nearly 10 years ago.

Photoshop is the biggest missing link.  (I'm actually glad nobody tried to tell me to use the Gimp.)  With that running on Wine, we'd have Nuke for comp and Maya for everything else.  Need to check on ZBrush but that may be available in Linux.  Most new apps are released in Linux if they want to be taken seriously.  (Dreamworks, Pixar, ILM, many others, all 95% Linux workstations.)

---

### Post by phillw on 2009-12-04
> **misterbk said:**
> I didn't want to go too far OT but I had to say I'm impressed by that!  I did not expect WINE to be able to handle the new graphics acceleration features for canvas rotation etc.  I've only had partial luck with it in the past, but that was nearly 10 years ago.

Photoshop is the biggest missing link.  (I'm actually glad nobody tried to tell me to use the Gimp.)  With that running on Wine, we'd have Nuke for comp and Maya for everything else.  Need to check on ZBrush but that may be available in Linux.  Most new apps are released in Linux if they want to be taken seriously.  (Dreamworks, Pixar, ILM, many others, all 95% Linux workstations.)

lol @ GIMP - there was a photoGimp available a while back - but the project was abandoned. I'm lucky in that a) I don't NEED photoshop (I have pro version - i think it was 7 - on my Vista area --- tooooo complicated for me - I use the SE ? - low version free one) - I am gradually getting used to GIMP.  b) I have a semi-tame dingo who is really good with Photoshop for if i need anything for sites I'm putting together - I'm a coder - not a graphical designer ;-)

Phill

---

### Post by u.b.u.n.t.u on 2009-12-04
> **phillw said:**
> As the OP asked for dual boot & there are quite a few issues with Wubi and Win7 having been reported

There are quite a few issues with a number of things. Take your pick.

> **phillw said:**
> It'd be the last thing I'd recommend.

Fine, a bit late for your opinion, but you are entitled to it.

> **phillw said:**
> Having a clean Dual boot has one other MASSIVE advantage

Also a massive disadvantage depending on what one wishes to achieve.

...

Anyway, why hijack the OP thread with off topic digressions? Start new threads for new topics or it becomes a right mess!

---

### Post by misterbk on 2009-12-04
> **u.b.u.n.t.u said:**
> There are quite a few issues with a number of things. Take your pick.
Linux has always gone hand in hand with issues for me.  Doesn't mean we shouldn't advise new people in a direction that has fewer of them.

> 
Also a massive disadvantage depending on what one wishes to achieve.

I'm really excited to hear these things actually backed up.  Otherwise the discussion can't go anywhere past "Does so!" "Does not!" "Does so!"

If you could mention some of the reported issues (which still hasn't been done) and debunk them, that would be absolutely awesome.

> Anyway, why hijack the OP thread with off topic digressions? Start new threads for new topics or it becomes a right mess!

One OT remark followed by a reply is not a hijack.  Unless you're referring to the in-depth discussion of the Wubi combined with Win7, which is absolutely on topic.  If there's an install method that's off the beaten track and/or leads to issues when paired with Win7 seems like this is the place to discuss.


BTW, I'm posting from my new Ubuntu install.  It's like the fifteenth time I've done this, but it still has that "new linux" smell!  It's the first time it's been on my actual daily-use modern workstation and not some old POS machine I had in a corner.

Now to try chaining Grub off of the Win7 bootloader using EasyBCD.  Will report back if my machine doesn't suddenly start spinning around and spewing pea soup.

---

### Post by u.b.u.n.t.u on 2009-12-04
misterbk, to put it simply, some may have had a negative experience with wubi such as yourself, and some may have had a positive experience with wubi such as myself.

One does not invalidate the other. It is academic to discuss the pros and cons. Therefore let the individual decide based on an informed opinion by reading relevant material.

I really have nothing further to add to this.

---

### Post by misterbk on 2009-12-04
> **u.b.u.n.t.u said:**
> decide based on an informed opinion
What I'm trying to get, yes.
>  by reading relevant material.
Was trying to find that but all I got was instructions how to click on it, nothing about what it did.

> I really have nothing further to add to this.

I will go try and find a FM to RT.

---

### Post by u.b.u.n.t.u on 2009-12-04
This may be of interest.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by misterbk on 2009-12-04
> **u.b.u.n.t.u said:**
> This may be of interest.

[http://wubi-installer.org/](http://wubi-installer.org/)

Thank you, the only place I'd seen "Wubi" so far was as an option on the ubuntu.com download page.

Again I have the problem that the only obvious info presented is that "you click it and you get Ubuntu!!" and again I have the problem of conflicting facts being presented:

[quote=Wubi Page]"Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers.  It works just like any other application."[/quote]

vs. 

[quote=Wubi Page]"Wubi only adds an extra option to **boot into Ubuntu.**"[/quote]

You don't "boot into" an application that runs within windows unless it is a VM, and it is also stated that it is not a VM.


Anyway I've finally been able to infer what this thing does.  **The Ubuntu Wubi installer installs Linux to an .ISO image within your Windows filesystem, and adds an option inside the Windows bootloader to boot that .ISO image as if it were a hard drive.**

Based on that, I can infer that the Wubi:

* Does NOT run within a Virtual Machine, i.e. uses real hardware access

* However, DOES virtualize the storage system, so that it can treat an .ISO within an NTFS filesystem as a physical device.

* Could potentially cause confusion with some howtos, if the howto assumes "/dev/sda" but the boot actually happens from "/dev/md0" or something.

* Would suffer reduced filesystem performance because it is piping block device (disk) accesses through NTFS-3G and into an ISO image that resides on yet another filesystem.

* Probably does not just boot the run the Ubuntu LiveCD (confirmation?) because it does ask you during install for things like username, password.


and now I am going to go eat tasty food.

---

### Post by u.b.u.n.t.u on 2009-12-04
> **misterbk said:**
> Again I have the problem that the only obvious info presented is that "you click it and you get Ubuntu!!"

Yes this can obviously be improved.

I consider wubi to be brilliant, but can confirm a bug where it may torrent downloads an Ubuntu 9.10 ISO rather than install from Ubuntu 9.10 ISO where  wubi.exe was just clicked.

I view such as early software issues and hope such will be addressed.

Perhaps even an additional option, install Ubuntu via wubi, and then an option for Ubuntu to either become a dedicated partition or make it the sole operating system.

What better way to install Ubuntu than via a Windows operating system, where only Ubuntu remains! lol

---

### Post by misterbk on 2009-12-04
> **u.b.u.n.t.u said:**
> Yes this can obviously be improved.
What better way to install Ubuntu than via a Windows operating system, where only Ubuntu remains! lol

This is why I've been trying to figure out exactly what this does.  If the Wubi does indeed function well, I can mention it in my talk.  These guys are used to the idea of clicking an installer and getting new software, but few or none have ever installed an OS from scratch.  The Wubi bypasses the whole issue of having to know how to enter your BIOS, set boot order, boot from CD, all that stuff.

The goal is to get them some user-level Linux experience so they can say that in a job interview.  Nobody will care if they used a dumbed-down "easy" install, that all gets handled by the studio's I.T. team.


Anyway the Wubi sounds like a "no risk" option so I do think I'll mention it.  Thanks for your help!

---

### Post by ShadowMage on 2009-12-05
Hi,

I think my question has relevance to this thread, so I hope this thread is appropriate for my question. I would like to dual boot Windows 7 64-bit with Ubuntu 9.10 by doing a _clean and full install_ of Ubuntu. I have installed Ubuntu many times on other machines but this is a new machine and my first one capable of 64-bit (or at least my first one that ever had any 64-bit software on it).

My question is, should I install the 64-bit version of Ubuntu, or the 32-bit version? **Before responding, please note:** I noticed the download file for the 64-bit version is called ubuntu-9.10-desktop-amd64.iso; however, my processor is not an AMD64 and not even an AMD at all. My processor is an _**Intel** Core2 Duo T6600_. This is why I am hesitant to install this version. If anyone could clear this up for me I would greatly appreciate it.

Thanks in advance.

---

### Post by misterbk on 2009-12-05
> **ShadowMage said:**
> Hi,

I think my question has relevance to this thread, so I hope this thread is appropriate for my question. I would like to dual boot Windows 7 64-bit with Ubuntu 9.10 by doing a _clean and full install_ of Ubuntu. I have installed Ubuntu many times on other machines but this is a new machine and my first one capable of 64-bit (or at least my first one that ever had any 64-bit software on it).

My question is, should I install the 64-bit version of Ubuntu, or the 32-bit version? **Before responding, please note:** I noticed the download file for the 64-bit version is called ubuntu-9.10-desktop-amd64.iso; however, my processor is not an AMD64 and not even an AMD at all. My processor is an _**Intel** Core2 Duo T6600_. This is why I am hesitant to install this version. If anyone could clear this up for me I would greatly appreciate it.

Thanks in advance.

Your system supports the AMD64 instruction set.  Whether you want it or the 32-bit depends mostly on your RAM situation.

AMD64 works on both AMD and Intel.  AMD64 is the name of the instruction set. All 64-bit processors use that instruction set (well except maybe Itanium).  It's called AMD64 because AMD was first out with a 64-bit instruction set, and for compatibility reasons Intel used theirs instead of making a new one.

If you have 4GB of RAM or more, you want AMD64.  If you have 3 or less, it's debatable whether there would be any benefit, and some old applications might not work.  (someone in another post was reporting they couldn't get some math simulator to work, it crashed if you calculated the square root of an integer.)

---

### Post by ShadowMage on 2009-12-05
misterbk, your detailed response cleared up my confusion, thank you!! :)

EDIT: I've now set-up my dual boot. Everything went smooth. Thanks again.

---

### Post by misterbk on 2009-12-05
Update on the attempt to get Win7 and Ubuntu cooperating, using the Win7 bootloader...

The Win7 bootloader doesn't seem to behave the way it used to in XP.  I can no longer just point an entry to the Linux drive and go.

I've found some tutorials for getting it to work.  They involve blindly piping the first so-many bytes of the Linux partition into a file, placing that file on the Windows drive, and somehow linking the Win7 bootloader's "Linux" option to that file.

Starting to re-think whether it's that important to keep the windows bootloader first.

---

### Post by SlashHeist on 2009-12-06
OK so I have a slight problem, and I figured I would use my existing thread to ask about it, hopefully that is ok. 

I installed Chromium (web browser).Worked fine and everything. But I decided to change the name of my computer because it was something lame that I forgot to change at installation. I changed the name using terminal.

Now when I go to start up Chromium it says "The profile appears to be in use by process 1876 on host booey-laptop. If you are sure no other processes are using this profile, delete the file /home/booey/.config/chromium/SingletonLock and restart Chromium." 

I changed the name so it is no longer booey-laptop. If it were a simple fix such as just deleting that file how do I do that, I can't find the directory. 

Thanks

---

### Post by u.b.u.n.t.u on 2009-12-06
Can you simply rename the profile? Within the browser can you delete it?

---

### Post by SlashHeist on 2009-12-06
> **u.b.u.n.t.u said:**
> Can you simply rename the profile? Within the browser can you delete it?

Yeah! I got it to work. It just wasn't doing it before hand. Idk. 

I just noticed to that when I boot up my laptop i have 8 different choices to boot into. Theres Ubuntu Linux Generic 14, 15, and 16 and each has a normal and recovery mode. So thats 6, then theres one that says Vista Loader or something like that. Then the very last one is Windows 7. I use the top one for Ubuntu. Which I believe is 14, not positive though. And the very bottom one, for Windows 7. 

Any ideas why there is so many?

---

### Post by u.b.u.n.t.u on 2009-12-06
Two default kernels and recovery modes by default equals four and the recent update is two more. So six in total for Ubuntu 9.10.

To be on the safe side, keep them for now. You may need them should you update and need to revert back for a time to an earlier kernel.

Naturally if you have Vista and Windows 7 also installed, that means two more boot options.

There are your eight.

---

### Post by SlashHeist on 2009-12-06
> **u.b.u.n.t.u said:**
> Two default kernels and recovery modes by default equals four and the recent update is two more. So six in total for Ubuntu 9.10.

To be on the safe side, keep them for now. You may need them should you update and need to revert back for a time to an earlier kernel.

Naturally if you have Vista and Windows 7 also installed, that means two more boot options.

There are your eight.

Yeah I just wasn't sure if that was normal or what... just seemed like overkill. I dont have vista installed, but I was reading that some parts of Windows7 are read as Vista since they are similar or something. Idk

---

### Post by u.b.u.n.t.u on 2009-12-06
> **SlashHeist said:**
> Yeah I just wasn't sure if that was normal or what... just seemed like overkill. I dont have vista installed, but I was reading that some parts of Windows7 are read as Vista since they are similar or something. Idk

Overkill perhaps. I think not though. Ubuntu 9.10 is in a constant state of development and release and the options of kernels avoids many a potential problem.

To remove the kernel options would need to limit the updates to some extent also. The whole storm in a tea cup argument about the development and release speed of Ubuntu becomes relevant.

Is it better to release one version each year and make it as ironclad as possible or is it better to go full steam ahead. The race is to catch up to and overtake Microsoft, that is the game.

Mark is absolutely right in his call, that full steam ahead is what is needed. Those who argue otherwise should start their own distro of Ubuntu!

So back to the matter at hand, kernel options are a good thing and if the boot loader is set to the desired default start and to about an 8 second delay, all is good.

I don't stop watch my computer, I coffee it - turn on the computer, make a cuppa coffee, and visit here to see what updates exist to my topic subscriptions.

Now with regards to Vista, that is strange. Try this if you wish, accept it and see what happens. Also check the reference in the boot loader. If such doesn't exist, why have it?

I have a Windows 7 and Ubuntu 9.10 combination and no sight or sound of Vista anyway.

---

### Post by girishganesan on 2009-12-08
> **phillw said:**
> Hi & welcome

So, you can boot into both systems.

Go into the ubuntu one, drop to the terminal (the little black thing on the top task bar with >_  in it and type
```
sudo fdisk -l
```It will ask you for your password - please post back the results.

Phill.

Hi, guess what, I just put in the live cd, deleted the partition on which ubuntu was. So i have 224 gb of unallocated unformatted space. then i created an extended partition on the whole thing and i split it into 160 NTFS for win7 and 63 Gb for Ubuntu and 1.29 Gb for Swap. And i set the mount point of the 63 Gb to '\'.

but i did what you told me. and this is the result. 

-------------------------
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dc11dc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2            1658        1671      102400    7  HPFS/NTFS
/dev/sda3   *        1672        9607    63743898    7  HPFS/NTFS
/dev/sda4            9608       38913   235400445    5  Extended
/dev/sda5            9608       30494   167774796    7  HPFS/NTFS
/dev/sda6           30495       38718    66059248+  83  Linux
/dev/sda7           38719       38913     1566306   82  Linux swap / Solaris

---------------------------


er....so whats all that?

---

### Post by ravi.m.sharma1 on 2009-12-08
**[FONT=Arial]Hey Everyone[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I am a novice as far as Ubuntu is concerned.I have been banging my head in google to help myself with the dual boot.:P but of no use.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]My Issue Goes like this: [/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]Installed Ubuntu 9.04 with Vista existing on my 320 GB hard drive.I upgraded my Jaunty to Koala as soon as it got released and then I upgraded Vista to Win 7.As soon as I did it Win 7 wiped out MBR and therefore I can't access Ubuntu now.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I have a Jaunty CD with me and Win 7 CD too.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I don't want to lose Data.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]Please help me.[/FONT]**

---

### Post by u.b.u.n.t.u on 2009-12-08
> **ravi.m.sharma1 said:**
> **[FONT=Arial]Hey Everyone[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I am a novice as far as Ubuntu is concerned.I have been banging my head in google to help myself with the dual boot.:P but of no use.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]My Issue Goes like this: [/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]Installed Ubuntu 9.04 with Vista existing on my 320 GB hard drive.I upgraded my Jaunty to Koala as soon as it got released and then I upgraded Vista to Win 7.As soon as I did it Win 7 wiped out MBR and therefore I can't access Ubuntu now.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I have a Jaunty CD with me and Win 7 CD too.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]I don't want to lose Data.[/FONT]**
**[FONT=Arial][/FONT]** 
**[FONT=Arial]Please help me.[/FONT]**

Welcome to the Ubuntu community.

Please start a new thread. It will get awfully confusing troubleshooting multiple problems in a single thread.

In this thread I will only be responding to SlashHeist as that person started this thread and wishes help with their problem.

---

### Post by misterbk on 2009-12-08
> **SlashHeist said:**
> Yeah I just wasn't sure if that was normal or what... just seemed like overkill. I dont have vista installed, but I was reading that some parts of Windows7 are read as Vista since they are similar or something. Idk

Win 7 has components that started development as Vista, then continued development to Win 7.  Some didn't need any development to go to Win 7.  (or maybe did and didn't get any.)

Software that detects the OS and reports it to you, but was written before Win 7 existed, might report Vista depending how it checks.

Also lots of architecture is similar enough between Vista and Win 7 that you can usually install Vista drivers in 7.  The two OS are pretty similar...  Just Win7 is snappy and usable in some things that Vista is not.  

The only reason I can think to keep both Vista and 7 around is if you have a nice printer or something that will not be getting Win 7 drivers.

---

