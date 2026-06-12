---
title: "Stuck in unsupported distro upgrade ... from 12.04 to 12.10 and stuck."
date: 2014-07-01
forum: Installation &amp; Upgrades
---

### Post by randomas on 2014-07-01
Hallo, I finally gave in to upgrade my 10.04 installation that was working very well but got ancient and most of the ppa stuff I used was unsupported or not working anymore. 

I first upgraded to the next LTS version (12.04) and that worked without issues, from here I tried to go to the next LTS (14.04), but it wasn't having it so opted to just move to the next one up 12.10 which it did. 
Little did I know that 12.10 is deprecated and so is 13.04, so now my upgrade path tries to jump to 13.10 (skipping 13.04) and fails. I am unable to try and upgrade to 14.04 as it doesn't seem to be an option. 

Is there a way to force upgrade to the next (even if deprecated) version (in my case 13.04)?

TIA

---

### Post by sudodus on 2014-07-01
At the first point release 14.04.1 LTS, I expect that there will be a well debugged upgrade method from 12.04 LTS. This will be soon, I think within 4-6 weeks from now.

I would recommend that you stay with 12.04 LTS at least until then, but the LTS flavours of 12.04 will be supported for a longer time (Xubuntu until April 2015, standard Ubuntu and Kubuntu until April 2017), so there is plenty of time to wait until 14.04 LTS will be well debugged and polished.

-o-

Since you are coming from 10.04 LTS, I think you already know that this is the idea with the long time support (LTS) versions: use them for your production machines unless you really need some new feature of the very last version.

---

### Post by bapoumba on 2014-07-01
Any reason why you did not go with a fresh install ?
Have you backed up all your important data ?
Is there any other OS on this machine ?
Will its specs be good enough for the standard Ubuntu 14.04 (ie have you considered lubuntu or xubuntu ?)

Going to 13.04 is not something I would advise as 1- it is EOL (as you already know) and 2- the repos are not on the main ones anymore, but on the old-releases here : [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by randomas on 2014-07-01
My issue is that unfortunately I'm already stuck with 12.10 (unsupported), because 12.04 was happy to upgrade to it and I assumed that from there I'd be able to step stone up to 14.04. So I really need to get up to 13.04 so I can move up to 13.10 and then finally 14.04 ... 

The reason I don't want to do a fresh install is that I've got a complicated system with 3 osses (windows7 and 2 linuxes sharing the same home partition), making it a pretty nasty grub nightmare, also the initial procedure to get the hardware working on this laptop were a little complicated and I don't know if I have them archived... :( 

is there any way to get this to work, I remember that on debian I used to brute force change the software sources (put the oldreleases sources for 13.04) and then just update and dist upgrade ... Any reason not to do this?

---

### Post by bapoumba on 2014-07-01
> **randomas said:**
> 
is there any way to get this to work, I remember that on debian I used to brute force change the software sources (put the oldreleases sources for 13.04) and then just update and dist upgrade ... Any reason not to do this?
You sure could, using the old.releases. But 13.04 > 13.10 > 14.04 is may be going to get difficult with your particular set up, re: the hardware issues.

Which hardware is giving you problems ? I may not be able to help you with that, but others will.

One additional thing, if you :

```
cat /etc/fstab
```
and write down your partition setup, you can choose "do something else" with the graphical installer, and reinstall Ubuntu on the partition you choose. I'd do that :)

---

### Post by sudodus on 2014-07-01
I think it is *very* risky to upgrade a system sharing the home partition with another system. Please check if the other linux system is still working, and if that is the case, I suggest that you ***backup*** as much as possible, the whole drive or at the very least all your important personal files.

The next step I would suggest is to make a clean installation of Ubuntu 12.04 LTS without sharing the home partition, but with a good backup you can also make a fresh installation where you select the current home partition for it. It might turn out well. You lose some general system settings and tweaks, but those belonging to the user account (in the home folder) might still work.

---

### Post by randomas on 2014-07-01
The issue is the asus ul30v laptop hybrid graphics pre optimus that now works with bumblebee (had stopped working in 10.04), but most of the special keys and other stuff I can't remember needed "special attention"... Then there's all my special interest libraries and programs that would need setting up again and ... oh the pain of it ... :(

If I reinstall I'll just do the single partition thing and then delete the home directory and fix fstab ... :p

Oh yes the other 10.04 system is still working (it just messed the favourited programs in the menu...) ;)

---

### Post by sudodus on 2014-07-01
Please backup your system now, and you will have peace of mind while testing further options.

I think there can be conflicts if you use the same home directory for one 12.04 system and one 10.04 system. If there is space enough, it might be better to clone /home and have separate home partitions for the two versions. An alternative is to have a ***common data partition*** with your personal files, while the system settings (in most hidden files) are separate. You can have symbolic links to easy access to the data partition.

---

### Post by Bashing-om on 2014-07-01
randomas; Hi !

+1 to the aboves, and in particular as sudodus advises. I quadruple boot 'buntus on my system and have a separate "data" partition I share with all. I have never had a problem doing so. Then there is also the means to mount any partition to the files system - on the fly - as the occasion should require.

How bout this for a thought, set up an additional partition to clean install 14.04, get it all fine tuned to your specifications before removing those End-Of-Life releases. As the legacy partitioning is limited to 4 primary partitions, some prior prudent planning might be in order. As a hint I always keep 50 gigs of 'unallocated' space for times such as this, can sure come in handy.

What ever course you choose, we are here to assist .. though making the on-line upgrades is fraught with perils, it can be done. There is a lot of time and effort and bandwidth involved, and then there is the time and aggravation to fix any problems that may result in that upgrade process.

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by randomas on 2014-07-01
The original plan was to upgrade this partition to 14.04 see how it went and then move the other one up once I was happy with it ... I missed the memo that said there was no path from 12.04 to 14.04 yet ... :mad:
I'm already quite pleased that the home settings didn't go to hell moving up from gnome 2 to gnome 3/shell/unity ... 
Unfortunately there's no room for any more partition splitting so I'm just going to have to give stuff a good backup... I could just comment the home partition out of fstab and then pull it back in after the damage ...   

So no big "No, no don't do that!" to changing the sources list to old-release 13.04 update and upgrade?:twisted:

Time to update my home backup then ...

---

### Post by bapoumba on 2014-07-01
Sorry I missed the sharing /home between 2 linux installs (are these both Ubuntu ?). You already have been living on risky grounds :)
I personally have the /home in the root tree, with 2 separate storage areas that I do not format should I fresh install. All my stuff is in there. For a long time I used to have a separate /home and one /storage, but not any longer.

I'm not sure I understand the *I could just comment the home partition out of fstab and then pull it back in after the damage ...* part.

You wont be able to upgrade with a package manager without a /home as far as I understand it (if I am mistaken, I'd really like to know). If you fresh install to an existing partition, either your point at a pre-existing /home and say to not format it (and use it as /home) or you say nothing and this install will have a /home in the root partition.

Please save anything that is of value to you in any case.

---

### Post by randomas on 2014-07-01
I'm running a full backup of mu home partition as we speak ... ;)
I was using a common home for twin installs one was regular work the other had 3d stuff I used to have to change a bios setting to get the nvidia card working and ubuntu would not, let's say, alternate gracefully. :lolflag:
Then came bumblebee that fixed (sort of) things. 
What I mean by the fstab thing is comment the home mountpoint from fstab reboot recreate a home environment (logging in should be sufficient) and do the update, delete and uncomment fstab ... Should be able to upgrade without a home too though. 

My fear is what an ubuntu distro upgrade entails, with debian (a long time ago admittedly) I would just change the sources update, upgrade and work my way through the conflicts, but there were no config scripts running during the upgrade process, I wonder if this is still the case with ubuntu, i.e. if all the scripts are contained within the dpkg package upgrade process or whether the upgrade manager does some crucial stuff behind my back as well.

---

### Post by sudodus on 2014-07-01
I don't know the details of the upgrade manager, but I know that the success rate is higher for fresh installs compared to upgrades between versions, talking about

```
do-release-upgrade
```

[COLOR=#696969]not

```
apt-get update && apt-get dist-upgrade
```[/COLOR]

---

### Post by bapoumba on 2014-07-01
For any upgrade (regular or adventurous), you should deactivate any third party repo or ppa you are using. Only keep regular ubuntu repos, main, restricted, universe, multiverse, with updates and security, but no backports or proposed either. Then change your sources.list, update and dist-upgrade, probably several times in a row (the update/dist-upgrade cycle) as we used to do in the old days until everything has pulled through. Absolutely SGDG.

(with the old.release repos, I'm not sure the do-release-upgrade will work sudodus. Will it ?)

---

### Post by sudodus on 2014-07-01
do-release-upgrade might not work, I have not tested it with old.release repos. I agree, your manual method is more likely to work, bapoumba. Anyway, the preparation to get a clean and well updated system without ppas etc increases the success rate.

---

### Post by bapoumba on 2014-07-01
I'd even do it from one of the virtual terminals, no GUI, but that is just me :)

---

### Post by randomas on 2014-07-01
Oh ok I hadn't thought about proposed and backports, thanks. 

do-release-upgrade won't work because it won't see 13.04 as a regular update ... I'm hoping it just changes the sources list and runs update upgrade and doesn't do any other odd stuff I don't know about ...

---

### Post by randomas on 2014-07-02
Ok, I'm a little surprised and confused now, I just noticed that 13.04 IS NOT deprecated... So why does update manager not see it as the next upgrade and try and push me to 13.10 (that doesn't work)?

---

### Post by randomas on 2014-07-02
Ok forget that, it is deprecated ... just hit an official page that didn't have it listed as such...

---

### Post by bapoumba on 2014-07-02
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) :)

---

### Post by randomas on 2014-07-03
OK I win! :guitar:

Using the old manually switch sources in the apt sources list trick worked and updated to 13.10 from there I just did the regular upgrade. 

Now I'm here, I must say that 12.04 gave me a better first impression, but it's early days yet. Thanks for the help. 

For anyone else reading this DO NOT ATTEMPT TO UPGRADE FROM 12.04 unless they have fixed the upgrade path.

---

### Post by bapoumba on 2014-07-03
Ah good, I was sure you would succeed.
One additional thing to make it total win : please mark your thread as solved (under Thread tools), thanks :)

---

### Post by sudodus on 2014-07-03
Congratulations :KS

I agree with your advice to avoid this long and cumbersome upgrading path, even if you proved it is possible. Please wait until 14.04.1 (the first point release) in the end of July or beginning of August, when we can expect there will be a tested and debugged method to upgrade directly from 12.04 LTS to 14.04.1 LTS.

Finally, please click on **Thread Tools** at the top of the page, and mark this thread as SOLVED.

---

### Post by Bashing-om on 2014-07-03
randomas; Great !

I too am pleased you made the transition !

pressing  on
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

