---
title: "[SOLVED] Major Hardy upgrade problems (my fault entirely)"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Theo148 on 2008-04-25
Well I guess I should get straight to the point. My laptop's battery conked out a couple of months ago, so I removed it (since the laptop wouldn't run properly otherwise) and have been running my laptop on just AC power ever since (I rarely need to bring it anywhere anyway).

The serious issues started when my AC power cord started to wear down, and eventually broke and frayed at one point, leading to a barrage of random and extremely frustrating shutdowns. Eventually, I managed to tape a small piece of aluminium foil around the frayed area, and that seemed to fix the problem.

Yesterday I decided I would let my computer upgrade from Gutsy to Hardy overnight - the whole thing was running smoothly so I didn't think there would be any problems. However, when I came to check on it in the morning, all it showed was a blank screen, and it refused to boot into both Ubuntu (including recovery mode) and Windows, randomly shutting down when I tried.

So I borrowed a power cord from a friend (which I'm using now) and since the installation had probably been interrupted, I ran the trusty 'dpkg --configure -a'. It seemed to be working for a while, but quit shortly afterwards with a long stream of dependency errors.

I'm thinking of giving 'apt-get install ubuntu-desktop' a go - will that work? And if it won't, is there any other way to complete the installation?

---

### Post by forestpixie on 2008-04-25
Not sure but maybe install -f will help

sudo apt-get install -f

---

### Post by Theo148 on 2008-04-25
Okay, I'll give that a shot.

Although come to think of it, won't apt-get just ask me to run 'dpkg --configure -a' again?

---

### Post by Theo148 on 2008-04-25
Confirmed sadly - apt-get just tells me that dpkg was interrupted and asks me to run 'dpkg --configure -a', which of course always exits due to its dependency errors.

---

### Post by forestpixie on 2008-04-25
See if you can find out from dpkg what is actually causing the problem in the first place, this command I think will 
> Searches for packages that have been installed only partially on your system. dpkg will suggest what to do with them to get them working.

dpkg -C

if you're running from recovery you won't need sudo I think

---

### Post by Theo148 on 2008-04-25
Okay - I'll reboot and try that (ugh, I'm stuck in Windows >.< ).

Thans for the assistance by the way. :)

---

### Post by Theo148 on 2008-04-25
All right, I've gotten a marginal success at last. dpkg indicated that I had only one problem package that was stopping all the rest: 'dbus'. It recommended that I run

```
dpkg --configure dbus
```

I did that and it didn't work, but at least there's some error code to work with:

```
dpkg --configure dbus
Setting up dbus (1.1.20-1ubuntu1)...
Warning: the home dir /var/run/dbus you specified can't be accessed: No such file or directory
The user 'messagebus' already exists. Exiting.
chown: cannot access '/var/run/dbus': No such file or directory
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dbus
```

---

### Post by forestpixie on 2008-04-25
I'm not sure here tbh, but it seems to be looking for a directory that doesn't exist. I have one here, but I have no idea what dbus is for - probably something not to muck about with :)

You could though if you wanted to check that the directory doesn't exist and if so make one.

You might be better served by reinstalling though, sorry I can't be of more help for you.

---

### Post by Theo148 on 2008-04-25
Well it's a good thing I backed up my important files then... I guess I'll go start torrenting the Hardy ISO (hopefully it's faster than the 1.5 kb/s I got last time I tried).

---

### Post by forestpixie on 2008-04-25
If you're resigned to reinstalling - try to make the directory

mkdir /var/run/dbus

---

### Post by Theo148 on 2008-04-25
Okay - I guess it's a good idea to have the CD around anyway, so I'll try that after I finish torrenting the ISO. :)

---

### Post by Theo148 on 2008-04-25
Well oddly enough making the directory worked - I was able to configure dbus (which appears to be related to networking somehow) and use 'dpkg --configure -a' to finish the operation. However when I booted Ubuntu, there were a bunch of things that were broken (I guess there's more to the upgrade than installing packages) so while the system was usable, it wasn't functioning like it was supposed to. I was able to access and back up a few files that weren't absolutely necessary but would have been a pain to lose, so it wasn't a complete failure. :)

I did a clean install of Hardy over the messed up partition and now everything is running smoothly, with the exception of a few issues that seem to be graphics problems, but hopefully those will be resolved shortly.

---

### Post by forestpixie on 2008-04-26
Maybe you need to caryry on with the apt-get update once it had finished fixing what was broken - anyway glads it sort of helped and that you were ok eventually.

---

### Post by Theo148 on 2008-04-26
Thanks for your assistance anyway. :) I guess it's probably a blessing in disguise anyway, since I finally had a good reason to go replace my AC power cord and do a clean install, both of which I was too lazy to do before. :lolflag:

---

### Post by shadowbuntu on 2008-05-24
I had the same issue with Ubuntu Server Hardy. I was unfortunately trying to install a desktop for it and in the middle of the installation my server kept rebooting randomly in terminal mode and it messed up the installation.

The thing was in an infinite loop. If i did
```
sudo dpkg --configure -a 
```

it would throw errors that I could not see.

Could not do 
```
sudo apt-get update
```

I finally tried

```
sudo dpkg --configure -a > error.log
``` 

to actually see the warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory.

Creating the directory worked:

```

sudo mkdir /var/run/dbus
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Please mark this thread as [SOLVED] and thanks for all the help!

---

### Post by Theo148 on 2008-05-25
Thread marked as solved - that feature was only reimplemented recently, so I hope you can excuse me for being a little slow to do so. :P

---

### Post by tech0007 on 2008-06-09
> **forestpixie said:**
> If you're resigned to reinstalling - try to make the directory

mkdir /var/run/dbus

this worked when i tried upgrading from hardy to intrepid!!!

---

