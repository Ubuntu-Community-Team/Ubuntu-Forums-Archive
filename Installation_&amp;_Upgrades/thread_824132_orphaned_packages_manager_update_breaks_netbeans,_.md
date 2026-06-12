---
title: "orphaned packages manager update breaks netbeans, seemingly forever"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by kendase3 on 2008-06-09
So I'm a little perplexed, this is the first really major technical problem I've had with Ubuntu since I started in 7.04.  I found the seemingly handy orphaned packages remover, so I decided to run it to get rid of whatever packages I no longer needed.  Not being overly technical, I took its word that four or so packages which I did not recognize really were orphaned.  However, when I went to start netbeans, I noticed it had been uninstalled from my system, and that when I went to reinstall it, I got the following message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libnb-java1-java: Depends: libappframework-java but it is not going to be installed
                    Depends: libbeansbinding-java but it is not going to be installed
                    Depends: libnb-ide8-java (>= 6.0.1) but it is not going to be installed
                    Depends: libnb-javaparser-java (>= 6.0) but it is not going to be installed
E: Broken packages


Any ideas anyone?  I can't seem to make any headway downloading anything without getting a similar message.

---

### Post by peitschie on 2008-06-09
Hi

What happens if you run the following in terminal:
```
sudo apt-get install -f
```

---

### Post by kendase3 on 2008-06-09
kendase3@hutbot:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Seemingly nothing.  I traced the dependencies all the way back to tzdata, which I supposedly have, and yet packages dependent on it can't seem to link to it.  When I go down the line it seems as though I've somehow destroyed my entire java dependency tree!  This is terrible for me especially because I use Netbeans to program on a daily basis, and also just very strange.

---

### Post by peitschie on 2008-06-09
Have you tried using synaptics to fix it?

(alt+f2, gksu synaptics)

---

### Post by kendase3 on 2008-06-09
Yeah, I've tried using the package manager, apt-get, and any other way I could think of to try to get the dependencies, but for some reason it won't let me.  

```
kendase3@hutbot:~$ sudo apt-get install netbeans

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  netbeans: Depends: libnb-apisupport1-java (>= 6.0.1) but it is not going to be installed
            Depends: libnb-ide8-java (>= 6.0.1) but it is not going to be installed
            Depends: libnb-java1-java (>= 6.0.1) but it is not going to be installed
E: Broken packages

```

Synaptic just gives me a GUI pop-up of the same.

So I guess my real question is, what do I have to remove to just get a good install again?  I wouldn't mind reinstalling java from scratch if I had to.

edit: but I don't really know how

---

### Post by kendase3 on 2008-06-09
This seems to be the whole problem:

```
kendase3@hutbot:~$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/656kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 243790 files and directories currently installed.)
Preparing to replace tzdata 2008c-1ubuntu0.8.04 (using .../tzdata_2008c-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2008c-1ubuntu0.8.04) ...

User defined timezone, leaving /etc/localtime unchanged.
Local time is now:      Mon Jun  9 23:27:43 EDT 2008.
Universal Time is now:  Tue Jun 10 03:27:43 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


kendase3@hutbot:~$ sudo apt-get install tzdata-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2008b-1ubuntu1) but 2008c-1ubuntu0.8.04 is to be installed
E: Broken packages

```

For some reason, tzdata-java won't install even though I've obviously installed the prerequisite.  Is there something about that version jargon that's much more important than I realize?  There may be other dependency conflicts like this that are similar, I only traced one back to its source.

---

### Post by peitschie on 2008-06-10
It is complaining because the wrong version of tzdata is already installed.  It looks like you have a partial update installed...

Have you turned off hardy-updates by chance?  This is enabled/disabled in System > Administration > Software Sources > Updates.  Make sure "recommended updates" is checked, then save and reload your package list.

Once this is done, do the following:
```

sudo aptitude install tzdata tzdata-java

```

Just for interests sake, here is the one you are trying to install: [http://packages.ubuntu.com/hardy/tzdata-java](http://packages.ubuntu.com/hardy/tzdata-java)
and here is the one that you should be installing: [http://packages.ubuntu.com/hardy-updates/tzdata-java](http://packages.ubuntu.com/hardy-updates/tzdata-java)

Note the differences in dependencies...

---

### Post by kendase3 on 2008-06-10
It worked!  I wonder how I managed to turn those off?  I'd never been in that menu, perhaps the orphaned package manager burped.  Anyway, I'm reinstalling Netbeans now.  Thanks a lot for your help!  It's very much appreciated, don't know what I would have done otherwise.

---

### Post by peitschie on 2008-06-10
Glad it has all resolved.  It was my pleasure to assist :)

---

### Post by DaveAU on 2008-06-10
I had the same problem and checking "recommended updates" worked for me as well.

Is "recommended updates" checked by default?  I've got a few systems and none of them had it checked - I can remember monkeying with one of the sources files back with fiesty, but the other has been unmodified from about the same time.  

If it's unchecked by default should someone point this out to some package maintainers? - not having it turned on and using the "important updates" removed java from my system because of a change to some timezones, which I'm assuming isn't the expected or desired behaviour. 

These things happen I guess, but since it took some less than obvious diagnosing and googling to find this thread I figured I'd ask about whether someone should be told something so either newer folks in the same position can get themselves out of trouble or so future trouble like this can be avoided.  No idea who to tell though.

All completely moot if the sources files on all of my systems have been messed with previously :)

---

### Post by peitschie on 2008-06-10
Apparently it is checked by default
[quote=http://www.informit.com/articles/article.aspx?p=1161217&seqNum=4]By default both the important security updates and recommended updates are checked to ensure that you have the latest bug fixes and patches.[/quote]

Though this is the kind of issue that would easily go unnoticed if introduced... I'll keep an eye out on my next install.

---

### Post by DaveAU on 2008-06-11
Yeah - my bad on that one - got someone I installed Ubuntu for to check their system (which I know for sure hasn't had the sources messed with) and it has the recommended system checked.  

Thanks for the fix and sorry for the barking up the wrong tree :)

---

### Post by adam77 on 2008-06-21
This thread would seem to be related to the following netbeans/tzdata bug...

[https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/240502](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/240502)

and this one...

[https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/241268](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/241268)

---

### Post by adam77 on 2008-06-21
The following worked for me, thanks!

(However, installing netbeans also installed openJDK, even though I already have the Sun JDK already installed. Strange.)

> **peitschie said:**
> It is complaining because the wrong version of tzdata is already installed.  It looks like you have a partial update installed...

Have you turned off hardy-updates by chance?  This is enabled/disabled in System > Administration > Software Sources > Updates.  Make sure "recommended updates" is checked, then save and reload your package list.

Once this is done, do the following:
```

sudo aptitude install tzdata tzdata-java

```

Just for interests sake, here is the one you are trying to install: [http://packages.ubuntu.com/hardy/tzdata-java](http://packages.ubuntu.com/hardy/tzdata-java)
and here is the one that you should be installing: [http://packages.ubuntu.com/hardy-updates/tzdata-java](http://packages.ubuntu.com/hardy-updates/tzdata-java)

Note the differences in dependencies...

---

