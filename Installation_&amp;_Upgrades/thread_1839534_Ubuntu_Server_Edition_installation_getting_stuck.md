---
title: "Ubuntu Server Edition installation getting stuck"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by GuyFawkess on 2011-09-05
So I burned a Ubuntu server iso, and I tried to insall it on a computer. (Note: I've never done anything with Ubuntu before.) The menu comes up. I select my language and everything's going okay. After that, I press the install button and it gets stuck on a purple screen (there's no text or icons on the screen). Please help!

---

### Post by papibe on 2011-09-05
Did you get the 32b or 64bits version?

Could you tell us more about the PC's hardware you are installing on?

Regards.

---

### Post by GuyFawkess on 2011-09-05
> **papibe said:**
> Did you get the 32b or 64bits version?
 
Could you tell us more about the PC's hardware you are installing on?
 
Regards.
 
I got the 32b version. It's an old Gateway 2000 G6233. That's all I really know about it.

---

### Post by papibe on 2011-09-05
I did some searching. I'm afraid I had bad news.

It looks you a have a Pentium II (which is fine), but 32Mb of RAM won't be enough to work. Even if you max the RAM up to 64Mb.

For more details check the [Installation System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Regards.

---

### Post by GuyFawkess on 2011-09-05
Aw. So that computer is unusable for that? Is there any secondary options for doing some kind of Ubuntu server? Prehaps one that takes less RAM?

---

### Post by haqking on 2011-09-05
> **GuyFawkess said:**
> Aw. So that computer is unusable for that? Is there any secondary options for doing some kind of Ubuntu server?


not really, even 7.04 needs 64 minimum.

56MB of memory and 650MB for a minimal install of Debian.

You coudl get something like puppy on it maybe [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

also see here [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by papibe on 2011-09-05
You have alternatives, but not in the Ubuntu family.

Take a look at this distributions:
[LIST]
[*][Damn Small Linux]("http://www.damnsmalllinux.org/") (DSL)
[*][Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")
[*][SliTaz]("http://www.slitaz.org/")
[/LIST]
Take this suggestions as a start for more research. I haven't tried any of this distros, and not all of them have easily available their minimum requirements. DSL is the only one that explicitly supports the amount of RAM you have.

Good Luck!

---

### Post by haqking on 2011-09-05
> **papibe said:**
> You have alternatives, but not in the Ubuntu family.

Take a look at this distributions:
[LIST]
[*][Damn Small Linux]("http://www.damnsmalllinux.org/") (DSL)
[*][Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")
[*][SliTaz]("http://www.slitaz.org/")
[/LIST]
Take this suggestions as a start for more research. I haven't tried any of this distros, and not all of them have easily available their minimum requirements. DSL is the only one that explicitly supports the amount of RAM you have.

Good Luck!


DSL is pretty dead in the water as far as updates or support last version release was 3 or 4 years ago i think.  But i used to like it on a USB key, used to carry it around with me everywhere.  but it should run fine on his system

---

### Post by GuyFawkess on 2011-09-06
Would this work for me? If so, which one?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
 
If not, what's a good **terminal operating system** for a server like Ubuntu that would be supported on my system?

---

### Post by haqking on 2011-09-06
> **GuyFawkess said:**
> Would this work for me? If so, which one?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
 
If not, what's a good **terminal operating system** for a server like Ubuntu that would be supported on my system?


The requirements are the same, the minimal install just means no packages or minimal packages which you add one by one as you need.

As mentioned above there are are a few, as for a server linux, though there are dedicated server version, any Linux version will act as a server,  a server is defined by its services not necessarily its hardware and all linux services can be added toa linux distro.

try here for a distro chooser [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

VectorLinux

[http://www.vectorlinux.com/](http://www.vectorlinux.com/)

Puppy Linux

[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

Slackware

[http://www.slackware.com/](http://www.slackware.com/)

Debian 

[http://www.debian.org/](http://www.debian.org/)

Damn Small Linux 

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)


[http://www.pclinuxos.com](http://www.pclinuxos.com)

Just dont add a GUI and even the ones that require a certain amount of memory may run

---

### Post by GuyFawkess on 2011-09-06
Slackware will work right?
[http://www.slackware.com/install/sysreq.php](http://www.slackware.com/install/sysreq.php)

---

### Post by haqking on 2011-09-06
> **GuyFawkess said:**
> Slackware will work right?
[http://www.slackware.com/install/sysreq.php](http://www.slackware.com/install/sysreq.php)


Yeah they all will pretty much without GUI, you said you had 32GB Ram ?

---

### Post by GuyFawkess on 2011-09-06
Yep. I'ma burn the CD. :D

---

### Post by GuyFawkess on 2011-09-06
Sorry to sound stupid but for Slackware ([http://www.slackware.com/index.html](http://www.slackware.com/index.html)) where do I download the ISO? Do I have to buy the CD?

---

### Post by haqking on 2011-09-06
> **GuyFawkess said:**
> Yep. I'ma burn the CD. :D

good luck, just dont add anything you dont need, especially services as they could be resource hungry.

Especially dont add X or any type of GUI DE ;-)

---

### Post by haqking on 2011-09-06
> **GuyFawkess said:**
> Sorry to sound stupid but for Slackware ([http://www.slackware.com/index.html](http://www.slackware.com/index.html)) where do I download the ISO? Do I have to buy the CD?

by clicking the get slack link in side menu ;-)

[http://www.slackware.com/getslack/](http://www.slackware.com/getslack/)

use a torrent or mirror

---

### Post by GuyFawkess on 2011-09-06
For a server I would probably want A, N, and TCL?
[http://www.slackware.com/install/softwaresets.php](http://www.slackware.com/install/softwaresets.php)

---

### Post by haqking on 2011-09-06
> **GuyFawkess said:**
> For a server I would probably want A, N, and TCL?
[http://www.slackware.com/install/softwaresets.php](http://www.slackware.com/install/softwaresets.php)


yeah sounds about right.

remember you can remove or disbale any unnecessary services.

---

### Post by GuyFawkess on 2011-09-06
Ugh. I can't because. The ISO is too big, so I'd need a DVD for that and I don't have a DVD drive. PuppyLinux didn't work, it got stuck on the "Installing kernal" (I don't remember exactly what it said)
 
Anyways will my system support either of these?
[http://distro.ibiblio.org/tinycorelinux/overview.html](http://distro.ibiblio.org/tinycorelinux/overview.html)
[http://distro.ibiblio.org/baslinux/](http://distro.ibiblio.org/baslinux/)
 
Also can I use BasicLinux as a server? I'm not sure if it will support a server or not.

---

### Post by 1clue on 2011-09-06
FWIW if you download anything that needs a whole single-layer CD then you got the wrong distro.

What's your intent here?  Is this a result of you being bored or curious and you just had the hardware sitting around, or do you expect to get something that will do real work in modern terms?

The reason I'm asking is because the specs on my phone are better than the specs on your computer, probably even if you consider that the phone has an ARM processor instead of Intel.  I have an old box with similar specs only it's a p4, and I wouldn't even think about trying to put a real distro on it.

If you're just doing it for a lark or to see if you can, then by all means go ahead.

If you're trying your first Linux install, then stop now and find something else.

If you know what you're doing and intend to use this system for a specific limited purpose well within its limitations, then go ahead.

If you're doing this because you heard or read somewhere that Linux is the fastest operating system you can put on a computer, then be aware that that statement can only be considered true if you skinny it up a lot.  And it still doesn't mean your system will work with it.

Based on the way you've been posting I do not think you're an expert Linux user.  IMO that eliminates this computer from consideration on almost every count.

Good luck and have fun.

---

