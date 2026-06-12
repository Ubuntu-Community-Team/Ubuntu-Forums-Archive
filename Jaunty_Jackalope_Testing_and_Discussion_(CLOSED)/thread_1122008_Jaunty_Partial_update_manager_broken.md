---
title: "Jaunty Partial update manager broken?"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rv65 on 2009-04-10
Basically I've been having problems with the partial updater. It will download the files but then disappears and won't install them. I don't know what to do? Any help would be great.

---

### Post by RookieUbuntuUser58 on 2009-04-10
I installed Jaunty on my desktop a few moments ago and Im having the same problem with the partial update manager.

---

### Post by Mokoma on 2009-04-10
im having this problem to. when i run update manager from cli this is the output from terminal 

crash2k@crash2k-desktop:~$ sudo /usr/bin/update-manager
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 100, in <module>
    controler.doPartialUpgrade()

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 1595, in doPartialUpgrade
    if not self.doDistUpgrade():

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 972, in doDistUpgrade
    self.quirks.run("StartUpgrade")

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeQuirks.py", line 77, in run
    for plugin in self.plugin_manager.get_plugins(condition):

  File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 167, in get_plugins
    filenames = self.get_plugin_files()

  File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 120, in get_plugin_files
    basenames = [x for x in os.listdir(dirname)

OSError: [Errno 2] No such file or directory: './plugins'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
none
crash2k@crash2k-desktop:~$

---

### Post by ubuntu27 on 2009-04-10
DId you guys filled a Bug Report about it? 

Fill a bug report and post a link here so anyone that has the same problem can comment on that.

---

### Post by Eclipse. on 2009-04-10
Cant really help much here as my Jaunty box had a horrible hardware failure the other day but what I can say is its not an actual bug in update-manager.Update-manager has not had any changes since the 8th according to the LP changelog.

---

### Post by DarkReaper79 on 2009-04-11
for me it seems to work now. I think it was a server or a repository problem.

---

### Post by Brejcha on 2009-04-17
I am having the same problem now. I am also having a separate problem where the main desktop no icons will display as well as no right click or single click function just on the desktop....

I hope that I can upgrade soon like in 6 days when the actual 9.04 comes out.

---

### Post by mixmaster on 2009-04-17
I'm just getting a box saying Authentication Failure then the update process stops.

---

### Post by rv65 on 2009-04-22
Still not working for me. It mainly includes stuff like pidgin-notify, amsn, mplayer, od2text, and other stuff. It will download them but the window will disappear and it will not install the updates.

---

### Post by cl333r on 2009-04-22
There was at least one showstopper regarding updates. I'd suggest downloading the latest daily build, installing it and and see whether the issue is still there. It will probably be the actual final Jaunty release btw.

---

### Post by taavikko on 2009-04-22
> **rv65 said:**
> Still not working for me. It mainly includes stuff like pidgin-notify, amsn, mplayer, od2text, and other stuff. It will download them but the window will disappear and it will not install the updates.

Have you tried updating from CLI
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you're unsure whether to proceed or not, paste the output of previous command.

@mokoma,
to use update-manager, you don't need to use sudo or absolute path,
just
```
update-manager
```
and it will prompt for password when needed
Also, never good idea to start graphical apps with "sudo"
Always use "gksudo"

---

### Post by rv65 on 2009-04-22
Where do I get the daily builds?

Edit:  Found them.

---

### Post by rv65 on 2009-04-22
> **taavikko said:**
> Have you tried updating from CLI
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you're unsure whether to proceed or not, paste the output of previous command.

@mokoma,
to use update-manager, you don't need to use sudo or absolute path,
just
```
update-manager
```
and it will prompt for password when needed
Also, never good idea to start graphical apps with "sudo"
Always use "gksudo"

Yes I've had used it. I usually use sudo apt-get upgrade.

---

### Post by rv65 on 2009-04-22
The dist-upgrade command works.

---

