---
title: "Cannot login as Administrator in GUI to Ubuntu 11.10"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by WolfpackLPK278 on 2012-01-29
Hello all,

I am new to Ubuntu and recently wiped my machine completely to transition to Ubuntu 11.10.  All was working flawlessly for about 2 days, but now I am getting login problems.

When I attempt to login to my (admin) account in the initial welcome screen, it logs me in, goes black, and immediately returns to the welcome screen as if I am to login again.

However, I can successfully login and perform any necessary actions in the non-GUI (command line) environment with Ctrl + Alt + F1.

I have read a good bit about this problem on other forums and have already tried deleting the /.Xauthority AND /.xsession-errors files to no avail.

I am able to login to a Guest session and that is where I am posting this thread.  Any ideas?

Thanks in advance!

---

### Post by benpack101 on 2012-01-29
Hmm, interesting. At first I would have said that you had didn't something to your Desktop Environment (perhaps uninstalling Unity or GNOME while using it).

What were you doing before this problem arose?

---

### Post by 2F4U on 2012-01-29
I would guess that the desktop environment is crashing, may be due to some graphics problem? What are your hardware specs and which graphics drivers are you using? Did you install new or updated software before the problem appeared? If you can login to a console, then look into the file .xsession-errors in your home folder. If it contains error messages then report them back.

---

### Post by WolfpackLPK278 on 2012-01-29
The last thing I did before the problems arose was install MCNP, a nuclear particle simulation code that I use for school.  I can't imagine this has anything to do with the login problems though.

Right now I'm thinking my best option is to just do a clean reinstall of 11.10.  I don't have much of anything on the computer and all is backed up, so that can be an option.

---

### Post by WolfpackLPK278 on 2012-01-29
> **2F4U said:**
> I would guess that the desktop environment is crashing, may be due to some graphics problem? What are your hardware specs and which graphics drivers are you using? Did you install new or updated software before the problem appeared? If you can login to a console, then look into the file .xsession-errors in your home folder. If it contains error messages then report them back.

If the desktop environment is crashing, why am I able to login as the Guest profile?  Wouldn't the graphical interface of that crash too in that case?

---

### Post by mcduck on 2012-01-29
> **WolfpackLPK278 said:**
> If the desktop environment is crashing, why am I able to login as the Guest profile?  Wouldn't the graphical interface of that crash too in that case?

Because the reason for it crashing would be some option on your user account (all the desktop and application settings are user-specific, so broken or corrupted configuration on one user would not have any effect on any other user account).

Also, talking about corrupted files, one thing worth checking would be the contents of your suer's Desktop directory. If there's a corrupted file on desktop, it could cause Nautilus to crash while trying to load the desktop, possibly taking the rest of the desktop environment with it. So if you have any files on your desktop directory, try moving them to some other location.

---

### Post by WolfpackLPK278 on 2012-01-29
> **mcduck said:**
> Because the reason for it crashing would be some option on your user account (all the desktop and application settings are user-specific, so broken or corrupted configuration on one user would not have any effect on any other user account).

Also, talking about corrupted files, one thing worth checking would be the contents of your suer's Desktop directory. If there's a corrupted file on desktop, it could cause Nautilus to crash while trying to load the desktop, possibly taking the rest of the desktop environment with it. So if you have any files on your desktop directory, try moving them to some other location.

On my user desktop there were two things, one installation README.txt and a directory containing other misc .exe files.  Removed them both.

Additionally, in the "Additional Drivers" option in System Settings, there are two NVIDIA graphics drivers options to choose from.

[IMG]http://db.tt/d9FVnKqR[/IMG]

Either of these going to make a difference?  As you can see I currently have the second one activated.

---

### Post by mcduck on 2012-01-29
> **WolfpackLPK278 said:**
> On my user desktop there were two things, one installation README.txt and a directory containing other misc .exe files.  Removed them both.

Additionally, in the "Additional Drivers" option in System Settings, there are two NVIDIA graphics drivers options to choose from.



Either of these going to make a difference?  As you can see I currently have the second one activated.

The drivers wouldn't be the cause for your problems, as they would affect all the user accounts. 

What comes to the files you had on desktop, if they were the problem you should be able to log in now. If not, then the problem is something else. Whatever it is, it's something in your user's home directory. Most likely some configuration file if removing stuff from your desktop didn't help and you don't get any errors.

...actually instead of deleting .xsession-errors, you should probably read it in case there's any error messages.... That's what such log files are for, anyway. ;)


And if everything else fails, one thing worth trying is moving all the hidden config files/directories into some other location. That would reset all your settings, but at the same time of course also give you fresh new configs and get rid of the problem. You could then return the old files one at a time back to it's original place to get your settings back. (of course you can ignore all the setting files that you know to be related to something else than the desktop itself, for example Firefox configs would never stop you from logging in so no need to mess with them for this reason...)

---

### Post by WolfpackLPK278 on 2012-01-29
> **mcduck said:**
> The drivers wouldn't be the cause for your problems, as they would affect all the user accounts. 

What comes to the files you had on desktop, if they were the problem you should be able to log in now. If not, then the problem is something else. Whatever it is, it's something in your user's home directory. Most likely some configuration file if removing stuff from your desktop didn't help and you don't get any errors.

...actually instead of deleting .xsession-errors, you should probably read it in case there's any error messages.... That's what such log files are for, anyway. ;)


And if everything else fails, one thing worth trying is moving all the hidden config files/directories into some other location. That would reset all your settings, but at the same time of course also give you fresh new configs and get rid of the problem. You could then return the old files one at a time back to it's original place to get your settings back. (of course you can ignore all the setting files that you know to be related to something else than the desktop itself, for example Firefox configs would never stop you from logging in so no need to mess with them for this reason...)

I didn't delete, but moved the Desktop files instead to my Documents folder.  This change made no difference however.

> And if everything else fails, one thing worth trying is moving all the  hidden config files/directories into some other location. That would  reset all your settings, but at the same time of course also give you  fresh new configs and get rid of the problem. You could then return the  old files one at a time back to it's original place to get your settings  back. (of course you can ignore all the setting files that you know to  be related to something else than the desktop itself, for example  Firefox configs would never stop you from logging in so no need to mess  with them for this reason...)

How would I got about moving all of these config files/directories?  Where are they hidden?

---

### Post by mcduck on 2012-01-29
> **WolfpackLPK278 said:**
> I didn't delete, but moved the Desktop files instead to my Documents folder.  This change made no difference however.



How would I got about moving all of these config files/directories?  Where are they hidden?

In your home directory. I'm talking about all the files and directories with names starting with a dot. (use "ls -a" in a terminal to see them, or press ctrl-h in the file manager to make them visible). They are the files that are used to store all your personal settings for all the applications you use.

You could, for example, create a new directory somewhere and then move all these setting files there (excluding all the ones you know to be related to some program, not the desktop environment itself). Next time you log in the system would automatically create new setting files for you, hopefully also fixing your login problem.

It would be quite an easy solution, but also take quite some work (especially when you begin moving the old files back to their original places to get your settings back, as you'd need to do that few fiels at a time and log out in between to find out which file was the problem). SO you might want to wait a while before you do that, in case somebody comes up with a more specific solution... And definitely check the .xsession-errors and log files in /var/log first in case there's soemthing that would give you a hint about what's the problem...

---

### Post by WolfpackLPK278 on 2012-01-29
> **mcduck said:**
> In your home directory. I'm talking about all the files and directories with names starting with a dot. (use "ls -a" in a terminal to see them, or press ctrl-h in the file manager to make them visible). They are the files that are used to store all your personal settings for all the applications you use.

You could, for example, create a new directory somewhere and then move all these setting files there (excluding all the ones you know to be related to some program, not the desktop environment itself). Next time you log in the system would automatically create new setting files for you, hopefully also fixing your login problem.

It would be quite an easy solution, but also take quite some work (especially when you begin moving the old files back to their original places to get your settings back, as you'd need to do that few fiels at a time and log out in between to find out which file was the problem). SO you might want to wait a while before you do that, in case somebody comes up with a more specific solution... And definitely check the .xsession-errors and log files in /var/log first in case there's soemthing that would give you a hint about what's the problem...

Ok so I went into Terminal under my login and viewed all items in my home directory using ls- a and found both a .Xauthority file (which I deleted without having to change permissions) as well as the .xsession-errors file.  I then went into the .xsession-errors file using 

```
cat .xsession-errors
```Which led me to the ultimate error:

```
** (gnome-session:1557): WARNING **: Cannot open display:
```

This seems like what you were talking about, any ideas on the proper fix?


UPDATE: While under Guest, I was trying to use SteamTab.exe (a Windows program) and use WINE as directed on a how-to forum guide.  WINE installed properly but when I tried to execute 
```
wine Steamtab.exe
```
Terminal states that a display could not be opened.  Similar/same problem?

---

### Post by MAFoElffen on 2012-01-29
> **WolfpackLPK278 said:**
> Ok so I went into Terminal under my login and viewed all items in my home directory using ls- a and found both a .Xauthority file (which I deleted without having to change permissions) as well as the .xsession-errors file.  I then went into the .xsession-errors file using 

```
cat .xsession-errors
```Which led me to the ultimate error:

```
** (gnome-session:1557): WARNING **: Cannot open display:
```This seems like what you were talking about, any ideas on the proper fix?


UPDATE: While under Guest, I was trying to use SteamTab.exe (a Windows program) and use WINE as directed on a how-to forum guide.  WINE installed properly but when I tried to execute 
```
wine Steamtab.exe
```Terminal states that a display could not be opened.  Similar/same problem?
To the OP-

Read through the thread.  You said you deleted the .Xauthority file... But I did not see anywhere where you created a new file, nor where you gave that new file the correct rights and authorities:
```
[FONT=monospace]
[/FONT]sudo rm .Xauthority*  
touch .Xauthority  
chmod 600 .Xauthority 
sudo shutdown -r reboot

```
That would be done from the CLI in your home directory... Which is what you're limited to without a functional .Xauthority file.

Tell me how it goes.

---

### Post by WolfpackLPK278 on 2012-01-31
Update: I installed Ubuntu 10.04 and all is well.  Integrated support for NVIDIA drivers and everything went smoothly.

Thank you all so much for the help!

---

### Post by swissinvestor on 2012-02-01
I was unable to login  anymore and none of the numerous "solutions" I found on this board worked for me. I had lost access to my - encrypted - harddisk for days.

I am absolutely unaware that I have done anything that could have broken my ability to access my account anymore but constantly end up at the login screen. Kind of bothering.

In the end, this was the solution:

I had to build a new system and transfer all my data from my old encrypted disk:

This is the "how to" to get access to the encryped data again:
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

Great thanks to the author!

Time consuming, but works

Ubuntu 11.10 64-bit

---

