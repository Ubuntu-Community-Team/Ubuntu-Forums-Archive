---
title: "Need to install Folio (NFO files) on Edgy with wine. Please Help!"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by sit properly on 2007-04-04
Hi folks. 

I'm nearly at my wits end with this. 

For the past week or so, I've been trying to install FolioViews (a program for viewing NFO files) in Edgy with wine. 

No matter what I'm doing, I'm getting errors. (Mostly, the "Unload the debugger and try again"). I'm installing this from a DVD-ROM.  It is supposed to install pretty seamless (as per: [this](http://appdb.winehq.org/appview.php?iVersionId=2115) ). 

At this point, I don't know what I'm doing wrong. I *did* get a version of it installed, but it wouldn't run. 

The link above says that I need to install dcom95. I think I did that, but I'm not really sure.

It's amazingly important that I get this program on my laptop (Sony C series, btw). If someone would be willing to help me, I would be so grateful. 

I'm fairly new to Linux, so keep that in mind. 

If there are other ways to view NFO files with special fonts (in this case, sanskrit and bengali), I'd be open to that as well.  I just need to get this up and running. 

Thank you very much!

eric


edit= I've been able to get another version of it installed - it even shows up under Applications > Wine > Programs. I'll click it and nothing happens. Ugh.

---

### Post by Stephen Howard on 2007-04-04
> "Unload the debugger and try again"

That sounds like the kind of error a program will give if it thinks its detected someone trying to crack it (ie pirate or remove copy protection).  Basically, crackers use debugging software like Softice to trace the execution of the code and by-pass copy protection.  Perhaps the installer is seeing that there's something odd going on (in installing under wine rather than windows) and is throwing an exception error.

---

### Post by Stephen Howard on 2007-04-04
regarding the older version, bring up a terminal window and run it with:  

```
wine your-program-name-goes-here
```

see what error messages come out.

---

### Post by sit properly on 2007-04-04
well, when i do that, i get this:
wine: could not load L"c:\\windows\\system32\\Views.exe": Module not found

it seems that from the command line, it will only "look" for the program in system32. if i install the program in system32, i get missing dll file errors. 

if i load those dlls in system32, it tells me that the viewer needs to be updated to view the nfo files (which I know it doesn't need to be as it works on windows). 

even though others have been able to get Folioviews running in wine, i'm having major doubts here. 

i'm looking into virtualbox, but at this point everything seems like a major pain in the ****.

---

### Post by Stephen Howard on 2007-04-05
Hmm, the wineHQ database lists [it as working]("http://appdb.winehq.org/appview.php?iVersionId=3919&iTestingId=2543").  Maybe there's something wrong with your wine setup?

I also found this on the [wineHQ db]("http://appdb.winehq.org/appview.php?iAppId=1557"):
> I first Installed dcom95 [http://frankscorner.org/modules.php?op=modload&name=Sections&file=index&req=viewarticle&artid=114&page=1]("http://frankscorner.org/modules.php?op=modload&name=Sections&file=index&req=viewarticle&artid=114&page=1") Note: You need a valid Microsoft Windows license to install dcom95. Then the setup worked easiely with: wine Setup.exe And I run the program with: wine Views.exe

The frankscorner link is now invalid, but [this]("http://frankscorner.org/index.php?p=office97") is a similar link at the same site about installing dcom95.

---

