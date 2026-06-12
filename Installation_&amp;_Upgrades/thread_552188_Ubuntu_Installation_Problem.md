---
title: "Ubuntu Installation Problem"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by D3v on 2007-09-16
Hi all,

I have been thinking about installing Ubuntu for a long time and decided to actually do it about a week back. I already got the 6.06LTS CDs from the shipit service (really great idea whoever came up with it) and had a later version (6.10 I think) downloaded on the HD.

Here is the problem I am facing:

With 6.06,When I click on the run/install option in the main menu after booting from the cd, it gives the message decompressing Linux.. Loading Linux Kernel and then just hangs there doing nothing. Not only that but the only option in the main menu which actually works is the Memtest one, all others just flash a blank page and hang there.

I thought maybe the CD shipped to me was faulty so I burnt the ISO of the later version on a blank CD at the lowest possible speed setting and tried installing it. This one actually shows the Ubuntu logo with the progress bar moving back and forth for some time but then goes to a blank screen with error message saying something like "/bin/sh: cant access tty; job control turned off..." "Type 'help' to get a list of commands available".

After trying to make it work without any luck, I decided to test the newer version on VMWare and its working fine there. I aborted the install where the partitions were to be decided as I was not sure if by it will just format and install on the partition where VMWare is installed or take over all the hd space. In any case, the iso is not hanging where its doing that when trying to do a real install.

My System Config:

Core2Duo E6300
Intel P965 mobo
2 GB Ram
Primary HD 80 gb IDE Seagate (trying to install on a seperate 25 gb partition on it)
DVD RD+W Sony

Will really appreciate if someone can help me out here. I am trying to get back into linux after being away from it for more than 6 years now. The only non-windows environment I have ever used are Red Hat (before they went enterprise), Mandrake, Suse 9.1/9.2 and Solaris.


Thanks a lot.

---

### Post by logos34 on 2007-09-16
You're going to have hit F6 to add some kernel parameters/boot options.  Try 'break=top'.  Look here for more clues:

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)
[http://ubuntuforums.org/showthread.php?t=292533](http://ubuntuforums.org/showthread.php?t=292533)

I'd recommend you download 7.04 Feisty.  It might work, saving you a lot of troubleshooting time.

---

### Post by D3v on 2007-09-16
Thanks for the reply. I will go through the links and update the thread if I can make it work or get stuck at some other place.

PS: I would have downloaded 7.04 Fiesty but I don't have a net connection at home at the moment so that option is closed to me at least till I move to a new place.

---

