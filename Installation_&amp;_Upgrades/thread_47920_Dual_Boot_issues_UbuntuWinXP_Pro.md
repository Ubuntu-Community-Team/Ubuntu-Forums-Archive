---
title: "Dual Boot issues Ubuntu/WinXP Pro"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by Lodis4 on 2005-07-10
I started with a fresh install of WinXP Pro on a 40GB hdd, I formatted and installed XP on 25GB and was able to boot into and run windows. The next day I decided to install Ubuntu on the remaining 13.5GB. I got all the way through the install and chose the correct options for the dual boot. I then finished the install and restarted, Grub menu came up as it should and I booted into Ubuntu flawlessly, I then restarted and again the Grub menu came up, I selected WinXP and now I get 4 lines of text on a black screen. 

I am not at home right now so I cannot post the exact syntax ( I will do that later) but was hoping someone out there has had a similar experience.

I have been running Ubuntu for the past two days with no problems, all hardware is OK, and I have not had software issues yet either.

Suggestions welcome, I am continuing my google/wiki research.

Thanks

---

### Post by dave9191 on 2005-07-10
Well ive never had that problem. boots into windows and ubuntu flawlessly. having said that i havent booted into windows for the last 3 or 4 months ;) Post the 4 lines of text or what its generally complaining about. Its probably some minor configuration issue that can be sorted out. And if you are desprate about getting back into windows put the win xp cd in , go into recovery mode and type fixmbr into the command line. This will make windows work, but will remove grub and you wont have access to linux.

---

### Post by Lodis4 on 2005-07-10
OK here is the exact syntax:

Booting Windows NT/2000/XP

root (hd0,0)
filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1 

I am reasonably new to Linux, I have seen a few references to these things individually but I have no idea where to start looking for a solution. ](*,)  It is weird that nothing happens when I get this. No beeps no errors, nothing...

---

### Post by dave9191 on 2005-07-11
Could you also post the contents of your grub conf file? 

/boot/grub/menu.lst

Dave

---

### Post by brim4brim on 2005-07-11
[QUOTE=Lodis4]OK here is the exact syntax:
root (hd0,0)
filesystem type unknown, partition type 0x7
[/QUOTE]

I think the hd0 is the problem.  I can't tell you what to change it to but mine is sda1, yours may not be this.  It looks like it just isn't recognising windows partition and it did with mine just after install but this is just my guess* (I'm new to linux) and I'd wait for someone with more experience to answer, just trying to shine some bit of light on the situation in that I believe it's very fixable if this is the problem.

I'm also duel booting XP Pro with Ubuntu and got no issues so this is weird in my novice opinion!

---

### Post by dave9191 on 2005-07-11
Yeh, it also depend what drives you have inside your computer. And where windows is installed. Im guessing that you have an IDE drive and windows is installed on the first partition. You also didnt mention other drives, so ill be assuming that you only have 1 :)

Dave

---

### Post by Bjorg on 2005-07-11
I am also very interested in seeing what's the solution for this issue.

My HD scheme: 
1st partitont: 40GB NTFS  Starting at GB #0 
2nd part: 38GB ext3          Starting at GB #40 (maybe I put it after the swap)
3rd part:2GB SWAP           Starting at GB #78 (maybe I put it after the NTFS)


I installed Ubuntu in the higher partition of my hardisk (starting at the 40th GB, or maybe after the Swap one)

Ubuntu booted properly.

Then I installed Win XP Pro at the beggining of the HD, It booted ok but now I am not able to boot to Ubuntu anymore, no multiboot menu nor anything.

How could I add a multiboot menu? (Bootmagic 7 doesn't work here) I guess I need to install Ubuntu again, right?
How can I be sure I will do it correctly and will be able to boot to win Xp again.

Grub or Lilo? Any custom options with either of these? At which piont of the installation do I need to try to install Lilo?

I'm lost with that "install grub in the mbr or ......whatever are the other options " I don't really understand that, which option to use?

Any help?

Thanks in advance   :D

---

### Post by Lodis4 on 2005-07-11
I have found one solution that may work for you. Unfortunately it does not work in my case though. :(

You can edit your Windows XP boot.ini file and add the partition information for Ubuntu. Having Windows boot Linux is sort of backwards but it does work. A better solution is to install Grub on the MBR. lol, if you can get it to go right, unlike me!

---

### Post by Bjorg on 2005-07-11
[QUOTE=Lodis4]I have found one solution that may work for you. Unfortunately it does not work in my case though. :(

You can edit your Windows XP boot.ini file and add the partition information for Ubuntu. Having Windows boot Linux is sort of backwards but it does work. A better solution is to install Grub on the MBR. lol, if you can get it to go right, unlike me![/QUOTE]


Is that comment for me?  :P

But which info should I add to "boot.ini"?

Currently it says:

[I][boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
[/I]


Any suggestion?

Thx in advance.

---

### Post by Bjorg on 2005-07-11
Finally my HD scheme is this:



(Partition)  -     ( Type)      -     (Size MB)   -    ( Status)   -    (Pri/Log)
[COLOR=Red](/  root)                -      Linux Ext3  -  36240      -    None      -   Primary
SWASPACE2   -  Linux Swap - 1906     -       None     -    Primary
Local Disk (F: ) -  NTFS       -     38162    -      Active     -   Primary[/COLOR]



How could I edit in WinXp "boot.ini" to add a multiboot menu to be able to choose betwen Ubuntu Liux and WinXP?

boot.ini currently says:

[I][boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/I]



Thanks

 ](*,)

---

### Post by mingus on 2005-07-11
Lotus4 and Bjorg -

It is difficult to help when there are two distinct problems running in the same thread.  While yours are both dual-boot questions, that is often where the similarity (and hence the fix) ends.  Better to use separate threads.  Having said that:

Bjorg, never install W$ after Linux or anything else.  Everything W$ does assumes it is the only OS on the system; it is even hostile to other instances of W$, requiring a lot of care and effort to get 2 W$ working together (arguably more difficult that W$ plus Linux).

When you installed W$ you wrote over the Master Boot Record entry that Ubuntu installed.  If you wish, you can reinstall Ubuntu and put the grub loader back in the MRB (that is the default).  If all goes well, when you reboot you will get a grub menu with a selection for booting W$.  Your config looks simple, so this should work.  If you run into a glitch doing this, since you have an XP install CD, fixing that would be easy.

If you would rather use W$ to be the primary boot control, then reinstall Ubuntu ***but*** when you get to the grub install step, do *not* accept the default; instead take manual control and on the next screen which asks where you want to install grub, type "/dev/hda2" (assuming that is the partition you put the Ubuntu root (/) on).  Now, use "Go Back" to repeat this step but this time install grub to a floppy using "/dev/fd0".  When you are prompted to remove media and reboot, do *not* remove the floppy.  You should goot into grub.  From there log in to Ubuntu, open a terminal, and follow the instructions in post #6 at:
[http://www.ubuntuforums.org/showthread.php?t=47873](http://www.ubuntuforums.org/showthread.php?t=47873)
Remove the floppy and reboot; you will now boot first to the Windows menu, and from there to grub and Ubuntu.

Lodis4, you need as Dave9191 suggested, to post back the contents of menu.lst:
$cat /boot/grub/menu.lst
You also need to do and post back:
$sudo fdisk -l
The problem is probably with the syntax you posted, but we need to see this info before advising what change to make.

---

### Post by Bjorg on 2005-07-11
I must say I that I really installed Ubuntu first (with GRUB in the MBR, I think) and then (hoping that WinXP would create the dual boot menu) I installed WinXP.

Now only Win XP boots.

I am tempted to install Ubuntu Linux again in that same partition (the 1st in the disk) and choose GRUB to be installed in the MBR again hoping that linux will create the multiboot menu, but I have read somewere ([http://www.devhood.com/Tutorials/tutorial_details.aspx?tutorial_id=405](http://www.devhood.com/Tutorials/tutorial_details.aspx?tutorial_id=405)) I that WinXP **must** be installed on the 1st partiton, which is not my case.

I don't want to reinstall WINXP again because Norton Antivirus during the activation process will think I am installing the antivirus on more computers than mine.

What can I do to create the multiboot menu? I am ready to reinstall linux but do not want to reinstall Win XP again.

Help, please, I would love to be able to use Linux.

 ](*,)

---

### Post by Bjorg on 2005-07-11
[QUOTE=mingus]Lotus4 and Bjorg -

If you wish, you can reinstall Ubuntu and put the grub loader back in the MRB (that is the default).  If all goes well, when you reboot you will get a grub menu with a selection for booting W$.  Your config looks simple, so this should work.  If you run into a glitch doing this, since you have an XP install CD, fixing that would be easy.

[/QUOTE]

I would rather use that first option since my laptop is "too" modern and doesn't have a floppy drive.

Do you think I will have trouble because windows Xp is not installed in the first partition as I have read in the article I mentioned above?

Thanks a lot for your time and help.

---

### Post by mingus on 2005-07-11
Your post is confusing.

*I must say I that I really installed Ubuntu first (with GRUB in the MBR, I think) and then (hoping that WinXP would create the dual boot menu) I installed WinXP.*

Yes, that is what I said that you did.  But of course, XP will not create a dual boot menu for anything else, including another W$.

*I read that WinXP must be installed on the 1st partiton, which is not my case.*

But you said in your post:

[I]1st partitont: 40GB NTFS Starting at GB #0 . . . and . . .
Then I installed Win XP Pro at the beggining of the HD[/I]

So which is it???  If you did not install W$ in the first partition, it would not boot.  So you must have installed it there.  Therefore you do not need to reinstall W$.

Go back to my prev post.  The paragraph that begins with "If you would rather use W$ to be the primary boot . . ." and follow those instructions.  This will get you reinstalled with Ubuntu, and have you booting from XP into Ubuntu.

---

### Post by Bjorg on 2005-07-11
Sorry Mingus, I posted this message 
[COLOR=Green][SIZE=1][I]I must say I that I really installed Ubuntu first (with GRUB in the MBR, I think) and then (hoping that WinXP would create the dual boot menu) I installed WinXP.

Now only Win XP boots.

I am tempted to install Ubuntu Linux again in that same partition (the 1st in the disk) and choose GRUB to be installed in the MBR again hoping that linux will create the multiboot menu, but I have read somewere ([http://www.devhood.com/Tutorials/tu...tutorial_id=405](http://www.devhood.com/Tutorials/tu...tutorial_id=405)) I that WinXP must be installed on the 1st partiton, which is not my case.

I don't want to reinstall WINXP again because Norton Antivirus during the activation process will think I am installing the antivirus on more computers than mine.

What can I do to create the multiboot menu? I am ready to reinstall linux but do not want to reinstall Win XP again.

Help, please, I would love to be able to use Linux.
[/I][/SIZE]
[/COLOR]
Just before reading yours.

About that inconsistencies I said, my real HD's scheme is this:

[COLOR=Green][SIZE=1][I](Partition) - ( Type) - (Size MB) - ( Status) - (Pri/Log)
(/ root) - Linux Ext3 - 36240 - None - Primary
SWASPACE2 - Linux Swap - 1906 - None - Primary
Local Disk (F: ) - NTFS - 38162 - Active - Primary
[/I][/SIZE][/COLOR]

So FINALLY (sorry for my error):

 I installed Ubuntu first (with no WinXP in the HD) in the HD's 1st partition.  It booted correctly.
Later I installed WinXp in the 3rd partition (called LocalDisk F: ). Boots correclty but no multiboot menu.

So is this method still good for me? 
[COLOR=Green][SIZE=1]*If you wish, you can reinstall Ubuntu and put the grub loader back in the MRB (that is the default). If all goes well, when you reboot you will get a grub menu with a selection for booting W$. Your config looks simple, so this should work. If you run into a glitch doing this, since you have an XP install CD, fixing that would be easy.*[/SIZE][/COLOR]

I can't use your second method since my laptop doesn't have a floppy drive.

Thanks again.

---

### Post by Bjorg on 2005-07-11
[QUOTE=mingus]Your post is confusing.

So which is it???  If you did not install W$ in the first partition, it would not boot.  So you must have installed it there.  Therefore you do not need to reinstall W$.

[/QUOTE]

Sorry, but WinXP Pro is installed into my HD's 3rd partition and it boots ....   ??? :-|

---

### Post by Lodis4 on 2005-07-11
I have class tonight after work, if I get a chance to post this I will, otherwise, I will wait until after work on Tuesday.

Thanks for the help so far Mingus!! It would be nice if all forums were like this my first impression of this one.

---

### Post by Bjorg on 2005-07-11
Lodis, sorry for "stealing" your post. ...

---

### Post by Bjorg on 2005-07-11
Hey I got it to work!!   \\:D/  . I just reinstalled Ubuntu again at placed GRUB in the MBR.

Thanks Mingus.

---

### Post by Lodis4 on 2005-07-11
Hey its all good, glad you got, ehhh........."fixed."    lol

---

### Post by MappyH on 2005-07-11
[QUOTE=Lodis4]OK here is the exact syntax:

Booting Windows NT/2000/XP

root (hd0,0)
filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1 

I am reasonably new to Linux, I have seen a few references to these things individually but I have no idea where to start looking for a solution. ](*,)  It is weird that nothing happens when I get this. No beeps no errors, nothing...[/QUOTE]

I had this error after installing suse, after searching the net I found advice from suse telling me to enable LBA for hard drive in bios.

edit: [http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html)

---

### Post by mingus on 2005-07-11
[I]Sorry, but WinXP Pro is installed into my HD's 3rd partition and it boots ....   ??? 

my real HD's scheme is this:

(Partition) - ( Type) - (Size MB) - ( Status) - (Pri/Log)
(/ root) - Linux Ext3 - 36240 - None - Primary
SWASPACE2 - Linux Swap - 1906 - None - Primary
Local Disk (F: ) - NTFS - 38162 - Active - Primary[/I]

There is a common misconception that Windows must only boot from the first partition.  In reality, Windows boots from whichever primary partition is marked as active, also called the system partition.  Furthermore, the system partition need only have the boot loader files on it; the rest of XP can reside on any other partition, including a logical.  However, even though Windows permits this, there can be issues.  For example, Windows wants to use C: as the drive letter for the system partition; as you see above F: was assigned.  MS generally recommends changes the drive letter assignment to C:, but again, there can be risks with this because pointers to drive letter get created in the Registry, changing the drive letter can break these pointers. 

If you are successfully booting straight into W$, you should be able to use the same procedure to boot from it into Ubuntu that I described before - except that you have the problem of not having a floppy to make the file transfer to W$.   There is a workaround, although it is a bit complicated for a newbie.  If you want to give this a try, I'll give you instructions.  You can get an idea of it by looking at steps 2 and 3 at: [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

If you want want to use grub to manage the boot process (the first option in my previous post), that should work, too.  All things considered, and since you have an XP install CD, this is probably the easiest.

*I don't want to reinstall WINXP again because Norton Antivirus during the activation process will think I am installing the antivirus on more computers than mine.*

I don't think so.  WPA uses a hashing algorithm to create a unique signature for your hardware configuration; this is what gets stored on the Symantec server when you do the WPA process.  If you reinstall, it will recreate the signature and compare it to what is on its server, if it's the same, it knows you are reinstalling on the same machine.  Symantec uses the same method as does MS with XP.

---

### Post by Lodis4 on 2005-07-12
OK I fixed the issue. 

When I installed I say Grub referred to XP Pro as NT/2000/XP which I though was weird but ehhh ok I'm game. When I looked at my /boot/grub/menu.lst file and realized there was not any actual partition references. Then I realized I had installed Warty instead of Hoary ssooooooooooo.......

I reinstalled XP, then installed Ubuntu 5.04 and VIOLA!

I am confident that I would have found a solution and been able to fix the original problem but I was not in the mood for patience.

---

### Post by darkmatter on 2005-07-12
[QUOTE=Lodis4]When I installed I say Grub referred to XP Pro as NT/2000/XP which I though was weird but ehhh ok I'm game.[/QUOTE]

The reason Grub refers to XP as NT/200/XP is that they are technically the same (NT platform). If this bothers you, just edit the title for your XP in menu.lst to read 'Windows XP Pro' or whatever you like (mines dozer) ;-)

---

### Post by dave9191 on 2005-07-12
Yeay, now everyone is happy and we can all go back to sleep :) Glad that you 2 are happy, now get on with using linux :)

Dave

---

### Post by Lodis4 on 2005-07-12
[QUOTE=darkmatter]The reason Grub refers to XP as NT/200/XP is that they are technically the same (NT platform). If this bothers you, just edit the title for your XP in menu.lst to read 'Windows XP Pro' or whatever you like (mines dozer) ;-)[/QUOTE]

Thanks for all the help everyone!

I actually now have Grub referring to this as Windows XP pro instead of a generic NT label. I believe part of the problem with the dual boot caused Grub to not recognize XP, properly.

But hey, it works now so who cares right? \\:D/

---

### Post by Bardaf on 2007-10-23
Hi All,

To make a dual boot with win xp, first you have to install Windows and then you can install Ubuntu. Otherwise, Windows change the MBR or bootsector( I don't remember wich one), this is the reason you can't start Ubuntu.

My laptop work fine (HP nc6120) in dual boot Win XP Pro SP2- Ubuntu Gutsy 7.10.

Have fun  :guitar:

---

### Post by ham-13G on 2008-01-10
hi Bardaf,

may i know your nc6120 configuration? is ubuntu 7.10 works fine an the hardware installed correctly? i'm new on linux, so i want to make it save for my laptop to install ubuntu.

Thanks
:p

---

