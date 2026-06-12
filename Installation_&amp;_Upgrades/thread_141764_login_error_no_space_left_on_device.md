---
title: "login error: no space left on device"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by imaca on 2006-03-09
Help!
Installed some new programs then after reboot logon fails with following error: mkdttemp: private socket dir: No space left on device

Used Live CD to check and I have:

dev/hda2 2865Mb total, [COLOR="Red"]18Mb[/COLOR] free (i presume this is system)
swap 480MB
dev/hda4 1425Mb total, 762 Mb free

Is lack of HD space the problem?
If so how can I fix?

---

### Post by Heliix on 2006-03-09
yes, lack of space is the problem. you must delete something from your /
clearing the whole /tmp directory *should* be harmless, afaik, because some people actually clear their /tmp at each reboot

if your home resides on separate partition, you'll probably need to free some space in your home as well, i can't guess how much is "enough" ;-) just try

did you try to log in in the console or only the graphical login? (if you boot from the hdd)
i'd advice to log in as root in the console and uninstal some unnecessary programs
if not, boot from the cd and either just delete something (the disc partition must be mounted in read+write mode: maybe you'll need to umount in ant mount -rw) or chroot to your / and tidy it up 

and in the future, never let yourself get trapped in such situation again. on comps with small memory, big fat programs such as gnome and the whole bunch of openoffice aren't the right thing..

and..you DO have backup, don't you?

---

### Post by imaca on 2006-03-09
Thanks - logged on in console and managed to fix it using "apt-get clean".
Luckily I have 2 PCs.
Looks like I need a bigger disk in this 1.
What is the minimum free disk space required for "system"?
(I have "home" on a seperate partion)
Is it possible to get Ubuntu to warn when space is getting to low?

---

### Post by Heliix on 2006-03-09
good :-)
the size of the disk is OK for running system quite happily, storing the data is another thing
it's more likely that your hdd is stuffed with things you don't need, such as unused programs, some temporary files, downloads that are no longer necessary.. it's a better school to learn how to use your disk space more effectively than just go and buy a new disk
if i were you, i'd buy a new disk only if i intend to store a lot of music, films, photos etc. and don't want CDs (DVDs)

i have a friend that runs linux on 2GB hdd, why not.. her free space is about 200MB, linux is modest with respect to memory ;-)

how could linux warn you that the space is getting low?
from time to time, run "df" (disc free)-show the free space on your partitions
"free" gives you info about your ram and swap state
"du" (disc usage) with some options informs you about the size of files and directories
and if you want to be auto-informed, you'll probably have to write a shell script ;-) i think there isn't any such tool yet

"deborphan" finds broken/incomplete packages, which you can then remove
"tmpreaper" cleans directories and remove files based on their age (hm.. i don't recommend)

i had also the problems with low memory (hdd size and small ram) and it got MUCH BETTER when i got rid of gnome and change to xfce4. (have you ever tried other desktop managers?)
try some googling, the size of your hdd is OK, you just need to learn how to use it more effectively.

---

