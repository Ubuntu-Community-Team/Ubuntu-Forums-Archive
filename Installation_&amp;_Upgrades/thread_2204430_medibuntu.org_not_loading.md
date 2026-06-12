---
title: "medibuntu.org not loading"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by borgward on 2014-02-08
I just installed Ubuntu 13.1 yesterday. I ran the Update Manager. It did not work. I then opened a terminal and ran:

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

The update failed at 100%

I then used Firefox to get to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) which led me to [http://guidetest.a.id.opendns.com/?url=packages%2Emedibuntu%2Eorg&servfail&nref](http://guidetest.a.id.opendns.com/?url=packages%2Emedibuntu%2Eorg&servfail&nref) which led me to 
[http://www.website-unavailable.com/main?wc=EWJoExd5AxtfBBR2GAkCHA%3D%3D&url=packages.medibuntu.org&servfail=&nref=&w=1280&h=604&ifc=0](http://www.website-unavailable.com/main?wc=EWJoExd5AxtfBBR2GAkCHA%3D%3D&url=packages.medibuntu.org&servfail=&nref=&w=1280&h=604&ifc=0) where I got the mesage:

Hmm, packages.medibuntu.org isn't loading right now.

The servers that run packages.medibuntu.org are having some trouble. This is usually just a temporary problem, so you might want to try again in a few minutes.

That was 12 hours and 6 attempts ago.

Are the servers really down?

---

### Post by kostkon on 2014-02-08
> **borgward said:**
> Are the servers really down?
[Yes, Medibuntu is no more.]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by borgward on 2014-02-08
So how are updates supposed to be done?

---

### Post by Bashing-om on 2014-02-08
borgward; Hi !

They are not; Remove the "fetch" lines from your sources.list file(s).
```

sudo apt-get update
sudo apt-get upgrade

```
To see what the consequences are and what must now be done (if anything).

[INDENT][INDENT]the times
[INDENT][INDENT]they are a change'n
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-02-08
Media howto: 
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by deadflowr on 2014-02-08
> **borgward said:**
> So how are updates supposed to be done?

Of the packages that mediubuntu held the most significant was the libdvdcss package.
That was moved over to [videolan]("http://blogs.kde.org/2013/09/11/medibuntu-disappear-libdvdcss-now-direct-videolan"). 
The install script (/usr/share/doc/libdvdread4/install-css.sh) has been updated to reflect the change.

I'm unclear on where any of the other packages have gone.

---

### Post by Bashing-om on 2014-02-08
borgward; Hi !

Lot's of help here on the forum ! See all the great aboves ^^^
We need to edit your sources.list file(s).
Post the outputs - between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

So we see what is to be done.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by borgward on 2014-02-08
cat -n /etc/apt/sources.list

$ cat -n /etc/apt/sources.list
     1	deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import
     2	deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
     3	deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
     4	deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
     5	deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise partner
     6	deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free
     7	
     8	#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
     9	#deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games

cat /etc/apt/sources.list.d/*.list

$ cat /etc/apt/sources.list.d/*.list
#deb file:///usr/share/local-repository binary/

---

### Post by borgward on 2014-02-08
> **oldfred said:**
> Media howto: 
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

I do not see how any of that applies to running the update manager. I guess I should be asking where are the updates for Linux Mint 13.

---

### Post by Bashing-om on 2014-02-08
borgward; Hi !

Finally getting back 'round to ya !

ok: offending entry is line 6 in /etc/apt/sources.list file.
Remember to make a current backup prior to editing any file.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-08Feb2014

```

Make the change in the file: - activate your text editor -
```

gksudo gedit /etc/apt/sources.list

```
I use gedit for the text editor, substitute your favorite.
In the editor arrow down to "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free"
and either place a comment character '#' (commenting why you commented out the line would be a good thing to do ) at the start of the line or better yet, completely remove the line.
Save the file and exit back to terminal:
terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
And post back if there are any reported errors.
Else you are good to go.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by donut123 on 2014-02-08
Medibuntu is discontinued
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

