---
title: "install over mandriva"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by tnc on 2007-08-05
Hello.  I don't think am posting an old topic.  Aplogies if I have.
Here is our problem:
We are installing over mandriva, which in itself isn't a problem.  We installed and can boot to login screen.  However, when we log in, we are told that gdm (I think) can not access the $home/.drmc configuration file.  Permissions were wrong and needed to be 644.  We changed that but then we get a complaint about access to $home/.gnome2_private/'.  We changed those permissions but then get complaints that permissions are incorrect on the home folder.
In the end we cannot boot into gnome.  That is the limit of my knowledge.
we have:  P4 1700 with 500mb ram.  
Thanks for your help.
Tim
P.S. Can we download full feature ISO's?  We have the "live CD" right now.

---

### Post by Pumalite on 2007-08-05
You'd be better off with Alternate Ubuntu CD. You have more control and at the end you end up with the same system

---

### Post by JudasReanimated on 2007-08-05
I would personally reformat the HD, and then install from scratch. I'm not sure what caused that error, but that may fix the issue. 

Also you can download the text based installer (I believe that's what you requested) from here. [http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=)

Check the box for text based.

Hope that helped, Adios.

---

### Post by MrFSL on 2007-08-05
So you had a seperate /home partition that you kept right?
And after installing Ubuntu you have permission issues with this /home partition. Specifically with your home folder?

---

### Post by tnc on 2007-08-06
Wow!  Thanks for your replies.  I sure hope we can set this thing too rights.

Pumalite:  I will look into the alternate CD.  Would you happen to have link handy?  Is Ubunto installed strictly off one CD and network (like this CD?) or is a complete OS available on CD?

JudasReanimated: We absolutely do not want to format the /home drive.  We have 5 years worth of stuff on there.  We back up to CD but formatting /home and reinstalling our stuff would present the identical problem in a different format i.e. permissions.  Correcting the present problem is part of the learning experience.  I will check out you link.  Thanks.

MrFSL:  You are correct.  /home is on a physically separate drive and we did indeed keep it.  The error messages are actual.  I opened up the home folder permissions to allow the program to write to /.gnome2_private/' but then ubuntu or gdm complained that the home folder permissions are not as they should be; which I would agree with.  I'm thinking that gdm has to be added as group user to that specific folder?  However, I don't know how to do that via terminal.

Thanks all.
Tim

---

### Post by tnc on 2007-08-06
Another idea: reinstall with new/formatted home folder and then install our stuff into the new home folder.  My concern is that I will have the same permissions problems.  
Input on that idea?
Thanks.
Tim

---

### Post by JudasReanimated on 2007-08-06
What exactly are you trying to have write to folder? I'm sort've confused to your problem exactly. What I was suggesting was exactly what your last post stated as an option.

Could you be more specific, like exactly what you did in steps and what the error was, as well as when it occured.?

---

### Post by tnc on 2007-08-07
Ok, we are not trying to write anything anywhere.  When we attempt to log in (to desktop) on our box, we get the error messages I posted.  Those error messages are actual, word for word.  Bear in mind, this is an install over mandriva using the original home folder.  My best bet is that permissions and/or groups is set up differently between Ubuntu and Mandriva.
As for the reinstall: Probably will be the simplest option.  However, the permissions problem will just become that we will not be allowed to access our own stuff.  Thoughts?
Tim

---

### Post by tnc on 2007-08-09
Ok.  Well.  So we gave up and reinstalled  in the true winblows way.   Would have preferred to figure out what went wrong so that we, and maybe others, could learn but.....yeah, we wimped out.  Reinstalled with a new home folder and the put our stuff back in.  No problem.  Everything works.

All in all, we are very impressed and happy with Ubuntu so far.  Kudos to all who put in the hard work to make Ubunto what is is.
Tim

---

### Post by MrFSL on 2007-08-11
@tnc 
Sorry about not getting back to you. 

Here are a few concepts that might help next time.

You CAN install Ubuntu over another *nix OS while keeping your old /home partition.
The first problem that you might get into is with file/directory permissions. Even if you have the same username and password as you had on your previous install, it does NOT mean you have the same User ID number (UID) or groups etc. (GID) You can check out this information by typing:
```
id
```
Now... to get around this issue you can boot into safe/recovery/single mode when Ubuntu starts (this should give you leave you at a terminal as the root user. From here you can change all the permissions and ownerships of your old files by typing:
```
chown -R <username>:<groupname> /home/<username/*
```
Here you would substitute '<username>' and '<groupname>' appropriately. For example, my username and groupname are 'fsl':
```
chown -R fsl:fsl /home/fsl/*
```

The next problem has to do with startup files and configuration files. These are usually stored as hidden files (prefixed by a period) in a users home directory. If your new Linux OS does not have the same software installed as the old one, or if the software is a different version, or the software is located is a different place, -- you can have obvious problems. Before you install a new OS like Ubuntu, it can be important to identify which configuration files you need to keep. I keep mine for my email and IM and that is about it. You'll want the new configuration files created or supplied by the Ubuntu installation. (Which might happen during install as long as you mount your old root partiton... I'm not sure how the installer would handle this.)

Personally I would do the following:
1) Install Ubuntu but do NOT mount the /home partition. Instead have /home be a regular folder created under '/'
2) Backup the configuration files you need from you old home directory. Delete all the rest perhaps with a:
```
sudo rm -rf /media/oldHome/<username>/\.*
```
3) Change the ownership of the existing Old Home files/folders:
```
sudo chown -R <username>:<username> /media/oldHome/<username>/*
```
4) Reboot into recovery/single user mode and copy all of the new config files to the old home partition:
```
cp -a /home/<username>/* /media/oldHome/<username>/
```
5) Edit /etc/fstab to reflect that your old home partition should be now your current home partition.
6) Reboot

I know this is short and perhaps confusing but I hope it helps next time.

---

### Post by tnc on 2007-08-11
MrFSL, 
 Thank-you very much!   That is exactly the info we were looking for.  We had somewhat the right idea but were heading in the wrong direction; never even thought about the UID/GID.
We will be installing Ubunto on a friend's box shortly.  He is running the identical Mandriva so  we will apply your ideas and post the results back here.
Thanks!
Tim

P.S. Thanks to all contributers on these forums.  We have learned so much here.  KUDOS.

---

### Post by tnc on 2007-08-15
MrFSL and others:
We went ahead and installed Ubuntu on my friends computer using the alternative installation cd.  At first boot up we encountered exactly the same errors as with our computer.   We used the commands suggested above:

$ id
$ sudo chown -R user:group /home/user

This worked flawlessly.  Gnome had been used on this computer before so Ubuntu Gnome picked up the configuration and the desktop showed up in the expected manner.
Totally excellent!
Thank-you MrFSL.
Tim

---

### Post by MrFSL on 2007-08-15
I am so glad that everything worked for you!

---

