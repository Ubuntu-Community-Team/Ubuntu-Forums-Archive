---
title: "error in removing programs im not sure about"
date: 2009-12-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-12-05
E: ttf-vlgothic: subprocess installed pre-removal script returned error exit status 1..Any advice?

---

### Post by ranch hand on 2009-12-06
This is interesting because I am thinking of removing that too.

Did you try running;
```

sudo dpkg --configure -a

```
?

---

### Post by sports fan Matt on 2009-12-06
I hadnt...but I hadnt been around the pc in a few days, it wasnt feeling well.

---

### Post by ranch hand on 2009-12-06
When ever you have problems with installation or removal, that is a good thing to run.  It may do nothing.  It may just fix your problem.

This appears to have to do with the install script so I do not know if it will help.

It might be good to just find the script and manually remove it and the tff file but I don't know.

---

### Post by collinp on 2009-12-06
Also, you may want to try running
```
sudo apt-get check
```and
```
sudo aptitude -f
```You may have broken packages/dependencies, which those commands above will fix.
It's fairly unlikely, and apt-get is *supposed* to error out if you do, but it might just be your problem.

---

### Post by SevenMachines on 2009-12-06
ttf-vlgothic is using an out of date option to defoma in its prerm script so fails showing the defoma-font help message

in /var/lib/dpkg/info/ttf-vlgothic.prerm

        test -x `which defoma-font` && defoma-font update ttf-vlgothic

should be,

test -x `which defoma-font` && defoma-font purge-all $FILE

it'll uninstall fine then

Is there a bug open on launchpad?

---

### Post by SevenMachines on 2009-12-06
[https://bugs.launchpad.net/ubuntu/+source/ttf-vlgothic/+bug/493192](https://bugs.launchpad.net/ubuntu/+source/ttf-vlgothic/+bug/493192)

---

### Post by ranch hand on 2009-12-06
I just gave this a try and it still will not be removed.  The bugger likes it here and wants to stay.
> 
/etc/defoma/hints/ttf-vlgothic.hints: Unable to open, or empty.
dpkg: error processing ttf-vlgothic (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-vlgothic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by SevenMachines on 2009-12-06
the file shouldnt have been removed when prerm failed so i'm not sure how its disappeared. i'll attach a copy of the missing file for you to add

---

### Post by ranch hand on 2009-12-06
Nope.  That did help though.  There seems to be a bunch of other problems;
> 
larry@larry-desktop:~$ sudo apt-get remove ttf-vlgothic
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-vlgothic
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
4 not fully installed or removed.
After this operation, 7,950kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 128714 files and directories currently installed.)
Removing ttf-vlgothic ...
W: /usr/share/fonts/truetype/vlgothic/VL-Gothic-Regular.ttf: not registered.
W: /usr/share/fonts/truetype/vlgothic/VL-PGothic-Regular.ttf: not registered.
dpkg: error processing ttf-vlgothic (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-vlgothic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no idea what this "registered" stuff is (is this like pedigree livestock) but at least the files are there.

Ugly font.

---

### Post by SevenMachines on 2009-12-06
the fonts have been de-registered, which is what the 'defoma-font purge-all' command does, unfortunately this has happened before the package is removed so the prerm fails. you just need to reregister them before removing the package
$sudo defoma-font reregister-all /etc/defoma/hints/ttf-vlgothic.hints

---

### Post by ranch hand on 2009-12-06
Ah, I will have to do a little more research into this "registry" business.  We live and learn.

I will give this a shot.

EDIT

That did the trick.  The sucker is gone.

That was FUN.

Thanks a bunch.  Hope this helps sox fan Matt

---

### Post by slakkie on 2009-12-08
I installed the karmic version and deleted that one :P

---

