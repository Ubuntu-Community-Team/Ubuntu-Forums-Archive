---
title: "dual boot fedora and ubuntu"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by wertyuiop408 on 2008-07-02
I want to dual boot fedora and ubuntu, currently got ubuntu installed and have read that fedore becomes a bitchcos it doesnt recognise otherlinux distros

I know hardly anything about partitioning so it might take a while to understand what ur saying if you arent clear

---

### Post by wersdaluv on 2008-07-02
> **wertyuiop408 said:**
> I want to dual boot fedora and ubuntu, currently got ubuntu installed and have read that fedore becomes a bitchcos it doesnt recognise otherlinux distros

I know hardly anything about partitioning so it might take a while to understand what ur saying if you arent clear

[This is what you do.]("http://ubuntuforums.org/showthread.php?t=224351")

> **catlett said:**
> This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```
find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Finally exit the grub shell
```
quit
```

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a  small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition,  grub will use the mbr. hd0 is the  grub label for the first drive's mbr.
Quit will exit you from the grub shell.



[COLOR="Red"]THIS IS AN EDIT. 5-HT MADE A GOOD POINT AND I AM JUST GOING TO COPY/PASTE IT HERE
[/COLOR]


[COLOR="Red"]THIS IS ANOTHER EDIT. TOSK POSTED A WAY TO MOUNT PROC AND UDEV. THIS WAS NEEDED BECAUSE GRUB WASN'T RECOGNISING THE DRIVE. I THOUGHT IT WAS A VALUABLE COMMENT AND DECIDED TO PUT IT IN THE ORIGINAL POST SO PEOPLE WILL SEE IT AT THE TOP. IT MAY BE MISSED AS JUST A REPLY POST DOWN THE PAGE. 
ALL KNOWLEDGE IS WELCOME![/COLOR]





**This set of instruction is a combination of 2 guides I saw before. One was a Mepis grub how to but I never found it again. The other is the grub manual. It's section explained the find, root, setup process but never mentioned it could be done from a live session.

This is the grub link [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

[COLOR="DeepSkyBlue"]Post script;
Just to post as much information as possible, this is an older how to for resoring grub to the mbr. The original post is directions for using the install cd and then there are replies that mention the method I posted here, as well as the chroot method mlind mentioned. If this method fails, you may want to try this [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)[/COLOR]



Good luck. :)

---

