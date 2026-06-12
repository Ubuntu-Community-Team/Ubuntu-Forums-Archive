---
title: "icedtea unable to install - Package dependencies cannot be resolved"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by AfrikaDietmar on 2013-03-26
Hi,

i have managed to install Java JDK6 via terminal but it wont install icedtea. From the Ubuntu Software Centre, when i try to install the icedtea plugin i get the error message: "Package dependencies cannot be resolved".
In synaptic, it doesn't show any broken packages. I have tried the apt and clean up commands shown in some tutorials but this didn't solve the issue. Ubuntu Software Centre doesn't show that JDK 6 is installed, but i have some programs that require JAVA and that run such as VUZE. I use Ubuntu 10.04 LTS on an intel core i5 and with an ASUS GT620 graphic card, 8 GB Ram and ASUS mainboard. Not to be part of this thread but it was sort of impossible to get 12.04 LTS working, the only thing that i managed to get installed is on my old cd the 10.04 LTS version where i have run the updates. I also tried to update upto 12.04 LTS which didn't work and maybe messed up things ? Hope you can help.

Best regards,
Dietmar :popcorn: :guitar:

---

### Post by gordintoronto on 2013-03-26
10.04 has so little support time left, it's not worthwhile trying to fix this in that version.

A better solution is a fresh install of 12.04. What happened when you tried to install it? This addresses the most common major problem:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by AfrikaDietmar on 2013-03-26
Hi gordintoronto,

i also my ubuntu pc to work, and spent around 3 days trying to get stuff fixed as a lot of updates and downloads take long. So now I finally have a working 10.04 LTS except with issues like icedtea. If this can sort of be fixed I'll be happy to keep on running the machine thats running without any future updates as I will most likely not require any additional software, a lot is just done through the browser and open office. I did try to get 12.04 LTS up installed and i tried the tutorial and > You can also try acpi = off and nolapic if nomodset also shows up as a black screen. none of these worked and no installation was possible. Regarding the part that says > The solution is to boot Ubuntu *once* in nomodeset  mode (your screen may look weird) to bypass the black screen, download  and install the drivers, and then reboot to fix it for ever.
  Start your computer, and press the Shift when booting up, to get the Grub menu. Use the arrow keys to navigate/highlight the entry you want (usually the first one).

 << Here its unclear to me if it means an already installed version or off the cd.

BUT before we mix up this thread with 2 different issues i have the issue regarding the installation of 12.04 LTS here:
[http://ubuntuforums.org/showthread.php?t=2129374](http://ubuntuforums.org/showthread.php?t=2129374)
But such a shame that its become so difficult to install. :( :guitar:

---

### Post by MAFoElffen on 2013-03-26
> **AfrikaDietmar said:**
> Hi,

i have managed to install Java JDK6 via terminal but it wont install icedtea. From the Ubuntu Software Centre, when i try to install the icedtea plugin i get the error message: "Package dependencies cannot be resolved".
In synaptic, it doesn't show any broken packages. I have tried the apt and clean up commands shown in some tutorials but this didn't solve the issue. Ubuntu Software Centre doesn't show that JDK 6 is installed, but i have some programs that require JAVA and that run such as VUZE. I use Ubuntu 10.04 LTS on an intel core i5 and with an ASUS GT620 graphic card, 8 GB Ram and ASUS mainboard. Not to be part of this thread but it was sort of impossible to get 12.04 LTS working, the only thing that i managed to get installed is on my old cd the 10.04 LTS version where i have run the updates. I also tried to update upto 12.04 LTS which didn't work and maybe messed up things ? Hope you can help.

Best regards,
Dietmar :popcorn: :guitar:
Question-- When you installed Java JDK6 (assuming Oracle's) it says to remove previous versions of Java, which really means to remove previous versions of it's "own" flavor of Java if installed...Not in removing other flavor's of Java. Did you mistakenly take that as meaning that you should remove the OpenJava JDK's? The OpenJDK-6 and OpenJDK-7 are already in 12.04 by default...

You probably didn't know that you can installed different flavors of Java and setup java alternates with symlinks right? The IceTea plugun needs the OpenJDK to hook into. The Oracle JDK can be installed alongside the OpenJDK and Sun Java and... and be setup as an install-alternate... that way if there is a call to a certain specific flavor of Java, it can then find the other flavors. There are many tutorials out there on the how-to's of that. Also, JDK6 is one version back. JDK7 is current for now.

EDIT-- But noting now that you upgrade from 10.04... Instal/reinstall the OpenJDK-7 and then try IcedTea...

---

### Post by AfrikaDietmar on 2013-03-26
> Question-- When you installed Java JDK6 (assuming Oracle's) it says to  remove previous versions of Java, which really means to remove previous  versions of it's "own" flavor of Java if installed...Not in removing  other flavor's of Java. Did you mistakenly take that as meaning that you  should remove the OpenJava JDK's? The OpenJDK-6 and OpenJDK-7 are  already in 12.04 by default...

I am using 10.04 LTS not 12.04 - i wished this worked so i would have all those features by default as you say but I dont and I am looking for making things work in my 10.04 LTS environment as I have already set up everything there and I prefer not to change now. It will be more work to make a fresh install than to fix this bug. I mean mostly everything is running fine apart those issues with icedtea.

How do i know if i have older versions ? I installed VUZE a program that requires JAVA, when i tried to make it run, it didn't. So I installed JDK6 via terminal and then VUZE worked. But in my ubuntu software centre it wont show that JDK6 is installed even though it is.

> You probably didn't know that you can installed different flavors of Java and setup java alternates with symlinks right?
No. Symlinks... hmm, not to clear - you mean i can connect different programs to run with different java versions ?
Right now i have JDK6, the tutorial i used to install it from terminal was simpler than for the JDK7. After that my programs that require java run.

> EDIT-- But noting now that you upgrade from 10.04... Instal/reinstall the OpenJDK-7 and then try IcedTea...
This thread remains as an aim and goal to figure out on how making icedtea work and solving the problem: "Package dependencies cannot be resolved"
Doing a fresh install of 12.04 is not the solution in this thread. In another thread i am looking to find other solutions of how to install 12.04 as it didn't work on my new pc but lets keep this thread for 10.04 of finding the solution of the problem i have. I might not install 12.04 in the soon immediate because its extremely time consuming, i tried it for the last 3 days but i need my machine operating to work with so there is also a time pressure constraint. But also out of interest am keen to get to know the reasons and solutions.

---

