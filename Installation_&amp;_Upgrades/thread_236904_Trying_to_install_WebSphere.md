---
title: "Trying to install WebSphere"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by timka1 on 2006-08-15
I am trying to install the IBM WebSphere Application Server Community Edition which appears to be a slimmed down version of the  commercial Java App Server which I use at work. IBM are pushing it hard on ads on the sourceforge site.

[http://websphere.dl.sourceforge.net/wasce_setup-1.0.1.2-unix.bin](http://websphere.dl.sourceforge.net/wasce_setup-1.0.1.2-unix.bin) 

but I'm not sure how to execute a .bin file. There is a comment in the very skimpy installation instructions that says that renaming from .bin to .sh allows the file to be executed from the desktop. However having done this and double clicked it just shows a busy cursor for a few seconds and then stops. No install appears to have taken place.

Anyone else done this or knows how to execute .bin or .sh files?

---

### Post by NetworkGuy on 2006-08-15
I believe you can do 

chmod +x filename.bin to make it executable.

---

### Post by timka1 on 2006-08-15
I changed the .bin installer file to allow execution but when I double clicked it same result: busy cursor, tab titled "opening... " appears in bottom bar but disappears after a few seconds.

I think an application to install is meant to appear but obviously it's either not possible on Ubuntu or I'm doing something wrong!

---

### Post by TomFrost on 2006-08-20
Most likely what's happening is that the installer is either running in the CLI, or it's hitting an error before you see anything.  You'll probably also need to run it as the root user.  Try opening up a terminal window and cd'ing to the directory with the /bin file, then execute the following commands.  Substitute the filename where "filename.bin" appears.

chmod +x filename.bin
sudo ./filename.bin

That will as you for your password and either put you in the installer, or it will give you an error that you can post here :)

Tom

---

### Post by timka1 on 2006-08-25
Apologies for delay in responding.

Good news (for me at least!) is that I got WebSphere Community Edition installed and running.

Didn't see advice from TomFrost until after I'd done it: in fact I managed to run the installer as follows:

```
sudo sh *installerfile*.bin
```

Other gotchas to be aware of: 

[INDENT]Although Ubuntu appears to have a Java runtime of the correct version (1.4.2), WebSphere also insists on it being either the Sun or IBM version. In other words you are best off choosing the IBM installer package that includes the IBM Java SDK.[/INDENT] 

[INDENT]Then, when I had downloaded that, I found the Java SDK is a .rpm package which is designed for Red Hat Linux. However I read it can be converted using a Linux utility called "alien" which allows Debian-based system to run .rpm packages.[/INDENT] 

You can tell I had fun can't you! :rolleyes:

Anyway it seems to be working OK now and it has a lot of features which I'm hoping to get my teeth into soon!

Be aware that Ubuntu (or Debian for that matter) is not a "supported" platform as far as IBM are concerned just in case anyone out there is thinking of getting into it in a big way for commercial purposes.

---

