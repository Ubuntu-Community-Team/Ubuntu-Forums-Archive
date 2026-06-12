---
title: "msttcorefonts install error"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by onthefritz on 2007-03-21
Well, for some reason my system does not want to install msttcorefonts. Here is the error message I a getting. I am running 6.10.

```

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--09:39:53--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--09:40:03--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.

```

that is not all the output but it all looks just like it. Failing on a connection to a few sites.

Any ideas?

---

### Post by floke on 2007-03-21
Why don't you just grab them with apt-get - they're in the repos?

---

### Post by onthefritz on 2007-03-21
That is part of the output of:

```
sudo apt-get install msttcorefonts
```

For some reason it goes through this and it will make other installs fail. One example is the ATI drivers. for some reason it does the same thing.

---

### Post by floke on 2007-03-21
Why is it trying to pull it from sourceforge??
Try disabling the 3rd party repos - everything except the universe and multiverse etc. and try it again.

---

### Post by yabbadabbadont on 2007-03-21
The microsoft fonts are hosted on the various sourceforge mirrors.  The update-ms-fonts script is being run as part of the postinstall operations of the msttcorefonts package.  That is what is being displayed.  Unfortunately, sourceforge mirrors are notorious for being unreliable.  Some will work one day and then not the next.  However, it looks to me like he is having DNS problems since the errors indicate a failure to resove the sourceforge mirror domain names.

---

### Post by onthefritz on 2007-03-22
It does seem that I am not able to get to any of the addresses. And you are right, it is the update-ms-fonts script that is fialing.

Here is a list of the sites that I can't get to. Please let me know if you can get to them.

[http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)  -- I was able to download the file from this one.

Is there a way for me to have it look to a local file for this update?

---

### Post by yabbadabbadont on 2007-03-22
> **onthefritz said:**
> It does seem that I am not able to get to any of the addresses. And you are right, it is the update-ms-fonts script that is fialing.

Here is a list of the sites that I can't get to. Please let me know if you can get to them.

[http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
[http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)  -- I was able to download the file from this one.

Is there a way for me to have it look to a local file for this update?

Just edit the /usr/sbin/update-ms-fonts script and change the list of mirrors so that only the one you can reach is listed.  Just change it so that it goes from this:
```
URLROOTS="http://belnet.dl.sourceforge.net/sourceforge/corefonts/
         http://easynews.dl.sourceforge.net/sourceforge/corefonts/
         http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/
         http://aleron.dl.sourceforge.net/sourceforge/corefonts/
         http://cesnet.dl.sourceforge.net/sourceforge/corefonts/
         http://switch.dl.sourceforge.net/sourceforge/corefonts/"
```
To this:
```
URLROOTS="http://switch.dl.sourceforge.net/sourceforge/corefonts/"
```

---

### Post by Gibran on 2007-03-24
I am having the same issue and tried the solution you suggest with no luck. I have actually lost interest in the darn fonts, it's just the annoyance of getting the same error every time I update Ubuntu that brought me here. How can I disable this package so it doesn't try the installation again? Thanks!

---

### Post by jrekkedal on 2007-03-24
First run the command:

```
sudo gedit /usr/sbin/update-ms-fonts
```


Edit the section that looks like this:
```

URLROOTS="http://belnet.dl.sourceforge.net/sourceforge/corefonts/
         http://easynews.dl.sourceforge.net/sourceforge/corefonts/
         http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/
         http://aleron.dl.sourceforge.net/sourceforge/corefonts/
         http://cesnet.dl.sourceforge.net/sourceforge/corefonts/
         http://switch.dl.sourceforge.net/sourceforge/corefonts/"
```

So that it looks like this:
```
URLROOTS="http://belnet.dl.sourceforge.net/sourceforge/corefonts/
         http://easynews.dl.sourceforge.net/sourceforge/corefonts/
         http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/
         http://aleron.dl.sourceforge.net/sourceforge/corefonts/
         http://cesnet.dl.sourceforge.net/sourceforge/corefonts/
         http://switch.dl.sourceforge.net/sourceforge/corefonts/
         http://sft.if.usp.br/msttcorefonts/"
```

Run the package again, or the apt-get and it should work. Did for me.

---

### Post by zemitras on 2007-04-04
I'm having the same problem now... Can someone tell me a working mirror for theres fonts? 

Thanks

---

