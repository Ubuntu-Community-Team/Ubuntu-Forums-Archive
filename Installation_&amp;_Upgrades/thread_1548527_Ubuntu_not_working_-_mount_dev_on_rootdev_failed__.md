---
title: "Ubuntu not working - mount /dev on /root/dev failed : no such file or directory"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by apoorvumang on 2010-08-08
Ubuntu(10.04) was working fine, then some program crashed or something, and I just switched off (power offed) the computer (sorry, shouldn't have). When I restarted it, this sort of stuff comes:
```

mount /dev on /root/dev failed : No such file or directory

```and some more lines like that, and then 'Busybox' starts with [intramfs].
I booted Ubuntu from a pen drive and ran fsck on the main partition. I just pressed 'y' for a long time (it asks stuff like should it continue repairing or something), and then it was done. I restarted the pc and it booted normally - it looked as if everything was fine.
I started google chrome, and it said it couldn't find a personal config file .. ok. Then I tried opening a folder - nothing happens. The system monitor doesn't open, and windows that do open eventually are completely blank. I restarted the pc (this time by doing the normal restart), and it gave me the same 'Busybox' thing.
I did the same procedure again, and got the same results. (ubuntu boots, programs dont work, then I restart and the Busybox thing comes again)
Why is this happening?
Please help!!

One More Thing :  The Ubuntu installed on the hard disk had all the recent updates (including the latest linux kernel) while the pen drive thing was around 2 months old I think. So maybe that's the cause? I'm completely new to Ubuntu, so I dunno anything about this.

---

### Post by tk189 on 2010-09-11
Hi,

Newbie here having the same problem as above.

I ran ubuntu 10.04 as a duel boot option alongside Windows Vista (bleuuurghhh) before deciding to go 100% ubuntu a week ago.

After installation everything was cool, got my duel monitor set up working. Got the superb AWN dock up and running, popped a few launchers onto it. Spent hours importing all my business email etc etc into Thunderbird, created the Thunderbird profile manager  thing so I can swap between several work/personal email accounts. Basically I did a load of work and everything was running fine.

Just before finishing for the day I whipped the SD card out of my camera and popped it in my card reader to check out some vids and pics. The vids wouldn't play (.mov) so rather than fart about getting codes etc i packed in for the night.

I went to bed a very happy and Windows free man.

Next day I re-booted and as mentioned by OP windows opened that were just blank grey boxes... the minimize and close buttons were there but nothing else.

Then certain apps (eg firefox, the gimp) wouldn't launch.

So, I moused up to the top to shut down or restart and got shown a blank box for that too...

Started to get a bit pi$$ed off at this point.

CTRL ALT DEL and the dialog box opened with the options shut down etc which I selected.

Re-booted and it was still all to crap and worse still nothing was opening so i had to press the restart button on the front of my tower.

Re-booted and black screen and a bunch of text ending with:
> 
mount: mounting/dev or /root/dev failed: No such file or directory

/sys on /root/sys failed: No such file or directory
/proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init

No init found Try passing init: bootarg

My system is a quad core AMD with 500GB HD and 3Gb RAM (might be 2, I can't double check from here)

From the OP post I'm not alone with this problem, anyone out there know what's happening?

---

