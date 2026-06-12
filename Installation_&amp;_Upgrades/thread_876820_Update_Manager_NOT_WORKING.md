---
title: "Update Manager NOT WORKING"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Vasilisgr on 2008-08-01
Hi guys, i am an absolute newbie in ubuntu and linux in general (just 2 days since i got my ubuntu setup ) and i already manage to screw something up .... :( .... and i don't know what.... My update manager refuses to operate no mater what i do I get this message : 

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 63 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

and this one 

E: Type '“deb' is not known on line 63 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Something is obviously wrong but as a newbie i don't know what... everything started after i tried to install an emulator for neo geo ... at least i think so.. :( Can anyone help me with this issue ?? Because i liked the linux spirit :-)  Thank very much in advance

---

### Post by iaculallad on 2008-08-01
Try to post the content of your sources.list file. Open your terminal and issue the command below.

```
cat etc/apt/sources.list
```

File has an error on line 63.

---

### Post by Malac on 2008-08-01
Go to [System->Administration->Software Sources] and see what repositories are listed there. You can disable repositories from that app.
If that won't open post the contents of /etc/apt/sources.list and I will try to help.

---

### Post by Vasilisgr on 2008-08-01
Guys thank you much for your fast response, i tried tis :    cat etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory

nothing happen :-( 

In software sources i don't know what to do i just change server and chose the one in USA but nothing... and at third party apps i deleted the getautomatix thing .... but again nothin... 

 Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 63 in source list /etc/apt/sources.list, E:The list of sources could not be read

:confused::confused::confused::confused:

Thanx again guys :-)

---

### Post by Vasilisgr on 2008-08-01
and now 63 is 61 :confused:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 61 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by iaculallad on 2008-08-01
A typo error. That should be:

```
cat /etc/apt/sources.list
```

---

### Post by IntuitiveNipple on 2008-08-01
I think you mis-typed - looks like you forgot the leading / on the path. Without it the path would be relative to the directory you were in when typing the command:
```

cat /etc/apt/sources.list

```

---

### Post by Vasilisgr on 2008-08-01
63 again...

---

### Post by Vasilisgr on 2008-08-01
vasilis@vasilis-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;
vasilis@vasilis-laptop:~$ 


this is the resault :-)

---

### Post by iaculallad on 2008-08-01
On your terminal, open your sources.list file for editing:

```
gksudo gedit /etc/apt/sources.list
```

and delete the line of text below:

> “deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

located at the last part of the file. Save and Close.

---

### Post by Malac on 2008-08-01
> **Vasilisgr said:**
> 
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main"
This is the faulty line.

Open a Terminal
```
gksu gedit /etc/apt/sources.list
```
Find that line at the bottom and remove quotes (").
Hit Save.
Then Exit.
You may want to change the "feisty" to "hardy" _without_ the quotes.

---

### Post by arcanus on 2008-08-01
do the following in console:

```

sudo gedit /etc/apt/sources.list

```

The last line is 
```
&#8220;deb http://www.getautomatix.com/apt feisty main&#8221;
```

it SHOULD be 
```
deb http://www.getautomatix.com/apt feisty main
```
WITHOUTH the quotes, so remove those, save and exit, then issue the following command in the shell:

```
sudo apt-get update
```

Should do the trick :)

---

### Post by arcanus on 2008-08-01
> **Malac said:**
> 
You may want to change the "feisty" to "hardy" _without_ the quotes.

Dont do that, thats a ugly way of upgrading the system, you should follow the instructions on the [Upgrading your existing Ubuntu installation | Ubuntu]("http://www.ubuntu.com/getubuntu/upgrading") page if you want to upgrade your system to a more recent version of ubuntu ;)

---

### Post by Vasilisgr on 2008-08-01
thank you very much my friend now is working fine :-) because i am a newbie you will see my next screw up post preaty soon :-) THNX AGAIN MATE

---

### Post by Malac on 2008-08-01
> **arcanus said:**
> Dont do that, thats a ugly way of upgrading the system, you should follow the instructions on the [Upgrading your existing Ubuntu installation | Ubuntu]("http://www.ubuntu.com/getubuntu/upgrading") page.Actually as the rest of his system repo is hardy it is correct that his automatix should be the hardy version.

---

### Post by dje on 2008-08-01
> **Malac said:**
> Actually as the rest of his system repo is hardy it is correct that his automatix should be the the hardy version.

there is no automatix for hardy, the software is discontinued and many believed it was dubious while it was active. **do not install it on hardy** as it was never released and adding that repo could damage your system, remove it from your sources.list and uninstall automatix, imho

dje

---

### Post by Vasilisgr on 2008-08-01
Yes my friends DO NOT install automatix in hardy thats what happen to my system and then my update manager broke ! its not supported :-(

THANKS TO EVERY ONE FOR THE HELP:guitar:

---

### Post by ouman63 on 2008-08-01
Hello! I am new user to Ubuntu.  I got fed up with Vista (aka Windows ME 2.0) and all the crashed.  Anyways, It seems that I have the same problem with my update manager.

This is what it says:

E: Type 'Alphaz63' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.


Any help would be greatly appreciated.  I was trying to install AWN when this started happening.

Thanks again

---

### Post by dje on 2008-08-01
> **ouman63 said:**
> Hello! I am new user to Ubuntu.  I got fed up with Vista (aka Windows ME 2.0) and all the crashed.  Anyways, It seems that I have the same problem with my update manager.

This is what it says:

E: Type 'Alphaz63' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.


Any help would be greatly appreciated.  I was trying to install AWN when this started happening.

Thanks again

Please post the output of the following command from the terminal (Applications >> Accessories >> Terminal):
```
cat /etc/apt/sources.list
```

dje

---

### Post by Malac on 2008-08-01
> **ouman63 said:**
> Hello! I am new user to Ubuntu. I got fed up with Vista (aka Windows ME 2.0) and all the crashed. Anyways, It seems that I have the same problem with my update manager.
 
This is what it says:
 
E: Type 'Alphaz63' is not known on line 51 in source list /etc/apt/sources.list
E: The list of sources could not be read.
 
 
Any help would be greatly appreciated. I was trying to install AWN when this started happening.
 
Thanks again
 see post #11

---

### Post by ouman63 on 2008-08-01
Thanks Malac!

---

### Post by Malac on 2008-08-02
> **ouman63 said:**
> Thanks Malac!
You're Welcome :)

---

