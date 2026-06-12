---
title: "Ubuntu 7 Server Install with base Xorg"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by bensode on 2007-06-11
Found an unusual problem when installing Ubuntu 7 server.  I install the base ubuntu 7 system then apt-get dist-upgrade to get current updates.  Then I run the following after rebooting with latest kernel:

apt-get install xorg

Testing the Xorg setup, I run startx and I get the Xserver up with an xterm session; works as expected.  Once I exit the X session with either ctrl-d or exit command, the screen flickers, goes black, then becomes unresponsive.

I am not able to login to either of the alternate consoles but a ctrl-alt-del restarts clean and brings me back to normal.  I installed openssh-server, then ran startx again and now displays a blank screen and remains unresponsive.  I ssh in from my workstation and see that the Xserver has started and an xterm process that looks like:


bensode   4328  4322  0 05:59 tty1     00:00:00 xterm -class UXTerm -title uxterm -u8

If I kill this process, I get my console back but now X is useless even after reboots.  Any suggestions?  I can duplicate this on the same system by repeating the entire installation.  The system is a Dell Optiplex 745 with an Intel integrated video card.  I'd like to point out that this system was my Ubuntu 6 LTS Desktop for a while and I had not experienced any of these problems under the desktop installation and was wondering what magic packages I was missing from desktop to server install ...

Bensode

Edit: If I let the blank screen sit, it continuously kills the xterm session and starts a new one with a new PID.  Thought that was odd.

root      **4730**  4289  0 06:11 pts/0    00:00:00 grep xterm

(wait about 30 seconds)

root      **4732**  4289  0 06:12 pts/0    00:00:00 grep xterm

(another short wait)

root      **4736**  4289  0 06:13 pts/0    00:00:00 grep xterm

---

### Post by bensode on 2007-06-11
Ok this only happens when I run startx from root.  My user account does not experience this problem and starts, exits, restarts just fine.  Is there something I am missing to get root to run X reliably?

---

