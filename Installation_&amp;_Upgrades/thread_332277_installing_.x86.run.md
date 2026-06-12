---
title: "installing .x86.run"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by jgweb2000 on 2007-01-05
i am trying to install tremulous. when i double click the .x86.run file that i got off of tremulous.net it said that it couldnt read the scripting or whatever, it didnt like the coding and thought it was binary


web

---

### Post by bruenig on 2007-01-05
Why not install it from the repositories.
```
sudo apt-get install tremulous
```
It is in multiverse, so make sure you have that enabled first.

---

### Post by stanthecaddy22 on 2007-01-05
To install .run files, open the terminal and run a 'chmod +x [filename.run]' to make it executable and then you can invoke it by either "./[filename].run" or "sudo ./[filename].run" if it requires root permissions.

---

### Post by jgweb2000 on 2007-01-06
multiverse? whats that 

im gonna try the respository thing.

im a total noob if u didnt figgure that out

webby

---

### Post by taurus on 2007-01-06
Remove the # in front of all the lines in /etc/apt/sources.list that have universe & multiverse near the end (with deb at the beginning)...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jgweb2000 on 2007-01-06
ok, what

i dont know what the heck im doin, this is like my first install on linux ( i lied i installed teamspeak)

but yea, it installed and everything but it freezes

oh and it said that it couldnt find any packages named tremulous

web

---

### Post by jgweb2000 on 2007-01-06
ok i did the # thing

what next?


web

---

### Post by taurus on 2007-01-06
Open a terminal by clicking Applications, then Accessories, and then Terminal.  At the prompt,
type

```
gksudo gedit /etc/apt/sources.list
```
Now, use the arrow keys to move up and down and remove the # sign in front of all the lines that have **deb** at the beginning.  Save it and then from the same terminal, run

```
sudo aptitude update
sudo aptitude install tremulous
```

---

### Post by jgweb2000 on 2007-01-06
kk im doin the aptitude update one

takin forever

but ok, i tryed to install tremulous from the download off tremulous.net and it just locks up ma pooter, should i remove it first?

web

---

### Post by taurus on 2007-01-06
If it locks up your machine, then you need to remove it or you will a one sick machine soon...

---

### Post by jgweb2000 on 2007-01-06
how would i go about doing that, ????apps, add remove????


web

---

### Post by jgweb2000 on 2007-01-06
i found where it is installed but i dunt have permissions, whats the console delete command?


web

---

### Post by taurus on 2007-01-06
```
sudo rm **filename**
```
(And better be careful with that because you cannot undelete it later...)

---

### Post by jgweb2000 on 2007-01-06
can i remove the whole folder?

---

### Post by taurus on 2007-01-06
```
sudo rm -rf **directory_name**
```
(Again, think twice before you hit the Return key because that command won't ask you for a confirmation...)

---

### Post by jgweb2000 on 2007-01-06
sudo aptitude install tremulous

that didnt work, it said it couldnt find it

web

---

### Post by taurus on 2007-01-06
Well, I have four versions that I can install on my machine, according to synaptic!

tremulous 1.1.0-1
tremulous-data 1.1.0-1
tremulous-doc 1.1.0-2
tremulous-server 1.1.0-2

---

### Post by jgweb2000 on 2007-01-06
is there a way i can get my snamptic goin to where it gets updates from the net or something (im running ubuntu 6.06)

web

---

### Post by jgweb2000 on 2007-01-06
yea it doesnt show any results when i search for tremulous

web

---

### Post by taurus on 2007-01-06
I think the problem perhaps is in your repos.  Therefore, why don't you post your /etc/apt/sources.list here then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jgweb2000 on 2007-01-06
i got updates from the net, no avail.

is this the pakage manager in system/administration?

---

### Post by jgweb2000 on 2007-01-06
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2007-01-06
Maybe you want to use this version...  Back up your old sources.list first with

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.original
```
Then, open it with an editor and remove everything in it.

```
gksudo gedit /etc/apt/sources.list
```
Now, paste the following lines to that empty /etc/apt/sources.list and save it.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 

```
Then run

```
sudo aptitude update
sudo aptitude install tremulous tremulous-data tremulous-doc
```

---

### Post by jgweb2000 on 2007-01-06
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


thats what i got (after everything else

web

the first "sudo aptitude update"

did that

---

### Post by jgweb2000 on 2007-01-06
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


thats what i get when i did the tremulous command

web

---

### Post by taurus on 2007-01-06
Do you happen to have synaptic running at the same time?  If you have synaptic open right now, close it and run these two commands from a terminal again.  Otherwise, what's the output of this command from a terminal?

```
ps -A
```

---

### Post by jgweb2000 on 2007-01-06
why am i so stupid... synaptec is running

lemme try again

---

### Post by jgweb2000 on 2007-01-06
ok the first one ran fine but...

jordan@jordan-desktop:~$ sudo aptitude install tremulous tremulous-data tremulous-doc
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "tremulous"
Couldn't find any package whose name or description matched "tremulous-data"
Couldn't find any package whose name or description matched "tremulous-doc"
The following packages have been kept back:
  liblircclient0 libtag1c2a libtheora0 readahead
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jordan@jordan-desktop:~$

ya 

web

---

### Post by jgweb2000 on 2007-01-06
meh

idk what do i do](*,) ](*,) ](*,) 

web

---

### Post by taurus on 2007-01-06
Now, open synaptic and in the Search field, type **tremulous** and hit Enter to see if it can find anything!

---

### Post by jgweb2000 on 2007-01-06
nothing no results, anything else i can try, it would be cool if this worked

](*,) ](*,) 

web

---

### Post by taurus on 2007-01-06
I am going to double check so can you post your /etc/apt/sources.list here again...

```
cat /etc/apt/sources.list
```

---

### Post by jgweb2000 on 2007-01-06
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free


btw like ur sig

web

---

### Post by jgweb2000 on 2007-01-06
is it not working cause im on 6.06 and not on 6.10?

web

---

### Post by taurus on 2007-01-06
You did run "sudo aptitude update" right?

---

### Post by jgweb2000 on 2007-01-06
yea i think so im gonna run it again

---

### Post by jgweb2000 on 2007-01-06
ran fine

---

### Post by jgweb2000 on 2007-01-06
should i go into the synaptic thing again and look?

---

### Post by jgweb2000 on 2007-01-06
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) 404 Not Found


thats what i get when i try to update the synaptic updater

web

---

### Post by taurus on 2007-01-06
Put a # sign in front of the last two lines in your /etc/apt/sources.list.

```

#deb http://packages.freecontrib.org/plf/ dapper free non-free
#deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```
Save it and run

```
sudo aptitude update
```
again and see if there is any error message.

---

### Post by jgweb2000 on 2007-01-06
no problems running sudo aptitude update

im running the trem one right now

web

---

### Post by jgweb2000 on 2007-01-06
jordan@jordan-desktop:~$ sudo aptitude install tremulous tremulous-data tremulous-doc
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "tremulous"
Couldn't find any package whose name or description matched "tremulous-data"
Couldn't find any package whose name or description matched "tremulous-doc"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jordan@jordan-desktop:~$

nothing in synaptec either
same diff
web

---

### Post by jgweb2000 on 2007-01-06
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

---

### Post by taurus on 2007-01-06
Sorry but can't find it anywhere in the Dapper...

[http://packages.ubuntu.com/dapper/games/](http://packages.ubuntu.com/dapper/games/)

So, I guess you have to either upgrade (or do a fresh install) to Edgy or download it from their website!

---

### Post by jgweb2000 on 2007-01-06
so if i install edgy it will work right off the bat

goes and gets iso (swapps back to windows hd)

lol

gates and his devil child all over again

web

---

### Post by taurus on 2007-01-06
If you enable both universe and multiverse like we have done so far, it should be in the repos because its on my machine in the office...

Just checked and yip.  It's in the multiverse repos!!!

[http://packages.ubuntu.com/edgy/games/tremulous](http://packages.ubuntu.com/edgy/games/tremulous)

---

### Post by jgweb2000 on 2007-01-06
thank you 

i am now running edgy and am downloading tremulous right off the bat :) 

no more ](*,) ](*,)  (although im sure there will be)

i will post if i have problems with it installing

web

---

### Post by taurus on 2007-01-06
Good luck and have fun.

---

### Post by jgweb2000 on 2007-01-11
thanks, turns out i didnt have nvidia drivers installed.... w/e thats why cedega ran so crappily



thanks again
web

---

### Post by taurus on 2007-01-11
Did somebody just say nVidia driver?  ;) 

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by jgweb2000 on 2007-01-11
nvidia driver wont install, wants me to stop the x server, i dont think that is possible and still keep ubuntu running...

web

---

### Post by taurus on 2007-01-11
How did you install it?

The link that I provided walks you through the whole process and you don't have to stop any X!  Sounds to me like you've downloaded the one from nVidia's site and try to install it by hand.

---

