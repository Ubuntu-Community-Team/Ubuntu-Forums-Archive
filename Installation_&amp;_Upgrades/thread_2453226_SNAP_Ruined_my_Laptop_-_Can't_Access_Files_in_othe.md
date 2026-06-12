---
title: "SNAP Ruined my Laptop - Can't Access Files in other partitions or USB"
date: 2020-11-05
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2020-11-05
Please forgive if  not correct thread ... and please move if necessdary.  After NEW fresh install (not upgrade) to Xubuntu 20.04, can't see or copy files from one partition to another or even my thumb drive. Any idea what gives???    [edit]  Also noticed that in directory media there are the user accounts with an X overlaid on the folder icon. What does this mean and how do I correct it??? I suspect this is the problem.  Thanks! Rick

---

### Post by TheFu on 2020-11-05
Are any of the programs from snap store packages?  Snap packages only allow access to files in the user's HOME directory.  Some snap packages can be setup by the packaging team to allow other locations to be accessed, after some snap commands are run.  Only the package creation team controls this.  We users have no control.

For non-snap packages, the file system used, mount options specified, and normal Unix permissions. The file system matters greatly, so we have to know that before going any farther to help.  When the storage is connected and mounted, run **df -Th** which will show the file system for the mounted storage.  We need to see that line, please.

---

### Post by Impavidus on 2020-11-05
Did you wipe everything when you made your fresh install or did you keep some partitions? Have you used the same username? If multiple users, have they all the same name and ID (i.e., created in the same order)?

Xubuntu 20.04 doesn't come with any snaps preinstalled, but you can install them.

---

### Post by Rick St. George on 2020-11-06
> **TheFu said:**
> Are any of the programs from snap store packages?  Snap packages only allow access to files in the user's HOME directory.  Some snap packages can be setup by the packaging team to allow other locations to be accessed, after some snap commands are run.  Only the package creation team controls this.  We users have no control.  For non-snap packages, the file system used, mount options specified, and normal Unix permissions. The file system matters greatly, so we have to know that before going any farther to help.  When the storage is connected and mounted, run **df -Th** which will show the file system for the mounted storage.  We need to see that line, please.  YES, I think I remember seeing snap (I assumed synaptic) to install Opera.  As for mounting and running requested command ... that is the problem - Nothing will Mount!  Else to storage, I get the following.  
```
Filesystem     Type      Size  Used Avail Use% Mounted on 
udev           devtmpfs  2.9G     0  2.9G   0% /dev 
tmpfs          tmpfs     585M  1.6M  584M   1% /run 
/dev/sda2      ext4      217G  175G   31G  86% / 
tmpfs          tmpfs     2.9G   43M  2.9G   2% /dev/shm 
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.9G     0  2.9G   0% /sys/fs/cgroup 
/dev/loop4     squashfs   33M   33M     0 100% /snap/chromium-ffmpeg/17 
/dev/loop6     squashfs   31M   31M     0 100% /snap/snapd/9721 
/dev/loop0     squashfs  146M  146M     0 100% /snap/opera/98 
/dev/loop1     squashfs   56M   56M     0 100% /snap/core18/1932 
/dev/loop2     squashfs   98M   98M     0 100% /snap/core/10185 
/dev/loop3     squashfs  163M  163M     0 100% /snap/gnome-3-28-1804/145 
/dev/loop5     squashfs   63M   63M     0 100% /snap/gtk-common-themes/1506 
tmpfs          tmpfs     585M   16K  585M   1% /run/user/1001 
```  
BTW - Don't understand why this is not Wrapping???

---

### Post by Rick St. George on 2020-11-06
> **Impavidus said:**
> Did you wipe everything when you made your fresh install or did you keep some partitions? Have you used the same username? If multiple users, have they all the same name and ID (i.e., created in the same order)?   I did an Upgrade from a CD with downloaded ISO for Xubuntu v20.04, using same partition. Had to create users with same name to see their Home directories. Seemed to work, except ... See post to TheFu's Q.  Thanks!

---

### Post by TheFu on 2020-11-07
Cleanup. Took 10 seconds. Hard for others to help when it is too hard to read the data.

```
Filesystem     Type      Size  Used Avail Use% Mounted on 
/dev/sda2      ext4      217G  175G   31G  86% / 
/dev/loop4     squashfs   33M   33M     0 100% /snap/chromium-ffmpeg/17 
/dev/loop6     squashfs   31M   31M     0 100% /snap/snapd/9721 
/dev/loop0     squashfs  146M  146M     0 100% /snap/opera/98 
/dev/loop1     squashfs   56M   56M     0 100% /snap/core18/1932 
/dev/loop2     squashfs   98M   98M     0 100% /snap/core/10185 
/dev/loop3     squashfs  163M  163M     0 100% /snap/gnome-3-28-1804/145 
/dev/loop5     squashfs   63M   63M     0 100% /snap/gtk-common-themes/1506

```
I removed all the non-snap and real storage devices. They aren't important.  The snaps usually aren't important for storage questions either and should be removed, but since we are specifically talking about snaps, I left them in.

All those "loop" devices are snaps, so those programs will be limited to your HOME by default. The easier way to get the list of snaps is to run
```
snap list
```
I don't use gnome, so I don't know how far that being a snap impacts other programs access to non-HOME areas. 
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface) explains the removable media interfaces for some snaps.
[https://snapcraft.io/docs/snap-confinement](https://snapcraft.io/docs/snap-confinement) explains the different sorts of confinement that snaps can use.

I've had problems where snaps refused to work over remote X/11 sessions, making them next to useless for me. That's just 1 issue, NFS was problem and because our NFS HOME directories aren't mounted under /home/ snaps all broke.  Desktop computers are NOT smart phones.

---

### Post by Rick St. George on 2020-11-08
From original post, in case you missed my Edit;    >   [edit] Also noticed that in directory media there are the user accounts with an X overlaid on the folder icon. What does this mean and how do I correct it??? I suspect this is the problem.    This is not normal, but how to fix?  Furthermore, can't I just delete SNAPD and OPERA?   Output from suggested command;    
```
snap list  
Name               Version                     Rev    Tracking       Publisher        Notes  
chromium-ffmpeg    0.1                         17     latest/stable  canonical&#10003;        - 
core               16-2.47.1                   10185  latest/stable  canonical&#10003;        core 
core18             20200929                    1932   latest/stable  canonical&#10003;        base 
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  145    latest/stable  canonical&#10003;        - 
gtk-common-themes  0.1-36-gc75f853             1506   latest/stable  canonical&#10003;        - 
opera              72.0.3815.207               99     latest/stable  opera-software&#10003;   - 
snapd              2.47.1                      9721   latest/stable  canonical&#10003;       snapd   
```  
Why does this THREAD remove all my Returns ???

---

### Post by CelticWarrior on 2020-11-09
> [COLOR=#000000][INDENT]Why does this THREAD remove all my Returns ???[/INDENT]


[/COLOR]

You joined this forum in March 2010 and you have 500+ posts. One would think that you should know how to use code tags by now.

> [COLOR=#000000]Furthermore, can't I just delete SNAPD and OPERA?[/COLOR]
You can but maybe you shouldn't?
Many things came as snaps nowadays and the tendency is to have more and more. So it's better to learn about it, namely how to enable access to additional locations at /media or /mnt. By default snaps only access /home/user but any can be configured to have additional permissions. One easy way it to secrah for agiven app in the Ubuntu Software and use the permissions button. Everything from there should be self-exlanatory.

---

### Post by TheFu on 2020-11-09
Lots of people here remove all snaps and all snap infrastructure.  They make alternate selections when installing software to prevent "auto-snap-installation".  You can do the same, but there are some packages which are only provided as snaps.

If you choose to remove all snaps, do it in reverse order, then remove the snap debian package (or whatever it is called). With your experience, it should be trivial to determine.

Or learn the limitations of snaps and work within those limitations.  The 2 links already provided are what the snap guys think we need to understand.  If you treat your desktop like cell phone users treat cell phones, snaps probably aren't a big deal and things will just work.  OTOH, if you use customized certain disk locations or work in a networked, corporate, setup, then snaps are terrible and need to go away.  Many of the issues which impact corporate users have been known since 2017, yet have not been addressed.  I dream of the say when my NFS mounted home directories work with snaps at all, but I'm not holding my breath. 

Basically, snaps need to allow local control of the directories to be allowed. Until they stop hard-coding those 3 location (/home, /mnt, /media) snap confinement is broken by design.

---

### Post by grahammechanical on 2020-11-09
> Also noticed that in directory media there are the user accounts with an X overlaid on the folder icon.

The X indicates that we need to give our sudo password to open that folder/directory. I have some snaps installed but none have created a user account in the media directory. I do not have any other users on my system. I do not believe that Snaps are the problem. You should look at the properties/permissions for those other partitions. Who is the Owner? What level of Access? Can create and delete files? From the main OS that you are using make sure that the owner is me and that the access is create and delete files.

I have more than one version of Ubuntu and a Data partition and I have not had any problem accessing and working on the files in the Data partition. I do have the same user name and password for all my installs of Ubuntu.

Regards

---

### Post by Rick St. George on 2020-11-10
This is the Error I get ... 
 >  FAILED TO OPEN DIRECTORY "HOME"
 Error opening directory '/media/steve/Home' Permission Denied. 


and FYI - Permissions is greyed out, FAILED to Open Terminal, and I am the Administrator.

Note to CelticWarrior;13998852 - I have a hard RETURN after  "HOME" in the above QUOTE TAGS, unless quote tags have changed ... you are out of line. You are also out of line insulting someones intelligence in this forum. You are also out of line not paying attention to RETURN (as in the key RETURN on your keyboard) and commenting out of ignorance!

---

### Post by webaake on 2020-11-11
How to disable and remove snap/snapd:

[https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/](https://www.kevin-custer.com/blog/disabling-snaps-in-ubuntu-20-04/)

---

### Post by CelticWarrior on 2020-11-11
> [COLOR=#000000]Note to CelticWarrior;13998852 - I have a hard RETURN after "HOME" in the above QUOTE TAGS, unless quote tags have changed ... you are out of line. You are also out of line insulting someones intelligence in this forum. You are also out of line not paying attention to RETURN (as in the key RETURN on your keyboard) and commenting out of ignorance![/COLOR]

For commands output you should use CODE TAGS, not Quote Tags. Go Advanced > press "#" and paste inside.
All your previous posts have been edited by a Mod in order to fix this.
But if you think I'm "out of line" then please report the posts. They'll be dealt with appropriately and swiftly. I had no intention to insult someone else's "intelligence" and I think in this case you're "projecting" because the only insult to other people's intelligence is the thread title itself. "SNAP Ruined my laptop..." is beyond acceptable hyperbole. it's borderline FUD spreading.

And snaps have nothing to do with the permissions issue. Its presence does not change permissions and their "by design" containment doesn't affect anything else in the system but the snaps themselves. Quoting from grahammechanical - and here I use Quote Tags because it's a quote, not code - with my bold on the parts you need to understand:

> [COLOR=#000000]The X indicates that we need to give our sudo password to open that folder/directory. I have some snaps installed but none have created a user account in the media directory. I do not have any other users on my system. **I do not believe that Snaps are the problem**. **You should look at the properties/permissions for those other partitions. Who is the Owner? What level of Access? Can create and delete files?** From the main OS that you are using make sure that the owner is me and that the access is create and delete files.[/COLOR]


---

### Post by TheFu on 2020-11-11
> **TheFu said:**
> For non-snap packages, the file system used, mount options specified, and normal Unix permissions. The file system matters greatly, so we have to know that before going any farther to help.  When the storage is connected and mounted, run **df -Th** which will show the file system for the mounted storage.  We need to see that line, please.

I asked these questions.
For the storage you cannot access, please answer.

**The file system matters for permissions and for setting up permissions in the way you probably would like.**

---

### Post by Rick St. George on 2020-11-11
That's the problem Fu, refer you to post #4 and #11 above. I get the Error Msg. Cannot Open/Mount/ nor can I open Terminal Window.
Contrary to what others have said, it worked fine prior to installation of SNAP because I installed Opera Browser. That was a mistake and so is SNAP (in my humble opinion).

---

### Post by TheFu on 2020-11-11
> **Rick St. George said:**
> That's the problem Fu, refer you to post #4 and #11 above. I get the Error Msg. Cannot Open/Mount/ nor can I open Terminal Window.
Contrary to what others have said, it worked fine prior to installation of SNAP because I installed Opera Browser. That was a mistake and so is SNAP (in my humble opinion).

Ok, so let me see if I understand this.
You are trying to use some GUI program to access storage and it isn't working.  You think this is "mounting."
And you cannot open a terminal?

So ... snaps are unlikely to be involved with those issues at all.  If Opera can't write to mounted storage outside your HOME, which is very likely as that is what snap packages do by default, then it is a snap constraint issue.  

However, if you can't open a terminal, that is a completely unrelated issue to any snap problem.  Something else has been screwed up, probably by using sudo or sudo with some file manager.  That would be my 1st guess.

For all the time spent on this, I would have just wiped the system, did a new install, then restored my data, my settings, and my non-snap packages to the new system.  Be certain to format all partitions, so any permissions issues are fixed.

Before doing the wipe+reinstall, there is 1 more thing you should try.  Create a new userid using the GUI and add that user into the sudo group - add, don't replace any existing group membership.  Then logout and login as the new userid.  If you can open a terminal using that new userid, we can try and fix stuff.  But if you cannot, the problems are likely to be huge and a wipe+reinstall is the shortest way back to a working system.

Just to be clear, there are 50 other things that could be done, but I'm not really willing to work with command after command like a forensic dentist in these forums for the next 3 weeks. I've had oral surgery after a nasty accident and had to eat only liquids/soups for about 2 months. Don't need that ever again.

We will probably never know the root cause, unless it happens again.  It could be hardware failure, kernel issues, or PEBCAK or something else completely.

Really, if this was me, I would have only spent about 30 minutes troubleshooting before I'd wiped and restored from backups.  That happened in July with a 20.04 install.  I never did figure out the root cause of my non-booting system. It hasn't happened again and only happened after an update that I manually installed on that system while doing weekly patching across all my systems. All the others were fine, but it was the only 20.04 box.

Please let us know how the new userid creation goes. It may not be possible, but you won't know until you try.

---

### Post by Rick St. George on 2020-11-15
Using Thunar, clicking on partition or USB -OR- Right click, Select Mount ... FAILS. And yes I thought about a Re-installing FRESH and Wiping partition. But HOME folder is not the same. 
For example: Copied .thunderbird over to new install (on another machine) and New ThunderBird could not open or import its own files. But at least ALL personal folders (docs, music, downloads, etc) can be.

---

### Post by Rick St. George on 2020-11-16
Problem solved by choosing FORMAT partition (other) while installing from ISO extracted to CD.
Previously backed-up all Home Folders and certain other (hidden) files such as .thunderbird, .mozilla, .kdenlive etc.

Hope this helps someone. If you have problems on an Upgrade to a new version ... Backup and make a Fresh INSTALL to a partition of your choice.

---

