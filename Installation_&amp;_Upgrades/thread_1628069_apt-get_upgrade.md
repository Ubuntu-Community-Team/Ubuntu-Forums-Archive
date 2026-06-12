---
title: "apt-get upgrade"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by ChrisRob300 on 2010-11-22
Hi

I have just updated:

Linux bfs08.local.bfs.uk.com 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux                                                   

administrator@bfs08:~$ sudo su                                                  >>> /etc/sudoers: syntax error near line 29 <<<                                 >>> /etc/sudoers: syntax error near line 30 <<<                                 sudo: parse error in /etc/sudoers near line 29                                  sudo: no valid sudoers sources found, quitting                                  

can not get into root on the network.  I also can not log in as root as the master terminal.

This was all OK before I installed the latest update.  I have installed it on my 2nd server, but am not going to reboot until i have this solved.

Chris

---

### Post by sikander3786 on 2010-11-23
Hi.

There is some syntax problem in your sudoers file near line 30 as the error suggests.

You can find a default sudoers file here and replace your existing one with this.

[https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File](https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File)

The link was intended for hardy but it is the same on newer releases.

You many need to drop to root shell before editing that if you are not able to use sudo to gain root access.

To drop to root shell, press and hold down Shift key from Bios screen until you see the Grub menu. Select Recovery (should be 2nd on the list) and then drop to root shell.

Use visudo to edit the file from gnome terminal.

```
sudo visudo
```

Or from root shell

```
visudo
```

Good Luck!

---

