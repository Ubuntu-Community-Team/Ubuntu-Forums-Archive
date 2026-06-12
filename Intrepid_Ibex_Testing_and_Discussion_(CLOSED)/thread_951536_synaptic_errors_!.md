---
title: "synaptic errors !"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by justborn on 2008-10-18
i get this error after upgrade to 8.10

"failed to fetch http//repoubuntusoftware.info/dists/hardy/all/binary-i386/pakages.gz 404 not found
some index files failed to download,they have been ignored,or old once used instead."


i am not able to use the normal mode the desktop freezes after logging in .


i am using the terminal session at present.

---

### Post by drs305 on 2008-10-18
Have you used this repository before? Normally the ***/dists*** section is left out in the sources.list.  

Going to the site, it confirms that the path for its repositories should be entered in sources.list as "deb [http://ubuntusoftware.info/](http://ubuntusoftware.info/) edgy all"  Note that I do not know if they have a hardy repository or not.

You can go to the web site and read how to add their repositories at:[http://repoubuntusoftware.info/]("http://repoubuntusoftware.info/")

---

### Post by mick222 on 2008-10-18
there has been numerous posts about these repositories better to disable them go to 
system-admin- software sources and untick the box see if synaptic works then.

---

### Post by justborn on 2008-10-18
> **drs305 said:**
> Have you used this repository before? Normally the ***/dists*** section is left out in the sources.list.  

Going to the site, it confirms that the path for its repositories should be entered in sources.list as "deb [http://ubuntusoftware.info/](http://ubuntusoftware.info/) edgy all"  Note that I do not know if they have a hardy repository or not.

You can go to the web site and read how to add their repositories at:[http://repoubuntusoftware.info/]("http://repoubuntusoftware.info/")

please can u be more explaing, iam not able to get u

---

### Post by justborn on 2008-10-18
> **mick222 said:**
> there has been numerous posts about these repositories better to disable them go to 
system-admin- software sources and untick the box see if synaptic works then.

can u tell me how to disable it using the command line,because i am stuck wid it

---

### Post by drs305 on 2008-10-18
justborn,

I went to the site and their directory structure did not allow me to access the repositories in the normal manner. Coupled with what mick222 posted I would recommend not using the site. 

When you say you are using the terminal session do you mean you are using apt-get to try to update your computer and you are getting errors? Can you access either software sources or synaptic to modify your sources.list? If you can, go to 'Third-Party Updates' and untick the reference to repoubuntusoftware.

If you can't access either synaptic or software sources:
If you are trying to update your computer but don't need apps from this particular site, you can modify your sources.list to exclude this site when you perform your updates.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

Place a comment symbol (#) in front of any lines that mention 'repoubuntusoftware', save the file and then run your update again.

---

### Post by justborn on 2008-10-18
> **drs305 said:**
> justborn,

I went to the site and their directory structure did not allow me to access the repositories in the normal manner. Coupled with what mick222 posted I would recommend not using the site. 

When you say you are using the terminal session do you mean you are using apt-get to try to update your computer and you are getting errors? Can you access either software sources or synaptic to modify your sources.list? If you can, go to 'Third-Party Updates' and untick the reference to repoubuntusoftware.

If you can't access either synaptic or software sources:
If you are trying to update your computer but don't need apps from this particular site, you can modify your sources.list to exclude this site when you perform your updates.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

Place a comment symbol (#) in front of any lines that mention 'repoubuntusoftware', save the file and then run your update again.
i am able to access synaptic,and what so i do after disabling the mentioned repository?

---

### Post by drs305 on 2008-10-18
> **justborn said:**
> i am able to access synaptic,and what so i do after disabling the mentioned repository?

After disabling the repoubuntusoftware repo, if still in synaptic you would hit the "Reload" button to update the repository list. This should refresh the repositories.

If you are in a terminal, run the following. The error message about the problem repo should no longer appear.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by justborn on 2008-10-18
> **drs305 said:**
> After disabling the repoubuntusoftware repo, if still in synaptic you would hit the "Reload" button to update the repository list. This should refresh the repositories.

If you are in a terminal, run the following. The error message about the problem repo should no longer appear.
```
sudo apt-get update && sudo apt-get upgrade
```

the the commands give me errors,i think my repositories are cuasing the problem.
and can u paste me the list of ibex repositories,so that i can delete all the repositories in the sources.list file and add only the needed once ,and after doing that i will try the commands after that and that will be a solutiohn to my problem .

---

### Post by drs305 on 2008-10-18
justborn,

I started up my other computer and here is a sources.list from Intrepid beta. If this does not work, please start a new thread in the Intrepid forum. Questions regarding that version are supposed to be in that forum until Intrepid is officially released. You will probably get more timely answers on Intrepid from that forum. Hope this sources.list fixes your problem. :-)

[Intrepid Ibex Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=346")

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.


deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main universe multiverse #Added by software-properties


```

---

### Post by gjoellee on 2008-10-18
you where able to access synaptic...good!

Lets open it:
Now click on Settings and then on Repositories go to find the "bad" repo and delete it or disable it. (If it opens a new window with the tab "Therd Party (something)" you will find it there :)

---

### Post by justborn on 2008-10-18
> **drs305 said:**
> justborn,

I started up my other computer and here is a sources.list from Intrepid beta. If this does not work, please start a new thread in the Intrepid forum. Questions regarding that version are supposed to be in that forum until Intrepid is officially released. You will probably get more timely answers on Intrepid from that forum. Hope this sources.list fixes your problem. :-)

[Intrepid Ibex Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=346")

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.


deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main universe multiverse #Added by software-properties


```
after making changes i nthe source.list,when i try "apt-get upgrade"

i get"E: sub-process /usr/bin/dpkg returned an error code (1)"

what should i do?

---

### Post by justborn on 2008-10-18
> **gjoellee said:**
> you where able to access synaptic...good!

Lets open it:
Now click on Settings and then on Repositories go to find the "bad" repo and delete it or disable it. (If it opens a new window with the tab "Therd Party (something)" you will find it there :)

i have removed all third party repos.(every thing)

---

### Post by Sef on 2008-10-18
Moved to Ibex forum.

---

### Post by plucky on 2008-10-18
> after making changes i nthe source.list,when i try "apt-get upgrade"

i get"E: sub-process /usr/bin/dpkg returned an error code (1)"

what should i do? 


Try ```
sudo apt-get update
``` to reload the package information,before you "sudo apt-get upgrade" to install the updates.


Good Luck

---

