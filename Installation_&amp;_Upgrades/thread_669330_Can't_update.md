---
title: "Can't update"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by LPA on 2008-01-16
I've looked at the other posts, but they don't help...
When I try to update 7.10, it starts to update, and gets to file 7 of 28 - and then gets stuck! (see attached picture update 01.png).
When I cancel the failed update, I get an error message:
Could not download all respository indexes
The repository might be no longer available, or could not be connected (see attached picture update 02.png).
This is the situation since I installed 7.10 over one month ago. Please help!
many thanks, and please reply also to:
[email]richard@LPAgroup.biz[/email]
MTIA

Richard:(

---

### Post by LPA on 2008-01-16
sorry -here are the two pictures

---

### Post by erginemr on 2008-01-16
Hello,

Please make sure to upload the attachments...

---

### Post by erginemr on 2008-01-16
Could you please make sure that the corresponding parts of synaptic are similar to the ones I have attached?

---

### Post by LPA on 2008-01-17
Thanks, but it didn't help ...
I changed all the check-boxes to be exactly like the ones in the pictures you sent, and I got two different error messages - attached here (03 & 04). It seems to be getting worse (??)

TiA

Richard

---

### Post by steelklvr on 2008-01-17
If you have a D-Link router, there could be a DNS issue stopping you from updating, i had this problem a while back and found that i had to edit the resolv.conf file to correct it.

Here's a link to my post regarding the fix.

[http://ubuntuforums.org/showthread.php?t=587225&page=2](http://ubuntuforums.org/showthread.php?t=587225&page=2)

---

### Post by LPA on 2008-01-17
Thanks. I don't have a D-link router - I have an ECI B-Focus Wireless 352, but the Ubuntubox is connected to the router by a cable - not through wireless.
I think you are on the right track, and I will try to do what it says there, but I have ZERO experience with actual Linux command-line work. 
Note: I had a problem with getting Ubuntu to allow multi language work and found out that if you open a browser, and type "about:config" , and then look for the line that says
          network.dns.disableIPv6 
and right-click to change the value to TRUE, everything then works fine. (But the update problem existed before I changed this, so it is not connected ...)
Maybe there is some similar line that needs to be changed?

Thanks again!
Richard

---

### Post by LPA on 2008-01-17
Whoops - correction - 
THe problem was not the multilanguage issue (that was another problem but I solved it), but rather I could not connect at all to the internet! Now I can, after the toggle, but I still can't update.

FRUSTRATED!

---

### Post by Partyboi2 on 2008-01-17
try changing the server under software sources to a different one. If that does not work
can you post your source.list
Open a terminal (Applications>Accessories>Terminal)
```
 cat /etc/apt/sources.list
```

---

### Post by LPA on 2008-01-17
worse and worse:
Changed server from "main" to USA, and no downloads at all - gets stuck on #1
and the command doesn't work either ..
cat: /etc/apt/source.list: No such file or directory ! ! ! !! !

arrrgggg

---

### Post by zipperback on 2008-01-17
> **LPA said:**
> Whoops - correction - 
THe problem was not the multilanguage issue (that was another problem but I solved it), but rather I could not connect at all to the internet! Now I can, after the toggle, but I still can't update.

FRUSTRATED!


See if it will update manually.


```


sudo apt-get update


```

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-17
Could you please provide a copy of your sources list

Your sources list is located in:

> 
/etc/apt/sources.list


Thank you

-zipperback
:popcorn:

---

### Post by comee on 2008-01-17
the same goes with the console
[INDENT]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages [5199B]
99% [5 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 4s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]
It seems that .packages.gz on the server is corrupted or some thing has bitten it into pieces.

--/PW

---

### Post by Joeb454 on 2008-01-17
did you say that when trying to run ```
cat /etc/apt/sources.list
``` from the terminal, you got "No such file or directory" ???

---

### Post by Partyboi2 on 2008-01-17
> **LPA said:**
> worse and worse:
Changed server from "main" to USA, and no downloads at all - gets stuck on #1
and the command doesn't work either ..
cat: /etc/apt/source.list: No such file or directory ! ! ! !! !

arrrgggg
cat /etc/apt/sources.list is with a s on the end of source
>  Err [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") edgy-updates/restricted PackagesIf you are running 7.10 (gusty) you should not have any edgy repo's
in your sources.list as this can cause breakages.
If you are not sure what to edit in /etc/apt/sources.list then post the contents of that file 
as well as the output to this command
```
lsb_release -a
```
and someone will be able to help you.

---

### Post by LPA on 2008-01-17
one more bit of information - please see attached screen shot. In the browser, doing about:config, I got the following list of update information. Many of the lines are LOCKED, so I can't even try toggling them.
Hope this helps ...
Tia
Richard

---

### Post by erginemr on 2008-01-17
I believe your problem has nothing to do with Firefox.

It is crucial that you should post the output of
```
cat /etc/apt/sources.list
```
here to have some progress for the solution. Please focus on this.

---

### Post by LPA on 2008-01-17
a) Attached is a file with the sources list. 
b) I also tried doing:
sudo dpkg --configure -a
and then
sudo apt-get update.

Absolutely nothing happens - it just sits there, trying and getting nowhere - 0% download.

MTIA

richard

---

### Post by Partyboi2 on 2008-01-17
> **LPA said:**
> a) Attached is a file with the sources list. 
b) I also tried doing:
sudo dpkg --configure -a
and then
sudo apt-get update.

Absolutely nothing happens - it just sits there, trying and getting nowhere - 0% download.

MTIA

richard
There is no attachment, please try again, or just copy and paste the output of 
cat etc/apt/sources.list into a post.

---

### Post by LPA on 2008-01-18
attached the file twice, but to no avail. Here is the list:
richard@ubuntubox:~$ cat /etc/apt/sources.list 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 
 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted 
 
## Major bug fix updates produced after the final release of the 
## distribution. 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe 
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse 
# Line commented out by installer because it failed to verify: 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse 
# Line commented out by installer because it failed to verify: 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse 
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse 
 
## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner 
 
# Line commented out by installer because it failed to verify: 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted 
# Line commented out by installer because it failed to verify: 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted 
# Line commented out by installer because it failed to verify: 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe 
# Line commented out by installer because it failed to verify: 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe 
# Line commented out by installer because it failed to verify: 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse 
# Line commented out by installer because it failed to verify: 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted #Added by software-properties 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted #Added by software-properties 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted #Added by software-properties 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse 
richard@ubuntubox:~$  
richard@ubuntubox:~$

---

### Post by Partyboi2 on 2008-01-18
I suggest trying a new source.list. I can not see any entries relating to edgy. But maybe a new source.list will fix this problem.
You can create a new one [here]("http://www.ubuntu-nl.org/source-o-matic/")
Then backup your current sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```then open up your sources.list
```
gksudo gedit /etc/apt/sources.list
```delete the contents and paste the new one in the empty text file that you generated from source-o-matic.
Save
then
```
sudo apt-get update
```

---

### Post by LPA on 2008-01-18
Thanks for the suggestions. I will try this when I have some time later in the day, hopefully I won't make a mess of it.

Have a nice weekend

Richard

---

### Post by LPA on 2008-01-18
NBG!!!
Did everything, and nothing happens. Only difference is that instead of saying "Downloading file 1 of 28" it says "Downloadiung file 1 of 15", But absolutely nothing happens!!!

There is a line in the config that says:

apt.update.enabled    locked    boolean   false
I think (???) that this should be true, but since it is locked, I can't toggle it. Do you know how to unlock it?
When I do the sudo update command, it just sits there trying to connect. There is something blocking access to the network (though I can access the internet).

R

---

### Post by Partyboi2 on 2008-01-18
>  apt.update.enabled    locked    boolean   false
I think (???) that this should be true, but since it is locked, I can't toggle it. Do you know how to unlock it?
the correct setting for firefox apt.update.enabled is
```
locked boolen false
```
Are you using a proxy? 
can you please post the results for
```
sudo apt-get update
```

---

### Post by LPA on 2008-01-18
There are no results for sudo apt-get update - it just sits there doing nothing

---

### Post by erginemr on 2008-01-18
By this time you should be pissed off by this issue, which is very annoying indeed. I hope you will solve it, soon.

Anyway, would you mind trying out your Live CD and its package downloading capabilities? So, please boot from the live CD, set up your network / internet and open up all repositories from under Synaptic and press the update button.

If you happen to be successful, then check out your /etc/apt/sources.list, the corresponding Firefox setting (about:config) and what not to see the difference. Otherwise, this might bring us to the conclusion that this is a network related problem, not your configuration.

P.S. I also have "apt.update.enabled" as "locked boolean false" and can update my system. So apparently, it has nothing to do with your problem.

---

### Post by erginemr on 2008-01-18
Not that it will help, but following the example of:
[http://wiki.freespire.org/index.php/Using_Apt](http://wiki.freespire.org/index.php/Using_Apt)

Does issuing:
sudo apt-get -f install

make any difference?

---

### Post by LPA on 2008-01-18
doesn't help - this is what I get, takes one microsecond:

richard@ubuntubox:~$ sudo apt-get -f install
[sudo] password for richard:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
richard@ubuntubox:~$ 

will try the live CD , but I am really really fed-up with this!

---

### Post by LPA on 2008-01-18
Just tried the live CD, same problem. I'm sure it is something to do with the network connection but I have no idea what, or how to find out or what to do about it!

---

### Post by Partyboi2 on 2008-01-18
If you are using a router try resetting your router to clear its DNS cache, or you could even try using different DNS server.
If you are using a proxy you will need to make sure its configured in Synaptic Package Manager.

---

### Post by LPA on 2008-01-19
I am using a router. Turned it off to clear the cache, but it didn't help. THere is something that is stopping the update application from accessing the network. 
I will speak to the phone company on Sunday, who supply the router and the network, to see if they have some firewall in place that is stopping this.

Thanks for your attempts at helping me.

Richard

---

### Post by LPA on 2008-01-19
Just had a thought 
The Windows network through which everything is connected here has a firewall, and on the firewall settings there is a tab for exceptions. On the exceptions tab, there is a button for "Add Port" - maybe something needs to be done here, but I have no idea what to do. When I click the add port button, I get two lines - "name" and port number, and a choice of TCP or UDP. 
ANy ideas???

---

### Post by Partyboi2 on 2008-01-19
Are you able to access your router settings by going to
[http://192.168.0.1](http://192.168.0.1)
If so, you should be able to change the firewall settings

---

### Post by LPA on 2008-01-20
Just accessed the router, there is no firewall on the ubuntu computer, but still no progress. 
Any suggestions on any other settings that might need to be changed?

---

### Post by erginemr on 2008-01-20
Please read the following old thread thoroughly:

[http://ubuntuforums.org/archive/index.php/t-9944.html](http://ubuntuforums.org/archive/index.php/t-9944.html)

By the end of the thread, it turned out that the culprit was the firewall of the proxy blocking the requests of Synaptic. Luckily, people therein have circumvented the proxy's block by using "ftp" in lieu of "http". 

They manually edited the "sources.list" to get that effect, but I believe you can do the same by selecting Software Resources directly from the Administration menu or from under Synaptic, use the drop-down menu to select another server, and select "ftp" as from the drop-down list below. (There is also another button yonder to automatically test and select the fastest server for your location.)

If selecting "ftp" doesn't work either, then try this:

[http://www.barregren.se/blog/sub-process-gzip-returned-error-code-1](http://www.barregren.se/blog/sub-process-gzip-returned-error-code-1)

---

### Post by LPA on 2008-01-21
YES ! ! ! SUCCESS ! ! 

The solution was to use the "find best server" - though it took two attempts. 177 downloads are now coming through, slowly but surely!  Many Many MANY THANKS for your help and patience!

All the best
richard

---

### Post by Partyboi2 on 2008-01-21
Glad you worked it out. Must be a great relief :)

---

### Post by erginemr on 2008-01-21
:guitar:
Have Fun!

---

### Post by jacklupino on 2008-01-21
after update.. what shall i do? how am i going to install the update? are the updates install automatically ??:)

right now, i am in process of downloading 177 updates.. :popcorn:

---

### Post by LPA on 2008-01-21
First of all - YES, an amazing relief. I was going out of my mind about this. 

Second, my sincere thanks to everyone in the community that gave advice - wonderful support system!

and to Jack Lupino - Just click on the update symbol on the top bar, right side and it will update everything. Note that this will take a LONG time - about 1 hour at least, depending on your line. Mine was also 177 updates!

And now, I can start using this system in earnest! Whoppee!

Rgds and thanks again

Richard

---

### Post by jacklupino on 2008-01-21
Thanks.. :guitar:

---

