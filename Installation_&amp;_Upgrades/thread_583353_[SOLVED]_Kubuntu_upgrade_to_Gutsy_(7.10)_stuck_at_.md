---
title: "[SOLVED] Kubuntu upgrade to Gutsy (7.10) stuck at 99%"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Linux_noob1 on 2007-10-20
Hello. I have been trying to upgrade my Kubuntu Feisty to Kubuntu Gutsy. To do this, I followed _[COLOR="Blue"][these]("http://kubuntu.org/announcements/7.10-release.php#upgrade") [/COLOR]_instructions to try and upgrade.

(click the links to view an image of what I'm talking about)

When following these instructions, it told me to go into Adept (Package manager) and do things like "Fetch Updates" and "Full Upgrade". However, when I do these things, _[COLOR="Blue"][it seems to get stuck at 99% some of the time.]("http://i211.photobucket.com/albums/bb153/woodland_photographer/IMG_0567.jpg?t=1192895707")[/COLOR]_ Although, After I did things like restarting, I managed to get it to work and go to 100% (It's like most of the time it gets stuck and 99%, and sometimes gets to 100% if I'm lucky.) But... After clicking the "Version Upgrade", it does some stuff, and then I click Finish and it closes Adept. Then it opens the upgrade utility and does the first step, "Preparing the Update", _[COLOR="Blue"][but and then gets stuck at 99%.]("http://i211.photobucket.com/albums/bb153/woodland_photographer/IMG_0566.jpg?t=1192895670")[/COLOR]_ I have tried leaving it for a long time, have tried restarting, and have tried it multiple times. It never gets passed 99% on the "Preparing the Update" step. (Also, after I clicked cancel, it's started to do weird things; such as after rebooting it asked me for my password, and also when typing this topic the  version upgrade window randomly popped up and got stuck at 99% again)

I am not sure how to fix this, and I really want to upgrade to Gutsy.
Thanks for any help.

---

### Post by Linux_noob1 on 2007-10-20
Could it just be that the servers are down due to all the people who are upgrading?

---

### Post by Linux_noob1 on 2007-10-23
I waited a few days to see if it was a server related issue. I am still getting the same problems on that one PC.

A slower PC I have that also has Kubuntu 7.04 installed is currently doing the update to gusty without any problems.

This must be an issue with my other computer. Any ideas? Please help! :'(

---

### Post by Linux_noob1 on 2007-10-23
Sorry for the quadruple post, but I got some more info on the problem. After doing another Full Upgrade, it managed to get past 99%. But... now it just gives me an error message.

[I]Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found[/I]

Here's a screenshot of what I got.
[[IMG]http://img512.imageshack.us/img512/2931/upgradeerrorcv5.th.png[/IMG]](http://img512.imageshack.us/img512/2931/upgradeerrorcv5.png)


I've tried doing the update twice and keep getting this same error!
Please help me!!
:confused::confused::confused:

---

### Post by AMDBuntu on 2007-10-23
Have you tried using another mirror (set within software sources)? I had a problem like that once and set the system to download from another mirror and all went well. I like the Utah mirror as it seems to go really fast and is always complete.

That said, I wonder why Medibuntu is giving you problems while upgrading?

---

### Post by Linux_noob1 on 2007-10-23
Thanks for replying!

I have another computer doing the gutsy upgrade and it's working just fine, it's being download from the same mirror...

I tried the Utah mirror like you said, but it just gets stuck at 99% again.

EDIT: I tried changing it back to the main server, and then I get that same error posted above. I'm gonna try another mirror.

---

### Post by Pete Kingston on 2007-10-23
Using the update manager, and clicking on the upgrade button next to "new distribution release '7.10' is available" text, the upgrade stops and gives me this message:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

How do you change to the Utah mirror?

---

### Post by Pete Kingston on 2007-10-24
I got it to upgrade. 

You also need to disable offending source in System, Administration, Software Sources, Third-Party Software tab, un-check the items that are stopping your upgrade, and then try again.

---

### Post by Linux_noob1 on 2007-11-22
> Using the update manager, and clicking on the upgrade button next to "new distribution release '7.10' is available" text, the upgrade stops and gives me this message:

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found

How do you change to the Utah mirror?



I booted into GNOME and tried an update through it.

I got a simmilar error message checking for updates with the update manager:

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 404 Not Found

 	
> Re: Kubuntu upgrade to Gutsy (7.10) stuck at 99%
I got it to upgrade.

You also need to disable offending source in System, Administration, Software Sources, Third-Party Software tab, un-check the items that are stopping your upgrade, and then try again.

So I need to disable the mediabuntu repository entirely? I thought it needs this? 

Could it be that I accidentally messed something up when I had messed with the software sources? Any ideas?


Very sorry for bumping a month old thread, I am just a little confused on how to fix this.

---

### Post by ajm2005 on 2007-12-02
I had the same problem as you (stuck at 99%). I found the method described by integr8e in this thread allowed me to upgrade my kubuntu installation from 7.04 to 7.10:

[http://kubuntuforums.net/forums/index.php?topic=3089239.0](http://kubuntuforums.net/forums/index.php?topic=3089239.0)

---

### Post by Linux_noob1 on 2007-12-16
> I had the same problem as you (stuck at 99%). I found the method described by integr8e in this thread allowed me to upgrade my kubuntu installation from 7.04 to 7.10:

[http://kubuntuforums.net/forums/inde...opic=3089239.0](http://kubuntuforums.net/forums/inde...opic=3089239.0)

Thanks, I made a new list  with the list generator and I can fetch updates without an error now. 

Only problem is I need to add the mediabuntu third party repository lists. I tried checking it in adept and the window would just crash. I tried the ubuntu-software sources list and I got this error.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 404 Not Found


What do I do now? Im thinking that I need to add something by hand.
    I am not worried about messing something up since I have a backup of my original broken list.
  If possible, could another feisty user post there list?

Thanks and sorry if this thread is kinda old.

---

### Post by Linux_noob1 on 2007-12-16
I thought I might paste the lists here.


Original list:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-security universe



deb http://archive.canonical.com/ubuntu feisty-commercial main
## Beryl repository
deb http://ubuntu.beryl-project.org feisty main
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates restricted main universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty-proposed restricted main universe
```




New list that was made with the list maker. (This fixed an issue I was having with fetching updates.)




```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```


I just don't know what I need to do to get my Mediabuntu lists in.  Do I need to first uncheck mediabuntu in my package manager before adding anything? 


Also what looked wrong with my original list? Maybe I could just repair it?


Could I just stick in a Kubuntu CD and use that 'rescue broken system?' feature I saw on it? Would that take care of my problem?

---

### Post by Partyboi2 on 2007-12-17
[quote]> **Linux_noob1 said:**
> Thanks, I made a new list  with the list generator and I can fetch updates without an error now. 

Only problem is I need to add the mediabuntu third party repository lists. I tried checking it in adept and the window would just crash. I tried the ubuntu-software sources list and I got this error.
Are you trying to upgrade still? Or are you now trying to sort out a apt problem?
if you are trying to upgrade still to Gusty you need to make sure that all 3rd party (mediubuntu) repo's are commented out in your source.list. (or by unticking boxes in your Software Sources, I am not sure how you get to it under kubuntu) once this is done you can run the upgrade again and it should work.
If you have already upgraded to Gusty make sure that your source.list is for Gusty not Feisty.

---

### Post by Linux_noob1 on 2007-12-17
> Are you trying to upgrade still? Or are you now trying to sort out a apt problem?
if you are trying to upgrade still to Gusty you need to make sure that all 3rd party (mediubuntu) repo's are commented out in your source.list. (or by unticking boxes in your Software Sources, I am not sure how you get to it under kubuntu) once this is done you can run the upgrade again and it should work.
If you have already upgraded to Gusty make sure that your source.list is for Gusty not Feisty.

Well I am planning too upgrade/install gutsy sometime. I first just want to get the list fully fixed though.

I can't turn on mediubuntu, when i try to do it the adept window just crashes. I found a new list and tried it:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
 
It still wont let me check  mediubuntu under the third party tab. Anyways I think ubuntu removes the slash in the repository list to turn on repositories right? ```
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
``` 

[[IMG]http://img107.imageshack.us/img107/2792/adeptmanagerji7.th.png[/IMG]](http://img107.imageshack.us/my.php?image=adeptmanagerji7.png)
( ^ the manage repositories window under third party tab will just crash when I try to enable lists there)

---

### Post by Partyboi2 on 2007-12-17
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

[COLOR=Red] #[/COLOR] deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
[COLOR=Red] #[/COLOR] deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```You need to remove the [COLOR=Red]# [COLOR=Black]from in front for it to work.
After you have saved the changed you will need to update
[/COLOR][/COLOR]```
sudo apt-get update
```[COLOR=Blue][B]But
[/B][COLOR=Black]when it comes time for you to upgrade to Gusty you will probably need to put the [COLOR=Red]# [COLOR=Black]back in front of it as well as putting a  [COLOR=Red]#   [COLOR=Black]in front of [/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main, for it to be able to complete the upgrade.
So to use mediubuntu it should look like this in your sources.list
```

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```When time to upgrade to Gusty it should be something like this:
```

# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb http://archive.canonical.com/ubuntu feisty-commercial main
```

---

### Post by Linux_noob1 on 2007-12-18
> You need to remove the # from in front for it to work.
After you have saved the changed you will need to update
Code:

sudo apt-get update

But
when it comes time for you to upgrade to Gusty you will probably need to put the # back in front of it as well as putting a # in front of deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main, for it to be able to complete the upgrade.
So to use mediubuntu it should look like this in your sources.list
Code:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

When time to upgrade to Gusty it should be something like this:
Code:

# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main




I removed the # on the medibuntu so it looked like this:
```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Then I saved the file.

After that I did sudo apt-get update in the terminal. I got back this:

```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz  404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas?

---

### Post by Partyboi2 on 2007-12-18
open up Software Sources and remove:
```
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free (Source Code)
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free (Source Code)
```Close Software Sources and open up a terminal
in the ternimal type:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```All going well that should do it. :)

---

### Post by Linux_noob1 on 2007-12-20
> Re: Kubuntu upgrade to Gutsy (7.10) stuck at 99%
open up Software Sources and remove:
Code:

  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free (Source Code)
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
  [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free (Source Code)

Close Software Sources and open up a terminal
in the ternimal type:
Code:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

then
Code:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

All going well that should do it. 


It looks like it fixed the problem. I still haven't upgraded yet but I am pretty sure it will work.
 All my other updating problems are gone. Thanks so much!

 Should mark this thread "solved"?

---

### Post by Partyboi2 on 2007-12-20
Hope the upgrade goes well when you do it. :)
Yeah, mark as Solved.

---

