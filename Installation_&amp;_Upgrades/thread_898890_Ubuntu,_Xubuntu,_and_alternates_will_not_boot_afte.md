---
title: "Ubuntu, Xubuntu, and alternates will not boot after install"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by mothraman on 2008-08-23
<I first posted this in "hardware & laptops," thinking that my machine was the problem, but I guess it belongs here.>

I have an IBM Thinkpad 1161-210 with a 6G HD, 160MB RAM, and a 500mhz intel celeron processor.

I have tried installing 4 flavours of Ubuntu 8.04--Ubuntu, Ubuntu alternate, xubuntu, xubuntu alternate. Ubunutu just hangs during install and looks at me with a blank screen.

The other all behave in the same way: they claim to have installed successfully, but when I try to boot I get the logo screen with a progress bar, then a blank screen, then a flash of the logo, then a blank screen forever.

I do see a "no dmi bios year use acpi=force" message, which I researched somewhat. Don't know if there's any relationship or not, but in just in case (in xubuntu, alternate--the last one I've tried) I edited the boot string and added acpi=force...no change.

I have seen one other post where a person claims to have installled xubuntu on this machine.

Any ideas on what I could try next?

---

### Post by Pumalite on 2008-08-23
With 160 MB of RAM; I'd stick to smaller distros like DSL or Puppy.

---

### Post by neilmaclennan on 2012-02-29
> **mothraman said:**
> <I first posted this in "hardware & laptops," thinking that my machine was the problem, but I guess it belongs here.>

I have an IBM Thinkpad 1161-210 with a 6G HD, 160MB RAM, and a 500mhz intel celeron processor.

I have tried installing 4 flavours of Ubuntu 8.04--Ubuntu, Ubuntu alternate, xubuntu, xubuntu alternate. Ubunutu just hangs during install and looks at me with a blank screen.

The other all behave in the same way: they claim to have installed successfully, but when I try to boot I get the logo screen with a progress bar, then a blank screen, then a flash of the logo, then a blank screen forever.

I do see a "no dmi bios year use acpi=force" message, which I researched somewhat. Don't know if there's any relationship or not, but in just in case (in xubuntu, alternate--the last one I've tried) I edited the boot string and added acpi=force...no change.

I have seen one other post where a person claims to have installled xubuntu on this machine.

Any ideas on what I could try next?
I recently was given a thinkpad 1161-11u with 160mb ram and have been having the same problems as yourself. When the installing stage, screen shows (the one that has the colored dots under the name) press escape and you get to see what's going on. Mine stalls too right after the battery check. If you press <ctrl>+<alt>+(f1) you get a command prompt I typed xterm to get a terminal and the message I got was "Not enough video memory for the configured screen size" blah blah blah and ending in "(EE) screen(s) found, but none have a usable configuration."
How this will help you I couldn't tell you as I know next to nothing about using the command line. lol. But I can say this I know more about it now since playing around with it, but am no closer to installing Ubuntu. lol. I have found out how to gain root access though. at the prompt type either 'sudo -i' or 'sudo su' What the difference is I don't know, but it allows you to navigate the directories and run any of the apps and commands that don't use a gui or need another pkg to work. I am going to try a DSL distro and or Puppy too. You can build your own distro step by step via SUSE Linux which may be an option as it can be tailored to be small and have all the right drivers to run an ancient laptop like the thinkpads. Anywho have a great day and if I get something working via any of those OS's mentioned I will let you know. And if you have made any progress beyond using the system for a doorstopper let me know.

---

### Post by neilmaclennan on 2012-02-29
I found a few things for you to try. At the install/liveCD menu press F6  then escape then press tab and add vga=770 this will result in a  failure but you will be able to scan for viable types as a result or  pick from the list. Let me know if any work for you I am working through  the list as I type this and haven't found one yet GGGRRRRRR.... that  works. And because each boot takes 3 minutes or so it is a very tedious  process. But I have nothing better to do tonight and can't pick up a new  CD to burn another OS till tomorrow. I have even tried pressing the  space bar at the error choice screen (sorry for the lack of correct  jargon) to have it continue, will that work??? dum de dum ... waiting  for the result OOOHHH orange font this time . Nope it didn't either  however the command prompt appeared on its own without me having to mash  the keyboard lol

---

### Post by MAFoElffen on 2012-03-01
> **neilmaclennan said:**
> I recently was given a thinkpad 1161-11u with 160mb ram and have been having the same problems as yourself. When the installing stage, screen shows (the one that has the colored dots under the name) press escape and you get to see what's going on. Mine stalls too right after the battery check. If you press <ctrl>+<alt>+(f1) you get a command prompt I typed xterm to get a terminal and the message I got was "Not enough video memory for the configured screen size" blah blah blah and ending in "(EE) screen(s) found, but none have a usable configuration."
How this will help you I couldn't tell you as I know next to nothing about using the command line. lol. But I can say this I know more about it now since playing around with it, but am no closer to installing Ubuntu. lol. I have found out how to gain root access though. at the prompt type either 'sudo -i' or 'sudo su' What the difference is I don't know, but it allows you to navigate the directories and run any of the apps and commands that don't use a gui or need another pkg to work. I am going to try a DSL distro and or Puppy too. You can build your own distro step by step via SUSE Linux which may be an option as it can be tailored to be small and have all the right drivers to run an ancient laptop like the thinkpads. Anywho have a great day and if I get something working via any of those OS's mentioned I will let you know. And if you have made any progress beyond using the system for a doorstopper let me know.
W/ only 160MB max on that Laptop, 

First, I'd try Lubuntu, which should boot in 53MB. 

If that doesn't suit you, then next I'd try Puppy Lynx, which is based on Ubuntu Lucid Lynx 10.04 LTS. It only uses 30MB booted to the desktop. Graphical applications will run well in 128MB.

[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

This link is the results of hardware tests (How much memory used) for various distros. Note that those tests are base reading after boot. Memory used would go up from there when applications are loaded on top of that.

Also note that Xubuntu loaded from the Xubuntu LiveCD uses more memory than if it where loaded from the Ubuntu Minimal Install CD.  The Minimal Install itself cuts an install down to the minimum needed without waste. This is like the step by step build you were talking about.

My experience with SUSE and OpenSuse is that they always seemed fat (non-lite) and end up in extra work with installations, updates and maintenance. I do like debian based distros over rpm based. I have to work with both styles (on servers and desktops)- but I do have my preferences.

---

