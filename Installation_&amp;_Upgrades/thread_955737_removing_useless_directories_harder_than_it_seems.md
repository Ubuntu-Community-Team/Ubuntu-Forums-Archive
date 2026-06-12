---
title: "removing useless directories: harder than it seems"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by .vinsai. on 2008-10-22
So I've been trying to install the Java jdk and runtime environment on my favorite new OS.  First, I went to Sun's website and downloaded .bin files for the jdk and jre and figured out how to make them run and did all that, the files installed and extracted and I thought I was golden, but when I tried to run java or javac in command window it told me how to install with apt-get.  Soooo I did that and now everything works, but I've got these files that the .bin's extracted that do nothing but take up space.  How can I get rid of them?

---

### Post by jamesstansell on 2008-10-22
Just delete them.  From the command line you want the 'rm -r' command.  Or you can also remove them using the graphical shell.  But in that case watch out or they will still be taking up space in your trash can.  You can get rid of the bin files too while you're at it.

Just curious - why are you finding it hard to get rid of them?

---

### Post by .vinsai. on 2008-10-23
I'm not new to computers, just Linux, I know how to delete from gui :P

It tells me permission is denied whenever I try to delete the files.  I tried using rm -r and it asked me if I wanted to delete the read only file 'name.whatever' and asked me for each individual file, but didn't do anything.  Some of them told me permission was denied, but all of the files are still there.

**Edit got rid of them using 'sudo rm -r'

---

