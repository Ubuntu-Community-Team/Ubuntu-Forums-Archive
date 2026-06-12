---
title: "Slow Ubuntu Desktop"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by henryjm206 on 2008-09-22
I installed ubuntu 8.04 today on a hp desktop w/ 1.0ghz proccessor and 384 mb SDRAM the OS should run smoothly but doesnt firefox takes about a minute to start up:(
please give me some tips about speeding my computer up :(

henry

---

### Post by wolterh on 2008-09-22
Well, to start, you are running on a relatively slow computer.
You should monitor your memory by running in the console/run-application (Alt+F2) what is consuming all the memory that slows down your computer. You should check also your processor usage percentage, and again, check which application(s) are eating it all up.

When you have done, post them here.

If there is no hope for you, you should try another distro with less graphical niceness

---

### Post by henryjm206 on 2008-09-22
Im running conky right now and my cpu usage is about 100% all the time :(
memory is 70% used up too.
Does anyone know any small operating systems that dont use fluxbox?

henry

---

### Post by wolterh on 2008-09-22
Well, you did not tell me which applications were consuming the CPU! Usually CPU consumption is 0%, but ocassionally some application insanely starts using all of it.

Now, I want you to press ALT+F2 and type in 'gnome-system-monitor' (without the quotes)
Click on the processes tab, sort by '% CPU', take a screenshot, and post it here. Sort now by 'Memory' and paste another screenshot here.

-----

For the distros, I think you might want 'xubuntu' which was designed for 'less powerful computers'

---

### Post by henryjm206 on 2008-09-22
here is memory usage and cpu usage 

henry

---

### Post by wolterh on 2008-09-22
Perfect. Now, in the screenshots you were not using 100% of CPU, and your memory consumption was fine.
I do not see why your desktop is slow...
So tell me, slow in what terms? Your applications take long to load?

**What do i have to do to have that conky thing? I downloaded conky but its an ugly console...**

---

### Post by liquidfunk on 2008-09-22
I'd personally recommend this [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

---

### Post by henryjm206 on 2008-09-22
open a text editor and paste in a .conkrc file that you find online [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
and name the file .conkyrc and put it in your home folder

then do killall conky
then conky and it should run

henry

---

### Post by snowpine on 2008-09-22
> **liquidfunk said:**
> I'd personally recommend this [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

+1, Crunchbang is quite a bit speedier than Ubuntu or Xubuntu.

If you want to stick with Ubuntu, one tip to speed things up is to go to System-->Sessions (I think that's what it's called, haven't used Ubuntu in a while) and turn off any processes you don't use. I found that turning off Tracker sped things up a bit.

ps Firefox is one of the slowest browsers around. Try some of the other options like Epiphany, Opera, Kazehakase, Swiftfox, Dillo, Links, etc.

---

