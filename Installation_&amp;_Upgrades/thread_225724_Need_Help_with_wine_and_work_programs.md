---
title: "Need Help with wine and work programs"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by jdseek on 2006-07-30
I have 2 more hurdles to overcome before I can format my windows partition.


Both relate to wine and programs I need for work.

First, AcroFill.exe (a form filler outer for windows, used to fill in my trip reports and other company forms) appears to work except when loading my forms, the text is missing.

Here is the terminal output


```
me@mybox:~$ wine /home/me/.wine/drive_c/Program\ Files/Acro\ Software/FormMax\ Filler/AcroFill.exe
fixme:ole:CoRegisterMessageFilter stub
```


The second issue is DriversDailyLog.exe won't run at all.  Here is the output.

```
me@mybox:~$ wine /home/me/.wine/drive_c/Program\ Files/Drivers\ Daily\ Log/DriversDailyLog.exe
fixme:ole:CoRegisterMessageFilter stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  135
  Current serial number in output stream:  135
me@mybox:~$
```

I have had both of these programs working with wine under suse 10. So I know they are compatable.
What do I need to do to make them both work?

Thanks, JD

---

### Post by jdseek on 2006-07-30
I hate to say it, but I have found no workable solutions for this problem.  I have tried every howto I have found and even removed wine and compiled from source and still the same error.  I was told in irc.freenode.net #winehq " it's not a wine issue, your X is bad"  but that person would not elaborate.  I have to have wine running for some work related programs.  And I have to do so quickly.
As much as I don't want to, I may have to reinstall suse 10 as these programs worked fine there.  That would suck, I would not have internet connectivity via my EVDO card.  Not to mention, SuSE 10 is slooooow.


Please Help.
JD

---

