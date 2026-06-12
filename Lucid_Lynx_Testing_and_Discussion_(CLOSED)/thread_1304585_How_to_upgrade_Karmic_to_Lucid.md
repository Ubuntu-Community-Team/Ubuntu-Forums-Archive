---
title: "How to upgrade Karmic to Lucid"
date: 2009-10-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lovinglinux on 2009-10-29
I guess Lucid repositories will be available soon, but I don't remember how to upgrade from  Karmic to Lucid. What is the command?

---

### Post by Technoviking on 2009-10-29
Not for a few days, the toolchain will be updated on November 5th. 

T-V

---

### Post by jpeddicord on 2009-10-29
Once [http://archive.ubuntu.com/ubuntu/dists/lucid/](http://archive.ubuntu.com/ubuntu/dists/lucid/) starts to work, update-manager should pick up on it if run with -d:

```
update-manager -d
```

Or if you're feeling ambitious, replace "karmic" with "lucid" in sources.list and **carefully** dist-upgrade. You're on your own if you try that though. (This still won't work until the toolchain is up.)

---

### Post by lovinglinux on 2009-10-29
> **jpeddicord said:**
> update-manager -d.


Or if you're feeling ambitious, replace "karmic" with "lucid" in sources.list and **carefully** dist-upgrade. You're on your own if you try that though.


Once [http://archive.ubuntu.com/ubuntu/dists/lucid/](http://archive.ubuntu.com/ubuntu/dists/lucid/) starts to work, update-manager should pick up on it if run with -d as above.

Thanks. I will use **update-manager -d** when the time comes. Do I need to run it with gksudo? 

Anyway, I'm running another instance of Karmic on another partition with a different user from my production environment, so unless it screws up Grub it shouldn't cause many problems ;)

---

### Post by jpeddicord on 2009-10-29
> **lovinglinux said:**
> Thanks. I will use **update-manager -d** when the time comes. Do I need to run it with gksudo?

No, when it needs to start the upgrade it will elevate its privileges automatically.

---

### Post by lovinglinux on 2009-10-29
> **jpeddicord said:**
> No, when it needs to start the upgrade it will elevate its privileges automatically.

Thanks.

---

### Post by jppr on 2009-10-29
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by autocrosser on 2009-10-29
Yes--mine are edited & ready to go.....

I just used apt-get & the repo IS open--all the placeholders are there--nothing really in them yet---but it looks like they are ready for the 5TH!!!!

---

### Post by slakkie on 2009-10-30
For command line upgrades run:

```

sudo aptitude install update-manager-core
sudo do-release-upgrade -d

```

BTW, if you want to upgrade without the tools, I think it is wise to do it the Debian way:

```

# Make sure your current release is the latest and greatest
sudo aptitude update
sudo aptitude safe-upgrade

# Change sources to new release
perl -p -i.karmic -e 's/karmic/lucid/' /etc/apt/sources.list

# Start upgrading to new release
sudo aptitude update
sudo aptitude install dpkg aptitude apt 
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```

---

### Post by klim8 on 2009-10-30
Repositories seem to be working. 7 updates already.

---

### Post by zika on 2009-10-30
You're making my fingers itch and my heart pound. But, 9.10 is so stable now ...

---

### Post by autocrosser on 2009-10-30
Then just give it--make a new one & leave your stable world behind.......

---

### Post by autocrosser on 2009-10-30
HERE WE GO!!!!!!

base-files (5.0.0ubuntu8) lucid; urgency=low

  * /etc/issue, /etc/issue.net, /etc/lsb-release: Welcome to Lucid!

 -- Colin Watson <[ cjwatson at ubuntu.com]("https://launchpad.net/%7Ecjwatson")>   Fri, 30 Oct 2009 11:39:07 +0000

Note>Colin's email edited

---

### Post by chrismine on 2009-10-30
The deed is done!

---

### Post by plun on 2009-10-30
Hello Lucid.......:popcorn:

> plun@plun-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"


---

### Post by fluteflute on 2009-10-30
> **jpeddicord said:**
> Or if you're feeling ambitious, replace "karmic" with "lucid" in sources.list and **carefully** dist-upgrade. You're on your own if you try that though. (This still won't work until the toolchain is up.)You're on your own anyway me thinks.

---

### Post by jppr on 2009-10-30
> **plun said:**
> hello lucid.......:popcorn:

+1 :)

---

### Post by jpeddicord on 2009-10-30
> **fluteflute said:**
> You're on your own anyway me thinks.

Very good point. (I actually had to do this to upgrade to Lucid earlier today; there's no information for update-manager to pick up about it yet.)

---

### Post by lukjad on 2009-10-30
> **lovinglinux said:**
> I guess Lucid repositories will be available soon, but I don't remember how to upgrade from  Karmic to Lucid. What is the command?
Jump the gun much? ;)

---

### Post by autocrosser on 2009-10-30
Never :guitar:

---

### Post by hikaricore on 2009-10-30
I figure the sooner i upgrade the smaller the number of packages i'll need to install next month.  :p

---

### Post by gjoellee on 2009-10-30
I am on Xubuntu...still awaiting updates :-&

---

### Post by MacUntu on 2009-10-30
Thanks for preventing the after-release-depression! :lolflag:

---

### Post by plun on 2009-10-31
> **MacUntu said:**
> Thanks for preventing the after-release-depression! :lolflag:

Hehe...:D

I also have **Karmic-Proposed** enabled.....already a bunch of updates.

[https://lists.ubuntu.com/archives/karmic-changes/2009-October/thread.html](https://lists.ubuntu.com/archives/karmic-changes/2009-October/thread.html)

;)

---

### Post by wnelson on 2009-10-31
Lucid list has been started.....

[https://lists.ubuntu.com/archives/lucid-changes/](https://lists.ubuntu.com/archives/lucid-changes/)

---

### Post by gjoellee on 2009-10-31
I've got updates on Xubuntu now :p

---

### Post by davideotape on 2009-10-31
Yep, I've already gota bunch of updates. Is there any danger in my manually changing my sources.list?

---

### Post by fahadsadah on 2009-10-31
It's safe to change it yourself.

---

### Post by slakkie on 2009-11-01
> **wnelson said:**
> Lucid list has been started.....

[https://lists.ubuntu.com/archives/lucid-changes/](https://lists.ubuntu.com/archives/lucid-changes/)

I want the rss link for that maillinglist.. I know there was a karmic one, but I mis-placed the link :{

---

### Post by 23meg on 2009-11-01
> **slakkie said:**
> I want the rss link for that maillinglist.. I know there was a karmic one, but I mis-placed the link :{

It's not available yet. When it is, it will probably be at [http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges).

---

### Post by linux6994 on 2009-11-01
Just changed my sources to lucid. A few updates, looking forward to newer things:)

---

### Post by celticbhoy on 2009-11-01
Why no Lucid testing in control panel yet ???
:cry:

---

### Post by NCLI on 2009-11-01
Write a mod about it, we must complain! :p

---

### Post by cariboo on 2009-11-01
If it's that important to you, create a thread in [ff&h]("http://ubuntuforums.org/forumdisplay.php?f=48"), us mods can't do anything about it. It's a job for the **Admin's**

---

### Post by Regenweald on 2009-11-01
Current status: 31 updates [+31], 22622 new [+22409].
rhiken@Horsford:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  grub{a} grub-common{a} grub-pc 
The following packages will be upgraded:
  base-files binutils cpp-4.4 gcc-4.4 gcc-4.4-base gcj-4.4-base gcj-4.4-jre 
  gcj-4.4-jre-headless gcj-4.4-jre-lib lib32gcc1 lib32stdc++6 libc-bin 
  libc-dev-bin libc6 libc6-dev libc6-i386 libgcc1 libgcj10 libgcj10-awt 
  libgfortran3 libgomp1 libpython2.6 libstdc++6 python python-minimal 
  python-support python2.6 python2.6-minimal 
28 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 50.7MB of archives. After unpacking 4,096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main base-files 5.0.0ubuntu8 [68.0kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main libc6-i386 2.10.1-3ubuntu1 [3,671kB]
1% [2 libc6-i386 824275/3,671kB 22%]      

nice.... :)

---

### Post by Kevbert on 2009-11-02
Only 25 updates so far for me...

---

### Post by jppr on 2009-11-02
> **Kevbert said:**
> Only 25 updates so far for me...

repos is new 2.6.32-2.2 kernel, just installed it and works fine

---

### Post by 00ber n00b on 2009-11-02
You guys are crazy!  ;)

---

### Post by sim-value on 2009-11-02
Is it possible to make a Seperator in GRUB which will seperate entrys of Lynx and Karmic ?

---

### Post by ranch hand on 2009-11-02
See my sig link for how to build a custom entry.

Use the "generic" entry and it will work no matter what kernel they throw at you.  It boots just about anything in that partition (I have changed OS' and it still boots them right up).
EDIT
Here is a sample;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF

```
That is a Kinky Kitten upgraded to Lounge Lizard

---

### Post by sim-value on 2009-11-02
Thank-you will try that !

---

### Post by sports fan Matt on 2009-11-02
Ok, I've been away from my pc all weekend.  Don't have much to lose on this pc..Should I jump in?  Opinions welcome :)

---

### Post by autocrosser on 2009-11-02
Jump in--the water is fine......nothing major will rock the boat until a week or so after the UDS & I have a feeling that this one will be a fairly tame ride....

---

### Post by shafin on 2009-11-02
> **autocrosser said:**
> Jump in--the water is fine......nothing major will rock the boat until a week or so after the UDS & I have a feeling that this one will be a fairly tame ride....
I jumped in, the water really looks fine :)

---

### Post by sports fan Matt on 2009-11-02
I had tried with : update-manager -d but nothing..any advice?

---

### Post by ranch hand on 2009-11-02
> **sox fan Matt said:**
> I had tried with : update-manager -d but nothing..any advice?
Check your /etc/apt.sources.list and see if it is for karmic or lucid.  If it has not changed edit it to read lucid anywhere it says karmic.

Then run sudo apt-get dist-upgrade.

That will do it.

---

### Post by sports fan Matt on 2009-11-02
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by nerdopolis on 2009-11-02
run sudo apt-get update before sudo apt-get dist-upgrade.

---

### Post by sports fan Matt on 2009-11-02
doh! Its been a long weekend with me hardly out of bed, just am now feeling somewhat better :)

---

### Post by Squonk07 on 2009-11-02
> **sox fan Matt said:**
> doh! Its been a long weekend with me hardly out of bed, just am now feeling somewhat better :)

Man, it's going around, isn't it? Sounds like my weekend. Hope you keep getting better. :)

Count me in for Licentious Leprechaun; I set up two identical new Karmic partitions and updated the second one to Lucid. They share a Home directory, so we'll see how that little experiment works out. So far for me the GUI for Software Sources has broken in Lucid, which is no biggie. Manual updates to the Sources list work fine.

Bring on the breakage!

---

### Post by ndefontenay on 2009-11-02
Will Lucid be running with Gnome 3?

---

### Post by sports fan Matt on 2009-11-02
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

---

### Post by DougieFresh4U on 2009-11-02
> **Squonk07 said:**
>  So far for me the GUI for Software Sources has broken in Lucid, which is no biggie. Manual updates to the Sources list work fine.
Bring on the breakage!

Why am I not surprised about that one!!
Seems a little bit early for the Software Sources issue which has happened in every beginning since Dapper :p:p

---

### Post by Squonk07 on 2009-11-02
> **DougieFresh4U said:**
> Why am I not surprised about that one!!
Seems a little bit early for the Software Sources issue which has happened in every beginning since Dapper :p:p

The breakage is logical. This is the first time I've gotten started this early, though, so it's new to me. I've only been around since Edgy, anyway.

---

### Post by ranch hand on 2009-11-02
> **sox fan Matt said:**
> Distributor ID:    Ubuntu
Description:    Ubuntu lucid (development branch)
Release:    10.04
Codename:    lucid
Bet that feels good.  It sure looks good.

---

### Post by Bimps on 2009-11-03
> **ndefontenay said:**
> Will Lucid be running with Gnome 3?

[No]("http://ubuntuforums.org/showpost.php?p=8214235&postcount=9").

---

### Post by phenest on 2009-11-03
```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
sudo apt-get update && sudo apt-get upgrade
```
Ok. I'm in.

---

### Post by zika on 2009-11-03
This is the first time for me to try to start without update-manager. What is going to happen with ppa's I have in sources.list.d and what about Medibuntu ...? Should I clean all that for myself or wait for toolchain?

---

### Post by ranch hand on 2009-11-03
Medibuntu should be fine treated just like the other entries, there may be some lag in their getting their repo up but I didn't get any errors about it not being found.

The ppas should also be fine as all we are doing is using 9.10 right now and they will probably update their stuff.

---

### Post by sports fan Matt on 2009-11-03
it feels good indeed :)

---

### Post by autocrosser on 2009-11-05
I normally dual-source until after the UDS--the past release will sometimes get things before the new testing due to bug fixes & in any case, if there is a change to the testing update--the numbers will be higher--so the prior release install will not be installed---It's normal to have a bit of a mix for the first couple of weeks---DO MAKE SURE YOU PURGE THE KARMIC SOURCE STUFF AFTER UDS......third party stuff you need to go on a "as-per" basis--I tend to keep Medibuntu with the old release & actively look for PPA's that include the testing release or do ask the maintainer if he/she is planning to include it soon.

---

### Post by VMC on 2009-11-05
> **ranch hand said:**
> Medibuntu should be fine treated just like the other entries, there may be some lag in their getting their repo up but I didn't get any errors about it not being found.

The ppas should also be fine as all we are doing is using 9.10 right now and they will probably update their stuff.

I'm getting 404's with ppa's right now. The Medibuntu seems fine.

---

### Post by rubenverweij on 2009-11-05
I'm in too and ever so excited! :lolflag:

---

### Post by jppr on 2009-11-05
> **zika said:**
> This is the first time for me to try to start without update-manager. What is going to happen with ppa's I have in sources.list.d and what about Medibuntu ...? Should I clean all that for myself or wait for toolchain?

it works now, just came toolchain updates, python-apt

---

### Post by Claus7 on 2009-11-05
Hello,

some quick and easily answered, I suppose, questions for all of you who have picked up Lucid.

I have two hdd, with hardy on one and karmic on the other. 

[LIST=1]
[*]If I update from hardy to lucid, am I going to face any grub problems?
If I type in karmic:
```
grub --version
```
I get:
> grub (GNU GRUB 0.97)

[*]How does it look like the environment? I mean that karmic is out only a few weeks now. What are the differences you are watching between the two? 

[*]Should, since it is later than 5th of November, to update my sources list?
 I mean, this is not done automatically if I type:

```
sudo apt-get update && sudo apt-get upgrade
```

Should I type:
```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
```
as well?
(That question goes for both upgrading hardy or karmic. So in place of karmic in the above command consider hardy for hardy).
[*]And finally, will ext3 of hardy and ext4 of lucid cause any conflicts?
[/LIST]

Thank you and nice adventure to all of you!
Regards!

---

### Post by ranch hand on 2009-11-05
First, I would not, in any universe I know of, be trying to update Hardy to 10.04 at this point.

If you want 9.10 to upgrade then I would;
A>Make sure that it is up to date.
B>Remove grub-legacy and grub-common
C>Install grub-pc and grub-common

As to the Hardy on ext3 and 10.04 on ext4, that is going to have to be looked into when we actually have 10.04.  I think a clean install would be better with the home folder backed up.

But we are not close to 10.04 at all.  Right now we are using a modified 9.10 to build a foundation for 10.04 and that has really not begun in any serious way.

---

### Post by flipper9 on 2009-11-05
Soooo.... (tongue in cheek)...if I upgrade now on my "stable" Karmic 9.10 system...on my production laptop...I'm in for a world of hurt? :D

---

### Post by ranch hand on 2009-11-05
No, I think you can handle it.

There is not much changed yet except the kernel really.  A slightly different version of grub2 (I can't see any difference).

I don't think you are proposing to upgrade from Hardy either.

---

### Post by VMC on 2009-11-06
> **ranch hand said:**
> First, I would not, in any universe I know of, be trying to update Hardy to 10.04 at this point.

If you want 9.10 to upgrade then I would;
A>Make sure that it is up to date.
B>Remove grub-legacy and grub-common
C>Install grub-pc and grub-common

As to the Hardy on ext3 and 10.04 on ext4, that is going to have to be looked into when we actually have 10.04.  I think a clean install would be better with the home folder backed up.

But we are not close to 10.04 at all.  Right now we are using a modified 9.10 to build a foundation for 10.04 and that has really not begun in any serious way.

This same question came up before when someone wanted to do the exact same thing from several releases back up to karmic. I'm not sure what the final suggest was but it would but it would be far easier to install karmic and go from there. I don't know if they could in fact work their way back or in this case up to karmic by upgrading to the closest release and then agin the the next release and so on. A real time consuming adventure and sure to case problems.

---

### Post by ranch hand on 2009-11-06
It sure would, I upgraded Stoner edition to 9.10 several times in 9.10 testing and then again for here.

Coming from Hardy to intrepid, get updated and stable, to Jaunty, get updated and stable, to Kinky, get updated and stable, to lounge would be real boring until something broke.

There should be a way to go from Hardy to Lounge when Lounge is released but I can't imagine that you would get ext4, I mean formatting is formatting, hard to keep your data.

I intend to change my "secure" OS from Hardy to Lounge (when I feel Lounge is stable - Hardy will still have a year of security updates), but it will be a clean install and data transfered from old to new.

---

### Post by cariboo on 2009-11-06
Supposedly you can update from LTS to LTS, otherwise you will have to update from one version to the next in steps.

8.04-->8.10-->9.04-->9.10-->10.04

---

### Post by excogitation on 2009-11-06
is the upgrade supposed to remove ubuntu-desktop?

ah ... what the heck ... I'll join the ride (better late than never) ... only a virtual machine anyways ;-)

---

### Post by LKjell on 2009-11-06
> **excogitation said:**
> is the upgrade supposed to remove ubuntu-desktop?

ah ... what the heck ... I'll join the ride (better late than never) ... only a virtual machine anyways ;-)
There was a partial upgrade today. Guess you just had bad luck.

---

### Post by zika on 2009-11-06
For some reason (unknown to me, probably the fear that I will not be able to use FF 3.6 and 3.7 that I grown accustomed to) I've waited to toolchain to upgrade. When can we expect toolchain?

---

### Post by slakkie on 2009-11-06
I believe the toolchain came Nov 5th or maybe Nov 10th... I forgot :(

---

### Post by jppr on 2009-11-06
> **zika said:**
> For some reason (unknown to me, probably the fear that I will not be able to use FF 3.6 and 3.7 that I grown accustomed to) I've waited to toolchain to upgrade. When can we expect toolchain?

toolchain updated yesterday

---

### Post by zika on 2009-11-06
> **jppr said:**
> toolchain updated yesterdayBut, when I try **update-manager -d** in CLI I do not get any distribution upgrade ...

---

### Post by ranch hand on 2009-11-06
Edit your /etc/apt/sources.list replacing all instances of "karmic" with "lucid".

Run;
```

sudo apt-get update

```
Then
```

sudo apt-get dist-upgrade

```
And there you will have it.

---

### Post by DougieFresh4U on 2009-11-06
> **zika said:**
> For some reason (unknown to me, probably the fear that I will not be able to use FF 3.6 and 3.7 that I grown accustomed to) I've waited to toolchain to upgrade. When can we expect toolchain?

Using 3.7 on a Lucid 32 bit and on my 64 bit

---

### Post by zika on 2009-11-06
> **DougieFresh4U said:**
> Using 3.7 on a Lucid 32 bit and on my 64 bitTotally off-topic: Did You loose Private Browsing and Undo close Tab in daily updates of 3.7? I had power outage once I was in 3.7 and after that I do not have those features. Not that need PB but UcT is kind off important ...

---

### Post by zika on 2009-11-06
> **ranch hand said:**
> Edit your /etc/apt/sources.list replacing all instances of "karmic" with "lucid".

Run;
```

sudo apt-get update

```Then
```

sudo apt-get dist-upgrade

```And there you will have it.I know that, we've talked about that days ago. I'm asking when it will be possible to do:```
~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found
```

---

### Post by jppr on 2009-11-06
i think that you can do it alpha 1, i´m not sure but i think so...  = )

---

### Post by zika on 2009-11-06
> **jppr said:**
> i think that you can do it alpha 1, i´m not sure but i think so...  = )OK, I'm on Lucid ...
What is the verdict on:```
~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-x11 
  pulseaudio-module-zeroconf{a} pulseaudio-utils 
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```are we waiting for rtkit or what?

---

### Post by Foaming Draught on 2009-11-06
> **jppr said:**
> sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

Thanks jppr, that's what I did yesterday and everything's fine (I changed my virtualbox repository back to Karmic).

Firefox 3.6 beta1 has installed well.  I'm a happy bunny.  I couldn't stand the thought of waiting until Dec 10 to get my daily fix of updates and crises.

---

### Post by shakaran on 2009-11-07
I'm in. Let's rock!

---

### Post by ComputerJy on 2009-11-29
The do-release-upgrade didn't show any changes but I'm getting lucid in system properties. Is it normal to still have the karmic kernel?

---

### Post by jppr on 2009-11-29
> **ComputerJy said:**
> The do-release-upgrade didn't show any changes but I'm getting lucid in system properties. Is it normal to still have the karmic kernel?

2.6.32-5 is lucid kernel ;)

---

### Post by ComputerJy on 2009-11-29
> **jppr said:**
> 2.6.32-5 is lucid kernel ;)
I knew that. I just am wondering why it still shows Karmic in the About ubuntu dialog.
I guess I didn't say that :P

---

### Post by jerrylamos on 2009-11-29
Upgrade to Lucid?  

Watch Out on Upgrades!  They've burned my @#$% a number of times.

Much better for me to define another partition, even 5 GB will do, and install from a .iso downloaded from daily build:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

Once you have a lucid .iso you can readily use rsync to keep it up to date

Code[

rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/lucid-desktop-i386.iso .

rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS .

md5sum jaunty-desktop-i386.iso >> MD5SUMS

less MD5SUMS

]EndCode

That way when lucid breaks (past alpha's & beta's do frequently) you still have your original running linux.

Jerry

---

### Post by VMC on 2009-11-29
> **jerrylamos said:**
> Upgrade to Lucid?  

Watch Out on Upgrades!  They've burned my @#$% a number of times.

Much better for me to define another partition, even 5 GB will do, and install from a .iso downloaded from daily build:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

Once you have a lucid .iso you can readily use rsync to keep it up to date

Code[

rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/lucid-desktop-i386.iso .

rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS .

md5sum jaunty-desktop-i386.iso >> MD5SUMS

less MD5SUMS

]EndCode

That way when lucid breaks (past alpha's & beta's do frequently) you still have your original running linux.

Jerry
Jerry, This sounds like a clever way to keep upgraded. Thanks for the tip. 

So this keeps your daily current?

---

### Post by ranch hand on 2009-11-29
I would like an answer to that too.

The reason is that I used it during the last testing round and it never, ever upgraded a kernel.  Everything else but not the kernel.

I just did not see the point and quit using it.

---

### Post by autocrosser on 2009-11-29
Shoot--I just have two installs of the current testing system---1 "main" install that I do the normal updates with & a backup install that is updated weekly at "safe" times...I've needed to boot into my safe backup a couple of times in the last few years--I spin 1.5TB worth of drives...so I setup the two installs on different drives in case of drive failure & sync my /home(s) at the same time---also keep a USB2 drive loaded as a insurance policy in case of system failure....pays to have all the bases covered.

---

### Post by VMC on 2009-11-30
> **jerrylamos said:**
> Upgrade to Lucid?  

...
[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

...

I noticed there are "zsync" files also on that link you provided for the daily updates. I found these files are a way to also keep updated. Anyone know about using the "zsync"?

Here is a [link]("http://lifehacker.com/5393555/use-zsync-to-upgrade-an-ubuntu-installation-image") on the subject.

---

### Post by Kraust on 2009-11-30
I updated with the mentioned guide (Changing repos and dist-upgrading) and I've had 0 issues thus far.

Hopefully, this version will have something to bennefit my old computer.

---

### Post by zika on 2009-12-01
> **VMC said:**
> I noticed there are "zsync" files also on that link you provided for the daily updates. I found these files are a way to also keep updated. Anyone know about using the "zsync"?
Here is a [link]("http://lifehacker.com/5393555/use-zsync-to-upgrade-an-ubuntu-installation-image") on the subject.On the link You gave there is [tutorial](http://ubuntu-tutorials.com/2009/10/29/use-zsync-to-update-existing-iso-images/).

---

### Post by dziki on 2009-12-01
> sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade
sed rules! thank you bud :-)

---

### Post by Gina on 2009-12-01
Thank you for the info on zsync :)  I use rsync ATM - I'll take a look at zsync :)

---

