---
title: "system won't start up"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by grayfox444 on 2008-05-21
I'll type everything i'm seeing on the screen right now. these errors apparently came out of no where, as i saw nothing that could have lead to this:

Checking drive /dev/sda1: 7% (stage 1/5, 260/2362)
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 7% (stage 1/5, 260/2362)
                                                [fail]
* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command nott found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@desktop:~#

---

### Post by xueg0i on 2008-05-21
Try typing:
```
fsck /dev/sda1
```

---

### Post by xueg0i on 2008-05-21
Well you might end up with pressing 'y' a lot of times, you might consider:
```
fsck -y /dev/sda
mount -o remount,rw /
```
And then Ctrl-D to reboot

Hope it helps. Do a backup of your essential files directly after it (don't forget to backup your config files!) Good luck.

---

### Post by grayfox444 on 2008-05-21
i typed in fsck /dev/sda1 and got the response 
"WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.
do you really want to continue?

when i did fsck -y /dev/sda it said device or resource busy while trying to open /dev/sda filesystem mounted or opened exclusively by another program.

---

### Post by xueg0i on 2008-05-21
Sorry mate, I don't know how to solve that. All I can suggest now is try to backup if possible at all in this state.

---

### Post by grayfox444 on 2008-05-21
i have everything on an external harddrive that i backed up not long ago.
any suggestions on how to go from here though? should i just reinstall?

---

### Post by grayfox444 on 2008-05-21
when it was checking the drives i was able to press ESC to skip it, and the system loaded up normally...

---

### Post by xueg0i on 2008-05-22
Try booting from a live-cd and do a fsck on your harddisk as I proposed earlier.

---

### Post by peakshysteria on 2008-05-22
Have you read [[COLOR="Red"]this one[/COLOR]]("http://ubuntuforums.org/showthread.php?t=789454&highlight=%2Fdev%2Fsda3%3A+UNEXPECTED+INCONSISTENCY%3B+RUN+fsck+MANUALLY")?? It's marked solved....

---

