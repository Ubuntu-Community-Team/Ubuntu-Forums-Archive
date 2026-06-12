---
title: "i have no desktop after upgrade"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cykotiktek on 2008-09-19
Well i did the upgrade from 8.04 to 8.10 and it just finished installing.  I can use my username and password to sign into the computer but I have no desktop.  So now i am signed into x-term but i am not sure what i can do to repair it.  If i can't repair it no biggie it's alpha i understand but i figured why not try to learn something new in the process.

---

### Post by ronacc on 2008-09-19
from the terminal try <sudo startx> and see what happens it may give you a basic desktop , you can also try <sudo /etc/init.d/gdm start>  . What video driver were you using in hardy , if it was one of the restricted ones you need a new version for intrepid .Also if you remove quiet splash from your boot line you can watch the boot and mabye see why gdm is failing to start . Note if you are using kubuntu substitue kdm for gdm .

---

### Post by TheBigT on 2008-09-19
I have the same issue. Your suggestion makes no sense, x and gdm are running fine after boot, and I could launch Firefox from the console (thus I can type this :)). 

The problem is that the Gnome environment doesn't come up. 

There are four rejected connection attempts in the Xorg log, so I think the X security settings got messed up and it won't let the default user open the desktop apps.

---

### Post by nanog on 2008-09-19
if gdm is running then the "gnome environment" is also running. try running nautilus or gnome-panel in a terminal (gnome-terminal) and letting us know what happens. its possible that during upgrade some dependencies got missed. you can also try reinstalling ubuntu-desktop to pull in necessary dependencies.

---

### Post by TheBigT on 2008-09-19
> **nanog said:**
> if gdm is running then the "gnome environment" is also running. try running nautilus or gnome-panel in a terminal (gnome-terminal) and letting us know what happens. its possible that during upgrade some dependencies got missed. you can also try reinstalling ubuntu-desktop to pull in necessary dependencies.

First I tried:
>export DISPLAY=:0.0
>gnome-panel &

this did not work, I got a "No protocol specified/Cannot open display" error. But if I did

> sudo gnome-panel &

... then the panel started. I could also start nautilus the same way. The window manager running at the time was x-window-manager. I tried to switch over to metacity with the "sudo" technique, but then X restarted and now I always get MAGIC-COOKIE errors, even after killing gdm and doing a manual startx.

---

### Post by Nullack on 2008-09-19
Upggrades are always problematic compared to fresh installs. It will require debugging. The ubuntu wiki has allot of useful info on debugging.

---

### Post by nanog on 2008-09-19
reinstall ubuntu-desktop. it should fix things or at least complain about unresolveable stuff.

---

### Post by TheBigT on 2008-09-19
> **nanog said:**
> reinstall ubuntu-desktop. it should fix things or at least complain about unresolveable stuff.

I reinstalled gdm and ubuntu-desktop, no change. IMHO the problem is not a dependency error, but some setting is out of sync. Unfortunately I'm no expert in X authentication, and don't really have time to become one...

---

### Post by satish_tvs on 2008-10-03
Hi Friends,

I am having the same problem with my Ubuntu. I kept my system
up to date with all updates. I was working on cross compiling
pango and dependent packages for arm. Suddenly when I restarted
login screen was not coming. It was alwasy showing busy sign. 

I uninstalled ubuntu-desktop and gdm.  I installed kubuntu-desktop.
Now I am able to login but no desktop. 

Please let me know any solution is found for this problem. 

Regards,
Sateesh

---

### Post by pvdeynse on 2008-10-07
got same problem, after upgrade 8.04 -> 8.10 beta no desktop after login username and password. Have been looking around for 2 days what could cause all this.

Finally looking at messages from my last upgrade I saw that a lot of gnome stuff could not be configured because the package "scrollkeeper" was not installed. I've installed above package, and now all is working fine again.
here is what I did:  

              sudo apt-get install scrollkeeper

looks like above problem is bug report
[https://bugs.launchpad.net/ubuntu/+source/rarian/+bug/276878](https://bugs.launchpad.net/ubuntu/+source/rarian/+bug/276878)

---

### Post by satish_tvs on 2008-10-07
Hi,

I tried to install scrollkeeper. But it was already installed
in the system. 

When I see syslog messages, there is some problem with
authentication of user. It is saying 

gdm[5120]: WARNING: Couldn't authenticate user

I am using VMWARE ubuntu guest on Windows XP system. 

I searched and now analysing some topics related to PAM
and dbus. 

If somebody can give me some info on authentication, it would
be fine. 

Regards,
Sateesh

---

### Post by martinlall on 2008-10-08
I did fresh install and using now 8.10
and i've got a question. 
Where the f is desktop? I have icons, folder etc stored on my desktop, but i can see them only in /home/me/Desktop folder but not on desktop!
WTF? Is this bug or just what kde 4.1 is?

Had this in suse too, but thought that's a bug and didn't try to do anything to fix it..

---

### Post by TheBigT on 2008-10-09
I was waiting to see if the beta version would solve the problem, but it's still present. Reinstalling scrollkeeper made no difference.

Is there some easy way to blow away all the X subsystem together with authentication and user rights and then reinstall clean?

If not, I guess I'm just not cut out for Linux, I'll go back to my XP installation that survived 5 years of updates without irreparably crashing. Ubuntu didn't even survive 5 months.

---

### Post by bretticus on 2008-10-09
> **TheBigT said:**
> ...I'll go back to my XP installation that survived 5 years of updates without irreparably crashing. Ubuntu didn't even survive 5 months.

I myself am peeved about my ati card not running compiz (w/o the proprietary driver. Obviously ATI's fault.) But I do remind you that you upgraded to a beta. Some issues like this are expected.

I, for one, will do some more research before upgrading Ubuntu to an beta/alpha again. I don't plan on booting Ubuntu again until I get that proprietary  driver or the open driver can at least allow me to use compiz. Point being, it will work (probably sooner than later), and I will be coming back!

---

### Post by bash on 2008-10-09
> **TheBigT said:**
> I was waiting to see if the beta version would solve the problem, but it's still present. Reinstalling scrollkeeper made no difference.

Is there some easy way to blow away all the X subsystem together with authentication and user rights and then reinstall clean?

If not, I guess I'm just not cut out for Linux, I'll go back to my XP installation that survived 5 years of updates without irreparably crashing. Ubuntu didn't even survive 5 months.

Have you tried just reinstalling Ubuntu all together? Complete fresh install. Backup any data you got, wipe the partition and reinstall Ubuntu. Maybe that helps.

---

### Post by jblackhall on 2008-10-09
> **martinlall said:**
> I did fresh install and using now 8.10
and i've got a question. 
Where the f is desktop? I have icons, folder etc stored on my desktop, but i can see them only in /home/me/Desktop folder but not on desktop!
WTF? Is this bug or just what kde 4.1 is?

Had this in suse too, but thought that's a bug and didn't try to do anything to fix it..

That's just what KDE 4.1 does.  You can add a folder plasmoid to your desktop so you can see what's in the folder.

---

### Post by martinlall on 2008-10-10
> **jblackhall said:**
> That's just what KDE 4.1 does.  You can add a folder plasmoid to your desktop so you can see what's in the folder.

Do you happen to know where the folder view settings file is?
I think, that if i make it 100% transparent and set the folder view size 1:1 with my screen size, it should do the trick..

---

### Post by ShirishAg75 on 2008-10-10
Isn't rariant supposed to be now the king instead of scrollkeeper?

```

aptitude show rarian-compat
Package: rarian-compat
New: yes
State: installed
Automatically installed: no
Version: 0.8.1-1ubuntu1
Priority: optional
Section: doc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 455k
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), librarian0 (>= 0.8.0), libstdc++6 (>= 4.1.1), xml-core (>= 0.05),
         docbook-xml
Conflicts: scrollkeeper
Replaces: librarian-dev (< 0.8.1), scrollkeeper
Provides: scrollkeeper
Description: Rarian is a documentation meta-data library (compatibility tools)
 Rarian (formerly Spoon) is a documentation meta-data library, designed as a replacement for Scrollkeeper.
Homepage: http://rarian.freedesktop.org/

```

It seems to have replaced scrollkeeper, anybody knows?

---

### Post by hari_home on 2008-10-10
This happened to me. I tried every thing and finally, I was able to recover by "fixing" x server in recovery mode.

Not a very technical answer but try the recovery mode of the latest kernel you have.

---

### Post by TheBigT on 2008-10-10
> **bash said:**
> Have you tried just reinstalling Ubuntu all together? Complete fresh install. Backup any data you got, wipe the partition and reinstall Ubuntu. Maybe that helps.

I tried to run the Live CD, and that works. So it's a configuration problem of the version on my HDD, not an incompatibility between Ubuntu and my machine.

If I'm going to invest several days on reinstalling and then reconfiguring and OS, it will be XP, because frankly I want an OS that just works, and not one that is a "project".

---

### Post by TheBigT on 2008-10-10
> **hari_home said:**
> This happened to me. I tried every thing and finally, I was able to recover by "fixing" x server in recovery mode.

Not a very technical answer but try the recovery mode of the latest kernel you have.

Didn't work :(

---

### Post by TheBigT on 2008-10-10
I tried regenerating the .Xauthority file, which helped a little, but I'm still getting authentication errors:

> 
AUDIT: Fri Oct 10 22:18:41 2008: 7128 X: client 1 connected from local host ( uid=0 gid=0 pid=7122 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: 129
AUDIT: Fri Oct 10 22:18:42 2008: 7128 X: client 2 connected from local host ( uid=106 gid=114 pid=7176 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: 129
AUDIT: Fri Oct 10 22:18:42 2008: 7128 X: client 3 connected from local host ( uid=106 gid=114 pid=7176 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: 129
AUDIT: Fri Oct 10 22:18:42 2008: 7128 X: client 3 disconnected
AUDIT: Fri Oct 10 22:18:45 2008: 7128 X: client 3 connected from local host ( uid=106 gid=114 pid=7176 )
  Auth name: MIT-MAGIC-COOKIE-1 ID: 129
AUDIT: Fri Oct 10 22:18:45 2008: 7128 X: client 4 rejected from local host ( uid=0 gid=0 pid=7406 )
AUDIT: Fri Oct 10 22:18:45 2008: 7128 X: client 4 disconnected
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7494 )
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 disconnected
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7495 )
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 disconnected
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7496 )
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 4 disconnected
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 2 disconnected
AUDIT: Fri Oct 10 22:18:59 2008: 7128 X: client 3 disconnected


Unfortunately the X logging code is totally ill-conceived and useless, because the pid disappears the moment the process stops (and of course it stops immediately when a connection to X fails) and there is no reason given for the rejection.

Any ideas?

---

### Post by crazy_fox on 2008-10-10
Hello

What i did to sort out this, was I went into the root console from failsafe boot.

Once there you have to manually bring up your network:

> ifconfig eth0 up
dhclient eth0

Notice if you are connected with wifi you have to setup the wifi connection:


> iwconfig ath0 essid "youressid"
iwconfig ath0 key yourkey
iwconfig ath0 rate 11M
ifconfig ath0 up
dhclient ath0

Ive assumed your devices might be not be eth0 and ath0.

Once your net is up (ping google.com), use aptitude to reinstall packages, apt-get to do upgrades if any etc.

Let me know how you get on

---

### Post by nanog on 2008-10-10
> I want an OS that just works, and not one that is a "project".

Have you tried creating a new user in root or recovery mode? This should generate a valid .Xauthority file. If this works you can then mv and chmod-chown your files into the new account.

---

### Post by crazy_fox on 2008-10-10
> **TheBigT said:**
> If I'm going to invest several days on reinstalling and then reconfiguring and OS, it will be XP, because frankly I want an OS that just works, and not one that is a "project".

It is true that anyone agreeing with the above is better off with an OS that will keep you at bay from fiddling around with stuff. Cause frankly if you cant read "Beta" stuck to something before you upgrade to it, then you need something to protect you (lock you out) from your computer. XP is probably a good solution for that.

---

### Post by wgrant on 2008-10-10
> **TheBigT said:**
> If I'm going to invest several days on reinstalling and then reconfiguring and OS, it will be XP, because frankly I want an OS that just works, and not one that is a "project".

If you run a beta, you can expect problems. It is the same as any other piece of software.

---

### Post by ruffneck on 2008-10-10
reinstalling Nautilus fixed this problem for me, it appears that a previous update removed it:

> sudo apt-get install nautilus

---

### Post by MacUntu on 2008-10-10
Finally some real beta action! Yay! :)

---

### Post by mister_pink on 2008-10-10
> **TheBigT said:**
> I want an OS that just works, and not one that is a "project".

I think it's already been said, but seriously, this is the beta. If you're not happy with breakage you shouldn't be using it. That is the whole point. Don't complain about the whole OS because of it - for me the vista beta was impossible to even install. If you want an OS that works you should have installed hardy.

---

### Post by wgrant on 2008-10-10
> **ruffneck said:**
> reinstalling Nautilus fixed this problem for me, it appears that a previous update removed it:

Ensure that ubuntu-desktop is installed too.

---

### Post by TheBigT on 2008-10-10
After learning a lot about strace, the nature of gdm and gnome, dpkg and a bunch of other stuff, I finally managed to figure out what happened.

I think I had two problems:
1. the .Xauthentication file was possibly corrupted
2. the alternatives/x-session-manager softlink jumped to startkde instead of gnome-session (but I didn't have the necessary KDE components, and the window manager stayed metacity anyways, so startkde just failed quietly) 

Solution to:
1. delete ~/.Xauthentication
2. run sudo update-alternatives --config x-session-manager and choose gnome-session

Things that would have helped a lot:
1. if gdm logged in the detailed log that it was starting startkde (strace says that it does do a readlink, so it has the information) 
2. if the x-session (and gnome-session, for that matter) log was included in the gdm.log

---
On the topic of beta software: I understand the nature of betas, but due to the utter crappiness of USB mass storage support in the Hardy kernel, I had no chance but to try the beta (it did make USB work a little better, but it's still borderline ridiculous).

Now on to the next challenge: why does Skype use 100% CPU since the upgrade? :(

---

### Post by ruffneck on 2008-10-11
> **wgrant said:**
> Ensure that ubuntu-desktop is installed too.

Thanks man, that actually fixed the compiz issues and other niggly stuff that were occuring. 

Cheers \\:D/

---

### Post by Noea on 2008-10-11
Hey 
id upgrade yesterday and the ubuntu-desktop and other pkg not configure after error with denependies , jockey gtk , nautilus and others :)
So id try to reinstal but my pkg is in the newest version . What id should do ??

---

