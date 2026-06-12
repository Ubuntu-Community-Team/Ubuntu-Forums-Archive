---
title: "return windows 7 to normal"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by brallan on 2010-06-21
I installed ubuntu on a friend's netbook and she hated it because it was not windows. ARRRGH! I want to get this woman's computer out of my life, but first I need to undo any changes I have made. 

I would like to remove the ubuntu partitions (that's easy) and restore the windows 7 mbr (that;s the problem). I do not have a bootdisk, since the netbook came without one, but I do not want to reformat windows using the restore partition, either, since I hate windows with a passion and do not want to have to install any programs for her. what can I do to get the system back to its original state before the ubuntu installer overwrote her MBR?

---

### Post by darkod on 2010-06-21
Just because computers today come without install media, MS has released repair CDs. You can use it to repair the boot process, but not for a full install. That's why it's legal to download it.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Don't touch the ubuntu partition yet. Boot with the win7 repair cd and fix the boot process. Once the computer can boot win7 directly and is working fine, just use Disk Management in win7 to delete the ubuntu partition(s) and extend the win7 partition, or simply create new ntfs partition from that space.

---

### Post by brallan on 2010-06-21
sweet! thank you darko! the only problem is, its a netbook, it doesn;t have a CD reader. will this work with a USB key, too?

---

### Post by darkod on 2010-06-21
> **brallan said:**
> sweet! thank you darko! the only problem is, its a netbook, it doesn;t have a CD reader. will this work with a USB key, too?

Oops slipped my mind. Yes it can, with few extra steps to make the usb bootable.

Unpack the ISO, and open command prompt in windows and go inside the boot folder of the unpacked ISO. From there issue a command to make the stick bootable first:

bootsect.exe /nt60 X:

where X: is the stick letter. That should make it bootable. After that just copy all files from the unpacked ISO onto the stick.

It should boot and work fine.

---

### Post by brallan on 2010-06-21
ok, got the file downloaded and unpacked, but i get an error when I run the command bootsect.exe /nt60 D:

'bootsect.exe' is not recognized as an internal or external command, operable program or batch file.

is the bootsect program one that came with the ISO? maybe its inside a folder somewhere? the iso had one file (bootmgr) and two folders (boot & sources)

---

### Post by darkod on 2010-06-21
It should be in boot. I said go inside the boot folder and execute... :)

It should be there, check. And you can only execute it if you are inside the folder, for example the command prompt would be:

C:\path\boot

---

### Post by brallan on 2010-06-21
thanks so much for your patience. inside the boot folder there are only the files: 

bcd
boot.sdi
bootfix.bin

is it bootfix.bin?

maybe i can just make it bootable from within ubuntu and copy the files over. any reason that won't work?

---

### Post by darkod on 2010-06-21
It seems bootrec is included only on the full install dvd. :(

Basically you can make the usb stick bootable anyway you can/know. And after copying the files from the image there, just boot the bootmgr file.

For example I have a stick created with grub4dos and in the menu.lst it just says:

title Win7
uuid xxxxxx
chainloader /bootmgr

The problem with creating the stick from ubuntu is that I don't know the exact steps. If you just plug it in and install grub/grub2 to the MBR, the config files for that grub will be in your hdd ubuntu so it won't work booting on its own.

---

### Post by brallan on 2010-06-21
great! i found an easy way to do it, which is to use unetbootin! :

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by brallan on 2010-06-22
when you get to a screen which gives you these options:

startup repair (Useless: does not detect a problem with windows 7)
system restore
system image recovery
windows memory diagnostic
command prompt

you will:

choose command prompt, then type the following

bootrec.exe /fixmbr

that should do the trick!

then all you need to do is use the native windows disk utility to repartition.

---

### Post by brallan on 2010-06-22
the disk management utility in windows 7 can be found by opening the control panel and typing "partitions"

after deleting the swap and ubuntu partitions, you will also need to delete the extended partition which were are in before you will be allowed to expand the widnows partition.

lord god I hope I never again have to touch a windows machine!

---

### Post by brallan on 2010-06-22
PS - glad that's behind me. Its been a bit of an emotional rollercoaster, because i love the idea of getting people to recover from their addiction to proprietary software and am willing to go to great lengths to help. But this one was too much.

She had been asking for ages to get into ubuntu. i was a bit reluctant, knowing she would be a hard person to deal with, but when her computer failed, it seemed like a good time. she had bought a new laptop with windows 7. she'd have to learn something new, it didn't even have office installed, why not try ubuntu and see if she could deal with it?

She was terribly frustrated with change. I myself was amazed how difficult it was for me to deal with windows, something I grew up with. And everyone makes out like its so easy, but I was quite shocked that it was so hard to do things which are very simple in ubuntu. I am  so happy I left windows behind five years ago. 

i am resolving never to do  another install for someone using ms outlook or ms word or internet explorer. They must first migrate to  free software in windows like ooo, firefox and thunderbird before i am going to try  and baby them into the real world. I say the real world, because the things windows does are unreal.

for example, the laptop with XP broke and it would be fixable, but take a couple weeks. I thought, well, lets take the harddrive out, back up her data, stick the original in another machine and export the data from outlook, right? nope, it was service pack 3, and even though i believe it was original and non-OEM software, it recognized the harddrive was in another machine and booted into some kind of security measure which asked for the registration code that came with windows. She didn't have it. bad assumption on my part. i eventually got thunderbird working, but she didn't like it. then i got evolution working, and she didn't like it. she just wants her old computer back the way it was, which I worry will be difficult.

Then we repaired the laptop and put the hard drive back into her original computer, and sure enough, from then on it gave blue screens of death. now i just uninstalled ubuntu (so she just has windows 7 in the new netbook, and come to find out outlook no longer exists in windows 7, anyway, to make a long story short, a total nightmare.

seems when when windows folks are frustrated with their computer, they blame the program they are using, the fates, etc, never do they blame the fact that MS has the keys to their world and wants them to pay for a house they have already paid for....  but when using linux and they lack patience, they blame linux, or in this case, me, the linux geek.

---

### Post by darkod on 2010-06-22
My, you really sound pi**ed... :)

---

### Post by sf-it-services on 2010-06-22
I have had this problem with converting users from windoze for a while now, so now I have started putting linux on computers for children, adults are too fickle

---

### Post by Mark Phelps on 2010-06-22
> **brallan said:**
> .. She was terribly frustrated with change. I myself was amazed how difficult it was for me to deal with windows, something I grew up with. And everyone makes out like its so easy, but I was quite shocked that it was so hard to do things which are very simple in ubuntu. I am  so happy I left windows behind five years ago. 
This may come as a shock to you, but MOST people are frustrated with change. Vista, and then Win7, made a LOT of changes to how things are done now in MS Windows and have generated a LOT of frustration in the MS Windows community as well.

> i am resolving never to do  another install for someone using ms outlook or ms word or internet explorer. 
Not really your fault in this case, since she was asking you to make the change for her,but in my own experience, folks don't like their computing environment to be changed.  Dare say that if MS suddenly decided to release a FREE version of Win7, you most probably would NOT see the regulars in this forum suddenly abandoning Ubuntu to jump to Win7; so why would you expect to see folks accustomed to MS Windows jumping to Ubuntu?

> for example ... nope, it was service pack 3, and even though i believe it was original and non-OEM software, it recognized the harddrive was in another machine and booted into some kind of security measure which asked for the registration code that came with windows. She didn't have it. 
SP3 killed a LOT of XP machines, yours was one of many.  LOTS of folks got stuck in the now infamous reboot loop where the machine would boot, error out, and reboot -- and keep doing this until you turned it off.  MS, of course, distributed an updated update -- but then, since you couldn't boot your machine into Windows, how exactly were you supposed to fix it??

> i eventually got thunderbird working, but she didn't like it. then i got evolution working, and she didn't like it. she just wants her old computer back the way it was ...

I suspect, that what she really wanted was a free CLONE of MS Windows -- which is a guarantee for disappointment.  As I (and others) have tried to tell folks repeatedly, Ubuntu is an ALTERNATIVE to MS Windows, not a CLONE.  Some changes have to be made in how you do things in order to become comfortable with Ubuntu.  If you're not willing to make those changes, you're going to be unhappy.

>  come to find out outlook no longer exists in windows 7, anyway, to make a long story short, a total nightmare.
I guess this will come as a shock as well, but Outlook was NEVER a part of MS Windows.  It comes bundled with the rest of MS Office (or can be purchased by itself if you're so inclined).  But since so many vendors bundle it with new machines, it's easy to see that folks think it "comes with Windows".

> seems when when windows folks are frustrated with their computer, they blame the program they are using, the fates, etc, never do they blame the fact that MS has the keys to their world and wants them to pay for a house they have already paid for.... 
Sorry, but this analogy makes no sense. MS doesn't charge you to use their products, but only to install their products, or to upgrade to newer versions of their products. I use MS Products every day, and don't see any bills from MS for that usage.

>  but when using linux and they lack patience, they blame linux, or in this case, me, the linux geek.
Well, unless you "oversold" Linux as a "miracle cure", they shouldn't be blaming you for anything -- other than giving them a chance to experience something different.  They SHOULD be thanking you, instead ... but then, whenever does that happen?[LIST]
[/LIST]

---

### Post by darkod on 2010-06-22
> I guess this will come as a shock as well, but Outlook was NEVER a part  of MS Windows.  It comes bundled with the rest of MS Office (or can be  purchased by itself if you're so inclined).

I guess he meant to say Outlook Express, which was part of Windows but isn't any more. Isn't there something like Windows Mail replacing it?

Otherwise, yes, MS Office Outlook was never part of Windows, just part of the Office suite.

---

### Post by brallan on 2010-06-22
Mark, thanks for your insights.

> **Mark Phelps said:**
> Sorry, but this analogy makes no sense. MS doesn't charge you to use their products, but only to install their products, or to upgrade to newer versions of their products. I use MS Products every day, and don't see any bills from MS for that usage.

I was just referring to the fact that a perfectly useful paid-for operating system unpleasantly demanded proof that it was paid for when put into a new machine. i was astonished, since I myself didn't write any changes at ALL to the drive, it just simply went belly-up all upon booting in a new machine.

This is the most conversation one of my threads has ever generated. I wonder if it's because the title is provocative, or perhaps because I got emotive.

Anyway, I calmed down now, made peace with the woman, and reconfirmed my own commitment to myself to never do tech support on windows machines... once i am done trying to help her get this one back in shape... her netbook is fine with windows 7 and no ubuntu now, but the laptop which had XP is blue screened of death halfway through the bootup. what's the procedure for recovering windows xp service pack 3 when this happens? I DO NOT have the original XP dvd or CD.

---

### Post by brallan on 2010-06-22
> **darkod said:**
> I guess he meant to say Outlook Express, which was part of Windows but isn't any more. Isn't there something like Windows Mail replacing it?


yes, outlook express. I will look into it.

---

### Post by wilee-nilee on 2010-06-22
> **brallan said:**
> 
I was just referring to the fact that a perfectly useful paid-for operating system unpleasantly demanded proof that it was paid for when put into a new machine.


It was a OEM attached to the original computer am I right. A OEM is a auto activation, if the firmware isn't in another computer you will get this.

If you want to fix the XP you can try a chkdsk/r/f from a command line from the f8 prompt or download this XP slipstream and do it drom a legit install disc.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

