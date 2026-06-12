---
title: "Incomplete upgrade jaunty-&gt;karmic.  How do I complete the upgrade?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-11-15
Greetings.
I have not yet resolved the questions of my previous post but I have a new problem.

The upgrade downloaded 1730 packages and installed nearly everything.  It failed with errors related to TTF fonts. In the two attachments here, I have screen shots of the error messages. First "Upgrade Error Message.png" and then the completion status in "UpgradeComplete-Error.png".  Then the upgrade process stopped.  It did not proceed to the Cleanup phase.

The fonts problem was solved in Launchpad, URL
[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/464422]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/464422"), in items #39-41. (It also gives away my real first name.  OY! ;)  )

So now that the font problem is solved, how do I proceed to completing the upgrade?  So many questions!
[LIST]
[*]Is it safe to reboot?
[*]If I do reboot, and it works (this is in doubt) how do I get the cleanup phase completed.  It occurs to me that there is a lot of trash in there I could not possible get at manually.
[*]Should I rather restart the upgrade process, **_without rebooting_**, hoping that it will recognize where it was up to and continue from the cleanup phase?  Or will it still think it needs to do the font downloads, since the previous upgrade run did not succeed at that step.  ie. It would be oblivious to my independent success on that step.  I fear that this would undo my successful font download.
[*]Or would running the upgrade process again start all the downloads from scratch and overwrite the successful code modification listed in that LaunchPad discussion?
[/LIST]

I profusely thanked the contributor of the solution to the fonts problem in the LaunchPad discussion (imad) and would be similarly grateful for a solution to this conundrum.

Thanks much!

---

### Post by rpaskudniak on 2009-11-15
Greetings again.

Unfortunately, some situation required me to boot Windows while awaiting a response to my opening salvo in this thread.  Hence, some of Windows seemed to come up OK.  Now I have had the chance to reboot Ubuntu and it has worked OK with some kinks.  So only one point of the four I raised is still relevant.

> If I do reboot, and it works (this is in doubt) how do I get the cleanup phase completed. It occurs to me that there is a lot of trash in there I could not possible get at manually.

Well, here I am after the reboot and, as I mentioned, there are some kinks.  For starters, I tried running the Update Manager and it did not offer to remove a blessed thing.  I don't recall how many packages needed to be removed but I'm sure there's a lot of trash in there I would want removed.


As an example, one thing I did know to look for was Postgres:
> **jake@chief:~$ ps -ef | grep postgr**
postgres  1311     1  0 19:15 ?        00:00:03 /usr/lib/postgresql/8.3/bin/postgres -D /var/lib/postgresql/8.3/main -c config_file=/etc/postgresql/8.3/main/postgresql.conf
postgres  1313  1311  0 19:15 ?        00:00:00 postgres: writer process                                                                                                    
postgres  1314  1311  0 19:15 ?        00:00:00 postgres: wal writer process                                                                                                
postgres  1315  1311  0 19:15 ?        00:00:00 postgres: autovacuum launcher process                                                                                       
postgres  1316  1311  0 19:15 ?        00:00:00 postgres: stats collector process                                                                                           
postgres  1429     1  0 19:15 ?        00:00:04 /usr/lib/postgresql/8.4/bin/postgres -D /var/lib/postgresql/8.4/main -c config_file=/etc/postgresql/8.4/main/postgresql.conf
postgres  1512  1429  0 19:15 ?        00:00:00 postgres: writer process                                                                                                    
postgres  1513  1429  0 19:15 ?        00:00:00 postgres: wal writer process                                                                                                
postgres  1514  1429  0 19:15 ?        00:00:00 postgres: autovacuum launcher process                                                                                       
postgres  1517  1429  0 19:15 ?        00:00:00 postgres: stats collector process

Notice: There are two separate sets of Postgres PIDs: The 8.3 version, starting from PID 1311, and the 8.4 version, starting from PID 1429.

Running Synaptic, I see no way to remove the 8.3 stuff - it just does not show up! :confused: So how do we remove the blessed thing?!

So it come down to these questions:
[LIST]
[*]How do I lose the 8.3 postgres?  This is the only package I **know** I need to lose.
[*]How do I determine what other packages needed to be deleted/uninstalled/updated?
[*]How do I actually  delete/uninstall/update these packages?
[/LIST]

I think I need guru-level help here. @:-{)  (Smiley wearing a turban?)

Thanks much!

---

### Post by rpaskudniak on 2009-11-15
Ignore me long enough and I eventually come up with a solution, eh? :evil:

At least that was the case for Postgres 8.3.

I typed in 8.3 in the filter panel and a this displayed postgresql-8.3 plus a few other 8.3 items, some installed, some not. When I marked postgresql-8.3 for removal, Synaptic also marked postgresql-plperl-8.3.  I removed these and watched it stop the 8.3 engine.  It also displayed some other postgresql items from release 8.3:
[LIST]
[*]postgresql-client-8.3
[*]postgresql-doc-8.3
[*]postgresql-server-dev-8.3
[/LIST]
I removed these as well, in a separate run.

Still, what about the other thousand or so now-obsolete packages I'd love to remove as part of that cleanup that never happened.  I still need to be able to identify them and remove them.

My guess is that the upgrade process built a script of dpkg-remove commands to execute when the install step (the 1730 packages) would complete. If so, where in *&^%! is that ^%^&* script?  I would edit it to remove the references to postgresql and then let 'er rip.

Hmm... I'm beginning to rant.  Please help me before I fall off the deep end.

Thanks much!

---

### Post by robert leleu on 2009-11-16
In 9.10, after having installed opendns, I could install ttf-mscorefonts....

the only point is that it changed somewhat the presentation of some works I had made using MSfonts which were in fact replaced by linux substitute....son I had to revamp a bit.

---

### Post by rpaskudniak on 2009-11-18
Robert said:
> In 9.10, after having installed opendns, I could install ttf-mscorefonts....
Robert,

As I have already stated, I no longer have a problem with the ttf-mscorefonts, having removed the --dns-timeout option from the wget command.  Installing opendns is an option I had no reason to think of but if that works, it is a solution to the bug in the upgrade process:  Merely install opendns as part of the operation.  This is a job for the Ubuntu team.  Or similar super-heroes. 

Still seeking that solution..

---

### Post by rpaskudniak on 2009-11-19
Hoo Boy!  Hey, not all at once, you'll overload the server! :?

OK, sarcasm aside:

Recall that the solution [I used] to get the TTF to install was to edit file /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst to remove the --dns-timeout option from a wget command.  (I recall later seeing something about a better DNS patch but I don't recall what it was.)

This gave me an idea about looking into the other .postinst files as part of the cleanup process.  I have found 1388 .postinst files in this directory.  The problem is, of course, that I have no way to be certain these are actually for cleanup - it's even more likely they are for completing the installation process of software going into place.

I also found 1070 files suffixed .postrm

Can anyone tell me for certain what these files are for?  What they do?

Also, the consequence of running them again if they have all been successfully run already?  (Though I am chastened by another experience and won't risk it in any case.)

FWIW, I have attached the directory listings of these mysterious files; the attachment is mysteryFiles.tar.

I wouldn't mind some useless stuff hanging around my directories for want of a cleanup.  Perhaps they are as innocuous as dead yeast in beer.  BUt in my experience, obsolete software hanging around manages to grow legs and an ego; it will somehow get executed instead of the up-to-date stuff.  My desire to finish that cleanup is fueled by this paranoia.

Still awaiting sound advice...

---

### Post by HeadHunter00 on 2009-11-19
soory man, I don't know a thing about this bug.

---

### Post by Fingerpickin on 2009-11-28
Hi,I had the same original problem and question as you after a 9.1 upgrade. I found something called Computer Janitor under System/Administration. It came up with 81 redundant packages and got rid of all bar 15 of them. When you try to get rid of last 15 it comes says could not clean up properly and error: "E:Sub-process /usr/bin/dpkg returned an error code (1)" so partial success maybe?

---

### Post by rpaskudniak on 2009-11-29
That solution was finger-pickin' good! :D

As with your case, it left a bunch of packages installed.  I unchecked a couple myself because I wanted the utilities and I did not think there was a new version of them.  However, 15 or so libraries remained stuck in place.

I unchecked all but one  and tried to uninstall that one library.  The janitor just hung and I killed it a couple of hours later.  I get the picture - it ain't gonna happen.  But it was nice to do that much clean-up.  Perhaps I can enter a bug for the proper removal of those libraries.

Of course, I won't mark this thread as solved until I get rid of all that.  But it was a big step in he right direction.

Thanks much!

---

### Post by thanatoast on 2010-01-10
I assume you've have no luck?
I just want to add a "me too" post.  I had the exact same problem.  Ms fonts failed, said it was doing a recovery, upgrade complete but with errors, but skipped over the cleanup and restart.

---

