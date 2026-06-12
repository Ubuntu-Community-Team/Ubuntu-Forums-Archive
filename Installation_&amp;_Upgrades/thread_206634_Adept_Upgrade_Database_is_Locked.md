---
title: "Adept Upgrade Database is Locked"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2006-06-30
My system informed my that there were upgrades available, so I opened up the package manager.  Immediately after entering my administrator password, the following message appeared:
> 
You will not be able to change your system settings in any way(install, remove, or upgrade software), because another process is using the packaging system database (probably another Adept application or apt-get or aptitude).  Please close the other application before using this one.


Problem is, I don't HAVE any other applications running at all, as far as I can tell.  I'm not a terminal wiz, so I don't know what I shoudl do to see if any other process is running and stop it.  Any advice?

---

### Post by thingy on 2006-06-30
Well if you don't have anything else running, can you tell us whether rebooting your box gets rid of this. If it does, then you did have something running and if it doesn't then its a stale lock file issue. In which case: 

sudo rm /var/lib/dpkg/lock

---

### Post by llanitedave on 2006-06-30
Neither one worked.  First I rebooted.  Same problem.  Then I did the command you suggested in terminal.  Same problem.  Then I rebooted again.  No joy.

How do I get  a list of running programs, so I can see if there's something that's getting activated on boot that shouldn't?

---

### Post by thingy on 2006-06-30
Try a: "sudo dpkg --configure -a"

---

### Post by llanitedave on 2006-07-01
OK, I tried it, and among the other 'Setting up' messages, it gave me this one:

Setting up apt-build (0.12.17) ...
mkdir: `': No such file or directory
dpkg: error processing apt-build (--configure):
 subprocess post-installation script returned error exit status 1

Am I going to have to reinstall something?

---

### Post by llanitedave on 2006-07-01
bump

---

### Post by rlklee on 2006-07-01
I am having the exact same problem.  Very annoying.

---

### Post by llanitedave on 2006-07-01
The annoying part is that it worked originally.  I did an update for software only a week ago, and it worked fine.  Something has happened since, possibly some corrupted data or file.

---

### Post by rlklee on 2006-07-01
"sudo dpkg --configure -a"  worked just dandy for me.

---

### Post by llanitedave on 2006-07-01
Our problems must be different, then. I'm going to try something drastic.

---

### Post by thingy on 2006-07-02
Dave,

1. Silly question but can you just confirm that you're not double clicking the Gnome panel/system tray icon for the package manager or double clicking the menu item for it and hence launching two copies of it?

2. Can you show us the output of "ps -a" when you've got that error message on the screen.

3. After having got rid of the message, can then launch a term and type in "sudo apt-get update" and paste the output of that as well. I'm asking because of this thread:

[http://ubuntuforums.org/showthread.php?t=192053&highlight=process+packaging+system+database](http://ubuntuforums.org/showthread.php?t=192053&highlight=process+packaging+system+database)

regards

jin

---

### Post by llanitedave on 2006-07-02
Odd...  A somewhat different problem now.  I typed 'ps -a' into the terminal before following your other directions.  

Here's the output:
```

dave@linuxDesktopAMD:~$ ps -a
  PID TTY          TIME CMD
 6233 pts/1    00:00:00 ps

```

Then I repeated the command you suggested a couple of days ago:
```

'sudo dpkg --configure -a'

```
I got the same error message that it returned originally.  THEN I went to the system menu (I'm in KDE, not Gnome) and selected "package manager".  Lo and behold, the error box I posted about originally did NOT appear, and Adept appeared on the screen with all update options activated, as they should be.  However, when I ran the updates, the process exited with an error -- after the download phase, during the package installation phase.  The mesage says it was unable to commit changes.

Then, in the terminal, as you suggested, I typed 'sudo apt-get update'.  It opened the repositories and downloaded files, then supplied the following message:

```

'Fetched 76.1kB in 8s (9295B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'

```
I did it again:
```

dave@linuxDesktopAMD:~$ sudo dpkg --configure -a
Setting up apt-build (0.12.17) ...
mkdir: `': No such file or directory
dpkg: error processing apt-build (--configure):
 subprocess post-installation script returned error exit status 1
Setting up acpi-support (0.85) ...
 * Checking battery state...                                             [ ok ]

Setting up libgtk2.0-common (2.8.18-0ubuntu2) ...
Setting up libgtk2.0-0 (2.8.18-0ubuntu2) ...

Setting up libgtk2.0-bin (2.8.18-0ubuntu2) ...
Updating the IM modules list for GTK+-2.4.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.4.0...done.

Errors were encountered while processing:
 apt-build
dave@linuxDesktopAMD:~$  

```
After it was all over, I ran 'ps -a' once more.  Here is the second output:
```

dave@linuxDesktopAMD:~$ ps -a
  PID TTY          TIME CMD
 6758 pts/1    00:00:00 ps

```

I'm not sure now whether I'm updated or not!

---

### Post by llanitedave on 2006-07-02
jin, the thread you linked to is interesting -- similar to my problem but not the same.  My error came not while downloading, but while installing.  The error messages are very similar, however.

---

### Post by thingy on 2006-07-03
> Setting up apt-build (0.12.17) ...
mkdir: `': No such file or directory
dpkg: error processing apt-build (--configure):
 subprocess post-installation script returned error exit status 1

Regarding this bit, can you remove the apt-build package and re-install it. You will need to make sure that the .deb file for it in /var/cache/apt is deleted as well so that it downloaded a new one.

I can't seem to find a problem with apt-build on bug tracker or in the forums.

Still looking...

---

### Post by llanitedave on 2006-07-03
I'll try that this evening.  Thanks for the attention and help you've given for this!

---

### Post by llanitedave on 2006-07-03
Can I reinstall this from the Dapper installation CD?

---

### Post by thingy on 2006-07-04
The CD is normally kept as a source repository and so if the version on the cd is the same one available for download, adept will ask for the CD for the package.

If the one on the servers is newer, it always download from the server.

The program does this checking by itself and so all you have to do is "apt-get remove apt-build" and "apt-get install apt-build"

---

### Post by Eltern on 2006-07-05
I'm having the exact same issue. I tried the dpkg --configure -a thing, and now I'm getting the same problem with Adept not being able to commit changes.

So, if you figure anything out, less us know ;-)

---

### Post by llanitedave on 2006-07-05
The problem is that the system apparently needs apt-build in order to install anything -- including itself!  Once I deleted apt-build, my fate was sealed.  I had to reinstall the whole thing!

So, I backed up my data, ran through the installation CD, and then did my updates.  So far, everything seems to be working fine.

---

### Post by thingy on 2006-07-06
> 
The problem is that the system apparently needs apt-build in order to install anything -- including itself! Once I deleted apt-build, my fate was sealed. I had to reinstall the whole thing!

So, I backed up my data, ran through the installation CD, and then did my updates. So far, everything seems to be working fine.

 
Oh craps!
 
So sorry! I didn't know that apt-build was a necessary component for apt-get to work. :-(
 
hmm I just looked up the package description:
 
"Frontend to apt to build, optimize and install packages. This is an apt-get front-end for compiling software optimized for your architecture by creating a local repository with built packages. It can manage system upgrades too."
 
From the above description it sounds like you need apt-build if you are going to build/compile packages...
 
Still, it could be that by removing apt-build, it got rid of apt as well...sigh!
 
Again, am sorry about this.

---

### Post by ronniet on 2006-07-30
I just had the Adept 'database locked' problem too.
Just as you suggested thingy, i ran:
*sudo dpkg --configure -a*

I got the following message:
[I]Setting up ktorrent (2.0rc1-0ktorrent1) ...
sed: can't read /usr/share/mimelnk/application/x-bittorrent.desktop: No such file or directory
dpkg: error processing ktorrent (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libqt4-core (4.1.2-1ubuntu1) ...

Setting up libglitz1 (0.5.3-0ubuntu2) ...

Setting up libqt4-gui (4.1.2-1ubuntu1) ...

Setting up libglitz-glx1 (0.5.3-0ubuntu2) ...

Setting up xserver-xgl (7.0.0-0ubuntu4) ...
Setting up compiz-kde (0.0.2-4ubuntu2) ...
Errors were encountered while processing:
 ktorrent[/I]

And i did have kTorrent running on another desktop so i shut it down then tried loading Adept and... it worked!

No idea why, but it worked. No idea why the command singled out ktorrent but maybe its a conflict of some kind??

To make sure Adept did work ok I installed Scribus and, although i got an install error, Scribus did still work...  :)

---

### Post by Contrast on 2006-10-27
> **llanitedave said:**
> Our problems must be different, then. I'm going to try something drastic.

Was just having this same problem. This got it. Thanks.

---

