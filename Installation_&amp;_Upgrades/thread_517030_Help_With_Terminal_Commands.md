---
title: "Help With Terminal Commands"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by CurtZX on 2007-08-04
Hey Folks.

hope one of you can help me here... I am one of the crazies that is trying to get MAC OS X to work on this laptop here but I am having problems with ubuntu... 

The instructions to get tiger on this system were to load ubuntu, copy tiger-x86-flat.img to an external drive, then run the terminal program through ubuntu to navigate to the external drive and copy the image (using a code provided)

WELL... This is my first experience with linux and I am lost as lost can be..

I have got some instructions off the net to change my 'su' to a root user so ive tried that... ive tried just typing in the command, but I cant seem to find my drive!

I have been typing in /dev/sdb1 and getting 'permission denied' messages.. I cant even find the /dev/hda1 drive without getting the same error...  I cant 'cd' to clear the directories or anything it seems..

I know this must be a simple solution, but I am sure I must have something locked down which would explain why I cant access my drives..

Any help is greatly appreciated!!!!!

---

### Post by CurtZX on 2007-08-04
bump!

---

### Post by ike on 2007-08-04
> **CurtZX said:**
> I have been typing in /dev/sdb1 and getting 'permission denied' messages.. I cant even find the /dev/hda1 drive without getting the same error...  I cant 'cd' to clear the directories or anything it seems..

Well, you're not supposed to access /dev/hda1 directly. You should mount it to a folder somewhere in your filesystem first. Maybe that's why you get the permission error? /dev/hda1 is probably mounted somewhere already, you can write "mount" in a terminal to see where it is mounted.

What does mount tell you?

---

### Post by CurtZX on 2007-08-04
I am just trying to do this

**[http://uneasysilence.com/os-x-proven-hacked-and-running-on-an-ordinary-pc/](http://uneasysilence.com/os-x-proven-hacked-and-running-on-an-ordinary-pc/)**

You can see they ust tell you to cd to the directory (/dev/yourdrivesvolumename) and then type in the command..

Really there is nothing about 'mounting' and I have no idea how in the world to do that :):lolflag:

---

### Post by CurtZX on 2007-08-04
here is what happened when i typed 'mount hda1' which I think is what you're saying?  Remember, you have to really put your answers in laymans terms for me, I am not used to any linux platform whatsoever

mount: can't find hda1 in /etc/fstab or /etc/mtab

---

### Post by aysiu on 2007-08-04
> **CurtZX said:**
> Hey Folks.

hope one of you can help me here... **I am one of the crazies that is trying to get MAC OS X to work on this laptop** here but I am having problems with ubuntu... 

The instructions to get tiger on this system were to load ubuntu, copy tiger-x86-flat.img to an external drive, then run the terminal program through ubuntu to navigate to the external drive and copy the image (using a code provided) I'm sorry, but what you're describing is illegal, and thus isn't appropriate for the Ubuntu Forums.

---

