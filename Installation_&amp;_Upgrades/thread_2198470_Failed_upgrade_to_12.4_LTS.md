---
title: "Failed upgrade to 12.4 LTS"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2014-01-08
My sister has Ubuntu running on a netbook and just had it upgrade itself to 12.4 LTS.  Now, she can log in but just gets a blank desktop with no icons or anything else.  If we move to a text console, it rejects her username and password.  At this point, is there anything we can do except a brain-wipe and reinstall?

---

### Post by ubfan1 on 2014-01-08
It sounds like a reinstall has already been done.  An upgrade should not have changed user logins, even if it messed up the desktop.  You can always boot from live media and see what's on the /home directory.  All your files should still be present if just an upgrade was done.  Back them up if necessary.  If the home directory you want is missing, well, I guess it doesn't matter if you just reinstall.

---

### Post by sideburns on 2014-01-09
The weird thing is that she can log in from the GUI, but the same username/password combo is rejected from a CLI.

Also, I'm coming from Fedora, and don't know what you can or can't do with apt-get.  Assuming that I can get in with a LiveCD and chroot to the hard disk, is there an equivalent to distro-sync, or package-cleanup that I can use?

---

### Post by mastablasta on 2014-01-09
apt-get can clean/autoremove. but it doesn't seem it's the issue here. did the update have any errors?

what is the GPU? Unity needs 3D acceleration, you might try fallback on the login screen and see if that helps.

it is difficult to say what went wrong. i would just backup all the files in home and do a fresh reinstall. you can just install over it (no need to reformat the drive) and if all goes well you will get 12.04 with all the files etc. almost like an upgrade. then you just clean the things you do not need with apt-get or with computer janitor or something like that.

on apt-get: [http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)

computer janitor: [http://manpages.ubuntu.com/manpages/lucid/man8/computer-janitor.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/computer-janitor.8.html)
the computer janitor GUI app: [https://apps.ubuntu.com/cat/applications/precise/computer-janitor-gtk/](https://apps.ubuntu.com/cat/applications/precise/computer-janitor-gtk/)

---

### Post by sideburns on 2014-01-09
The netbook was running Just Fine with Unity before the upgrade, so that's not an issue.  Also, my sister tells me that there were over 1100 packages to upgrade, and there was a message that it was only able to do a partial upgrade.  I know how to do a reinstall if I need to (and wasn't asking that) but I'd like to know how to rescue what we have if possible.  If you don't know how to rescue this, just say so because I'd expect that there'd be a lot I could do from a LiveCD, if I had the proper instructions, and that's mostly what I'm looking for.

---

### Post by mastablasta on 2014-01-09
what is the GPU?
you upgraded from which version? 11.10? how did you upgrade since normal upgrade would not be possible from old versions? EOL upgrade?

is it possible to open terminal inside GUI (ctrl-alt-t i believe)?

---

### Post by ubfan1 on 2014-01-09
I'd believe special characters in a username (like space or anything other than lower case a-z) could confuse the terminal login, but might be accepted by the GUI login.

---

### Post by sideburns on 2014-01-09
All I know is that she was offered an upgrade to 12.4 and accepted it.  (I wasn't there when it happened.)  The GPU is not relevant, because Unity worked before the upgrade.  However, her username is Marcia, with a capital M, but I'd not think that the CLI login would barf over that.  And, we haven't tried opening a terminal in the GUI, yet, because I didn't know how.  (I don't use Unity, so I'm not familiar with such things.)  Will report back later.

---

### Post by sideburns on 2014-01-09
OK.  Now, the netbook seems to autologin, which it never did before.  However, ^Alt-Del lets you log out and brings up the login window.  Yes, the username has a capital in it (which we knew) and the password works, but only in the GUI.  I wasn't able to bring up a terminal, but you'd told me that you weren't sure how to do it.

To me, this is looking more and more like the Unity config file is mung.  If I can gain access through a LiveCD, I can easily remove or rename that file.  What do I look for?  (Assume, btw, that I know how to do this; I started using Linux in the 20th Century, and I'm an old-time CLI hack.)  Just tell me what's needed and I'll figure it out.

Thanx, btw, for the pointer to apt-get info; it may come in handy getting things cleaned up.

---

### Post by mastablasta on 2014-01-10
> **sideburns said:**
>  The GPU is not relevant, because Unity worked before the upgrade. .

i am glad you think so. because if one would have GPU with proprietary drivers and those drivers didn't update/upgrade propperly it could leave desktop in a mess. since there was no further information given i will assume that the GPU and all porgrams are actually rendering fine including desktop (graphically). furthermore you may have been using unity 2D before and it now somehow switched to 3D and that maybe is not supported by GPU?! but let's leave the GPU and it's drivers alone for now.

> **sideburns said:**
> OK. Now, the netbook seems to autologin, which it never did before. However, ^Alt-Del lets you log out and brings up the login window. Yes, the username has a capital in it (which we knew) and the password works, but only in the GUI. I wasn't able to bring up a terminal, but you'd told me that you weren't sure how to do it. 
capital letters are ok.

> 
To me, this is looking more and more like the Unity config file is mung. If I can gain access through a LiveCD, I can easily remove or rename that file. What do I look for? (Assume, btw, that I know how to do this; I started using Linux in the 20th Century, and I'm an old-time CLI hack.) Just tell me what's needed and I'll figure it out.


the thing and problem here is that all versions that upgraded to 12.04 are long time EOL. so the only way one would be prompted for an upgrade would be if they changed the sources file or if they installed some PPA that would then want to do a partial upgrade. 

you would need to get into CLI first to solve this. but you say you can't login in CLI. because if you can't get to terminal then you wont' be able to do any troubleshooting or anything like that.

if you manage to get to temrinal you can try to redo the upgrade but you will need to edit sources file (since all version prior to 12.04 reached end of life):
[U][COLOR=#810081][https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[/COLOR][/U]
finnaly if all fails just do a reinstall (without formatting the disk). you will keep the data but will possibly have to reinstall the programs.
[http://askubuntu.com/questions/295933/what-to-do-upgrading-from-12-10-to-13-04-failed](http://askubuntu.com/questions/295933/what-to-do-upgrading-from-12-10-to-13-04-failed)

---

### Post by sideburns on 2014-01-10
I don't know why you're obsessing over 12.04, as I've said she upgraded to 12.4, which I'd think is an entirely different animal.  And, as far as the desktop rendering goes, the blank background renders Just Fine.

Thanx, however for confirming my belief that the capital letter in the username isn't an issue, because I've never heard of a Linux login program that couldn't handle having capitals or numbers in usernames.

Now, assuming that I can find a way to get into her home folder, what file or files do I have to remove/rename to force Unity to replace them with the defaults when she logs in?

---

### Post by mastablasta on 2014-01-10
there is no ubutnu 12.4! there are 12.04, 12.04.1, 12.04.2, 12.04.3 : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

i guess those under desktop. a way into the home folder is via liveCD/USB boot

from other posts some people had similar issue in upgrade to 12.04 and nvidia drivers are at fault. removing them completely and reinstaling seems to solve the issue.

i still suggets backing up data and installig fresh over the current install (no reformat). should keep all the data intact but backup is there just in case...

re capital letter:
actually after some reading it could be that GUI and terminal are using different way to add users.:
[http://ubuntuforums.org/showthread.php?t=1836950](http://ubuntuforums.org/showthread.php?t=1836950)


try with all letters uncapitalised or all letter capitalised. 7,8 years ago user had to be small letter only. adduser command is taking care of this in ubuntu now:
[http://askubuntu.com/questions/19455/using-capitals-in-my-username](http://askubuntu.com/questions/19455/using-capitals-in-my-username)

one thing you could do is go into recovery mode first and then change the password: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
and see if that helps you login.
if not you could rename the old user or try to create a new user with sudo rights: [http://ubuntuforums.org/showthread.php?t=2086753](http://ubuntuforums.org/showthread.php?t=2086753)

by the way recovery mode - can you get to desktop using failsafe mode?

this new user should hopefully also resolve desktop issues. then you transfer old one into new one.

---

### Post by sideburns on 2014-01-10
When we get a GUI login box, it shows the username as Marcia, which is correct, and accepts the password with no problems.  I've never before heard of Linux caring about such things, except that if you have a capitalized username, that's how you have to enter it.  Now, assuming that I can get in with recovery mode, and a quick check of /etc/passwd doesn't show anything funky, I'd like to clear out all of her desktop settings because it's almost like there's something wrong with them.  (Using failsafe mode is also a good idea, and we may try it.)  Is there, as an example a folder ~/.unity or something similar that can be nuked or renamed?  I've seen that work several times on various Fedora versions and DEs.

In case you're wondering, I'm retired, I have the time to play with this and have repaired hung upgrades on Fedora before without ever needing to reinstall from scratch, so I'd prefer at least trying it here.

---

### Post by ubfan1 on 2014-01-10
Oh the GUI login displays the name field, not the username.  Check the first field for her login in /etc/passwd, and use that to login to the terminal screen.

---

### Post by sideburns on 2014-01-10
Yeah; that was one of the things I was planning on doing.  However, we've tried both Marcia and marcia, and neither of them works, at least, so far.

---

