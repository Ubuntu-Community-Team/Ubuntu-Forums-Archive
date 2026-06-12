---
title: "Cant boot to Ubuntu after booting into Windows"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Psycholiquid71 on 2007-09-13
Well I have looked at all the posts on:
/bin/sh: can't access tty; job control turned off

None of the options are working for me. Here is my setup and what is happening:

Dell Optiplex 745
2 SATA HDs
Ubuntu 6.06

I already have Winblows loaded to the second HD. This will boot fine as the second HD and without problems.

The first HD is what I load Ubuntu on and the load goes fine and finishes the install. Once it installs I am able to go into Ubuntu and do everything just fine. I have sound and all the fun things that come with the OS. 

Now that I have Ubuntu installed and working I go back into windows because I still have stuff int here I have to work on until I can move everything over to Ubuntu. IT finds the drive and I am not sure what it is doing but after this I cannot get back into Ubuntu.

My question is this, Can I hide the drive from windows so that it wont mess with it, and if not, what might it be doing that causes:

/bin/sh: can't access tty; job control turned off

only after I go into window. 

Right now I am in windows and have the other drive unplugged so that i don't have to reinstall for the 10th time. 

Thanx for hte help in advance, you guys are the first forum that doesn't treat us noobs like noobs.

---

### Post by flatwombat on 2007-09-13
Just curious, but what happens if you switch the drive order in the BIOS?  Grub should be showing up and giving you the option to boot into either OS, if you had both drives plugged in and installed Grub on the mbr.  I've run dual drives where I had XP entirely on one drive and linux entirely on the second drive.  At that time, I had unplugged my XP drive and installed linux on the other one, creating a second mbr.  Then, plugged back XP and booted the linux drive.  That worked fine, but it was a pain to switch the boot order in the BIOS every time I wanted to change OS's.  To solve it, I added these lines in Grub:

title  Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

That told Grub that there was a second drive to look at for booting and the partition to boot.  From there, the NTFS bootloader took over as usual and booted Windows.

---

### Post by Psycholiquid71 on 2007-09-13
Ive done jsut that, they are two seperate drives also. It seems that grub is not the problem as it will start to load the Ubuntu and then stop after it hits the splash screen and just lock. It wont do this however until I have them both plugged in at the same time and load into windows then try to go bakc into linux. That is when the problem starts.

Basically I am in windows now with the Linux drive unplugged. If I plug it back in and load into windows, then logout and load into Linux the problem will start. 

Its like Windows changes something on the first drive. I also don't have an option to pick which drive it boots form in the bios as Dell uses some hokey bios program that doesn't give that option.

---

### Post by jnorthr on 2007-09-13
Could you please clarify : the first drive has ubuntu and the second drive has windows ? I was under the impression that the windows o/s ALWAYS had to be on the first drive. 

Also can you see which partition has the bootable flag set as that should be the windows partition  cos ubuntu ignores that flag anyway. Is there any possibility of a conflict there ?

---

### Post by dabl on 2007-09-13
> **Psycholiquid71 said:**
> 

 grub is not the problem as it will start to load the Ubuntu and then stop after it hits the splash screen and just lock.



You say "lock", but are you sure?  When it is locked, try Ctrl-Alt-F1 -- if you get a text prompt, then it's not locked, it's just got a wrong video driver setup.  :)

---

### Post by Psycholiquid71 on 2007-09-13
Very sure I hit CTRL-ALT-F1 and sitll nothing, I can even hit CRTL-ALT-End and nothing same for backspace.

---

### Post by Psycholiquid71 on 2007-09-13
> **jnorthr said:**
> Could you please clarify : the first drive has ubuntu and the second drive has windows ? I was under the impression that the windows o/s ALWAYS had to be on the first drive. 

Also can you see which partition has the bootable flag set as that should be the windows partition  cos ubuntu ignores that flag anyway. Is there any possibility of a conflict there ?

The first drive sda has Ubuntu

The second drive sdb has Winblows

sda1 has the boot partition and if flagged by grub.

Not sure about windows having to be the first drive as it is working now(Linux drive unplugged)

Now if I plug it in Log into Linux, it will work. Log out and log into winblows, that will work. Now if I log out of winblows and try to lgo back into Linux I will get the "tty is turned off" error message.

Very weird stuff but I can duplicate it all day long.

---

### Post by Psycholiquid71 on 2007-09-17
Just checking in to see if anyone has any ideas. I would love to tell my boss he can no longer log into my machine because I run Linux, LOL.

---

