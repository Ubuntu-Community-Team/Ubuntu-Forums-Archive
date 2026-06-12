---
title: "How to install gcc and build-essential without apt-get ?"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by xoros on 2005-06-14
Why wasn't gcc included in the default installation?  I am finding it a real pain to install.   I don't have an internet connection in Ubuntu... (as I don't have broadband or a detected modem) so I am downloading the .debs through windows.  

Is this even possible or is there endless dependencies and problems? 

This really sucks for people with no broadband access and/or modem detection.  Isn't there any answer?

---

### Post by Leif on 2005-06-14
It should be included in the installation cd. Just put it in the cd drive and try again.

---

### Post by xoros on 2005-06-14
[QUOTE=Leif]It should be included in the installation cd. Just put it in the cd drive and try again.[/QUOTE]

So your saying to try apt-get install with the cd in ?  I won't have to update my /etc/apt/sources.lst to point to the cdrom drive or even mount the cdrom first ?

---

### Post by Leif on 2005-06-14
Your cd should be auto-mounted when you insert it, and your sources should include it by default. Disable all the net based sources and search for gcc, you should get what's on the cd. 

I'm afraid I'm working by second hand info here as I do have net access at home and don't install things from the cd, but before answering your first post I searched the forum for "gcc cd" and found threads answering the same question, so I guess it should work.

---

### Post by xoros on 2005-06-14
[QUOTE=Leif]Your cd should be auto-mounted when you insert it, and your sources should include it by default. Disable all the net based sources and search for gcc, you should get what's on the cd. 

I'm afraid I'm working by second hand info here as I do have net access at home and don't install things from the cd, but before answering your first post I searched the forum for "gcc cd" and found threads answering the same question, so I guess it should work.[/QUOTE]

That didn't work for sh*t.  First I commented out all the lines in sources.list then I ran package manager and all I got was a bunch of errors about broken packages,  it didn't even look at the cd.   

So I went into terminal and tried apt-get install and that just listed the dependencies and wouldn't install.... again it did not even look at the cd.

---

### Post by Leif on 2005-06-14
[QUOTE=xoros]That didn't work for sh*t.  First I commented out all the lines in sources.list then I ran package manager and all I got was a bunch of errors about broken packages,  it didn't even look at the cd.   

So I went into terminal and tried apt-get install and that just listed the dependencies and wouldn't install.... again it did not even look at the cd.[/QUOTE]

Watch your language. I was only trying to help, but I won't continue that mistake.

---

### Post by az on 2005-06-14
[QUOTE=xoros]That didn't work for sh*t.  First I commented out all the lines in sources.list then I ran package manager and all I got was a bunch of errors about broken packages,  it didn't even look at the cd.   

So I went into terminal and tried apt-get install and that just listed the dependencies and wouldn't install.... again it did not even look at the cd.[/QUOTE]


A cd can be a repo like any other.  The difference is that you are prompted for the cd when it is needed.

If you do not have the cdrom as the very fist repo on your list (it was there by default, you may have deleted it) you can make another entry for it from the command line.

sudo apt-cdrom add

sudo apt-get update

sudo apt-get install build-essential

Also, please change your tone or no one will be nice to you.  Thanks!

---

### Post by xoros on 2005-06-14
[QUOTE=azz]A cd can be a repo like any other.  The difference is that you are prompted for the cd when it is needed.

If you do not have the cdrom as the very fist repo on your list (it was there by default, you may have deleted it) you can make another entry for it from the command line.

sudo apt-cdrom add

sudo apt-get update

sudo apt-get install build-essential

Also, please change your tone or no one will be nice to you.  Thanks![/QUOTE]

Thanks azz that worked.  It would have been nice if that was documented somewhere,  maybe I wouldn't have had that tone then.  

I guess it is too hard to add simple things like this to the guide or faq.  :roll:

---

### Post by deadpickle on 2005-06-14
New to Linux here
I did the action
sudo apt-get install build-essential
but I keep geting this THING
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter
I insert the Ubuntu install disc (cause its the only disc i have) and nothing happens. What do I do?

---

### Post by xoros on 2005-06-14
[QUOTE=deadpickle]New to Linux here
I did the action
sudo apt-get install build-essential
but I keep geting this THING
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter
I insert the Ubuntu install disc (cause its the only disc i have) and nothing happens. What do I do?[/QUOTE]

This is what I did: 
boot up and go to console login
sudo mount /dev/cdrom /media/cdrom
sudo aptitude install build-essential
sudo aptitude install linux-headers-$(uname -r)

If you had not changed anything in the sources.list since installing ubuntu it will look at the cd as a repository.

---

### Post by xoros on 2005-06-14
My next problem is ./configure still doesn't work.  It is now looking for flex.  I guess I am basically giving up on the idea that I can do anything in linux without an internet connection.  

I don't see why it is such a pain installing .debs manually.... it never works.  Why can't there be just whole packages with all its dependencies included ????

---

### Post by az on 2005-06-15
[QUOTE=xoros]My next problem is ./configure still doesn't work.  It is now looking for flex.  I guess I am basically giving up on the idea that I can do anything in linux without an internet connection.  

I don't see why it is such a pain installing .debs manually.... it never works.  Why can't there be just whole packages with all its dependencies included ????[/QUOTE]

Is flex not on the cd?

---

### Post by az on 2005-06-15
[QUOTE=deadpickle]New to Linux here
I did the action
sudo apt-get install build-essential
but I keep geting this THING
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter
I insert the Ubuntu install disc (cause its the only disc i have) and nothing happens. What do I do?[/QUOTE]


If you did not change any hardware, and you only have one cdrom, file a bug report.  Ubuntu should be mounting and using the cd right after you hit enter.

---

### Post by Joeb on 2005-06-15
[QUOTE=xoros]My next problem is ./configure still doesn't work.  It is now looking for flex.  I guess I am basically giving up on the idea that I can do anything in linux without an internet connection.  

I don't see why it is such a pain installing .debs manually.... it never works.  Why can't there be just whole packages with all its dependencies included ????[/QUOTE]


While the philosphy of .debs is not to have one mega-package, it normally handles the depencies quite well.  The problem as you have already guessed, is that without an internet connection, you don't have access to the repositories.

Actually, I think you have a compound problem.  You are trying to install packages without an internet connection and you are trying to install source packages to compile.  Chances are that if what you are wanting to install is already available (in a repository), you could just apt-get it, assuming you were connected to the internet.

The workaround you need for not having an internect connection (is it broke, or you just don't have a connection) is that you would need to download the repositories from somewhere else and then you could access them off-line so to speak.  That is, however, a lot of downloading and is why some distros ship with five or six CDs, so you don't have to.  However, those same distros make you download five or six CDs when you won't use most of the stuff on them, so it's a trade off.

Again, I don't think the problem you are having is with .debs, but is with not having access to the repositories.  Out of curiousity, what are you trying to install by compiling?

---

### Post by davegod75 on 2005-06-15
[QUOTE=Joeb]While the philosphy of .debs is not to have one mega-package, it normally handles the depencies quite well.  The problem as you have already guessed, is that without an internet connection, you don't have access to the repositories.

Actually, I think you have a compound problem.  You are trying to install packages without an internet connection and you are trying to install source packages to compile.  Chances are that if what you are wanting to install is already available (in a repository), you could just apt-get it, assuming you were connected to the internet.

The workaround you need for not having an internect connection (is it broke, or you just don't have a connection) is that you would need to download the repositories from somewhere else and then you could access them off-line so to speak.  That is, however, a lot of downloading and is why some distros ship with five or six CDs, so you don't have to.  However, those same distros make you download five or six CDs when you won't use most of the stuff on them, so it's a trade off.

Again, I don't think the problem you are having is with .debs, but is with not having access to the repositories.  Out of curiousity, what are you trying to install by compiling?[/QUOTE]
 speaking of gcc...i did a "which gcc" command and it's not working...even though /usr/bin is in my path and gcc-3.3 is installed.  

this is causing problems for me as i'm trying to install vmware

---

### Post by Joeb on 2005-06-15
[QUOTE=davegod75]speaking of gcc...i did a "which gcc" command and it's not working...even though /usr/bin is in my path and gcc-3.3 is installed.  

this is causing problems for me as i'm trying to install vmware[/QUOTE]


On my system /usr/bin/gcc is a symlink to /usr/bin/gcc-3.3.  Is that symlink missing on your system?

---

### Post by High_Yield on 2008-03-10
> **Leif said:**
> Watch your language. I was only trying to help, but I won't continue that mistake.

Oh no!  Now we've lost his guidance forever as he won't make that mistake again.

Set Sensitivity=Sensitivity.CryBaby;

---

