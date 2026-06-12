---
title: "[SOLVED] nuked intrepid twice , need help isolating problem ."
date: 2008-07-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-07-18
twice now I have nuked my intrepid install by copying some files as root using a root nautilus ( gksudo nautilus ) . the first time I had copied some mplayerhq.hu codecs into /usr/lib/codecs the second time I had copied /var/log/installer into a tmp dir in /root inorder to tar it and the tried to access it with archive manager , both times gdm seems to have crashed and I can nolonger login to my home dir , on boot it dumps me to a login prompt and when I enter my user name and password it returns " cant cd to /home/ron " . I can boot into recovery mode and start x as root but without gdm . starting x as root gets me to an x session desktop but I cannot access many admin functions (permission denied ). I can access /home /ron from recovery mode but have not found out what is wrong yet . Any suggestions on where to look and what to try will be greatefuly accepted . if this is a bug its potentialy a bad one and I need help isolating it .

---

### Post by BwackNinja on 2008-07-18
I have had the exact same problem. With all this, the permissions for my entire partition are screwed up (as you've heard and probably experienced yourself). Normally I can access the "/" of my intrepid install from hardy, but after the ibex dies, I can't. This is kinda a **really big deal**.

Intrepid doesn't die gracefully, it seems to take everything it can with it.

---

### Post by ronacc on 2008-07-18
I saw in the thread about grub that you had the same problem under about the same scenario . I can access my /home from my hardy install on the same box but not / , strangely I can access / from recovey mode I just can't access most admin functions ( permission denied) even though I am at a root prompt . I'm going to try to access my intrepid / from a puppy live cd if I can't get at it from there its really screwed . this is a bad one, we need to find out what is causing it and what exactly it is doing .

---

### Post by cjm5229 on 2008-07-18
I had this one also, I was untarring a file in my root Nautilus and suddenly everything died. I had to do a complete reinstall to get it back. I'm guessing it's a Nautilus bug.

---

### Post by ronacc on 2008-07-18
yes and its a bad one , we need to try to find out what is going wrong to provide as much info as possible . so far I have been looking at dir and file permissions and cannot find anything wrong, mabye a policy kit bug ? or something is munging up the user id ? I am going to hold off reinstalling or modifying anything so I can search for the problem but I am running out of Ideas. any sugestions welcome , what is the name and location of the file that lists users nad groups ?

---

### Post by BwackNinja on 2008-07-18
/etc/group

Check your logs, they might have something important in there. Basically everything in /var/log/. I didn't check mine and I probably should've. I'm sure permissions changed on my partition when it died, so there's unfortunately the possibility that whatever could have been written wasn't due to errors (ironically). I hope there is something worthwhile to be found there, I'd check my own, but I already reinstalled.

---

### Post by ronacc on 2008-07-18
the first time it happened I poked around a bit and then gaveup and reinstalled , this time I am not going to destroy the evidence until I have exahusted every avenue of investigation , I did a cursory look at the logs and I can see where things go down the tubes but no indication as to why yet atleast none that I understand . I'm going to copy the whole /var/log dir to a cd to preserve it .

---

### Post by autocrosser on 2008-07-18
I've had it happen once about two weeks ago--for some reason it changed my permissions in /tmp & I couldn't log in as my user, only as root. After resetting the permissions I got back in--I have enabled my root user & logout/login as root to do changes--have not had any problems after this---but it is a PITA to do it.........:(

---

### Post by ronacc on 2008-07-18
thanks for that tip on where to look I'll check it out as soon as I finish backing up that whole drive to dvd for evidence , it shouldn't take too long its a fresh install . I'll report back , BTW what should my permissions on /tmp be ?

---

### Post by ronacc on 2008-07-18
here is what I  found for /tmp , permissions look ok , rw for user group and others the same as on my working hardy install , but there are no user subdirs, for example gconfd-ron does not exist in intrepids /tmp but does in hardys, gconfd-root does exist but I cannot start gdm as root , it fails with no reason given .

---

### Post by ronacc on 2008-07-19
found something but I'm not sure what it means , logged in as root using my root password (not sudo) when I go to system>admin>users and groups I get this message  " the configuration could not be loaded you are not allowed to access the system configuration "
edit:    the permissions for /usr/bin/users-admin are rwx for root

---

### Post by ronacc on 2008-07-19
ok I have filed bug# 250021 on this please add any info you may have to this bug so we can squash it .

---

### Post by autocrosser on 2008-07-19
Sorry I was not able to get back to you--I changed the permissions on /tmp so my user & root could write to it--I did not change the permissions to the folders inside--once I allowed my user to write to /tmp, the folders/files were created.

Hope that helps-----

---

### Post by ronacc on 2008-07-19
@ autocrosser not a problem I don't expect instant responses :) we on this forum are spread across 24 timezones and aren't always in sync . my questions about the permissions  was kind of stupid anyway I have 2 working hardy installs for comparison and checking against those the permissions on my /tmp are the same ( rw for user group and others ). I was going to try creating a new user to see if I could log in as that user but even logged in as root I am denied permission to system>administration>users and groups and I don't know the cmds to try it from term , alsoI can't start gdm even as root although I can start an x session as root.

---

### Post by autocrosser on 2008-07-19
So it sounds like you had a slightly different problem than I did--I still think that we are chasing parts of the same problem. I was working in gksudo nautilus at the time of the problem--just like you--my icons all went generic & the desktop was non-responsive.

Looks like Nautilus is not working with sudo permissions well......

wrote my comment to  [https://bugs.launchpad.net/ubuntu/+bug/250021](https://bugs.launchpad.net/ubuntu/+bug/250021)  also......

---

### Post by BwackNinja on 2008-07-19
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/238668](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/238668) - a bug I had encountered while in hardy. Its the only other "nautilus with super-user privileges" problem I know off the top of my head. May be related somehow, may not.

---

### Post by ronacc on 2008-07-19
@ autocrosser  yes exactly the same symptoms generic icons unresponsive desktop  , thanks for adding your comments . I'm keeping my intrepid install as is so I can try things for the devs if they ask me to . this is a bad one .

@ BwackNinja possibly part of the same problem ,nautilus (gvs ?) not playing nice with sudo or gksu , I never use trash so I didn't bump into that one but I seem to remember a couple of posts in the hardy developement forum about emptying the trash deleting the whole FS .

---

### Post by ronacc on 2008-07-21
I still haven't had any response from the devs on my bug report yet , from the rate the bug#'s are going up they are swamped . I'll hold position until a3 then resize that partition and install a3 to the freed up space but I'd rather not do anything right now that might disturb clues.

---

### Post by scradock on 2008-07-22
> **ronacc said:**
> I still haven't had any response from the devs on my bug report yet , from the rate the bug#'s are going up they are swamped . I'll hold position until a3 then resize that partition and install a3 to the freed up space but I'd rather not do anything right now that might disturb clues.

Did today's upgrade to Nautilus change the behavior? The list of changes was fairly long, though I didn't see a specific mention of your problem on a cursory glance....

---

### Post by ronacc on 2008-07-22
I haven't updated or changed anything since it happened, I am preserveing everything as is incase the devs want me to look at something specific to try to isolate what is happening . I think this one is potentialy bad enough that if I can help fixing it, that is worth waiting awhile . I'm on my hardy install right now just marking time .

---

### Post by autocrosser on 2008-07-22
There was a nautilus update within the last day or so--I will try to provoke it this evening & post back----

---

### Post by ronacc on 2008-07-22
thanks

---

### Post by autocrosser on 2008-07-23
Well--there was another nautilus update this evening--I d/l'd it & then went thru a reboot just to start "fresh"--used gksudo nautilus for about 20 minutes--worked with various files--edits, remove & move--all without problems. Not conclusive, but seems to be working well "right now".

Interesting side-note. I remember seeing this output (SSSSSSSSSSSSS) in the term during Hardy development--can't remember what was causing it--see attached----

dean1@linux:~/Desktop$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension

** (nautilus:20676): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSseahorse nautilus module shutdown
Shutting down nautilus-open-terminal extension

--- Hash table keys for warning below:
--> file:///initrd
--> file:///mnt
--> file:///mnt/Drive1
--> file:///mnt/HardyHome
--> file:///root
--> file:///srv/cvs
--> file:///mnt/Ibexbackup
--> file:///dev
--> file:///
--> file:///home
--> file:///srv
--> file:///srv/cvs/CVSROOT

(nautilus:20676): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 12 elements at quit time (keys above)

(nautilus:20676): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 12 elements at quit time
dean1@linux:~/Desktop$ 

I would try a new install with the updates & see if you are seeing the same--It displayed the SSSSSSseahorse until I shutdown nautilus---Interesting that there are hanging hash marks for every folder I was working in......I think that if you see the same thing it would be a good add to the bug report.

---

### Post by ronacc on 2008-07-23
thanks for the info I'll repartition and do a fresh install of alpha3 when it comes out (scheduled for tomorrow) . On the error I get the same thing in hardy. 

ron@ron-desktopA:~$ gksudo nautilus
Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

** (nautilus:512): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

???????????????????????????????????????????????????????????????????????

--- Hash table keys for warning below:
--> file:///

(nautilus:512): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:512): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-open-terminal extension
ron@ron-desktopA:~$ 


everything above the line of ????? which inserted  as a marker appears as soon as I open nautilus , below appears when I close nautilus . I never paid much attention to it as it dosen't seem to cause problems.

---

### Post by autocrosser on 2008-07-23
Yes--I don't get the samba stuff--have usershares enabled. On another note: I was looking at the bug-list & they are talking about the large number of gksudo bugs--looks like there will be some movement on that issue........

Luck to you & I do hope that the last two nautilus updates "cured" your problems.

---

### Post by scradock on 2008-07-24
Just to let you know, the problem persists after the two nautilus updates.... I managed to nuke Intrepid this morning by using gksudo nautilus, trying to open an old term.log. Next time I'll remember to change the file permissions instead of using gksudo(!)

---

### Post by ronacc on 2008-07-24
thanks for the info , please add your comments to bug# 250021 , hopefuly we will get some action on this .

---

### Post by plun on 2008-07-24
Difficult bug and I have tried to test different issues with Nautilus

Network including Samba enabled with shares-admin, no warnings

Today I got new ones, not a clue whats about ??

```
plun@dunder:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:10934): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:10934): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:10934): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

```

---

### Post by scradock on 2008-07-24
> **ronacc said:**
> thanks for the info , please add your comments to bug# 250021 , hopefuly we will get some action on this .

I have added my confirmation, and a copy of .xsession-errors, which has similar warnings to the ones shown above from the terminal, and a fatal error that crashed the Xserver.

```
(nautilus:16663): Gtk-WARNING **: Attempting to store changes into `/home/sc/.recently-used.xbel', but failed: Failed to create file '/home/sc/.recently-used.xbel.O94IEU': Permission denied

--- Hash table keys for warning below:
--> x-nautilus-desktop:///
--> file:///media
--> file:///media/hda5
--> file:///home/sc
--> file:///home/sc/Desktop

(nautilus:16663): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 5 elements at quit time (keys above)

(nautilus:16663): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time

(gnome-panel:5023): Gtk-WARNING **: Attempting to store changes into `/home/sc/.recently-used.xbel', but failed: Failed to create file '/home/sc/.recently-used.xbel.HJ1LEU': Permission denied
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 28694 requests (28694 known processed) with 0 events remaining.

DBus connection has been lost, trackerd will now shutdown

** (trackerd:5034): WARNING **: could not open /home/sc/.local/share/tracker/tracker.log
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

---

### Post by ronacc on 2008-07-24
I get that warning in the term in hardy also . see above , the xsessinion error might be a clue I'll check my logs and see if I have a error like that at the time the problem showed up .

---

### Post by ronacc on 2008-07-24
@ scradock I'm glad you thought to save your xsession log , when my system trashed I tried rebooting c aouple of different ways and did manage to start an xsession (without gdm) which apearently wiped my xsession log from the crash .

---

### Post by ronacc on 2008-07-26
update following a hint in another thread I had a look at the permissions of / on my nuked system they were 700  chmoding to 755 restored the system .
it looks like performing some actions as root alters the perms on / and its not just nautilus the other thread mentions file roller .

---

### Post by ronacc on 2008-08-08
do they actualy read the bug reports or just make up whatever answer strikes them ???? I cannot belive the response on this one !!! first mark it as a duplicate of an unrelated bug ,then when I question that decission mark it as not a bug at all !!!! yeah right a completely normal action renders your system not able to boot to gdm and it isn't a bug . are they copying their answers from MS ???

---

### Post by autocrosser on 2008-08-08
Looks like someone is a "bit" miss-informed---post your findings again--with more "spirit" :)

---

### Post by ronacc on 2008-08-08
If I hadn't translated that into something less spirited I would have been banned :lolflag:

---

### Post by autocrosser on 2008-08-08
"Fighting MS-ism one post at a time" ;)

:lolflag::lolflag::lolflag:

---

### Post by Nullack on 2008-08-09
Yeah, clearly the bug management is performing poorly in your case Ronacc. This is a bad bug and you have my support and Im sure everyone else's to ensure this is properly looked at and resolved. As it is intermittent its more problematic but the devs need to take some accountability for quality.

---

### Post by ronacc on 2008-08-09
first sorry nullack I got clumsy hitting the "new reply" button and may have accidently reported you . Well I went ahead and trashed ny third install and posted exact steps and a screenshot taken with a digital camera to the bug report if they can't understand that it is hopeless . recovered the system with chmod 755 /   .

---

### Post by exploder on 2008-08-09
ronacc, I am glad that you re-submitted the bug report. I have gone through the same kind of problems with bug reports twice before.

---

### Post by autocrosser on 2008-08-09
I just installed Alpha 3 on a spare drive & will "test it to death" in the logic that I might be able to add more weight to the report--I've been logging out & back in as root user to avoid the problem--so now I have another install to "trash"

---

### Post by ronacc on 2008-08-09
at least they seem to be paying attention the second time around . In the past I have let them "flipping me off" slide but this one is too potentialy harmful .

---

### Post by autocrosser on 2008-08-09
WOW--just happened to me while I was editing menu.lst....Found something odd in my syslog.

Aug  9 17:02:03 linux last message repeated 20 times
Aug  9 17:02:30 linux last message repeated 5 times
Aug  9 17:02:31 linux sensord: Sensor alarm: Chip it8718-isa-0290: in5: +0.00 V (min = +0.00 V, max = +4.08 V) [ALARM]
Aug  9 17:03:01 linux pulseaudio[6427]: protocol-esound.c: kicked client with invalid authorization key.
Aug  9 17:03:17 linux last message repeated 4 times
Aug 10 00:03:31 linux sensord: Sensor alarm: Chip it8718-isa-0290: in5: +0.00 V (min = +0.00 V, max = +4.08 V) [ALARM]
Aug 10 00:04:31 linux sensord: Sensor alarm: Chip it8718-isa-0290: in5: +0.00 V (min = +0.00 V, max = +4.08 V) [ALARM]
Aug  9 17:05:31 linux sensord: Sensor alarm: Chip it8718-isa-0290: in5: +0.00 V (min = +0.00 V, max = +4.08 V) [ALARM]
Aug  9 17:06:31 linux sensord: Sensor alarm: Chip it8718-isa-0290: in5: +0.00 V (min = +0.00 V, max = +4.08 V) [ALARM]
Aug  9 17:06:57 linux pulseaudio[6427]: protocol-esound.c: kicked client with invalid authorization key.

Notice the time in the centre---not sure why that happened....I had a terminal window open when it happened & cd'd to / & did a quick chmod 755 & all my icons came back...phew!!!!!

I'll add that to the bugreport....

---

### Post by ronacc on 2008-08-09
I noticed something like that checking my logs from the first time it happened , right at the time it occurs the time shown in the log jumps forward then back , I have no idea what that tells us . I'll look at the rest of my logs and see if it happens every time.
edit: checked my logs , yes that "time warp" is there on every occurence .

---

### Post by autocrosser on 2008-08-09
Just happened to me two more times--at least I had root terminals open each time, so the fix was "easy". I would post your time warp also--I would think it really has something to do with permission setting.

I will note that both times I was using Fileroller to look at grub splash files (in as root)

---

### Post by ronacc on 2008-08-09
added the sections of my syslog showing the time jump.

---

### Post by Gina on 2008-08-10
Yesterday's updates stopped all my Intrepids from booting up normally - I can only boot in recovery mode.  Not tried yet today, going out shortly.  When I have time I'll run the updates from command line and see if there's any improvement.  I'll report back what I find.

---

### Post by Nullack on 2008-08-16
Having persisted with this, it seems that file roller in the gnome trunk has this now fixed:

[http://bugzilla.gnome.org/show_bug.cgi?id=546698](http://bugzilla.gnome.org/show_bug.cgi?id=546698)

Once this gets into Ubuntu it will be nice to retest and close this off :)

---

### Post by ronacc on 2008-08-16
I hope it gets updated soon :) 
edit: I notice that upstream thinks it is "critical" as opposed to Ubuntus "low"

---

### Post by inportb on 2008-08-16
So is the workaround simply to chmod +x / ?

---

### Post by ronacc on 2008-08-16
it would be chmod +rx /     or chmod 755 /   . it has to be done as root so you would need to have a root password set or do it from recovery mode .

---

### Post by nanog on 2008-08-16
Gina,  I can only boot in recovery mode too.  Have you filed a bug about the new kernel panicking?

---

### Post by nanog on 2008-08-16
big filed for 2.6.25-5 kernel panic in generic mode.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258689](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/258689)

---

### Post by Gina on 2008-08-17
> **nanog said:**
> Gina,  I can only boot in recovery mode too.  Have you filed a bug about the new kernel panicking?Now appears fixed for me.  Alpha 4 seems OK in that respect on my machines.  I get most of the other known bugs though.

---

### Post by ronacc on 2008-08-17
several of the bugs I filed at alpha 1 are still here . just keep hoping .

---

### Post by Nullack on 2008-08-17
Good prompts to getting bugs moving:

* Finding the upstream bug/creating one and linking it to launchpad
* Asking people to confirm your bugs on IRC, this forum etcetc
* Getting more people to subscribe to the bug
* Having a go at further diagnosing the bug yourself

---

### Post by plun on 2008-08-18
> **ronacc said:**
> several of the bugs I filed at alpha 1 are still here . just keep hoping .

Well, this morning I was also badly hit and this must be a kernel bug.

Running a "[Ubuntu Kernel Next]("http://blog.phunnypharm.org/")"-kernel and all permissions was wrong and
/home was also broken, not recognized.

Ok with latest 2.6.26-5 kernel.

But how to find clues about this....:confused:

---

### Post by ronacc on 2008-08-18
I think there may be some permission problems lurking besides the fileroller bug , yesterday I moved a couple of gigs of work files from one box to the other by burning to dvd and then copying onto the other box from the dvd and all of the file permissions were changed to read only and this was with hardy on both boxes .

---

### Post by plun on 2008-08-18
> **ronacc said:**
> I think there may be some permission problems lurking besides the fileroller bug , yesterday I moved a couple of gigs of work files from one box to the other by burning to dvd and then copying onto the other box from the dvd and all of the file permissions were changed to read only and this was with hardy on both boxes .

The challenge for me is log files and which log files.

Probably also a SSH connection to get those logs or ?....the xsession
log would be nice to see.  

It must also be mounting errors when the kernel mounts all partitions
and checks permissions.

Rather impossible without a developer with knowledge to sort this out.

---

### Post by ronacc on 2008-08-18
if you d/l a puppy linux live cd it makes it very easy to mount your partitions and examine them and your logs , puppy is small so its a quick d/l and can run completly in ram  , I find it to be very handy to have around as a rescue tool or just to poke around when something goes wrong.

---

### Post by Nullack on 2008-08-19
good news!

[https://launchpad.net/ubuntu/+source/file-roller/2.23.6-0ubuntu1/+build/695992](https://launchpad.net/ubuntu/+source/file-roller/2.23.6-0ubuntu1/+build/695992)

This will hit the mirrors and be ready for us all to test very soon

---

### Post by plun on 2008-08-19
Yup....

[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005424.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005424.html)

> Bugs fixed:
     - #350640: sending an empty folder doesn't work. (lp: #55603)
     - #548020: "create archive" directory selection not working correctly.
 	       (lp: #230044)
     - #546698: file-roller-2.23.1/2.23.5 removes r/x bit for anyone but
                root from / (lp: #250021)
     - #547733: 7-zip tells about invalid command line
     - #547297: Crash reading zip/7za files with 7z version 4.55.
     - #546978: wrong icon for folders.
     - #547017: segfault in "Open with".
     - #546505: Debian packages not supported anymore. (lp: #258499)
     - #542424: Tar.bz2 archives create uncompressed archive files.
     - #546541: Typo and little errors in documentation.
     - LP#26662: file-roller fails to open .Z files. (lp: #26662)
   * debian/file-roller.mime:
     - new version update
   * debian/patches/70_autoconf.patch:
     - new version update


Se if I can reproduce my loss of permissions....

---

### Post by ronacc on 2008-08-19
It has hit the US repos and it seems to have fixed this one so I'm marking the thread solved . strange side effect though archive manager no longer shows up in the applications menu even though add/remove shows it as being there under "accessories" .

---

