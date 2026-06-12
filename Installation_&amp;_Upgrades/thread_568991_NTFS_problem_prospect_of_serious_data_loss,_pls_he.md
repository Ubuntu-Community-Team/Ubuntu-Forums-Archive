---
title: "NTFS problem: prospect of serious data loss, pls help!"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by akchaste on 2007-10-06
Hi,

I am stuck with the prospect of serious data loss and that too when I was trying to demonstrate the strength of ubuntu to my windows biased uncle! Here goes the fact: I was trying to install ubuntu from a live cd by partitioning one of the 4  hard drives in my uncle's Dell Precision 690. After booting the live CD, I tried the option of allowing the 'installer' to 'create the maximum free space' by itself and install the OS there (I am banging my head now as to why I refrained from using my time tested partition magic!). At this point, I some how got suspect and on rebooting back to xp, I found that the drive has vanished (MS can't see it! not a surprise, it is 'journaled' now!) from 'My Computer'  and the file format is rendered 'unknown' by windows. Could you pls help me with a suggestion on how to recover the data in this drive by switching the 'journaled' partition back to the ntfs format? 

It would be great if you could give a Bill Gates based advice, meaning how to recover the data from windows, because I would rather not infuriate my patron any more! 

Sorry mates but situation's rather desperate!!!

akchaste

---

### Post by cuby on 2007-10-07
I think it can't be done, I hope you have backups (obligatory when messing with partitions).

---

### Post by akchaste on 2007-10-09
Oh no! I have already managed to recover a substantial amount of the data (the software is still running and I expect a full data recovery) using a commercial software called 'Easeus Data Recovery Software'. I suspect there might be other softwares, even freewares, that might be able to do it but this is the one I successfully tried. Thanks, though, for having a look at the problem.

---

### Post by az on 2007-10-09
> **akchaste said:**
> I suspect there might be other softwares, even freewares, that might be able to do it but this is the one I successfully tried. Thanks, though, for having a look at the problem.

Better still, free-libre open source software!

ubuntu-rescue-remix.org

While your partition was changed and the filesystem formatted, much of your data is still there.  You need to use file-carving techniques to retrieve the data.

As for the cause, what version of the installer were you using?  The installer is typically very safe.  The partitioner has been more effective than partition magic, in my experience.

---

### Post by akchaste on 2007-10-12
Hi, thanks a lot for the ubuntu-rescue-remix.org. Unfortunately, i was trying to pacify a distinctly windows man (it was in his computer that the mishap took place) and had to try windows' ways of solving things. That 'easeus software' has worked but personally i will have a go at the ubuntu-rescue-remix stuff. As of the installer, it was the newest version but I guess my error was in opting for the  auto-install mode using the 'maximum continuous free space' (or something like that) option instead of doing it manually as I am used to ...

---

### Post by az on 2007-10-12
> **akchaste said:**
> Hi, thanks a lot for the ubuntu-rescue-remix.org. Unfortunately, i was trying to pacify a distinctly windows man (it was in his computer that the mishap took place) and had to try windows' ways of solving things. That 'easeus software' has worked but personally i will have a go at the ubuntu-rescue-remix stuff. As of the installer, it was the newest version but I guess my error was in opting for the  auto-install mode using the 'maximum continuous free space' (or something like that) option instead of doing it manually as I am used to ...

Well, the problem with those proprietary windows data recovery tools is that you need to install them in windows, which tends to overwrite some of your recoverable data.

As for the installer, using "largest contiguous free space" should have preserved your other operating system(s).

---

### Post by akchaste on 2007-10-17
hi,

Seems you were quite right in your apprehension that proprietary windows recovery tools (like my 'Easeus software') manage to do away with some data. In my case, it happens to be some important bits, although, I should admit that it managed to recover the bulk. Now here is my query: do you think I can use the 'ubuntu rescue remix' software from a windows (xp) system? Trouble is that this computer is not mine and I am having to deal with a windows system that anyway I am not too happy with.

---

