---
title: "Hardy Upgrade...stuck."
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by panagioti on 2008-07-16
Hi,
I was upgrading to Ubuntu 8.04 from Ubuntu 7.10 and ran into an issue. I was attempting to perform the upgrade via network. Everything download, extracted and began installing. However, it seems to get stuck at installing "locales". I stopped the install(it was suck there for at least 30 minutes) and reran "dpkg --configure -a". But it keeps getting stuck at installing locales and "locales" is chewing up most of the CPU while it's doing this. Running apt-get update and apt-get upgrade just brings back the same message"

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

How should i proceed?

Again,
running "dpkg --configure -a" just gets stuck at:

# dpkg --configure -a
Setting up locales (2.7.9-4) ...
Generating locales...
  en_CA.UTF-8...

....and it just stays there...please help.

---

### Post by shanek on 2008-07-16
I was searching for the solution of the same exact problem, and found this thread. Any ideas anyone?

I'd really prefer not to do a fresh installation, since I'd have to set up a dozen different users all over again. (and get them to come up with new passwords, etc)

---

### Post by hurlements on 2008-07-16
We have the same problem here :

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1932000](http://forum.ubuntu-fr.org/viewtopic.php?pid=1932000)

I might suggest a solution, but it brings new problems, so...
And for me, the configuration is stuck some times after the locales, now.

I tried 

echo 'locales hold' | sudo dpkg --set-selections
dpkg --configure -a

But, as I've just said, I'm not sure it may work.

Now we are 5 to face this problem. At least.

---

### Post by JRPettus on 2008-07-16
> **hurlements said:**
> We have the same problem here :

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1932000](http://forum.ubuntu-fr.org/viewtopic.php?pid=1932000)

I might suggest a solution, but it brings new problems, so...
And for me, the configuration is stuck some times after the locales, now.

I tried 

echo 'locales hold' | sudo dpkg --set-selections
dpkg --configure -a

But, as I've just said, I'm not sure it may work.

Now we are 5 to face this problem. At least.

Make that six.  I got to that point and it hung.

---

### Post by MarkX on 2008-07-16
Mine hung on locales too, and the alternate now hangs on openoffice.org-core. Tried using different hard drives as well.

---

### Post by wpshooter on 2008-07-16
Glad I am still on Gutsy. :)

---

### Post by cal6n on 2008-07-16
Add another one stuck at "generating locales"

This time while updating a G3 pismo...

Any ideas? It looks like this is quite common.

---

### Post by Bluztrvler on 2008-07-16
Me too!

---

### Post by Dante444 on 2008-07-16
Same here! It's stuck at:

Setting up locales (2.7.9-4) ...
Generating locales...
en_AU.UTF-8...

---

### Post by SGreth on 2008-07-16
Anybody have any workarounds for this? I'm upgrading from 7.10. I tried to kill -9 the localedef process but it seems rather invincible. It isn't a zombied process (top shows it as running) so I'm not sure why it won't die.

---

### Post by SGreth on 2008-07-16
Alright, no clue how detrimental this will be to my install but killing this process seemed to keep the install going:

root     11709  0.0  0.0   1772   316 pts/1    S+   19:47   0:00 /bin/sh /usr/sbin/locale-gen

---

### Post by ssamoon on 2008-07-16
same problem here.

i found and killed that process (use 'ps aux' and 'sudo kill <ID>' for anyone who doesn't know how in terminal), got a lot of 'package not configured' errors afterwards, say about 20, for everything from something like en-language-pack to ubuntu-minimal.

hope everything ends up working OK.

---

### Post by rsay on 2008-07-16
I'm also stuck at the same point. I was waiting for these kind of kinks to get worked out before I upgraded. Oh well... 

Has anybody filed a bug?

---

### Post by Kiwi Jono on 2008-07-16
Me Too!!

Must be something new as I had a good look at forums before starting upgrading and could not find any big issues.

---

### Post by n8gray on 2008-07-17
Come on, *somebody* must have a solution!

Has anybody filed a bug?

---

### Post by Kiwi Jono on 2008-07-17
Damn - mine when even more pear shaped. Further through the process started doing the same step again (some sort of dependancy I think) and this time nothing seemed to work.

Ended up with a corrupt install and now doing a fresh install :-(

---

### Post by n8gray on 2008-07-17
I just filed a launchpad bug on this:

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

---

### Post by hurlements on 2008-07-17
We may have the solution here (on the french forum).

Just reboot, but don't choose the upper choice proposed
by grub. Take another one, not in recovery mode.

Wait for the login screen, then ctrl+alt+F1
and log in.

Then make

sudo apt-get dist upgrade (but I'm not sure this is necessary)

then :

sudo dpkg --configure -a

and for me everything is fine. Still this is a big bug...

---

### Post by Voland on 2008-07-17
I have same problem too. *sudo killall locale-gen* is a way to proceed upgrade, but I think there is another way to solve this problem.
UPD: Workaround is
Use *sudo killall locale-gen* every time when Setting locale appears. Then reboot in recovery mode and choose "Dpkg-fix broken packages"

---

### Post by behda on 2008-07-17
I had the same problem on two different machines while updating from kubuntu Gutsy to Hardy. For me it did not help to kill the process. It was not possible to kill localedef at all with 

kill -9 <pid>

The only working solution was killing the update and ignoring the running localedef process followed by:

rm /usr/bin/localdef

and

dpkg --configure -a

at least it was possible to renice localedef to speed up the real update. After the completed installation and reboot I reinstalled

belocs-locales-bin
locals

and everything worked.

---

### Post by Bluztrvler on 2008-07-17
Thanks to herlements:  This worked for me.

We may have the solution here (on the french forum).

Just reboot, but don't choose the upper choice proposed
by grub. Take another one, not in recovery mode.

Wait for the login screen, then ctrl+alt+F1
and log in.

Then make

sudo apt-get dist upgrade (but I'm not sure this is necessary)

then :

sudo dpkg --configure -a

and for me everything is fine. Still this is a big bug...



Seems that running dpkg --configure-a   outside of X works.  I still have issues with my desktop, but at least it boots.

---

### Post by panagioti on 2008-07-17
Thanks for all the replies.....I didn't realize the bug was this bad! Anyhow, this worked for me as well:

rm /usr/bin/localedef

and

dpkg --configure -a


I now have a broken locale definition, but at least the upgrade process is more or less completed. Now ... on to fixing the locales!

---

### Post by tm.winston on 2008-07-17
I had the same problem on Ubuntu Server, upgrading from 7.10 to 8.04.  I used the "killall locale-gen" method.  After updating everything else and rebooting, I ran "apt-get upgrade" and it seems to have correctly configured this system's locale information.

Does anyone know how to check, for sure, that the locale information is correctly configured?

---

### Post by shanek on 2008-07-17
Ok, I got it more or less figured out from these posts and the ones over at the launchpad bug report.

First, either somehow kill locale-gen or reboot.

```
chmod 744 /usr/bin/localedef 
dpkg --configure -a
reboot
chmod 755 /usr/bin/localedef
apt-get dist-upgrade
dpkg --configure -a
```

The first dpkg --configure -a worked and finished what needed to be done just fine, but generated a bunch of locale related error messages. A few packages wouldn't configure properly either. The main thing is to get the kernel in place so you can reboot into the new kernel. 

Once you've rebooted, you can make localedef executable again (chmod 755) and most of the packages should configure.

After the last dpkg command, I still had problems with timidity and no-ip. Timidity was fixed by using apt-get to remove and install it. Still working on no-ip. 

Otherwise, we're moving on just fine. Thanks for the help everyone!:guitar:

---

### Post by jasond496 on 2008-07-17
Just chiming in...

I finally had the time (I thought) to update our Ubuntu server here at work, but ran into this bug today.

I was able to get it fixed mostly using the information in this thread, *except* that I had to re-generate en_US.UTF-8.  Simply running ```
$ sudo locale-gen en_US.UTF-8
``` didn't work, I had to run ```
$ sudo locale-gen --purge en_US.UTF-8
``` to get the error messages to go away.

Now all seems to be well.

---

### Post by tm.winston on 2008-07-17
Confirmed on a second server upgrade from 7.10 to 8.04.  After killing the process, finishing upgrading everything else, and rebooting I was able to finish the update successfully and both machines appear to be functioning well.

---

### Post by jeffhbk on 2008-07-18
I was able to use the following workaround.

1) restart to the login screen
2) select options
3) change language to English (Canada)
4) Just for this session
5) Then run dpkg --configure -a from terminal

worked for me....

---

### Post by bjornolai on 2008-07-18
I seem to be stuck on this one. I tried removing locales, (dpkg -r locales) in order to have dpkg set up the remaining packages. It sort of worked. However with dpkg returning a lot of dependency errors. The problem now seems to be that I can't reinstall locales because it just hangs as before. Rebooting was not a good idea as I can't get back into X (can't really tell what's wrong there but the screen is all scrambled). 

I'd really appreciate any clue as to how I may reinstall locales.

Or maybe this is a good opportunity for a fresh install :)

***
Update: X up and running after fixing xorg-config (problem not related to locales :) Still working on the locales issue, but of some unexplained reason it seems to be going the right way after logging in to X.

---

### Post by jamoo1980 on 2008-07-18
To re-install locales do:

```
sudo locale-gen --purge en_GB.UTF-8
```

...or whatever locale you want. Because I'd previously removed the entire /usr/sbin/locale-gen folder in order to get the Hardy upgrade to work (see above) I first had to use Synaptic to re-install the belocs-locales-bin package.

I seem to have my system upgraded to Hardy now. Hope this helps.

---

### Post by alecz20 on 2008-07-18
> **wpshooter said:**
> Glad I am still on Gutsy. :)

Using Gutsy here and when I tried to add another language I got into the same problem. This is not only limited to the Upgrade, try adding another language and you'll join the group.

Btw, I still haven't read the whole thread... working on it.

---

### Post by alecz20 on 2008-07-18
> **behda said:**
> 
...
rm /usr/bin/localdef

and

dpkg --configure -a

The above worked and restored my system to being able to install stuff.

However...
> **behda said:**
> 
at least it was possible to renice localedef to speed up the real update. After the completed installation and reboot I reinstalled

belocs-locales-bin
locals

and everything worked.

This only caused it to hang again when installing locales.

THIS IS STILL A BIG ISSUE. I lost all localization on my system and can't get it back in any way.:(

---

### Post by Llewxam on 2008-07-19
well great... i'm also stuck on this. T_T tried the various work arounds in here and none have helped. still stuck on generating en_AU.UTF-8. 

....why didn't i follow my gut and not upgrade!

please ignore. got it running now.

---

### Post by n00bWillingToLearn on 2008-07-19
If you would like to help get this problem solved the Ubuntu devs are asking for information, specifically the log files from
 /var/log/dist-upgrade/

Here is a link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/)

And there are probably going to be other requests in the future as well so come back to it if you can.

---

### Post by hedonplay on 2008-07-19
Thank you all.
I hope it works.

---

### Post by punkybouy on 2008-07-19
I can't run the apt-get upgrade because it says I have to run the dpkg --configure.  I can't do that because it hangs up generating en_AU.UTF.8.  Anybody got any ideas?

---

### Post by punkybouy on 2008-07-19
Here is what worked for me and a "hardy" (get it?)  Hardy, thanks to all.  First some background.  I used the alternate CD that I burned in April.  I ran the upgrade from the X desktop by inserting the CD and choosing upgrade from the autorun popup screen.  The fix for me was:
1 start PC and let it load to X login screen (after getting X setup popup and choosing continue)
2 do a ctrl+alt+F1 and get to terminal and login.
3  sudo rm /usr/bin/localedef
4  sudo dpkg --configure -a
5 let upgrade finish and when back to the prompt "reboot"


Seems to work fine now.  Hope this helps.

---

### Post by punkybouy on 2008-07-19
Thanks behda!

---

### Post by alecz20 on 2008-07-19
> **n00bWillingToLearn said:**
> If you would like to help get this problem solved the Ubuntu devs are asking for information, specifically the log files from
 /var/log/dist-upgrade/

Here is a link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/)

And there are probably going to be other requests in the future as well so come back to it if you can.

I don't know if you read my comment on that bug report, but this issue is not limited to upgrading the OS. The issues has something to do with the Language Support.

Anyone can easily reproduce this bug without upgrading. This can be done by simply adding another language via System->Administration->Language Support.

After you click OK, you will notice the hang (hint: press Details to see where it hangs)

---

### Post by ReelExterminator on 2008-07-20
I've finally got my computer sorted out. After cancelling out of the upgrade, the newest kernel wouldn't boot because the initrd hadn't been successfully created. I'm not sure if this was directly related to the locale generation issue or whether it just got messed up in the process of dpkg having packages fail installing. In any case, booting the second-newest kernel in recovery mode and running dpkg --configure -a fixed the kernel problem, but with the same locale generation issue. Rebooting and booting the latest kernel and running dpkg --configure -a again got the locales generated without a problem. Are people having trouble generating locales under 2.6.24-19?

---

### Post by Dscottmc7 on 2008-07-20
Yup, I got stuck in Ubuntu Studio on Dell Inspiron also.

Setting up locales (2.7.9-4) ...
Generating locales...
en_AU.UTF-8...

Finally had to reinstall via live CD.  No options...

Anyone yet?

Also, on HP-Desktop, upgraded to Hardy, hung same place...
Now boot generic.  Afraid I'll wipe out data until I back up my files
so no booting rt for now...
BTW, Studio (Audacity 1.3.4 from Synaptic) has v19 PortAudio-- does not show the Audio I/O Controls.  v18 PortAudio, (earlier stable release) works, but that requires deletion of Ubuntu Studio audio...aw well...

hang in there...

---

### Post by behda on 2008-07-21
> **alecz20 said:**
> The above worked and restored my system to being able to install stuff.

However...


This only caused it to hang again when installing locales.

THIS IS STILL A BIG ISSUE. I lost all localization on my system and can't get it back in any way.:(

Did you reboot to the new kernel? Before a completed upgrade and reboot I got the same behaviour. Now tested on three different systems with hardy I can even remove all locales:

sudo mv /usr/lib/locale /tmp/     # just for backup

and regenerate them again with:

sudo aptitude reinstall belocs-locales-bin
sudo aptitude reinstall locales   # sorry for the typo before

Hope that helps...

---

### Post by ishields on 2008-07-21
When mine stuck, I was able to continue by running
dpkg -r -a
before running
dpkg --configure -a
(Prefix these with sudo if you're not in a root shell).

The install appeared to pick up where it left off. I didn't have to delete any directories or kill any processes, other than the initial reboot after the system got stuck.

dpkg -r -a simply removes all packages that are pending removal and is probably a lot less brutal than some of the other methods suggested here.

---

### Post by breadbaps on 2008-07-22
yet another one stuck...this time at en_AU.UTF-8.Should I exit program and hope the problem resolves?

---

### Post by alecz20 on 2008-07-22
> **behda said:**
> Did you reboot to the new kernel? Before a completed upgrade and reboot I got the same behaviour. Now tested on three different systems with hardy I can even remove all locales:

sudo mv /usr/lib/locale /tmp/     # just for backup

and regenerate them again with:

sudo aptitude reinstall belocs-locales-bin
sudo aptitude reinstall locales   # sorry for the typo before

Hope that helps...

First of all, I never upgraded to Hardy. This hang happened to me when I wanted to add another language.

I tried to re-install locales and belocs-locales-bin using synaptic and the same hang occurred!

I also booted with the older kernel and got the locales file figured out, now I have the proper language in the file but still no default system language. This is fine for now, but how can I have multiple language support in Ubuntu then?

---

### Post by travv0 on 2008-07-22
I had the same problem, so I rebooted, and now my desktop is KDE and I have no idea how to use it.

---

### Post by calvert888 on 2008-07-23
Just ran into this problem today on my machine while upgrading to Hardy. After it had sat there trying to do the locale gen for a few hours I ran:

```
sudo killall locale-gen
```

This produced several errors, then it got hung trying to do it again a few minutes later, and I had to run the killall cmd again.

Then after a reboot ran:

```
sudo locale-gen en_US.UTF-8
```

Mine seems to be fine, but I don't really know how to check to make sure. :-/

---

### Post by ukripper on 2008-07-28
i had the same problem while upgrading to 8.04.1 server.

What i did was:
```
sudo killall locale-gen
```

updates carried on and then got the same message en_GB.UTF8...

then i just logged into ssh from another machine and 
```
sudo reboot now
```

After reboot at login prompt-
```
sudo dpkg --configure -a 
```

and then 
to check 
```
sudo locale-gen en_GB.UTF-8
```
change GB to US if you are in US or to your local language.

---

### Post by IwasAnex on 2008-07-28
This appears to be a recurring problem and I am sure the devs are working on it. There are solutions/work arounds in this thread  [HTML]http://ubuntuforums.org/showthread.php?t=861384[/HTML] 
Most are variations on a theme but it helped me when I was stuck in the same spot. 

Good Luck

---

### Post by themoebius on 2008-07-30
EDIT: yeah, I spoke too soon I guess. Before locale-gen just wasn't doing anything, but when I stopped GDM it at least started using all my CPU so I figured it was doing something, but after a few hours it hadn't gotten anywhere. I did a rm /usr/bin/localedef and then reinstalled locale with apt-get --reinstall install locale.

---

### Post by ukripper on 2008-07-31
> **themoebius said:**
> Yeah the problem seems to be when you try to upgrade from within a GDM session (a graphical interface). When I switched to a terminal by pressing Ctrl + Alt + F1 and shut down GDM but sudo /etc/init.d/gdm stop and then made sure it wasn't still trying to generate locales by doing pd -ef|grep locale, then I could finally run the upgrade and it would actually do the work. It still takes a while to generate the locales, but you can tell its working by switching to another terminal (Ctrl + Alt + F2) and running the command 'top'. You should see that localedef is using all your CPU power so its actually working now.

I don't run GDM or any graphical interface on my server, but I still had that problem! This problem is more related to locale-gen configuration I believe while upgrading.

---

### Post by Aiello on 2008-07-31
Well, another one stuck on the same spot here. Unfortunatly, I haven't been able to find a work around that works for me yet! upgrading Ubuntu 7.10 desktop 32 bit.

---

### Post by alecz20 on 2008-07-31
> **travv0 said:**
> I had the same problem, so I rebooted, and now my desktop is KDE and I have no idea how to use it.

[http://spread.kde.org/files/kde35screenies.pdf](http://spread.kde.org/files/kde35screenies.pdf) (Right Click and save Link as)


On the other hand... is there ANYONE that upgraded to hardy and DID NOT get stuck?

I am curious because I think of new users... when they see it hangs they get... disappointed.

---

### Post by Aiello on 2008-07-31
Well, after letting the upgrade sit for a few hours, it crashed and closed its self... I had to boot in recovery mode and select fix broken packages. Every thing appers to be okay now, as I am running hardy. But, it seems alot slower than gutsy was and there are a couple bugs. I am just glad the upgrade didnt' completly kill my compy!

---

### Post by groundpounder on 2008-07-31
yep... mine got stuck too.  I've been running ubuntu for 3 years now.  I've had enough of this garbage. I'm going back to SUSE (ok, openSUSE now).  Good luck to the rest of you.

---

### Post by Blinky981 on 2008-07-31
> **groundpounder said:**
> yep... mine got stuck too.  I've been running ubuntu for 3 years now.  I've had enough of this garbage. I'm going back to SUSE (ok, openSUSE now).  Good luck to the rest of you.

Yet another disappointed customer. This is the second time I've tried installing in two days and the second time it's hung on generating locales. I haven't tried any of these workarounds yet, and don't fancy the look of some. When I do, however, I will post the outcome.

As you said though, if nothing works I may just go back to my six-disc OpenSUSE 10.2 installation...  The discs are a couple years old now so I dread to think how many upgrades that would need.

This bug is beginning to try my patience. Every time I upgrade I have to use 700 megs of my bandwidth, and the install disc I have is for 7.04. So for two upgrades to 7.10 and two (so far failed) upgrades to 8.04, that totals about 2.8GB... Who's going to pay for the bandwidth if my ISP gets fussy? And the electric bill too, come to mention it.

Is there any way I can just roll back the install? When it hung yesterday (before I bothered to check on here) I thought a restart might do the trick , only to find it wouldn't boot into a usable GUI... Of course, I didn't think about terminal. My bad.

Saying that, however, I am now wary about restarting the computer at all. I'm posting this from my laptop - which runs Windows.

If it has been three or four months since the release, can anyone make a realistic guess as to how long it will take to kill this bug?


Anyway, I guess I should actually try to work this out. If anyone finds a guaranteed-working workaround in the mean time, let me know.

---

### Post by Llewxam on 2008-07-31
i can testify that even though i was also stuck on the same bug i tried out the workaround of rebooting and doing the reconfigure of packages from terminal. it worked great. 
...then again i managed to break the entire system after doing a stupid move and upgrading to the dev branch of intrepid then having to do a fresh install of hardy. have to say it works MUCH better than when i originally upgraded. hope it helps shine a ray of hope for the rest here. :D

---

### Post by Blinky981 on 2008-08-01
Update: I tried out a workaround involving killing the locale thing before restarting, Ctrl+Alt+F1, sudo apt-get update and sudo apt-get upgrade. After that I logged in  and although it seems to be okay, I'm having problems sharing folders over the network :confused:

---

### Post by Llewxam on 2008-08-01
> **Blinky981 said:**
> Update: I tried out a workaround involving killing the locale thing before restarting, Ctrl+Alt+F1, sudo apt-get update and sudo apt-get upgrade. After that I logged in  and although it seems to be okay, I'm having problems sharing folders over the network :confused:

have you tried enabling all the repos in synaptic then sudo apt-get update? samba seems to work a bit differently for me now. it mounts the folder i go into on the desktop

---

### Post by Blinky981 on 2008-08-01
> **Llewxam said:**
> have you tried enabling all the repos in synaptic then sudo apt-get update? samba seems to work a bit differently for me now. it mounts the folder i go into on the desktop

I pretty much have all the repositories switched on anyway so that I could get multiverse packages for mp3 support etc. but I'll list them here:

**Switched on**
Ubuntu Software: All 5
Third Party Software: Unsupported Updates and their source code are switched off
Updates: hardy-security and hardy-updates are **on**, proposed and backports are **off**


*Edit: I just checked samba and samba-common and both are said to be installed. They installed when I attemped to share a folder but I got some kind of error about applying permissions and setting user something-or-others. I've just reinstalled them both and will try sharing a folder again.*

---

### Post by Blinky981 on 2008-08-01
Ok a quick update. When I try to share a folder on the ext3 partition I get the following error:
```
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```

I'm not sure if this is related to the upgrade bug or not, but either way I haven't got a clue how to resolve it.


Edit:
It seems that only root and members of the sambashare group have rw access to the usershares folder. I'm gonna go check I'm in the samba group.

Second Edit:
Yes, I'm the only person in the sambashare group. Also, it may be worth noting that I have all available User Privileges... What other things would cause me to not have permission to create usershares?

---

### Post by ukripper on 2008-08-01
> **groundpounder said:**
> yep... mine got stuck too.  I've been running ubuntu for 3 years now.  I've had enough of this garbage. I'm going back to SUSE (ok, openSUSE now).  Good luck to the rest of you.

i am using opensuse on one of my box. It works ok but not as good as ubuntu/debian. Personally I don't like how YAST controls it all and package management is not as i expected. I am just using it with my cctv security camera through capture card which is only detected in kernel 2.6-25 +. Once intrepid is out I am back to ubuntu on that box as well.

---

### Post by obscenic on 2008-08-07
Same problem.. I'm just staring at it...

---

### Post by sklyer on 2008-08-07
This is probably not very helpful, but after getting stuck on Gusty when trying to install a new language, I decided to try my Hardy CD again. I was able to reinstall AND add French afterward without getting stuck. My CD is Hardy 8.04.1 (burned 7/16/08 ) so perhaps it preempted the current issue.

---

### Post by alecz20 on 2008-08-07
I found I had no problems if adding languages (and fixing my locales) using the old kernel (2.6.22-14).

I am pretty sure the upgrade will go smoothly if people upgrade from the old kernel rather than the new one.

It would be great if users could somehow be warned to reboot in the old kernel and do the upgrade to avoid ANY hassles with hangs!

---

### Post by candtalan on 2008-08-24
Stuck on locales too, here.

After *then* (too late!) seeing this thread, and waiting about 30 minutes, I pressed the machine reset button(!) to reboot

then
chose the second down choice of kernel (non recovery). I was not offered any gui so I logged in as  normal user and used
sudo dpkg --configure -a

this seemed to go ok  and left me with  still no gui. so I shutdown
sudo shutdown -h now
and rebooted normally and it seems to now be working.

This thread began a few weeks ago - I do hope it can be sorted soon. It will be bad news for newcomers.

---

### Post by ss339 on 2008-08-24
> **Dante444 said:**
> Same here! It's stuck at:

Setting up locales (2.7.9-4) ...
Generating locales...
en_AU.UTF-8...



I too am stuck on this.

anyone found the solution yet?

---

### Post by keinea on 2008-08-25
I've just recovered from my third failed attempt at upgrading my Gutsy to Hardy.

uname -a
Linux ubuntu2 2.6.22-15-generic #1 SMP Fri Jul 11 19:25:33 UTC 2008 i686 GNU/Linux

This Gutsy config is from a previous upgrade from Fiesty Fawn, which was the version installed initially.


The procedures I used were:

1)  GRUB selection (option 2) -> Ubuntu 7.10 kernel 2.6.22-14-generic   
(did not get Ubuntu 7.10 kernel 2.6.22-15-generic option to cooperate on the previous attempt)

2) At the Gnome Login box, entered  -   CTRL-ALT-F2  for the console

3) Login in at the CLI, and enter the following;

   "sudo apt-get upgrade"     

Executing this upgrade at the console CLI at least didn't hang at the locales-def, as it did in the previous attempt.


4) System auto rebooted and was sitting at the Gnome Login box.  Did a CTR-ALT-F2 to finish the CLI commands recommended:

"dpkg --configure -a"

Exited out of CLI, and logged into the GUI.  Was then prompted with a "System restart required" message.


Knew I was in trouble when I was again presented with the GRUB 7.10 options only.

So far, all the procedures attempted still corrupts my installation (lose all my Desktop icons, and can't browse my Computer Places).



I have to thank the folks at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) .  Since I have my /home directory on a different partition, it 
only takes about 10 minutes to restore the root partition back using my  sysresccd backup image.


Quess I'll stay with Gutsy until a newer solution is recommended.

Sincerely,
Keith
:neutral:

---

### Post by keinea on 2008-08-26
I successfully upgraded Gutsy too Hardy this evening, after FIRST running the Update Manager on Gutsy  (uname -a, reported a August 20 date for the Linux ubuntu2 2.6.22-15-generic package, after updating).

Also refer to launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)   

Mouse-over the linux kernel link to view the details; "The latest Gutsy release: 2.6.22-15.58, was uploaded to the main on 2008-08-25."

I was able to perform the upgrade by simply using the System --> Administration --> Update Manager, which is the way it should work.

During the last few minutes of the upgrade, the install of the "Generating locales ..." went through without any pauses.

This bug may be related to systems that have been step-upgraded from 7.04 to 7.10 then to 8.04.  Refer to "Tony Maro wrote on 2008-08-04" comments in the 249340 bug report; which is exactly what my system was.

The only issues encountered during the upgrade:  my screen saver locked me out of the desktop and would not accept my password to get back in, so I CTRL-ALT-F2 into a console to kill the multiple screen saver processes.  Also, after rebooting into Hardy I had two application crash reports generated for Seahorse and Firestarter, but after rebooting the system again, those issues seemed to have corrected themselves.

I'll post back to this forum if I encounter any other application issues in the next few days.  But for now I'm a happy Hardy user.

Cheers,
Keith
:cool:

---

### Post by Blackjack Davy on 2008-09-01
I've tried upgrading from Gutsy to Hardy tonight and had exactly the same problem. Can't believe this still hasn't been fixed after all this time.

I couldn't even reboot, I had to switch off the PC at the mains. Not good. 

I might try some of these solutions, although they're all terribly "techie" for a Linux noob such as myself. That Vista upgrade I've been thinking about is looking awfully tempting just now...

---

### Post by whazooo on 2008-09-02
I had the same problems
I didnt have the .14 kernel
after it got stuck, I rebooted into the .15 recovery kernel and dropped into a root shell.

I renamed /usr/bin/localedef to localedef.old
Then did a dpkg --configure -a

then after the install was done renamed localedef back and booted into the 
new hardy kernel..

My system works great so far..

---

### Post by Blinky981 on 2008-09-03
I gave up in the end... I didn't have any extra blank disks so I ordered a free one and dualbooted Vista / openSUSE until it arrived. As from last week I've been running a 100% Ubuntu system. When 8.10 is released I can guarantee I won't be upgrading any time soon if the Hardy upgrade was anything to go by.

---

