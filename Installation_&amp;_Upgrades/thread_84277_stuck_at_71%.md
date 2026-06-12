---
title: "stuck at 71%"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by ernie on 2005-10-30
on the 2nd part of the install it went to 71% and then stoped it said something bout acpi configuring so i left it on for 3 hrs and it still was there i shut down the computer and restarted it and i get a bash screen asking me for user name and password and i put that in and do not know what to do now any help

---

### Post by aysiu on 2005-10-30
Sounds as if:

1. The ISO was corrupted during download
2. The CD was corrupted during burning
3. You have faulty hardware
4. Two or more of the above

---

### Post by Stereotypical Rage on 2005-10-30
[http://ubuntuforums.org/showthread.php?t=84157](http://ubuntuforums.org/showthread.php?t=84157)

I'm having the same issue. When you say faulty hardware, what could it be? What does acpi do?

---

### Post by towsonu2003 on 2005-10-30
[QUOTE=aysiu]Sounds as if:

1. The ISO was corrupted during download
2. The CD was corrupted during burning
3. You have faulty hardware
4. Two or more of the above[/QUOTE]

5. unsupported hardware

---

### Post by ernie on 2005-10-30
this is the 2nd time i have tried to install it the 1 st time did not work eiether but it got father than this

how do i get the first try off my hdd

---

### Post by aysiu on 2005-10-30
You don't need to get the first try off--just install right over it.

---

### Post by ernie on 2005-10-30
well i must have messed something up because in gurb there is 4 ubuntu options i can pick and 1 windows XP home  2 are from the first time excluding the recovry thing and to more for the 2 nd try 

anyway what should i do
if i pick form the first install regular boot not recovery mode i see the splash screen for a while then it goes to a text login then it goes to a solid white line horizontial in the top left corner 
in the 1st install in recovery mode it goes though a list of all kinds of things marking most of them w/  [ok]  then down the list a ways it it says [fail]  for one of them then 3 lines down it give me a bash prompt (i hink thats what it is called)
on the secound install it shows the splash screen then goes to the installersays something (i forget the message i press ok and it installs up to 5% thats it
i forget what it does on recovery mode in the 2nd try install.

---

### Post by taygan on 2005-11-01
2nd part of install? installing from CD/DVD drive or after the boot?

If it's reading the CD try enabling DMA.

when you reach the first install screen where you select the language, type Ctl+Alt+F2 , and then enable DMA using (sudo?) hdparm -d1 /dev/sda (or sdb or hdb or whatever device your drive is at.)

---

