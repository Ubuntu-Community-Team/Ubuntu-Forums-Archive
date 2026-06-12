---
title: "New Security Policy for executables"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lolpanda on 2010-04-18
Google's turned up no results, so its back to the forums I go. For those you havent had a run-in with this... [https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required)


For personal reasons I need to know how to disable this new 'feature.' as its more annoying than anything else. Note, not looking for someone's opinion on how great and secure this is, just need the knowledge to remove these requirements, whether it be wholesale, or remove them from my limiting my Cdrom drive. 


Thank you.

---

### Post by cariboo on 2010-04-18
I might be better if you explained what it is that you are trying to do, as I have no problem with the policy.

---

### Post by mc4man on 2010-04-18
As far as overall don't know.
In most cases this is enabled thru the EXEC= in an app's .desktop, for example wine.desktop

> Exec=[COLOR="Red"]cautious-launcher[/COLOR] %f wine start /unix

If your issue with the cdrom  is wine related see here for various methods
(fstab entry, new wine launch command (userapp.desktop), start wine from cli, or go ahead and edit the default .desktop

[http://ubuntuforums.org/showthread.php?p=9121470#post9121470](http://ubuntuforums.org/showthread.php?p=9121470#post9121470) (# 11 also

Whether this "cautious-launcher" should be applied to .exe's on a cdrom drive is quite debatable - I believe it shouldn't

---

### Post by Lolpanda on 2010-04-18
I'm attempting to install several games from CD's. In Karmic If something didnt have executable rights, I went into the properties and gave it executable permissions, no problem. That never applied with CD's because I TOLD wine to run them.

Now with Lucid, I can't tell wine to run them without giving the files exec. permissions, and gaming CD's are read-only, so I can't edit permissions. 

Typically I'd just copy the CD contents, but with a slow HDD, the copying process takes too long. 

Summary:

1) New security policy is not allowing wine to force-run it because it  doesnt have permission

2) Can't edit the .exe on the CD because its read-only TO give it permission



Edit: Cariboo, I'm not sure if you're someone who CAN do anything, and if not, then I hope someone is reading this who can,  but by Final Release or soon after, I'm asking, for my sake as well as many others, that a script gets written up by the Dev Team that can be, at user's choice, run to disable this new policy or allow for it to be configured by the user, for their machines in a way that suits them. This kind of idea while great from a security standpoint, will only be a hindrance to executables that are, like this, read only, or cannot be edited for whatever reason. ESPECIALLY considering many games and programs alike still use CD's for installation, and many manufactured CD's are read-only by design so that they cannot be tampered with.  User's shouldn't have to use a work-around like the one described in the link just to be allowed to get the OPTION to install something.

As mc4man in the link said, "certainly not as many choices as before."  which I find disheartening for multiple reasons, one of which being the cruel irony that we are LINUX users, being denied choices or having to edge around unchangeable rules when the core of the linux ideal is choice.

---

### Post by mc4man on 2010-04-18
If you read the links above you'll find 3 methods that  will all work.

The creation of an fstab entry will return behavior to what you've had in the past - if there is a downside to that I don't know - though have seen none.

2 screens - first shows using new launcher (wine) and r. clicking on the .exe

second shows that with an fstab one can use the default launcher - note mount point - /media/cdrom

using the command line always works, with or without an fstab entry

Ex. ( no fstab - mount point /media/<volume label>

> doug@doug-desktop:~$ wine /media/COD1/Setup.exe

(If you absolutely need drive detection in wine and this isn't fixed in next release then an fstab entry is the best way, - noting drive detection is not needed to install prog,'s from a cd.

Eit: I filed a bug against this  ( no drive detection), some time ago, has been ignored so to speak.
[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/554642)

---

### Post by LKjell on 2010-04-18
You can always mount the cd with exec option

---

### Post by Lolpanda on 2010-04-18
I wasnt saying there weren't workarounds with my edit, mc4, what I was saying is that there should be OFFICIAL work arounds, or even a simple on/off switch under gconf-editor, or similar program instead of having to practically trick Ubuntu. 

If there were absolutely no workarounds, I'd already be back using 9.10 and waiting to see if things changed in 10.10

---

### Post by Killigrew on 2010-04-18
Hi

Why is it so hard to understand that we don't want to edit our fstab file and we don't want to use the terminal? 
Ubuntu is designed to work as easy as it could be and this would include executing Windows files with a double click 
or at least right-click -> execute with wine. Not more not lease! 
Of course there could be a warning pop-up but only with a "proceed" button!

greetings :)

---

### Post by mc4man on 2010-04-18
> Why is it so hard to understand that we don't want to edit our fstab file and we don't want to use the terminal? 

It's certainly not hard too understand here, but that's probably not going to get you anything other than workarounds.

You should either file a bug against .exe's on cd's/dvd's being included in this policy or wait and see what shakes out in the next several weeks or so.

As mentioned you don't need to add an fstab entry or use the command line.

A simple one time setup of a custom launch command for right and left click will take care of, takes about 20 secs.

or a *much less preferred way* - edit wine's .desktop itself.

make the EXEC=
wine start /unix %f

---

