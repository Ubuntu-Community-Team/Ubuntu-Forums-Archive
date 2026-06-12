---
title: "Running an autorun script??? root?? huh?"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by cyph3x on 2007-09-23
I have just download a driver for my Samsung ML-2510 printer. it is a .tar.gz i extract it to my desktop and "autorun" (some kind of script?) wont run without root privileges. And i am not experienced with ubuntu enough to be able to achieve root in the terminal and run it that way. Also, the top folder once i extract is called "cdroot" and i cant seem to delete that either without root priveleges (so now i have 5 copies of the same folder that i cant move or get rid of... dah!)

any help/pointers would be helpful... i guess in a nutshell i am asking: How do i achieve uber root in the GUI so i can run things and delete them?

-Thanks ><

---

### Post by jrib on 2007-09-23
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersSamsung](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersSamsung) has some basic instructions but I've never played with this driver as I do not have a Samsung printer.  Here's what the comment on the wiki basically recommends.

You will need to 'cd' to the directory where yourVersion_UnifiedLinuxDriver.tar.gz is first.  If yourVersion_UnifiedLinuxDriver.tar.gz is on the Desktop, then you would need to do "cd ~/Desktop".  Recall that linux is case-sensitive.  After this:
```

tar xzf yourVersion_UnifiedLinuxDriver.tar.gz
cd cdboot
sudo -i
./autorun
exit

```

---

