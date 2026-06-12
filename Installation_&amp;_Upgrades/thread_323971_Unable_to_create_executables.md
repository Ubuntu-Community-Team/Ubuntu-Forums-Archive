---
title: "Unable to create executables"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2006-12-23
I can't seem to find the cause or fix for this problem.   Me -> ](*,) 

When ever I try to run " ./configure " on a downloaded application/driver/whatever
I always get the same error.

 configure: error: C compiler cannot create executables

This has happened to a number of different attempted installs - each from a different source.
The only consistency is this error so, obviously, none of these programs have been installed.
 
I'm still at the "Novice" stage with Linux but, have worked with 'puters for last 12yrs and 
originally started "playing" with them in 1977 as a15yr old.


Any and all help gratefully received.

---

### Post by taurus on 2006-12-23
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```
Then, run your ./configure again...

---

### Post by netsurfau on 2006-12-23
Thanks Taurus, Looks like that fixed the problem.

Now to get the "make" to work.  Current install's documentation says it set the destination
directories automatically.  So, of course, I get an error msg wanting a destination.

I will learn all this - eventually

---

### Post by taurus on 2006-12-23
```
./configure
make
**sudo** make install
```

---

### Post by netsurfau on 2006-12-23
Error Msg received after "sudo make install"

make: *** No rule to make target `install'.  Stop.

Will go to author's site and file a Bug Report & see how I go.

Thanks for the help.

---

### Post by taurus on 2006-12-23
What's the name of the app that you try to build from source?  Usually, there should be a README or INSTALL telling you exactly what you need to do to install it...

---

### Post by netsurfau on 2006-12-23
I'm trying to install "IMWheel" so, I can get my 5 button trackball to use all buttons.

The "Install" text file says "make install" by default, puts the files where they belong under
/usr/local/**
Have attached the Install file, in case it can help you work this out.
As I've said before, I'm quite a novice with Linux, but can work in command line fairly confidently.  Studying Computer Forensics at the local Tech college and we've just finished an intro to Linux (Red Hat), which was nearly completely command line access only.

Thanks again Taurus, your help is greatly appreciated.

Luke

---

### Post by taurus on 2006-12-23
Don't see any attachment but if you tell me where to download it, I will check it out myself!  ;)

---

### Post by netsurfau on 2006-12-23
Still learning my way around here.
I downloaded the source code from: 
[http://sourceforge.net/project/showfiles.php?group_id=14292](http://sourceforge.net/project/showfiles.php?group_id=14292)

Thanks mate

---

### Post by taurus on 2006-12-23
> **netsurfau said:**
> Still learning my way around here.
I downloaded the source code from: 
[http://sourceforge.net/project/showfiles.php?group_id=14292](http://sourceforge.net/project/showfiles.php?group_id=14292)

Thanks mate

Do you get this error message when you run ./configure?

```

checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XCreateWindow in -lX11... yes
checking for XextAddDisplay in -lXext... yes
checking for XtFree in -lXt... yes
checking for XmuInternAtom in -lXmu... no
checking for XTestFakeDeviceKeyEvent in -lXtst... no
configure: error: IMWheel depends on the XTest extention!

```
Looks like you need to install xtest extension first before you can build imwheel...

I am not sure if this is the right one!!!
[http://xtest.netbeans.org/XTest_installation.html](http://xtest.netbeans.org/XTest_installation.html)

Actually, I think this page has the right info about xtest extension thing!!!
[http://www.google.com/search?hl=en&q=xtest+for+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=xtest+for+linux&btnG=Google+Search)

I guess you have to download the .rpm (for RedHat) and use alien to convert it to .deb and install it!!!

---

