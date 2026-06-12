---
title: "Ubuntu fails to update"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by AACMasterblaster on 2013-05-15
Hi All,

I run Ubunto 13,04 and the new packages will not install anymore. I get:

installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-lowlatency': Input/output error

when i try installing from package manager I get:
"
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-lowlatency': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
"

I tried a lot but nothing seems to solve my problem.

your help would be highly appreciated

---

### Post by ibjsb4 on 2013-05-15
Are you running Ubuntu Studio?

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
uname -r
```

And please post the output.

---

### Post by AACMasterblaster on 2013-05-16
yes I'm running Ubuntu studio.

Output after [COLOR=#000000][FONT=Ubuntu Mono]uname -r  = [/FONT][/COLOR]

3.8.0-19-lowlatency

Output after [COLOR=#111111][FONT=Consolas]uname -mrs =
[/FONT][/COLOR]
Linux 3.8.0-19-lowlatency i686


Output after [COLOR=#111111][FONT=Consolas]uname -a =[/FONT][/COLOR]

Linux media-ThinkPad-T60 3.8.0-19-lowlatency #13-Ubuntu SMP PREEMPT Thu Apr 18 09:42:14 UTC 2013 i686 i686 i686 GNU/Linux

thanks for your help

---

### Post by ibjsb4 on 2013-05-16
I have been searching "linux-image input/output error" without any positive results.  From what I have read, there seems to be a possibility of file corruption in /var/lib/dpkg/info/linux-image-lowlatency.  If this is indeed the case then possibly reinstalling linux-image-lowlatency would solve the problem.
```

sudo apt-get remove --reinstall linux-image-lowlatency && sudo apt-get update
```

---

### Post by AACMasterblaster on 2013-05-17
Thanks again for your suggestion, but even this will not install

sudo apt-get remove --reinstall linux-image-lowlatency && sudo apt-get update
[sudo] password for media: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-lowlatency linux-lowlatency
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded.
After this operation, 55.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-lowlatency': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

I also fear some files are corrupted.

If you have more suggestions, please let me know.

Kind regards

---

