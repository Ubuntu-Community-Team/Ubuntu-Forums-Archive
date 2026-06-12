---
title: "Openoffice.org Problem after updates"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by MikeDK on 2006-12-20
Hi havin trouble with openoffice.org. simply wont start up in any way, after last updates

hope someone have had that same prob, and that someone figured it out

Best Regards MikeDK

BTW Have merry Christmas and a Happy New Year every one:KS :)

---

### Post by ingo on 2006-12-21
Which version did you update to, 2.0.4? If so, that's what I'm running on and I haven't had any probs. 

If that is the case, though, you might want to try and get relevant repositories to get you up to the recently released 2.1.

---

### Post by hxx4 on 2006-12-21
I also upgraded openoffice to the latest version this morning and it has disappeared from my system. I believe the upgrade was from openoffice.org2.0.4-0ubuntu2 to openoffice.org2.0.4-0ubuntu4 although I am not sure of the exact package name. When I look in the Synaptic Package Manager, all the OpenOffice packages are still installed. However, the menu icons for it disappeared and I cannot access one of the programs like writer by typing openoffice.org-writer.

I have the latest updates on my system and I am running Edgy which I upgraded from Dapper. x86

---

### Post by ingo on 2006-12-22
Not really sure what happened there. But to get things going type

oo 

in your shell followed by a couple of tabs. This will list all the possible commands starting with oo.

> ingo@dicker:~$ oo
oobase          oodraw          oofromtemplate  oomath          ooweb
oocalc          ooffice         ooimpress       ooo-wrapper     oowriter

If you get anything like I did above you should at least be able to start OpenOffice. As for start menus: I'm using Kubuntu and am having a hard time adjusting it, too :(

---

### Post by bapoumba on 2006-12-22
I did the upgrade yesterday and got no problem (GNOME).
```
Package: openoffice.org
State: installed
Automatically installed: no
Version: 2.0.4-0ubuntu4

```

What are the errors when you launch **ooffice -writer %U** from a terminal ?

---

### Post by hxx4 on 2006-12-22
> **ingo said:**
> Not really sure what happened there. But to get things going type

oo 

in your shell followed by a couple of tabs. This will list all the possible commands starting with oo.



If you get anything like I did above you should at least be able to start OpenOffice. As for start menus: I'm using Kubuntu and am having a hard time adjusting it, too :(

None of those commands work for me.

---

### Post by hxx4 on 2006-12-22
> **bapoumba said:**
> I did the upgrade yesterday and got no problem (GNOME).
```
Package: openoffice.org
State: installed
Automatically installed: no
Version: 2.0.4-0ubuntu4

```

What are the errors when you launch **ooffice -writer %U** from a terminal ?

I get a popup error that says /home/user/%U does not exist.

---

### Post by bapoumba on 2006-12-22
Yes, I'm sorry, **ooffice -writer** is the correct command from the terminal. The above one is for the launcher. Apologies.

---

### Post by hxx4 on 2006-12-22
> **bapoumba said:**
> Yes, I'm sorry, **ooffice -writer** is the correct command from the terminal. The above one is for the launcher. Apologies.

When I type that, the OpenOffice load screen comes up with the progress bar but it then disappears and the command exits.

---

### Post by bapoumba on 2006-12-22
> **hxx4 said:**
> When I type that, the OpenOffice load screen comes up with the progress bar but it then disappears and the command exits.
No error messages in the terminal ? Very strange indeed.
I (quickly) looked for bugs, but did not find any directly related to yours. There are several threads in openoffice.org forums, but without any error message, it's going to be difficult to find what's going on :/

---

### Post by coolclassic on 2006-12-22
I to have the same problem openoffice will not start, tried  "ooffice -writer" and nothing happened.

Unfortunately for me I need Oo now and not tomorrow.

---

### Post by hxx4 on 2006-12-22
> **bapoumba said:**
> No error messages in the terminal ? Very strange indeed.
I (quickly) looked for bugs, but did not find any directly related to yours. There are several threads in openoffice.org forums, but without any error message, it's going to be difficult to find what's going on :/

There were no error messages. Is there a way to clear out any configuration files from OpenOffice that might be problematic? Or is there a way to downgrade to the previous version? I know that I can't uninstall it because that would remove gnome as well.

---

### Post by bapoumba on 2006-12-22
I'm sending an email to one of my friends who is an openoffice wiz. Hopefully he'll be around.

---

### Post by hxx4 on 2006-12-22
> **bapoumba said:**
> I'm sending an email to one of my friends who is an openoffice wiz. Hopefully he'll be around.

Thanks a lot bapoumba, I hope we can get this figured out quickly.

---

### Post by Hagar Delest on 2006-12-22
Hi all,

First post here for the 'OOo wiz' as said bapoumba, I hope I'll be of some help ('wiz' reputation at stake here !!).

First try could be launching OOo with 'soffice.bin' to see if there is any difference.
Second, rename your user profile OOo folder to see if the new one created by OOo clears it up. Sometimes, rights for some files are changed.

Personally, I don't trust the Ubuntu packages for OOo (sorry guys). I've even heard that some features are disabled like the plug-in for Firefox (can someone confirm ?). So I always upgrade manually with the official RPMs from the OOo website. So I would advise the following installation [here]("http://www.oooforum.org/forum/viewtopic.phtml?p=184259#184259")

---

### Post by bapoumba on 2006-12-22
Hi Hagar de l'Est :)
Thanks a lot.

I do no use Firefox, how can I check for the plugin thing in Openoffice ?

I have two hidden file in my /home : .openoffice and .openoffice.org2
Which ones should them rename ?

To view an hidden file in nautilus : > View > Show hidden files

Or in a terminal :
```
ls -la .open*
.openoffice:
total 16
drwxr-xr-x   3 isabella isabella 4096 2005-02-19 10:14 .
drwxr-xr-x 100 isabella isabella 8192 2006-12-22 20:23 ..
drwxr-xr-x   5 isabella isabella 4096 2006-05-28 17:52 1.1.3

.openoffice.org2:
total 20
drwx------   3 isabella isabella 4096 2006-12-22 22:27 .
drwxr-xr-x 100 isabella isabella 8192 2006-12-22 20:23 ..
-rw-r--r--   1 isabella isabella  131 2006-12-22 22:27 .lock
drwxr-xr-x  17 isabella isabella 4096 2006-01-19 19:21 user

```

---

### Post by Hagar Delest on 2006-12-22
Hi bapoumba,

The plug-in activation in OOo is located in the menu Tools>Options>Internet>Mozilla Plug-in.

From 2.x release, the profile user folder is /.openoffice.org2. To be sure it doesn't try to import the settings of the 1.x release (it should not but who knows ?), better rename it also.

---

### Post by bapoumba on 2006-12-22
> **Hagar de l'Est said:**
> Hi bapoumba,

The plug-in activation in OOo is located in the menu Tools>Options>Internet>Mozilla Plug-in.


Well, nothing in here, see the screenshot.

---

### Post by Hagar Delest on 2006-12-22
OK, this confirms what I had heard. Here is my configuration (and it works).

I've to leave right now. As I'll be on vacation in a quite remote place of France, I won't be online until tuesday. Good luck !

---

### Post by hxx4 on 2006-12-23
I temporarily moved .openoffice.org2 from my home folder and ran```
ooffice --writer
```and this command recreated the folder but right after the splash screen disappeared, the command exited. I really need OpenOffice back asap! Help!

---

### Post by ingo on 2006-12-23
I would simply uninstall openoffice using adept manager, delete my /.openofficeorg2 folder and then reinstall. Everything should work hunky-dory.

---

### Post by hxx4 on 2006-12-23
> **ingo said:**
> I would simply uninstall openoffice using adept manager, delete my /.openofficeorg2 folder and then reinstall. Everything should work hunky-dory.

I assume Synaptic Package Manager is what I would use to remove it, but when I go to do this it tells me that it will remove ubuntu-desktop too. What can I do about this?

---

### Post by ingo on 2006-12-23
I hadn't foreseen that so I checked the info under /usr/share/doc/openoffice.org-core/README.html and it says:

> Problems During Program Startup on Gnome
If you experience OpenOffice.org startup problems (most notably while using Gnome) please 'unset' the SESSION_MANAGER environment variable inside the shell you use to start OpenOffice.org. This can be done by adding the line "unset SESSION_MANAGER" to the beginning of the soffice shell script found in the "[office folder]/program" directory.

I'd try that first before uninstalling the Ubuntu desktop (I've done it a few times, but then again I'm running on Kubuntu and never felt the impact - if any).

---

### Post by ingo on 2006-12-23
Forgot, depending on how well you know your way round the shell and linux you might find this superfluous but they are probably referring to this file here
/usr/lib/openoffice/program/soffice

---

### Post by hxx4 on 2006-12-23
> **ingo said:**
> Forgot, depending on how well you know your way round the shell and linux you might find this superfluous but they are probably referring to this file here
/usr/lib/openoffice/program/soffice

Thanks ingo, I tried adding *unset SESSION_MANAGER* right after *#!/bin/sh* in /usr/lib/openoffice/program/soffice. Then I typed```
ooffice --writer
``` but nothing happened. If it becomes necessary for me to remove ubuntu-desktop, will it be easy to install it again without breaking my system?

---

### Post by ingo on 2006-12-24
Goooooooooood question! I reckon you should try (or stick your head in the sand :) ). But beforehand I'd backup anything important like your /home directory. Then I'd carefully note down all the programmes that are to be uninstalled by OpenOffice before actually doing it. Then do it.....

Once it is finished you have two options. X should still be up. Whether this is the case once you log out is another question. First try would be to install OpenOffice again and see whether all the dependencies are reinstalled as a matter of course (should be the case). If OOo comes up then Merry Christmas and all that. If not, repeat the process, log out and see whether X comes up :) If yes, proceed as above, if not, proceed as above but using 

sudo apt-get install OpenOffice

on the command line. Or report back beforehand just in case.

It's all fun and games :) Good luck.

---

### Post by towsonu2003 on 2006-12-24
> **Hagar de l'Est said:**
> So I would advise the following installation [here]("http://www.oooforum.org/forum/viewtopic.phtml?p=184259#184259")

Those who need openoffice right now might like [this installation method]("http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight="), especially if you'd like to have a local installation without touching apt. File names change with every release, so don't forget to change file and folder names.Also, I don't install any deb packages. 

I currently have 2.0.2 (ubuntu's), 2.0.3 (self, older, forgot to delete), 2.0.4 (self, older, for a place to fall back), and 2.1 (self, new, using now).

Here is what you do (kind of):
1 Download tar.gz to ~/
2 Start a shell (also called a terminal)
3 ```
mkdir ~/ooo; cd ~/ooo
```
4 ```
tar xvzf ../blabla.tar.gz
```
5 ```
for i in `ls OOOADJUSTFILENAME/RPMS/*rpm`; do rpm2cpio $i | cpio -ivd; done
```
6 ```
(optional) rm -rf OOOADJUSTFILENAME
```
7 ```
(optional) rm ~/blabla.tar.gz
```
8 ```
sudo mv ~/ooo/opt/openoffice.org2.0 /opt/openoffice
```
9 ```
/opt/openoffice/program/soffice
```

[Via this bug report]("http://www.openoffice.org/issues/show_bug.cgi?id=70436") (was dupe), I asked OOo devs to provide us with a firefox-style .tar.gz package instead of RPMs.

---

