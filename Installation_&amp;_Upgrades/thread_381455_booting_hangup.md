---
title: "booting hangup?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Axehammer on 2007-03-10
Greetings, 

I have run across a small hassle with my wife's new notebook

She recently purchased an acer aspire 5610, and had me install Ubuntu for her.
The system seems to hang up when booting.  the graphical screen gets about 40% and then holds for about 20 seconds, the screen switches to text with a message about checking the file systems, then stops.  I thought that it may have been aglitch on the install, so I hit ctrl-alt-del to reboot to the set-up screen, and run the insaller again.  there were two kill messages, then the login screen popped up.  everything after that went as usual.  

are there any tricks to find exactly what is causing the hang-up?  and how can I make sure that it dosen't do this again?

Thanks for your help, sorry that I couldn't get accurate kill messages, they dissapeared too quickly to read them.

---

### Post by Herman on 2007-03-11
Hello Axehammer,
Welcome to Ubuntu Web Forums! :) I notice this is your first post!
> The system seems to hang up when booting. the graphical screen gets about 40% and then holds for about 20 seconds, the screen switches to text with a message about checking the file systems, then stops.If you have an ext3 filesystem and it is running an automatic filesystem check, you normally see a type of progress bar, like a tumbling bar leading a row of '=' signs from left to right across the monitor. When that happens of course, we just wait until it's finished and the computer usually will boot up the rest of the way as per normal. They do that once every thirty boot-ups, or if the computer was shut down wrong, (by the 'off' button or by being unplugged or the like).
Link here:                   [Automatic filesystem checks on bootup]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_checks_on_bootup")
It you have a reiserfs file system it may not show any signs of activity but maybe the hard drive led will be flashing while the filesystem check is being done. It is best to be patient and wait a while for this check to complete, as it is important.

These are not the same as a scandisk or a defrag in Windows, because the Linux filesystems work a completely different way to your Windows filesystems.
However, to most ordinary folks, it seems quite similar, you wait a few minutes while something is done for you on your hard disk and after that our computer works better.

Usually if there is a problem, an error message will be displayed. After taking note of this error message you can normally press 'ctrl' +'d' to continue booting.
>  are there any tricks to find exactly what is causing the hang-up? Getting the exact error messages would be ideal, but since in your case they flash by too quick maybe that's impossible. Maybe nothing's really wrong anyway, maybe it was just a regular filesystem check.



If you have an ext3 filesystem you can run your filesystem checks manually from a live CD. You need to know which partition it is you want checked. Look at your partitions with GParted or do 'sudo fdisk -lu' ```
sudo fdisk -lu
```Then according to which ext3 filesystem partition you want to check, apply a command like this, ```
sudo e2fsck -C0 -p -f -v /dev/hda2
```(Where hda2 is the partition to be checked. Replace with whatever partition number is appropriate)


If you have reiserfs, use this command,```
sudo reiserfsck --check --logfile check.log /dev/hda2
```(Where hda2 is the partition to be checked. Replace with whatever partition number is appropriate)
This runs a quick check (takes a look around), and tells you if anything is wrong. It doesn't fix anything. This is a safe command for new users. If it reports back that something needs fixing, you need to run reiserfsck again with the **--fix-fixable **option. Ask for more help if you need to do anything more than that, (unlikely).

My wife and I have an Acer Aspire T300 desktop each  and an Acer Aspire  laptop each as well. We have a couple of other Acers in the house. They all run Ubuntu really well.

Does it seem as if I'm understanding your problem correctly, or am I 'barking up the wrong tree'?

Regards, Herman :)

---

### Post by Axehammer on 2007-03-13
Thanks, seems it is booting just fine now.

only hassle left is to change the screen resolution.  she tried, but there was only one resolution to pick from, 1200x720?  where the monitor is listed at 1280x800.  otherwise she loves it now.

I recommended Acer to her because I had purchased an Aspire 1800 about two years ago, and have loved it.  My system is a dual boot, partly because it is the first computer I have tried linux on.  Hers is now a Ubuntu only machine, as she was playing with the Vista in the store, and was getting frustrated with how slow everything was running.  the salesman let me pop a Ubuntu disk in to see how well it would configure.  I got a quite a few weird looks from people walking by and looking. :)  but she was much happier with the speed, even running off a cd.

Ken

---

### Post by Herman on 2007-03-13
Hello Axehammer,
About the video resolution, you could try running               [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") and let Ubuntu re-detect your hardware agan automatically,see the link I just gave you for details. Otherwise you should start a new thread with an appropriate heading and you might get someone who's more of an expert on that subject than I am.

My mother called me the other night, she has been allowed some money from her employer to buy herself a nice laptop for her job. She's going to install Ubuntu in it too. She doesn't want Windows and all the adware, spyware and viral hassles that go with it. Ubuntu is much better. I advised her to get an Acer. 

Ubuntu is getting well known in my town, more and more people are switching to it.  Here's a link where you can find some nice videos, they help prospective new users interested and off to the right start,[**ubuntuclips.org** | video howtos for human beings.]("http://ubuntuclips.org/")
They're great, I hope they keep on making more of those. 
:guitar:
Regards, Herman

---

