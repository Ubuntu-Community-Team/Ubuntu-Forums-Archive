---
title: "aptitude on dapper wants to remove lots of packages"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2006-06-09
I recently upgraded to dapper Kubuntu.

I usually use aptitude to keep my system up-to-date.  But, since upgrading to dapper, when I do:

    $ sudo aptitude update
    $ sudo aptitude -s upgrade

aptitude wants to remove over 100 packages, some of which I want to keep and others I unsure of.  apt-get does not try to remove all those packages, so I've gone back to using apt-get.

Is anyone else using aptitude with dapper and having this kind of problem?

Is there anywhere I can read about the differences between aptitude and apt-get.  And, if there are these kind of differences between aptitude and apt-get, are there also differences in adept, kpackage, synaptic, etc?  Does this mean that once I start using one of these package managers, I should not switch to another and that, for example, I should not use one on one day and another the next day?

I've done several Web searches for info on aptitude, but have not found much.

Thanks for guidance.

Dave

---

### Post by John.Michael.Kane on 2006-06-09
dkuhlman Look here **[Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware.php")**

---

### Post by dkuhlman on 2006-06-13
A little follow-up to my own message.

I finally did an upgrade using aptitude.  I did:

    $ sudo aptitude upgrade

And, aptitude did indeed remove lots of stuff.

I started by trying to re-install several individual things, but then learned that I had lost the ability to boot/logon to a KDE session.

After a bit of struggling, I fixed things by doing:

    $ sudo aptitude install kubuntu-desktop

Now, all is well.  I can once again logon to a KDE session and most (if not all) of the KDE apps that I want are there.

So, now I am once again able to use aptitude to do my upgrades.

But, if I use the aptitude GUI interface, that is, if I type:

    $ sudo aptitude

then (within the GUI interface) aptitude still wants to remove lots of stuff.  So, I'm staying away from the aptitude GUI.

Hope this helps someone who is also struggling with aptitude.

And, if anyone knows of a place to find more information about aptitude (other than the docs in file://localhost/usr/share/doc/aptitude/html/en/index.html, please let me know.

Dave


Dave

---

### Post by 5-HT on 2006-06-13
[quote=dkuhlman]... aptitude still wants to remove lots of stuff.  So, I'm staying away from the aptitude GUI.

Hope this helps someone who is also struggling with aptitude.[/quote] 
There could be many reasons why aptitude is trying to remove all those packages, and aptitude will let you know why it's trying to remove things automatically. 

Using aptitude from the CLI, or GUI, are there any indications of why it's trying to remove all those packages?

My first guess would be that you have a broken package(s), most likely kubuntu-desktop (or another metapackage).

If you go into aptitude's pseudo-GUI and select Search -> Find Broken, you will get a listing of all broken packages. By selecting (press enter) each one, you'll get a listing of unmet dependencies. If a broken package(s) is the problem, hopefullly that information will be enough to get you started from and resolve the issue.

[quote=dkuhlman] And, if anyone knows of a place to find more information about aptitude (other than the docs in file://localhost/usr/share/doc/aptitude/html/en/index.html, please let me know. [/quote] I don't have that file installed, but the Aptitude README which details _ALL_ aspects of Aptitude can be found in /usr/share/aptitude/README (hope it's not the same information).

Hope that helps.

---

### Post by dkuhlman on 2006-06-14
[QUOTE=5-HT]

If you go into aptitude's pseudo-GUI and select Search -> Find Broken, you will get a listing of all broken packages. By selecting (press enter) each one, you'll get a listing of unmet dependencies. If a broken package(s) is the problem, hopefullly that information will be enough to get you started from and resolve the issue.[/QUOTE]

Thanks for pushing me on this.  I guess I needed encouragement to take on the task of cleaning up those problems that the aptitude GUI was complaining about.

What I did:  Mostly I did "aptitude reinstall" using the CLI for all that packages that the aptitude GUI said it wanted to remove (except for a few that I was sure I would not need).  There is probably a quicker, easier way to do this, perhaps in the aptitude GUI itself, but I was unsure about what would happen and did not want to destroy my system.

Now when I bring up the aptitude GUI and press "g", aptitude reports that there is nothing to be installed, removed, or upgraded.  So, I believe that I can now successfully use the aptitude GUI.

[QUOTE=5-HT]
I don't have that file installed, but the Aptitude README which details _ALL_ aspects of Aptitude can be found in /usr/share/aptitude/README (hope it's not the same information).[/QUOTE]

Yes.  It's the same document in a different format.  However, thanks for pointing it out to me.  It's more "grep-able".

Thanks again.

Dave

---

### Post by 5-HT on 2006-06-14
[quote=dkuhlman]

What I did:  Mostly I did "aptitude reinstall" using the CLI for all that packages that the aptitude GUI said it wanted to remove (except for a few that I was sure I would not need).  There is probably a quicker, easier way to do this, perhaps in the aptitude GUI itself, but I was unsure about what would happen and did not want to destroy my system. [/quote] 
If I have any broken packages that result in Aptitude wanting to remove a plethora of other packages, I usually try to see if there is one (or a couple) of unmet dependencies that are the cause (I start with big[ish] meta-packages first, or anything I recently installed/upgraded/removed). If I can find the culprit package(s), a reinstall (or just pressing + in the text-based-GUI) solves everything...the tricky part can be in finding the package(s), however.

Using Aptitude's own resolver is probably a better way to sort these kinds of problems out. If you start aptitude in its text-based-GUI mode, the resolver will display - with large red warnings - broken packages and will even offer you suggestions of how you can resolve them.

[quote=dkuhlman]
Now when I bring up the aptitude GUI and press "g", aptitude reports that there is nothing to be installed, removed, or upgraded.  So, I believe that I can now successfully use the aptitude GUI.
[/quote] 
Congrats! 
Whatever the problem was, you've solved it!

---

