---
title: "Something's gone awry at install-land"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2011-06-21
I have a friend who has a netbook. An HP mini.  It comes with Windows starter edition.  He can't stand Windows.  I installed Ubuntu 11.04 with the classic gnome interface.  As he was working with it it became apparent that his thumbs are lazy and as he typed his thumbs would touch the touchpad thus making the mouse cursor jump to other places.  Needless to say this is very annoying.  I looked up about how to resolve this, but it appears that there are issues with HP netbooks (at least the HP Pro).  Anyway, it does appear that the solutions to this issue are resolved with the touch pad patch.

After reading some web pages there appeared to be an option in Kubuntu that allowed you to specify that the touchpad be turned off as you type.  Two seconds after you stop pressing a key it is supposed to turn the trackpad back on.

My choice at this point was to install Kubuntu-desktop.  About 90% though I received some warnings that there was an issue with the crypt and file system.  The computer locked.  I had to force it off.  SSH into the box was refused (whereas earlier it was working find)--meaning that the service just wasn't responding--hence I know the computer was locked.

After rebooting all I could get when attemping to boot into Linux was a grub command.  No menus, nothing.  Now I don't have forever to work through these problems.  So, I decided to boot with the LIVE-CD only to find more difficulty in having it see the wubi install (obviously, as it is using a virtual file system).  My choice at this point was to start the install over only this time I was going to install a full verison along side Windows.  The problem is that there's a limit on the number of partitions on the device (limited to 4) and the HP Mini partition structure as put in place by HP utilized all 4. 

I went looking for a solution to this only to find that someone had found an answer to his similar problem (of the limit of 4 partitions) except he didn't explain how he solved it.  After a  request he did fill in with some detail on how he did it.  I chose not to go that route, instead going back to the wubi install.

I downloaded wubi, executed it, selected the max disk space, and the Kubuntu install type.  I gave it the necessary passwords and let it continue.  All seemed to go well, except when I did get to the desktop there was some horribly aweful looking and less than easy to use version of Unity for Kubuntu.  I found that I couldn't even locate a terminal in order to execute commands.  It was far too easy to confuse me.  I concluded this would NOT be a good fit for my friend.  At this point I logged out hoping that there was Kubuntu classic option.  There wasn't.  I looked through system settings.  Nothing that I could see would permit me to switch this back to the normal plasma desktop with folder view.

At that point I decided to uninstall Ubuntu via wubi and reinstall it again with the flat out Ubuntu install because I know it has the option for a classic gnome.

As you can see I had many problems and this tells me that whatever changes from the philosophical ideas to the implementation have gone awry.  Something isn't right.  Users are being corralled into using something they might not like nor want.

So, to recap:

1) Mouse trackpad issue leads to locating software to turn it off during the time the keyboard is being used in an effort to keep the mouse from jumping all over the place.

2) The software doesn't appear to function and further investigation leads to references to where KDE apparently has an option under input devices and then hardware to turn off the touchpad while typing, so kubuntu-desktop was installed (or rather an attempt), which resulted in a hard lock of the computer and a subsequent reboot that only gave grub prompt at boot.  The find command didn't work, BTW.

3) Force to remove the old install and reinstall Ubuntu only this time with Kubuntu as the default desktop resulted in a HORRIBLY awful Unity like interface.  The ease of use features were sorely lacking, it was confusing, basic obvious features were missing, and it was deemed to be a non-functional desktop (to me).

4) Reinstall of Ubuntu desktop with the classic gnome.

This is very annoying and it would be nice if anyone could address these issues, such as how to get back the default grub, why kubuntu-desktop warned and then locked, how to get the default desktop version of the folder view of KDE without having to reinstall the whole thing, etc.

My frustration level is high on this one.  Any help would be appreciated and I thank you in advance.

---

