---
title: "Can't load Ubuntu or Windows 7 after Wubi install"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by brownish on 2010-11-25
Hi everyone!

I am a brand new Linux user and so far I am really  liking the setup, except I am having a big problem. I installed Ubuntu  10.10 from inside Windows 7 Ultimate using Wubi and after restart, I was  only able to run Ubuntu for one power off/back on cycle. After I turned  it back on, it gave me the option of which OS to boot, and I chose  Linux. When I restarted the next time, it just went to the GRUB rescue  screen and I cannot load either!

I have tried booting from hard  disk and from usb with ubuntu 10.10 on it. Hard disk brings me to the  grub rescue screen. USB gets me to the Ubuntu loading screen. The dots  progress as if it is loading but I've been waiting 30 minutes with no  loading. 

[COLOR=Red][SIZE=2]EDIT: I pressed esc after rebooting (it got stuck again) and here is what it says:
(process:347): GLib-Warning **: getpwuid_r():failed due to unknown user id (0) stdin: error 0

[/SIZE][/COLOR] Any ideas?

Much appreciated!

Andy

---

### Post by wilee-nilee on 2010-11-26
Did you have any grub update/upgrades in the Ubuntu install. Right now we are seeing a few. This can be fixed with from a install W7 DVD or a recovery cd with this command generally.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
```

You might confirm any updates/upgrades before doing this and or post the bootscript in my signature.

---

### Post by brownish on 2010-11-26
Downloading the Windows 7 recovery cd now. I will post results as soon as I can. 

Thanks!

---

### Post by wilee-nilee on 2010-11-26
> **brownish said:**
> Downloading the Windows 7 recovery cd now. I will post results as soon as I can. 

Thanks!

You might consider posting the bootscript first is all or running it for your self just to see if grub is in the MBR.

It will be in the first line of the readout text.

---

### Post by brownish on 2010-11-26
> **wilee-nilee said:**
> You might consider posting the bootscript first is all or running it for your self just to see if grub is in the MBR.

Is there a way I can do this without access to any OS? my CD drive isn't working right now and booting Ubuntu from a usb only gets me to the loading screen.

---

### Post by wilee-nilee on 2010-11-26
> **brownish said:**
> Is there a way I can do this without access to any OS? my CD drive isn't working right now and booting Ubuntu from a usb only gets me to the loading screen.

So you can't even boot the recovery disc correct?

Do you have a thumb drive you can boot linux with? 

There is another option of putting a bootloader called lilo in but you have to in your situation boot from a Ubuntu cd, via a thumb would work.

Lets see who else is on line, calling all lurkers to the rescue here, lots of popcorn for your efforts.:popcorn::popcorn::popcorn:

---

### Post by brownish on 2010-11-26
I have a flash drive with ubuntu loaded on. That is what got me to the loading screen and then nothing. I tried loading the windows recovery onto another flash drive using unetbootin, but when I booted it, it only got me to a weird unetbootin screen. 

How do I mount the windows recovery on a usb?

---

### Post by wilee-nilee on 2010-11-26
> **brownish said:**
> I have a flash drive with ubuntu loaded on. That is what got me to the loading screen and then nothing. I tried loading the windows recovery onto another flash drive using unetbootin, but when I booted it, it only got me to a weird unetbootin screen. 

How do I mount the windows recovery on a usb?

I have never seen anybody do this, but I am able to extract a W7 install from a W7 ISO from Digital River using Ubuntu to a thumb, to a pre-formatted NTFS partition, and just setting the bootflag with gparted boots up to the W7 install. This is just a possibility,  but your not the first person to come on the forum with no real way to boot anything.

So about the cd reader what happens if you just try and boot the recovery cd? People some times have problems that are easily fixed by using a per-session boot like you would boot into the bios. On my computer it is the f12 key. The cd being read first in the bios, seems to not work at times

---

### Post by brownish on 2010-11-26
> **wilee-nilee said:**
> So about the cd reader what happens if you just try and boot the recovery cd? People some times have problems that are easily fixed by using a per-session boot like you would boot into the bios. On my computer it is the f12 key. The cd being read first in the bios, seems to not work at times

I don't think I've ever tried to boot anything with a cd on this pc since my roommate built it a couple years ago. Since then everything has been transferred without use of a cd. For a while now, I have not been able to use the drive to play dvds or cds in windows 7. I'm burning a cd with windows recovery on it now so I'll let you know.

---

### Post by wilee-nilee on 2010-11-26
> **brownish said:**
> I don't think I've ever tried to boot anything with a cd on this pc since my roommate built it a couple years ago. Since then everything has been transferred without use of a cd. For a while now, I have not been able to use the drive to play dvds or cds in windows 7. I'm burning a cd with windows recovery on it now so I'll let you know.


Argh matey if you can get that cd to boot into the recovery console per the instructions and run that command I think you will be fixed. You have a wubi install and have except for not confirming any grub upgrades described what we have been seeing.

Its not talk like a pirate day but it helps to slip it in for me at least other wise I'll ah be keelhauled.

---

### Post by brownish on 2010-11-26
Looks like my problems are yet to be solved. I successfully burned the recovery cd and booted from cd-rom, and then it just goes to:

Boot from CD/DVD:_
_
error: no such device: 1fec1f89-a9a7-4e37-a342-bf7f5c958f17

Is there a way to simply remove ubuntu and grub and whatever else is stopping this? I didn't have anything installed. I'd just prefer to save my windows 7 files before reformatting.

---

### Post by wilee-nilee on 2010-11-26
> **brownish said:**
> Looks like my problems are yet to be solved. I successfully burned the recovery cd and booted from cd-rom, and then it just goes to:

Boot from CD/DVD:_
_
error: no such device: 1fec1f89-a9a7-4e37-a342-bf7f5c958f17

Is there a way to simply remove ubuntu and grub and whatever else is stopping this? I didn't have anything installed. I'd just prefer to save my windows 7 files before reformatting.

Not that I know of without booting into a Ubuntu OS or a live cd

Grub is in the master boot record probably, without the bootscript I can't confirm that but I would wager quite high that it is. And removing it is not all that simple, it needs to be replaced with the MS or lilo bootlader this needs a bootable device.

If you can get a usb cd reader you will be set I think.

The only other thing is that when you burn any ISO you burn it as a image not a data file, so if it is data burn, burn it as a image and try again.

If it was me I would be unplugging the cd/dvd reader and checking it out seeing if the one you burned with could work some how, it is your creativity at this point.

---

### Post by brownish on 2010-11-26
Bummer. I will try booting the usb again. I'll look around the net more as well. Someone knows how to fix this!

I'll update tomorrow morning on progress.

---

### Post by madjr on 2010-11-26
> **brownish said:**
> Looks like my problems are yet to be solved. I successfully burned the recovery cd and booted from cd-rom, and then it just goes to:

Boot from CD/DVD:_
_
error: no such device: 1fec1f89-a9a7-4e37-a342-bf7f5c958f17

Is there a way to simply remove ubuntu and grub and whatever else is stopping this? I didn't have anything installed. I'd just prefer to save my windows 7 files before reformatting.

with the ubuntu live-cd you can browse and save your files in the windows partition

burn as image.

or install live image to usb stick with unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wilee-nilee on 2010-11-26
> **madjr said:**
> with the ubuntu live-cd you can browse and save your files in the windows partition

burn as image.

Apparently no booting available, and this is just a simple grub update in wubi, I think that just needs the MS bootloader put in the MBR, no recovery needed here just a bootable W7 install or recovery for one command or Ubuntu for lilo. This is the standard procedure that woks in this scenario.

This has been going on for a couple of days now.

---

### Post by brownish on 2010-11-26
> **wilee-nilee said:**
> Apparently no booting available, and this is just a simple grub update in wubi, I think that just needs the MS bootloader put in the MBR, no recovery needed here just a bootable W7 install or recovery for one command or Ubuntu for lilo. This is the standard procedure that woks in this scenario.

I was able to boot up SystemRescueCD and it was able to detect my hard disk and everything. I didn't want to mess around with it too much because I wasn't sure what everything meant. Is SystemRescueCD able to fix my problem? 

Also, what is the best program to create a Windows 7 repair bootable usb? I tried once, but it didn't work. Unetbootin doesn't have the option to create one.

---

### Post by brownish on 2010-11-26
> **brownish said:**
> I was able to boot up SystemRescueCD and it was able to detect my hard disk and everything. I didn't want to mess around with it too much because I wasn't sure what everything meant. Is SystemRescueCD able to fix my problem? 

Also, what is the best program to create a Windows 7 repair bootable usb? I tried once, but it didn't work. Unetbootin doesn't have the option to create one.

[COLOR=Red]Edit: I was able to get the windows 7 repair disc to boot via usb. I used [this page]("http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html") to fix the mbr via command prompt. I was able to choose windows 7 or ubuntu to load. I loaded windows. Got me to the login screen of windows 7. I logged in, and got a back screen with cursor visible. I was then able to ctrl-alt-delete back to the login screen, but then it just brings me back to a black screen. 


Trying a couple other options now. At least I've got something.I just need to get rid of ubuntu and reinstall via usb now, any thoughts?[/COLOR]

---

### Post by brownish on 2010-11-26
I was finally able to fix it!

I was able to uninstall ubuntu using the terminal, then I rebooted and loaded windows. It still gave me the option to load ubuntu, but windows loaded all the way. I then reformatted the partition with ubuntu on it (i'm guessing this created the problem, not installing ubuntu on the same partition as windows). I think everything is good!

Thanks for you help!

---

