---
title: "Wine problems.."
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by Itachi89 on 2006-08-27
I am all new to Ubuntu (and Linux) and I am trying to get Wine to work.

I keep getting this error though:

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

I would be very happy if someone could please help me! I have Nvidia graphic card by the way...

---

### Post by croak77 on 2006-08-27
What are you doing to get this error?

---

### Post by Itachi89 on 2006-08-27
> **croak77 said:**
> What are you doing to get this error?

winecfg

---

### Post by croak77 on 2006-08-27
Did you build you own version of wine or use the .deb in the repo?

---

### Post by Itachi89 on 2006-08-27
> **croak77 said:**
> Did you build you own version of wine or use the .deb in the repo?

the .deb one

---

### Post by Itachi89 on 2006-08-27
I am trying to get it to run with WoW, but if I try wine wow.exe I get this:

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program\\World_of_Warcraft\\wow.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program\\World_of_Warcraft\\wow.exe" failed, status c0000135

please help me with both things!

---

### Post by Itachi89 on 2006-08-28
bump! Please help me!

---

### Post by nikki on 2006-08-31
I get this same error. This occurs for me as well after trying winecfg. It gives the error above. I first went ./configure to configure the install, then 'make depend' and 'sudo make install'. I am running a 6800GT and with my video drivers updated as well. If anymore information is needed I will try to comply quickly =)

Since I see someone else posted a different error within the same thread, I'll post the error message I get.

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

---

### Post by nikki on 2006-09-01
I have updated to wine 0.9.20  with the same error when I enter winecfg.

---

### Post by nikki on 2006-09-02
Bumping, hoping for some help. Don't know if I should just try another distro or if it's a problem with my computer.

---

### Post by nikki on 2006-09-02
I have solved the problem myself. I downloaded the driver from this post on codeweavers and placed it into /libs/wine/ folder before recompiling and reinstalling.

[http://www.codeweavers.com/bin/view_attachment?id=8149](http://www.codeweavers.com/bin/view_attachment?id=8149)

This link goes directly to the file.

---

### Post by Itachi89 on 2006-09-05
alright, I have a 6800GT aswell so Im going to try this when I get home, thanks a lot m8 now I can keep ubuntu!

---

### Post by komputes on 2006-09-18
Hey guys, this Wine thing sounds great, it is amazing how the world of computers is changing. I have a few questions for those of you using Ubuntu. Is  there a Ubuntu specific tutorial on what need to be done to install and use Wine on Linux. Is there a place with guides for all the Win32 applications that people were successful in using Ubuntu/Wine. Another intrest: If it is possible to use Win32 Apps on Linux, has anyone ever tried finding a way to use Mac OS X applications on Linux. Granted, it must be much easier due to the similarities between BSD Unix and Linux.

---

### Post by bolt212 on 2006-10-24
> **nikki said:**
> I have solved the problem myself. I downloaded the driver from this post on codeweavers and placed it into /libs/wine/ folder before recompiling and reinstalling.

[http://www.codeweavers.com/bin/view_attachment?id=8149](http://www.codeweavers.com/bin/view_attachment?id=8149)

This link goes directly to the file.


i did this (i put the file in /usr/lib/wine because there wasn't a /lib/wine directory...)

and now i get this error. when i type winecfg


```
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libwine_unicode.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libwine_unicode.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
```

this is so dang frustrating.     i installed wine using automatix

---

### Post by SendDerek on 2006-10-29
I have been having the same issues as you guys...

There is another thread that has this same issue and I wanted to link them together.

So, it's here at:
[http://ubuntuforums.org/showthread.php?p=1682928#post1682928](http://ubuntuforums.org/showthread.php?p=1682928#post1682928)

I posted on that thread the problems that I've been having with this as well.  I'm going to quote myself on this:

> 
I've been getting this same error message. 

I tried what sumo had to say, but I couldn't find winex11.drv.so in the directory he specified.  I actually found it in a picassa directory:
"sudo cp /opt/picasa/wine/lib/wine/winex11.drv.so /usr/local/lib /wine/"

Well, I tried this method and ran winecfg (BTW: I'm working with wine version 0.9.24) and I recieved a different error message:

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": l ibwine_unicode.so.1: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).

```

Does anybody know what might be happening?

I don't know much about how wine works, but is it possibly the wrong winex11.drv.so file for the wine version?

If we need to, lets step back to the original problem with:
```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:imagelist:ImageList_ReplaceIcon no color!

```


This remains unresolved for myself.  I was hoping since this thread is more active than the other that we could get a resolution...

Thanks!

PS For the sake of completeness, I recieved the error after building wine from ./configure; make depend; make; make install and then trying "winecfg".  I have placed the winex11.drv.so file into the suggested directory without re-compiling it.

---

### Post by Xenix on 2006-11-22
I have made a post in another, less active thread already, but is there any solution to this yet?  I get the same error when compiling Wine 0.9.25 from source.  I have to compile from source to apply the Subspace / Continuum patch.

---

### Post by Xenix on 2006-11-24
*BUMP*
Anyone have any solutions / fixes yet?

---

### Post by wamarler on 2007-02-17
So here's what I did:

apt-cache search wine | grep lib (find all the wine library packages)

apt-get install libwine libwine-gl

I use Debian, not Ubuntu, but if they use the same package repositories then all these libs are downloaded and installed to /usr/lib NOT /usr/local/lib, where wine is looking for them. Once you've installed them check /usr/lib for the wine directory and that it's populated and then create a symlink:

ln -s /usr/lib/wine /usr/local/lib/wine

Once I did that I had no problems.

---

