---
title: "Need Help Fixing Failed Offline Update"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by dwh367 on 2023-02-24
I've done my due diligence on this (lots of research) trying to fix it myself.  So far I've spent 4 hours and nothing I've tried has fixed it yet.  I guess it's time to finally ask for some help.   I cannot get rid of the "[COLOR=#000000]Failed to update 1 package[/COLOR][COLOR=#000000]Error while installing package: installed update-notifier-common package post-installation script subprocess returned error exit status 1" [/COLOR] error.  Anyone have any ideas please?

---

### Post by Bashing-om on 2023-02-24
Hello dwh367

Let's begin by looking at what the package manager thinks of the situation.
Post back - between code tags - the return from terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2023-02-24
*Just an observation* based on the original post and the title of the thread... Says "... Failed [COLOR=#ff0000]Offline[/COLOR] Update".

We need the full text of the error.

Updates assume you have an online connection or an offline repo... In case installing a new package requires subsequent update of dependencies to satisfy the update process.

The full text of the process error would tell if the process triggered or failed because other new packages were required to work that out.

So the only command ([COLOR=#ff0000]offline[/COLOR]) that would produce the text of the error would be
```

sudo apt install --fix-broken

```

---

### Post by dwh367 on 2023-02-24
> **Bashing-om said:**
> Hello dwh367

Let's begin by looking at what the package manager thinks of the situation.
Post back - between code tags - the return from terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```[INDENT][INDENT]see where we go from here
[/INDENT]
[/INDENT]


Here you go: 

[FONT=monospace][COLOR=#000000]```
sudo apt update[/COLOR]
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]                     
Hit:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease [107 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [898 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 DEP-11 Metadata [101 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 DEP-11 Metadata [267 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports/main amd64 DEP-11 Metadata [7976 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 DEP-11 Metadata [41.6 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 DEP-11 Metadata [15.2 kB]
Fetched 1681 kB in 3s (610 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.[/FONT][FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]
sudo apt upgrade[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libopenexr25 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6
  libeditorconfig0 libmagickcore-6.q16-6 imagemagick-6-common
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
``````
[FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]
sudo apt -f install[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/FONT]
```[FONT=monospace]
[/FONT][FONT=monospace]


[/FONT]

---

### Post by MAFoElffen on 2023-02-24
Please go back to your last post: EDIT > Advanced > Select the text of your output > Select the "#" Icon, to wrap the output with CODE Tags > Save

Raw output or commands can wreak havoc on the Forums system, and and using CODE Tags makes posts easier to read...

---

### Post by dwh367 on 2023-02-24
[COLOR=#000000]Duplicate. Deleted. Not used to how this forum is laid out. 

[/COLOR]

---

### Post by dwh367 on 2023-02-24
[COLOR=#000000]>  We need the full text of the error. 
[/COLOR][COLOR=#000000]This is the error I get even though everything shows fine so far. I get the error every time I log in.
 [/COLOR]
```
[COLOR=#000000]Failed to update 1 package [/COLOR][COLOR=#000000]Error while installing package: installed update-notifier-common package post-installation script subprocess returned error exit status 1

[/COLOR][FONT=monospace][COLOR=#000000]sudo apt install --fix-broken[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
[/FONT]
```[FONT=monospace]
[/FONT][COLOR=#000000]




[/COLOR]

---

### Post by dwh367 on 2023-02-24
> **MAFoElffen said:**
> Please go back to your last post: EDIT > Advanced > Select the text of your output > Select the "#" Icon, to wrap the output with CODE Tags > Save

Raw output or commands can wreak havoc on the Forums system, and and using CODE Tags makes posts easier to read...

Done.

---

### Post by ian-weisser on 2023-02-24
If you are seeing the error text at login, that suggests your motd (MOTD = Message Of The Day) is displaying a stale message.

Your apt output suggests that your system currently has no package management problems. Trust apt over motd.

---

### Post by dwh367 on 2023-02-24
> **ian-weisser said:**
> If you are seeing the error text at login, that suggests your motd (MOTD = Message Of The Day) is displaying a stale message.

Your apt output suggests that your system currently has no package management problems. Trust apt over motd.

This is my motd output 

```
 

[FONT=monospace][COLOR=#000000]sudo run-parts /etc/update-motd.d/[/COLOR]
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.15.0-60-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

 * Introducing Expanded Security Maintenance for Applications.
   Receive updates to over 25,000 software packages with your
   Ubuntu Pro subscription. Free for personal use.

     https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

6 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

```[/FONT]

---

### Post by ian-weisser on 2023-02-24
It's unclear when or how you are seeing the error message. "When I login" is too vague to offer useful advice.

You have shown us a clean modt. It's not that.

It might be that you are running an apt update after logging in...but then you showed us apt update output without any error message.

That's two wild goose chases that could have been avoided.

Everything else you have shown us says that your system is fine.

If you still want help, be detailed and accurate in the steps you take  to get the error message to show.

---

### Post by MAFoElffen on 2023-02-25
Just curious: Based on 'what you did post' on the error you saw, what is the output of
```

sudo apt-get install --reinstall --dry-run update-notifier-common

```

---

### Post by dwh367 on 2023-02-25
> **MAFoElffen said:**
> Just curious: Based on 'what you did post' on the error you saw, what is the output of
```

sudo apt-get install --reinstall --dry-run update-notifier-common

```


Here you go:
```

[FONT=monospace][COLOR=#000000]sudo apt-get install --reinstall --dry-run update-notifier-common[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Inst update-notifier-common [3.192.54.5] (3.192.54.5 Ubuntu:22.04/jammy-updates [all])
Conf update-notifier-common (3.192.54.5 Ubuntu:22.04/jammy-updates [all])
[/FONT]
```

---

### Post by MAFoElffen on 2023-02-25
I don't see a problem there either...

---

### Post by dwh367 on 2023-02-25
> **ian-weisser said:**
> It's unclear when or how you are seeing the error message. "When I login" is too vague to offer useful advice.

You have shown us a clean modt. It's not that.

It might be that you are running an apt update after logging in...but then you showed us apt update output without any error message.

That's two wild goose chases that could have been avoided.

Everything else you have shown us says that your system is fine.

If you still want help, be detailed and accurate in the steps you take  to get the error message to show.


I wish I knew what to tell you. The steps to recreate the problem is to just log in.  Then the error message pops up. It's almost like something is stuck in the package manager or something. Thanks for everyone who tried to help.  I'm going to abandon this thread now.  I run Arch on a Raspberry Pi and Debian on a VSP.  I've never had a problem with either of them.  They just work.  I've had nothing but issues with Ubuntu.  Looks like it's time to move on to another distro here on my laptop.

---

### Post by MAFoElffen on 2023-02-25
You've already done a 'dry run' and there was no problems shown by that... It would cost you nothing to try this to see if it corrects that:
```

sudo apt-get install --reinstall update-notifier-common

```

---

### Post by TheFu on 2023-02-27
There's an easy fix for bothersome login junk.  
```
touch ~/.hushlogin
```

---

