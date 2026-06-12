---
title: "help i need to start the live cd and windows says the wubi.exe file is corrupt"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by jakeroo123 on 2008-08-15
ok the wubi.exe is not corrupt and i ned it to start the live cd because it won't let me unless i click help me boot from cd and that wont work w/out the wubi file can anybody help me please answer ASAP!

---

### Post by doas777 on 2008-08-15
have you tried re-burning the disk or redownloading? I'd prolly do so, and in that order.

---

### Post by dje on 2008-08-15
reboot with the cd in your cd drive. when the bios comes up press the key that gets you into the setup (could be f2, f12 or DEL) and move the cd drive to the top of the boot order. then reboot and when the ubuntu menu comes up choose start or install ubuntu (or option with similar wording)

dje

---

### Post by jakeroo123 on 2008-08-15
I tried that it didn't work.

---

### Post by jakeroo123 on 2008-08-15
well my computer doesn't have a cd burner i used my sister's caomputer and she's using it

---

### Post by jakeroo123 on 2008-08-15
Hey i need answers!

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> well my computer doesn't have a cd burner i used my sister's caomputer and she's using it

OK, just to clarify, you are trying to boot into ubuntu off the live CD, on your sisters windows PC? just trying to get a clear view of your problem.

if you can't boot into the live CD, then it is probably unlikely that a wubi install would fair much better on your hardware, but that depends. what specifically did not work with dje's suggestion?

---

### Post by jakeroo123 on 2008-08-15
no my sisters computer has a cd burner and mine doesn't

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> no my sisters computer has a cd burner and mine doesn't

ok so you burned the live cd you are using off your sisters pc. do you have access to that PC right now? you could use it to reburn the CD.

also what didn't work about booting into the live CD? try to be as specific as possible.

---

### Post by jakeroo123 on 2008-08-15
no one of them (two of my sisters share that computer) watching videos on youtube.

it wont let me boot into the live cd because windows says the wubi file is corrupt and i need access to that to boot into the cd

---

### Post by doas777 on 2008-08-15
so what is wrong when booting into the live cd

---

### Post by lisati on 2008-08-15
> **jakeroo123 said:**
> no one of them (two of my sisters share that computer) watching videos on youtube.

it wont let me boot into the live cd because windows says the wubi file is corrupt and i need access to that to boot into the cd

So, if I understand you correctly, the LiveCD wouldn't work on YOUR computer, and you want access to your SISTER's compute to download/burn a new one.

---

### Post by jakeroo123 on 2008-08-15
ok this is a reply to lisati and doas777

no it says that the wubi file is corrupt and i need to click "help me boot from cd" in the ubuntu menu to get the livecd to work and i need the wubi file to work for that.

---

### Post by doas777 on 2008-08-15
ok. wubi is for installing ubuntu as an application in windows. 
if you are booting into the live CD you should not need wubi. it is only for running inside of windows.

what dje and I are suggesting is that you put the CD in. then shut your PC down. then power it back on, and configure your bios to boot from a CD (the ubuntu live CD).
then restart your PC and when it says "Press any key to boot from CD...", press any key. your PC should boot ubuntu.

---

### Post by jakeroo123 on 2008-08-15
ok that doesn't work either i've tried

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> ok that doesn't work either i've tried
what dosen't work about it?

---

### Post by jakeroo123 on 2008-08-15
as in it's not detecting the cd to boot from

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> as in it's not detecting the cd to boot from

unfourtunatly that comes back to the aforementioned bad burn. I don't think theres much you can do until you are able to either reburn or redownload/burn a copy. 

sorry i can't be of more help,
franklin

---

### Post by lisati on 2008-08-15
(please ignore this post)

---

### Post by coolsmileys on 2008-08-15
There's an Install CD and LiveCD right? if you really want to try or run Ubuntu, you might want to consider installing VMWare on your PC. If your PC is fast enough to accomodate another virtual machine then you could run new OS's there without having to keep on booting/rebooting your machine, etc.

---

### Post by dje on 2008-08-15
jakeroo123: have a read through this [excellent guide]("http://www.psychocats.net/ubuntu/installing"), that should help. And just to clarify which computer are you trying to install ubuntu on, yours or your sisters?

dje

---

### Post by doas777 on 2008-08-15
> **coolsmileys said:**
> There's an Install CD and LiveCD right? if you really want to try or run Ubuntu, you might want to consider installing VMWare on your PC. If your PC is fast enough to accomodate another virtual machine then you could run new OS's there without having to keep on booting/rebooting your machine, etc.

that is a good point, if the problem is supportable hardware. a VM might just do the trick. my only concern is that if the CD won;t boot, it is probably corrupt. the bonus however is that you could mount the ISO to the VM without having to burn it. 

good luck

---

### Post by jakeroo123 on 2008-08-15
> **lisati said:**
> (please ignore this post)
i'll try...

---

### Post by jakeroo123 on 2008-08-15
> **dje said:**
> jakeroo123: have a read through this [excellent guide]("http://www.psychocats.net/ubuntu/installing"), that should help. And just to clarify which computer are you trying to install ubuntu on, yours or your sisters?

dje

ok imy sisters' is already running ubuntu and mine is a dell optiplexgx150 and i'm trying to reinstall ubuntu

---

### Post by dje on 2008-08-15
so you are trying to reinstall ubuntu on your computer which does **not** have a cd drive, correct?

dje

---

### Post by jakeroo123 on 2008-08-15
it has a drive that doesn't burn cds.

---

### Post by dje on 2008-08-15
right ok, what happens when you try to do what i illustrated in my first post (boot from the cd)

dje

---

### Post by jakeroo123 on 2008-08-15
_re: daos777_

no my computer won't boot from a cd unles it's specific

---

### Post by dje on 2008-08-15
have you tried to follow the instructions from [here]("http://www.psychocats.net/ubuntu/installing") to boot the live cd

dje

---

### Post by jakeroo123 on 2008-08-15
ok it won't let me use the menu either...

---

### Post by dje on 2008-08-15
> **jakeroo123 said:**
> ok it won't let me use the menu either...

which menu?

---

### Post by jakeroo123 on 2008-08-15
ok that link is for a dual install and i dont want that

---

### Post by jakeroo123 on 2008-08-15
the umenu.exe in the cd

---

### Post by dje on 2008-08-15
> **jakeroo123 said:**
> ok that link is for a dual install and i dont want that

yes but the beginning explains well how to boot from the cd. just follow the beginning of the guide. who originally installed ubuntu on your computer?

dje

---

### Post by jakeroo123 on 2008-08-15
well me

---

### Post by dje on 2008-08-15
so is it the same cd that you used before? can you not repeat the procedure that you did the first time you installed ubuntu? how did you install ubuntu the first time you did it?

dje

---

### Post by jakeroo123 on 2008-08-15
well i installed it twice before and i opened the umenu.exe file but now it says that the file is corrupt.

---

### Post by dje on 2008-08-15
how did you open a windows executable if you don't dual boot and have windows?

dje

---

### Post by jakeroo123 on 2008-08-15
as in i want to install ubuntu as the only operating system on my computer and right now i only have windows.

---

### Post by thehobnob on 2008-08-15
Are you using write-once/CD-Rs or re-writeable/CD-RWs? If the latter I'd recommend burning a to a CD-R, at the slowest possible speed to eliminate errors. 

Does the "test CD for defects" option produce an error?

If it still doesn't work then it's probably your CD image that is corrupt and you'll have to redownload it. Remember to check its md5 hash once you've downloaded it to make sure it isn't corrupt.

EDIT: If you're gonna have Ubuntu as your sole OS, wubi is NOT NEEDED.
Boot the PC **with the CD in the drive** or **in Windows, insert the CD and restart the computer. Ignore the autorun menu that may pop up.**

---

### Post by jakeroo123 on 2008-08-15
and for the first two times i installed ubuntu i installed inside windows

---

### Post by dje on 2008-08-15
the umenu.exe file is for installing ubuntu in wubi which will keep windows, if you only want to have ubuntu you need to boot from the cd using the instructions in the guide i posted twice before

---

### Post by jakeroo123 on 2008-08-15
i use CD-Rs i only have one CD-RW and i do'nt use it often and there isn't enogh space left for ubuntu.
no, windows ony says the installer is corrupt on a cd the one on my computer works fine but it won't work for the live cd.

---

### Post by jakeroo123 on 2008-08-15
yes wat i'm trying to do is boot from the cd it isnt letting me

---

### Post by dje on 2008-08-15
have you followed the instructions in the guide (to change the boot order in the bios) and what do you mean it doesnt work. what happens?

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> yes wat i'm trying to do is boot from the cd it isnt letting me
now you are focused on the right question.

first go into your BIOS, and check your boot order. write it down and post it for us please.

---

### Post by jakeroo123 on 2008-08-15
i mean i can only boot from cds if the cd is a specific cd and what i'm trying to do is get it to leat me boot from cd

---

### Post by jakeroo123 on 2008-08-15
ok i've gone into the boot menu and chosen cd device and it wont work.

---

### Post by hotrod6657 on 2008-08-15
you should be able to boot from Cd, but it will require changing things around in the BIOS.  When you boot your computer one of the very first screens you should see should tell you what to press to enter the bios.  Then one of the options should be something about startup, there it should let you change the boot order and put your CD drive at the top of the list so it boots off the Cd.

When you try and boot with the CD in do you even get the screen with Ubuntu on it and a list of options, like install, check CD for defects, ect?

---

### Post by dje on 2008-08-15
i dont understand what you mean by a specific cd, insert the ubuntu cd in the drive and reboot, enter the bios and change the boot order to the cd drive is first then reboot again. the live cd will boot. **how does it "not work" you must tell us what happens instead**

---

### Post by jakeroo123 on 2008-08-15
no it doesn't even know that the cd's there

---

### Post by jakeroo123 on 2008-08-15
it does not detect the cd unless windows tells it to.

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> ok i've gone into the boot menu and chosen cd device and it wont work.

ok. thats what i wanted to know. 

if the CD dosn't provide you an option to boot, then the boot sector is probably corrupt. when you get access to the other pc, burn a new copy, and if your burning software has a "verify disk" option, use it.

---

### Post by dje on 2008-08-15
right the cd is in the drive, the cd drive is first in the boot order and you reboot. **step by step what happens** and what do you mean by "a specific cd"

---

### Post by hotrod6657 on 2008-08-15
are you sure that you changed the boot order?  The list of divices it gives you has to be changed, you can't just hover the selector over CD.  It should give you the controls at the bottom of the bios page on how to move an item up or down on the list, just use them to move CD to the top.

---

### Post by thehobnob on 2008-08-15
> **jakeroo123 said:**
> it does not detect the cd unless windows tells it to.

This has nothing to do with Windows. It is your computer's BIOS, and likely a defective CD

---

### Post by doas777 on 2008-08-15
> **thehobnob said:**
> This has nothing to do with Windows. It is your computer's BIOS, and likely a defective CD

exactly.

---

### Post by hotrod6657 on 2008-08-15
Windows won't be keeping it from booting, it's an option in the bios which isn't part of your operating system

If the boot order is correct then i agree, bad CD burn.  Try burning another one.

---

### Post by jakeroo123 on 2008-08-15
well, what  i mean is it won't detect the cd unless something else tells it to (the **umenu.exe** file speciffically)

---

### Post by jakeroo123 on 2008-08-15
the thing is there is only one computer in my house wiht a cd burner an it belongs to two of my sisters and one of them is using it.

---

### Post by jakeroo123 on 2008-08-15
i guess i could burn a cd from that one with the text installer

---

### Post by dje on 2008-08-15
[COLOR="Red"][B]forget umenu.exe it is irrelevant!!
please tell us what happens instead of the cd booting and what a "specific cd" is[/B][/COLOR]

---

### Post by jakeroo123 on 2008-08-15
if she lets me

---

### Post by hotrod6657 on 2008-08-15
If it is a bad burn though and your computer won't let it boot from the CD there's not much else you can do.  Do you have any other bootable Cds that you can try out (like a windows XP disk) to see if you BIOS will let other CD's boot?

---

### Post by jakeroo123 on 2008-08-15
brb

---

### Post by jakeroo123 on 2008-08-15
no

---

### Post by doas777 on 2008-08-15
> **jakeroo123 said:**
> well, what  i mean is it won't detect the cd unless something else tells it to (the **umenu.exe** file speciffically)

booting from a cd comes long before you are able to run any excutables. it happens when your pc screen is still text only black and white. if you can execute anything, then you have already booted.

I'm at a loss to give you any further advice, except to burn a new copy of the disk. if your bios is not good at booting off a cdr, then there really isn;t any troubleshooting to be done anyway, except mabey updating the bios itself. if it's just the disk though, you will be able to boot and install off a clean burn of it.

good luck

---

### Post by hotrod6657 on 2008-08-15
The .exe file is a Windows excecutable file, I don't know for sure but i don't think that's what controls wether it will boot into that CD.  I'm sure it effects how the CD performs in Windows but that should be indepentant of the rest of your computer.

---

### Post by dje on 2008-08-15
are you sure that the cd drive is set to boot first?

---

### Post by jakeroo123 on 2008-08-15
what i dont get is how to update the bios

---

### Post by dje on 2008-08-15
when you turn the computer on it will say which keys you need to press, press the one it tells you to. you have not been doing what we ask, we cannot help you if you dont follow instructions, read the guide i posted it tells you common key combinations if you cant find yours

---

### Post by hotrod6657 on 2008-08-15
lets not worry about updating the bios right yet.  Are you positive that the CD is listed first in the BIOS boot order?  What key do you have to press to get in to the bios?  and walk us through what you do when you're in there.

---

### Post by thehobnob on 2008-08-15
> **doas777 said:**
> booting from a cd comes long before you are able to run any excutables. it happens when your pc screen is still text only black and white. if you can execute anything, then you have already booted.

I'm at a loss to give you any further advice, except to burn a new copy of the disk. if your bios is not good at booting off a cdr, then there really isn;t any troubleshooting to be done anyway, except mabey updating the bios itself. if it's just the disk though, you will be able to boot and install off a clean burn of it.

Couldn't have put it better myself.
exe is a format specific to Windows. Because booting the CD doesn't involve windows at all, it is not needed.

---

### Post by jakeroo123 on 2008-08-15
it is'nt but i tell it to boot from the cd on the boot menu (when it lists booting options and it does the one you pick first ignoring the default settings

---

### Post by dje on 2008-08-15
> **jakeroo123 said:**
> it is'nt but i tell it to boot from the cd on the boot menu (when it lists booting options and it does the one you pick first ignoring the default settings

[COLOR="Red"]**[SIZE="4"]ok so what happens when you select the cd, you have not told us what happens! are there any errors?[/SIZE]**[/COLOR]

sorry for the large font but i and others have asked this many times and you have not answered!

---

### Post by hotrod6657 on 2008-08-15
does your computer just keep on booting in to your OS when you tell it to boot the CD?

---

### Post by thehobnob on 2008-08-15
If so, then its definitely the CD at fault

---

### Post by jakeroo123 on 2008-08-15
ok first when the screen comes up i press F12 to bring up a menu like this:

> 1.Normal
2.Hard disk
3.CD

and i choose cd and it says

> strike F1 to retry boot, press F2 for the setup utility

and if i press F1 it does it again it ony stops if i press F2

then it shows a setup utiliy, but thet does me no good.

when i exit that it does the F1/F2 message again.

---

### Post by hotrod6657 on 2008-08-15
okay, thank you for that.  It's sounding more and more like a bad CD.  Hate to say it but you might have to bug your sisters or wait until their done to get a new one burned.  Any way you could get them to let you burn it in the background while they use the computer?

---

### Post by jakeroo123 on 2008-08-15
was this helpful to any of you? i hope it was.

---

### Post by dje on 2008-08-15
yes the cd is most likely corrupt and you are going to need to burn a new one

---

### Post by jakeroo123 on 2008-08-15
hmm... well i'll ask her *again*

---

### Post by thehobnob on 2008-08-15
Burn at a **slow** speed

---

### Post by hotrod6657 on 2008-08-15
the only other suggestion i could give it to change the boot order the other way we mentions, by entering the bios and really changing it (the way you're using is a temorary change) and seeing if that helps any, but i doubt it would.

btw, that was very helpful, those sort of details should always be included when you're having a problme :)  
Thanks!

---

### Post by jakeroo123 on 2008-08-15
sshe says when she's done doing what she's doing... whatever that is.

---

### Post by jakeroo123 on 2008-08-15
you'r welcome,hotrod6657

---

### Post by dje on 2008-08-15
well we cannot help you until then... :D
please remember in future that we cannot provide the best help unless you provide details when we ask you, it's for your benefit ;)

dje

---

### Post by hotrod6657 on 2008-08-15
haha, sorry you have to wait lol.  The forum will be here if you have any more trouble after the new burn.

Forgive me, blessed by being an only child ;)

---

### Post by jakeroo123 on 2008-08-15
Ok

---

### Post by thehobnob on 2008-08-15
help will come much more quickly if you include info like that next time something crops up. remember, we aren't sat at the computer with you!

---

### Post by jakeroo123 on 2008-08-15
geuess what i have four sisters... and one of them skipped two grades and is in my class. i get along with her ok thogh but it's the seven-year-old thats not letting me use her computer... until now that  is

---

### Post by jakeroo123 on 2008-08-15
i know i'm sorry i didn't give more info i was kinda in a hurry

---

### Post by jakeroo123 on 2008-08-15
i'll be offline for awhile to burn the cd

---

### Post by jakeroo123 on 2008-08-15
oh yes.. all of you, thanks for trying to help.
:-)

---

### Post by hotrod6657 on 2008-08-15
no problem, it's why we're here.  Good luck with the new burn, we'll be here if anything goes wrong.

I can't imagine having that many sisters.  I've gotten way too used to being the only child lol.

hotrod

---

