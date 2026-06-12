---
title: "I have no idea what to do now!"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by nickyspaghetti on 2008-01-09
Ok my old PC died so I bought a new one and decided to lose windows altogether. 
Ran the live CD no problem - installation no problem.
Now I boot up and after selecting how to boot up (regular/recovery/mem test) it just goes black.
at the bottom it says something about kernel(too fast to read it)
What is the first step - I want to get this system running as soon as possible but I have no idea where to start as I have no windows and limited access to a computer.
I downloaded the 64 version and I'm using an intel core duo 2.4 ghz processor with 2 gb ram. what more information do you need?

---

### Post by AlanR8 on 2008-01-09
I'd try downloading the 32 bit version and give that a go

---

### Post by PmDematagoda on 2008-01-09
Did you try booting Ubuntu in Recovery Mode?

---

### Post by Gina on 2008-01-09
Att first I thought of screen resolution set too high but if it's a new PC I imagine the monitor will do 1280x1024.  Otherwise, see [this thread]("http://ubuntuforums.org/showthread.php?t=662592") post no.2

---

### Post by nickyspaghetti on 2008-01-10
Ok, so I have tried the 32 bit version and it starts slightly different. This time instead of showing the thing about kernel, it shows the ubuntu loading screen with the line(that should move) It does nothing. just frozen at this screen.
I tried doing the recovery mode but it doesn't work. It gives out loads of script and then just stops. you can then type underneath all the script but I still have to reboot get anywhere freom there.

I don't understand why both the live discs run fine but the real installation won't run at all. It freezes at the exact same point in the boot, just one is with a black screen and the other isn't.

I don't think it is the resolution. This monitor has worked using gutsy on my past pc with no problem - even if it was the problem,  how do I write in the terminal if I can't get it to boot?
Any ideas?

---

### Post by PmDematagoda on 2008-01-10
Did you try installing a previous version of Ubuntu such as Ubuntu 6.06?

---

### Post by nickyspaghetti on 2008-01-10
I haven't tried that yet. I wanted the newest version really. I'm not sure what the problem could be as there is no information shown at all.
I really don't want to run windows if I can help it. I was just getting used to ubuntu before I got the new PC

---

### Post by PmDematagoda on 2008-01-10
Well, you could try Ubuntu 8.04 if you want, but Ubuntu 8.04 is too unstable for normal day-to-day work so if you face any problems on it, then you will have to accept them as being part of an OS in development. You may download the Hardy ISO image from [here]("http://cdimage.ubuntu.com/releases/hardy/alpha-2/").

---

### Post by nickyspaghetti on 2008-01-10
Do you think that the problems I am having booting could just be a problem with this version - I don't especially want to download another version and burn it if it will be unlikely to work becaus of somthing else - I have already got a friend to download and burn 2 copies so far(I think he is already a bit tired of trying to fix my problems!)
Its just a bit frustrating that everything went very smooth installing on my old pc(is that because ubuntu is more likely to be compatible with older hardware?) and this there is no clue (for me) as to what is the problem.

---

### Post by PmDematagoda on 2008-01-10
From the error message you are getting, your problem may be because the current kernel may be incompatible with your hardware, we can find this out for certain if you try and use a previous or newer Ubuntu version that runs on a different kernel version.

---

### Post by nickyspaghetti on 2008-01-10
i see. Ok I will try to get another version then.
Sorry, I am completely ignorant about the terms used in computing, so when I get an error I never know what it is!

---

### Post by jeffus_il on 2008-01-10
> **PmDematagoda said:**
> From the error message you are getting, your problem may be because the current kernel may be incompatible with your hardware, we can find this out for certain if you try and use a previous or newer Ubuntu version that runs on a different kernel version.

I wouldn't chase after versions, the first one you chose will work, the fact that the livecd booted and installed means that the hardware is compatible. Stick with your version and try to find the problem, can you get to the grub boot menu by hitting ESC when it starts to boot?

---

### Post by nickyspaghetti on 2008-01-10
Yes, I can. I get three options. Regular, recovery and memory test.
Memory test does something but I don't know what it is doing. The other two don't work.

---

### Post by jeffus_il on 2008-01-10
> **nickyspaghetti said:**
> Yes, I can. I get three options. Regular, recovery and memory test.
Memory test does something but I don't know what it is doing. The other two don't work.
Hopefully the memory test shows success and doesn't give lots of lines that look like errors.
Can you give any other information as to what output you get before the screen goes black?

---

### Post by zero-9376 on 2008-01-10
is the computer rebooting or just sitting there with a black screen? 
is there any hard disk activity?

---

### Post by nickyspaghetti on 2008-01-10
After grub with the 64 edition it says two lines about kernel - it doesn't look like an error message though. It's too fast for me to figure out what it is. Then I get a black screen. On my monitor there is an led that starts flashing as though the screensaver is on or somthing(maybe there is no signal to the monitor?
With the x86(?) version it just shows ubuntu on the screen like it should be loading, but the bar doesn't appear(just a line 1 pixel wide) as though it is the first frame of the animation.
There is nothing shown after the grub menu(i think)
The memory test sppeared to be doing something  - a blue screen with percentage bars and things - i'm not sure what any of them are but the process seemed to be ok.

---

### Post by nickyspaghetti on 2008-01-10
There is no activity at all just the black screen with no reboot.

---

### Post by jeffus_il on 2008-01-10
Try Ctrl-Alt-F1 when you have a black screen and let us know what happens.

---

### Post by nickyspaghetti on 2008-01-10
Ok the ubuntu loading screen disappears and a message come up - something like - 

starting up
Loading, please wait

(This appears just before the ubuntu screen too, I just noticed)

Nothing happens, you can type underneath this message.

---

### Post by jeffus_il on 2008-01-10
OK when you're in the grub boot menu, hit e to edit the menu line, add the word nosplash at the end, hit return, and then b to boot, you should see more text.

---

### Post by jeffus_il on 2008-01-10
Another step you can take:

> **Temporary disable framebuffer in GRUB boot menu**

  Making this change will have no impact on your installed system and is to be considered safe. If you reboot your system this change will disappear. It is temporary. 
 Start your computer normally and after a few seconds you will see the GRUB boot loader menu. 
 [LIST]
[*] With the use of the arrow keys, highlight the title of your choice you want to edit (the first Ubuntu entry should be ok) and press "e" to go to the entry editor interface. You will now see the boot entries for the title you selected. 
[*] Highlight, again with the use of the arrow keys, the line that say "kernel" and press "e" to edit that line. 
[*] Add, without the quotes " vga=normal" and press the enter key to go out of edit mode. 
[*] Press the "b" key to boot your system.  
[/LIST] Note: To cancel your changes press the Escape key until the main menu appear. 
  

---

### Post by nickyspaghetti on 2008-01-10
ok, I went into the edit and tried doing nosplash.
still the same text appears.
I tried vga=normal and also the same.
no text appears and it doesn't boot either

---

### Post by Dreamlocked on 2008-01-10
When I installed Xubuntu 7.10, I had a black screen during boot.
I reinstalled several times, always trying to figure out what the problem was.

Turns out that I just had to wait, because the boot splash wasn't loading and fsdisk was scanning my fat32 windows partition.

Bottomline is : Did you wait long enough on your first installs (both 32 and 64bit) or did you shut down after 5 min?

---

### Post by nickyspaghetti on 2008-01-10
how long are we talking?
Is this just for the first boot?
I will try to leave it for a few hours as I have to go to work now.
I will check in again later to let you know if it did anything

---

### Post by jeffus_il on 2008-01-10
Fine.

---

### Post by Dreamlocked on 2008-01-10
> **nickyspaghetti said:**
> how long are we talking?
Is this just for the first boot?
I will try to leave it for a few hours as I have to go to work now.
I will check in again later to let you know if it did anything

If you have a FAT32 parition, it might be for every boot (you can edit fstab to prevent that, but let's worry about that later).
In my case, I had to wait 10-20 min. I can't imagine needing to wait "hours"...

---

### Post by nickyspaghetti on 2008-01-10
ok, I have an update. After about 10 mins it says this

Busybox v1.1.3 (Debian 1:1.1.3 -5ubuntu7 Built in shell (ash)
enter help for a list of built in commands
(initramfs)

AFter this I tried ctrl alt f1 and it said this

check root =bootarg cat /proc/cmdline
or missing modules,devices: cat/proc/modules ls/dev

ALERT! /dev/hda1 does not exist
dropping to a shell

Ok this seems more like an error message but I don't know if it is just because i pressed the wrong thing.


What is busybox and why does it open after the ubuntu loading screen?
I'm going to work now so I will check back later

---

### Post by nickyspaghetti on 2008-01-10
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123)
[http://www.debianhelp.org/node/6610](http://www.debianhelp.org/node/6610)

I googled the error message and came up with these sites
Could these sites be talking about a similar problem?
If so is there an easy way to solve it?

---

### Post by zero-9376 on 2008-01-10
i used to get an error like this if my parititon uuids didnt match up.
busybox is a very basic set of utilities that will let you do stuff to your system.
have you tried checking your install cds for defects? you can do this from the boot menu for the livecds

when you eventually get to a terminal maybe post the output of the commands 
ls /dev | grep hd
ls /dev | grep sd
these are checking if what disks/partitions are recognised.

---

### Post by nickyspaghetti on 2008-01-10
does this have to be done running from the installation or can it be done from the live cd - at the moment I have only the live cd to access everything(I have to reboot with live cd every time I want to check the advice on here!

---

### Post by nickyspaghetti on 2008-01-10
Sorry - what are uuid's? I am fairly ignorant of these terms as I am new at this!

---

### Post by nickyspaghetti on 2008-01-10
Tested the cd and there were no problems.
Any other approaches that are worth trying?

---

### Post by Gina on 2008-01-10
**uuids** are the identification numbers for the partitions.  Trouble can occur if you delete or reformat  a partition outside the current HD installation as the bootup checks for each partition by **uuid** and the boot fails if the right ones cannot be found (it assumes a disk error).  I have run foul of this when installing new versions on a PC with other installed versions.  The old versions complain because a partition has been reformatted when installing the new system.  The answer is to edit **fstab** to remove the wrong entry.

This I agree, is rather technical for newbies or less experienced Linux users.  However, at least the new version should work OK.  There must be a simpler way round this problem...  I'll have to investigate.

The above doesn't help your problem I know but hope it helps to explain what **uuids** are.

---

### Post by nickyspaghetti on 2008-01-10
Ok, I'm sure I can do that if I knew what I was looking for, but I don't think it can be this problem as the whole computer was untouched before I put the ubuntu disc in. Everything was new. Or could there still be a problem even with new hardware?

---

### Post by nickyspaghetti on 2008-01-10
Please correct me if I am wrong on this
Just been looking around the place and found that hda is a hard drive on an ide cable.
The error message said it couldn't find hda1.
I have a sata disc so why is it looking for an ide disc? 
could this be the problem?

---

### Post by Gordon_Bombay on 2008-01-10
time for a dumb post by a newbie.

Im just giving my opinion dont grill me,

did you remove the disk upon reboot?, lol thats what I would do.

---

### Post by nickyspaghetti on 2008-01-12
Yeah. It's definately the installation.
I'm afraid I'm going to have to go back to windows now as there don't seem to be any solutions yet. 
Does anybody think that the new version could work?
Or is it likely to be a more general problem that will occur with all copies of ubuntu

---

### Post by zero-9376 on 2008-01-12
you have come to the same possible conclusion i did earlier that for some unknown reaon your system thinks your disk is hda during install and now recognises the disk as a sata drive sda.
this is why i asked you to do this:

when you eventually get to a terminal maybe post the output of the commands
ls /dev | grep hd
ls /dev | grep sd
these are checking if what disks/partitions are recognised.

sorry about not getting back to you earlier but as i mentioned you should do this from the installed system

alternatively you could simply try changing the grub option during the boot, this will not be permanent but if it works i can tell you how to make it so

when you boot press esc to see the grub menu, highlight recovery mode entry and press e to edit, highlight the kernel line and press e again to edit that line
change root=UUID=whateverrandomsuffishere to root=/dev/sda1 press enter to save the changes then b to boot

edit: the reason to use the recovery mode is that if this works fstab (the file that tells linux how to mount your partitions after boot) will still have hda references in it although this may not be a problem is the uuids are correct it doesn't seem like uuids are working for you so i thought better to run in recovery mode and see if it works, if it does you should get a root@yourcomputersname prompt

---

