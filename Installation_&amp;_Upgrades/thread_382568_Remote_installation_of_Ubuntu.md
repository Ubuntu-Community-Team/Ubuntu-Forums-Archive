---
title: "Remote installation of Ubuntu"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by bigblondbear on 2007-03-12
Hi all,

I'm attempting to install Ubuntu (Edgy in this case but my question applies to all releases) remotely , ie. on a PC that I can only access via the Internet. Local (tech) help is limited to inserting a CD. I've made a bootable CD (using the great grml distribution) that starts a SSH server, sets the root password and then sits and waits for me to login. So far so good.

I've used debootstrap with the script for Edgy to install Ubuntu Edgy on the local harddisc. Grub is installed in the MBR and it all looks good. However, I imagine many (configuration) things that are normally done duing the installion from a Ubuntu CD that may not have been done yet; creation of users etc.

I am looking for the ability to kind of run the Ubuntu/Debian installer from my ssh session once debootstrap is done. I can do bits & pieces manually but that takes quite a bit of time and I can't be sure I've done everything required.

Rebooting the PC to try is only something I would do as a last resort since the PC is unattended at the moment (and I don't want to run the risk of not being able to login again once its rebooted).

Any ideas?

rgds,
Jan

---

### Post by bernied on 2007-03-12
There are a few things you can do:
- there is a [fallback option in grub](http://www.gnu.org/software/grub/manual/grub.html#Booting-fallback-systems). So I'd suggest that you create a second OS (which also includes a ssh server), installed on the hard disk to fallback to, this will be useful at other times as well, for recovery after a dirty shutdown, or other crash issues. I used a live-cd install for this, slax was my choice. You need to test this method somewhere that you have physical access first. Slax needs about 230MB of hard disk space, from memory.
- you can set the default in grub to be something other than the entry you boot. So, say your ubuntu is entry 0 and your fallback OS is entry 1, you do something like:
```
default saved

title ubuntu
root (hd0,0)
kernel blah
initrd blah
savedefault 1
fallback 1
boot

title fallback
blah blah
savedefault 0
```Initially you have to set the default to 0, there is a [grub utility](http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html) for this. You also need to check my usage of all those commands (see the grub manual I linked to earlier) and ideally check them on a system that you have physical access to.
- you can set a cron job in the ubuntu install to reboot after 30 minutes, and set the cron daemon to start nice and early in the init sequence. This way if ssh fails, the system will reboot into the fallback OS and you can go in a and troubleshoot.
- when you want to do a normal restart, you can run the grub-set-default utility as part of your shutdown scripts. This will make sure that ubuntu boots and not the fallback OS.
- it is possible to have a terminal on a serial cable. I won't go into the details as this is probably not an option - you need another computer next to the one you're trying to set up. The advantage is that you can see the entire boot process, including grub, if you have this set up correctly.

There will come a time when you need to have that cd-rom removed from the drive. You can't just eject it, it will get reinserted on startup, so someone needs to go and get it at the right moment (unless there is another way, is there?). If you can get them to hang about for another 10 minutes at that time, then you can test all the above stuff.

---

### Post by bigblondbear on 2007-03-12
Hi Bernied,

Thanks for your reply. I usually also install a recovery OS... just in case the real one gets messed up.

My main question was how to go about getting Ubuntu installed properly. Ideally, I would like to start the Installer (somehow, someway) and go thru the same questions one gets when installing directly from a CD. Or any other "automated" install/setup script that brings the system in a state as if one used the CD to install.

Any ideas?

brgds,
Jan

PS in my case I'm lucky as I can eject the CD (its a slimdrive so once out it won't pop back in :-) )

---

### Post by bernied on 2007-03-12
I don't really know. I haven't done this with ubuntu, as I think of it as being a desktop OS (it's so pretty!). I had a headless server running gentoo, and although it wasn't as inaccessible as yours (in a cupboard), it was good to learn about all that stuff. 

But, that's maybe not relevant to you...

I think you basically want the ubuntu alternate install cd with a ssh server run at startup, maybe this would not be so hard to make yourself. This exists on Debian for the arm architecture - eg. Linksys NSLU-2 (network attached storage unit, only interface is via network port) - but I don't think there is one of these for Ubuntu.

Have you seen [this](http://blog.nanorails.com/articles/2006/07/01/remote-ubuntu-dapper-drake-install) and the links in it?

---

### Post by FerGeCo on 2007-05-07
It's a bit late but i'm also looking into this and found this:

[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

---

### Post by sputnik1 on 2007-05-30
I am also looking at headless installation - in order to re-use an aging server which only has a matrix display.

I will continue to monitor this thread, thanks to all contributors ... sputnik1 :)

---

