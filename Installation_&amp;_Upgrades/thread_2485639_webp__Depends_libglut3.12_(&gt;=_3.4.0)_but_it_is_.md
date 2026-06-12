---
title: "webp : Depends: libglut3.12 (&gt;= 3.4.0) but it is not installable"
date: 2023-04-04
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-04-04
I've tried a number of things to meet this dependency**, webp** will not update because of it.

```
--> *apt list --upgradable -a* 

webp/focal,focal 1.3.0-0ubuntu1~20.04.sav1 amd64 [upgradable from: 1.2.4-0ubuntu1~20.04.sav0]
webp/now 1.2.4-0ubuntu1~20.04.sav0 amd64 [installed,upgradable to: 1.3.0-0ubuntu1~20.04.sav1]
webp/focal-updates,focal-security 0.6.1-2ubuntu0.20.04.1 amd64currently running
webp/focal 0.6.1-2 amd64
```
```
--> *sudo apt install webp*
[. . . ]
The following packages have unmet dependencies:
 webp : Depends: libglut3.12 (>= 3.4.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I'm on Ubuntu MATE 20.04.6 LTS, kernel 5.4.0-146-generic.

Thanks to anyone with any ideas how I can get this unmet dependency satisfied.

---

### Post by Bashing-om on 2023-04-04
watchpocket; Hey :D

Where did you obtain webp : even 22.04 has a lower version for that app?
> 
sysop@x2204mini:~$ apt list webp
Listing... Done
webp/jammy 1.2.2-2 amd64


Post back:
```

apt policy webp libglut3.12

```

Maybe a snap package ??

see what we can finger out --- libglut3.12 is not in focal's repo so far as I can see.

[INDENT]not nice to try and fool mother Ubuntu
[/INDENT]

---

### Post by MAFoElffen on 2023-04-05
The first time I see libglut is in Lunar:
> 
**Package libglut3.12**

   
[LIST]
[*][lunar]("https://packages.ubuntu.com/lunar/libglut3.12") (libs):     OpenGL Utility Toolkit [**universe**]             
3.4.0-1: amd64 arm64 armhf i386 ppc64el s390x 
[/LIST]



---

### Post by watchpocket on 2023-04-05
> **Bashing-om said:**
> watchpocket; Hey :D
Where did you obtain webp : even 22.04 has a lower version for that app?

Hi Bashing. Not sure where I got it, tbh. (Actually, it must have been from a PPA. But which one, I don't know. I've tried to find it.)
```
--> *apt policy webp libglut3.12*
webp:
  Installed: 1.2.4-0ubuntu1~20.04.sav0
  Candidate: 1.3.0-0ubuntu1~20.04.sav1
  Version table:
     1.3.0-0ubuntu1~20.04.sav1 500
        500 [http://ppa.launchpad.net/savoury1/ffmpeg4/ubuntu](http://ppa.launchpad.net/savoury1/ffmpeg4/ubuntu) focal/main amd64 Packages
        500 [http://ppa.launchpad.net/savoury1/xapps/ubuntu](http://ppa.launchpad.net/savoury1/xapps/ubuntu) focal/main amd64 Packages
 *** 1.2.4-0ubuntu1~20.04.sav0 100
        100 /var/lib/dpkg/status
     0.6.1-2ubuntu0.20.04.1 500
        500 [https://nyc.mirrors.clouvider.net/ubuntu](https://nyc.mirrors.clouvider.net/ubuntu) focal-updates/universe amd64 Packages
        500 [https://nyc.mirrors.clouvider.net/ubuntu](https://nyc.mirrors.clouvider.net/ubuntu) focal-security/universe amd64 Packages
     0.6.1-2 500
        500 [https://nyc.mirrors.clouvider.net/ubuntu](https://nyc.mirrors.clouvider.net/ubuntu) focal/universe amd64 Packages
libglut3.12:
  Installed: (none)
  Candidate: (none)
  Version table:
```
> [I]not nice to try and fool mother Ubuntu
[/I]
Indeed. And I don't want to!


And [**[B]MAFoElffen**[/B]]("https://ubuntuforums.org/member.php?u=1044547") wrote:
> *The first time I see libglut is in Lu*nar

Wow. Interesting.  At least I can say I've been in worse messes.

---

### Post by MAFoElffen on 2023-04-05
Hmmmm:
```

http://ppa.launchpad.net/savoury1/ffmpeg4/ubuntu

```
My condolences that you have experienced this challenge.

I have to say that this is the second case this week where a User was having problems with that PPA, just this week. In the other issue, most of us looking at the new edits of his PPA description, there were quite a few red flags there, where the owner has expressly warned people from using his own PPA. That the PPA (PPA:savuory1/ffmpeg4) using things from there will certainly cause problems, that it is not maintained, and that he will not support any problems that people get from using anything there. That his focus is on a paid-for-support repo elsewhere, where he can make a living off his efforts.

I am not reading anything further into that than is already stated by himself there at: [https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4](https://launchpad.net/~savoury1/+archive/ubuntu/ffmpeg4)

My recommendation would be to back up any data associated with the app you are using from there. Remove and purge webp. Then install and use ppa-purge to get rid of that (now) questionable PPA. Once that is done, then install 'webp' from the standard Ubuntu Repositories.

---

### Post by watchpocket on 2023-04-05
What puzzles me though is that I've gotten the prompt to upgrade webp for a few months now but ignored it.  

I did have a problem last week with Rob's PPA when I couldn't upgrade FFmpeg without causing all sorts of problems and which could have caused potential removal of some useful apps.  

I  then donated to his PPA efforts, and he gave me the info to unlock FFmpeg & its libraries.  After that, all was well except for webp.

But yes, removing and purging webp and installing it from repo would be the thing to do.  I may have to temporarily remove his PPAs to do that, but otherwise I'll keep them since in all other respects they seem to be working well for me now.

>  a paid-for-support repo elsewhere

He's got a few different ones but they're all on launchpad.net.  I don't think they're elsewhere.  The one's he's already got, he's making them only partially available for free, I believe.

---

### Post by MAFoElffen on 2023-04-06
> **watchpocket said:**
> I  then donated to his PPA efforts, and he gave me the info to unlock FFmpeg & its libraries.  After that, all was well except for webp.

>  a paid-for-support repo elsewhere
He's got a few different ones but they're all on launchpad.net.  I don't think they're elsewhere.  The one's he's already got, he's making them only partially available for free, I believe.
Maybe you can remind him that you donated to his cause, adn ask for further help with 'webp.'

It's odd to me that the packages on the PPA were "locked" or crippled, and if you donated, then you got the information to unlock them.

My values are different. I will keep my thoughts on that to myself. At least for now.

I can say that i no longer recommend that PPA to others.

---

### Post by watchpocket on 2023-04-06
***webp problem solved. ***

The PPA maintainer didn't realize [I]"that the webp binary itself now depends on the new libglut3.12 system library introduced with newer freeglut versions."
[/I]
He maintains over a dozen PPAs, and freeglut-3.4.0 (which provides libglut3.12) had only been copied to a few of them.  

He thanked me for alerting him.

```
--> *apt policy webp libglut3.12*
webp:
  Installed: 1.3.0-0ubuntu1~20.04.sav1
  Candidate: 1.3.0-0ubuntu1~20.04.sav1
  Version table:
 *** 1.3.0-0ubuntu1~20.04.sav1 500
        500 http://ppa.launchpad.net/savoury1/ffmpeg4/ubuntu focal/main amd64 Packages
        500 http://ppa.launchpad.net/savoury1/xapps/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
     0.6.1-2ubuntu0.20.04.1 500
        500 https://nyc.mirrors.clouvider.net/ubuntu focal-updates/universe amd64 Packages
        500 https://nyc.mirrors.clouvider.net/ubuntu focal-security/universe amd64 Packages
     0.6.1-2 500
        500 https://nyc.mirrors.clouvider.net/ubuntu focal/universe amd64 Packages
libglut3.12:
  Installed: 3.4.0-1~20.04.sav0
  Candidate: 3.4.0-1~20.04.sav0
  Version table:
 *** 3.4.0-1~20.04.sav0 500
        500 http://ppa.launchpad.net/savoury1/ffmpeg4/ubuntu focal/main amd64 Packages
        500 http://ppa.launchpad.net/savoury1/xapps/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status 
```

---

### Post by Bashing-om on 2023-04-06
watchpocket; Great

Good that you provided the solution - from the PPA maintainner.
 
A coordinated effort that shows dividends on all the input.

[INDENT]together we do
[/INDENT]

---

