---
title: "software centre will not launch, no error message"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by itsme91 on 2011-01-06
Hi everyone,

my problem is simple: the software centre and firefox do not run when i try to launch them from any icon or with Alt+F2. The "Window List" app in the bottom panel shows "Starting Ubuntu Soft..." or "Starting Mozilla Firefox" but that just disappears again after a few seconds and thats it (no error message whatsoever).
I just installed Ubuntu 10.10 (new install - no upgrade) and it runs without problems on my other computer.

Ps: I managed to get firefox running with 'gksudo firefox' but not the software centre (i am not so good with all the commands yet :P ) and i dont want to have to do that alle the time

your help is very much appreciated (even a link to a thread i have not found despite a long long research)
itsme :)

---

### Post by oldos2er on 2011-01-06
Could you run **gksu software-center** in a terminal, and if it fails to open, please post the terminal output here.

---

### Post by tommcd on 2011-01-06
> **itsme91 said:**
> 
Ps: I managed to get firefox running with 'gksudo firefox' ...

You should not need to use *gksudo* with Firefox, since you can (and should) run Firefox as a normal user, and not with root privileges. Try running Firefox from the terminal simply by running *firefox*. If you get errors, then post them here.
Also, try renaming your *~/.mozilla* directory to *~/.mozilla.bak* and then launch Firefox. This will help to rule out a corrupted profile.

---

### Post by jimd562000_1 on 2011-01-06
go into system monitor (administration, system monitor) , find any running instances of software center, and end them. i have the same problem. Don't know why, but that is the temporary solution.

---

### Post by itsme91 on 2011-01-07
Heya,

thank you very much for your fast answers! the renaming of the firefox worked perfectly, so i consider that one fixed :) thank you tommcd!

@[oldos2er]("http://ubuntuforums.org/member.php?u=338320") :
I can start the software centre by typing **gksu software-center **but this is what appears in the terminal anyway:

 [B]johannes@johannes-laptop2:~$ gksu software-center
2011-01-07 18:09:34,514 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-01-07 18:09:34,514 - root - WARNING - failed to add sca db Couldn't detect type of database
2011-01-07 18:09:39,186 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2011-01-07 18:09:39,186 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/update.py', 367, '_error_cb')'
2011-01-07 18:09:39,186 - root - WARNING - error: Operation not supported
2011-01-07 18:09:39,357 - softwarecenter.app - INFO - software-center-agent finished with status 1
2011-01-07 18:09:42,222 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-01-07 18:09:42,222 - dbus.proxies - ERROR - Introspect error on :1.50:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.61" (uid=0 pid=1953 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.50" (uid=0 pid=1644 comm="/usr/bin/python))
2011-01-07 18:09:50,279 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-01-07 18:09:50,279 - root - WARNING - failed to add sca db Couldn't detect type of database
[/B]

what do i have to do to start it normally? can i rename it just like firefox?

thanks ahead

PS: @jim: there is no running instance of softwar centre :/

---

### Post by oldos2er on 2011-01-07
I would try using Synaptic (System, Administration, Synaptic Package Manager) instead of software center.

---

### Post by itsme91 on 2011-01-07
[oldos2er]("http://ubuntuforums.org/member.php?u=338320"): interesting! didn't know that one thanks

but still: I'd like to solve the problem once and for all and not just avoid it :P

---

### Post by tommcd on 2011-01-07
> **itsme91 said:**
>  the renaming of the firefox worked perfectly, so i consider that one fixed ...
If renaming *~/.mozilla* to *~/.mozilla.bak* fixed the problem, you may have had an addon in your profile that had gone rogue on you. If you use addons, try adding them back one by one. This way if Firefox fails to start you will know which addon caused it.
> **itsme91 said:**
> 
I can start the software centre by typing **gksu software-center **but this is what appears in the terminal anyway ...
There is a bug report on Lauchpad that is similar to this:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/618411](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/618411) It is described as being fixed. But there is also a similar bug report for Ubuntu 11.04 alpha:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/684887](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/684887)
> **itsme91 said:**
> 
what do i have to do to start it normally? can i rename it just like firefox?
So are you able to use the software center now? Are you able to install packages using the software center?
I am not sure how to fix this. I don't use the software center. I do all my package updates and installs using the terminal. I use *aptitude* for searching for stuff; and I use *apt-get* to update, install, and remove packages.

---

### Post by oldos2er on 2011-01-08
> **itsme91 said:**
> [oldos2er]("http://ubuntuforums.org/member.php?u=338320"): interesting! didn't know that one thanks

but still: I'd like to solve the problem once and for all and not just avoid it :P

Understood. I don't use Software Center (in fact I've uninstalled it) so perhaps someone who does can help you further.

---

### Post by itsme91 on 2011-01-16
mhhh so i've tried all the propositions but nothing worked so far! (coulnt do much with the bug-reports :/ )

I can use the software center once i opened it with **gksudo software-center**!

I also reinstalled it using the synaptic package manager and that did noch change a thin!
The whole add-on thing doesnt make much sense to me because as far as i am aware the software center does not have any add-ons and if so i did not install them!

What i did before it stoppped working, was changing the appearence of ubuntu (got the clearlooks theme now)! might that be related?

I used the package manager during the week but today i was looking for skype and i didnt find it so i guess i do need the software center.

thanks for you help so far and in future :)

---

### Post by tommcd on 2011-01-19
> **itsme91 said:**
> 
The whole add-on thing doesnt make much sense to me because as far as i am aware the software center does not have any add-ons and if so i did not install them!

My suggestion about rogue addons was for your Firefox problem, which you have said was solved:
> **itsme91 said:**
> 
thank you very much for your fast answers! the renaming of the firefox worked perfectly, so i consider that one fixed thank you tommcd!
The software center is a work in progress. I would either just use synaptic, or learn how to use apt-get from the terminal (which is what I do) and forget about the software center if you are having problems with it.

---

### Post by mangamanray on 2012-09-09
File "/usr/bin/software-center", line 44, in <module>
    from softwarecenter.utils import ExecutionTime
  File "/usr/share/software-center/softwarecenter/utils.py", line 34, in <module>
    import xml.sax.saxutils
ImportError: No module named xml.sax.saxutils
 wont open it or anything but firefox

---

### Post by tommcd on 2012-09-09
> **mangamanray said:**
> File "/usr/bin/software-center", line 44, in <module>
    from softwarecenter.utils import ExecutionTime
  File "/usr/share/software-center/softwarecenter/utils.py", line 34, in <module>
    import xml.sax.saxutils
ImportError: No module named xml.sax.saxutils
 wont open it or anything but firefox
Is there a question here???
Please tell us what you are trying to do, what the problem is, and what errors you get.
Just posting the terminal output without telling us what the problem is is not very helpful here.
Try to give us as much detail as you can if you want help.

And welcome to the Ubuntu forums!

---

### Post by oldos2er on 2012-09-09
Anyone with a question, please start a new thread since this one's fairly old.

---

