---
title: "Computer Janitor too enthusiastic"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2009-03-28
I just ran the Computer Janitor utility in System-Administration, and it uninstalled a package I had previously installed (pulseaudio-mixer-applet). Should it do that? Does it uninstall packages that didn't come from one of the listed repositories?

---

### Post by phenest on 2009-03-28
Did you notice the checkboxes to the left of each package? If you uncheck one, it will leave it alone. It also remembers what's unchecked the next time you use it.

---

### Post by rockin_goliath on 2009-03-28
ahh, I see. That could be really confusing for users. Is there a way of preventing that kind of behavior, such as having certain classifications of packages be unchecked by default? I can just imagine that users are going to install their own packages, like Skype, and then run Computer Janitor and have it removed. From my Windows days, I remember running something like SpyBot and not bothering to read the list of all the crap it's found, just hitting the delete button.

---

### Post by Bakon Jarser on 2009-03-28
This seems like it should be a bug.  It wanted to uninstall Truecrypt for me.  It seems to want to uninstall anything that is not in the repositories.  IMO it should make an exception for programs installed from a .deb file instead of with apt.

---

### Post by phenest on 2009-03-28
> **rockin_goliath said:**
> ... not bothering to read the list of all the crap it's found, just hitting the delete button.

Well, if you're not going to bother reading before hitting Delete... That's hardly a bug.

---

### Post by trot2millah on 2009-03-28
> **phenest said:**
> Well, if you're not going to bother reading before hitting Delete... That's hardly a bug.

I wouldn't consider a bug, but when the average user wants to run this tool to get rid of excessive programs and sees a bunch of "libx" files, he or she would probably not have an idea of what they were doing and accidentaly could delete some important files.

---

### Post by phenest on 2009-03-28
> **trot2millah said:**
> ...when the average user...would probably not have an idea of what they were doing and accidentaly could delete some important files.

What you are expecting is called 'dumbing down'. The average user must learn to use these apps. It's not rocket science.

If you click on an item in Computer Janitor, a brief explanation appears at the bottom so you know what that package is.

The alternative is to not use Computer Janitor. You don't have to.

---

### Post by Polygon on 2009-03-28
what computer janitor does is make your system LIKE A FRESHLY INSTALLED ONE

which means, any and ALL packages that were not installed by default, get deleted.

---

### Post by trot2millah on 2009-03-28
> **phenest said:**
> What you are expecting is called 'dumbing down'. The average user must learn to use these apps. It's not rocket science. 

Still, the compare it to XP (blech) there are system utils which separate different things into Network Tools, Temp Files, Software etc, there could be something comparable to this in Ubuntu.

> If you click on an item in Computer Janitor, a brief explanation appears at the bottom so you know what that package is.

The alternative is to not use Computer Janitor. You don't have to.

When the user sees an option to get rid of clutter, they might not necessarily use their brains and just click the "Cleanup" button and expect to have it work.


I'm not talking about "dumbing it down," and you could assume the average user would attempt to explore and clean up unnecessary space.  It wouldn't be too hard to sort different software options into whether or not other packages have dependencies relating to that software etc.  I'm no expert, but it's just one area that rockin_goliath has revealed there could be improvements.

---

### Post by forcecore on 2009-03-28
> **Polygon said:**
> what computer janitor does is make your system LIKE A FRESHLY INSTALLED ONE

which means, any and ALL packages that were not installed by default, get deleted.

and your post explains why i had problem with this:
[http://ubuntuforums.org/showthread.php?p=6973019#post6973019](http://ubuntuforums.org/showthread.php?p=6973019#post6973019) too bad that there is no option to delete own topic if no replys.

---

### Post by lisati on 2009-03-28
I've been caught out too, mostly with Windows software which installed "extras" and also made changes to my system that I didn't really want. There's no substitute for paying attention to what's on the screen.

---

### Post by phenest on 2009-03-28
> **Polygon said:**
> what computer janitor does is make your system LIKE A FRESHLY INSTALLED ONE

which means, any and ALL packages that were not installed by default, get deleted.

No it doesn't. I don't any of you here on this thread so far, have any idea what Computer Janitor does. I think you all had best leave it alone.

Computer Janitor removes 'unused' packages and old kernels. It does not remove anything you are using. The only exception, is packages you installed manually. And if you have installed anything manually, you'd know its name, and uncheck it before hitting the Cleanup button.

Computer Janitor doesn't do much more than can already be done in Synaptics.

---

### Post by phenest on 2009-03-28
> **trot2millah said:**
> When the user sees an option to get rid of clutter, they might not necessarily use their brains and just click the "Cleanup" button and expect to have it work.

That's the whole point of the list it provides. You choose what to keep or remove first, then click Cleanup. What 'brains' is it that you think you need?

---

### Post by Bakon Jarser on 2009-03-28
> **Polygon said:**
> what computer janitor does is make your system LIKE A FRESHLY INSTALLED ONE

which means, any and ALL packages that were not installed by default, get deleted.

That's not how I see it.

> Over time, a computer system tends to get cluttered. For example,
software packages that are no longer needed can be uninstalled.
When the system is upgraded from release to release, it may miss
out on configuration tweaks that freshly installed systems get.

Computer Janitor is an application to fix these kinds of problems.
It attempts to find software packages that can be removed, and
tweak the system configuration in useful ways.

That seems to say that it tries to find packages that are no longer needed. It does not uninstall everything that wasn't there originally.

---

### Post by aaronb on 2009-03-28
Should it not provide a list of things to clean up, but have them all unchecked be default, this would leave it up to the user to specifically select stuff that should be removed?

This way people who just "click their way through life" will not do any "damage" by default.

---

### Post by phenest on 2009-03-28
I can't help thinking that if some one doesn't think about unchecking items, why would they check them? Then they will be complaining that CJ does nothing, and don't understand why.

---

### Post by phenest on 2009-03-28
I have an idea. If you manually install a .deb file either through the Package Installer or dpkg from a terminal, then those packages should show unchecked in Computer Janitor. That should prevent deleting of packages you installed yourself.

---

### Post by ezsit on 2009-03-28
> What you are expecting is called 'dumbing down'. The average user must learn to use these apps. It's not rocket science.

No, it is not "dumbing down" to expect that a GUI utility NOT remove possibly needed files. The GUI utility Janitor is merely running 'apt-get autoclean' and 'apt-get autoremove'. 

The Janitor program is dumbing down the process of apt-get clean-up. Why not make the dumbed-down Janitor idiot proof as it should be? If you want control over your system, use the apt-get commands. For those users who want a simplified GUI program to do things for them, those GUI programs should be dumbed-down and idiot proof. 

I've had 'apt-get autoremove' want to remove some things that I still wanted, so I aborted the 'apt-get autoremove' by responding "No" at the appropriate time and place. Users who are relying on the GUI programs are doing so because they WANT a dumbed-down process.

There is nothing wrong with dumbing down a lot of the computer using experience. That is what most users want, an idiot-proof box that surfs and prints. I say that is fine and good. Heck, Ubuntu is just a dumbed-down version of Debian, but I love and use it anyway! :-)

---

### Post by phenest on 2009-03-28
> **ezsit said:**
> The GUI utility Janitor is merely running 'apt-get autoclean' and 'apt-get autoremove'. 
No it doesn't. autoclean removes downloaded packages from the cache, and does not uninstall anything. After using apt-get autoremove, there are still packages in CJ, so I think it's doing a lot more than that.
> **ezsit said:**
> Users who are relying on the GUI programs are doing so because they WANT a dumbed-down process.
Actually, GUI's only serve one purpose: to have a graphical equivalent of a terminal command. GUI's are not intended to dumb down anything.
> **ezsit said:**
> There is nothing wrong with dumbing down a lot of the computer using experience. That is what most users want, an idiot-proof box that surfs and prints.
There is a time for dumbing down software, and a time when the user should learn how to use things. Be careful you get it right, or you will reduce the whole experience.

---

### Post by olskar on 2009-03-28
It's bug [https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746)

I also find this a bad behavior. 


Users might think (real example, happened to a friend of mine) that it is old configurationfiles for those marked programs that are being removed.

Another example with the same logic would be if the janitor asked if it should remove all the files in /home/use/Music for example and then blame the user for not unchecking that..

It does not make sense to treat manually installed packages as cruft, therein lies the bug.

---

### Post by phenest on 2009-03-28
Which is what I suggested in post #17.

---

### Post by olskar on 2009-03-28
> **phenest said:**
> Which is what I suggested in post #17.

Yep, great idea, add it to the bugreport :)

---

### Post by Jimbob0i0 on 2009-03-28
I was active on the bug report but it seemed obvious Lars wasn't willing to listen to anything and despite no real change in behaviour from when it was denied entry to intrepid (CLI or GUI) it looks like it will be going in on jaunty....

Personally I see this as a very bad thing and can forsee a lot of problems for people who gets linux PCs from dell etc that have extras such as powerdvd and so on pre-installed. Those users are unlikely to know what to keep or not and yet the how description of the application (and indeed it's reason to be according to one note on the comments for the bug) is to make it easy for novice users to clean up their system - which it obviously fails to do.... power users get better results with synaptic and custom filters.

Oh and adding code to dpkg/gdebi/apt/synaptic etc to automatically whitelist things was denied already due to the fact that manually installed packages already in place for upgraders wouldn't be detected properly.... and the whitelisting described in the man page isn't the same as unticking the boxes according to the dev Lars to make matters even more confusing.

---

### Post by phenest on 2009-03-28
Yes, the ticking and white list are separate, but they need to be able to update each other. I think the current situation is to remove it from the repos until this bug can be resolved. That seems a good idea.

---

### Post by ktp on 2009-03-28
> **phenest said:**
> Which is what I suggested in post #17.

Hum the packages which I installed seem to come back as unchecked.  Maybe its the second time around and remembered my selection.

---

### Post by kansasnoob on 2009-03-28
I don't like it!

I've installed over 20 systems, mostly for elderly folks that have no puter knowledge at all, and that's one I'll hide using the Main Menu edit options!

And I think it interferes with the command: sudo apt-get clean.

The janitor needs to be cli only!

---

### Post by novafluxx on 2009-03-28
> **phenest said:**
> I can't help thinking that if some one doesn't think about unchecking items, why would they check them? Then they will be complaining that CJ does nothing, and don't understand why.

LOL Good one, I agree

---

### Post by phenest on 2009-03-29
> **kansasnoob said:**
> The janitor needs to be cli only!

Pointless CJ being cli only when you have apt-get.

---

### Post by rburkartjo on 2009-03-29
i really like this feature it is an easy way to remove old kernels and deb files. it does hang up sometimes and you have to run it twice to work. i do wish that by default no packages were checked. but all in all a nice addition

---

### Post by Lunx on 2009-03-30
> **phenest said:**
> What you are expecting is called 'dumbing down'. The average user must learn to use these apps. It's not rocket science.



So where in Jaunty does it explain what it is, what it does, and how to use it? "Average" users aren't psychic, and regardless of what you think they should or shouldn't know/do, I'll bet my proverbials there will be a flood of posts soon from new Linux and Ubuntu users who have deleted stuff they shouldn't have, I can even guess what many of the thread titles will be. I installed Jaunty late last night to have my first look, installed Opera from a deb and then was looking at the other new features like CJ. Opened it up to see what it was about, saw Opera was listed and I DID read the message at the bottom (guessed it would remove Opera from my system and discovered that this is indeed the case:P)

In the case of Opera, I get the following

> Package is no longer supported: it is no longer in the package archive. (It may also have been installed from an unofficial archive that is no longer available. In that case you may want to keep it.)


To me (a new "average" user of only three months to Ubuntu and Linux generally), that isn't very clear and I can see how it could/will cause confusion and grief to many.

---

### Post by emarkay on 2009-03-30
Hey, someone better DEFINE what this is, as one would see in a "Help" or "FAQ" - as I see it it WOULD remove my Skype app if I didn't uncheck it!

How can I be a Beta Tester of 9.04 if I am both unsure what the new feature does and what the technical (behind the scenes) reasons are for it and what modes and options there may be and any specific issues on it.

Seems like a simple request?

---

