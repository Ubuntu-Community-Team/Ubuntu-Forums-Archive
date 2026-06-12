---
title: "Home folder permissions issues after update"
date: 2020-02-07
forum: Installation &amp; Upgrades
---

### Post by wmsfoeva on 2020-02-07
After successfully upgrading 19 something to 19.1 many applications seem to be having permission issues. Opening an app file, like Kodi now has everything locked which was not the case before upgrading. This is throughout my /home folder. I feel like I've read about this happening before and hope someone knows what the commands are to fix the folder permissions if that is what the issue is. Thanks in advance for any help.
[ATTACH=CONFIG]284985[/ATTACH]

---

### Post by CatKiller on 2020-02-07
The two common causes for applications not being able to read/write in directories in your home folder are:

1) You've been running graphical programs as root and that's messed up your ownership. Don't do that. 

2) The application you're running is a snap, and it's been sandboxed from being able to read/write other than in specific directories. 

You'll probably already know which of these is likely to be the case on your system.

---

### Post by wmsfoeva on 2020-02-07
Thanks, but neither fits my situation. Kodi, as an example but not limited to this one program, was initially installed with the software manager in the dash of ubuntu before the upgrade. Worked like a champ. Never needed root for it, never used root for it. After the update the files show as previously pictured and the program will not start.

$ kodi
Could not init logging classes. Log folder error (/home/username/.kodi/temp/)
ERROR: Unable to create application. Exiting

It will run if I 
$ sudo kodi
but that's not ideal.

This is after removing and purging to reinstall.

---

### Post by CatKiller on 2020-02-08
> **wmsfoeva said:**
> Thanks, but neither fits my situation.  

The first one means doing this:

>  It will run if I 
$ sudo kodi 

That will make all the configuration files in your home folder be owned by root. Which breaks stuff, and means that you can no longer use that application as not-root. 

>  This is after removing and purging to reinstall.

Removing packages does absolutely nothing to configuration files in users' home folders.

So, it sounds very much like you've done number 1.

You'll need to change the ownership of those files (and any others that you've broken by running graphical applications as root) back to your user. In future if you need to run graphical applications as root (which you don't) you should use ```
pkexec <application>
``` or ```
sudo -H <application>
``` to break fewer things.

---

### Post by oldfred on 2020-02-08
What does these show?
ls -l ~/.kodi/temp/
ls -l ~/.kodi

I would expect files to be 664 and folders to be 775 as those are defaults. Unless required to be executable by kodi.
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by deadflowr on 2020-02-08
> Thanks, but neither fits my situation. Kodi, as an example but not limited to this one program, 
so what other programs are affected?
Is it only a few others or are all programs affected?

---

### Post by TheFu on 2020-02-08
To set all the file ownership inside the current userid's HOME back, assuming all sorts of ubuntu specific things, run
```
sudo chown -R  $LOGNAME:$LOGNAME $HOME
```
that has been corrected thanks to Yeti's sharp eye.

That shouldn't do any harm and should fix stuff.

_Don't use sudo to run any GUI programs._ At least not before learning and understanding normal Unix file permissions.

Previously, this post had the incorrect:
> sudo chown -R  $LOGNAME:LOGNAME $HOME
it is missing a required $.

---

### Post by yetimon_64 on 2020-02-08
> **TheFu said:**
> ...
```
sudo chown -R  $LOGNAME:LOGNAME $HOME
```...

I'm thinking for that code to work the second "LOGNAME" should also have a "$" symbol before it or the group will be named "LOGNAME" rather than the shell expanding it to the users actual logname.

It appears to be a simple typo/omission that I'd normally send another user a PM to correct it themselves; except when PMs are turned off of course :) ... 
```
sudo chown -R  $LOGNAME:**$**LOGNAME $HOME
```

Regards, yeti.

**Edit:** @TheFu, I also notice there is a double spacing before the first "$LOGNAME". Not sure if that will cause any problem, just to bring it to your attention in case it does. I suspect the missing $ symbol is more important for the OP.

---

### Post by TheFu on 2020-02-08
Correct!  Most definitely a typo on my part.  I'll correct above to limit confusion.  

 Spacing of options in the shell seldom matters, provided there is at least 1 space where needed and no-spaces where not allowed.
```
sudo        chown           -R           $LOGNAME:$LOGNAME         $HOME
```
is perfectly fine.  Some others here seem to put the -R last.  I'd never seen that before in 25 yrs, but if the command doesn't care, why not?  The only reason a command might care is when multiple path options are provided.

There is a certain order for options I've come to expect with CLI tools.

```
command      options/switches     switch+arguments       paths-to-files/directories
```From the chmod manpage:
```
       chown [OPTION]... [OWNER][:[GROUP]] FILE...   
```
-R is an option.
OWNER:GROUP is filled in by $LOGNAME:$LOGNAME
FILE is provided my $HOME

The examples section of the manpage shows the order I use.  But whatever works, works. ;)

---

### Post by wmsfoeva on 2020-02-14
Thanks for everyone's help so far. I've been out of town and just got  back to this box. To clarify, I don't open GUIs as sudo as a regular  rule. When it was mentioned earlier I tried it, hence knowing kodi opens  using sudo. I mentioned kodi was not the only program I had permission  issues with, just an easy example. To answer all earlier questions, here  is the output of those commands and the offered solution. After  execution of the command I tried to open libreoffice which I had not  touched since upgrading. I was greeted with this...
[ATTACH=CONFIG]285026[/ATTACH]

I have not issued sudo on this program (or any other than kodi).

---

### Post by wmsfoeva on 2020-02-14
Here were the results of the commands earlier. 
[ATTACH=CONFIG]285027[/ATTACH]

---

### Post by yetimon_64 on 2020-02-14
> **wmsfoeva said:**
> Here were the results of the commands earlier. 
[ATTACH=CONFIG]285027[/ATTACH]

That last command issued is wrong it is either "$LOGNAME" or "hydra" (without the "$" symbol). Not sure how the shell will handle that error.

You can either copy/paste TheFu's code box OR substitute your username "hydra" (again without the "$" symbol), don't combine the two. The $ symbol causes the shell to expand the system variable "LOGNAME" to give, in your case, the name "hydra".

May be worth another try and then check if you keep getting the permissions issues.

**Edit:** after a bit of testing here the $hydra used in your command should not be a problem. I tested by creating a directory with a file in it and after issuing the command on it all ownership was set to my username even with the $ symbol used.

---

### Post by wmsfoeva on 2020-02-15
And using the exact code was the winner! After using $hydra didn't work I used the code as instructed in the first place because I'm an excellent listener eventually...

Thank you all for your help.

---

### Post by yetimon_64 on 2020-02-15
> **wmsfoeva said:**
> And using the exact code was the winner! ...

If everything is now working well, could you please mark the thread as [SOLVED]? My signature line below has a guide for how to do so; the blue link in the middle, if it is needed.

Regards, yeti.

---

