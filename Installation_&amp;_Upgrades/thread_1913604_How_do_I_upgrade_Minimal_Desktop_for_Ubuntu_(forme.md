---
title: "How do I upgrade Minimal Desktop for Ubuntu (formerly Ubuntu Minimal)?"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by Advice Pro on 2012-01-22
I want to upgrade 10.04 to 11.10 because the 11.10 iso didn't  install for me.  I've tried: ```
sudo apt-get dist-upgrade ubuntu-minimal 

```
And got: ```
Reading package list... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by jerrrys on 2012-01-23
Try:

sudo apt-get dist-upgrade

and before you say yes to install, take a good look at what it will download.

---

### Post by snowpine on 2012-01-23
"dist-upgrade" doesn't do what you think it does. It updates your *current* 10.04 release (equivalent to running Update Manager) but will not upgrade you to 10.10 and beyond.

Please read the Ubuntu Upgrade Notes, which detail the necessary upgrade procedures:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by jerrrys on 2012-01-23
Snowpine; check out my logic.

Minimal (mini iso) install is nothing more than terminal.  So a dist-upgrade will upgrade the kernel.  What else can be upgraded on a terminal install?

---

### Post by snowpine on 2012-01-23
> **jerrrys said:**
> Snowpine; check out my logic.

Minimal (mini iso) install is nothing more than terminal.  So a dist-upgrade will upgrade the kernel.  What else can be upgraded on a terminal install?

See the OP; they want 11.10.

---

### Post by jerrrys on 2012-01-23
Ok, now I don't know.

I too run the minimal ubuntu desktop install in 11.10, but to get there I did:

sudo apt-get install --no-recommend ubuntu-desktop

Sounds like the no recommend needs to be worked in somehow.

---

### Post by Advice Pro on 2012-01-23
I tried:
```
sudo apt-get dist-upgrade
```
and got the same results as:
```
sudo apt-get dist-upgrade ubuntu-minimal
```
I also tried:
```
sudo apt-get install --no-recommend ubuntu-desktop
```
And got:
```
sudo: apt-get: command not found
```

---

### Post by snowpine on 2012-01-23
^--- none of those commands will upgrade your system to 11.10.

Correct answer is in my post #3.

---

### Post by Advice Pro on 2012-01-23
It seems that to upgrade from 10.04 to 10.10, I need to access for Software Sources, which I don't have, but according to [url=https://help.ubuntu.com/community/Repositories/CommandLine:

> Apt stores a list of repositories or software channels in the file

```
/etc/apt/sources.list
```

But I'm lost, what do I do from here?

---

### Post by snowpine on 2012-01-23
Since you do not have the full Ubuntu Desktop you can try the Server instructions:

```
sudo apt-get install update-manager-core
```

Then "edit /etc/update-manager/release-upgrades and set Prompt=normal" which you can do with gedit, nano, or your favorite text editor, for example if you prefer nano:

```
sudo nano /etc/update-manager/release-upgrades
```

Find where it says "Prompt=" and make sure it's set to "normal." Save and exit from your text editor.

```
sudo do-release-upgrade
```

HOWEVER this is only a very brief summary of the helpful and detailed Upgrade Notes, which I encourage you to read start to finish **before** you make any permanent changes to your system. :)

---

### Post by snowpine on 2012-01-23
Also, to play devil's advocate... you can wait 3 months and upgrade directly from 10.04 to 12.04 in 1 easy step. Is there a specific reason why you want 11.10?

---

### Post by jerrrys on 2012-01-23
sudo do-release-upgrade

This will upgrade a standard system.  What it will do for you?  Once again take a good look 
at whats being install before you say yes to the install.

EDIT: nevermind, snowpine has you covered.

---

### Post by Advice Pro on 2012-01-23
> **snowpine said:**
> 
```
sudo apt-get install update-manager-core
```

This just gave me the same output as in my first post.

I don't know how to > **snowpine said:**
> edit /etc/update-manager/release-upgradeswith LeaPad

> **snowpine said:**
> Is there a specific reason why you want 11.10?
No, I just want to try other versions of MDU. in fact, because of the major size change in 11.04 and 11.10, I'll probably just want to get to 10.10

---

### Post by snowpine on 2012-01-23
> **Advice Pro said:**
> This just gave me the same output as in my first post.

I don't know how to with LeaPad

Please copy & paste the output of:

```
sudo apt-get install update-manager-core
```

To edit a system config file with leafpad:

```
gksu leafpad /etc/update-manager/release-upgrades
```

(This is assuming you have already installed gksu and leafpad.)

---

### Post by Advice Pro on 2012-01-23
Output of:```
sudo apt-get install update-manager-core
```
```
Reading package list... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

What is gksu?

---

### Post by snowpine on 2012-01-23
update-manager-core is installed, so you may proceed to the next step. :)

'gksu' is like 'sudo' but for GUI applications (like leafpad): [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Advice Pro on 2012-01-23
```
gksu leafpad /etc/update-manager/release-upgrades
```

This just gets me a blank page in leafpad

---

### Post by snowpine on 2012-01-23
Then I guess the official Ubuntu Upgrade Guide is wrong, I don't know what to tell you. :(

---

### Post by jerrrys on 2012-01-23
A fresh install would be a way out.

---

### Post by Advice Pro on 2012-01-23
I think I'll  have to upgrade as an ordinary version, using software sources, but I need help.  The way to do this is, via command line, edit:
```
/etc/apt/sources.list
```

The Ubuntu documentation [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

(I had nano and I didn't even know it.)

---

### Post by jerrrys on 2012-01-23
have gedit installed?

sudo gedit /etc/apt/sources.list

---

### Post by Advice Pro on 2012-01-23
Even with gedit I'm getting a blank page.  Am I doing something wrong?

---

### Post by snowpine on 2012-01-23
> **Advice Pro said:**
> I think I'll  have to upgrade as an ordinary version, using software sources, but I need help.  The way to do this is, via command line, edit:
```
/etc/apt/sources.list
```

The Ubuntu documentation [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

(I had nano and I didn't even know it.)

Whoever told you to do that is incorrect; editing /etc/apt/sources.list is **not the recommended method** to upgrade Ubuntu. (Sometimes Debian users do it that way and give bad advice to Ubuntu users.)

If your system does not have an /etc/apt/sources.list file (or it is blank) then it is beyond my ability to troubleshoot, sorry. :(

---

### Post by jerrrys on 2012-01-23
got a backup?  in terminal:

ls /etc/apt/

and please post

---

### Post by Advice Pro on 2012-01-23
what did you mean backup?

The output of ls /etc/apt/:

```
ls: cannot access /etc/apt/: No such file or directory
```

---

### Post by jerrrys on 2012-01-23
You don't seem to have much of anything.  You can create a sources.list folder and fill it yourself.

[http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/](http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/)

[https://help.ubuntu.com/community/Beginners/BashScripting#Creating_folders](https://help.ubuntu.com/community/Beginners/BashScripting#Creating_folders)

---

### Post by snowpine on 2012-01-23
> **Advice Pro said:**
> what did you mean backup?

The output of ls /etc/apt/:

```
ls: cannot access /ect/apt/:No such file or directory
```

Linux syntax is not "fuzzy." You should use copy & paste and check carefully for typos. Please re-read Jerry's post #24 and try again. :)

---

### Post by Advice Pro on 2012-01-23
> **snowpine said:**
> Linux syntax is not "fuzzy." You should use copy & paste and check carefully for typos. Please re-read Jerry's post #24 and try again. :)

Sorry, I don't understand.

---

### Post by snowpine on 2012-01-23
> **Advice Pro said:**
> Sorry, I don't understand.

There is a typo in your post #25. See post #24 for the correct command.

---

### Post by Advice Pro on 2012-01-23
> **snowpine said:**
> There is a typo in your post #25. See post #24 for the correct command.

Oh, sorry. I'm going to end it to:

ls: cannot access /ect/apt/: No such file or directory

---

### Post by snowpine on 2012-01-23
If you don't see the typo then I recommend you Copy & Paste the correct command from post #24. :)

---

### Post by Advice Pro on 2012-01-23
OK, the output of

```
ls /etc/apt
``` is

```

apt.conf.d  secring.gpg  sources.list.d  trusted.gpg  trusted.gpg.d
preferences.d  sources.list  trustdb.gpg  trusted.gpga~

```

---

### Post by snowpine on 2012-01-23
I see you do indeed have an /etc/apt/sources.list file, which leads me to believe you may have made a typo earlier when trying to edit it. Copy & paste will avoid this in the future. ;)

However, there is no reason to edit this file. It is not relevant to your goal of upgrading your system to 10.10 (and beyond). At this point I think the easiest way to accomplish that goal is a fresh reinstall of the desired version.

---

### Post by jerrrys on 2012-01-23
Just to be sure.  In terminal copy and paste:

ls -sh /etc/apt/sources.list

You should see a file size of about 4K.

---

### Post by Advice Pro on 2012-01-24
Yes ```
4.0K /etc/apt/sources.list
```

---

