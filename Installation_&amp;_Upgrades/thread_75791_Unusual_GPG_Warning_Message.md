---
title: "Unusual GPG Warning Message"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by azteech on 2005-10-14
When I went to do a dist-upgrade (after doing update) from breezy (5.10-RC, Colony 5) to Breezy (5.10 Final), received the following warning message:

W: GPG error: [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

see attachment for screenshot of error window

Any idea why I would get this, and how do I correct the issue?

---

### Post by Vytas on 2005-10-14
[QUOTE=azteech]When I went to do a dist-upgrade (after doing update) from breezy (5.10-RC, Colony 5) to Breezy (5.10 Final), received the following warning message:

W: GPG error: [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

see attachment for screenshot of error window

Any idea why I would get this, and how do I correct the issue?[/QUOTE]

Strange... I got this too today.

Btw the message is exactly the same.

W: GPG error: [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Brunellus on 2005-10-14
I got the same thing.  I dist-upgraded from the console, so no pretty screenie.

Note that after a cold boot, I was unable to start X, nor was I able to run irssi from the commandline (to avail myself of the patient help of #ubuntu  and #ubuntuforums on freenode).  Checking things over, it seems that a number of packages were either not downloaded or not installed, and I can only guess that they should have come from the affected repository.

---

### Post by azteech on 2005-10-14
[quote=Brunellus]I got the same thing.  I dist-upgraded from the console, so no pretty screenie.

Note that after a cold boot, I was unable to start X, nor was I able to run irssi from the commandline (to avail myself of the patient help of #ubuntu and #ubuntuforums on freenode). Checking things over, it seems that a number of packages were either not downloaded or not installed, and I can only guess that they should have come from the affected repository.[/quote] 
Unlike your situation, I was able to successfully launch X with no problems. In fact, I am entering all messages in the forum, from my 5.10 system. But, like all things, there are differences in systems, which cause minor problems/headaches (and some not so minor, for some users) .

So far the only problem I see is the error message. But, I must temper that with the statement that, as of yet I have not launched, or used every piece of software available on the new OS. I am sure I will find other items that will give me (some) fits.

Anyone have any suggestion(s) on what the cause of the problem might be, and what steps/procedures we can try to rectify this error? 
Or, is this a case of a self-inflicted user error that can be overlooked/forgotten because the system is already upgraded, and the error is really telling us the system already updated to the final release?

Just for the record, this was a clean install of Breezy Colony 5-RC, (about 45 days ago). After initial install, I conducted daily upgrades, and periodic dist-upgrades.

---

### Post by moopere on 2005-10-16
[QUOTE=Vytas]Strange... I got this too today.

Btw the message is exactly the same.

W: GPG error: [http://lt.archive.ubuntu.com](http://lt.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/QUOTE]


See this thread for a workaround:

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599](http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599)

---

### Post by azteech on 2005-10-16
[quote=moopere]See this thread for a workaround:

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599]("http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599")[/quote]

I was able to successfully clear the error doing the following, as recommended in another thread.

System > Administration > Synaptic Package Manager
 Settings > Repositories > Authentication > Restore default keys
 
 And then do an "apt-get update" again.

---

### Post by fifi on 2005-10-18
I had the same problem as described above. After several apt-get updates the same GPG Warning appeared. Finally I tried simply
1) cp /etc/apt/source.list /etc/apt/source.list.backup
2) comment out every item in the /etc/apt/sources.list file,
3) run apt-get update
4) mv /etc/apt/source.list.backup /etc/apt/source.list

And the problem disappeared.

---

### Post by mhael on 2005-10-18
[QUOTE=azteech]When I went to do a dist-upgrade (after doing update) from breezy (5.10-RC, Colony 5) to Breezy (5.10 Final), received the following warning message:

W: GPG error: [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any idea why I would get this, and how do I correct the issue?[/QUOTE]

Edit /etc/apt/sources.list and find this lines:
```

## Major bug fix updates produced after the final release of the                                    
## distribution.                                                                                    
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted                                 
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

```(URL may contain any two-letter country code instead of "us" - depends of your choice of location at install time)

Remove this country prefix:
```

## Major bug fix updates produced after the final release of the                                    
## distribution.                                                                                    
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted                                 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

```
Save file, then open Synaptic and press "Reload" - it must give no errors this time. Press "Mark all Upgrades", then "Apply". Voila!

---

### Post by linuxa on 2005-10-22
Thanks for the input guys, I was somewhat worried about the error message :confused: 

[QUOTE=fifi]I had the same problem as described above. After several apt-get updates the same GPG Warning appeared. Finally I tried simply
1) cp /etc/apt/source.list /etc/apt/source.list.backup
2) comment out every item in the /etc/apt/sources.list file,
3) run apt-get update
4) mv /etc/apt/source.list.backup /etc/apt/source.list

And the problem disappeared.[/QUOTE]

However, If you were to run "apt-get update" after (4), you'll still get the same problem. Also, the modules available to you after you updating in (3) will be nil. In other words, you've basically disabled yourself from reaching any of your sources.

**mheal**: I tried your solution. Unfortunately, it worked the first time round. I think it pretty much comes down to server load. I went with the work-round  provided in the link - ignoring authentication. Guess it'll have to do till the server load is back to normal :D

---

### Post by iltofa on 2005-11-09
I've tried changing the mirror server in repositories list from

*[http://lc.archive.ubuntu.com/ubuntu](http://lc.archive.ubuntu.com/ubuntu)*

to

*[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)*

where *lc* is the localization prefix.

The error has disappared :)

---

### Post by Stabicron on 2005-11-09
[QUOTE=iltofa]I've tried changing the mirror server in repositories list from

*[http://lc.archive.ubuntu.com/ubuntu](http://lc.archive.ubuntu.com/ubuntu)*

to

*[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)*

where *lc* is the localization prefix.

The error has disappared :)[/QUOTE]

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

No it hasn't :P wonder if this is some sort of bug?

---

### Post by Cyborganism on 2005-11-09
Here's the solution:

First off, go to the /etc/apt directory.
Then copy the sources.list file to sources.list.mybackup to backup your copy of repositories.
Now delete your sources.list and then create a new file with the same name.
Update apt
Now restore your backup by overwriting sources.list with sources.list.mybackup
Finally, re-update apt.

Here's how:

As root type the following commands in a command line:

```

$ cd /etc/apt
$ mv sources.list sources.list.mybackup
$ touch sources.list
$ apt-get update
$ cp sources.list.mybackup sources.list
Overwrite file 'sources.list' ? (y)es (n)o: y
$ apt-get update

```

This empties the trusted keys list to finally replace them with the new ones. You will not have any problem with GPG keys again, but its still unsage because we don't know who the new GPG keys belong to or if they had been changed by an authorized person or not.

So you may do this at your own risk.

---

### Post by iltofa on 2005-11-09
[QUOTE=Stabicron]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

No it hasn't :P wonder if this is some sort of bug?[/QUOTE]

My opersonal opinion is that is a mirror/server/connection issue. 
Ignore the error at the moment and then retry again in few days....

Somebody out there has an idea? :confused:

---

### Post by markthecarp on 2005-11-09
[QUOTE=mhael]Edit /etc/apt/sources.list and find this lines:
```

## Major bug fix updates produced after the final release of the                                    
## distribution.                                                                                    
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted                                 
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

```(URL may contain any two-letter country code instead of "us" - depends of your choice of location at install time)

Remove this country prefix:
```

## Major bug fix updates produced after the final release of the                                    
## distribution.                                                                                    
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted                                 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

```
Save file, then open Synaptic and press "Reload" - it must give no errors this time. Press "Mark all Upgrades", then "Apply". Voila![/QUOTE]

The above worked for me. But raises the question of what about the other repositories listed by country code? Should the country code be dropped from these as well? Also can universe and multiverse be added to "breezy-updates"?

On my system removing the country code, apt-get update, apt-get -dist-upgrade -u dropped three nautilus related packages.

-mark

---

### Post by Topsiho on 2005-11-10
By deleting the localization prefix like us, lc, nl and so on, the main server will be flooded more and more from over all this lovely world of ours. So even if this works I don't think we should adopt this procedure.

Probably we have to wait until the local mirrors are working again as they should.

My two pennies ... :)

Topsiho

---

### Post by lethargo on 2005-11-10
Thank you Cyboranism (and others).  I followed your instructions from post [12]("http://ubuntuforums.org/showpost.php?p=479026&postcount=12"), and it worked great.

One glitch I had was that it didn't like the CDROM in my sources.list after that...
```
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - 
Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  
Please use apt-cdrom to make this CD-ROM recognized by APT. 
apt-get update cannot be used to add new CD-ROMs
```

In case anyone else runs into that, sticking the CD-ROM in the drive and typing the following seemed to resolve it.
```
apt-cdrom add
```

After that I took the CD-ROM out, and apt-get update worked great.

---

### Post by PerfMonk on 2005-11-10
Thanks,

It did work for me too.  I had a few source that where prefixed with "ca.".  I took it off and it did the job. 

I wonder why the other sites don't add their GPG key ?   Someone please correct this!  I don't know how, at first, my official source changed to the Canadian mirrors.  I'm still a newbie at apt-get but I'm starting to like it.  It's a lot more stable and efficient than 'URPMI' from Mandriva wich was my old distro in a distant past life...

   Regards,
              BT

---

