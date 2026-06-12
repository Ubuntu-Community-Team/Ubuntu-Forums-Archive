---
title: "Can't install Ubuntu along side Windows"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-03-25
I have WindowsXP installed and working properly.
I installed Hardy and was unsuccessful as stated in my last post. Here is the result which I posted earlier...

As it was installing files I got tired of watching and walked away. About a half hour later I came back and the same window was up and the text that was flashing by was saying things like "Removing package blah blah".
This went on with piles of packages being removed. I noticed that most were support and help packages.
Finally install was completed and I rebooted. the bar that goes back and forth on the splash screen went back and forth about 60 times.The screen that finally came up said "Busybox v 1.1.3 (Debian 1:1.1-3-5 Ubuntu12) Built-in shell (ash)
Enter 'help' for list of commands".

This is as far as I could go.

...After this occurred I ran Gnome Partition Editor to view my partitions and I saw that there were Exclamation marks(!) on the Windows partition and on the Ubuntu partition. I right clicked on them and chose "Information".

I do not remember the error messages but they were similar to the messages I got later when I uninstalled Hardy and installed Gutsy.

This is my Gutsy experience...
I installed it with no problem. On running it the splash screen came up and under the word Ubuntu there was a verticle bar which I am sure is the left hand edge of the text box which did not complete being drawn. This is where everything stopped and the system just sat there.

I ran Gnome Partition Editor and this is what I found...

The Windows partition information stated...
"Status-unmounted"
"Warning-Unable to read the contents of this file system"

The Ubuntu partition information stated...
"Status-uunmounted"
"e2label: No such file or directory while trying to open /dev/hda2. Couldn't find valid file system superblock"
"Dump e2fs 1.39 (29-May-2006"
"Dump e2fs: No such file or directory while trying to open /dev/hda2"
"Unable to read the contents of this file system"


I can boot to Windows and run it with no problem. I can boot to Ubuntu but it does not run. I can delete the Ubuntu partition and the error message disappears from the Windows Partition.
I've install Gutsy with Windows many times over the last few months with no problem.
I wonder if this is a hard drive going bad.

---

### Post by sofasurfer on 2008-03-26
I really do need some help with this problem. Someone out there has some suggestions or at least knows a better place where I should be asking this question.

Go ahead now.
No, thats ok. You go first.

---

