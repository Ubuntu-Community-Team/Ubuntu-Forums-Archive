---
title: "Running Teamviewer on 16.04"
date: 2016-06-30
forum: Installation &amp; Upgrades
---

### Post by paul263 on 2016-06-30
Hello everyone,

I have the following problem: I installed Teamviewer on Ubuntu 16.04, but for mysterious reasons I am unable to execute the program 'normally': when I click on the Teamviewer icon or when I type ```
teamviewer
``` in the terminal, the program doesn't start. 
Only typing the commands ```
sudo su
``` and then ```
sudo teamviewer
``` makes it start. 
It seems that Teamviewer requires root permissions at each startup but I don't know how to give them automatically. Would anyone have an idea of how to tackle this issue?

Thanks a lot in advance,
Paul

---

### Post by oldfred on 2016-06-30
I would never give root access to software on the Internet.

[http://arstechnica.com/security/2016/06/teamviewer-says-theres-no-evidence-of-2fa-bypass-in-mass-account-hack/](http://arstechnica.com/security/2016/06/teamviewer-says-theres-no-evidence-of-2fa-bypass-in-mass-account-hack/)

---

### Post by paul263 on 2016-06-30
Thank you for the advice, oldfred! No permanent root privilege for Teamviewer then.
Would you know if I could do something else to let this software launch at startup? (This was my initial goal)

---

### Post by QDR06VV9 on 2016-06-30
How did you install it?

---

### Post by paul263 on 2016-06-30
I downloaded the v11.0.57095 (deb 32-Bit / 64-Bit Multiarch) from the [official website]("https://www.teamviewer.com/en/download/linux/") and then typed on the terminal ```
sudo dpkg -i teamviewer_11.0.57095_i386.deb
```

---

### Post by QDR06VV9 on 2016-06-30
> **paul263 said:**
> I downloaded the v11.0.57095 (deb 32-Bit / 64-Bit Multiarch) from the [official website]("https://www.teamviewer.com/en/download/linux/") and then typed on the terminal ```
sudo dpkg -i teamviewer_11.0.57095_i386.deb
```

Good Job!:) That is what I hoped you did
TeamViewer has a script called teamviewerd.sysv available in **/opt/teamviewer/tv_bin/script.** 

All you need to do is make sure this script runs on startup. Making sure of this is relatively simple, just copy it to /etc/init.d like so:

```
cd /opt/teamviewer/tv_bin/script
sudo cp teamviewerd.sysv /etc/init.d/

```
Don't forget to make the script non-writable to anyone but the owner!

```
sudo chmod 755 /etc/init.d/teamviewerd.sysv
```

Then run

```
sudo update-rc.d teamviewerd.sysv defaults

```
The service will now start automatically with each boot. If you don't feel like rebooting, you can start the service manually with:

```
sudo service teamviewerd.sysv start
```
Hope This was Helpful

---

### Post by paul263 on 2016-07-01
Thank you runrickus for the time you took to write this detailed answer.
 I did it but unfortunately, it seems that it doesn't work: now on startup I have the error message 'System program problem detected'. In the details, it is written:

```
ExecutablePath: /opt/teamviewer/tv_bin/teamviewerd
Package: teamviewer (not installed)
ProblemType: Crash
CrashCounter: 1
UnreportableReason: The report belongs to a package that is not installed
```

I don't understand because Teamviewer is installed...

---

### Post by X-RED_Tech on 2016-07-01
Lucky you I had a freshly installed 16.04 in a miniPC and installed Teamviewer for testing. And the result was the same, it runs - the process is there - but the GUI doesn't open. Haven't run it as root and you shouldn't either.
Besides, Teamviewer always worked before with the normal users as it should so something is wrong now but not reason enough to even try running with elevated privileges.

The solution is actually quite simple: install WINE.
Yes, Teamviewer is still a Windows software wrapped with WINE to run in Linux. It used to pop up a dialog informing about the setup of wine in the first use. That didn't happen now so somehow it has issues with an freshly installed updated 16.04 (installed before in a couple of 16.04, no problems). With wine installed it just runs as usual, as always, as it should be. Not a clean solution but works.

---

### Post by QDR06VV9 on 2016-07-01
> **paul263 said:**
> Thank you runrickus for the time you took to write this detailed answer.
 I did it but unfortunately, it seems that it doesn't work: now on startup I have the error message 'System program problem detected'. In the details, it is written:

```
ExecutablePath: /opt/teamviewer/tv_bin/teamviewerd
Package: teamviewer (not installed)
ProblemType: Crash
CrashCounter: 1
UnreportableReason: The report belongs to a package that is not installed
```

I don't understand because Teamviewer is installed...

> **X-RED_Tech said:**
> Lucky you I had a freshly installed 16.04 in a miniPC and installed Teamviewer for testing. And the result was the same, it runs - the process is there - but the GUI doesn't open. Haven't run it as root and you shouldn't either.
Besides, Teamviewer always worked before with the normal users as it should so something is wrong now but not reason enough to even try running with elevated privileges.

The solution is actually quite simple: install WINE.
Yes, Teamviewer is still a Windows software wrapped with WINE to run in Linux. It used to pop up a dialog informing about the setup of wine in the first use. That didn't happen now so somehow it has issues with an freshly installed updated 16.04 (installed before in a couple of 16.04, no problems). With wine installed it just runs as usual, as always, as it should be. Not a clean solution but works.
I just must be lucky then but i had installed since trusty and it has just come along with me to now 16.10 yackkety.
I will do some more research here and report back soon.
I am curious about using Teamviewer with wine also..if someone here would let us know how that works out.
Thanks:)

---

### Post by X-RED_Tech on 2016-07-01
You always used Teamviewer with WINE ;)
We all do.
The Ubuntu/Debian .deb installer is the Windows code + WINE.

---

### Post by QDR06VV9 on 2016-07-01
> **X-RED_Tech said:**
> You always used Teamviewer with WINE ;)
We all do.
The Ubuntu/Debian .deb installer is the Windows code + WINE.

Yes I under stand that!:wink:
I just do not understand why you guys had problems installing the .deb package.:)
```
apt-cache policy teamviewer
teamviewer:i386:
  Installed: 11.0.57095
  Candidate: 11.0.57095
  Version table:
 *** 11.0.57095 100
        100 /var/lib/dpkg/status

```
```
apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1:1.6.2-0ubuntu15
  Version table:
     1:1.6.2-0ubuntu15 500
        500 http://us.archive.ubuntu.com/ubuntu yakkety/universe amd64 Packages


```
```
 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Yakkety Yak (development branch)
Release:    16.10
Codename:    yakkety


```

---

### Post by X-RED_Tech on 2016-07-01
> **runrickus said:**
> I just do not understand why you guys had problems installing the .deb package.:)

We didn't. It installed as usual but didn't run as usual: No GUI and not even the initial "setting up .wine" message but it started some process.
The OP mentions it worked as usual with sudo. ****I didn't test that****
Then I installed WINE, tried Teamviewer again and it worked as usual :p

So it's probably something in 16.04 (or the installer needs update).
I didn't have this problem with Teamviewer in a 16.04 notebook (upgraded from 15.10) nor in a desktop installed around February when 16.04 was still dev.

---

### Post by QDR06VV9 on 2016-07-01
> **X-RED_Tech said:**
> We didn't. It installed as usual but didn't run as usual: No GUI and not even the initial "setting up .wine" message but it started some process.
The OP mentions it worked as usual with sudo. ****I didn't test that****
Then I installed WINE, tried Teamviewer again and it worked as usual :p

So it's probably something in 16.04 (or the installer needs update).
I didn't have this problem with Teamviewer in a 16.04 notebook (upgraded from 15.10) nor in a desktop installed around February when 16.04 was still dev.

Understood.
Here are some Deps needed for the OP, since you have it running with wine.
```
 apt-cache showpkg teamviewer
Package: teamviewer:i386
Versions: 
11.0.57095 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: 33697fb60badd3f816da5b267ad1a01a


Reverse Depends: 
Dependencies: 
11.0.57095 - libc6:i386 (2 2.4) libgcc1:i386 (0 (null)) libasound2:i386 (0 (null)) libdbus-1-3:i386 (0 (null)) libexpat1:i386 (0 (null)) libfontconfig1:i386 (0 (null)) libfreetype6:i386 (0 (null)) libjpeg62:i386 (0 (null)) libpng12-0:i386 (0 (null)) libsm6:i386 (0 (null)) libxdamage1:i386 (0 (null)) libxext6:i386 (0 (null)) libxfixes3:i386 (0 (null)) libxinerama1:i386 (0 (null)) libxrandr2:i386 (0 (null)) libxrender1:i386 (0 (null)) libxtst6:i386 (0 (null)) zlib1g:i386 (0 (null)) teamviewer5:i386 (0 (null)) teamviewer6:i386 (0 (null)) teamviewer7:i386 (0 (null)) teamviewer8:i386 (0 (null)) teamviewer9:i386 (0 (null)) ttf-liberation:i386 (16 (null)) fonts-liberation:i386 (0 (null)) teamviewer5:i386 (0 (null)) teamviewer6:i386 (0 (null)) teamviewer7:i386 (0 (null)) teamviewer8:i386 (0 (null)) teamviewer9:i386 (0 (null)) 
Provides: 
11.0.57095 - 
Reverse Provides: 


```
My bit to try and help is all.
Cheers

---

### Post by paul263 on 2016-07-16
Thank you both for this productive discussion and sorry for the delay of my reply.

@X-RED_Tech: I tried to do the install by myself with Wine as you described it, but I have the same issue at the end. Teamviewer won't start when I click on the icon.

---

### Post by paul263 on 2016-07-17
Problem solved by installing TeamViewer 10 instead of TeamViewer 11. For those who might encounter the same problem as mine, the solution was to install version v10.0.460203 'TeamViewer deb 32 Bit/64 Bit Multiarch' from the [official website]("https://www.teamviewer.com/en/download/previous-versions/") by typing on Terminal ```
sudo dpkg -i teamviewer_10.0.46203_i386.deb
```

Hope it may help!
 And thanks again oldfred, runrickus and X-Red_Tech for your contribution to this topic.


EDIT: Would it be possible to change the name of the topic from 'How to permanently give root privileges to an application?' to 'Problem with TeamViewer on Ubuntu 64 bit' please? I think the previous title is less appropriate than expected.

---

### Post by vasa1 on 2016-07-17
> **paul263 said:**
> Problem solved by installing Teamviewer 10 instead of Teamviewer 11. For those who might encounter the same problem as mine, the solution was to install version v10.0.460203 'TeamViewer deb 32 Bit/64 Bit Multiarch' from the [official website]("https://www.teamviewer.com/en/download/previous-versions/") by typing on Terminal ```
sudo dpkg -i teamviewer_10.0.46203_i386.deb
```

Hope it may help!
 And thanks again to oldfred, runrickus and X-Red_Tech for your contribution to this topic.
@paul263, you can mark this thread [SOLVED] as described in [How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

May I also suggest you edit the first post to give the thread a title that reflects the actual problem you had. Something like "Running Teamviewer on 16.04"? You need to click on "Go Advanced" after clicking "edit" on your first post. It's possible you may encounter some difficulty brought about by recent changes to the forum. In which case, no big deal. It's just a suggestion!

---

### Post by QDR06VV9 on 2016-07-17
> **paul263 said:**
> Problem solved by installing TeamViewer 10 instead of TeamViewer 11. For those who might encounter the same problem as mine, the solution was to install version v10.0.460203 'TeamViewer deb 32 Bit/64 Bit Multiarch' from the [official website]("https://www.teamviewer.com/en/download/previous-versions/") by typing on Terminal ```
sudo dpkg -i teamviewer_10.0.46203_i386.deb
```

Hope it may help!
 And thanks again oldfred, runrickus and X-Red_Tech for your contribution to this topic.


EDIT: Would it be possible to change the name of the topic from 'How to permanently give root privileges to an application?' to 'Problem with TeamViewer on Ubuntu 64 bit' please? I think the previous title is less appropriate than expected.

Glad to hear this, and thanks for sharing your solution.
And I have Edited the Thread Title.

---

