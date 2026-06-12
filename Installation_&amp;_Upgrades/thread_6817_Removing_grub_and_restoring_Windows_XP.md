---
title: "Removing grub and restoring Windows XP"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by freds45 on 2004-12-01
Hi
I have 160Gb hard disk as /dev/hda, and a 6.4Gb hard disk as /dev/hdc
I installed Ubuntu yesterday from my dvd on /dev/hdd on the 6.4Gb HDD. Now, I'd like to remove Ubuntu and restore my Windows XP boot.
But I cant do anything, I tried fixmbr and fixboot from windows XP cd recovery console, but nothing works, and I cant get into Windows again...
What can I do except reformating and reinstalling Windows ? Any idea ?
BIG thanks!! :)

---

### Post by az on 2004-12-01
fdisk /mbr

I am not sure of the syntax.

---

### Post by freds45 on 2004-12-01
i tried it many times, but does not work :(
It's worse than a virus to remove :mrgreen: !

---

### Post by Jspired on 2004-12-01
fdisk /mbr
As mentioned, that should work.  Are you spacing it correctly?  And you're running that command from a Windows prompt, right?

---

### Post by wallijonn on 2004-12-01
Check that your windows partition is set to ACTIVE.

I wonder if getting into [COLOR=Green]grub[/COLOR] and issuing the [COLOR=Red]uninstall[/COLOR] command will work. 

.

---

### Post by FLeiXiuS on 2004-12-01
[QUOTE=wallijonn]Check that your windows partition is set to ACTIVE.[/QUOTE]


Or just pop in the windows cd and go to recovery console, and type fixmbr

---

### Post by mark on 2004-12-01
[QUOTE=FLeiXiuS]Or just pop in the windows cd and go to recovery console, and type fixmbr[/QUOTE] I can confirm that this worked for me when I was still running Windows 2000 (yuck).

---

### Post by wallijonn on 2004-12-01
FLeiXiuS,

Yeah, but fred35 said > I tried [COLOR=Red]fixmbr[/COLOR] and [COLOR=Red]fixboot[/COLOR] from windows XP cd recovery console, but nothing works, and I can't get into Windows again...

So that is implying that GRUB was removed and now he comes up with an "[COLOR=Blue]OS not found[/COLOR]" error. Which would imply that he needs to get back into the CD Recovery Console and [COLOR=Red]FIXMBR C:[/COLOR], [COLOR=Red]FIXBOOT C:[/COLOR], & he may also need to boot from a MSDos6.22 floppy (or W98SE floppy), _**NOT**_ run [COLOR=Red]fdisk/mbr[/COLOR], but set the partition ACTIVE via [COLOR=Red]fdisk[/COLOR].

.

---

### Post by freds45 on 2004-12-02
[QUOTE=wallijonn]FLeiXiuS,

Yeah, but fred**35** said 

So that is implying that GRUB was removed and now he comes up with an "[COLOR=Blue]OS not found[/COLOR]" error. Which would imply that he needs to get back into the CD Recovery Console and [COLOR=Red]FIXMBR C:[/COLOR], [COLOR=Red]FIXBOOT C:[/COLOR], & he may also need to boot from a MSDos6.22 floppy (or W98SE floppy), _**NOT**_ run [COLOR=Red]fdisk/mbr[/COLOR], but set the partition ACTIVE via [COLOR=Red]fdisk[/COLOR].

.[/QUOTE]
Not 35, but 45 :D
thanks for all that, I'll try it right now :) !

---

### Post by jdong on 2004-12-02
Warning: **fdisk /mbr** installs a **Windows 9x/ME MBR!** It does a pretty good job of locking up with XP, though... Use **fixboot** to install a boot record (usually unnecessary), **fixmbr** to install an MBR (which will wipe off GRUB)

---

### Post by rekurzion on 2004-12-12
What you need to do for Win XP:

Get your WinXP install CD and install the recovery console (which fixmbr is only available with).  After installing restart your computer and press whatever key allows you to make a selection of startup options.  On my laptop it is <F5> and you should options such as Safe Mode . . . Normal and so forth.  There should be an option which refers to Recovery, select that start the computer in the recovery option.  

Once loaded, simply type the command: fixmbr
No other commands needed. (Have done this more than my share of times trying to use Red Hat, Ubunut is an amazing distro).  

Now just restart and get into windows.  You should now be prompted for a regular/recovery startup everytime you being windows.  

Regardless of suggestion, repairing an master boot record for a WinXP system with any other MBR from an older Win OS will not work and potentially mess up your windows partition.  If you typed in fdisk /mbr and it worked that means that you tried booting up from a Win 98/Me CD, and that's a big no no.  (Like putting water in your gas tank).

My suggestion would be to install linux and mount to your windows patition and backup your files.  Then wipe the computer with a fresh WinXP install and install Ubuntu :)  Or just Linux if you want.

And always RTFM and other manuals to get an idea of what to do and what not to do before following everything read. your data is at risk.

---

### Post by harryfear on 2005-03-20
I can confirm that:
[B]FIXMBR 
DID WORK[/B]

My prob was that i had installed Linux RedHat and GRUB had taken over all of my HDD.

Creating the new MBR table did work.

---

