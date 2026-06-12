---
title: "System Crash: No commands anymore! Difference between recovery &amp; common boot mode"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by tsteuerwald on 2005-08-19
Hi all,

I use Ubuntu Hoary Hedgehog. Yesterday I just compiled something with
```
sudo checkinstall
``` inside a gnome terminal and aborted via ctrl+c after this I tried it again wie sudo checkinstall, then it appeared "sudo command not found" (or similar) on the console. After this I tried to change the current directory and typed ```
cd /
``` and then got the same answer  "cd command not found".
After this, I thought it would be a good idea to start a new terminal and clicked on the gnome terminal symbol. May be you can already imagine, gnome said 
"command terminal not found".  ](*,) 
Straight after this, all icons on the desktop and the "quickstart icons" (don't know how it is called in gnome, is it "gnome-applet"???)  disappeared and were replaced by a red "X". Also the  "start menu" had also no icons any longer.  :shock: 
Now I thought, may be it is a nasty kernel problem. So i started the computer again, but I got no graphical login and beyond that, a few failures during startup:
```
art-stop-daemon: Unable to start /sbin/klogd: Permission denied [fail]
Startubg GNOME Display Manager [fail]
Starting deferred execution scheduler [fail]
```If I want to login on the command line it says (after the copyright and warranty remarks of ubuntu)
```
No mail.
Unable to cd to "/home/timo"
```I'm not sure if it means, that it can't find the cd command or if it means that "/home/timo" doesn't exist.
The interesting point is, that if I now boot via the recovery entry in the boot menu, I can access the hard drive and /home/timo - as IMHO everything else -  exists. 

My question now is what can that be? How does the recovery mode differs from the common mode? - I had a look in /boot/grub/menu.lst and have seen that both entries use the same kernel. So what makes the difference? - May be if I know that, I can better track down the problem.

Another question is how can I increase the trace level of the processes that will be started during the system boot?

Because the harddisk is from maxtor (Maxtor 6Y20L0) I already tried the tool powermax from their homepage. It reports no problems. So I think the source for this problem is not the harddisk itself.
My tip is that the problem is caused by the bios and the recovery mode handles the bios settings in another way as the common boot mode, but this must be proven...

Please help, this is really urgent!  :-? 

Cheers,

Timo

---

### Post by tsteuerwald on 2005-08-19
Ok, I found the source of this problem myself. The rights for the "/"-directory were changed. So, users can't read or execute anything. After ```
chmod 755 /
``` everything works again.

See also [http://linuxfromscratch.org/pipermail/lfs-dev/2001-July/016455.html](http://linuxfromscratch.org/pipermail/lfs-dev/2001-July/016455.html) or for german language speakers [http://lists.debian.org/debian-user-de/2001/10/msg00665.html](http://lists.debian.org/debian-user-de/2001/10/msg00665.html) 

Cheers,

Timo

---

### Post by iheartorcs on 2008-05-27
If someone could offer some support I would be greatly appreciative. This is my exact problem, but being the Ubuntu noob that I am I don't know exactly how to chmod 755 to /.

I booted up in the recovery console and put that in but nothing seemed to happen. Still get the same error: Unable to start /sbin/klogd: Permission denied [fail], so if someone could explain how to do this that would help.

Thanks!

---

