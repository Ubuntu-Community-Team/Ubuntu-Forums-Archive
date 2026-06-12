---
title: "Cannot upgrade with Update Manager"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2014-06-07
I have 13.10 installed on my computer and wanted to upgrade to 14.04LTS
However Update Manager does not have an option to upgrade and tells me "The software on this computer is up to date"
while "The notify me of a new Ubuntu version" is set to "For any new version".
How can I proceed?

---

### Post by rahul4557 on 2014-06-07
Run this command in terminal
> sudo apt-get update && sudo apt-get dist-upgrade

Later you can open Software Updater and upgrade to 14.04.

---

### Post by LastDino on 2014-06-07
> **rahul4557 said:**
> Run this command in terminal


Later you can open Software Updater and upgrade to 14.04.

This. Plus, remove anything 3rd party you've before you run update. Example: Proprietary graphic drivers and PPA's in source list.

---

### Post by jj.wauters on 2014-06-08
There were no drivers or PPAs to remove.
But the behavior is very strange to me :
After running the commands and launching Software Updater again it did not show the Upgrade button.
[ATTACH=CONFIG]253813[/ATTACH]
So I entered from terminal "sudo update-manager -d".
Now Software manager has a button to make the upgrade.
[ATTACH=CONFIG]253814[/ATTACH]
When trying to upgrade the next screen "Release notes" is a blank screen. Should I continue??? Are these known install bugs ???
[ATTACH=CONFIG]253815[/ATTACH]

---

### Post by LastDino on 2014-06-08
Running that command itself is update procedure different from GUI update manager, you need not open update manager when you run those commands. 

When you run those commands in terminal, keep and eye on out put, it will list all the available updates and you'll be asked to install them or not in terminal itself. Don't shut down terminal.

---

### Post by jj.wauters on 2014-06-08
I did what was proposed by rahul4577 :
1° run in terminal : sudo apt-get update && sudo apt-get dist-upgrade
2° open Update Manager in order to upgrade 
The result was what I described under #4

So I entered the command again.
It comes back to the prompt without asking to do what so ever.
Here you see the output.
[ATTACH]253819[/ATTACH]

How to continue?

---

### Post by LastDino on 2014-06-08
Can you post the output of 

```
uname -a
```
And
```
lsb_release -a
```

---

### Post by jj.wauters on 2014-06-08
jan@jan-HP-ENVY-15-Notebook-PC:~$ uname -a
Linux jan-HP-ENVY-15-Notebook-PC 3.11.0-23-generic #40-Ubuntu SMP Wed Jun 4 21:05:23 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
jan@jan-HP-ENVY-15-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

---

### Post by LastDino on 2014-06-08
Ok, you should probably take backup of everything important and try that ''upgrade'' option at ''release notes''.

---

### Post by oldos2er on 2014-06-08
If you can do without Update Manager, open a terminal and run ```
do-release-upgrade
```

---

### Post by LastDino on 2014-06-08
> **oldos2er said:**
> If you can do without Update Manager, open a terminal and run ```
do-release-upgrade
```

That should be one way to do it, try this too :3

---

### Post by jj.wauters on 2014-06-08
I ran "sudo update-manager -d" again and this time the "Release notes" in Software Manager
was filled up with text. I continued the upgrade and finally 14.04 is installed.
However during the upgrade I had again a blank screen where I was upposed to make a choice (see picture)
[ATTACH=CONFIG]253828[/ATTACH]

Thanks for helping me.

---

### Post by LastDino on 2014-06-09
I would generally go with Keep option. But just in case, wait for someone else to confirm.

---

### Post by bapoumba on 2014-06-09
It all depends which custom file is being replaced. I usually replace to have the default release file, but take note of the file in question in case something happens. Here, it all depends on what has been done to this file.

---

