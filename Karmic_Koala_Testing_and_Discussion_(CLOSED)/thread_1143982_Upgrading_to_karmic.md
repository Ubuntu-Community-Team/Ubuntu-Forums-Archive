---
title: "Upgrading to karmic?"
date: 2009-04-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-04-30
How is this done? I have an old computer, that I use for testing and I might as well upgrade to start testing karmic :D

---

### Post by rudenko_ruslan on 2009-04-30
I just edited my /etc/apt/sources.list (changed all "jaunty" to "karmic") and then updated through "Update Manager".

Or you're asking about a "current state of things" there?

---

### Post by davideotape on 2009-04-30
Wherabouts can I find sources.list in my filesystem?

---

### Post by rudenko_ruslan on 2009-04-30
> **davideotape said:**
> Wherabouts can I find sources.list in my filesystem?
**/etc/apt/**sources.list (type in terminal "gksudo gedit /etc/apt/sources.list")

---

### Post by snowpine on 2009-04-30
Please do not take offense at the following. :)

If you have to ask "where is /etc/apt/sources.list in my filesystem?" you should wait until Karmic is in beta. It is extremely unstable pre-alpha at this point, you will need some technical skills when problems invariably arise.

---

### Post by SuperSonic4 on 2009-04-30
It will need to be edited as root (if you don't know how perhaps a pre-alpha isn't for you ;))

---

### Post by dox_drum on 2009-04-30
> **davideotape said:**
> Wherabouts can I find sources.list in my filesystem?

```
sudo gedit /etc/apt/sources.list
```

---

### Post by davideotape on 2009-04-30
> **snowpine said:**
> Please do not take offense at the following. :)

If you have to ask "where is /etc/apt/sources.list in my filesystem?" you should wait until Karmic is in beta. It is extremely unstable pre-alpha at this point, you will need some technical skills when problems invariably arise.

No offense taken :D. I've used it before, I just couldn't remember where exactly it was.

> It will need to be edited as root (if you don't know how perhaps a pre-alpha isn't for you ) 

I do know about these things. I'm always trying to fix my menu.lst using sudo gedit.

Thanks for the quick replies guys, I've just upgraded :D

---

### Post by taavikko on 2009-04-30
Best way IMHO is to use sed to change sources.list

oneliner:
```
sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list; sudo aptitude update && sudo aptitude dist-upgrade
```

after alpha1 is released you can use
```
update-manager -d
```
to upgrade to development release, as long prompt is set to "normal" in 
**/etc/update-manager/release-upgrades**

---

### Post by davideotape on 2009-04-30
> **taavikko said:**
> Best way IMHO is to use sed to change sources.list

oneliner:
```
sudo sed -i 's/jaunty/karmic/g' /etc/apt/sources.list;
```

I presume that's just a simple replace function?

---

### Post by Monotoko on 2009-04-30
Yeah it is:

> One of the best things about the Linux operating system is that it is crammed full of utilities. There are so many different utilities, in fact, that it is next to impossible to know and understand all of them. One utility that can simplify life in key situations is sed. It is one of the most powerful tools in any administrator's toolkit and can prove itself invaluable in a crunch.

The sed utility is an "editor," but it is unlike most others. In addition to not being screen-oriented, it is also noninteractive. This means you have to insert commands to be executed on the data at the command line or in a script to be processed. When you visualize it, forget any ability to interactively edit files as you would do with Microsoft Word or most other editors. sed accepts a series of commands and executes them on a file (or set of files) noninteractively and unquestionably

source: [http://www.oracle.com/technology/pub/articles/dulaney_sed.html](http://www.oracle.com/technology/pub/articles/dulaney_sed.html)

---

### Post by davideotape on 2009-05-01
Cool, I might look into that. Like the quote aswell. I'm learning new things all the time :D

---

### Post by Reiger on 2009-05-01
Sed stands for **S**tream **Ed**itor, or so I believe anyways, and it operates on streams. What you do is you specify rules for what is to be done with data that does (not) match a pattern; in the example given it is an 'inplace' replace rule: every occurence of the string "jaunty" is replaced with "karmic".

---

### Post by linux6994 on 2009-05-01
I have edited sources.list and have updated to karmic and all is well. All of my applications,belkin wireless card WAN0 and ICS sharing ETH0 are running sweet just like on Jaunty.

---

### Post by celticbhoy on 2009-05-03
Getting this trying to upgrade :-

> ERROR:root:not handled expection:
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
testing@testing-laptop:~$ 


Any help ....

---

### Post by taavikko on 2009-05-03
Upgrade manually for now.
By editing sources.list and then dist-upgrade.

---

### Post by celticbhoy on 2009-05-03
I used the sed instruction posted earlier in this thread to update my sources and then tried to update - will check that the sources has changed properlly.

---

### Post by taavikko on 2009-05-03
> **celticbhoy said:**
> I used the sed instruction posted earlier in this thread to update my sources and then tried to update - will check that the sources has changed properlly.

You can use "sed" to change the sources.list, but you need to use 
"apt{itude}-get update && dist-upgrade" to finish the process,
Like i stated earlier, update-manager isn't able to to this yet.

---

### Post by davideotape on 2009-05-03
> **taavikko said:**
> You can use "sed" to change the sources.list, but you need to use 
"apt{itude}-get update && dist-upgrade" to finish the process,
Like i stated earlier, update-manager isn't able to to this yet.

Strange, I just changed all the jaunty's in sources.lst, reloaded synaptic and everything worked fine.:-k

---

### Post by celticbhoy on 2009-05-03
I have checked my sources.list file and it seems fine, I have also followed all the other mentioned steps but still no joy.

---

### Post by charleskw on 2009-05-05
I have it installed, and I can't tell a difference. Are there any changes yet?

---

### Post by Nullack on 2009-05-05
Maybe you should subscribe to the karmic changes mailing list

---

### Post by Chris_21 on 2009-07-26
ALT F2 Then Update-Manager -d

---

