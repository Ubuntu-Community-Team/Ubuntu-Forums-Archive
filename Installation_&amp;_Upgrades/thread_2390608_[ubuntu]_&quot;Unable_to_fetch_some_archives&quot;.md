---
title: "[ubuntu] &quot;Unable to fetch some archives&quot; problem"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by trenza on 2018-04-30
Hey everyone!
Let me lay out my situation here and give all the background info. 
I'm doing mathematics work at my university, and I've been given the ability to login to a high-powered computation computer to do some long calculations. I log into the machine using ssh and its local address on the university's network.
I attempted to install sagemath on the computer, as I need it for some of the calculations I'm doing, but after adding the repository and, and doing 
```

$ sudo apt-get update
$ sudo apt-get install sage-upstream-binary

```
the installation began, then failed with the following error:
```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
Of course, I had already run update, but I tried --fix-missing, and unfortunately that did not solve the problem.
I then tried
```

$ sudo apt-get update
$ sudo apt-get upgrade
```
and it failed with an identical error to when I tried to install sage.
Next I tried 
```
$ sudo apt dist-upgrade
```
and, you guessed it, the same error as the last two.
It seems that all upgrade/install related commands are ending with this error. I've been given permission by the computer's owner (who doesn't know much about linux) to do what I need to to try and fix it, but I'm a little lost. Any suggestions?
Thanks! And please let me know if more info is required.

Edit: just realized I should probably add system info, huh? 
The computer is running Ubuntu 15.04

---

### Post by deadflowr on 2018-04-30
what's the actual output from those commands?

---

### Post by trenza on 2018-04-30
Here it is for upgrade. It's pretty similar for the others.
```

$ sudo apt-get upgrade
[FONT=Menlo]Reading package lists... Done[/FONT]
[FONT=Menlo]Building dependency tree       [/FONT]
[FONT=Menlo]Reading state information... Done[/FONT]
[FONT=Menlo]Calculating upgrade... Done[/FONT]
[FONT=Menlo]The following packages have been kept back:[/FONT]
[FONT=Menlo]  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 linux-generic[/FONT]
[FONT=Menlo]  linux-headers-generic linux-image-generic oxideqt-codecs[/FONT]
[FONT=Menlo]The following packages will be upgraded:[/FONT]
[FONT=Menlo]  linux-libc-dev[/FONT]
[FONT=Menlo]1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.[/FONT]
[FONT=Menlo]Need to get 786 kB of archives.[/FONT]
[FONT=Menlo]After this operation, 31.7 kB of additional disk space will be used.[/FONT]
[FONT=Menlo]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Menlo]WARNING: The following packages cannot be authenticated![/FONT]
[FONT=Menlo]  linux-libc-dev[/FONT]
[FONT=Menlo]Install these packages without verification? [y/N] y[/FONT]
[FONT=Menlo]Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-libc-dev amd64 3.19.0-84.92[/FONT]
[COLOR=#500050][FONT=arial][FONT=Menlo]  404  Not Found [IP: 91.189.91.23 80][/FONT]
[/FONT][/COLOR][FONT=Menlo]Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) vivid-security/main linux-libc-dev amd64 3.19.0-84.92
[COLOR=#500050]  404  Not Found [IP: 91.189.91.23 80][/COLOR][/FONT]
[FONT=arial][COLOR=#500050][FONT=Menlo]E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.19.0-84.92_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.19.0-84.92_amd64.deb)  404  Not Found [IP: 91.189.91.23 80][/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/FONT]
[/COLOR][/FONT]

```

---

### Post by deadflowr on 2018-04-30
Vivid?
That's [EOL]("http://fridge.ubuntu.com/2016/01/14/ubuntu-15-04-vivid-vervet-reaches-end-of-life-on-february-4-2016/") and the archives no longer exist as they are.
Install a fresh version of a supported release.
(Either 14.04 16.04 17.10 or 18.04)

Sorry to be harsh.

---

### Post by trenza on 2018-04-30
Haha don't worry, I'm not offended! It's not my computer anyway. 
Do you know the best way to go about the instillation? 
do-release-upgrade gives
```

[FONT=Menlo]Can not upgrade [/FONT][FONT=Menlo]
[/FONT]
[FONT=Menlo]An upgrade from 'vivid' to 'xenial' is not supported with this tool.[/FONT]
```
I'd really like to avoid a fresh instillation, because at the moment I only have ssh access, but if I have to recommend that they do that I certainly will. I guess I'm just wondering if there's any way to avoid it.

---

### Post by deadflowr on 2018-04-30
If not fresh then best option might be an EOL upgrade
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")
But I'm not sure if it'll point to 16.04 or 15.10.

It's just miles easier to deal with by doing a clean install.
Much more so than when dealing with end of lifer's.
As an upgrade from an end of life release may have an issue or two which cannot be resolved.

---

### Post by trenza on 2018-04-30
Thank you so much! That's all very helpful. Fresh install seems like it might be the way to go.

---

