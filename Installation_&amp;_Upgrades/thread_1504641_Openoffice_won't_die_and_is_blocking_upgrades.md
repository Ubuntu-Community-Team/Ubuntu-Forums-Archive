---
title: "Openoffice won't die and is blocking upgrades"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by rifter on 2010-06-08
](*,)I am trying to upgrade packages on my system, and I have openoffice installed.
When I try to do an upgrade, I get the following message:

> 
OpenOffice.org is running right now. A running OpenOffice.org makes extension (de-)registration not possible and it causes problems with (de-)registering components.

Please close OpenOffice.org (including an eventually running Quickstarter).


I don't have a quickstarter in my systray, and the quickstarter is unchecked in the settings in openoffice.  I do, however, have the following processes running:

> 
docvert  22867     1  0 07:32 ?        00:00:00 /bin/sh /usr/share/docvert/core/config/unix-specific/openoffice.org-server.sh
docvert  22869 22867  0 07:32 ?        00:00:00 /bin/sh /usr/bin/soffice -headless -norestore -nologo -norestore -nofirststartwizard -accept=socket,port=2002;urp;
docvert  22884 22869  0 07:32 ?        00:00:00 /usr/lib/openoffice/program/soffice.bin -headless -norestore -nologo -norestore -nofirststartwizard -accept=socket,port=2002;urp;


If I kill them (with sudo kill) and try to push forward with the upgrade, they just come back immediately.  These are the only processes running under the docvert and besides the upgrade processes are the only processes that show up with the string (using grep -i) "office".

Not only does having these processes stop the upgrade of openoffice, but even when I say to go ahead with a partial upgrade, everything else doesn't get upgraded either (which I don't think should happen; if on package or a set of packages fails to upgrade the rest of them should get upgraded anyway unless they depend on the failed packages, which in this case they do not).

I'm pulling my hair out because these processes keep coming back, which they should not imho, in fact I would like never to see them again because I don't want office running unless I start it! :evil:  And of course I would like to be able to upgrade office so it is the latest when I do start it. :mad:

Any ideas?

---

### Post by dabl on 2010-06-08
How about rebooting your system, and on the greeter choose a command line session?  (Or you could reboot and choose "Recovery" mode).

Doing this, GDM will not be running.  To make sure, issue ```
sudo service gdm stop
```

Now

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get clean

```
```
sudo service gdm start
```

Should put you back in Gnome with all packages updated.

---

### Post by rifter on 2010-06-08
> **dabl said:**
> How about rebooting your system, and on the greeter choose a command line session?  (Or you could reboot and choose "Recovery" mode).

Doing this, GDM will not be running.  To make sure, issue ```
sudo service gdm stop
```

Now

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get clean

```
```
sudo service gdm start
```

Should put you back in Gnome with all packages updated.

That's not a bad idea, although I'm not sure those openoffice processes won't still be starting.  They seem to be processes for the openoffice server, and are set for headless mode which means they would start without a display.  Even so, I will give it a whirl.  It couldn't hurt to try.

I think I'd better do
> 
sudo apt-get upgrade


instead of dist-upgrade because I am not ready to upgrade to lucid yet.

---

### Post by itsjustarumour on 2010-06-08
> **rifter said:**
> That's not a bad idea, although I'm not sure those openoffice processes won't still be starting.  They seem to be processes for the openoffice server, and are set for headless mode which means they would start without a display.  Even so, I will give it a whirl.  It couldn't hurt to try.

I think I'd better do


instead of dist-upgrade because I am not ready to upgrade to lucid yet.

Slightly simpler version, worked for me:

Log off
Ctrl+Alt+F1

```
sudo apt-get upgrade
```

Ctrl+Alt+F6
Log back in

:)

---

### Post by bumanie on 2010-06-08
You could also put top into terminal, view the PID of open office and then in another terminal kill the process via > sudo kill -9 <PID number>

---

### Post by rifter on 2010-06-09
> **bumanie said:**
> You could also put top into terminal, view the PID of open office and then in another terminal kill the process via

You're missing the point.  I killed the processes over and over but they just came back.

Anyway this is what I figured out.  I rebooted into single user mode and made sure the processes weren't running.  Then I tried to do the upgrade, and got the error again because they were getting restarted. ](*,) Apparently when you try to update certain openoffice packages, they start these processes I was listing before and then complain that they are started so they will not do the upgrade.

So I said "Fine, you know what, I will just uninstall openoffice; then it won't be able to be started so I will be able to reinstall it and not get those errors!"  Ah, grasshopper, it was not so easy as that.  You see, when you UNINSTALL the packages, they start those same processes again also, and then complain that they are started! :evil:

What I ended up having to do was go and back up /etc/passwd and /etc/shadow and then delete the whole line for the docvert user (I did not want the rest of the stuff deleted in case my plan did not work).  Not being a programmer, I think if the uid (the number not the name) does not exist in /etc/passwd you can't change to that user.  Then those processes could never start! :idea:

This actually worked.  What I had to do first is use apt-cache search to find all the openoffice.org packages and list them in a file so I could give them as arguments to apt-get remove. Since I used the script command to record the whole session I was able then to find all the packages that actually got removed and reinstall them.  (I could have used the apt logs, but call me lazy).  \\:D/  Oh and after I did the uninstall I put the original /etc/passwd and /etc/shadow back to make sure docvert had the same uid when the packages got reinstalled so his home directory would work.  :-\"

I learned two things about this set of packages in this adventure.  The first is that openoffice actually tries to delete the docvert user when you do the uninstall but it fails.

> 
/etc/init.d/docvert-converter: 126: cannot create /var/run/docvert/converter.pid: Directory nonexistent

> 
Removing docvert-openoffice.org ...
Removing user `docvert' ...
Warning: group `docvert' has no more members.
userdel: user docvert is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel docvert' returned error code 8. Exiting.


Now docvert's shell is /bin/false so he cannot log in normally, however when those processes I was talking about start, they run as docvert, so that is probably what it is on about.

The following packages seemed to cause those processes to start and then give errors (or at least these are the ones I got errors on the last time I tried this, before I deleted the docvert entry in /etc/passwd and /etc/shadow

> 
openoffice.org-evolution
openoffice.org-sdbc-postgresql 
openoffice.org-presenter-console 
openoffice.org-pdfimport
openoffice.org-wiki-publisher
openoffice.org-filter-binfilter


So, long story short, I got this to work, but only by nasty, ugly, highly dangerous hacks that no one should even try much less have to do.  As things are, I will probably find I have some cleanup yet to do (in particular the dbgsym packages, which can't be installed normally because they have to be supplied with a version number on the command line... big mess. And I need to double check that other packages were not affected.  But if I did this right, I should have all the packages back that were deleted, and probably the dbgsym ones will need to be reinstalled so they match the right version number.

What irks me more is that I will have to do this again every time I try to upgrade.  So I am going to push something upstream and see if I can get some devs to bite.  I can't be the only person getting these errors, or if I am I can get a better answer on why and how to deal with it next time I need to upgrade openoffice.  I vaguely remember having to completely uninstall openoffice to upgrade it another time, but I am sure I did not have to go through this many hoops, and in that case my problem turned out to be in some unrelated font package that hosed nearly everything.

So, I fixed it, but this is not the right answer.

---

### Post by rifter on 2010-06-09
> **itsjustarumour said:**
> Slightly simpler version, worked for me:

Log off
Ctrl+Alt+F1

```
sudo apt-get upgrade
```

Ctrl+Alt+F6
Log back in

:)

No the upgrade won't work because the openoffice processes are running, and when you kill them they come back.  You missed that in my original post.  If apt-get upgrade had worked, I would never have had to make this post in the first place.  Thank you for trying though.

See my post below for what I ended up doing.

---

