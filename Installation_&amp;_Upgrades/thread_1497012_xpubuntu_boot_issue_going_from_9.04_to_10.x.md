---
title: "xp/ubuntu boot issue going from 9.04 to 10.x"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by macguru on 2010-05-30
hi everyone..initial setup was Windows XP HOME with Ubuntu 9.04 installed on a separate partition created during install. This booted and worked fine. I updated everything. Was offered to goto 10.x (latest) -- accepted. 

now I  cannot boot win xp OR (recovery partition which was seen previously by grup and booted fine just like XP did), this happened during 'upgrade' for grub to grub2 -- i think it did something directly to the two partitions for windows xp and recovery partition 

 note grub and supergrub see the winxp and 'vista' (recovery) OS's just fine but just drops to a dash (-) and no disk activity when you try to boot from them

 when i was updating from 9.10 to 10.4 (i think) it loaded a grub installer..the help said 'select them all' when in doubt...but that was a mistake...it was doing something to the partitions..have not the tech skills with linux to know what...but it said error couldn't do something and kept saying 'not recommended' and it would use some special method that doesn't work typically--- as the installer was trying to do its thing....so the next round i selected ONLY the single drive in the system itself and it said installation successful no errors etc.... in the meantime it may have hosed the recovery and xp partitions...i have since reabsorbed the linux partition into the xp one with parted magic and then reinstalled ubuntu 9.04 but the grub sees both XP and Recovery and ubuntu but only ubuntu can boot

 its a netbook with winxp home....brand new...and some kind of vista booter for the recovery mechanism..
 i got a vista recovery CD and tried that..it sees NO windows installations  (i guess it cannot see XP and says so)
 have no idea why they had to used a hybrid but they did....so right now all i can boot off is ultimatebootcd which has supergrub and things..i could install grub from there as well but even when it see's xp and you trial boot it just hangs...any clue what the updater might have tried to do when going from 9.x to 10x?

 the files seem intact in windows xp part (c:) and i think the recovery part is x:    both seem fine

i tried using mbrtool to set the mbr back (removing grub) -- still hangs and messed up grub so went for a reinstall of ubuntu and have grub working now but only for ubuntu.....

 any ideas what is a nonstandard thing that it would have tried to do when configuring grub update and having  the partitions selected rather than just the drive?

 i seemed to remember seeing all kinds of warnings that it was not recommended (couldn't stop it as it was in the background running from the standard update installer -- was just scrolling by)..i guess it was installing grub to partitions instead of the start of the drive...or was trying to...is there any way to reverse this?   i hope someone has run into this and can help....


hope i have been clear enough
THANK YOU so much in advance!!!

---

### Post by darkod on 2010-05-30
It said "if in doubt install on all DISKS", not to select all check boxes including all partitions.
You need to start to make a difference what is a disk and what a partition on it.

You will need to run this fix on both your windows and recovery partition, one at a time:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you are in doubt which are these partition, run the boot info script as per these instructions and it will show you more details:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

If still in doubt, ask here.

---

### Post by macguru on 2010-05-30
you're quite right it likely said 'disks' --- but then why offer to install to partitions in the first place for instance? i do discern disk from partition but this was a bit misleading  (IMHO)
not know precisely how grub operates I had no idea if it needed to be on all those offered check boxes (including partitions) .. a mistake I immediately noted but it was too late to do anything about it...

i do not know why the installer  wasn't set up a bit more intelligently so that merely parsed the existing settings and updated them to the new grub format??


i don't have  any access to a windows xp recovery CD so the easier options were not available and ultimatebootCD utilities didn't seem to have the scope to accomplish what was needed

after looking over your link briefly it seems it is precisely the nature of the issue i'm having

I appreciate your help again very much -- I have been looking for a solution for a day or two already and was unable to find the topic covered via searches 

i will let you know how it goes or if i run into any troubles...wish me luck .. thanks!!!!

---

### Post by macguru on 2010-05-30
testdisk reported that the backup boot record was bad
i tried the rebuild but that didn't work
sourceforge link directs back to windows cd which I don't have
any other options or suggestions? thanks again

---

### Post by darkod on 2010-05-30
Uhhh... for Vista and 7 MS released repair CDs because these days usually you don't get install media with the computer. They are released free for download but they can only help repair basic things, like the boot process.

Not sure if something similar exists for XP. I guess MS didn't bother with it, maybe some enthusiasts.

The only I can think of is trying to google for "how to reinstall xp boot files without cd" or similar.

---

### Post by darkod on 2010-05-30
For windows if you hit F8 you get advanced options, but I don't know at which stage of the boot process that happens.

You can try selecting XP from the grub menu and start hitting F8 right away, if it shows you the advanced options at least. And I'm not sure if there is something like Recovery Console in them at all.

---

### Post by macguru on 2010-05-30
yes, microsux still doesn't supply this tool online anyplace that I can find.

i'm looking at [http://www.ubcd4win.com/](http://www.ubcd4win.com/) right now to see if this may help

i have  a very old windows xp boot cd but it crashes when I try it. I may end up having to wait on restore CD's to be mailed that I will have to purchase from the pc vendor ...

if you think of anything --- let me know..thanks again! best regards

---

### Post by macguru on 2010-05-30
i thought of the f8 also, it never gets that far unfortunately -- doesn't boot at all

---

### Post by macguru on 2010-05-30
just to note, i believe grub wrote to the partition given the circumstances but it does not goto grub again when trying to boot the xp partition it just hangs

the updater for grub said it was using something unusual ..i cannot recall..but it said it was not recommended and often failed...have any idea what it might have been doing to the partition?

re:"Grub was installed to the boot sector of the Windows System Partition. So when trying to boot Windows, the Grub code in the Windows boot sector is activated and the Grub menu appears. Sometimes Grub is not installed correctly, resulting in various different errors. Running the boot info script is an easy way to diagnose this problem. It will show the the "Boot sector type" of the Windows system partition as some version of Grub."

---

### Post by darkod on 2010-05-30
The message about not being recommended might be because installing grub2 on a partition is not recommended as a whole. However, some people that insist to use the windows bootloader, are installing grub2 to the ubuntu partition and it's working fine.

But on the windows partition there is no easy way out of this, because grub2 boots windows by chainloading and leaving the boot process to continue from there. Now you have another grub2 there, and it will just go in circles.

You can try one more thing, but not sure if it will work (I have tried it with win7 and it worked).

In the grub2 boot menu, highlight the XP enrty but don't press Enter. Press 'e' and it will show the boot lines.

In the line chainloader +1 change it to try to call the file directly, not the bootloader as a whole. So, for XP it would be something like:

chainloader /ntldr

because I think that's the XP loader. Press Ctrl + X to try to boot.

If that works, it might be a work around until you get hold of XP cd. If it doesn't, try also with:

chainloader /boot.ini

but I think the /ntldr is the correct file.

---

### Post by macguru on 2010-05-30
same problem here [http://ubuntuforums.org/showthread.php?t=1472140&page=2](http://ubuntuforums.org/showthread.php?t=1472140&page=2) but he managed to get to recovery console

i have a vista boot cd but bootrec won't fix XP i need fixboot


is fixboot anywhere on the c: drive that has windows xp installed? i have not been able to find it


thanks
--again

---

### Post by darkod on 2010-05-30
See also my previous post if you missed it. It might help.

---

### Post by GoldenAxe on 2010-05-30
I had this problem. Updated from 9.10 to 10.04 and lost access to Windows XP at boot, which was installed on a seperate hard drive. When I tried to boot Windows I just got a black screen with a cursor blinking top left.

Darkod's fix worked perfectly. Thanks!

---

### Post by macguru on 2010-05-30
goldenaxe which one worked perfectly? the grub /nltdr ?

---

### Post by macguru on 2010-05-30
hi darko,

no luck on the edit of grub (e)


i have no way to get to an XP recovery console ..... what a hassle!!!


i have an original partition magic CD here..its bootable...
apparently its SO old it doesn't work anymore..it boots but doesn't even mount C

---

### Post by darkod on 2010-05-30
Well, the last resort is: get a pirated copy. You paid for your license so technically it's not even illegal.

Besides, you will not install XP from that CD, just use it to repair the boot sector...

Or give testdisk another go first.

---

### Post by macguru on 2010-05-30
hi

I did try the testdisk again but it thinks things are fine....no option to rebuild and says they're indentical now....

sorry for delay in replying

---

### Post by macguru on 2010-05-30
found a utility called GUJIN -- it shows GRUB for the two windows partitions, recovery and XP as we suspected



darko do you have any idea how i could use Grub2 to boot windows? saw a post about using grub2 to boot macos x  -- sounds like its possible

i am trying to find info on it but if you see this and have any knowledge on it let me know

thanks again!!!!!!!!!!!

---

### Post by darkod on 2010-05-30
> **macguru said:**
> found a utility called GUJIN -- it shows GRUB for the two windows partitions, recovery and XP as we suspected



darko do you have any idea how i could use Grub2 to boot windows? saw a post about using grub2 to boot macos x  -- sounds like its possible

i am trying to find info on it but if you see this and have any knowledge on it let me know

thanks again!!!!!!!!!!!

I know how to boot windows from grub2 but your situation is complicated because of the grub2 installed on the windows partition.

You see, the way grub2 (which is on the MBR) boots windows is it just knows which the windows partition is, and it's calling the boot files on that partition to continue the boot. But in your case, the grub2 is continuing because it gets in the way, and it has nowhere to go. Hence the blinking cursor in the corner. And it stays like that.

Until that bootloader is removed from there, I have no idea how to make XP boot.

---

### Post by macguru on 2010-05-30
understood

i tried using another mbrwork utility 
it claims it installs 'standard mbr' 
gujin still shows GRUB on that drive however


studying this presently [http://www.insanelymac.com/forum/lofiversion/index.php/t189079.html](http://www.insanelymac.com/forum/lofiversion/index.php/t189079.html)

one post makes it sound like the bootmanager can handle windows but it may well be like you said in your prior post.....just passing off to the windows boot manager right?

---

### Post by macguru on 2010-05-30
one old bootable CD tries to setup windows xp
cannot get to recovery console cause it crashes with
STOP: 0x0000007b and more in ()
from looking around the web it would seem this is a bootsector related error...its looking at the drive and thinks its a virus??? do you suspect this is the case? if it is then its a real catch 22 to repair this problem of grub2 going onto the boot area of the drive

note that the windows vista recovery CD does not give any error and boots but it cannot see xp installations just vista and the commands are different.... bootrec doesn't do the same job as those in the recovery console under XP

i may have an xp disk issue (owing to age or differences in releases) but do you think it thinks this is  a virus situation ?? 



i do not understand why mircosoft releases recovery CD's for vista/7 online but nothing for XP after ALL these years...doesn't make any sense really

---

### Post by darkod on 2010-05-30
I don't have a clue what that STOP error might mean. But the situation does look like catch 22 definitely.

As for trying to make sense of MS, it might be because with XP they were still shipping install media (cd). In the past few years, maybe thinking that would help battle piracy, vista and 7 come on restore partitions without media, so releasing those repair images was under a pressure from the customers I guess.

Have in mind that the repair image is still not proper install media which lets you reinstall your OS without wiping your hdd in the process (that's what usually the restore partition does).

---

### Post by macguru on 2010-05-30
ok, took a loot at a utility called XFDISK [http://www.mecronome.de/xfdisk/files/history_en.txt](http://www.mecronome.de/xfdisk/files/history_en.txt) its supposed to be a bootmanager --- i installed it and told it to replace the bootmanager on the XP partition (1st part after recovery partition)

it does boot into a screen which lets you select windows XP

then says its booting please be patient

lolz


of course it isn't

GUJIN (another utility) still shows GRUB as booter even after i put in the XFDISK change
[http://gujin.sourceforge.net/](http://gujin.sourceforge.net/)

i was maybe at least hoping that windows recovery might run if it sees something else...will try that just in case..but with Gujin saying GRUB still I have my doubts
whatever Grub2 did to setup booting from partition it sure hosed this system royally

PS: all these utilities are off the ultimatebootcd just in case you or someone else needs them or are interested

---

### Post by macguru on 2010-05-30
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893)  SEE THIS FOR REFERENCE.

IF ANYTHING COMES TO MIND LET ME KNOW


I am dead in the water as of now short of getting factory install disks which will wipe everything....that is OK and i'll start over -- i sure hope the reinstaller dvd/cd's allow for a reformat and reinstall like factory..i assume they should but hassling around with windows again has taught me that nothing can be taken for granted particularly if its logical and makes sense.


Thanks very much Darkod for sticking with me......
Still hope we can figure a workaround


it would be nice not to have this thing beat me! lolz

---

### Post by kansasnoob on 2010-05-30
Look at Meierfra's first post here:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

It includes a tar.gz with XP boot files.

---

### Post by macguru on 2010-05-31
hi, thanks kansasnoob for your reply

i finally got a xp w/ recovery console cd to boot...the STOP problem did have to do with the fact that the XP was so old ..what was going on was the controller for the HD was AHCI, i switched that in BIOS to  IDE and success the CD booted (apparently able to see the drive in that mode and thus not crashing)...got to recovery command line...used fixboot/fixmbr and got a normal nt-xp loader where grub was on C (win xp drive)

used ultimatebootcd to mbrwork to switch active partition and did the same thing to the vista recovery... cause it still showed GRUB in GujN -- tried bootrec /fixmbr from vista recovery console but that still shows as nt/xp-loader    bootrec /fixboot does not see any active installations which is probably correct because this is only a recovery CD so it won't rewrite the loader for vista which I believe must be different than nt-xp loader since vista uses a registry type table to boot and not the ntldr loader -- still learning and reading on this.


there WAS previously  a splash screen before GRUB2 did its damage that said press f5 for recovery
i have no idea how this was implemented....still trying to figure it out

in the meantime i have windows XP booted so thats a relief

will still keep hacking away at the rest. thanks everyone very much!!!


does anybody know if you can start anything in VISTA from windows xp? could I set it up as another windows os (the recovery software) in the boot.ini???   it would be a way to get back to default and accomplish the same thing right?

---

### Post by oldfred on 2010-05-31
I was looking around MS site to see if they had anything downloadable for repair and saw this.

see this:
Option 3: Adding the Windows Recovery Console as a startup option
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

If you have repaired each windows you may be able to directly boot both from grub where before windows combines boot files into the active partition (boot flag) of the first install from the second install and windows then only boots one partition. Grub then only can directly boot into the windows choice. But if both are separated then grub can boot either:

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by macguru on 2010-05-31
hi oldfred

they put two partitions on this computer from the factory
 1 is a vista partition with a recovery program that runs in a text/dos type window
2 is the bootable windows xp

before falling to the grub2 fiasco (which overwrote both bootloaders) the computer would boot, splash manuf. and f2 for bios then it would say on its own screen hit f5 for recovery
if you did that it would boot and then run a script that replaced the windows xp partition files so that they were factory like..i.e. win xp home would have to start up new and reconfigure etc.


now i finally have an nt/xp loader for each partition
there must be a vista loader for vista/7 but i used a vista recovery CD and it doesn't see a 'vista installation' -- tried bootrec /fixmbr etc.etc... didn't work out apparently cause it does not see vista installed so it won't rewrite to a vista bootloader....

i just used gujin to see what could be booted
both say nt/xp loader
when you try the one for the vista partition it tries to load with the wrong nt/xp loader and says 'nldtr' not present hit ctl-alt delete to restart...

so now i am able to use windows......at least

hopefully can figure out what kind of a factory setup existed
does not look like xp can boot vista however

thanks again. hope this explains it

---

### Post by oldfred on 2010-05-31
It may not be a true Vista partition. It just may be a recovery partition and during the time they were installing either XP or Vista the recovery was compatible with either (for booting) as is just seen as Vista.

---

### Post by macguru on 2010-05-31
hi oldfred

according to my research
it has the right files to be a 'vista' partition
it is hidden and inactive
none of the file sets changed
the typical boot files for stuff prior to Vista are missing

it isn't a full install of vista naturally but it did use to boot into a command line window then throw up an option to restore the other drive (i.e. erase all and reinstall XP as typical)


when I got the vista recovery download from MS and booted off the CD (made this the primary partition first with another utility) -- the Vista recovery asks to send a report and when you look at the details it says the bootmanager is missing (i believe it said bootmanager i could try it again ifyou want me to get the exact wording)


grub, before it became grub2 and overwrote the bootloaders indentified it as vista --- the system comes from factory as Drive with 2 partitions 1 is the vista recovery and 2 is the xp -- i believe Vista booter could handoff to XP from the reading i did....so i was thinking it may have been booting all along (until grub2 did its damage) from there and then going to 2nd partition XP  -- however this seems unlikely because that partition isn't active and 2 is (the one with XP) so perhaps there is a way to invoke a startup from the first volume with a function key...... the boot.ini on xp volume 2 was not modified so i cannot see how that may or may not have been implemented

---

### Post by darkod on 2010-05-31
I'm slightly confused by something. You said partition #1 is a vista partition with recovery program, I guess that means a vista recovery partition. And #2 is the XP system partition.

Usually a vista recovery part would be used to recover your computer with vista identical to the factory setup. Did you put XP on there yourself? If yes, why not simply over the recovery partition, or deleting it, so you can also utilize that space?

Anyway, so many things have happened trying to restore your XP booting, I think we need to see the current results from the boot info script.

And also, to tell us what is your question right now exactly, is the recovery partition missing from grub menu, or how to access it, or what ever...

---

### Post by macguru on 2010-05-31
hi darkod

> **darkod said:**
> I'm slightly confused by something. You said partition #1 is a vista partition with recovery program, I guess that means a vista recovery partition. And #2 is the XP system partition.

Usually a vista recovery part would be used to recover your computer with vista identical to the factory setup. Did you put XP on there yourself? If yes, why not simply over the recovery partition, or deleting it, so you can also utilize that space?

Anyway, so many things have happened trying to restore your XP booting, I think we need to see the current results from the boot info script.

And also, to tell us what is your question right now exactly, is the recovery partition missing from grub menu, or how to access it, or what ever...

I have NO idea why they made it a Vista partition for Recovery -- this was factory. I thought that was odd as well and may have mused about it. My guess is that the company simply did it for their own ease of implementation because this may be one of last of the units to ever ship with XP. It came with XP Home from the factory..it is a netbook. I did not install XP. 

Now the unit boots directly with the windows bootloader (nt-xp) nldtr and runs windows xp -- no issues. All other linux partitions were absorbed into partition 2 using PARTED MAGIC leaving only the two factory partitions which were untouched other than grub2 writing the bootloader sectors.

the 'vista' implemented recovery partition writes XP as a fresh install
very odd...

formerly the unit said 'press f5 for recovery' when it booted -- i have no idea which part booted originally from factory but i presume it must have been the XP volume 2 because that is the active one..correct? it may have had a special bootloader (nt/xp) that could boot into the vista partition to start the recovery script perhaps????????? is this possible you think???

i am at a loss to figure that out....which file would you invoke in the vista partition from inside windows xp during boot that would allow it to startup? any ideas?? 

i presume it must have been a special bootloader or a script..but so far as I know (going by dates) the boot.ini was not changed nor were any of the other xp startup files

incidentally -- Grub and grub 2 saw the 1st partition  (hidden) as vista loader, 2nd partition as xp -- later after the grub2 incident it saw them both as grub (as you know)

---

### Post by macguru on 2010-05-31
> **darkod said:**
> I'm slightly confused by something. You said partition #1 is a vista partition with recovery program, I guess that means a vista recovery partition. And #2 is the XP system partition.

Usually a vista recovery part would be used to recover your computer with vista identical to the factory setup. Did you put XP on there yourself? If yes, why not simply over the recovery partition, or deleting it, so you can also utilize that space?

Anyway, so many things have happened trying to restore your XP booting, I think we need to see the current results from the boot info script.

And also, to tell us what is your question right now exactly, is the recovery partition missing from grub menu, or how to access it, or what ever...

grub is not presently installed -- i'd like to figure out how to be able to boot into the vista recovery partition for recovery purposes should that be needed in the future -- i.e. get back to the factory setup i had initially 

i tried using supergrub (off a cd bootable) to start up the vista partition recovery  but it cannot do that ..it just hangs...this is true even though the bootloader is now xp/nt -- it looks for the nltdr etc... i really cannot figure out how i'd be able to get a vista bootloader back into that area since the vista recovery CD does not see a full vista implementation it doesn't mess with it..it also asks to send a note to MS regarding the missing bootmanager situation (i.e vista bootloader i presume)

---

### Post by wilee-nilee on 2010-05-31
You will need to post the script as darkod suggested if you want to get to to the heart of the matter. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
In code tags, [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2010-05-31
Like I said, it's time to run the script again. It will show us more.

Depending what exactly the restore process do. Maybe it cleared grub2 from the recovery partition boot sector too.
In that case it would appear in the grub2 boot menu (once you reinstall grub2 to the MBR). We need to see what is the current situation.

Because if we can make it boot with grub, don't worry about the F5 option not being there. You will be able to start it from grub.

---

### Post by macguru on 2010-05-31
hi everyone,

i wouldnt have a problem with  using Grub again if it could boot the recovery partition but it cannot (at least in its present state)

i have supergrub and supergrub2 on ultimatebootcd --
running supergrub 2 1.30 --selecting any os
i get

windows nt/2000/xp loader
windows vista bootmgr
other os

selecting other os (not sure what its seeing) it gives error: invalid signature
selecting windows vista bootmgr it gives NTLDR is missing hit CNTL ALT DEL to restart
selecting nt/2000/xp it will boot into XP

so grub2 see's the windows vista bootmgr but it has an xp/nt/2000 bootloader so it looks for the wrong thing..vista/7 use a different bootup

[I]> note: The sequence of booting Windows Vista is slightly different from any previous version of Windows that uses the NT kernel. First, when the computer is switched on, either the BIOS or the EFI is loaded. In the case of a BIOS system, the MBR of the boot disk, which can be a hard drive or external media, is accessed, followed by the boot sector of the drive or of the relevant hard disk partition. This boot sector then loads the rest of the boot blocks. For Windows Vista, the boot sector loads the Windows Boot Manager (with filename BOOTMGR), which accesses the Boot Configuration Data store and uses the information to load the final stage, the operating system. The Windows Boot Manager (BOOTMGR) reads the boot configuration data and displays an operating system selection menu,[1] and is thus, in some respects, equivalent to the boot selection menu functionality of NTLDR in prior versions of Windows NT. A notable change is that the Windows Boot Manager is invoked by pressing the space bar instead of the F8 function key. [2] The F8 key still remains assigned for advanced boot options once the Windows Boot Manager menu appears.
To maintain a consistent boot experience on Extensible Firmware Interface systems that also have a boot manager of their own, the Windows Boot Manager, and hence all of the installed Windows operating systems that can be booted using it, appear as a single entry on the EFI boot manager menu. (On EFI systems, the Windows Boot Manager is an EFI application stored on the EFI System Partition). Microsoft only adds multiple entries to the Windows Boot Manager (BCD) menu itself, and sets the timeout of the EFI boot manager to two seconds.[/I]


> Depending what exactly the restore process do. Maybe it cleared grub2 from the recovery partition boot sector too.
In that case it would appear in the grub2 boot menu (once you reinstall grub2 to the MBR). We need to see what is the current situation. -- again, i set the main bootable partition to the recovery partition and loaded the windows vista CD and it wants to notify MS about a problem with 'missing bootmgr' -- for what it was worth i went ahead and used the windows XP recovery console and did fixboot fixmbr on this partition in hopes the bootloader would be the same (since vista recovery could not repair it or simply would not) and it finally got rid of the grub2 that was occupying that area -- this is evidenced by Gujin booter which sees the bootloaders and it formerly showed grub2 (as did both until repaired)


> Because if we can make it boot with grub, don't worry about the F5 option not being there. You will be able to start it from grub.  i sure could live with that but it doesn't seem possible given all i'm seeing....the problem is the bootmgr that must be written in the beginning of the partition for vista -- vista recovery software doesn't see an actual vista installation cause its only a partial one and it wants to send the error to ms that the bootmgr is missing...  as of now..be clear...supergrub2 Cannot boot this recovery partition (it has an nt/xp bootloader which is trying to look for NTLDR.... its nice grub2 is gone but the original isn't

is it possible to run that script you guys mention from live CD? would it do any good at this point (i doubt it given what i've outlined)

the problem now is finding a way to get the vista partition to boot for recovery purposes should it be needed one day in the future -- this would entail getting the correct bootmgr that grub2 overwrote in the right place on that drive....


i do not think grub2 touched any of the files for booting on either partition (as evidenced by dates etc) it only changed the beginning sectors have the bootloader/bootmanager

the directory for recovery partition has a file called bootmgr so i presume its looking for a bootloader which cannot be repaired by the vista recovery cd automatically or manually

i made vista partition active
booted vista recovery
it cannot see installations of vista (obviously cause its partial right? just enough to get a restore script going)
goto command prompt
type bootrec /fixboot
error "the volume does not contain a recognized file system. pleae make sure that all required file system drivers are loaded and that the volume is not corrupted"
the volume is fine..chkdsk fine..computer new with no use until install of ubuntu where grub2 trashed it (due to misleading statement -if in doubt select them all)

bootrec /scanos says 

succressfully scanned windows installations
total identified windows installations : 0
operation completed successfully  (note this will  ONLY find vista/7 installations not xp)

i did try  bootrec /fixmbr then bootrec /fixboot


well here is some more information
this recovery partition appears to be using boot image of some sort
inside the /boot folder (normal on vista from what i've seen) it has a 3GB file boot.sdi
there is also  a BCD file bootfix.bin etfsboot.com and a directory fonts
main directory of the recover partition

boot dir
bootmgr
efi dir
imagex dir
napp6.log
rcv dir
sources dir
temp dir


my guess is that somescript in the bootloader in XP with f5 must have invoked something similar to this  [http://technet.microsoft.com/en-us/library/cc771845(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc771845(WS.10).aspx)  this only makes sense since the active partition was the XP one...the f5 probably opened a ramdisk of some sort which invoked the recovery scripts--however now that i think about it...grub could boot that vista loader so that partiion must have been capable of self boot prior to the grbu2 overwrite......so again how to get the right vista loader on there when the system thinks there is no true vista on that partition...can NTFS use MSDOS??? i think that is limited to FAT right?

i am none to familiar with these directly but i am familiar with the concepts...willing to learn -- if anyone can save the learning curve that would be great

any ideas??

i know its been a real chore, hard to wrap the mind around and complex -- thanks for hanging in there everyone...


i am trying to find recovery CD's for this computer....in which case i could backup the xp installation files and just blanket out the entire drive whereby it would be factory including the recovery console..i hope its possible..this may be the only way at this point....but i'm sure there are people who know more and may figure a hack around the hangup..

---

### Post by darkod on 2010-05-31
At this moment it is all up to you.
If you did manage to get rid of grub2 from both partitions as you said, I would reinstall grub2 to the MBR now and do update-grub.

Don't rely too much on Super Grub Disk.

The /bootmgr and /boot/BCD files are all you need as boot files on recovery partition. A vista/7 installation has a third file, winload.exe in addition.

XP boot files are /ntldr, /boot.ini and ntdetect.com

Getting rid of grub2 from the partitions was the hard part. Now even installing grub2 to the MBR will not touch the partitions any more and you can easily return windows bootloader to the MBR if you want to. Just my humble opinion. I would reinstall grub2 to the MBR. Keeping things like this, you can't boot ubuntu also.

---

### Post by macguru on 2010-05-31
> **darkod said:**
> At this moment it is all up to you.
If you did manage to get rid of grub2 from both partitions as you said, I would reinstall grub2 to the MBR now and do update-grub.

Don't rely too much on Super Grub Disk.

The /bootmgr and /boot/BCD files are all you need as boot files on recovery partition. A vista/7 installation has a third file, winload.exe in addition.

XP boot files are /ntldr, /boot.ini and ntdetect.com

Getting rid of grub2 from the partitions was the hard part. Now even installing grub2 to the MBR will not touch the partitions any more and you can easily return windows bootloader to the MBR if you want to. Just my humble opinion. I would reinstall grub2 to the MBR. Keeping things like this, you can't boot ubuntu also.

thanks for the info

the point still remains that  the incorrect windows type bootloader is on the vista partition
grub 2 could not boot the partition when it was there and updated previously
it could only boot the partition when it was grub and had not installed itself to all partitions

i didn't just try supergrub
i used gujin which calls the bootloader directly (identifies them as xp/nt loader)
both gujin and supergrub2 can boot xp fine...it cannot boot vista recovery cause its got an xp/nt bootloader in there

> Getting rid of grub2 from the partitions was the hard part i was only successful with partition 2 (the xP partition) -- partition 1 (vista) is free of grub2 but it now has the xp/nt bootloader courtesy of me....i have no way to get the right VISTA loader on there

as i said bootrec doesn't accomplish the job....error codes above

the older XP recovery console doesn't check for installation it just does what you tell it... i.e. fixboot ... i wish bootrec /fixmbr and /fixboot would do what i tell it regardless of what it thinks it sees...i looked for a FORCE command and tried /force   DO YOU KNOW if there is a force command that I can invoke..if there is that would fix it i think  let me know and thank you

---

### Post by macguru on 2010-05-31
if there is a command line in vista to force bootrec /fixboot that would do it

this is what i need..have not found that info yet

---

### Post by macguru on 2010-05-31
i am investigating a utility called EasyBCD right now
will let you know how it goes
it allegedly can overwrite grub with the vista or xp bootloader
so hopefully can get around it
if it runs in XP i may be homefree
wish me luck!!

---

### Post by oldfred on 2010-06-01
All the repair software that talks about fixing boot of windows is installing the MBR which is relatively simple. The partition boot sector is more important and harder to recover as it varies a lot more.

I still wonder if the computer you purchased was standard with Vista and downgraded to XP and they never bothered to remove the Vista recovery partition. A vista recovery will not repair XP and XP does not have a separate repair partition. XP may have a vendor supplied recovery partition instead of the XP install disk but it is usually an image to reinstall the system to as purchased, erasing the entire drive.

---

### Post by deadeyes666 on 2010-06-02
Hi all,

I am recently investigating an issue that seems to be the same as the OP.

After an update of Ubuntu netbook remix from 9.04 to 10.x on an Acer d250 netbook it seemed that the grub bootloader has not only been installed on the linux partitions but also on the Windows ones.

The configuration is as follows:
sda1: recovery partition (mentioned as Vista in grub, however I doubt if that really is a vista partition)
sda2: Windows XP
sda7: Ubuntu netbook remix (10.x)

First of all the system could not be booted after migration from grub to grub2.
After some reading I got it back to work rather easily.

However when I select Windows XP to boot I just get a blank screen with a cursor blinking in the top left corner. It hangs there forever. After trying several grub configs the result was still the same.
After using the Boot Info Script ([http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)) it mentioned that grub was installed on the sda1 and sda2 partition. I don't know if that was a bug of Grub2(maybe the install scripts) or a human error where to much partitions were selected in the config menu.

I googled for some info about this error message and it seemed that the MBR was corrupt and that this could be fixed using Testdisk.
I tried using testdisk and where normally you can copy the backup bootblock to your original bootblock, it seemed that the backup bootblock was corrupt.
So no possibility to restore the backup there.

I also knew I could use fixboot to do this. This is on the Windows Recovery Console.
Another way was using a recovery install.
1st option: the windows install cd could not see the diskdrive, so making it impossible to use fixboot. After that I tried with a vista recovery cd (this cd has bootrec and bootsect as tools to be able to fix both boots for vista/xp/2003/2000 as these have bootloaders 5.2 and 6.0). The netbook showed that the found windows partition was not mountable(mountable as in: I don't want to mount as it is not M$ Windows Vista) for recovery. I got on the recovery console using the vista recovery cd but I could not succesfuly use the bootrec/bootsect tools probably because no windows install was mounted.
2nd option: When trying to do the install, the cd could not detect the hdd. This made it impossible to reinstall.

After this I tried some other things:
1: creating a BartPE bootable cd. Now I got the correct drivers on the cd which is great.
However there are no tools to rewrite a bootblock included.
So I searched the cdforums and found mbrfix is a tool that should do the trick.
However I could not find a plugin to include it onto the cd. The forum mentions link, but these are invalid.
Using the mbrfix binary on the running os itself (see below) I was not able to write a correct bootblock (I had the choice between DOS5, DOS6 and Win95). None of them seemed to work.
2: I tried the Paragon Rescue Kit Express ([http://www.paragon-software.com/home/rk-express/](http://www.paragon-software.com/home/rk-express/))
This actually got me somewhere. It was able to recognize the Windows XP install and after that I could even boot the windows on the hdd from the cd.
That was a great step forward. There was actually also an option to restore the bootblock but this option was greyed out for some unclear reasons.
The fixboot binary itself is not on the windows installed on the hdd. So while running windows I could not fix it.

Maybe I should boot using the cd(Rescue Kit Express CD) and then install the recovery console (if that is possible from the running Windows)?
Maybe this would make the hdd accessible from within Windows XP recovery console and using fixboot. (I previously used a Windows Recovery Console CD; IIRC I can start Recovery console by using F8 when booting up after it has been installed).
Another possibility might be using EasyBCD (I don't know if it can run in Windows XP but it "claims" to be able to fix bootblock on a running Windows system; note my

emphasis on the word "claims")


This case is really frustrating... while I know the cause of this problem and the fact that using the fixboot binary it should be easily fixed, however I lost alot of time on this.

PS: after all those years Windows seems still to be the same mess it has ever been.

---

### Post by oldfred on 2010-06-02
testdisk also has some ability to rebuild the boot sector.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Also check that only windows files are in the windows root directory. Some have seen extra grub files or folders that should not be there.

---

### Post by deadeyes666 on 2010-06-03
> **oldfred said:**
> testdisk also has some ability to rebuild the boot sector.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Also check that only windows files are in the windows root directory. Some have seen extra grub files or folders that should not be there.

Strangely I did not had the option "Rebuild BS" IIRC.
On my own laptop I have this option.
I will try it when I see the owner of the netbook again :)

---

