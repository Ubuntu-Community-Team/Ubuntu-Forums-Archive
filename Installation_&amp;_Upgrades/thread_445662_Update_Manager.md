---
title: "Update Manager"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by bilbobagins on 2007-05-16
Hi .
I am now running 7.04 and its all good except update manager,it don't notify if there are updates.
It seems that i have the notify box checked. Any thoughts from our more learned members.
Oh by the way since edgy I'm  fully ubuntu 100%

---

### Post by gwoodard on 2007-05-16
Go to System->Administration->Update Manager

---

### Post by gweaver on 2007-05-17
I have the same issue, despite the Software Sources settings looking correct.

---

### Post by bapoumba on 2007-05-17
Could you check in your session preferences (or settings i do not remember) if update-manager starts up on login ?

---

### Post by gweaver on 2007-05-17
I have update-notifier, but not update-manager listed amongst the startup programs.

And I've just tried adding another user to see if the default startup programs include update-manager - but apparently not.

---

### Post by bapoumba on 2007-05-17
update-notifier is fine, sorry. I'm not running GNOME right now and this was top of my head. When new updates come in, you do not see an orange square icon popping up, do you ?

---

### Post by gweaver on 2007-05-17
No, I don't normally get the orange square star icon thingy appearing in the system tray.

It does appear if I manually check for updates using Update Manager, but choose not to install the updates. If I do that the update-notifier icon appears within a minute or two, and then goes away when I install the updates.
If I manually check for the updates and then immediately install them I don't see the icon.

Is there a log file that I can check to find clues as to why update-notifier/manager isn't automatically talking to the repositories?

---

### Post by bapoumba on 2007-05-17
Does this happen with the regular human theme and icons ?

---

### Post by gweaver on 2007-05-17
Yes I'm using the standard Feisty human theme and icons.

I don't think its a graphical issue. If I run Update Manager it doesn't list updates until I check for them manually. This exception to this is if I have not installed the updates found when I checked manually on a previous occasion.

---

### Post by bapoumba on 2007-05-17
i've looked for bugs, but nothing obvious. Any error if running update-notifier from a terminal ?
```
~$ update-notifier

** (update-notifier:7856): WARNING **: already running?
```

---

### Post by gweaver on 2007-05-17
No errors reported.

I get:
> ~$ update-notifier

** (update-notifier:11377): WARNING **: already running?

I should add that I get this error on two separate installations (both upgraded from Edgy), both at work. I haven't got Ubuntu on my home computer right now, but will try a fresh Feisty install when I get the time to see if I get the same issue.
I wonder if there could be some sort of obscure network proxy issue? But I have the proxy configuration set correctly (I think), and don't get any errors...

 :confused:

---

### Post by bapoumba on 2007-05-17
Hmm.
How did you set up your proxy ?
In **/etc/apt/apt.conf **?

---

### Post by gwoodard on 2007-05-17
About the theme you were talking about why just you don't change the theme(Sometimes onboard video works in strange ways with human) Use Clear Looks or the theme of your choosing(maybe except human:lolflag:)

---

### Post by gweaver on 2007-05-18
I don't have an /etc/apt/apt.conf file. I used the Network Proxy dialog which is under system->preferences in gnome.

Maybe the proxy is not the problem and I am barking up the wrong tree, as update manager can talk to the repositories when I click the check button by hand.

I think the problem is that update-notifier is either not attempting to check the repositories or that its not able to connect, but without a log I have no idea which.

As regards the theme, I have no complaints with Human, its just fine for me.

---

### Post by martinrandau on 2007-05-20
Just want to say that I'm having the same problems.

Running update-notifier in terminal says update notifier is already running.

---

### Post by bapoumba on 2007-05-20
Okay. I have run a search on update-notifier in launchpad and did not find anything relevant.
Could you guys have a look at current LP bugs with update-notifier ? If nothing looks relevant to you, you should file a bug report (I can help you out with that, if you wish).

---

### Post by gweaver on 2007-05-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/update-notifier/+bug/53868](https://bugs.launchpad.net/update-notifier/+bug/53868) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've just checked on Launchpad and found a bug which looks relevant.

It is described as "update-notifier doesn't notify about available updates" and you can read/post about it at: [https://bugs.launchpad.net/update-notifier/+bug/53868](https://bugs.launchpad.net/update-notifier/+bug/53868)

---

### Post by bapoumba on 2007-05-22
OK, I was about to suggest you comment in it :)
Does the ps show update-notifier running ? (two comments above yours).

---

### Post by gweaver on 2007-05-22
Done.

update-notifier was running.

---

### Post by warjowuch on 2007-06-03
yep, same problem here. Have ubuntu running since breezy, dist-upgraded to dapper, then notifier did not work anymore. 2 dist-upgrades later (edgy and feisty) still not working. Grr. I am thinking of reïnstalling the whole thing. Then I have better partitioning and I am jalous at my wife who is running ubuntu (CE) fresh install 7.04, with notifier notifying gently about available updates... :-)
By the way, is there not any solution for this? Since in linux about everything should be resolvable without reïnstalling...

---

### Post by bapoumba on 2007-06-03
The bug report is confirmed. Now, when it gets fixed, there will be an upgrade. Use apt-get or aptitude in the mean time.

---

### Post by colossus73 on 2007-10-21
Any news on this? May I help someway maybe reporting the content of some update-notifier related directories?

Thanks,

---

