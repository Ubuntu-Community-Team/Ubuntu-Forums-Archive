---
title: "Upgrading from dapper to edgy"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by super newbie on 2007-04-28
Hi all
When I try to upgrade my dapper to edgy, I get the following error message....
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

I found out this is has to do with the "Listen Music Player"
The question is....how do I stop the upgrade from looking for this file?  Also I have a copy of the new Feisty 7.04 but if install that, I assume it will write over everything and I'll lose all my data.  Any help would be great.  Also I don't know much about the command line so if you could explain the solution in the simplest way possible....thanks everyone.

---

### Post by craigsn on 2007-04-30
I don't have an answer, but I have an upgrade issue along the same line, dapper to edgy, amd64, I get this error "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)". And then it stops. I've tried it a couple of times over 1/2 period in case it was an overcrowded server. 

Any help would be appreciated.

Thanks
Craig

---

### Post by randell6564 on 2007-04-30
> **super newbie said:**
> Hi all
When I try to upgrade my dapper to edgy, I get the following error message....
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

I found out this is has to do with the "Listen Music Player"
The question is....how do I stop the upgrade from looking for this file?  Also I have a copy of the new Feisty 7.04 but if install that, I assume it will write over everything and I'll lose all my data.  Any help would be great.  Also I don't know much about the command line so if you could explain the solution in the simplest way possible....thanks everyone.
Post your /etc/apt/sources.list.  In other words, copy and post it here so that I can get a looksy!

---

### Post by randell6564 on 2007-04-30
> **craigsn said:**
> I don't have an answer, but I have an upgrade issue along the same line, dapper to edgy, amd64, I get this error "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)". And then it stops. I've tried it a couple of times over 1/2 period in case it was an overcrowded server. 

Any help would be appreciated.

Thanks
Craig
Post YOUR /etc/apt/sources.list

---

### Post by craigsn on 2007-04-30
Here is my /etc/apt/sources.list


# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by randell6564 on 2007-04-30
> **craigsn said:**
> Here is my /etc/apt/sources.list


# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper **main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper**-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper**-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **dapper **universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper** universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper**-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) **dapper**-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **dapper**-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **dapper**-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **dapper**-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) **dapper**-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) **dapper** main

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) **dapper** misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **dapper**-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **dapper**-security main restricted universe multiverse
#AUTOMATIX REPOS END
Well my friend, you need to change ALL instances of "dapper" to "edgy".  THEN do:
```
sudo update-manager -c
```

---

### Post by craigsn on 2007-04-30
Hi randell6564, thanks for the prompt response, but that did not fix the problem. The same message still appears as originally. I used gedit and did a search/replace on dapper to edgy, and no joy.

Anything else to try?

Craig

---

### Post by randell6564 on 2007-04-30
>  I used gedit and did a search/replace on dapper to edgy, and no joy.
What do you mean here?
Are you sure that you replaced the word "dapper" with the word "edgy" in your /etc/apt/sources.list?
Before doing
```
sudo update-manager -c
```
Try doing
```
sudo apt-get update
```
THEN check update-manager.

---

### Post by craigsn on 2007-04-30
Yup, I checked to make sure dapper was replaced with edgy in all instances. I can copy /etc/apt/sources.list again, but am pretty sure it worked fine. And as I said, still got the same response. 

You suggested to run sudo apt-get update, which I did, and I got the same error message here as before "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)"

So something strange it happening here. 

Thanks for your patience on this.

---

### Post by randell6564 on 2007-04-30
> **craigsn said:**
> Yup, I checked to make sure dapper was replaced with edgy in all instances. I can copy /etc/apt/sources.list again, but am pretty sure it worked fine. And as I said, still got the same response. 

You suggested to run sudo apt-get update, which I did, and I got the same error message here as before "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)"

So something strange it happening here. 

Thanks for your patience on this.
Can you describe your system to me please?  allow me some time to research, and I'll get back to you k?

---

### Post by craigsn on 2007-04-30
Sure it is an HP a1250n with an athlon 64 bit dual core processor with 2gb of ram. I dual boot to windows xp using grub, and I'm running 64 bit dapper on my machine. I'm trying to upgrade to edgy then to feisty rather than load feisty directly in order not to lose "things". Is there anything more specific you would like me to include? I'll be happy to comply.

Thanks again

---

### Post by randell6564 on 2007-04-30
I have a feeling that this has something to do with the server that your system is trying to retrieve the packages from.
Make a backup copy of your sources.list , then do:
```
sudo gedit  /etc/apt/sources.list
```
find all the entries, [au] and replace them with [us].  This will retrieve packages from the U.S. repositories.
> # Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src [http://**au](http://**au)**.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by craigsn on 2007-05-01
Ah randell6564, this is frustrating :). I made the changes you suggested to the sources.list file (change au to us) and then ran sudo apt-get update and got the same error message "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)", 

then tried the sudo update-manager -c. I then started the upgrade process and it failed in the same place with the same message "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)".

So something hideous is going on.

Craig

---

### Post by randell6564 on 2007-05-02
> **craigsn said:**
> Ah randell6564, this is frustrating :). I made the changes you suggested to the sources.list file (change au to us) and then ran sudo apt-get update and got the same error message "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)", 

then tried the sudo update-manager -c. I then started the upgrade process and it failed in the same place with the same message "Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)".

So something hideous is going on.

Craig
MAN dude!  I just don't know what to say!  I refered you to 'aysiu'.  He has helped me many times in the past. I private messaged him yesterday, but apparently you have not heard from him yet.

I'm still looking into this my friend!  Sorry about the wait.,just got home from work.

---

### Post by craigsn on 2007-05-02
Very much appreciate all of your help on this issue, even if it hasn't been fruitful yet. I'll wait for 'aysiu' to drop me a note. If you think of another thing to try, let me know.

Craig

---

### Post by randell6564 on 2007-05-02
> **craigsn said:**
> Very much appreciate all of your help on this issue, even if it hasn't been fruitful yet. I'll wait for 'aysiu' to drop me a note. If you think of another thing to try, let me know.

Craig
I just got home from work.  I'm looking into this right now my friend.  It's got ME bothered now! (lol!)  We are going to get this fixed!!:)

---

### Post by randell6564 on 2007-05-02
OK.,LETS try THIS!
You already have a backup copy of your sources.list, so edit the one in use:
```
sudo gedit /etc/apt/sources.list
```
Remove everything and copy mine.  Here it is:
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://getswiftfox.com/builds/debian/branch](http://getswiftfox.com/builds/debian/branch) unstable non-free
## Medibuntu - Ubuntu 6.10 “edgy eft”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free
NOW do:
```
sudo apt-get update
```
THEN do:
```
sudo update-manager -c
```
NOW PRAY! :)

---

### Post by craigsn on 2007-05-03
No joy on this either. I replaced the sources.list file with the one you suggested and got a bunch of errors, mostly dealing with getswiftfox stuff. I'll be happy to post the results of the apt-get update command if you wish. But I still get the same original error message as well, the "Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1"

any more suggestions would be appreciated, but I may just bite the bullet, clear the hd and load feisty if we can't figure this out soon.

Thanks

---

### Post by randell6564 on 2007-05-03
> **craigsn said:**
> No joy on this either. I replaced the sources.list file with the one you suggested and got a bunch of errors, mostly dealing with getswiftfox stuff. I'll be happy to post the results of the apt-get update command if you wish. But I still get the same original error message as well, the "Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1"

any more suggestions would be appreciated, but I may just bite the bullet, clear the hd and load feisty if we can't figure this out soon.

Thanks
Damn,damn,DAMN! :(  You can just delete the "swiftfox" archives, but it sounds like that will not matter anyway.
This is CRAZY!  I have researched over and over, posted threads about your problem and no one seems to know anything about it!
At this point, I would wipe my drive and reinstall if it were me. (I never keep anything too important on my computers, so it's no big deal to me to install and reinstall )

My computer is 32bit OR 64bit capable.  I have the official Ubuntu Dapper Drake 32bit CD AND the 64bit CD.  I never liked how the 64bit version acted on my box, so I always ran the 32bit and never had problems. I'm guessing that this whole problem has something to do with 64bit because the original error that you're getting refers to "...-amd64/packages.gz".
Can you run the 32bit version on your box?  I know that this would mean a possible loss of performance, but I read somewhere that there is really no noticible difference between 32 and 64bit versions of Ubuntu anyway.
The only thing that I could find related to this problem explains it as a server issue.  Thats why I had you change from "au" to "us".

Please let me know what the end results are.  Good Luck!:)

---

### Post by randell6564 on 2007-05-03
Just a thought!
Could you open your software sources application, take a screenshot and post it here so that I can have a looksy?

---

### Post by craigsn on 2007-05-04
> randell6564  	Just a thought!
Could you open your software sources application, take a screenshot and post it here so that I can have a looksy?

Randell, sorry to be a pain, but what specifically do you mean by software sources application? Is it the Software Properties under the System/Administration menu (in Dapper anyway), or Synaptic or Update Manager. 

I'll be happy to do that for you as soon as I know which one it is.

I also saw you note about possibly just biting the bullet and loading on the new software with a clean install. And I may do that. If we don't solve it shortly, then that is the way I'll go. I'll probably stay 64bit just because the "world" needs to get there someday and I might as well be there now because I can. I do not use this maching for production I use Windows for that, but I use it daily and am trying to see if/when I can move to Linux permanently. 

Thanks again

Craig

---

### Post by randell6564 on 2007-05-05
> Randell, sorry to be a pain, but what specifically do you mean by software sources application? Is it the Software Properties under the System/Administration menu (in Dapper anyway), or Synaptic or Update Manager.
Well.,I just can't remember.  It's been a while since I've used Dapper Drake, but it IS under System>Administration...  It is a Gui Application that you can go to in order to add/remove software sources.  
After you installed Dapper, did you edit your /etc/apt/sources.list in any way before attempting to upgrade? 

> I also saw you note about possibly just biting the bullet and loading on the new software with a clean install. And I may do that. If we don't solve it shortly, then that is the way I'll go. I'll probably stay 64bit just because the "world" needs to get there someday and I might as well be there now because I can. I do not use this maching for production I use Windows for that, but I use it daily and am trying to see if/when I can move to Linux permanently.
Damn, I wish I had my other box!  It's in storage now, but I use to use it for testing distro's.  I never had any problems with the 64bit version of Ubuntu Dapper other than, I didn't notice any difference between the two. 
Well.,if it's not your production machine then go for it!  Load Feisty on a clean disk.  BUT., I for one, am going to keep searching for answers!:)  I'm fired up now!!:lolflag:

---

### Post by craigsn on 2007-05-05
> BUT., I for one, am going to keep searching for answers! I'm fired up now!!

In that case, I'll hold off on installing feisty to see if we can figure this out together. As I said I don't use it for production so we can "Play" 

> Well.,I just can't remember. It's been a while since I've used Dapper Drake, but it IS under System>Administration... It is a Gui Application that you can go to in order to add/remove software sources. 


That is the Software Properties then. But isn't that just a GUI into the sources. list file? Seems like it. 

> After you installed Dapper, did you edit your /etc/apt/sources.list in any way before attempting to upgrade? 

Nope, it was just the generic one that I had installed, and when I added things thru the GUI.

Craig

---

### Post by prince_of_hackers on 2007-05-05
Hey guys, having a similar problem to the one you are describing here - same error, trying to run apt-get update and apt-get upgrade, however, this is running on SPARC hardware. Brand new, clean install of dapper, everything is running smoothly other than internet updates. No problems using apt-get or aptitude to install software from the original CD, just from internet sources. I notice one similarity in our problems, however, and that is that both installations having update problems are NOT 32-bit intel. Perhaps this is related to the cause of the problem.

---

### Post by randell6564 on 2007-05-05
> I notice one similarity in our problems, however, and that is that both installations having update problems are NOT 32-bit intel. Perhaps this is related to the cause of the problem.
Yeah, I was thinking along those lines as well.  something to do with upgrading 64bit via internet.  When I was running dapper 64bit, I had no problems updating.  But MY board is intel.
Don't know.,I'm still trying to google this issue, but I keep coming up with the same thing.,'archive server problems'.  There seems to be no other reason for this problem as far as google is concerned!

---

### Post by randell6564 on 2007-05-05
'craigsn' and 'prince of hackers'.  [Check out this thread!]("http://ubuntuforums.org/showthread.php?t=369001")  It might just be your solution!

---

### Post by prince_of_hackers on 2007-05-07
Checked out that thread on my lunch hour, tried updating with the sources.list file commented out, of course that worked fine. Tried uncommenting just one entry, but no good, same error messages. I then tried the idea of switching the URI to ftp instead of http, it seemed to work just fine then, but I haven't tried it on anything but the first repository. I'll try more later and post the results, thanks for that link randell.

---

### Post by randell6564 on 2007-05-07
> I then tried the idea of switching the URL to ftp instead of http, it seemed to work just fine then...
THATS what I was getting at!  If it worked on one, then it should work on the others.  If it doesn't, I would THEN make sure that I had the generic sources.list and try again.
Cheers!

---

### Post by craigsn on 2007-05-12
Randall, I tried changing my http:// to ftp:// but it didn't work. Sorry to bring you this news, as I was hopeful of a resolution after reading it. 

Not sure what is next. do you, or anyone have a "generic" sources.list for me to load and try?

---

### Post by randell6564 on 2007-05-12
> **craigsn said:**
> Randall, I tried changing my http:// to ftp:// but it didn't work. Sorry to bring you this news, as I was hopeful of a resolution after reading it. 

Not sure what is next. do you, or anyone have a "generic" sources.list for me to load and try?
Hey craigsn!
Sorry that you're still having this problem.  You should have the "generic sources.list" after removing the automatix repo's as long as you didn't edit it any other way.

---

### Post by craigsn on 2007-05-14
Good news Randall,
I reloaded my original sources.list, ran the apt-get update, apt-get upgrade & then update-manager -c and it all worked fine. So now I'm on Edgy. 

I wish to thank you for your patience and help in this.

Craig

---

### Post by prince_of_hackers on 2007-05-14
> **craigsn said:**
> Randall, I tried changing my http:// to ftp:// but it didn't work. Sorry to bring you this news, as I was hopeful of a resolution after reading it. 

Not sure what is next. do you, or anyone have a "generic" sources.list for me to load and try?

I have attached a copy of my original sources.list file, as existed on a brand new clean install of Dapper. However, as I indicated in my previous post, this file did not work for me until I switched all of the http://'s to [ftp://.](ftp://.)

If you would, try backing up your original sources.list, then replace it with this one. If you still cannot upgrade, try this: Comment out ALL but the first repository line in the sources.list file, then go to a shell and run 'apt-get update', and copy and paste the ENTIRE output and post it here, so perhaps we can narrow down your problem. You might also try switching the first line from http to ftp and post the output of that, if it is any different.

sources.list
____________________________________________________________
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by randell6564 on 2007-05-14
> **craigsn said:**
> Good news Randall,
I reloaded my original sources.list, ran the apt-get update, apt-get upgrade & then update-manager -c and it all worked fine. So now I'm on Edgy. 

I wish to thank you for your patience and help in this.

Craig
Well ALRIGHT!  Thats great my friend!  Have fun!

---

