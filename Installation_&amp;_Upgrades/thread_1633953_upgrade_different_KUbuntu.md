---
title: "upgrade different KUbuntu"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by wike1970 on 2010-11-29
Hi Everybody

I have some question about upgrades. As I understand one who install Ubuntu/KUbuntu 8.04 can't upgrade to Ubuntu/KUbuntu 10.04. Well I installed KUbuntu 9.10 on my leastest computer. Now to my questions, if I understand correct when KUbuntu 11.10 comes out in about a year from now. How should one do since if I understand correctly I can't upgrade to that version then? Do I have to do a new installation then? Or can one take home the ISO-file and burn it to a CD and upgrade it from the CD? Or is one force to do a new installation and lose everything one has on the computer. If so is there a program that you can do backup with? Or can one move everything to external hard drive? I hope that someone can help me with these questions. I know they are a lot of questions. But still hope that someone can help me with them. Thank in advance. 

Yours
Wike1970

---

### Post by ender4 on 2010-11-29
most of what you want to back up is in your /home folder, so for a re-installation copying your /home folder to an external media should save most of your documents and settings, the exception would be if you manually changed something outside of /home (for example if you developed code in the /src folder, or installed custom programs in /usr/local).  In particular /etc may contain system-wide configurations you want to keep (though if you didn't make any changes you *probably* won't need to back it up), and /var will contain things like log files and possibly email, which you probably won't need to keep, but that depends on your needs. Most likely, unless you have a specific reason to save something else, just back up /home. There are programs specifically made for backups, but any means of copying files will do.  

Besides the files themselve, you might want to back up the packages that you installed. Note, the following commands must be run in a terminal.

The command "dpkg -l" (that is an ell) prints out a list of packages you have installed (along with some extra information).
The secon field contains the name of the package, so to get a list of the package names in file run the command

"dpkg -l | awk '{print $2}' > *name_of_file*"
where *name_of_file* is the file you want to save the list to.

To install all the packages on the new system run:
"apt-get install `cat *name_of_file*`"

As a side note, if you have a seperate partition for /home, then you can easily reinstall Ubuntu (or any other linux distro for that matter) without worrying about overwriting your important files.

---

