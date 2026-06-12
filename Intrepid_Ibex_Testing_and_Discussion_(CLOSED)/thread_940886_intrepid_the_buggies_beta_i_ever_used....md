---
title: "intrepid the buggies beta i ever used..."
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kforum on 2008-10-07
hi im a traditionally a gentoo user, so i know what im doing generally around the linux world.

im trying to use kubuntu more as of late to help/learn more about the distro.

ok, so first and foremost, when i boot the live cd(Oct,1 version) it above all shows me 2 options, the traditional test and play, and the direct to install one.

if i choose the direct to install one, it boots me into weird screens with scrambled colors, everything is broken video-wise, but the system seems to be running fine in the background...
(already filed a bug on this)

if i boot the first, traditional choice, it boots fine. its strange though that its a VERY time consuming boot considering other distros, even other ubuntu versions. 
And also, when kde4 is loading things(i assume) it show me what looks like an HD inside a separate window, and it just halts there(until i click somewhere then it continues loading/booting stuff).
Normally in kde3 you would see these many icons show up and light up one after the other, until everything was set then the system loaded, so this is strange. 
i hope it gets fixed in time for release.

another thing, inside the liveCD environment, when trying to access my wireless network, its simply not found... and more then that, there around around 5 of them around the block, and only 1 is detected... VERY weird indeed.

still, being stubborn i installer the 'bugger' anyways, and after the new system was installed, then 'knetmanager' saw all of the wifi nets, but i still cant connect to it dont know why, i set all the proper info and it seems to ignore it.

also, if i do iwconfig, the essid field and everything else is empty...

anyways, its been a long show of horrors so far, making this certainly the buggiest beta experience ever, which makes me wonder... how are ubuntu devs capable of making things so buggy, in a whole?

anyways just for the record i have a core2duo, a gforce 8600m GT, and the iwl4965 intel card.(in case you where wondering)


comments and assistances in solving my problems will be very appreciated.


cheers.
:)

edit; also, does anyone know the syntax for inputting dnss inside the new knetman., i assume it s bunch of comma separated values, like : xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx . but im not really sure so far...

edit2:another issue is with my battery, in the live cd the battery was not charging(which is better i believe), and when i pressed my 'charge' button in the laptop it started charging like it should.
but after the install the battery just charges relentlessly and the charge button is ignored... great.

also, the 'kmix' or whatever brings functionality to the multimedia keys, needs some serious calibration, the up/down volumes only call the event, they dont change it up or down. on the other hand the brightness ones change 2 presses instead of only one, and the Mute one works, but doesnt lid up my led, when its at it...(i have a led that shines if mute is on...).

all very, very strange.

---

### Post by MikeB23930 on 2008-10-07
I can't offer you any help, but I can go you one better.  I can't get my wired network to work even though ifconfig shows that it is up and has been assigned an IP address by my router.  Wired network works fine in Kubuntu 8.04 installed in a different partition on the same machine.

Oh, woe is me.

Mike

---

### Post by Kow on 2008-10-07
Nice to know... but Intrepid is the most stable beta I have ever used. In fact, the ONLY bug I encountered was having to disable "Unredirect Fullscreen" in compiz settings to get the screensaver to activate. And, this is on an upgraded hardy install. Upgrades from release to a development branch are never supposed to go smoothly (and it did.)

---

### Post by ofb on 2008-10-07
> **kforum said:**
> anyways, its been a long show of horrors so far, making this certainly the buggiest beta experience ever, which makes me wonder... how are ubuntu devs capable of making things so buggy, in a whole?

As you've probably noticed from the "Tell us about your Intrepid experience" thread, most people aren't having trouble. Like you, I'm not so lucky, and would suggest filing bug reports like you have and then just wait for final.

'IMHO' time: I prefer Ubuntu overall and am thus pretty impressed with the devs, but also I've found other distros like Mandriva/PCLOS install better on my boxes. I'm hoping Ibex will finally correct some of the problems we've picked up with Gibbon and Heron. In my experience Ubuntu isn't a distro you can hand to just anyone and walk away yet. Others quite disagree, so obviously it depends on the hardware.

Sorry that's all comment and no assistance. You've got quite a list of trouble there. What happens if you try Heron?

---

### Post by mariner09 on 2008-10-07
Does Kubuntu come with an alternate CD?

Maybe try the standard Ubuntu or alternate and see if it works better.  From what I've read, Kubuntu seems to be buggier than the standard Ubuntu releases.

---

### Post by kforum on 2008-10-07
i think most people arent having trouble because upgrading into a beta is more reliable then installing a *beta* from scratch.
least to say, in the elder one you have made many fixes along the way.

but anyhow, rest assured guys that im not trying to use kubuntu, just trying to help it, id prob never trade gentoo-based for anything.

though, to all of you taht say your system is flawless... have you tried using multimedia keys? how are they responding?
and what about wifi?

cheers.

thanks for teh replies
and besides there are better distros out there then ubuntu, like mentioned above.

---

### Post by jfernyhough on 2008-10-07
Try a daily LiveCD.

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/) , or ideally a mirror.

---

### Post by kforum on 2008-10-07
i did, and i also got a problem updating today btw, it coudnt download certain files form a mirror. and boy is the new adept troublesome... 
ill try it again later, but i doubt it will fix my problems, even tough i hope it will. ^.^;

---

### Post by cariboo on 2008-10-07
If you are going to do a clean install, using the alternate cd, it seems to have better hardware detection. With the alternate my hard drives are detected in the correct order, while the LiveCD detects them wrong and sets them up wrong my install still works with no problem, it just plain bugs me.

```
sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       20023   146183467+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sdb3           10200       30401   162272565    5  Extended
/dev/sdb5           29697       30401     5662881   82  Linux swap / Solaris
/dev/sdb6           12112       29696   141251481   83  Linux
/dev/sdb7           10200       12111    15358077   83  Linux
```

/dev/sdb is actually my first and only ide drive while /dev/sda is the first of three sata drives. The other two are esata and turned off at the moment.

Jim

---

### Post by mariner09 on 2008-10-07
On my T61 with the std Ubuntu, since Alpha 6, everything worked well, except for using a projector.  I've had some xorg updates since and will try again in a few days.

All my media keys and function keys are working properly except for Fn+F7 which is the key that switches the LCD/CRT combinations.  That hasn't worked for some time back to a few major releases ago...

---

### Post by nanog on 2008-10-08
> though, to all of you taht say your system is flawless... have you tried using multimedia keys? how are they responding?
and what about wifi?


ummm...the function keys and wireless all work flawlessly on my dell 1405, dell m1330, dell mini 9, and compaq v2000z.  this is out of the box with no fiddling. that being said i don't like kde so i've never tried kubuntu. 

its probably a good thing that you are trying other distros...not sure how much longer gentoo will be around.

---

### Post by kforum on 2008-10-08
yes these worked for me too, the problem was mainly with volume keys and brightness keys, etc... anything that has increase/decrease function.
^^

cheers

---

### Post by KrazyPenguin on 2008-10-08
How come every release, there is a thread like this:

Buggiest alpha, buggiest Beta, Buggiest release!?!?!?

Don't use beta versions if you want a working system .period.

Also, if Hardy is working for you, then keep using it.

I installed Ibex, and it isn't really that much better.

Maybe if the themes were overhauled, like the way they were suppose to be, it would have felt more exciting.

;-)
:guitar:

---

### Post by caryb on 2008-10-08
Have to agree with the previous post & I generally don't post in these sort of un-constructive posts but I had to answer this question...

> Does Kubuntu come with an alternate CD?

Answer is yes!


Cary

---

### Post by kforum on 2008-10-08
i really dont see how my original post was un-constructive, but rather very informative. bringing attention to a few things, besides im not here for 'every beta' like mentioned above, i was exactly testing this one(and in dont use ubuntu regularly) and giving the feedback.(like i do sometimes with interesting distros)

honestly to me its post like krazypenguin's that are VERY un-constructive least to say.

there is nothing to say beyond that really, i felt this post was very civilized until the later comments.

...and im not stretching this any further given the 'quality' of local perception.

maybe the mods should close this, specially since this got no attention from anyone with actual suggestions/solutions.(even though it did server as a gathering spot for common issues)

cheers.

---

### Post by Slug71 on 2008-10-08
Wasn't the Beta released on Oct 2nd and not 1st though??
Which means the OP actually has Alpha 6.
RC comes out Oct 23rd. Might want to wait for that.

---

### Post by kforum on 2008-10-08
maybe it was released on the 2nd ,but the file says mod. on oct 1.

you know it makes sense, made on the 1st, released on the 2nd.
besides, i got it on the 6th.

also, bear in mind that when i downloaded this, like my post says, i wasn't looking for a working distro, but rather to contribute to a beta one...

i feel like a recorder atm, but anyways, by the way things are going i dont think many of these issues will be solved by RC1, specially since some of them seem to not be ubuntu's responsibility but rather, the kde's team responsibility, so...

^.^

cheers

---

### Post by KrazyPenguin on 2008-10-08
> **kforum said:**
> i really dont see how my original post was un-constructive, but rather very informative. bringing attention to a few things, besides im not here for 'every beta' like mentioned above, i was exactly testing this one(and in dont use ubuntu regularly) and giving the feedback.(like i do sometimes with interesting distros)

honestly to me its post like krazypenguin's that are VERY un-constructive least to say.

there is nothing to say beyond that really, i felt this post was very civilized until the later comments.

...and im not stretching this any further given the 'quality' of local perception.

maybe the mods should close this, specially since this got no attention from anyone with actual suggestions/solutions.(even though it did server as a gathering spot for common issues)

cheers.

I don't really see how your post was CONSTRUCTIVE.
It appears to be about Kubuntu.  Why not use the Kubuntu forums???

Also, how does whining about how buggy a beta is help anybody???

Please enlighten us.

Thanks.

:shock:

---

### Post by kforum on 2008-10-08
> **KrazyPenguin said:**
> I don't really see how your post was CONSTRUCTIVE.
It appears to be about Kubuntu.  Why not use the Kubuntu forums???

Also, how does whining about how buggy a beta is help anybody???

Please enlighten us.

Thanks.

:shock:

it is curious that i bare to behold the times when honestly no longer stand tall and invited in the halls of fortitude and respect, in a time when the individual says, be not, and bear so within...
to change the words of a man and literally 'explain'(to draw out below)
'i spread my honesty below your feet, and pledged myself in faith, tread lightly, for you tread on my honesty.'

cheers.

---

