---
title: "Breezy to Dapper upgrade breaks"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by canonical-user on 2006-06-21
I upgraded breezy to dapper using the gui installer on a pentium system.
I got no errors on the upgrade process, but the new kernel it picked from th e update had PCMCIA enabled and now the system hangs in

STARTING PCMCIA SERVICES

It hangs there, there is no PCMCIA controller, this is not a laptop.


Any help appreciated.

---

### Post by canonical-user on 2006-06-21
The recovery mode also goes up to the PCMCIA services and hangs there for ever. So basically i have a non usable system.

---

### Post by canonical-user on 2006-06-21
A non usable system and a deadline thats moving closer and closer.
And all my work is there. :( 

Somebody please? ](*,)

---

### Post by CarpKing on 2006-06-21
On grub can you select a previous kernal?  That sort of worked for me- got me into a dapper gui with some stuff broken.  I then got my data the hell out of there though.  Haven't solved the problem yet though.

---

### Post by bodhi.zazen on 2006-06-22
This seems to be a serrious flaw with Ubuntu. This is the third post in the last week.

No solution has yet been identified to the problem.

See the following two posts:

[http://www.ubuntuforums.org/showthread.php?t=191477](http://www.ubuntuforums.org/showthread.php?t=191477)

[http://www.ubuntuforums.org/showthread.php?t=199549](http://www.ubuntuforums.org/showthread.php?t=199549)

Your system, like mine, is likely beyound any rapid repair and may never be repaired. Thus, at this point, with a looming deadline, your only option is to BOOT TO A RESCUE CD, COPY YOUR DATA, AND MIGRATE TO A WORKING OS.

Could someone please advise further??????

---

### Post by Daniel Ibrahim on 2006-06-22
[QUOTE=bodhi.zazen]Your system, like mine, is likely beyound any rapid repair and may never be repaired. Thus, at this point, with a looming deadline, your only option is to BOOT TO A RESCUE CD, COPY YOUR DATA, AND MIGRATE TO A WORKING OS.

Could someone please advise further??????[/QUOTE]

Please don't give this kind of advice,  it is nonsense, this is a fix described if you just read the common upgrading instructions on
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

It is quickly done, you can either do it with the Original Disk or with recovery system. (just read this site above and then try it out)

Mr bodhi.zazen: do not give this kind of advice, especially not in a SHOUTING tone, better meditate on this.. ;) 

Be polite and give good information or you will be seen as someone who doesn't have a clue and gives bad advice.

For both of you: read the instructions in the beginning of the forums so you will save yourself a lot of trouble.

And be cool 8-)  because a GNU/linux system is never completely lost, that is why we are using GNU/Linux, even Ubuntu is still Linux in it's heart...

---

### Post by Daniel Ibrahim on 2006-06-22
[QUOTE=Daniel Ibrahim]It is quickly done, you can either do it with the Original Disk or with recovery system. (just read this site above and then try it out)
...
And be cool 8-)  because a GNU/linux system is never completely lost, that is why we are using GNU/Linux, even Ubuntu is still Linux in it's heart...[/QUOTE]

If your deadline allows for ten to twenty minutes you can do this fix. If you haven't got the time, don't worry, just use a bootable CD (like Knoppix or the Ubuntu Live CD if you have it) and boot your system, mount your harddrives and finish your work, you can do the system recovery after that.

you can get the bootable disk here:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

---

### Post by bodhi.zazen on 2006-06-22
Daniel:

As you can see from my posts my Ubuntu system has failed and is unusable.

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) is a general guide and does not address a single issue in my post.

From the site itself
" 
      Make sure you type  dist-upgrade  rather than  upgrade , because  upgrade  will totally hose your machine and render it completely unbootable. (Why? This warning would have a lot more impact if someone could explain it!)

"

It seems my system is totally hosed and canonical-user seems to have the same predicement. Any distro that will corrutp a system to this magnitude is, in my opinion, unstable. [as you say in yor post it is rare for this to occurr with Linux, but wake up and smell the roses, it is happening in Ubuntu right now. You should work to fix the problem and not ignore it and tell useres they will be OK with a 20 minute fix]

Your post does not not contain a solution to my problem, let alone a 20 minute fix.

You should not advise a person with a deadline that a problem of this magnitude can be solved in 20 minutes unless you have a very good understanding of the problem.

If you have a solution to my problem I would be eternally grateful, otherwise do not advise people they have a problem that can be fixed in 20 minutes.

---

### Post by rcarring on 2006-06-22
A suggestion:

if the data on your hard disk is not corrupted then you may be able to boot up with PuppyLinux 2.01, this of course makes the assumption that you have another machine around that can download the iso image and burn it to cd.

If I was in your situation...

I would boot with Puppy, mount the partition that I need to access and then delete the file in the rcS.d folder that loads pcmcia services. When the system boots it won't try to load these services and that may allow you then to get to either a command line or the desktop.

The Puppy download is about 75mb using the Seamonkey version.

---

### Post by canonical-user on 2006-06-23
rcarring many thanks for your insight. Many thanks to the rest of the users for trying to help me. The recovery kernel from grub halted at the same PCMCIA services loading part.

Before seeing rcarring's post and with the deadline close i realised i didnt have much to lose so i booted a small rescue cd with busybox i put together some moons ago.
Mounted my drive on it, navigated to the rc scripts dir, grep'd for pcmcia and deleted the startup scripts.

On reboot i had my system back fully functional. 

Many thanks to all of you. Hope those lines help another user

---

