---
title: "failed to upgrade"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by winniwinter on 2014-10-19
Hi,
I tried to upgrade my server from ubuntu (I think) 13.04 to the latest release. Therefore I did a "do-release-upgrade". During upgrade I did a huge mistake. I used CTRL+C which threw me out of the installation. I couldn't do a do-release-upgrade again due some locks.
So I did the next mistake. I restarted. Now I'm not able to boot ubuntu. I get to the screen where it says that I can access the maintenance shell or reboot via ctr+d. 
Problem is. I cannot access the maintenance shell. The system immidiatly reboots. I also entered the recovery menu where I wanted to start the a root shell. As soon as I enter my root pw I get back to the recovery menu again. That means I'm not able to access the shell.

Do I have some other possibilities to fix this?

I would try something like this: [http://askubuntu.com/questions/361332/ubuntu-13-04-to-13-10-filesystem-check-or-mount-failed](http://askubuntu.com/questions/361332/ubuntu-13-04-to-13-10-filesystem-check-or-mount-failed)

If I could access the damn shell..

---

### Post by Bashing-om on 2014-10-19
winniwinter; Hooo Boy !

What can I say, but I will try and help.

As you surmise we MUST be able to access a terminal in order to "fix" this install.
To that end can we ?
Try:
Boot the install to the grub boot menu. With the latest kernel highlighted, press the 'e' key for edit mode -> boot options screen.
In the line 'similar" :
> 
linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff

Arrow down and across to "ro" and insert the term "text" - without the quotes and delete all other parameters you may have ;
Key combo ctl+x to continue the boot process to a textual terminal (TTY1).

IF you can get to here and login (username and password), we can proceed and see what we can do to access/salvage/release-upgrade.

For the why you are in this situation: Release 13.04 is End-Of-Life, and has no support. The software repository no longer exists as you have known it !
One would have had to change the sources.list file to redirect, 
See: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

For now we just want to see if we can access the system, maybe fix permissions/access and then effect the EOL release upgrade.

ELSE: - non raided drives - mount the filesystem(s) from a liveDVD, copy off your data, and do a clean fresh install .

You are welcome and encouraged to bounce any ideas off me in this process of think'n. All I know to do is try and see what we can do. 1st approximation is get us to a terminal !

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by winniwinter on 2014-10-19
HeeyHo,

thanks for your support. Well  the server is **alive** again and I'm dancing around it :)

Before you posted I created an live CD of ubuntu and started it. I mounted my linux partition and did steps that are described [here]("https://help.ubuntu.com/community/LiveCdRecovery")

> 
[h=2]Update Failure[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]If there was an update that made your system non-bootable and they have fixed it in the repositories, you can use the Live CD to run apt-get to get the new files to fix your system.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST=1]
[*=left]Boot the Ubuntu Live CD.[FONT=inherit][/FONT]
[*=left][FONT=inherit]Press Ctrl-Alt-F1[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount /dev/sdaX /mnt[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /dev /mnt/dev[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /proc /mnt/proc[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo mount --bind /sys /mnt/sys[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]sudo chroot /mnt[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]apt-get update[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]apt-get upgrade[/FONT]
[/LIST]


after that I rebooted and I was pretty happy to see that linux booted up again. Then I did an upgrade. And now it looks pretty good!!!

I'l added your hints on changing the grub configuration to my linux tips&tricks. thank you for that! 

good night..signing off now!

ps: next big thing on my list is to backup the server..didn't do it yet..just stupid of me

---

### Post by Bashing-om on 2014-10-19
winniwinter; Great !

If you are now up on 14.04;
Please mark this thread solved; 
aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

See it was ;
[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

