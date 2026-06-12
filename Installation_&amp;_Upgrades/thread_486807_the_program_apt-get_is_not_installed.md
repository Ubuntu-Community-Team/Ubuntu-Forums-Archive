---
title: "the program apt-get is not installed"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by mikehipson on 2007-06-28
i recently installed ubuntu on my laptop.  it worked ok for about 3 or 4 days until one day the computer would not boot.  the message i get is that the program apt-get is currently not installed.  ill just write everything that appears on the screen, i am new at this

*an automatic file system check (fsck) of the root filesystem failed.  a manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read.only mode.  A maintenance shell will now be started.  After performing system maintenance, press control-D to terminated the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups. command not found
bash: lesspipe: command not found
bash: The: command not found
The program "apt-get" is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program "apt-get" is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@ (the name of my computer): #


Here the laptop waits for me to do something..... what should i do?  I do the obvious by typing what it asked me to type, but it just ends up the same, like this:
bash: apt-get: command not found
root@ (the name of my computer): #


Can anyone help me? I dont even know if it is ubuntu that is doing this, or the ghost of windows xp home edition haunting my computer.  that was the os i had before.....
What can i do? 

Mike

---

### Post by PaulFr on 2007-06-28
When this happens, usually you have to run **fsck** - this will check the filesystem(s) and ask you to confirm any changes it does to repair the filesystem(s). Once this is done, then press control-D as the message suggests.

---

### Post by mikehipson on 2007-06-28
Paul
It worked!  
thank you very much for your advice.  I really appreciate it.

Mike

---

### Post by fred0843 on 2007-07-01
I have the same problem I tried fsck does not work.This happens when I install on A multiboot setup.If I install ubuntu last it is ok.

---

### Post by PaulFr on 2007-07-01
Are you shutting down the laptop / system or switching off the power ?

Having this message frequently usually points to filesystem issues which can be caused by abrupt loss of power, or hard disk failures. Try this: Log off and properly shut down the computer. Then restart it - does the fsck message come ?

Other possibilities: your /etc/fstab has fsck checking turned on for removable media (see **[http://ubuntuforums.org/showthread.php?t=288625](http://ubuntuforums.org/showthread.php?t=288625)**) or your hardware clock has problems (see **[https://launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175](https://launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175)**).

---

