---
title: "Would prefer repair to reinstalling..."
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by jonrkc on 2005-06-09
I have so many things messed up possibly due to permissions problems that it seems hopeless to go on trying to fix one thing then another, often with no results--and after hours of searching via Google and this forum.  Nothing to do with Gnome works right, and many things won't work at all.  I don't use the Gnome environment, but a LOT of programs depend on Gnome stuff no matter what environment one uses.  And now KDE apps are failing to work right, too--unable to connect to the DCOPserver.  When I remove the .ICEauthority file it just gets put back and root is always the owner, not me.  As a result it's always unwritable.  

So...

Before I grit my teeth and do a complete reinstall, with about a week's worth of trying to get apps put back like I had them, and working, I would like to ask if there's any equivalent in Ubuntu to the Mandrake/Mandriva "upgrade" installation, which actually serves as a "repair" installation--putting the system back in order re: permissions, etc., without touching any of your hard-won apps or configurations.  I know for certain that if I were still running Mandriva I could do that and be back in good shape in twenty minutes, not two weeks.  

Is there such a possibility with Ubuntu?  I think I know the answer, but am hoping otherwise.

(I did an apt-get upgrade-dist last night and it didn't help; I reinstalled ALL of Gnome and that got ONE program working again, otherwise still just as bad...)

Thanks in advance.

---

### Post by Joeb on 2005-06-09
Do you know what you did to mess up the system?  That might impact what to do to fix it.

---

### Post by jonrkc on 2005-06-09
[QUOTE=Joeb]Do you know what you did to mess up the system?  That might impact what to do to fix it.[/QUOTE]
I changed a lot of permissions in an attempt to get xcdroast and k3b to work.  I finally got those to work but in the process a bunch of others stopped working.  By trial and error I've got some of the permissions those apps want back in order, but nothing I do satisfies Gnome applications.  K3b will still work though I get the message about inability to communicate with the DCOPserver before it finally starts.  With Gnome apps, it finds wrong permissions on all the /tmp/orbit-jon* files (of which there are at least fifty) no matter how I set the permissions.  It also was claiming that /tmp/gconfd-jon didn't exist; I finally persuaded Gnome that it DOES exist, but then it couldn't convert /tmp/gonfd-jon/lock/IOR to an object reference, presumably because IOR didn't exist before I put it in there as an empty file with the touch command.  It doesn't seem to have existed on my prior installation of Ubuntu (on another hard drive), either, yet Gnome worked on it.  

I've tried the suggestions to delete .ICEauthority (no good), delete the /tmp/gconfd-[user] directory and the /tmp/orbit-[user]* files (also no good) and as for the DCOPserver problem, it appears to me from my searches with Google and in this forum that nobody has figured that one out yet.  It's just something that happens.  

The thing I dislike about complete reinstallation is not the reinstalling itself, which is almost painless, but losing tons of applications and configurations that I have to piece together afterward, which in one instance took fifteen hours, in another nine...   I guess I could go back to Mandriva, but I'd rather stay with Ubuntu because it's basically non-commercial and also runs a good deal faster and nicer when it's working right.

---

### Post by Joeb on 2005-06-09
If you inadvertantly changed a bunch of permissions, then I don't think there is an easy fix.  Even Mandrake/Mandriva has problems with that kind of repair.

That said, there are some things you can do that might fix things.  For instance to get your gnome working again, you could uninstall it and then reinstall it.  That should fix permissions for gnome.  The same for kde.  Any settings or customizations to them should be in your /home directory and shouldn't be touched (although you might want to make a backup of your home directory, just in case).  Of course, if what is actually borked is the configurations, then this won't help you.

One risk to the above is if any of the apps you have installed depend on gnome or kde, then they will be uninstalled, too and you will have to reinstall them.  Two good news things about this are that most apps also store their configurations in the home directory, so you shouldn't loose that and if you use apt-get or synaptic, the .deb files are usually cached on the hard drive, so you won't need to redownload them.

I should also add that if you are going to attempt the above, you can't do it from within gnome or kde (it's not wise to remove the windowmanager that you are actually running from!!).

---

### Post by jonrkc on 2005-06-09
[QUOTE=Joeb]If you inadvertantly changed a bunch of permissions, then I don't think there is an easy fix.  Even Mandrake/Mandriva has problems with that kind of repair.

That said, there are some things you can do that might fix things.  For instance to get your gnome working again, you could uninstall it and then reinstall it.  That should fix permissions for gnome.  The same for kde.  Any settings or customizations to them should be in your /home directory and shouldn't be touched (although you might want to make a backup of your home directory, just in case).  Of course, if what is actually borked is the configurations, then this won't help you.

One risk to the above is if any of the apps you have installed depend on gnome or kde, then they will be uninstalled, too and you will have to reinstall them.  Two good news things about this are that most apps also store their configurations in the home directory, so you shouldn't loose that and if you use apt-get or synaptic, the .deb files are usually cached on the hard drive, so you won't need to redownload them.

I should also add that if you are going to attempt the above, you can't do it from within gnome or kde (it's not wise to remove the windowmanager that you are actually running from!!).[/QUOTE]
Thanks for these helpful suggestions.  I learned the hard way some time ago not to attempt major reparations from within the operating system itself. I will probably have a go at it using Knoppix in command-line mode, which I'm comfortable with to a certain extent.  I managed to transfer my whole system to a new hard drive that way last week and was amazed at how well I did, considering my level of experience (and I'd never done something like that ever).

This is slightly off-topic, but really not: I feel that the whole GNU/Linux philosophy is tacitly based on a multi-user, and probably networked, system; while the big hope for much of the Linux community, including myself, is that individuals will start to adopt Linux more and more in preference to that system that dominates 95% of the world's PC's.  

I suspect the Linux emphasis on multi-user use is a carryover from the early UNIX days, when that was virtually the only environment that computers were used in.  

In a multi-user environment, it makes perfect sense to have applications and files essential to them stored in a central, root-user-only-accessible collection of libraries and other directories.  But with today's huge hard drives, I think there should be an option to install a user's programs (for a single-user, or family, machine) in the user's home directory. That way when a major repair becomes necessary, or a complete reinstall, there would be no problem with restoring dozens of applications and fine-tuning them again (or simply working hours to get them to work, period).

Firefox and Thunderbird are the only apps I can think of offhand that easily lend themselves to this single-user-friendly approach.  OpenOffice.org can be made to do so if you know how.  (I know how, but many users wouldn't.)  Most everything else, if it doesn't come in the stock distro, is a chore to get going again.

I'm going to seriously consider your suggestions and probably attempt them; there's little to lose, since I can always fall back on a full install if I have to.  

Thanks again. I really appreciate your quick help, for I wanted to decide TODAY if possible.

---

### Post by jonrkc on 2005-06-09
Well, I just logged out into a console, since removing kde and gnome shouldn't impact the basic system, and attempted to remove them.  Apt-get remove gnome removed only one package, and when I went back into X I was still able to get gnome apps to run after a string of popups with error messages, like before.  So I obviously need some help as to "how to remove gnome."  Same with kde only this time apt-get remove kde said "package is not installed" so it would not be removed.  

There are literally thousands of references to KDE on my system, of course, and I don't know why it's said kde is not installed!  I tried again with "kde-base" and got the same answer.  

As a result, I'm at a standstill, in this particular approach to the problem, till maybe I can learn the correct way to do this.

---

### Post by az on 2005-06-09
If you want to remove gnome, remove libgnome.  If you want to remove kde, remove kdelibs.

The fact that your sustem is tweaked makes it difficult to find an easy-fix.  Like partitioning your drive and installing another Hoary there, only to copy your home folder over to get your preferred settings.  The trouble is that you need to install all the extra packages anyway,

WHat takes you so long to tweak everything?  Are you on dialup?  If so, you can always save what is in /var/apt/cache/archive and avoid having to download them again....

Hope this helps...

---

### Post by Joeb on 2005-06-09
Thanks azz, I should have been more specific about how to remove gnome and/or kde.

Jonrkc,  you need to follow azz's advice on removing the core lib for gnome and/or kde.    As a matter of fact, installing those libs is what allows you to run gnome or kde apps, even if you don't have gnome or kde installed as a desktop environment.

With the way apt-get works, removing the core library will also remove anything dependant on them (which will probably be a lot of things on your system).  However, when you go to reinstall do the apt-get install gnome or kde and it will automatically install the everything dependant on it.  You will then need to install any additional apps you had previously installed that might have been removed, too.

As for your observations on linux, one problem with the simplified approach you are talking about is when your use changes.  Say, right now, you are just trying to learn linux and figure things out and use linux simply as a single user desktop.  But, a little later, you get a second computer and think wouldn't it be nice to back this computer up to the linux box?  Well, without the structures that linux has, it would be really easy to bork and installation by mistake.  Or lets say, you want to add a mail server or web server to your linux box.  Now, you could have outside people hitting your linux box and you probably don't want them getting into your personal files.

So, yes, linux defaults to a multi-user setup with security enabled, because ultimately, it's the most flexible system.  It is possible, to have linux boot up and have you automatically log in, etc. but underneath, it would still be multiuser.

One additional thing, once you have used it for awhile, things start to make more sense.  Home is obviously where your personal directory is.  bin and sbin are where system programs are.  /usr/bin and /usr/sbin and /usr/share are where other applications and shared data are located.  /mnt and/or /media are where additional drives are mounted so you can access them (whether they are on your machine or another).  There are further directories, but that hits most of them and really isn't much different than having all of those directories under C:\Windows (ie system, system32, settings, etc.).

---

### Post by jonrkc on 2005-06-10
Thanks for the additional good points and clarifications, Joeb and Azz.  

I have used Linux exclusively since January 2003, when I swore never again voluntarily to use a Microsoft product, a promise I've kept.  But I have no desire to be a technical genius at it.  It's simply that I will throw my computer in the dumpster before I will patronize Microsoft again.  

It takes so long to tweak--and perhaps I should have said customize instead--because I have two functions going, lmsensors and apcupsd, that are almost impossible to set up right without several hours of work EVERY TIME.  Then I have a list of about twenty-five other programs I may not use every day, but that I want on hand for when I need/desire to to use them; and each one of those presents its own difficulties in setup.  That's why it takes as much as fifteen hours' straight work (which I have done, no sleep, no meals) or a week or two (if I can make myself stretch it out).

I don't agree with the someday-add-a-server argument against simplicity; if I ever wanted to run a non-local  server (which my ISP would definitely frown on, and probably terminate my account for), I would just start from scratch and (with somebody's help) set up my system that way.  

As I write this it's 3 am local time and now OpenOffice.org has quit working--while I was asleep and not touching the computer.  I load it and nothing appears, though it's in its normal place with the same normal two entries in the list of processes.  And that's the program I use most.

So I guess today I'll just have to start all over, with either Mandriva or Ubuntu.  I'll decide probably at the last minute.

I want to thank you both again for taking the time the write so patiently, and I hope you will understand my feelings of frustration.

---

### Post by jonrkc on 2005-06-10
I decided to try removing the Gnome and kde packages before resorting to a reinstall.

I issued as root in a console:

```

apt-get remove libgnome kdelibs

```

and also tried with each separately, and was told that kdelibs "is not installed and so will not be removed," and that libgnome was "not found."

Next step?

---

### Post by desdinova on 2005-06-10
[QUOTE=jonrkc]I decided to try removing the Gnome and kde packages before resorting to a reinstall.

I issued as root in a console:

```

apt-get remove libgnome kdelibs

```

and also tried with each separately, and was told that kdelibs "is not installed and so will not be removed," and that libgnome was "not found."

Next step?[/QUOTE]
 Since you b0rked the permissions in /usr - its quite likely there isn't a simple fix here - as the tools to repair the damage were themselves damaged, so to speak.

I'd backup /home and /etc (for the config files) and reinstall Ubuntu.

And as the permissions thing - I'd mirror the above - Linux's strength is the permissions thing, turning Linux into a single user system would negate half (if not 90%) of its strength.

---

### Post by jonrkc on 2005-06-10
(Edit: I wrote and posted the below before seeing the post by Desdinova above.  That may be the best solution; in which case I'll probably return to MandrivaLinux, since it allows repairing a system without totally reinstalling, and also does not have the heavy emphasis on Gnome that Ubuntu has.)

Update: I'm not sure removing Gnome and/or KDE is the solution I need anyway.  

I always advise people against running an X session as root, but decided I'd do it as a test.  

Didn't try out KDE, but Gnome desktop works perfectly well for root--as I kind of suspected.

It's apparently a problem with permissions.  It would certainly help if my (normal user, "jon") .ICEauthority file were not recreated EVERY time with root as the owner, for one thing.  Why do you suppose that's happening?  And why do my /tmp/orbit-jon* directories all get created with root as owner?  I suspect this is a large part of why I can't use Gnome-related apps successfully.

I really feel if I could fix the problem with ~/.ICEauthority and with the /tmp files, I would probably be back in normal operation.  But every time I change ownership manually, it gets put back to root as owner next time I try to run Gnome-anything.  I've searched for literally hours (probably three hours yesterday alone) using Google for the solution to this problem, and all I find is dozens of people with the same problem, and no answers.  

Obviously root is not intervening to change things back: because that's ME.  So some process is setting things to ownership by root, denying jon access to what's needed to run Gnome (and probably KDE) apps/desktop.  

I can totally wipe out .ICEauthority and all my files in /tmp and at least I get the blank, brown-colored default Gnome desktop screen, and NO error popups, when I attempt a Gnome session as jon.

But if I let those files remain, I get a stream of close to a hundred error messages proclaiming that the ownership is wrong, etc.

Any idea what might be wrong in this regard, and how to fix it?  It would be far preferable to any reinstall.

---

### Post by jonrkc on 2005-06-10
A few hours later.  I did a complete reinstall of Ubuntu, which entailed wiping out my entire hard drive as the option NOT to just resulted in a loop in the installation program.  

I have so many unfavorable comments about Ubuntu and about Linux at this moment that I'd better just keep my mouth shut.

I may choose to be computer free.  Increasingly use of the computer results in impoverishment of my life, not enrichment.

Oh, by the way, some things are working now.  Some.

---

### Post by az on 2005-06-10
Sorry your experience was bad.  Ubuntu makes a lot of effort to prevent these problems from happening.  

The next time an application will not run properly, look to it's configuration by using synaptic or the /etc files.  Changing permissions is never the way to go to solve problems.

Please ask on the forums.  Probably many users have had the same problems as you.

---

### Post by jonrkc on 2005-06-13
[QUOTE=azz]Sorry your experience was bad.  Ubuntu makes a lot of effort to prevent these problems from happening.  

The next time an application will not run properly, look to it's configuration by using synaptic or the /etc files.  Changing permissions is never the way to go to solve problems.

Please ask on the forums.  Probably many users have had the same problems as you.[/QUOTE]
 Thanks, Azz, and all others for putting up with my posts soaked in frustration.  I'm usually very dignified and careful and often even embarrassingly witty on forums.  I was just so beside myself...  Physically pounding on the keyboard, slamming the CD-ROM drive drawer in, etc.  

I do agree that Ubuntu places emphasis on being user-friendly--perhaps just a little too much so, in defaulting to graphic logins, which to me are anything but friendly.  I got rid of that feature, although I had to figure it out for myself.  Now I'm quite a bit happier, with my text login where I can edit .xinitrc and do other things before starting X, as I am used to doing.  

I'm 65 years old and every day brings some fresh reminder that I no longer can deceive myself that I have unlimited time to learn things, so I am more or less forced to set priorities.

I have my system going very nicely now, and I certainly learned my lesson about changing permissions.  Sometimes it's necessary to do that (or else, I guess, the facility wouldn't be made available), but I am going to be careful of the possible ramifications more than ever, and attempt to avoid changing outside my home directory (where, I learned, you can STILL mess things up).

Azz, you're right that many users have the same problem with bad permissions, whether due to their own error or something else.  Google searching brought me thousands of posts of people in desperation because they couldn't figure out what was wrong with their permissions.  Sometimes they got a good answer, and sometimes one that would probably make things even worse for them.

I imagine O'Reilly has a book for $50 on permissions, but I'm just going to try being very careful and conservative for a while and spend the $50 on coffee beans.  :)

Thanks again for being patient, and I apologize for my tone of rancor.  I have nothing against Ubuntu and though I like Mandriva, I am finding Ubuntu to be quite a bit faster, seemingly more trouble-free, and actually quite a bit more configurable, once a few tricks are learned.

(By the way, this whole major problem started when I was trying to help two different people on two different forums having trouble with CD-writing--one of the most common difficulties on any distro, to judge from what I've read.  I had had the exact same problems as those users, but couldn't remember how to solve them.  XCDroast was cranky about permissions, and that's how it began to snowball.  I am now relying on K3b for my limited burning, because it seems much more perceptive thatn XCDroast, which still sends semi-sarcastic messages about kernel 2.6x and "It would help if you would close the CD drawer" (not exact wording, but that's what it means)...  I can do without that, and the constant reminder when there's an error writing that the original author is "not to be bothered" with this kind of problem.  Even in free software, sarcasm and rudeness is uncalled for.

---

### Post by Joeb on 2005-06-13
To Jonrkc,

First I have to hand it to you in trying to take on a new distro.  Mandrake/Mandriva is a very good distro, I used it for many years, joined their "club," etc.,  and for reasons I won't go into here, I felt it was time to move to a different distro.

I bring all of that up, because, what landed me here with Ubuntu, is something you alluded to in your posts, without really saying out loud and that is, the number one thing going for Ubuntu, is it's friendly user community.  Don't get me wrong, the distro is great in and of itself, but you know, there are a lot of good distros out there (and I think I tried most of them).

What kept bringing me back to Ubuntu though, was the community.  Unlike a lot of other distros, you normally aren't treated like an idiot for doing something that an expert might know not to do, but the rest of us usually learn the hard way.  Instead, the community tries as best it can to help people solve their problems (whether self-induced or accidental).

My biggest obstacles, coming from Mandrake, were getting used to using .deb vs .rpms, which wasn't a big deal, just different (plus Mandrake's UPRMI is a very good tool), using gnome (I was a diehard kde fan, but now, I actually prefer gnome -- go figure!) and getting multimedia and various plugins working (since Ubunut only ships with "free" software).  Again, not a big problem, but did involve some learning, particularly coming from a distro that included just about anything you wanted.  It was at this point that I discovered how wonderful the community here is and to tell the truth, it was ultimately my deciding factor.

I hope you hang in there with Ubuntu and feel free to ask questions.  Chances are, somebody else has the same problem and more importantly, they've already found a fix for it.

I imagine, before too long, we'll see you posting answers to other people's questions.

I'm pretty confident in predicting that if you stick with Ubuntu for a while longer, you will grow even more comfortable with it and wonder why you would ever want to go back to your old distro (just wait to the next version release and you upgrade with a single command or a few mouse clicks)!

Joeb

---

### Post by jonrkc on 2005-06-13
Joeb, I was thinking just this morning what a contrast there is between Mandrake's user forums and Ubuntu's.  Nothing against Mandrake/Mandriva--but Ubuntu wins hands-down in the forum department!  I also frequent LinuxQuestions a lot and have over 900 posts there and have had the satisfaction of helping a lot of users with simple problems.  (I generally focus on the questions with zero responses!)

I was attracted by the philosophy behind Ubuntu: Linux for humans.  That's my kind of thinking.  I was originally put off by that infamous "controversial" art that Ubuntu featured for a while but dropped, I think due to numerous objections.  In contrast to that, I am CRAZY about the earth colors.  Finally a distro had the guts to drop BLUE.  What is it about blue, anyway?!  Also the earth colors fit well with the African-language name for the distro.

I hope that eventually Ubuntu will be able to have a mechanism similar to Mandriva's "upgrade" option for installation, which, though they won't officially seem to admit it, is just as much as anything a repair option.  In many cases it works extremely well, and it never seems to hurt anything even if it doesn't cure a problem.  It takes only about twenty minutes and for a busy person (I'm retired, but I STILL have a few other things to do than work with my computer all day) it can make a world of difference when there's a problem that just won't go away and resists easy solution.

I certainly plan to stick with Ubuntu, and, as you suggest, it's in considerable part because of the cohesive and helpful community that doesn't look down its collective nose at beginners.

Thanks for the encouragement.

---

### Post by desdinova on 2005-06-13
Jon

I've used *nixes since around 92, however I still do really STUPENDOUS mistakes.

Unlike you I wasn't happy enough to change the permissions in /usr - no, I did a rm * -rf in it as root by mistake....

Serious ouch

It as MDK 9.0, and I stopped it in time to be able to manually reinstall what I'd just lost - a 3 day recovery.

Bear with Linux, it truly is an exciting time to deal with it as it grows. Perhaps google for RUTE the free online book and relax and enjoy the disasters as they happen!

---

### Post by jonrkc on 2005-06-13
[QUOTE=desdinova]S mistakes.

Unlike you I wasn't happy enough to change the permissions in /usr - no, I did a rm * -rf in it as root by mistake....

Serious ouch  [...]

Bear with Linux, it truly is an exciting time to deal with it as it grows. Perhaps google for RUTE the free online book and relax and enjoy the disasters as they happen![/QUOTE]

Somebody joked, obviously innocently, about rm -rf the other day on a forum, and I pointed out as tactfully as possible to the person asking the initial question that unless he/she REALLY knew what they were doing, it would be best to avoid that command!  I've started using it quite often recently because of the horrid complexity of rmdir, but I always stop and think twice and double-check what I've typed before I hit "enter."

I've had the RUTE guide bookmarked for two years, and read large parts of it.  The only time it's let me down so far is in its discussion of mail, which must have either been MUCH simpler when it was written, or else the writer just didn't think of the fact that most users will have to struggle to get sendmail working (at all!) first, or struggle a lot less, but still work with postfix, before anything happens.  Otherwise, an excellent guide.

---

### Post by desdinova on 2005-06-13
The advantage of postfix is that the two main cf files are normally well documented, whereas sendmails cf file is just ughhhhhhhhhhhhhh! QMail is another that is worth configuring.

This is an unpopular opinion of mine, (borne from 12 years of sysadmin) - but I much prefer to use the command line to configure servers. I had more grief in 6 weeks with MS Exchange then 6 years with postfix and courier ;-)

I read a really good tip on using rm - to be sure, do the command with "ls" instead of "rm" and it will list exactly what files it will delete.....

---

### Post by Joeb on 2005-06-13
[QUOTE=jonrkc]

I hope that eventually Ubuntu will be able to have a mechanism similar to Mandriva's "upgrade" option for installation, which, though they won't officially seem to admit it, is just as much as anything a repair option.  
[/QUOTE]

Let me start by saying that I haven't tried this, but I did find this googling around a little bit:

apt-get --reinstall `dpkg --get-selections | grep install | grep -v deinstall | cut -d' ' f1`


Supposedly, it should reinstall every package installed on the system.  It was from the Debian Developers Mailing List, but as I said, I haven't tried it, so it might not work.

---

### Post by jonrkc on 2005-06-13
[QUOTE=Joeb]Let me start by saying that I haven't tried this, but I did find this googling around a little bit:

apt-get --reinstall `dpkg --get-selections | grep install | grep -v deinstall | cut -d' ' f1`


Supposedly, it should reinstall every package installed on the system.  It was from the Debian Developers Mailing List, but as I said, I haven't tried it, so it might not work.[/QUOTE]
It sounds mighty interesting, and mighty scary!  I don't see how in the world it could work from a running system--but how could it be done from an outside environment (i. e. "live" environment such as Knoppix)? Maybe if you went to the Knoppix environment and then did chroot [to wherever you mounted your installation needing repair] and issued the command?

Hmm!


I will copy this down and think about it quite a bit.  Thanks for the tip.

---

### Post by Joeb on 2005-06-13
[QUOTE=jonrkc]It sounds mighty interesting, and mighty scary!  I don't see how in the world it could work from a running system--but how could it be done from an outside environment (i. e. "live" environment such as Knoppix)? Maybe if you went to the Knoppix environment and then did chroot [to wherever you mounted your installation needing repair] and issued the command?

Hmm!


I will copy this down and think about it quite a bit.  Thanks for the tip.[/QUOTE]


I think it will ONLY work from a running system as it needs to read the installed packages from the running system (that's the dpkg --get-selections part, the grep parts tell it only to use the "install"ed ones and not any you have "deinstall"ed).  If you boot from the LiveCD (Ubuntu's or other's), it would be trying to read the dpkg database from the system you booted from.  Also, you would only have the repositories from the live environment, so if you booted from Knoppix, you would have Knoppix repositories and not Ubuntu ones.

If you ever want a list of everything you installed, you can just issue the dpkg --get-selection command it list all of the installed packages.

---

### Post by jonrkc on 2005-06-13
[QUOTE=Joeb]I think it will ONLY work from a running system as it needs to read the installed packages from the running system (that's the dpkg --get-selections part, the grep parts tell it only to use the "install"ed ones and not any you have "deinstall"ed).  If you boot from the LiveCD (Ubuntu's or other's), it would be trying to read the dpkg database from the system you booted from.  Also, you would only have the repositories from the live environment, so if you booted from Knoppix, you would have Knoppix repositories and not Ubuntu ones.

If you ever want a list of everything you installed, you can just issue the dpkg --get-selection command it list all of the installed packages.[/QUOTE]
Yes, I see the difficulty you're pointing out.  I don't understand, though, how the libraries in a functioning system can be restored without causing a catastrophic crash.  That's what happened to me the one and only time I tried doing something similar.  As soon as I got to libraries involved in the copy process (I was watching the verbatim output on the screen) the system exploded, or perhaps imploded would be a better term.  A couple of days later I was running again.

I don't see how this process could avoid the same pitfall...

---

### Post by Joeb on 2005-06-14
[QUOTE=jonrkc]Yes, I see the difficulty you're pointing out.  I don't understand, though, how the libraries in a functioning system can be restored without causing a catastrophic crash.  That's what happened to me the one and only time I tried doing something similar.  As soon as I got to libraries involved in the copy process (I was watching the verbatim output on the screen) the system exploded, or perhaps imploded would be a better term.  A couple of days later I was running again.

I don't see how this process could avoid the same pitfall...[/QUOTE]


Were you using the cp command instead of apt-get when it locked up?  I'm not sure why that would make a difference though.  I do know that you can do an upgrade with apt-get while the system is running and it works great.  I should add that I wouldn't do this while logged in through gnome, but instead from the command line.

---

