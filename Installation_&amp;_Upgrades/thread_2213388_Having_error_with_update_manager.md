---
title: "Having error with update manager"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by arvyleandro on 2014-03-26
Hi guys,

Hope you can help me with this. I am having an error when accessing update manager.

i did sudo apt-get update and here is the output (i only included the error)

```
Get:79 http://ph.archive.ubuntu.com oneiric-backports/main Translation-en [2,292 B]                                                                   
Get:80 http://ph.archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]                                                                
Get:81 http://ph.archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]                                                                
Get:82 http://ph.archive.ubuntu.com oneiric-backports/universe Translation-en [11.8 kB]                                                               
Err http://ph.archive.ubuntu.com oneiric-updates/restricted Sources                                                                                   
  416  Requested Range Not Satisfiable
Err http://ph.archive.ubuntu.com oneiric-updates/multiverse Sources                                                                                   
  416  Requested Range Not Satisfiable
Err http://ph.archive.ubuntu.com oneiric-backports/main Sources                                                                                       
  416  Requested Range Not Satisfiable
Err http://ph.archive.ubuntu.com oneiric-backports/main i386 Packages                                                                                 
  416  Requested Range Not Satisfiable
Fetched 17.5 MB in 1min 18s (222 kB/s)     

```

EDIT: Fixed it with sudo rm -rf /var/lib/apt/lists/partial/*
hmm wonder why this happens.

---

### Post by ajgreeny on 2014-03-26
Oneiric (Ubuntu 11.10) is no longer supported so you really should upgrade to a newer version.
12.04 is supported for another 3 years, or 14.04 at present only beta, will be supported for 5 years, so until 2019.  It looks good at the moment, even to me, and I do not like unity, but could be persuaded with this version.

---

### Post by Bashing-om on 2014-03-26
arvyleandro; Hi ! Welcome to the forum .

Edit: Hey, AJ, I had not even thought of arvyleandro running an End Of Life release - Yikes !
@ arvyleandro; If this release is "onieric" then all below is null and void ! As advised by ajgreeny, install a current release.
XXXXXXXXXXXX

What you have done is but a temporary solution, as soon as the package manager's index files are "updated" the problem will re-appear.
To address the cause of the situation look to the cause in your sources list file(s).
> 
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) [color=blue]oneiric[/color]-updates/multiverse Sources

"oneiric" is no longer supported, and that "fetch" must be removed.
There are two places where this source may exist; /etc/apt/sources.list file, or within the additionals of the directory /etc/apt/sources.list.d .
To look:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
In the 1st instance - if found there, edit the file with your preferred text editor ( make a backup of the file prior to editing, SOP). Remove or comment out the offending line.
2nd instance - if found- a) remove the file [ sudo rm etc/apt/sources.list.d/<file_name>.list]; or b) comment out that line in your favorite text editor. 
Such that theses lines are no longer parsed by the package manager.

Once done check the status of the package management system:
```

sudo apt-get update
sudo apt-get upgrade

```
If all is now well, these commands will run with no generated errors.

If you are uncertain or hesitant or desire confirmation of required action, by all means- we are here, post back the outputs of the cat commands for our inspection and advisements.

[INDENT][INDENT]just my little bit to
[INDENT][INDENT][INDENT]try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by arvyleandro on 2014-03-26
Wow, amazing forums! Quick replies too. Well, I have been holding out on upgrading to 12. I cant do Ubuntu 13 since my laptop gets stuck when the installer is starting. Reason for holding back is because I am currently working on a rails project and I'm not sure if laptop will boot properly when upgraded to 12.

Thanks guys.

---

### Post by Bashing-om on 2014-03-27
arvyleandro; hello;

Running a out-of-support release is highly ill-advised !! Upgrade to a current version soonest.

Hey, OK; Try Lubuntu !
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT]regards
[/INDENT]

---

