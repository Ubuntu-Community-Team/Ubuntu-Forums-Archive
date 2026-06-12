---
title: "Won't start up after recent update"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LinuxLars on 2009-09-15
I'm testing Koala and it's been working great (except for the nvidia and intel stuff). 

However, this morning, after the update, Ubuntu fails to load. 

I would like to be able to continue updates before reinstalling. 

I've started in text mode (Ctrl+Alt_F1) and can sudo to run apt-get. I started NetworkManager with /etc/init.d/NetworkManager start 
but it's not connecting to the internet.

I've never run Ubuntu in text mode before (just Centos/Redhat/Fedora). 

What's the command to start networking using my wireless before I can run apt-get?

Thanks!

---

### Post by psyke83 on 2009-09-15
Did you perform a partial upgrade? It's possible that you removed NetworkManager due to forcing an update when all packages weren't yet available.

Or perhaps are you using the ubuntu-boot PPA as mentioned in [this]("http://ubuntuforums.org/showthread.php?t=1266816") thread? 

Either way, try:

```
$ sudo /etc/init.d/NetworkManager restart
$ init 5
```

If Xorg won't initialize, try editing your xorg.conf and switching to the vesa driver.

Failing that:
```
$ sudo <plug in ethernet cable, then update>
```

;)

---

### Post by philinux on 2009-09-15
Same here. Recovery mode fails too. Think it a graphics driver issue as I get corrupted screen, red and green stuff and it hangs.

I can chroot in from jaunty but not sure what to do apart from do updates.

---

### Post by LinuxLars on 2009-09-15
Yes, it ran a partial upgrade. First one that hasn't worked.

I did locate /etc/init.d/networking restart, but I'm getting errors running it, like:

ifdown: failed to open statefile /var/run/network/ifstate: No such file or directory
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory

I'm hoping that if I can get networking started and can run apt-get, in a day or 2 I can be back in business with the alpha/beta without having to reinstall.

And what do you mean sudo <plug in ethernet cable>?

---

### Post by Schendje on 2009-09-15
> **LinuxLars said:**
> 
And what do you mean sudo <plug in ethernet cable>?

I think he means it as a joke. Saying that if nothing works, you should check your actual ethernet cable. ;)

---

### Post by joey-elijah on 2009-09-15
Not entirely the same issue, but my X Sever fails to start since an update earlier today. I see the boot screen... then that sodding blinking line.

---

### Post by zoomy942 on 2009-09-15
mine is broke too :(

---

### Post by LinuxLars on 2009-09-15
Well, just for grins, I DID plug in an ethernet cable, then ran sudo NetworkManagerRestart. 

At least I can ping the outside world and run apt-get. So maybe when this gets fixed I can get back in business without a reinstall.

---

### Post by cykotiktek on 2009-09-15
major breakage for me also no x screen just the blinking cursor after the latest updates.  thank god for live cd's!

---

### Post by philinux on 2009-09-15
Got into recovery and it's hanging on winbind.

Chroot from my jaunty install shows no updates yet. Although network-manager got updated 15 mins ago.

---

### Post by zoomy942 on 2009-09-15
so sit tight till later?

---

### Post by LinuxLars on 2009-09-15
I'd recommend not updating today. Unless of course you like high risk...

---

### Post by zoomy942 on 2009-09-15
lol.  i always update right away in the morning - over cereal :).

oh well.  I will wait till later then run an update

---

### Post by JCoster on 2009-09-15
Same problem here on an ATI card.  Get the blinking line after usplash.

From vt2 attempting to 'startx' give:
```
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(EE) fglrx(0): Unknown EDID version 0
```

Thought it was just me but glad it's not!

---

### Post by VMC on 2009-09-15
> **psyke83 said:**
> Did you perform a partial upgrade? It's possible that you removed NetworkManager due to forcing an update when all packages weren't yet available.

Or perhaps are you using the ubuntu-boot PPA as mentioned in [this]("http://ubuntuforums.org/showthread.php?t=1266816") thread? 

Either way, try:

```
$ sudo /etc/init.d/NetworkManager restart
$ init 5
```

If Xorg won't initialize, try editing your xorg.conf and switching to the vesa driver.

Failing that:
```
$ sudo <plug in ethernet cable, then update>
```

;)

Yes, that's exactly what I did. Thanks for this tip. I will try it. I removed that ppa that broke my system, but I fear its too late now.

---

### Post by zoomy942 on 2009-09-15
man i hope i dont have to reinstall.  i looked for a daily build but didnt see it any more recent than sept 3

---

### Post by chek2fire on 2009-09-15
Same problem here. The system seems to hang at start samba daemons.

---

### Post by terry_gardener on 2009-09-15
i have just updated my system and it wont start i dont even get a blinking cursor nothing just a black screen. 

pressed esc to get cli and logged in and tried to startx and it load the panels and then just goes back to cli again with an error. 

i have tried changing the xorg driver to nv and vesa and still the same.

i have libc6 and libc6-i686 and libc6-dev pinned at version ending ubuntu9. 

i did notice that there might have been a libc6 update to ubuntu12 could this be the cause if so how do i unpin the packages from cli.

---

### Post by PhilippeK on 2009-09-15
Same problem: after upgrade (normal NOT partial), the restart gave me the normal screen without internet connection (networking disabled).
1. shutdown and manual restart: normal scree WITHOUT menu line above
2. restart: again normal screen without internet connection

Tried the sudo /etc/init.d/NetworkManager restart: Command not found

How will it be possible to dwonloaad a correction (when available??)

---

### Post by philinux on 2009-09-15
> **PhilippeK said:**
> Same problem: after upgrade (normal NOT partial), the restart gave me the normal screen without internet connection (networking disabled).
1. shutdown and manual restart: normal scree WITHOUT menu line above
2. restart: again normal screen without internet connection

Tried the sudo /etc/init.d/NetworkManager restart: Command not found

How will it be possible to dwonloaad a correction (when available??)

chroot is the answer if you cant get in at all. Although I just checked and no updates as yet.

[http://ubuntuforums.org/showthread.php?p=7952958#post7952958](http://ubuntuforums.org/showthread.php?p=7952958#post7952958)

---

### Post by zika on 2009-09-15
> **PhilippeK said:**
> Same problem: after upgrade (normal NOT partial), the restart gave me the normal screen without internet connection (networking disabled).
1. shutdown and manual restart: normal scree WITHOUT menu line above
2. restart: again normal screen without internet connection

Tried the sudo /etc/init.d/NetworkManager restart: Command not found

How will it be possible to dwonloaad a correction (when available??)
Ctrl-Alt-F1
login
sudo dhclient eth0 (or whatever is appropriate)
sudo apt-get update
sudo apt-get upgrade

My PS/2 mouse is not working and I do not have sound ...

---

### Post by cykotiktek on 2009-09-15
wouldn't that only work if you are DHCP not manual?

---

### Post by el_sordo on 2009-09-15
You might want to to try restarting dbus, i.e, 'sudo stop dbus' and 'sudo start dbus'. Then restart gdm or just startx. 'sudo stop gdm' and 'sudo start gdm'.

---

### Post by plun on 2009-09-15
A chroot also seems to fail.....

```
Fetched 10.3MB in 41s (249kB/s)                                                
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

EDIT

Its probably Mr Remnants updates which causes this.... moving X probably

```
stop: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```

---

### Post by zika on 2009-09-15
> **cykotiktek said:**
> wouldn't that only work if you are DHCP not manual?I have static connection but this got me on-line again. While booting it complains about not having /dev/shm and /dev/pts, my PS/2 mouse stopped working (it works on Jaunty live CD) but I connected USB one and I'm on track again. There are two packages that are kept back and I hope they will solve this mess. My USB DAC is also not working ... Complete mess ...

---

### Post by moviemaniac on 2009-09-15
Same here. I spent the whole day installing applications, setting the internet connection up and fixing stuff. When everything worked I made an update. At least I can still access the net from the console as I don't use NetWorkmanager but configure it manually :D

---

### Post by JCoster on 2009-09-15
@zika can you now boot into X? Can't even run apt-get update.. Same error as above.

---

### Post by philinux on 2009-09-15
> **plun said:**
> A chroot also seems to fail.....

```
Fetched 10.3MB in 41s (249kB/s)                                                
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

EDIT

Its probably Mr Remnants updates which causes this.... moving X probably

```
stop: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```

Hi Plun,

My chroot from jaunty does the update and upgrade ok. Nothing that looks like a fix yet though. Will keep trying.

```
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-backports/main Packages
Hit http://archive.ubuntu.com karmic-backports/restricted Packages
Hit http://archive.ubuntu.com karmic-backports/universe Packages
Hit http://archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  initscripts lib32asound2-plugins upstart
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by zoomy942 on 2009-09-15
i can connect by having the ehternet plug in while i boot

then alt+f2

then sudo apt-get update
sudo apt-get upgrade.

it did a 10MB update a little while ago but that didnt fix anything so i will just keep trying.

---

### Post by PhilippeK on 2009-09-15
Thanks Philinux for the link. There I followed waspber advice - end up with a large size terminal without any apparent progress.
Restarted the computer via Alt/Sysrq/b, came back to the normal page without internet connection. 
1. Edited the Connections, and retyped manually the Auto eth0.
2. sudo dhclient eth0
3. sudo :etc:init.d/NetWork manager restart: bad command
4. sudo NetworkManager restart : RECONNECTED

Now I do not move anymore until the next update solving the problem

Maybe it can help

---

### Post by plun on 2009-09-15
> **philinux said:**
> Hi Plun,

My chroot from jaunty does the update and upgrade ok. Nothing that looks like a fix yet though. Will keep trying.



Yup it looks like a chroot works..

Upstart and initscripts are probably the evil packages.


```
root@plun-laptop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  **initscripts** mplayer mplayer-nogui ubuntu-desktop **upstart**
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@plun-laptop:/# 

```

---

### Post by zika on 2009-09-15
Before I figured out that sudo dhclient eth0 could get me on-line again I've DL-ed (on other machine) LiveCd both Daily and Alpha5 for Karmic (64bit) and both of them got into infinite loop before ever getting to X ... So, they are, at least for me, useless ... So, I contemplated installing JJ again ... Just to give You the impression of level of desperation ... Now I'm waiting for upstart upgrade ... I hope.

---

### Post by steeleyuk on 2009-09-15
> **plun said:**
> Yup it looks like a chroot works..

Upstart and initscripts are probably the evil packages.

I didn't install/upgrade them and I'm having the same issues as others.

---

### Post by zika on 2009-09-15
> **steeleyuk said:**
> I didn't install/upgrade them and I'm having the same issues as others.That are not the good news ...

---

### Post by Starks on 2009-09-15
> **zoomy942 said:**
> man i hope i dont have to reinstall.  i looked for a daily build but didnt see it any more recent than sept 3
Look harder.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by philinux on 2009-09-15
> **plun said:**
> Yup it looks like a chroot works..

Upstart and initscripts are probably the evil packages.


```
root@plun-laptop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  **initscripts** mplayer mplayer-nogui ubuntu-desktop **upstart**
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@plun-laptop:/# 

```

If I run a recovery mode in karmic it hangs at winbind. It could have been the libc6 update.

---

### Post by plun on 2009-09-15
> **philinux said:**
> If I run a recovery mode in karmic it hangs at winbind.

Scott J Remnant updated several packages today and its probably for moving X-start but something went totally wrong.

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/thread.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/thread.html)

Close to the end in the list...

---

### Post by philinux on 2009-09-15
I wish these guys would update their test systems and check with a reboot if at all possible. :confused:

Has this been bugged. Will the devs know?

---

### Post by tehk on 2009-09-15
hoping some new packages get pushed to solve this... been living on the edge with karmic for a few months... need it back to get some work done today!

---

### Post by zoomy942 on 2009-09-15
there will be.  dont worry.  just be patient

---

### Post by motang on 2009-09-15
Damn, I should not have done a partial update, and I am at work right now and my notebook is rendered useless (I use it for music and stuff as I am off school at the moment).  Mine boot but I get a blank screen and it seem X is broken...I hope this will be fixed soon so that I won't have to do a reinstall.

---

### Post by zika on 2009-09-15
> **Starks said:**
> Look harder.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)In a moment of crisis today I made a copy of 64-bit Daily LiveCD but it did not work (also Alpha 5 did not work) and got into endless loop before it (never) got to X. Useless, ... I got out of the mess with sudo dhclient eth0 and did the upgrade but upstart and initsripts are still kept back ...

---

### Post by philinux on 2009-09-15
> **motang said:**
> Damn, I should not have done a partial update, and I am at work right now and my notebook is rendered useless (I use it for music and stuff as I am off school at the moment).  Mine boot but I get a blank screen and it seem X is broken...I hope this will be fixed soon so that I won't have to do a reinstall.

In the words of the wise, never do a partial in the development cycle. However I didn't and am in the same boat. :P

---

### Post by Abandon on 2009-09-15
> **steeleyuk said:**
> I didn't install/upgrade them and I'm having the same issues as others.

Me to :(

---

### Post by zoomy942 on 2009-09-15
it'll get fixed.  I always feel better when i'm part of a broken group instead of just one guy :)

broken installs unite!

---

### Post by rajeev1204 on 2009-09-15
Iam getting a dpkg error ,subprocess returned an error code when i run apt-get update.

Neither the older kernel is booting now.How is that possible?

---

### Post by schmolch on 2009-09-15
Damn i wanted to study and now i have to watch TV cause the Laptop is useless.
Life is so unfair sometimes.

---

### Post by steeleyuk on 2009-09-15
> Neither the older kernel is booting now.How is that possible?

Because it isn't a kernel issue, its something loading after the kernel... which is why access via the command line is still possible.

---

### Post by Jim March on 2009-09-15
Same boat here.  And I didn't do a partial.  Dammit.

OK, I think the "winbind" thing is a red herring.  I managed a sudo apt-get remove winbind and it made no difference.  It's a Samba part and I don't see that being an issue.

The /var/log/Xorg.0.log file has all kinds of X-related errors including a warning that the kernel is lacking some video support stuff - I'm on an Intel 965/X3100 chipset so that makes sense.  Also, when starting off the latest -10 kernel the font size during GDM startup is much larger than I've been seeing - the screen is doing 640x480 at that point I'll bet.  Restarting off the -9 and earlier kernels shows the smaller font at the same place, suggesting that video is at least 1024x768 (my lappy is 1280x800).

The -9 and previous kernels (I tried several) can start X, but probably due to some xorg component updates, keyboard and mouse are dead as doornails in them!!!  Dammit...no help there.

Right now I'm typing this on an Alpha4 LiveCD as I only have one machine.  I'm looking for the daily kernel builds; I suspect some xorg-related parts just updated but the kernel-level bits to match didn't get pushed at the same time - they might however be in the daily kernel build.  I'm going to save those to external disk (along with a winbind .deb so I can replace that too!), reboot and see if I can load the .deb files off external media at the command line.

I'm double-screwed because I use whole-disk-encryption and the LiveCDs cannot get to my working disk at all.  Fortunately I have an unencrypted USB scratch drive laying around to transfer the .debs with.

SIGH.

I'll report back when I try the daily kernel.

---

### Post by motang on 2009-09-15
> **schmolch said:**
> Damn i wanted to study and now i have to watch TV cause the Laptop is useless.
Life is so unfair sometimes.

Yes life is unfair like that isn't it. ;)

---

### Post by steeleyuk on 2009-09-15
> **motang said:**
> Yes life is unfair like that isn't it. ;)

Probably also best not to mention that you shouldn't use dev releases in a production environment... yadda yadda yadda :)

---

### Post by Longinus00 on 2009-09-15
After chrooting into the broken karmic install from an alpha 5 cd, I can't get apt-get to work correctly because it complains about dbus.

```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

How would I go about updating in this case or how would I get dbus into the chrooted environment?

---

### Post by Jim March on 2009-09-15
Arright, latest daily kernel is here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

I'm trying that next.  BRB.

---

### Post by Jim March on 2009-09-15
Oh, and as far as "shouldn't use this in a working environment"...um...yeah, if you have an Intel video card you more or less have to.  Jaunty was and remains a steaming pile when you have Intel video, I don't care what you do to it.  You can improve the video by using unstable kernels and funky-as-hell xorg-edgers parts.  Ghaa.  Jaunty should have been delayed, period, it had baaaaad parts in it.

---

### Post by philinux on 2009-09-15
> **Longinus00 said:**
> After chrooting into the broken karmic install from an alpha 5 cd, I can't get apt-get to work correctly because it complains about dbus.

```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

How would I go about updating in this case or how would I get dbus into the chrooted environment?

Plun had this in post #24 but he seemed then to get it working. By the way I've got karmic in a chroot terminal and there are still no updates only the same 3 packages held back.

---

### Post by plun on 2009-09-15
> **philinux said:**
> Plun had this in post #24 but he seemed then to get it working. By the way I've got karmic in a chroot terminal and there are still no updates only the same 3 packages held back.

No the chroot seems to be broken.

Tried to remove winbind but it just gives errors.......

```
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is a heavy break.....

---

### Post by steeleyuk on 2009-09-15
> **Jim March said:**
> Oh, and as far as "shouldn't use this in a working environment"...um...yeah, if you have an Intel video card you more or less have to.  Jaunty was and remains a steaming pile when you have Intel video, I don't care what you do to it.  You can improve the video by using unstable kernels and funky-as-hell xorg-edgers parts.  Ghaa.  Jaunty should have been delayed, period, it had baaaaad parts in it.

I have an Intel card on this laptop, it was never a major problem for me in Jaunty due to me not really using 3D.

Thats the risk of running dev at the moment, a choice between poor but just about usable graphics, and the potential of some updates breaking your install one morning.

Anyway, I'm waiting this problem out, hope there will be an official fix/update by tomorrow at the latest.

---

### Post by motang on 2009-09-15
> **steeleyuk said:**
> I have an Intel card on this laptop, it was never a major problem for me in Jaunty due to me not really using 3D.

Thats the risk of running dev at the moment, a choice between poor but just about usable graphics, and the potential of some updates breaking your install one morning.

Anyway, I'm waiting this problem out, hope there will be an official fix/update by tomorrow at the latest.

I have an en Intel video card in my EeeBox and I didn't have any problems either.

---

### Post by portis on 2009-09-15
I finally fix my karmic.

I downloaded the mountall package and installed it.
I downloaded the rsyslog source and compile it. (Since it failed to compile in launchpad)
I installed the rsyslog package.
And then I can upgrade upstart and initscripts.
After that, I can boot normally.

The only problem is that I must manually start Network-Manager.

---

### Post by philinux on 2009-09-15
Hi Plun,

How come my chroot is ok then? I can update etc.

---

### Post by Vanishing on 2009-09-15
my problem have been Completely Fixed:lolflag:

---

### Post by Longinus00 on 2009-09-15
> **plun said:**
> No the chroot seems to be broken.

Tried to remove winbind but it just gives errors.......

```
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is a heavy break.....

For some reason, aptitude still works for me. I guess it doesn't use dbus.

---

### Post by plun on 2009-09-15
> **philinux said:**
> Hi Plun,

How come my chroot is ok then? I can update etc.

Yup, you are right, just upgraded upstart...

Restarting...:)

EDIT.... broken..

---

### Post by cykotiktek on 2009-09-15
> **Vanishing said:**
> my problem have been Completely Fixed:lolflag:

my problems are nearly fixed also I am formatting lol

---

### Post by philinux on 2009-09-15
Was just doing that in chroot.
```

Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  mountall
The following packages have been kept back:
  initscripts lib32asound2-plugins
The following packages will be upgraded:
  upstart
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 617kB of archives.
After this operation, 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://archive.ubuntu.com karmic/main mountall 0.1.3 [59.1kB]
Get: 2 http://archive.ubuntu.com karmic/main upstart 0.6.3-2 [558kB]
Fetched 617kB in 1s (404kB/s)   
Selecting previously deselected package mountall.
(Reading database ... 217624 files and directories currently installed.)
Unpacking mountall (from .../mountall_0.1.3_amd64.deb) ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up mountall (0.1.3) ...
(Reading database ... 217630 files and directories currently installed.)
Preparing to replace upstart 0.6.3-1 (using .../upstart_0.6.3-2_amd64.deb) ...
Unpacking replacement upstart ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Setting up upstart (0.6.3-2) ...
Installing new version of config file /etc/init/rc-sysinit.conf ...

```

---

### Post by Jim March on 2009-09-15
[COLOR="Red"][SIZE="6"]WAIT: ARE YOU GUYS FIXED USING INTEL VIDEO?[/SIZE][/COLOR]

Because I'm pretty sure "upstart" and "mountall" are not my problems here!  Please, for God's sake, posting "I'm working!" with no details is just...ugly.

I think we have two issues going on: upstart/mountall update failure is one, Intel video (limited to just some cards like my 965!?) is another.

---

### Post by zika on 2009-09-15
Crisis over, upstart fixed, ... I'm glad LiveCD's did not work so I did not reinstall ... I've learned a lot and that is why I love Alpha testing. But my blood pressure does not like it ...

---

### Post by philinux on 2009-09-15
Using [SIZE="5"]**[COLOR="Red"]NVIDIA[/COLOR]**[/SIZE]

Got in eventually, had a fsck problem with the home partition. Then I needed a ```
sudo NetworkManager
```

But I'm back.

---

### Post by Vanishing on 2009-09-15
> **Jim March said:**
> [COLOR="Red"][SIZE="6"]WAIT: ARE YOU GUYS FIXED USING INTEL VIDEO?[/SIZE][/COLOR]

Because I'm pretty sure "upstart" and "mountall" are not my problems here!  Please, for God's sake, posting "I'm working!" with no details is just...ugly.

I think we have two issues going on: upstart/mountall update failure is one, Intel video (limited to just some cards like my 965!?) is another.

im using 965 card.
my "solution" to intel driver is ..............use old drivers...
basicly
if you want to have a working desktop for 965, do the following for now:

downgrade everything listed to the following version:


> 
libgl1-mesa-dev_7.5-1ubuntu1_i386.deb

libgl1-mesa-dri_7.5-1ubuntu1_i386.deb

libgl1-mesa-glx_7.5-1ubuntu1_i386.deb

mesa-common-dev_7.5-1ubuntu1_i386.deb

xserver-xorg-video-intel_2.7.1-1ubuntu1_i386.deb

and voila, you get it.

also, i thought we are just discussing mountall issues here...o.o:lolflag:

---

### Post by Vanishing on 2009-09-15
> **zika said:**
> Crisis over, upstart fixed, ... I'm glad LiveCD's did not work so I did not reinstall ... I've learned a lot and that is why I love Alpha testing. But my blood pressure do not like it ...

:lolflag::lolflag:
im used to that anyways..

---

### Post by rajeev1204 on 2009-09-15
I used aptitude instead of apt-get since that returned some error code, got upstart as new package,upgraded and now my prompt says root@none. cant type anything in terminal.

Total fail :(

---

### Post by JCoster on 2009-09-15
> **rajeev1204 said:**
> I used aptitude instead of apt-get since that returned some error code, got upstart as new package,upgraded and now my prompt says root@none. cant type anything in terminal.

Total fail :(

Using aptitude i've just severely screwed up my install.  I'm getting a loop of 'fuse failed to create temporary directory' just after i'm told to run fsck. 

Attempting to run fsck from live CD but can see a reinstall on the horizon.  I think i should learn how to use aptitude a bit better....

---

### Post by Mercury_Alpha on 2009-09-15
I updated this morning, and acpid failed to install. I had not seen this error before. Ubuntu notified this of me in a warning window. I was also prompted to restart, since I'd recieved some other updates that required that. Upon rebooting, the usplash progress bar halts after a couple seconds and I am dumped to the command line, where I am informed that there is some corrupted data on sda5 (my /home partition) and that I must run fsck to repair it.

I do so, and restart (from the command line, properly, not just hitting the reset button). I am again diverted to the CLI, where the same message repeats. I go through this process several times, until fsck itself apparently hangs.

I have reverted back to 9.04. I get screen tearing in Karmic when playing videos in full screen anyway (doesn't matter the source or file type).

I noticed this error when the updates were being installed:

[img]http://imgur.com/mAJAw.png[/img]

---

### Post by rajeev1204 on 2009-09-15
> **JCoster said:**
> Using aptitude i've just severely screwed up my install.  I'm getting a loop of 'fuse failed to create temporary directory' just after i'm told to run fsck. 

Attempting to run fsck from live CD but can see a reinstall on the horizon.  I think i should learn how to use aptitude a bit better....


Iam thinking a reinstall is the only option for me now.hmm.

---

### Post by whoop on 2009-09-15
I did Ctrl+Alt+F1 to get a shell then:
```

sudo bash
/etc/init.d/NetworkManager.dpkg-backup restart
apt-get update
apt-get dist-upgrade

```
But there is no solution (yet) for me.

---

### Post by xens on 2009-09-15
I broke my EEEPC1000H, it's not my main computer so I'll wait tomorrow for a fix update :]

---

### Post by tehk on 2009-09-15
using nvidia 185 drivers here...
installed mountall and upgraded upstart
i get a fsck error on every boot, and unless i ctrl-alt-f8, i get a black screen every boot.
when i go there tho, i can ctrl-d and skip the check, and get back to my gui...

however, now kde is hosed, when i login, i get this error:

**kstartupconfig4 does not exist or fails. the error code is 3.**

---

### Post by captive on 2009-09-15
here's what I did:
chrooted from a live cd
downgraded upstart to 0.6.3-1
```
wget https://launchpad.net/ubuntu/+source/upstart/0.6.3-1/+build/1146627/+files/upstart_0.6.3-1_i386.deb
sudo dpkg -i upstart_0.6.3-1_i386.deb
```
rebooted

to get gnome up and (quite) running I had to do:
```

sudo start udev
sudo start hal
sudo start network-manager
sudo start gdm

```

but system is still broken (i.e.: upstart won't let default serivces auto-start).

---

### Post by celticbhoy on 2009-09-15
Having the same issues, but with a slight differance. I at least get to tty1, and am able to login. Startx loads the desktop so far then crashes back to CLI. I can also get network root through recovery boot, so like everyone else I will hold off for a day or two to see how to sort it. I do know I wont be updating my second Karmic install until the all clear comes out.

---

### Post by tehk on 2009-09-15
ahh, forget my kstartupconfig4 problem... i changed uuid/guid on myself ages ago and forgot to chown my home folder :D

---

### Post by zika on 2009-09-15
> **celticbhoy said:**
> Having the same issues, but with a slight differance. I at least get to tty1, and am able to login. Startx loads the desktop so far then crashes back to CLI. I can also get network root through recovery boot, so like everyone else I will hold off for a day or two to see how to sort it. I do know I wont be updating my second Karmic install until the all clear comes out.I think it is safe now to upgrade but ...

---

### Post by steeleyuk on 2009-09-15
initscripts and upstart are still being held back. There's no way I'm upgrading this laptop at the moment...

---

### Post by Jim March on 2009-09-15
Vanishing: I tried updating these in AMD64 flavor:

> libgl1-mesa-dev_7.5-1ubuntu1_i386.deb

libgl1-mesa-dri_7.5-1ubuntu1_i386.deb

libgl1-mesa-glx_7.5-1ubuntu1_i386.deb

mesa-common-dev_7.5-1ubuntu1_i386.deb

xserver-xorg-video-intel_2.7.1-1ubuntu1_i386.deb 


...but on mesa-common I get:

> ubuntu@ubuntu:/media/6369efc9-40ab-4c9d-9738-2b298bd4279d/x$ sudo dpkg -i mesa-common-dev_7.5-1ubuntu1_amd64.deb
Selecting previously deselected package mesa-common-dev.
(Reading database ... 105305 files and directories currently installed.)
Unpacking mesa-common-dev (from mesa-common-dev_7.5-1ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of mesa-common-dev:
 mesa-common-dev depends on libx11-dev; however:
  Package libx11-dev is not installed.
dpkg: error processing mesa-common-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mesa-common-dev
ubuntu@ubuntu:/media/6369efc9-40ab-4c9d-9738-2b298bd4279d/x$ 

I'm now trying to find libx11-dev...but...is the "dev" version of this stuff what I want?

With the other four of your five successfully installed, booting into X still fails in the same manner.

Did you do a typo where I need "mesa-common" instead of "mesa-common-dev"?

It appears not - this page lists all the mesa parts:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-retro/+build/1175872](https://launchpad.net/~ubuntu-x-swat/+archive/x-retro/+build/1175872)

Um...guess I'll go download "libx11-dev", reboot, try again?

If anybody else can help me get a booting system, I'd be very happy :(.

My problem now is, off the LiveCD I can't get to my working disk due to encryption issues...

---

### Post by plun on 2009-09-15
> **zika said:**
> I think it is safe now to upgrade but ...

I am still broken....

```
The following packages are BROKEN:
  initscripts 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.7kB of archives. After unpacking 94.2kB will be freed.
The following packages have unmet dependencies:
  initscripts: Breaks: udev (< 146-2~boot6) but 146-1 is installed.
The following actions will resolve these dependencies:


```

---

### Post by zika on 2009-09-15
> **steeleyuk said:**
> initscripts and upstart are still being held back. There's no way I'm upgrading this laptop at the moment...It might depend on the server You are using. In my case (main server) initsripts is still held back but upstart is upgraded and that solved all my issues ...

---

### Post by thecityofgold2006 on 2009-09-15
> **celticbhoy said:**
> Having the same issues, but with a slight differance. I at least get to tty1, and am able to login. Startx loads the desktop so far then crashes back to CLI. I can also get network root through recovery boot, so like everyone else I will hold off for a day or two to see how to sort it. I do know I wont be updating my second Karmic install until the all clear comes out.

+1 exactly. nvidia 185?

---

### Post by Longinus00 on 2009-09-15
Is there any solution out there for the intel people with blinking cursors besides manually downgrading packages? What's weird is that the packages that have been recommended for downgrading

> libgl1-mesa-dev_7.5-1ubuntu1_i386.deb

libgl1-mesa-dri_7.5-1ubuntu1_i386.deb

libgl1-mesa-glx_7.5-1ubuntu1_i386.deb

mesa-common-dev_7.5-1ubuntu1_i386.deb

xserver-xorg-video-intel_2.7.1-1ubuntu1_i386.deb 

weren't touched by the last upgrade. Is that really what's going on here? Reading through the syslog I can see that dbus still isn't loading on boot.

---

### Post by celticbhoy on 2009-09-15
> **thecityofgold2006 said:**
> +1 exactly. nvidia 185?

No Intel!

---

### Post by geordish on 2009-09-15
> **Longinus00 said:**
> Is there any solution out there for the intel people with blinking cursors besides manually downgrading packages? What's weird is that the packages that have been recommended for downgrading



weren't touched by the last upgrade. Is that really what's going on here? Reading through the syslog I can see that dbus still isn't loading on boot.

I'm still having this problem, but I also notice initscripts is still not installable. If I try to force it to install, it wants to remove a whole load of X related packages. Fun.

---

### Post by thecityofgold2006 on 2009-09-15
> **celticbhoy said:**
> No Intel!

Weird. I get exactly the same with an Nvidia 6150 using the 185 drivers. Haven't really been following this thread. Am hoping it'll be fixed by an update tomorrow morning..

---

### Post by celticbhoy on 2009-09-15
Hoping for the same....

I dont know if the exact extent of damage depends on exactlly when I updated, maybe a little later and the results would have been worse?

---

### Post by rolfc on 2009-09-15
I'm up again,   I had three packages held back, Upstart seemed to fix it, initscript want to remove hostname so I left it as is. Now the laptop boot as it should again.  So get it up on the net and run  sudo apt-get install upstart

---

### Post by Vanishing on 2009-09-15
> **Jim March said:**
> Vanishing: I tried updating these in AMD64 flavor:




...but on mesa-common I get:



I'm now trying to find libx11-dev...but...is the "dev" version of this stuff what I want?

With the other four of your five successfully installed, booting into X still fails in the same manner.

Did you do a typo where I need "mesa-common" instead of "mesa-common-dev"?

It appears not - this page lists all the mesa parts:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-retro/+build/1175872](https://launchpad.net/~ubuntu-x-swat/+archive/x-retro/+build/1175872)

Um...guess I'll go download "libx11-dev", reboot, try again?

If anybody else can help me get a booting system, I'd be very happy :(.

My problem now is, off the LiveCD I can't get to my working disk due to encryption issues...
what i think you should do is:
> sudo apt-get install libx11-dev
then put all the before mentioned deb files in a newly created folder(no other deb files) and run:
> sudo dpkg - *.deb
do not dpkg them seperately.
hope this helps..
oh..and you can always chroot to your current install with a livecd to install those debs..:lolflag:

---

### Post by Jim March on 2009-09-15
> oh..and you can always chroot to your current install with a livecd to install those debs.

Wanna bet?  I've got an encrypted file system.  My LiveCD can't access the disk at all.  Everything I try needs a reboot.  Total pain in the butt.

I managed to get upstart_0.6.3-1_amd64.deb in there.  Didn't help.

Why won't any of the devs who broke this stuff come in here and tell us how to fix it?  This is just ugly...

---

### Post by Vanishing on 2009-09-15
> **Jim March said:**
> Wanna bet?  I've got an encrypted file system.  My LiveCD can't access the disk at all.  Everything I try needs a reboot.  Total pain in the butt.

I managed to get upstart_0.6.3-1_amd64.deb in there.  Didn't help.

Why won't any of the devs who broke this stuff come in here and tell us how to fix it?  This is just ugly...

lol...they dont come here(from somewhere i saw this line):lolflag:


well
can you even get a shell out of the current install?



oh, forgot the mention:
i hate the new uxa accelmethod in the new intel drivers(and they dropped the exa accelmethod in them), thats why i kept the old xserver-xorg-intel driver.

i had these lines in my xorg.conf to make sure i use exa:
> Section "Device"
	Identifier	"Configured Video Device"
	driver "intel"
	Option "AccelMethod" "exa"
	Option "MigrationHeuristic" "greedy"
EndSection

for the mesa part, my comp stops working with anything newer than the versions i mentioned, so i thought thats the same problem with you.

so try the following, at least im using 965 and its working for me now with the following setup:

> sudo apt-get install libx11-dev
then put all the before mentioned deb files in a newly created folder(no other deb files) and run:
> sudo dpkg - *.deb
> sudo vim /etc/X11/xorg.conf
add the following lines in
> Section "Device"
	Identifier	"Configured Video Device"
	driver "intel"
	Option "AccelMethod" "exa"
	Option "MigrationHeuristic" "greedy"
EndSection
Note:if you have Section "Device" and EndSection, just add everything from Identifier to greedy in between.
reboot..

---

### Post by ilna on 2009-09-15
Currently I have such situation:

```
The following packages have unmet dependencies:
  initscripts: Breaks: hostname (< 2.95ubuntu1**~boot2**) but 2.95 is installed.
               Breaks: rsyslog (< 4.2.0-2ubuntu3**~boot1**) but 4.2.0-2ubuntu2 is installed.

```

These packages:

```
hostname 2.95ubuntu1
rsyslog 4.2.0-2ubuntu3
```

are reported here

[http://feeds.ubuntu-nl.org/KarmicChanges?format=xml](http://feeds.ubuntu-nl.org/KarmicChanges?format=xml)

to be commited in about 10 hour ago. But what is those** ~boot1** and **~boot2**?

(rather surprising situation before A6 ;-))

---

### Post by celticbhoy on 2009-09-15
> **rolfc said:**
> I'm up again,   I had three packages held back, Upstart seemed to fix it, initscript want to remove hostname so I left it as is. Now the laptop boot as it should again.  So get it up on the net and run  sudo apt-get install upstart

My system claims that upstart is already the newest version.

---

### Post by ppjose on 2009-09-15
same problem problem here.... :(

---

### Post by tghe-retford on 2009-09-15
Current status:

```
The following packages have been kept back:
  initscripts 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Although everything is completely borked. My PC speaker went nuts when it started, the screen produced a pretty pattern of white lines on a red background and the system refused to reboot.

Using recovery mode, I could eventually get to a KDE desktop (after fsck complains about partitions being already mounted) although knetworkmanager is on strike and there is no Internet connection.

So off to the back-up stable partition to chroot and await updates to fix this mess. I love this, keeps me occupied in the evenings. :lolflag:

---

### Post by NCLI on 2009-09-15
Ah... I've missed some breakage this alpha cycle, glad to see it's finally happening! :guitar:

---

### Post by Jim March on 2009-09-15
Vanishing:

Can you please quote your whole xorg.conf file?  Your instructions are useless otherwise because I have NONE in there.  Gotta put the whole thing in from scratch.

And yeah, booting into the borked system I can get to a command line.

---

### Post by MJWitter on 2009-09-15
So i take it, having updated recently, now would not be a good time to reboot?

---

### Post by nandoc on 2009-09-15
Hola,
A new upstart and mountall files have delivered: DO NOT use them... make thing worst!!! Before I was able to boot at recovery and under netboot, now I only get a black screen!!
Lets wait, I will have to reinstall?
Fernandoc

---

### Post by steeleyuk on 2009-09-15
> So i take it, having updated recently, now would not be a good time to reboot?

Definitely not, unless you like looking at the terminal.

---

### Post by celticbhoy on 2009-09-15
> **steeleyuk said:**
> Definitely not, unless you like looking at the terminal.

If you are lucky that is - a blinking curser might be waiting...

---

### Post by captive on 2009-09-15
it seems to be fixed (for the upstart problem, I mean).
Latest updates made my system up and running (except for usplash)

---

### Post by ilna on 2009-09-15
Aha, ```
rsyslog
``` has arrived main server, waiting for ```
hostname
```...

---

### Post by steeleyuk on 2009-09-15
I'm trying to work out whether I can get the updates on to my machine. Tried wireless, not working. Tried USB drive, not working for god knows what reason. Trying CD at the moment... I get the feeling I'm going to have to manually input the code from the DEBs. :D

---

### Post by terry_gardener on 2009-09-15
> **nandoc said:**
> Hola,
A new upstart and mountall files have delivered: DO NOT use them... make thing worst!!! Before I was able to boot at recovery and under netboot, now I only get a black screen!!
Lets wait, I will have to reinstall?
Fernandoc

no you dont have to reinstall i did the same thing. 
follow the instructions on the link below 

[http://ubuntuforums.org/showthread.php?p=7952958#post7952958]("http://ubuntuforums.org/showthread.php?p=7952958#post7952958")

sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

---

### Post by joey-elijah on 2009-09-15
> **steeleyuk said:**
> I'm trying to work out whether I can get the updates on to my machine. Tried wireless, not working. Tried USB drive, not working for god knows what reason. Trying CD at the moment... I get the feeling I'm going to have to manually input the code from the DEBs. :D

Haha! I'm fearing the exact same situation myself. Wifi doesn't work... USB won't work... 

It's all part and parcel of the Alpha&#8482; experience i guess! :P 

That said, from now on i will most certainly be installing my $home separately... (once i can figure out how...)

---

### Post by JCoster on 2009-09-15
Is anyone getting that 
```
initscripts
``` 
is being held back after sudo apt-get upgrade?

Similarly, from chroot>'sudo apt-get update' I'm getting:
```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

Anyone else?

---

### Post by nandoc on 2009-09-15
That release is worst, you won't be able to access the terminal.
Fernando

---

### Post by whoop on 2009-09-15
Seems to be working again, with last updates...
although network is still borked.

---

### Post by joey-elijah on 2009-09-15
I'll wait until Alpha 6 now. I don't think i'm gonna get this mess sorted anytime soon, and A6 is only 2 days away.

*le sigh*

---

### Post by ranch hand on 2009-09-15
Well, I have been enjoying this thread a bunch.  Glad t osee other folks have worse problems than I have.

I update my 32bit 9.10s in the AM and 64s at night.  Of my four 32s, three are working (one does not connect)

I think I can get them all working with the info in this thread.  I am, for once, really happy with my having an ATI card.

---

### Post by celticbhoy on 2009-09-15
> **JCoster said:**
> Is anyone getting that 
```
initscripts
``` 
is being held back after sudo apt-get upgrade?

Similarly, from chroot>'sudo apt-get update' I'm getting:
```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code

```

Anyone else?


Yeah exactly the same here.



joey-elijah - just to say been following the blog for a couple of months - good stuff.

---

### Post by zoomy942 on 2009-09-15
wtf.  the sudo /etc/init.d/NetworkManager start   command worked a little while ago and now it doesnt?

ugh.

---

### Post by scaine on 2009-09-15
Think it was mentioned a bit ago, but if anyone has borked their system and can't even get to a terminal to upgrade it (no network, etc), then fire up a live CD and use this thread to chroot to your borked system and run updates from there.

[http://ubuntuforums.org/showthread.php?t=1255263](http://ubuntuforums.org/showthread.php?t=1255263)

I think [philinux]("http://ubuntuforums.org/member.php?u=353083") has mentioned this in a couple of threads now.  Pretty handy.

---

### Post by Vanishing on 2009-09-15
Jim March:
run:
> sudo dpkg-reconfigure xserver-xorg

to generate the xorg.conf file and put my device code in..you'll be good i think

---

### Post by Starks on 2009-09-15
I prefer my oft-referenced chroot method. ;)

[http://ubuntuforums.org/showpost.php?p=7259112&postcount=5](http://ubuntuforums.org/showpost.php?p=7259112&postcount=5)

---

### Post by JCoster on 2009-09-15
> **ranch hand said:**
> I am, for once, really happy with my having an ATI card.

I have an ATI card and can't start xserver...
Nor can I enable desktop effects with out that damn restore lag but that's for another day when I can actually login..

---

### Post by aj_org_nz on 2009-09-15
Well my Toshiba with ATI (HD2400) got borked after this upgrade. Tried to fix but made matters worse. 
```
initscripts
``` 
held back.
x broken
ah well....back to install

---

### Post by JCoster on 2009-09-15
I wouldn't reinstall yet.. Give the devs a few more hours to sort it out. Or just wait til Thursday and run a dist-upgrade and get alpha6 if you don't want to delete everything. I have exactly the same symptoms as you.

---

### Post by philinux on 2009-09-15
Network manager is still borked.

Had to do a 

```
sudo NetworkManager 
```

To get internet after a reboot.

I like this, Proper breakage at last.

---

### Post by grandtoubab on 2009-09-15
Originally Posted by **tmschmitz** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7954526#post7954526") 				
 				[I]sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

this works for me and save my laptop 
[/I]

---

### Post by tghe-retford on 2009-09-15
initscripts has updated from the main server for me...

...however, nothing interrupts Family Guy. :lolflag: So I will have to wait to see if everything works again.

---

### Post by celticbhoy on 2009-09-15
Still waiting here...

Think I'm on UK server.

---

### Post by thegodsquirrel on 2009-09-15
What do you guys suggest for a system that will not boot to terminal either in regular or recovery mode,   I cant get into the system to do anything!!

---

### Post by nandoc on 2009-09-15
1

---

### Post by celticbhoy on 2009-09-15
Up and running thanx philinux for the chroot commands.

thegodsquirrel - search the thread for phil's chroot option to gain access using a live disk or another install.

---

### Post by celticbhoy on 2009-09-15
Getting a lot of app crashes...

---

### Post by tghe-retford on 2009-09-15
Still getting errors on startup, the annoying constant beep from the PC speaker and the KNetworkManager is stuffed, but I can get to the desktop.

Wicd restores Internet access for now until the Internet can work without it (luckily I had already downloaded it so didn't need to download it again).

---

### Post by celticbhoy on 2009-09-15
App crashes seemed to have stopped, but on startup I am getting a lot of info about failed device setups (usplash never worked on this install since grub2 so it could be be happening on other install also but not showing)

---

### Post by maestrobwh1 on 2009-09-15
> **tghe-retford said:**
> Still getting errors on startup, the annoying constant beep from the PC speaker and the KNetworkManager is stuffed, but I can get to the desktop.

Wicd restores Internet access for now until the Internet can work without it (luckily I had already downloaded it so didn't need to download it again).

I can't deal with the network manager needing access to kwallet in Kubuntu karmic.  Seriously, when did someone decide that it needs this?

I have dumped networkmanager in every version of ubuntu.  It just does not work as well as wicd.

---

### Post by blakamin on 2009-09-15
I'm sitting running the box cli... x wont start...
I had the flashing cursor until I pressed "enter" then just got a terminal login. I have internet etc. Laptop is running nvidia gfx.
0 updates available at the moment.

---

### Post by JCoster on 2009-09-15
I'm now being dropped to a root shell on startup after updating everything through aptitude.
My fsck error every alternate boot seems to have stopped.
My network is borked for the first time today but can get in via chroot.
Still getting this from my sudo apt-get update:
```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code
```

I see that dbus is being held back in aptitude so hopefully that will resolve this once released..

---

### Post by celticbhoy on 2009-09-15
blakamin, I guess it depends on your server how soon it gets to you.
JCoster I fixed with sudo apt-get dist-upgrade -y

---

### Post by blakamin on 2009-09-15
> **celticbhoy said:**
> blakamin, I guess it depends on your server how soon it gets to you.

The joys of being at the ****-end of the world!

---

### Post by whoop on 2009-09-15
> **thegodsquirrel said:**
> What do you guys suggest for a system that will not boot to terminal either in regular or recovery mode,   I cant get into the system to do anything!!

I got to gdm and after I logged in I got a few error messages and just got a wallparer, nothing else. I could launch a schell via Ctrl+Alt+F1.

---

### Post by JCoster on 2009-09-15
@celticbhoy Thanks for your advice, but after installing all packages from chroot I'm still getting dropped to a root shell on startup (even from recovery mode) and my network isn't working...

I guess I'll see if there's any progress in the morning, although just so I can be clear, where are we on this?  What's the general stage people are up to in getting this mess sorted out?

---

### Post by thegodsquirrel on 2009-09-15
> **celticbhoy said:**
> Up and running thanx philinux for the chroot commands.

thegodsquirrel - search the thread for phil's chroot option to gain access using a live disk or another install.



what command did you run when you got into root for karmic

I ran apt-get update && apt-get dist-upgrade -y

---

### Post by frustphil on 2009-09-15
up and running..
just choose netroot in recovery mode then 'apt-get install upstart' and then 'reboot'.
i am using kubuntu...

---

### Post by graaant on 2009-09-15
Still struggling with this one too.
Just a blank screen after a quick usplash.
Choosing recovery mode put me straight into X - not recovery mode!?

---

### Post by thegodsquirrel on 2009-09-15
> **graaant said:**
> Still struggling with this one too.
Just a blank screen after a quick usplash.
Choosing recovery mode put me straight into X - not recovery mode!?



reference back in this thread and find Philinux's guide to chroot using a liveCD

I am currently running an upgrade that appears to be reinstalling all packages that were taken out this afternoon will post as soon as I reboot

---

### Post by aonegodman on 2009-09-15
Hi all - don't know if this is related problem, but this thread only one I found after "Update" install this morning. Seems Ubuntu has new startup screens and runs a program "fsck" before new start screen appears. Checks devices and other stuff then gives a new Login Screen. First time it ran it failed to recognize and would not mount 2 - HD's in my system. I did a restart and got a GRUB Error 21. Had to run LiveCD and rebuild GRUB. Looks like it got it right second time around as it now sees and mounts other HD's. But what I want to know is - what is this new startup routine? What is "fsck" running each time? Is all this part of new update? Thanks all :confused:

---

### Post by thegodsquirrel on 2009-09-15
no you dont have to reinstall i did the same thing.
follow the instructions on the link below

[http://ubuntuforums.org/showthread.p...58#post7952958](http://ubuntuforums.org/showthread.p...58#post7952958)

sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash
__________________


In short boot into Livecd input above commands into terminal

then run sudo apt-get update

then run apt-get upgrade

this is what restored the missing packages and fixed my system.

---

### Post by novafluxx on 2009-09-15
I just updated today, and also ran into the no boot issue. The screen goes blank and the HDD activity light stays on for a few seconds, then dies. I waited a couple of minutes, and nothing changed.

I booted to recovery and ran fsck and it seemed to make some corrections, I then restarted and now I no longer see USplash, however I do see a blank screen, a flicker, another blank screen, then XSplash.

Not sure what happened but I will be doing a clean install of Alpha 6 later this week, so no worries on my part.

Glad to see Karmic Koming along so nicely :P

---

### Post by frustphil on 2009-09-15
from Mr. Remnant: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125)
> 
Thanks the report, however this isn't a bug at the source package level but merely a transitional artefact at the point you upgraded. It'll sort itself out automatically over the next few hours.
patience baby...

---

### Post by motang on 2009-09-16
I downloaded the dialy build and installed it...it is working now...but dammit I have set everything up again. Oh well, that is why we are alpha testing right? 

The new boot sequence is cool, the way it fades in and fades out like Vista/Win7 does.

---

### Post by Jay_Bee on 2009-09-16
I updated and restarted... everything works like before except the DVB tuner, which isn't recognized by Me-TV anymore, any ideas about how I could fix this?

---

### Post by Jim March on 2009-09-16
New complete instructions at:

[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

...aimed at the total newbie.  Plus bonus lyrics.  You'll see.

---

### Post by jms-ubuntu-en on 2009-09-16
I'm in the middle of mayhem as well. The problem seems to be a package upstart which is in state "hald-configured". Every time I try to configure it karmic just reboots.

Done so far:

[LIST]
[*]karmic won't boot, chrooted using daily build (alternative flavour because of lvm)
[*]at first try package mount (i guess) didn't upgrade because of 'ro' rootfs - I tested it afterwards and it was 'rw'
[*]after that failed upgrade attempt a "dpkg --configure -a" was needeed, however this causes karmic to boot (in a controlled way, not crashed)
[*]according to dpkg.log the package upstart is the last that dpkg has dealt with -> I tried to configure "dpkg --configure upstart" -> karmic booted again
[*]now there is a bunch of packages in state half-configured waiting for upstart (i guess) to be configured, upstart is in state half-configured as well
[/LIST]
What do you suggest?

---

### Post by ranch hand on 2009-09-16
I certainly am not using LVM so can't help there.  I only have two 9.10 variations, one of four 32bit and one of five 64bit that are not booting.

The only thing I can say is to keep chrooting in and updating.  I am sure the 32bit will straighten out with tomorows update (32s in AM, 64s in PM).

The 64bit problem is a week old now and I have given it a 2 day break as I couldn't see just screwing it up more.

---

### Post by moviemaniac on 2009-09-16
Hmmm... the latest update brought a new upstart package but the new udev-package that came along as well is now messing with my system rendering my keyboard useless. Oh the joys of using Alpha-releases :D

---

### Post by ignasigarcia on 2009-09-16
> **jms-ubuntu-en said:**
> I'm in the middle of mayhem as well. The problem seems to be a package upstart which is in state "hald-configured". Every time I try to configure it karmic just reboots.

Done so far:

[LIST]
[*]karmic won't boot, chrooted using daily build (alternative flavour because of lvm)
[*]at first try package mount (i guess) didn't upgrade because of 'ro' rootfs - I tested it afterwards and it was 'rw'
[*]after that failed upgrade attempt a "dpkg --configure -a" was needeed, however this causes karmic to boot (in a controlled way, not crashed)
[*]according to dpkg.log the package upstart is the last that dpkg has dealt with -> I tried to configure "dpkg --configure upstart" -> karmic booted again
[*]now there is a bunch of packages in state half-configured waiting for upstart (i guess) to be configured, upstart is in state half-configured as well
[/LIST]
What do you suggest?


same problem here :(

---

### Post by LinuxLars on 2009-09-16
After the upgrade this morning (Wednesday), it looks like I may be toast. 

After a reboot, I get dumped to a tty prompt. On screen is the error:

init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Oddly - my first login is always unsuccessful, with "Login incorrect". My 2nd login attempt works.

So far, I have been unable to get connected to the internet - which means no more updates and a reinstall in my near future.

Anyone have any ideas?

---

### Post by zika on 2009-09-16
> **LinuxLars said:**
> After the upgrade this morning (Wednesday), it looks like I may be toast. 

After a reboot, I get dumped to a tty prompt. On screen is the error:

init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Oddly - my first login is always unsuccessful, with "Login incorrect". My 2nd login attempt works.

So far, I have been unable to get connected to the internet - which means no more updates and a reinstall in my near future.

Anyone have any ideas?Did You try sudo dhclient eth0(or whatever) in CLI ...?

---

### Post by LinuxLars on 2009-09-16
Actually I'm currently following the steps outlined in:
[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

---

### Post by LinuxLars on 2009-09-16
And even after an apt-get dist-upgrade, I'm still in the same boat. Guess I'll try again tomorrow.

---

### Post by VMC on 2009-09-16
> **moviemaniac said:**
> Hmmm... the latest update brought a new upstart package but the new udev-package that came along as well is now messing with my system rendering my keyboard useless. Oh the joys of using Alpha-releases :D
I got the following error regarding upstart:
```

(Reading database ... 107130 files and directories currently installed.)
Preparing to replace util-linux 2.16-1ubuntu2 (using .../util-linux_2.16-1ubuntu3_i386.deb) ...
Unpacking replacement util-linux ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up util-linux (2.16-1ubuntu3) ...
start: Unable to connect to Upstart: **Failed to connect to socket** /com/ubuntu/upstart: Connection refused
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

```

---

### Post by rajeev1204 on 2009-09-16
> **LinuxLars said:**
> After the upgrade this morning (Wednesday), it looks like I may be toast. 

After a reboot, I get dumped to a tty prompt. On screen is the error:

init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Oddly - my first login is always unsuccessful, with "Login incorrect". My 2nd login attempt works.

So far, I have been unable to get connected to the internet - which means no more updates and a reinstall in my near future.

Anyone have any ideas?


Just type dhclient eth0 ,this starts your network, then apt-get update followed by upgrade.

Its fixed now for me.

---

### Post by JCoster on 2009-09-16
After finally booting to xserver this morning after upgrading packages and finding that network-manager-pptp had been corrupted (I assume because of the network-manager cockup) I ran a ```
sudo apt-get install --reinstall network-manager-pptp
```.

After rebooting, I get greeted with: ```
udevd could not read /etc/udev/rules.d/z80_user.rules
```

Any ideas?  This occurs in recovery mode or standard.

---

### Post by magian on 2009-09-16
> **grandtoubab said:**
> Originally Posted by **tmschmitz** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7954526#post7954526") 				
 				[I]sudo start dbus
sudo start hal
sudo start network-manager
sudo start gdm

this works for me and save my laptop 
[/I]

Thanks bro.  That saved my *** and got my netbook running again so I could to a *sudo apt-get update* and fix everything.

*UPDATE* I spoke too soon....I am still having crazy issues after the update.

---

### Post by TDK800 on 2009-09-16
Getting a bunch of symlink errors in /lib/udev/rules.d/ on fresh install of alternative daily build.

Removed winbind yesterday and it booted up after that, but mouse wasn't working.

On the fresh install i did all the aptitude updates,upgrades,distro-upgrades and it is still not loading into gnome. 

When started gnome manually, it hanged at gnome user login box.

EDIT: restarted laptop and it logged me into gnome now, without crashing. So starting the Gnome manually once seemed to fix the problem as far as I can see: "sudo start gdm".

And NetworkManager immediately crashed in the crash reports after successfully logged into Gnome Desktop.

---

### Post by grandtoubab on 2009-09-16
shoot again it's more fun to compete
[http://ubuntuforums.org/showpost.php?p=7958872&postcount=14](http://ubuntuforums.org/showpost.php?p=7958872&postcount=14)

---

### Post by jms-ubuntu-en on 2009-09-16
> **jms-ubuntu-en said:**
> I'm in the middle of mayhem as well. The problem seems to be a package upstart which is in state "hald-configured". Every time I try to configure it karmic just reboots.

FYI,
I got the upstart's half-configured problem fixed by modifying script upstart.postinst. I added 'echo' before function 'reexec_init' execution at line 30:
before:
reexec_init
after:
echo reexec_init

After that I was able to run 'dpkg --configure -a' and after that normal upgrade routines. After succesful upgrade (system up and running) I restored the original upstart.postinst and ran 'dpkg-reconfigure upstart'.

---

### Post by rubenverweij on 2009-09-16
Same issue here.
However, I am not even able to login via tty. I just get a blinking cursor, recovery mode hangs after
```
Begin: Running /scripts/local-bottom
Done.
Done.
Begin: Running /scripts/init-bottom
Done.
```
Is there a way to get into tty?

---

### Post by LinuxLars on 2009-09-16
Had the same issue - I can only get into tty following these directions:

[http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657)

---

### Post by rubenverweij on 2009-09-16
It doesn't work for me... :(
Nice song though...

---

### Post by LinuxLars on 2009-09-16
Great news for me at least. 

I updated/upgraded again this afternoon, and removed the nvidia dev package. 

I'm up and running.

---

### Post by goldsniper on 2009-09-17
:popcorn: My problems is resolved! I'm in X again!

I was fortunate to be able to boot into the terminal.

Then I enable network support, dhclient. Mine uses dhcp so it is easy. When the net connection is up and running I did a install, update, upgrade and lastly dist-upgrade.

login into terminal

sudo dhclient eth0

sudo apt-get install
sudo apt-get update && sudo apt-get upgrade

sudo start dbus
sudo start hal
sudo start gdm

sudo apt-get dist-upgrade

Restart

Login back into terminal, 

Type "X"


Don't ask me how or why it worked.. I don't know what those command actually did! It just lame luck I guess!  
:guitar:

---

### Post by ProgrammingAce on 2009-09-17
My situation is getting progressively worse...

i ran apt-get update and upgrade, then rebooted.

I was greeted with Grub Error 15, File not found. I didn't have any luck messing around with the grub entries, so finally took a look at the kernel and see that all of my kernels were wiped out.

/boot is empty except for a grub directory and memtest86.

My boot disc is a slack distro, but i have no idea how to install a kernel to a linux system that doesn't have *any*. Any ideas?

EDIT: It may because i was using kernel 2.6.31-Generic instead of 2.6.31.10. I wonder if the updater got confused and wiped out the active kernel without offering a substitute?

EDIT2: I managed to get a kernel into the system by running an ubuntu boot disc and using chroot to install a new kernel. That still dumped me back at a terminal session with no X server. I tried another apt-get update and apt-get upgrade, but that didn't do anything. On a whim I tried 

 apt-get install ubuntu-desktop  
That worked and got me back up and running, but i don't trust this install anymore. I'll keep messing around with it until Karmic goes final, but i'll end up doing a clean install.

---

### Post by rubenverweij on 2009-09-17
I gather installing the latest updates will fix the problem?
I am however only able to get internet connection in a live cd environment because I only have access to wifi...
How could I install the updates from within the live cd? I already tried to chroot my / partition, but sudo apt-get update failed...

EDIT:
Even if I try ifconfig in / chroot, it won't work:
ifconfig
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.

EDIT2:
I tried dpkg-reconfigure -a, this returns all kinds of upstart errors:

```
* Disabling power management...                                                grep: /sys/power/state: No such file or directory
                                                                         [ OK ]
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
invoke-rc.d: initscript acpid, action "restart" failed.
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Checking battery state...                                                    grep: /sys/power/state: No such file or directory
                                                                         [ OK ]
stop: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.

```

Any ideas?

---

### Post by GokuH12 on 2009-09-17
I Was able to get into a shell with my ubuntu server 9.04 disc ( its recognize ext4) i did the update && upgrade part, but when its installing hte upstart package its just reboot! i tried doing manually dpkg -i package name and when its installing reboot again! what its the problem :S?

its possible to boot with the netroot option from grub1?

thanks in advice

EDIT: Saw the answer back there and already running fine :D

---

### Post by LindsayD on 2009-09-18
I'm also having the same problem. I've tried all the advice on the various forums, including booting with the live cd of karmic 6, and using the terminal to upgrade from the  mounted drive. All seemed to work fine, until I tried to boot again. 
I reach the tty1 point and can log in, and access all my files from the terminal. 
However, there is no display available. 
I tried to type X and receive a message that the display has no memory. 
I tried to use a gedit to see what was in the xorg cof file, and received the message that display is not available. 
Basically my Ubuntu installation is unaccessible and useless. 
 
Can anyone suggest anything else? Otherwise I'll wait for October and do a fresh installation. I've managed to backup personal files using the live cd (as I have a Windows partition to which I can save files), but can't access Firefox to save my favourites. Does anyone know where these are kept?

---

### Post by yellerKat on 2009-09-18
> **LindsayD said:**
> can't access Firefox to save my favourites. Does anyone know where these are kept?

.mozilla/firefox/*.default/bookmarkbackups

Go to Bookmarks > Organize Bookmarks > Import and Backup > Restore > Choose File...

Navigate to the JSON file and select your backup.

---

### Post by VMC on 2009-09-18
> **LindsayD said:**
> I'm also having the same problem. I've tried all the advice on the various forums, including booting with the live cd of karmic 6, and using the terminal to upgrade from the  mounted drive. All seemed to work fine, until I tried to boot again. 
I reach the tty1 point and can log in, and access all my files from the terminal. 
However, there is no display available. 
I tried to type X and receive a message that the display has no memory. 
I tried to use a gedit to see what was in the xorg cof file, and received the message that display is not available. 
Basically my Ubuntu installation is unaccessible and useless. 
 
Can anyone suggest anything else? Otherwise I'll wait for October and do a fresh installation. I've managed to backup personal files using the live cd (as I have a Windows partition to which I can save files), but can't access Firefox to save my favourites. Does anyone know where these are kept?

Did you try "vesa" route. Editing "/etc/X11/xorg.conf", and changing:
Section "Device"
	Identifier	"vesa"

What video chip do you have, ATI, nVidia, Intel?

---

### Post by nandoc on 2009-09-18
HI,
I am not seening any xorg.conf file in my /etc/X11 directory. I have to reinstall alpha5 again, and for safety I have not upgraded until no bad new are shown here. 

Any comments on a clean install with alpha 6?
Fernandoc

---

### Post by LindsayD on 2009-09-19
Managed to get my bookmarks - it was a major mission until I found where they were kept. 
For anyone else with this problem, this is what I did:
Made a live alpaha 6 "cd" (put it on a flashdrive) and booted into ubuntu from there

1) Mounted my linux drive 
2) at the terminal, cd'd into the mounted partition
3) used chroot to get root permissions : "sudo chroot /media/drivename
4) This will give, at the terminal root@ubuntu
5) cd'd into my home directory 
6) cd .mozilla/firefox
7) there is a file and a folder here - the profile.ini file and a folder which is numbers and letters.default
8  ) cd into this folder, and use ls command
9) In this folder is a further folder called bookmarkbackups - cd into this folder, and find the files with .json extension. The latest will be copied to another location
10) copy to the home directory using cp command
11) cd back into the home directory and use ls -l command to see the permissions of the file 
12) use chmod to give all users permission for these files - to be able to copy them somewhere else

In my case I am dual booting with windows so I copied them to the windows drive 

After booting into windows, I was able to restore my backups into firefox in windows.

What I learned from this? Backup backup backup!!!1

---

### Post by LindsayD on 2009-09-19
Reply to VMC:
No I have't tried the "vesa" yet. 
I have an Acer Timeline and I think my video card is an Intel one. 
Still haven't solved the problems of booting into Ubuntu yet - just using the live cd image on my flash drive for now. I think I'll wait a bit until a more stable version comes up, and then reinstall, and formatting properly with ext4 filesystem.

---

### Post by rednukleus on 2009-09-19
> **goldsniper said:**
> :popcorn: My problems is resolved! I'm in X again!
...
...
Don't ask me how or why it worked.. I don't know what those command actually did! It just lame luck I guess!  
:guitar:

You just saved my hide. A few minutes ago, I thought I'd update my karmic preview because I was having video issues with the pop up messages. Update manager gave some errors and froze while attempting a "partial upgrade", which should have tipped me off, but I went ahead and tried apt-get -d. Next thing I know, I get a "Failed to connect to Socket /var/run/ blablah" error and I'm at a terminal login prompt. After floundering a bit with apt-get and a file system check, I booted to terminal with networking, and entered the same commands you used. I don't know what dbus, hal, or gdm are, and ubuntu didn't know what gdm was either, but I typed those in too for good measure. the dist-upgrade step gave a scary number of errors, and I don't know if they are really resolved, but at least I'm back in Gnome again!! Thanks a lot.

---

