---
title: "clearing the decks for action by removing Grub"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by Chan on 2005-06-14
As a newbie, I've found that when you get involved with Ubuntu the first time, after working with Windows for twenty years or so, that you have to have to learn an awful lot of new terms and programs.

Two weeks ago, I tried to install Hoary and entered the usernames and passwords incorrectly during installation.  Because I don't have much experience with Bash, Nano, and Ubuntu, I just got in deeper and deeper.  I think that the best way out of this quagmire might be to just start all over again.

Question: is there any reason that I can't go back to Win XP and use the command "fdisk /mbr" to restore the master boot record,  then format the space that I had installed Ubuntu in, and then try a completely new installation of Ubuntu and Grub?  I think, at this point, I have a little better understanding of the various commands that are used in the installation.  (That stack of reference material on my desk is about to topple over, so I've got to do something soon!)

May I have a few comments, before I create another disaster?  Will what I'm proposing work, or is there another problem waiting for me?  Thanks, Chan

---

### Post by Xian on 2005-06-14
[QUOTE=Chan]Question: is there any reason that I can't go back to Win XP and use the command "fdisk /mbr" to restore the master boot record,  then format the space that I had installed Ubuntu in, and then try a completely new installation of Ubuntu and Grub?  I think, at this point, I have a little better understanding of the various commands that are used in the installation.[/QUOTE]
You can, but you can also do all of that with the Ubuntu Install CD.
You can do your partitioning & formatting during the install.

There's no need to restore the MBR and then install Grub again.
It can all be done in a one shot process.

When you install Grub it will still see Windows and set it up.
Restoring the MBR is just an added step that is not required.

---

### Post by Chan on 2005-06-14
I'll need to be able to install those pesky names and passwords.  will that be possible doing what you propose?  Thanks fr the reply, Chan

---

### Post by Xian on 2005-06-14
[QUOTE=Chan]I'll need to be able to install those pesky names and passwords.  will that be possible doing what you propose? [/QUOTE]
Heh. Sure, that won't be a problem. 

The install is just a process: 
-Load the base files
-Partition and Mount
-Load the system files
-Install the bootloader

And so on. There is no "upgrade" option so everything you do will be brand new and just as you remember it, including the opportunity to make new pesky names and passwords.

---

### Post by Chan on 2005-06-14
As to what you're proposing, shall I just stick in my Install CD, and let Ubuntu know that I want to reinstall?  It won't get nervous when all that similar data comes at it?  Chan

---

### Post by Xian on 2005-06-14
It won't know anything about "reinstalling". 
It will be every bit of a new install from scratch.

Just reformat all your linux partitions and re-set their mount points.
Install the bootloader to the MBR just like before.

Then have at it. :)

---

### Post by LittleBlue on 2005-06-14
Hello Chan:

I just did a reinstall of Ubuntu with no problems.  I used the install CD as if I never had installed Ubuntu.  I have two hard drives.  XP is on the main drive.  Ununtu is on the secondary.  I'm making a guess.  First the reinstall just partitioned and reformated the secondary hard drive from scracth.  Also, I believe the reinstall just rewrote the MBR from scratch.  I have not had problems with booting into XP after the reinstall.

Alan

---

### Post by Chan on 2005-06-14
Ok, you folks have made my day tomorrow look a lot brighter.  I'm really looking forward to trying a re-install, and continueing on the path to using Ubuntu.  Thanks a bunch, Chan  \\:D/

---

### Post by Chan on 2005-06-15
[COLOR=Red]Hooray!![/COLOR]
I finally got Ubuntu installed and working, thanks to Xian and Little Blue.  That tip of just doing another install of the the Ubuntu that I screwed up worked great!  And to think I chewed my fingernails for two  weeks, getting lost in Bash and Nano, trying to figure out how to get this beast tamed.  Well, it seems to be working now, but I can see a couple of days of adjusting a lot of parameters ahead.

Thanks for jumping in, and giving the benefit of your experiences.  Chan  \\:D/

---

