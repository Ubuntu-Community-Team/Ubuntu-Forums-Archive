---
title: "terminal problem"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by Jo Ann on 2008-03-10
I am trying to update gimp on ubuntu which i finally got installed. and i used terminal to try and update gimp using terminal and this is what i did:

sudo apt-get remove gimp

and it said it did.

then i did

sudo aptitude install gimp

and it said it did.

well i still have 2.0 and no evidence of removal and up date cuz 2.0 is still running.

i downloaded gimp 2.4.5 but i have not clue how to uninstall gimp and then install the update....sigh.

---

### Post by jken146 on 2008-03-10
2.4.2 is the latest version in the Gutsy (7.10) repositories.  Try ```
sudo aptitude update

sudo aptitude upgrade
```

---

### Post by Jo Ann on 2008-03-10
thanx, went into synapses and it said gimp was 2.4.2, the newest stable version is 2.4.5, but i will try that. should i use sudo in front of that?

---

### Post by Jo Ann on 2008-03-10
i used 

sudo aptitude full-upgrade gimp and it upgraded python

oh well. :confused:

---

### Post by jken146 on 2008-03-10
Ubuntu 7.10 is six months old now, so I'm not surprised that there is a newer stable version of GIMP.  If you copy & paste the commands I gave you into a terminal (or use Synaptic to install all updates)  you'll get version 2.4.2.

If you really need 2.4.5 -- I don't know what the changes are myself -- go to [http://www.getdeb.net/release.php?id=2265](http://www.getdeb.net/release.php?id=2265) and click on the link that says just "gimp".  Double-click on the file, once downloaded, to install it.  If you do this, though, Ubuntu won't update it for you any more.

---

### Post by jken146 on 2008-03-10
> **Jo Ann said:**
> i used 

sudo aptitude full-upgrade gimp and it upgraded python

oh well. :confused:

Did you run the commands I gave you?  If you did, what does it say when you type ```
gimp -version
```?

---

### Post by Jo Ann on 2008-03-10
my gimp vs is 2.4.2, and i did download the 2.4.5,  but have no way to install it that i know. would rather have ubuntu do it.  the site said to use apt-get install gimp to get the new 2.4.5 vs but that didnt work either.

---

### Post by jken146 on 2008-03-10
You can only get up to 2.4.2 with apt-get, aptitude or Synaptic.  The link I gave you has a .deb package for 2.4.5, which is the easiest way to install it.  What sort of file did you download?

---

### Post by Jo Ann on 2008-03-10
tar.bz2

i am downloading it now

---

### Post by jken146 on 2008-03-10
It looks like you downloaded the source code, so if you want to install it that way you'll have to compile it first.  [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) should help.

---

### Post by Jo Ann on 2008-03-10
i get an error when i try to run the deb file. it said dependency is not satisfiable: gimp-data

---

### Post by DarinB on 2008-03-10
i love ubuntu but i have the same problem with all of my feisty programs they won't upgrade to the next level no matter what i try.
i.e open office
Gimp
thunderbird 
etc.
it is really confusing maybe some one from the tech circle could address this.
i don't think this is an OS upgrade issue the new programs should update even if you don't install Gutsy or later install hardy!!!!!!

---

### Post by Jo Ann on 2008-03-11
gutsy???? istalled????  hmmmmm.  what is gutsy, thought it was a he/she:rolleyes:

---

### Post by Jo Ann on 2008-03-11
i remember a time when i could jump between windows and OS2....now those where the fun days. LOL

---

### Post by Jo Ann on 2008-03-11
i also remember the only way to access the net was thru a terminal and using linux commands.  nothing at all like today.  i first got on the net around 1994.  and i have always hated windows, and vista has forced me back to linus cuz i can't even fax, cuz i can't afford the full blown vista.

---

### Post by jken146 on 2008-03-11
> **DarinB said:**
> i love ubuntu but i have the same problem with all of my feisty programs they won't upgrade to the next level no matter what i try.
i.e open office
Gimp
thunderbird 
etc.
it is really confusing maybe some one from the tech circle could address this.
i don't think this is an OS upgrade issue the new programs should update even if you don't install Gutsy or later install hardy!!!!!!

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


[quote=Jo Ann]gutsy???? istalled???? hmmmmm. what is gutsy, thought it was a he/she[/quote]
Gutsy Gibbon is the other name for Ubuntu 7.10, the latest version thant has been released (it was released in October 2007, hence 7.10).  Fiesty Fawn was 7.04 and Hardy Heron will be 8.04.

---

### Post by Jo Ann on 2008-03-11
OH...software updates in alphabetical order....got it. :KS

---

### Post by jken146 on 2008-03-11
No, it's not software updates.  There is a new release (version) of the Ubuntu operating system every six months.  When they put the next release together, they will use the latest stable versions of all the pieces of software that they put in the repositories.

---

### Post by Jo Ann on 2008-03-11
is there a reason the deb version didn't open?

---

### Post by jken146 on 2008-03-11
[quote=Jo Ann]it said dependency is not satisfiable: gimp-data [/quote]
The reason is that the package **gimp** depends on the package **gimp-data** -- the latter has to be installed or the former won't work.  This probably means that the version of gimp-data in the repository is too old, so you'll have to download the .deb for gimp-data from the link I gave you earlier.

This is why it's easier to stick with the versions in the repositories.

edit:  I've just [discovered]("http://packages.ubuntu.com/hardy/gimp") that 2.4.5 will be in Hardy, which will be released in April.  If you can wait until then, you don't need to do anything.

By the way, why do you need 2.4.5?

---

### Post by Jo Ann on 2008-03-11
oh yeah...i can wait till then. updated/upgrading ubuntu is easier than gimp isn't it!!!?????:lolflag:

thanx jken for all your help, i really appreciate it. love the way you get help pretty darn fast on here!!!!

gonna go to bed....rather getting late. kinda like the ole days when i would be up till 4 am making pictures out of asteriks on my old timex sinclair with a full 1k of memory. LOL

---

### Post by Jo Ann on 2008-03-11
one more thing, i can read my drives from vista...can i like get my images directly from them as well? didn't try cuz i was gimpin'

good night!!!!

---

### Post by jken146 on 2008-03-11
You can read and write to NTFS partitions, so yes, if I understand you correctly.  > thanx jken for all your help, i really appreciate it. love the way you get help pretty darn fast on here!!!!You're welcome :)

---

