---
title: "Is alpha 4 dealyed?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-08-13
Is alpha 4 dealyed?

---

### Post by taavikko on 2009-08-13
> **rednus said:**
> Is alpha 4 dealyed?

Wait for the official announcement so you don't have to guess,
Subscribe to the announce lists: [https://lists.ubuntu.com/](https://lists.ubuntu.com/)

---

### Post by bear24rw on 2009-08-13
i havent heard anything about it being delayed.. i would keep trying this page

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

it should be up later today i imagine.

btw, anyone know how to see what alpha you are current running?

---

### Post by novafluxx on 2009-08-13
FIRST! hehe


> **bear24rw said:**
> i havent heard anything about it being delayed.. i would keep trying this page

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

it should be up later today i imagine.

btw, anyone know how to see what alpha you are current running?

The Alpha's themselves are nothing more then snapshots of the repositories. So if you installed Alpha 3, and when Alpha 4 is released you run update manager, you're running the equivilent of Alpha 4.

They are not mutually exclusive!

They are simply named milestones of the development process. The only real difference you will see is the installer may be updated/changed. As is the case with Alpha 3 and GRUB 2 not detecting other OS's, that bug was fixed after Alpha 3's release, so if you install a daily build (thats what I do, instead of waiting for the next alpha) or install Alpha 4, that issue won't occur during the installation process

---

### Post by taavikko on 2009-08-13
> **bear24rw said:**
> 
btw, anyone know how to see what alpha you are current running?

Alpha-release is just a snapshot of current state. when installing during devel-release you're running development-release, not alpha.
And then finally official-release.

---

### Post by psyke83 on 2009-08-13
> **bear24rw said:**
> i havent heard anything about it being delayed.. i would keep trying this page

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

it should be up later today i imagine.

btw, anyone know how to see what alpha you are current running?

No, things don't work like that. Each of the milestones (alpha, beta, release candidate, final) are only snapshots of the latest code in the repositories at the time that the ISOs were released.

---

### Post by jppr on 2009-08-13
if you want to do a fresh installation... [http://cdimage.ubuntu.com/daily-live/... ]("http://cdimage.ubuntu.com/daily-live/")
there is always latest ubuntu version

---

### Post by taavikko on 2009-08-13
> **jppr said:**
> [http://cdimage.ubuntu.com/daily-live/... ]("http://cdimage.ubuntu.com/daily-live/")
there is always latest ubuntu version

nope, there's always the latest daily-image, just a little bit of semantics.

---

### Post by rednus on 2009-08-13
> **jppr said:**
> if you want to do a fresh installation... [http://cdimage.ubuntu.com/daily-live/... ]("http://cdimage.ubuntu.com/daily-live/")
there is always latest ubuntu version

thanks jppr.... but I am really not looking for the software.. but the announcement.. i already have latest updates until yesterday night.. but curious to see the announcement thats all..

---

### Post by novafluxx on 2009-08-13
> **taavikko said:**
> nope, there's always the latest daily-image, just a little bit of semantics.

This is what I usually install whenever I want to try the development releases. No point in downloading a 2 week old image when teh daily-live will do just fine! :popcorn:

---

### Post by kevpan815 on 2009-08-13
It's still only 11:20 A.M. here in Chicago, I would keep checking the [http://cdimages.ubuntu.com/](http://cdimages.ubuntu.com/) download server (look under the releases folder for Alpha 4).

---

### Post by inportb on 2009-08-13
> **novafluxx said:**
> This is what I usually install whenever I want to try the development releases. No point in downloading a 2 week old image when teh daily-live will do just fine! :popcorn:

... except when the daily-live breaks hard. That's when I grab the 2 week old image in a jiffy.

---

### Post by keypox on 2009-08-13
Since alpha 4 is nothing more than a dated, daily release, then its not dealyaed right?

---

### Post by keypox on 2009-08-13
And its up hehe first lol, well this page is up [http://www.ubuntu.com/testing/karmic/alpha4](http://www.ubuntu.com/testing/karmic/alpha4) but links are still down.  Prob really soon though.

---

### Post by wayne_cat on 2009-08-13
just installed gdm 2.27.4-0ubuntu11 ... so my system is already better than A4 :tongue:

---

### Post by nhasian on 2009-08-13
downloading the 64 bit karmic alpha 4 iso right now from:

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

---

### Post by fjosh on 2009-08-13
32-bit Ubuntu Alpha 4 .torrent -- let's get this torrent going!  :popcorn:


[http://cdimage.ubuntu.com/releases/karmic/alpha-4/karmic-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/releases/karmic/alpha-4/karmic-desktop-i386.iso.torrent)

---

### Post by slakkie on 2009-08-13
No updates for me via the repo's, guess my laptop is already at alpha 4 level..

---

### Post by terry_gardener on 2009-08-13
i have only had 1 package update all day. guess mine is update to date also

---

### Post by Luca_turicci on 2009-08-13
i've been updating packages since 01:00 in the morning, i guess it means i'm at alpha 4 now.... I was specting it was like when i updated from Hardy to Intrepid, with the Update manager and stuff.

---

### Post by GeorgeVita on 2009-08-13
> **slakkie said:**
> No updates for me via the repo's, guess my laptop is already at alpha 4 level..

Hi **slakkie**, R U using 'Karmic-proposed' updates?
Thanks for answering,
George

---

### Post by hansdown on 2009-08-13
Hi rednus.

It is available.

[http://ubuntuforums.org/showthread.php?t=1239590](http://ubuntuforums.org/showthread.php?t=1239590)

---

### Post by slakkie on 2009-08-13
> **GeorgeVita said:**
> Hi **slakkie**, R U using 'Karmic-proposed' updates?
Thanks for answering,
George

Yes, but I had no proposed packages installed. Do you know a way of finding out which packages are installed from proposed?

```

for i in $(dpkg -l | grep "^ii"| awk '{print $2}')
do
apt-cache policy $i | grep "karmic-proposed" &>/dev/null
[ $? -eq 0 ] && echo $i

```

This came up empty

---

### Post by novafluxx on 2009-08-13
> **inportb said:**
> ... except when the daily-live breaks hard. That's when I grab the 2 week old image in a jiffy.

Never had that problem, but I suppose it can happen

---

