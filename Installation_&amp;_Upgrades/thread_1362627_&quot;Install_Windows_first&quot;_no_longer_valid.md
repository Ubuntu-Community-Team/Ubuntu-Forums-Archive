---
title: "&quot;Install Windows first&quot; no longer valid?"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2009-12-23
Good morning!

I'm on dial-up so researching is a hassle.  When dual-booting, is the old saw about installing Windows first no longer valid?  I'm getting the impression from some of the recent threads that GRUB2 has changed the game.

---

### Post by coffeecat on 2009-12-23
Not at all. The advice to install Windows first is indeed still valid. It doesn't matter whether you have legacy grub or grub2, if you install Windows second it will overwrite grub stage 1 (legacy or version 2) with the Windows mbr.

Then you will have to repair grub from a live CD - and you will have to make sure you are using a live CD with the appropriate version of grub.

---

### Post by gcmartin on 2009-12-23
@CoffeeCat
Will GRUB2 autoscan, detect, and rebuild the boot manager screen to include ALL bootable images seen of the system's disk automatically?
THX

---

### Post by chuck4200 on 2009-12-23
Linux Newb/Old DOS 2.0 guy here.  Little twist on this problem.  

Cleaned and reformatted, etc.  GRUB booted fine for Win (DOS prompt) and Linux.
installed Ub9.1, running fine.  
20GB old IBM laptop.  Want to restore win98 image.    
5GB Win, 8 GB FAT32 for dual access storage of Win & Linux, & 6 GB for Ubuntu w/swap.

Used Ghost to restore a partition image of Win98.  Was a bad image, etc.  
Can not boot back into DOS or C: via HDD or CD boot.
Apparently the drive is not being recognized.

Unless I can fix quick before trip tomorrow, will be in a bind.
Have Live CD running now.

Any suggestions to fix?

---

### Post by Bartender on 2009-12-23
OK, I'm just getting a little mixed up is all and I don't want to keep giving out bad advice.  I've been saying "Windows first" for quite a while because 1) that's what everybody else was saying, and 2) that's what worked for me.  I understand the basic principle behind the MBR and GRUB Stage 1, just wanted to know if that had changed.

Some folks on the forums are proposing Linux first as their preferred method and I haven't spent the time to figure out what exactly they're talking about...

chuck, there are too many moving parts described in your thread for me to hazard a guess.  Sounds like the image didn't work.  Wait a minute, if I understand things correctly an image won't change the MBR, which is (or was) strictly set up for Ubuntu.  If you want to try fixing the Windows MBR, that might work.  But it might not, unless the image is otherwise ready to go, and restoring the Windows MBR will mean you'll have to fix GRUB too if you want to dual-boot.  So the immediate effect of fixing the Windows MBR could easily be two unbootable OS'es...

---

### Post by Herman on 2009-12-23
> I'm on dial-up so researching is a hassle. When dual-booting, is the old saw about installing Windows first no longer valid? I'm getting the impression from some of the recent threads that GRUB2 has changed the game.:) Hi Bartender,
It's a myth that people 'have to have install Windows installed first'.
The only reason for having Windows installed first is because it's simpler to advise beginners do things that way, it saves the effort of explaining how to re-install GRUB. 
Generally speaking, Windows can be installed first, middle or last and boot Windows in any physical location on any hard disk, and in any partition number, (even in a logical partition).
You need to know how to configure whatever boot loaders you're using. 
There are certain peculiarities, (or bugs), to be aware of with various Windows versions.

@ chuck4200,
Windows 98 has a bug in the installer that prevents it from recognising any hard disk if there are logical partitions present. Try deleting any logical partitions and then try again to install Windows 98 from CD. If your only logical partition is a swap area, that won't be too much of a hassle. If you have Ubuntu installed in a logical partition it might be more work though. I seem to recall there's some convoluted workaround with the Windows 98 partitioner to get it to co-operate even with a logical partition present but my memory of that is a little vague right now ...

---

### Post by chuck4200 on 2009-12-23
Thanks for the W98 image advice.  Had both on the system when I first started this comedy of errors for dual booting.  The whole gparted thing got me confused the first time through install and I decided to start from scratch due to potential partition nightmares from resizing, etc.

The only thing I do understand is that it is much simpler to install any Windows flavors on the first partition due to the boot and install circumstances.  Will repartition and format later and put a clean W98 image back on, then reinstall Linux again.

I can live with muddling my way through Ubuntu until I return.  The main thing is email access to email databases and my doc/excel files.  Solved those problems with FF and Tbird already.

My question is solved for now.

---

### Post by Bartender on 2009-12-23
hiya, herman!

High five

Understood that you don't "have" to install Windows first, it's just the easier path.  Can you install Windows second or third or in the middle as you describe without doing command-line edits to grub config files that would likely be intimidating for newbs or for people such as myself who find they're *still* not very good at the terminal?

I guess what I was hoping for was that GRUB2 could deflect a Windows installation that's trying to overwrite the MBR and assimilate it automagically.  Like the Borg.  Now that would be cool!

---

### Post by Herman on 2009-12-23
> Can you install Windows second or third or in the middle as you describe without doing command-line edits to grub config files that would likely be intimidating for newbs or for people such as myself who find they're *still* not very good at the terminal?If you're installing Windows from a Windows installation CD, the answer is yes. Windows should normally be able to configure itself automatically, all you need to be able to do is re-install GRUB. 

If you're copying Windows there from a cloned image, like with a dd command, partimage, clonezilla or the proprietary 'Norton Ghost', that would be a little bit more complicated.

The degree of complexity varies.

You can copy an operating system to the same partition number you had it installed in previously, and you can probably boot it right up without the need to edit any Windows boot loader files.
You'd only need to edit menu.lst with the old (Legacy) GRUB, or run grub-mkconfig if you're using GRUB 1.9*. 
Probably you'd need to re-install the boot sector to make it point to the boot loader files. 
I was taking it for a fact that chuck4200's image was corrupt, but your suggestion for him to try fixing the MBR was a good idea, maybe the image was okay and just needs the boot sector fixed.

If it's a cloned image and you copy it to a different partition number then you will probably need to edit the Windows boot loader configuration files or issue a command to have Windows update its boot loader files.
For Windows 95 or 98, you can run A:\ SYS C: from a boot floppy, and in Windows XP it's bootcfg /rebuild from a recovery console in an installation CD  if you don't know how to edit boot.ini yourself. 
With Windows XP or earlier, if you want to you can edit the boot loader configuration files from Ubuntu, that's the easiest way. We can edit the numbers in the file, but it's important to avoid using the return key (to make any new line), because the Windows format for new lines is different from the Linux kind. Wikipedia link: [5 Common problems]("http://en.wikipedia.org/wiki/Newline#Common_problems") That can be fixed with  a program called [unix2dos]("http://gaarai.com/2009/03/08/convert-dos-formatted-files-to-unix-format-in-ubuntu-and-centos/").
Otherwise we need to fix Windows with Windows, which is impossible because Windows can't boot, so it's a recursive problem unless we have a boot disc from [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").

 Vista or Windows7 have better repair programs in their installation discs for fixing their boot loaders automatically, but we can't edit their boot loader files from Linux anymore.
Vista and Windows 7 are both made with a bug or at least a peculiarity built into them which ties the bootloader files to the MBR ID number when they're installed, so if you want to clone them to a new hard disk you need to copy the first 446 bytes of the old hard disk's MBR with a dd command and copy that to the new hard disk's MBR, or at least that's the way I do it. Microsoft might have some other workaround recommended for that, I haven't needed to look for it.

---

### Post by chuck4200 on 2009-12-26
> **Herman said:**
> 
I was taking it for a fact that chuck4200's image was corrupt, but your suggestion for him to try fixing the MBR was a good idea, maybe the image was okay and just needs the boot sector fixed.


Herman,

Thanks for the advice.  The image is bad, but I have several older clean images, and will will try the MBR fix when I return and have more time to try out some things.

Starting from a scratch 9.1 install after all the "attempts" I've made would not hurt this setup, and I will probably abandon W98 altogether if possible.  Nothing like having the time and a good challenge to learn things.

Chuck

---

