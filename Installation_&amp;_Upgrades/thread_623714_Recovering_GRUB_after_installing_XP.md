---
title: "Recovering GRUB after installing XP"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Westy87 on 2007-11-26
Hey, I've seen a few people with the same problem as mine but not 100% the same and being totally new to Linux and ubuntu I thought I would ask for personal help, hope you all dont mind.

So here is the situation.  I did a complete drive wipe the other day when I bought microsoft vista.  However I also got the gutsy livecd off a mate and thought it would be fun to run tripple boot of vista xp and gutsy.

So I partitioned my 160gb sata drive into 100gb NTSF, 30gb NTSF, 28gb ext and 2gb swap.  (in that order according to partition editor on the livecd)

I then installed vista on the 100gb partition, and straight after installed ubuntu on the 28gb partition and all was working well.  Then I installed XP on the 30gb drive.

I restarted my PC and now do not have the option to boot into either ubuntu or vista.  So firstly I would like to know how to restore my grub menu, and then either to edit grub so that is shows both xp and vista, or to just leave it how it was and have it load the vista bootloader program, in which case I will then have to somehow edit vistas bootloader to include XP.

Reformatting and reinstalling is not an option at this moment in time.

Thanks a lot :)

---

### Post by Steve1961 on 2007-11-26
Use the vista cd to fix the boot problem and then use easybcd to manage the boot process through vista's bootloader. Alternatively restore grub to the mbr:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Westy87 on 2007-11-26
If I use the vista cd will I be able to gain access to ubuntu?

I think I would prefer to have grub load 1st then to have to option to load vista or xp to grub.  My mate installed xp then vista then ubuntu and he ends up with grub loading and if he wants windows then he selects longhorne in the other OS's section of grub, which brings him the vista bootloader which has the option to load xp.  So to load xp you have to go through 2 processes.  So if possible I would rather GRUB have both xp and vista display on the 1st list of choices if that is possible?

---

### Post by Steve1961 on 2007-11-26
> If I use the vista cd will I be able to gain access to ubuntu?

yes once you install easybcd you can add it to the menu.

If you prefer grub to do the work then follow the link to reinstall it to the mbr from the live cd.

---

### Post by Westy87 on 2007-11-26
Hmm which do you recommend, reinstalling grub or using easybcd through vista after using vista fix disc?

---

### Post by Steve1961 on 2007-11-26
It's personal preference, but I use easyBCD as it seems to work very well

---

### Post by Westy87 on 2007-11-26
Hey thanks for the help so far.  I decided to try the vista method first, so doing a quick startup repair then using easybcd I was able to make the vista bootloader appear on startup.  I then added the windows xp boot option to its menu and one of ubuntu (through the linux tab)

The windows xp option works fine but I couldnt get ubuntu to work.  My numbering is vista-0 (C drive), xp-1 (D drive), ubuntu-2 for my partitions.

So I thought I would give the ubuntu live cd a go which worked to install the grub menu at startup again, which still had the menu to load into vista, which then took me to the vista one where i then had the option to get into xp thanks to easybcd.  However I still want to be able to access all boot options from just one bootloader.  I tried adding xp to the grub menu.lst by copying and pasting the entry for vista and changing the name to XP and the root to (hd0, 1) instead of (hd0,0).  I tried with and without a chain loader number and no difference.

So now my question is:

Do you know what settings I need to be able to boot XP from grub, and if I cant then how to disable grub again so that the vista bootloader is default, in which case I will have to try and figure out how to get the option for ubuntu to work correctly on the bootloader using easybcd again.

Thanks, Daniel.

---

### Post by Steve1961 on 2007-11-26
The problem you have when trying to create separate entries for vista and xp in grub is that only the vista bootloader exists in the mbr, so you always have to go through a two stage process AFAIK.  What I did to get easyBCD working with all my OSs (see signature) was to install grub to the root partition of Ubuntu.  So with the live cd you would just do something like:

sudo grub
root (0,1) - this is just an example, it should be grub notation for the Ubuntu root partition, whatever that is.

Then just type setup (0,1) - again the root partition.

You can get the vista bootloader back again with the vista CD.

---

### Post by Westy87 on 2007-11-26
Ah ok I see thanks.  Well, if its going to be a 2 stage process anyway then I think I'll just stick with how it is now with grub then vista/xp.  But yes I think I know what you mean by how to install grub to its own ubuntu partition,  In my case it would be

sudo grub
find /boot/grub/stage1  (which would return 0,2)
root (hd0,2)
setup (0,2)  (usually would be just: setup (0) to install to the mbr)
quit

Actually, if I installed it to its own partition, then insalled vista's bootloader to the mbr and used easyBCD to add in ubunto to the list I think it would work?  I think the problem the 1st time was that when I installed vista to the mbr it just kicked out the ubuntu files, so when vista tried loading ubuntu it was going to the ubuntu partition but not all the files were there to load?  So if I installed grub to the ubuntu partition not the mbr 1st...Hmm Ill give it a go see what I can come up with

---

### Post by Westy87 on 2007-11-26
Ah ok I see thanks.  Well, if its going to be a 2 stage process anyway then I think I'll just stick with how it is now with grub then vista/xp.  But yes I think I know what you mean by how to install grub to its own ubuntu partition,  In my case it would be

sudo grub
find /boot/grub/stage1  (which would return 0,2)
root (hd0,2)
setup (0,2)  (usually would be just: setup (0) to install to the mbr)
quit

Actually, if I installed it to its own partition, then insalled vista's bootloader to the mbr and used easyBCD to add in ubunto to the list I think it would work?  I think the problem the 1st time was that when I installed vista to the mbr it just kicked out the ubuntu files, so when vista tried loading ubuntu it was going to the ubuntu partition but not all the files were there to load?  So if I installed grub to the ubuntu partition not the mbr 1st...Hmm Ill give it a go see what I can come up with

---

### Post by Steve1961 on 2007-11-27
> **Westy87 said:**
> Ah ok I see thanks.  Well, if its going to be a 2 stage process anyway then I think I'll just stick with how it is now with grub then vista/xp.  But yes I think I know what you mean by how to install grub to its own ubuntu partition,  In my case it would be

sudo grub
find /boot/grub/stage1  (which would return 0,2)
root (hd0,2)
setup (0,2)  (usually would be just: setup (0) to install to the mbr)
quit

Actually, if I installed it to its own partition, then insalled vista's bootloader to the mbr and used easyBCD to add in ubunto to the list I think it would work?  I think the problem the 1st time was that when I installed vista to the mbr it just kicked out the ubuntu files, so when vista tried loading ubuntu it was going to the ubuntu partition but not all the files were there to load?  So if I installed grub to the ubuntu partition not the mbr 1st...Hmm Ill give it a go see what I can come up with

Ooops, just noted an error on the setup command.  It should actually be:

setup (hd0,2)

---

### Post by Westy87 on 2007-11-27
> **Steve1961 said:**
> Ooops, just noted an error on the setup command.  It should actually be:

setup (hd0,2)


Woops your right thanks

---

