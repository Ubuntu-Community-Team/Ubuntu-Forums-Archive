---
title: "Shut down durring Ubuntu 11.10 update System76 Starling"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by drewfish on 2013-01-30
I have had a System76 Starling for a while now, but I have just used it for basics like internet and word so am still a total newbie to ubuntu. I went to upgrade the other day to 11.10.1 (or .4?) it looked like everything installed ok, but then it wasn't doing anything for a while and stupid me I shut it down (i know, i know! already kicking myself in the you-know-what for this).
Now when I turn it on i get a screen with:

GNU GRUB version 1.99-12ubuntu5.1

and the following options inside a box:

Ubuntu, with Linux 3.0.0-29-generic
Ubuntu, with Linux 3.0.0-29-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

I have tried selecting a various combo of the first three and they ultimately lead to a Recovery Menu (filesystem state: read-only) where I can select resume, clean, dpkg, failsafeX, fsck, grub, network, root, and system summary. I have tried resume and it takes me to a screen that looks like it is trying to load Ubuntu 11.10, but just keeps cycling through the dots. (also tried to do dpkg but I cannot arrow down to select it?)

Any suggestions?

---

### Post by Bashing-om on 2013-01-30
drewfish; Hi ! Welcome to the forum.

Try this and advise results:
In that grub menu with the first kernel entry highlighted; press the "e" key for edit mode;
Arrow down to the line containing the term "quiet splash" insert the term "text" within the quote marks, remove - quiet splash -.  Ctl+x to continue to boot, This hopefully enables one to see boot messages and boots to a command line interface login (textural).
login: username and password.
What results from the terminal commands:
```
 sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
dpkg --configure -a
```[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by drewfish on 2013-01-30
Hi Bashing-om! Thanks for getting back to me!

I booted up and went into edit mode. The line containing the term "quiet splash" looks like this:
linux /boot/vmlinuz-3.0.0-29-generic root=UUID=33ac49be-0a52-411b-9654-4b7ccb572180 ro \ quiet splash vt.handoff=7

If i understand you right , that line should instead read:
linux /boot/vmlinuz-3.0.0-29-generic root=UUID=33ac49be-0a52-411b-9654-4b7ccb572180 ro \ text vt.handoff=7

then hit the ctrl key and simultaneously hit the x key?

I did that and all I have is a black screen... did I miss-read somewhere?

---

### Post by drewfish on 2013-01-30
Further Update:

I hit ESC in the blank screen state (i need to stop thinking i can experiment with this guy like I used to do with my mac!), and it took me to a texted screen with lots of lines that boil down to the computer trying to load the essential drivers, and running several things successfully until it gets to a line where it says 'GLIBC-2.14' not found and the mountall main process 319 was terminated with status 1... general error mounting filesystems, maintenance shell will now be started, ctrl D will terminate shell and reboot system.
last line is:
root@drew-Starling:~#

this make any sense?

---

### Post by Bashing-om on 2013-01-30
drewfish;

Somewhat makes sense, surprised to be dropped to a "root" shell. Not able to find that library might hurt real bad. But there still exist a operating system!

Let's see if ubuntu's file system check/repair utility will fix things up:
From that grub menu this time choose the "recovery" kernel -> in the recovery console choose "fsck".
After fsck completes choose "resume normal boot".

Do you now boot to a GUI to log into the system ? Login and run that sequence of terminal commands. [if not mounted "read only"]

----
vt.handoff=7 : has been depreciated/some time ago was used as : vt = virtual terminal, handoff = the GUI terminal # 7//And yeah, think'n about it, should remove that term also to get a "text" login// Would not hurt to try it and see what haps -> tty1 login ??
----------
> linux /boot/vmlinuz-3.0.0-29-generic root=UUID=33ac49be-0a52-411b-9654-4b7ccb572180 ro \ quiet splash vt.handoff=7 The "ro \"  means the system is mounting "Read Only" to protect it's self from additional damage. "fsck" might take care of it ?
-----------

Experimenting : That is a good thing too ! I can not tell you how may times I have (or my Wife) broke my system. Many times to the point of giving up fixing it and (re)installing.
I learned a lot breaking and fixing. Practice and backups of what is important, and I can now (re)install in 20 minutes to my present workable configuration.
With one's files backed up and a liveCD can repair whatever may mishap in this operating system. Then there is an axiom here on the forum - if it ain't broke you have not tweaked on it enough !
---------
Try the two above and see what happens.

---

### Post by drewfish on 2013-01-31
Ok, so I tried to go into the recovery kernel but it is not letting me arrow or choose options from there? I have tried arrowing down, and it just starts running the first option (which is resume) and I also tried typing in "f" to try to get to fsck but it just takes me to the first "f" which is the failsafeX... (and doing "fs" takes me from failsafeX to system summary) The Recovery Menu does say that the filesystem state is read-only - is that effecting this or is there some other way to choose options?
 
Thanks for all your patience with this!

---

### Post by Bashing-om on 2013-01-31
drewfish;

Are you still having problems getting to the "fsck" option?

In that intitial grub menu arrow down to the "recovery" kernel, press enter key -> recovery menu ->fsck (12.04 version -your version should be similar). I'll reboot and refresh my memory.
[INDENT]try'n to help

edit: Yep, that is the way mine is. Please advise you current status -(will you need to (re)install ??)
[/INDENT]

---

