---
title: "Updating issues"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by Penny N. Nickels on 2013-12-31
I upgraded to 12.04 about a year ago and have been having issue after issue. I am now spending more time on another computer than this one, so I am not doing the updates at regular intervals. My most recent issue, I cannot find anything here that covers it. When I try to install the updates/upgrade with the update manager, I get a message that a couple items ([COLOR=#ff0000]python-problem-report[/COLOR] & [COLOR=#ff0000]python-lazr.restfulclient[/COLOR]) are damaged. I cannot get the other updates there installed. When I've done it in the terminal, the messages I get read: 

dpkg - error processing [COLOR=#ff0000]file name[/COLOR] (--configure): Package is in a very bad inconsistant state - you should reinstall it before attempting configuration

And, still, none of the other updates are installed. Over at synaptic, I am unable to reinstall either one of those files. I have tried so many things ... apt-get -f install, --configure -a, clean, update, ... I've lost track! With the update manager, and in synaptic, I have tried to untick those to see if I could get the other updates installed. Those 2 keep on coming up, preventing the process. I am at a loss and turning to you here, to see if anyone can resolve my issue. Thank you in advance!

---

### Post by zealibib slaughter on 2013-12-31
have you tried dpkg -P package_name by chance then reinstall the package

---

### Post by Penny N. Nickels on 2013-12-31
> have you tried dpkg -P package_name by chance then reinstall the package

That's one I've not tried. I will try it and let you know what happens. Thanks!

---

### Post by Penny N. Nickels on 2013-12-31
I tried the suggestion to purge then reinstall. And this is what I got:

> marilyn@marilyn-desktop:~$ sudo dpkg -P python-lazr.restfulclient
[sudo] password for marilyn: 
dpkg: dependency problems prevent removal of python-lazr.restfulclient:
 python-launchpadlib depends on python-lazr.restfulclient (>= 0.11.2-1).
dpkg: error processing python-lazr.restfulclient (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 python-lazr.restfulclient
marilyn@marilyn-desktop:~$ sudo dpkg -P python-problem-report
dpkg: dependency problems prevent removal of python-problem-report:
 python-apport depends on python-problem-report (>= 0.94).
dpkg: error processing python-problem-report (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 python-problem-report
marilyn@marilyn-desktop:~$ 



As you can see, it didn't work. Thank you anyway. I am open to other suggestions to get this issue resolved.

---

### Post by steeldriver on 2013-12-31
Do you have any active ppas in your sources? they can sometimes cause dependency problems

```
grep -r '^[^#].*ppa' /etc/apt
```

---

### Post by zealibib slaughter on 2014-01-01
since these are python packages I assume that a apt-get purge python* will purge all of python but you will have to write down exactly what is being removed so you can reinstall.  Also you may need to purge the packages that are already downloaded in var/cache/apt/archives.  Careful though purging python may/can/most likely will remove a large part of your os. You may also want to check the health of your hard disk.  The times I have had problems like this it was due to a failing drive.

---

### Post by Penny N. Nickels on 2014-01-05
> Do you have any active ppas in your sources? they can sometimes cause dependency problems

I don't have any ppas in my sources.

> You may also want to check the health of your hard disk.  The times I have had problems like this it was due to a failing drive.

I think you might be on to something. How do I check my hard disk?

---

### Post by Bashing-om on 2014-01-05
Penny N. Nickels; Hi !

A quick check is to activate "disk utility" and run the S.M.A.R.T routine on the hard disk(s).

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by Penny N. Nickels on 2014-01-27
I'm sorry it has been a while.

> A quick check is to activate "disk utility" and run the S.M.A.R.T routine on the hard disk(s).

It states that I have a few bad sectors. I'm guessing that means that the hard disk is probably the root of my trouble and needs to be replaced. I really wish it didn't come to that. Thanks for the help.

---

### Post by Bashing-om on 2014-01-27
Penny N. Nickels; Weehll,

A "few" bad sectors may not be a real bad thing, there is no perfect hard drive, and provisions are made to map our "bad" sectors and use the spares.

If you have a problem reading the SMART data output, post it here and we will take a look at it and advise.

[INDENT][INDENT]I have been hasty a few times in my life
[INDENT][INDENT][INDENT]luckily, I am still here to regret those times
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Penny N. Nickels on 2014-01-28
I'm not sure how do I share the data. Almost all of the attributes were either GOOD or N/A, except for Relocated Sector Count. That one came up as red (Warning) with a value of 7 sectors. Anything else? I really appreciate all the help you're giving me!

---

### Post by Bashing-om on 2014-01-28
Penny N. Nickels; Hey:

That is not good at all ..Heed the warning - RED do mean a serious problem. The safe thing to do;
Back your data up, replace that drive ! Now, before the situation gets worse and you can not retrieve your data.
Then one may wipe that drive and (re)use it in non critical application after zeroing out the drive and putting a new partition table(s) in place. Never trust that drive again though It is always nice to have a "transfer files" or what not drive around.

The SMART data is not lying to us, heed the warning, hard drives only have a limited lifetime.

[INDENT][INDENT]hey 
[INDENT][INDENT][INDENT]just what I have done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Penny N. Nickels on 2014-01-28
I had feared that I would have to replace the hard drive. Replacing the drive will be easier said than done since I currently don't have finances. How would I know what type of hard drive to get to replace it, when I financially can, that is? As for backing up my data, how would I do that? If it involves putting it on CD, I have a bit of problem there, too, because my burner is also acting up. Thank you for your help!

---

### Post by Bashing-om on 2014-01-28
Penny N. Nickels; Pardon me if you have said,

And I do not remember, This is a laptop or a desk top machine ?
Lap tops may be a real chore to tear into !
Desk tops ->easy to access.

Generally Harddrives are mainly 2 types:
a) IDE drive, flat cables 40 or 80 conductors in that ribbon;
b) SATA round small cable (pencil size) with a separate power cord. .

Ya might Google your machine and get the specs and what drives it came with.
One place - I frequent a lot - is:
[http://www.newegg.com/](http://www.newegg.com/)
to price/purchase a new drive. I can pay big time to shop around .

As to backup, well USB thumb drive ? depending on how much data ya back up,  a 4 gig drive may be good enough.

Do not feel bad, we have all been there and done that. Just a fact, hard drives die. That is a primary reason why one keeps GOOD backups.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Penny N. Nickels on 2014-01-28
It's a desktop computer. I know that I have seen IDE mentioned in something on this computer. I should start there, I guess. I will check into the USB thumb drive for the back up. I thank you very much for all the help you've been giving me! I will inform you when I get the new hard drive. Thanks!

---

### Post by Bashing-om on 2014-01-28
Penny N. Nickels; Ha !

Help is what we do.

Desk top, piece of cake.

two phillips head screws at the back of the case, holding on a side, slip the side of the case off, and have a look at the cables on the hard drive. If you do not pull the external wiring, takes two minutes tops .

[INDENT][INDENT]easy peasy
[/INDENT][/INDENT]

---

