---
title: "cant boot to windows says&quot;ntldr missing&quot;"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by sridarshan on 2009-11-14
hello
a few days back ,i edited my fstab file to autmatically mount the drives and after that i could not boot to windows ,,gives me an error,says "ntldr missing"
i tries undoing the changes made to fstab file,but no luck
please reply
i need to boot to windows for a few things
looking forward for a reply

---

### Post by darkod on 2009-11-14
You are pointing grub to the wrong partition, where windows is not. Take a better look at your partitions and their "names", sda1, sda2, etc, and try to put the correct one and see how it goes.

---

### Post by coffeecat on 2009-11-14
Edit: Posted in error.

---

### Post by sridarshan on 2009-11-14
> **darkod said:**
> You are pointing grub to the wrong partition, where windows is not. Take a better look at your partitions and their "names", sda1, sda2, etc, and try to put the correct one and see how it goes.


can you please guide

---

### Post by Herman on 2009-11-14
You problem probably has nothing at all to do with GRUB, but is most likely a Windows problem.

The most common reason for the error message 'NTLDR in missing' when trying to boot Windows XP or similar, is the Windows partition number has somehow accidentally been changed during disc partitioning.
In that case, NTLDR, NTDetect.com and boot.ini are actually there, but boot.ini doesn't know what partition number to find NTLDR in.
When that happens, simply editing boot.ini with the correct (current) partition number will solve the problem, or automatically generating a new boot.ini file with the bootcfg /rebuild command from a [Windows XP recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").

One other reason why this error message can appear is sometimes because NTLDR really is missing!
That can happen when somebody had a Windows-Windows dual boot and they deleted one Windows to install Ubuntu. When they set up a dual boot, Windows is programmed to automatically copy the boot loader files to the existing older Windows in a primary partition. The new Windows is installed in a logical partition. It's called a 'Microsoft Default Dual Boot', and it's the easiest for the user. Unfortunately nobody takes the time to tell the user their boot loader files have been copied out into the older version of Windows. When they delete that to install Ubuntu then the wonder why their newer Windows won't boot.

Take a look in your Windows partition by mounting it and looking around for those files to see if they're there or if they're really missing.
Check your partition number, normally Windows is in partition number 1, but if it's in partition 5 then it's in a logical partition.

Either way, you should go to this great website, [How to fix: NTLDR is missing, press any key to restart.]("http://tinyempire.com/notes/ntldrismissing.htm")
There you can download an .iso file for a powerful Windows XP boot loader CD which includes its own copy of NTLDR, NTDetect.com and a generic version of boot.ini which can be used to try to boot Windows in any primary partition in I think the first two hard disks. 
That should boot your Windows XP for you.

Later, when you have it booting, you can fix it by either editing your boot.ini, or if needed, by copying the three vital Windows boot loader files from the CD into the root of drive C:\.
;)

---

### Post by Herman on 2009-11-14
Here's a link to show you what the root of drive C:/ should look like from Ubuntu, [A Birds's eye view of Windows XP]("http://members.iinet.net.au/%7Eherman546/p6.html#A_Birdss_eye_view_of_Windows_XP")...** **showing the important files needed for booting.

---

### Post by darkod on 2009-11-14
Pardon me, I always try to learn new things. :)
The OP said the problem started after tempering with the /etc/fstab file. Wouldn't that mean he changed something and all files are still there?
Yes, ntldr missing could mean error in boot.ini but in windows only situation, or not? I always thought that once grub is running the boot process it "jumps" straight to ntldr without boot.ini. So if I point it to a "wrong" windows partition, wouldn't the message be the same?

---

### Post by Herman on 2009-11-14
> I always thought that once grub is running the boot process it "jumps" straight to ntldr without boot.ini. So if I point it to a "wrong" windows partition, wouldn't the message be the same? Not really because GRUB doesn't boot Windows, it only 'chainloads' the Windows boot loader by the Windows boot sector. From there it seems that NTLDR needs boot.ini to point to the right disk and partition number. It doesn't make much sense, I know, not many things about Windows do make sense. I have found out by spending a lot of time experimenting that this seems to be the case.  
> The OP said the problem started after tempering with the /etc/fstab file. Wouldn't that mean he changed something and all files are still there?I don't think editing the /etc/fstab file in Ubuntu could possibly have anything to do with it. More likely Windows was already like that but for some reason it wasn't noticed until by co-incidence not long after editing /etc/fstab.
However, another idea that might help could be to try running CHKDSK in Windows, from a [Windows XP recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), just in case some calamity happened like a slight power supply fluctuation during a disk write to the NTFS or something odd like that.

---

### Post by coffeecat on 2009-11-14
> **Herman said:**
> I don't think editing the /etc/fstab file in Ubuntu could possibly have anything to do with it.

I agree, but there is one possible scenario we need to exclude. By mounting the Windows C: partition by means of fstab, the OP had full write access (presumably) to all Windows system files that are protected in Windows. Did the OP accidentally write/change something that has corrupted the NTLDR? We need to know. Also - we don't yet know which version of Windows the OP is running. Vista is much more sensitive to writes to its C: partition than XP, and it is easily rendered unbootable.

---

### Post by darkod on 2009-11-14
Don't Vista and 7 use bootmgr instead of ntldr? I think it has to be XP max.

---

### Post by Herman on 2009-11-14
Yes, I found out we shouldn't edit boot.ini too much directly from Ubuntu.
It's okay  to use gedit to edit the partition numbers as long as we don't make a new line.
It seems that the carriage return in Linux doesn't agree with whatever is used for the same thing in Windows and the file will appear perfect when viewed from Ubuntu, but will be corrupted as far as Windows is concerned. At least that has been my experience from one of my adventures. (LOL) :D

---

### Post by coffeecat on 2009-11-14
> **darkod said:**
> Don't Vista and 7 use bootmgr instead of ntldr? I think it has to be XP max.

I stand corrected. Thanks.

We're having a nice chat, the three of us, but I think we need some more information from the OP! :p

---

### Post by sridarshan on 2009-11-14
> **darkod said:**
> Don't Vista and 7 use bootmgr instead of ntldr? I think it has to be XP max.


exactly i'm running windows xp

---

### Post by sridarshan on 2009-11-14
and now i went through the c drive of windows xp ,,,THE BOOT.INI FILE IS MISSING
if i copy someone else's boot.ini will it work??(sounds stupid)

---

### Post by Herman on 2009-11-14
No, it's not stupid, it's smart. 
You can use copies of the three vital Windows XP boot loader files, NTLDR, NTDetect.com and boot.ini from another computer.
Normally I don't think we're allowed to copy parts of the proprietary operating system, but it seems as if this situation is an exception because there's an MS Support Bulletin advising people how to do that here: [FONT=Bitstream Vera Sans Mono][FONT=serif][How to create your own boot disk for Windows XP]("http://support.microsoft.com/kb/305595/EN-US/").

If it's easier, (and probably it will be), just go to the site I already linked you to and download one of those .iso files for an NTLDR CD. It's the same thing except it's a CD and the files will already be on the CD for you. [/FONT][/FONT][How to fix: NTLDR is missing, press any key to restart.]("http://tinyempire.com/notes/ntldrismissing.htm")
[FONT=Bitstream Vera Sans Mono][FONT=serif]
With the floppy disk you can edit the boot.ini from Ubuntu (but be careful not to put any carriage returns in it), until you guess the right partition number.
With the CD, you can't edit boot.ini because you can't write to a CD of course, but it's already edited for you with a list of possible partitions and hard disks, just keep trying until your Windows XP boots. 

Then when you finally get it to boot, (first or second try I hope), you may copy the three vital boot loader files and paste them into the root of drive C:\ or whatever letter it happens to be.

I'm not sure, but may need to use a partition editor such as GParted in the Ubuntu Live CD or a Parted Magic CD to set the boot flag in your Windows partition. 
Since your boot loader files are really missing, I am guessing probably your Windows XP is in a logical partition. That means GRUB can't set the boot flag in it, (at least it couldn't last time I tried), so you need to do that with a partition editor.
I'm told that in some computers Windows can boot without the boot flag, but in mine and other computers I tried in, Windows seems to need the boot flag for some reason.

[/FONT][/FONT]

---

### Post by lisati on 2009-11-14
> **Herman said:**
> 
I'm not sure, but may need to use a partition editor such as GParted in the Ubuntu Live CD or a Parted Magic CD to set the boot flag in your Windows partition. 


<aside>
A word of caution. Sometimes it's better to use the tools that come with Windows in preference to gparted. See [here]("http://ubuntuforums.org/showthread.php?t=1212755") for one discussion on some of the challenges.
(Yes, I noticed that the OP is using XP, not Vista.)
</aside>

---

### Post by Herman on 2009-11-14
> A word of caution. Sometimes it's better to use the tools that come with Windows in preference to gparted. See [here]("http://ubuntuforums.org/showthread.php?t=1212755") for one discussion on some of the challenges.
(Yes, I noticed that the OP is using XP, not Vista.)Thank you lisati,
I have tried the partition editor in Windows 7 and I must admit that is is quick and easy to use and I agree that it's probably okay to do things that way if the user wants.
The only problem is, it sometimes requires hours and hours of defragging before it can be used, (at least from what I read), although the actual resize operation itself is very fast.

The Ubuntu installer's partition editor is absolutely as safe as any other partition editor in the world at resizing Windows 7 and Vista partitions, and so is GParted when it's used correctly. :D

The problem is, for whatever reason, there are a lot of people who keep spreading FUD and bad information based on one or two long out of date versions of GParted and wrong ways of doing things.

I have two web pages explaining the right way to resize Windows Vista or 7 and install Ubuntu, and it's really quite simple and safe when people go about it in the correct manner. ;)

[COLOR=#000000][Jaunty Jackalope / Windows 7]("http://members.iinet.net.au/%7Eherman546/p23.html") - Graphical Installation 'B'. 
Dual Boot or multi boot, use the Ubuntu Live CD's installer's inbuilt partitioner for 'Manual Partitioning' during the installation. 

[/COLOR][Jaunty Jackalope / Windows 7 ]("http://members.iinet.net.au/%7Eherman546/p22.html") - [COLOR=#000000]Graphical Installation 'C'.[/COLOR] 
[COLOR=#000000]Dual Boot or multi boot,[/COLOR] partition the hard disk first using Gnome Partition Editor in the Live CD. Then install Ubuntu Jaunty Jackalope.  
    
If you take the time to look through those two pages, you'll see the right way to do things fully explained, especially in the second or lower link.
I even have large and easy to see illustrations, so a person of normal intelligence can't make a mistake, even if English isn't their first language.

The main thing to do when working on a Windows Vista or Windows 7 partition is simply to **remove the tick from the 'Round to cylinders' checkbox** and everything will be fine. :D


[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

If people **remove that tick from the checkbox **it will be a lot faster to resize Windows because GParted won't need to move the entire partition, which takes a very long time.

Even if someone forgets or doesn't know, the damage' is not actually all the serious. 
It only takes a minute or so for Windows to reset its boot sector.
Most of the time Windows can fix itself even without the repair option in the Windows Installation CD.

---

### Post by sridarshan on 2009-11-15
im in big trouble now
i just inserted the windows xp cd
and found out that no there was no repair option there(thats what everyone suggested me to do,,ie use reapair option)

and so rebooted ,but then to my surprise even the linux grub is gone,,now it just says "ntldr missing"
so now im running "try ubuntu without any change to your compouter" option from the ubuntu cd......
I HOPE YOU UNDERSTAND THE LEVEL OF TROUBLE I;M HAVING HERE

---

### Post by sridarshan on 2009-11-15
still waiting for a reply

---

### Post by Herman on 2009-11-15
[LEFT]> im in big trouble now
i just inserted the windows xp cd
and found out that no there was no repair option there(thats what everyone suggested me to do,,ie use reapair option) :confused: I didn't advise you to use any 'Repair Option' in your Windows XP 'Installation Disk'? 
As far as I know there is no Repair Option in a Windows XP Disk. 
Windows Vista has a 'Repair Option', and it works very well too.

I'm guessing you probably booted into a  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the so-called 'FIXMBR' command.
Now you need to re-install GRUB again, here's a link, [Ubuntu Blog: Howto Recover Grub2 After Windows Installation]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html").

How about you try:
1. download that NTLDR disk and copy NTLDR, NTDetect.com and boot.ini into the root of drive C:\ from Ubuntu.
2. Set the boot flag in your Windows partition with GParted in Ubuntu.
3. Boot your [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") again and run bootcfg /rebuild and if you like you can also run fixboot.
Don't run fixmbr though, or else you'll need to re-install GRUB all over again.
The command: bootcfg /rebuild is for automatically fixing your boot.ini file if you have one or if you don't have one it will make a new one for you. 

That should do it.  ;)


[/LEFT]

---

### Post by Herman on 2009-11-15
You can download an .iso file to make an NTLDR disk from the following website: [How to fix: NTLDR is missing, press any key to restart.]("http://tinyempire.com/notes/ntldrismissing.htm")

It's very good for booting Windows XP with but I'm not sure if it'll work for XP in a logical partition, it might, but remember to set that boot flag first.
Even if you can't boot with that CD, you can at least get a copy of the boot loader files from it.

---

