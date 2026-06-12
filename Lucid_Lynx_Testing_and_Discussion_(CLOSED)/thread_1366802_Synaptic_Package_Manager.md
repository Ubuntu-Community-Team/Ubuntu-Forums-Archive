---
title: "Synaptic Package Manager"
date: 2009-12-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2009-12-28
I'm sure this was okay the other day... Now it shows as starting, then seems to quietly die .. 

Well, on screen it does - I have multiple entries of the following from my trying to start it ..

> phillw   12764     1  1 01:35 ?        00:00:00 gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
root     12765 12764  0 01:35 ?        00:00:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/sbin/synaptic
 Time stamped at my trying to start it.

Phill.

---

### Post by phillw on 2009-12-28
It's picking on me !!!
I tried to report it using ```
ubuntu-bug 12764
```

And all seemed to be quite well .... until.

> 
**Oops!**

                        Sorry, something just went wrong in Launchpad.           
                        We’ve recorded what happened,             and we’ll fix it as soon as possible.             Apologies for the inconvenience.           
                        (Error ID:             OOPS-1459G203)


Ah well...  time for bed, I'll do an update & re-boot in the morning


Regards,


Phill.

---

### Post by ranch hand on 2009-12-28
I would try opening it with "sudo synaptic" in terminal.

Why not "ubuntu-bug synaptic"?

---

### Post by 23meg on 2009-12-28
> **ranch hand said:**
> I would try opening it with "sudo synaptic" in terminal.

I would try "gksudo synaptic", since using sudo with graphical apps can be problematic and shouldn't be advised.

---

### Post by ranch hand on 2009-12-28
> **23meg said:**
> I would try "gksudo synaptic", since using sudo with graphical apps can be problematic and shouldn't be advised.
Oh my. my bad.  "gksudo" for sure.

---

### Post by ronacc on 2009-12-28
and in Kubuntu you want to use kdesudo for graphical apps .

---

### Post by phillw on 2009-12-29
> I would try "gksudo synaptic", since using sudo with graphical apps can be problematic and shouldn't be advised.I do use gksudo !! -- those two lines in my previous post were what were left AFTER trying to start it from System --> Admin --> Synaptic Pkge Mngr.

> phillw   10692     1  0 01:26 ?        00:00:00 gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
I am guessing, is the invocation via the System method, with me as owner and 

> root     10693 10692  0 01:26 ?        00:00:00 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/sbin/synaptic Is owned by the process I believe I started - and it did that all on it's own ;-)

So, if sudo is **bad**, some one better hurry and tell synaptic, as it *owns* the line with sudo in !!!!

The reason I didn't do ubuntu-bug Synaptic is that it was asking for the PID of the process - which is what I told it !!

Please advise me if giving ubuntu-bug the PID, as it asked me for, was incorrect - I'm still learning this stuff !!!

Regards,

Phill.

---

### Post by Gourgi on 2009-12-29
```
ubuntu-bug synaptic
``` isn't enough ?  :confused:

---

### Post by phillw on 2009-12-29
>  ubuntu-bug synaptic

it went off like a good little programme, gathered details - popped me onto launchpad with my login, allowed me to see if there were any other occurences in lucid (none) - press 'report new bug' and .... > 
**Oops!**

                        Sorry, something just went wrong in Launchpad.           
                        We’ve recorded what happened,             and we’ll fix it as soon as possible.             Apologies for the inconvenience.           
                        (Error ID:             OOPS-1459F1541)           
                                               

This is now being a pain !!!!  

::sigh::

Phill.

---

### Post by phillw on 2009-12-29
```
gksudo synaptic
``` Started it & after that I could start it from System-->Admin-->Synaptic pkg mngr.

Guess the system was just a bit confused.

As to launchpad ... pass !!!

Phill.

---

### Post by VMC on 2009-12-29
> **ronacc said:**
> and in Kubuntu you want to use kdesudo for graphical apps .

Good to know ! I didn't realize they had gui-root. I did something like sudo dolphin. Now I know.

---

### Post by hikaricore on 2009-12-30
I've never had a single issue using sudo for graphical applications.
If possible I'd like to know some of the possible problems associated with this.
After years of doing such myself and not even a hiccup why wouldn't it be adviseable to tell others to do this?

---

### Post by sisco311 on 2009-12-30
> **hikaricore said:**
> I've never had a single issue using sudo for graphical applications.
If possible I'd like to know some of the possible problems associated with this.
After years of doing such myself and not even a hiccup why wouldn't it be adviseable to tell others to do this?

By default, sudo doesn't reset the some of the environment variables (HOME, USER, SHELL, LOGNAME and PATH). You may end up with files owned by root in the user's home directory. 

So, you should use sudo -i or gksudo with GUI apps.

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by hikaricore on 2009-12-30
Sounds as if the proper course of action would be to fix sudo then.  :)
Thanks for the info.

---

### Post by wfarr_09 on 2009-12-31
> **23meg said:**
> I would try "gksudo synaptic", since using sudo with graphical apps can be problematic and shouldn't be advised.

@everyone

Just a Correction.... I Think. It's ```
gk(kde)su example
```

---

### Post by Gourgi on 2009-12-31
> **wfarr_09 said:**
> @everyone

Just a Correction.... I Think. It's ```
gk(kde)su example
```

it is the same thing
```
man gksu
man gksudo
```

---

### Post by sisco311 on 2009-12-31
> **wfarr_09 said:**
> @everyone

Just a Correction.... I Think. It's ```
gk(kde)su example
```

gksudo is a symbolic link to gksu.
```
ls -al /usr/bin/gksu*
```

---

### Post by 23meg on 2010-01-01
> **hikaricore said:**
> Sounds as if the proper course of action would be to fix sudo then.  :)
Thanks for the info.

The proper course of action is to get rid of the need to run those applications as root, and if needed, use PolicyKit to elevate privileges for the parts that need them.

---

### Post by sisco311 on 2010-01-01
> **hikaricore said:**
> Sounds as if the proper course of action would be to fix sudo then.  :)
Thanks for the info.

The proper course of action is to fix (oh well, educate) the users. Did I say users? I meant system administrators. ;)

> **23meg said:**
> The proper course of action is to get rid of the need to run those applications as root, and if needed, use PolicyKit to elevate privileges for the parts that need them.

+1

---

### Post by ranch hand on 2010-01-01
> **23meg said:**
> The proper course of action is to get rid of the need to run those applications as root, and if needed, use PolicyKit to elevate privileges for the parts that need them.
Where on earth do you get information on PolicyKit that is not nearly 3 years old and has nothing to do with the system we have.

Everything I can find calls for a PolicyKit.conf file in /etc.  I do not have anything like that or the subdiretory /PolicyKit in which that file is to reside in.

---

### Post by sisco311 on 2010-01-01
> **ranch hand said:**
> Where on earth do you get information on PolicyKit that is not nearly 3 years old and has nothing to do with the system we have.

Everything I can find calls for a PolicyKit.conf file in /etc.  I do not have anything like that or the subdiretory /PolicyKit in which that file is to reside in.

Yep, the documentation of polkit is imperfect and incomplete. 



[http://hal.freedesktop.org/docs/polkit/]("http://hal.freedesktop.org/docs/polkit/")

```
man polkit
```

---

### Post by ranch hand on 2010-01-01
> **sisco311 said:**
> Yep, the documentation of polkit is imperfect and incomplete. 



[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)

```
man polkit
```
Thanks.  Everything I have found is from 07.

The man page has not been too helpful for me but that may be because of my ignorance.  All it seems to say is here is what this does, live with it.  pkaction may be amusing but is not real helpful.

Maybe if I read your link it will make me smarter.  One can always hope.

---

### Post by ranch hand on 2010-01-01
From the polkit man page;
[quote]
        2. developer documentation
           file:///usr/share/gtk-doc/html/polkit-1/index.html
[/polkit]
There is no such thing here in a fully updated 10.04.

---

### Post by sisco311 on 2010-01-01
> **ranch hand said:**
> 
Maybe if I read your link it will make me smarter.  One can always hope.

I have had to read it several times to get a basic idea about polkit. :)

Good luck!!!


But polkit is under active development, so there is no guarantee that the documentation is accurate. :(

---

### Post by ranch hand on 2010-01-01
Well there has to be something to keep us having FUN.

---

### Post by Ibidem on 2010-01-08
I use sudo if I have problems--occasionally it works better, and the useful part is that the terminal is where errors go, so I can see them.
But I have had some problems with Synaptic in Lucid ("cannot build tree. Aborting" or the like), which I should investigate further.  Might just be that a dependency is labeled as recommended, as I stopped Aptitude from installing several "recommended" packages.

---

### Post by paul_in_london on 2010-01-08
> **Ibidem said:**
> I use sudo if I have problems--occasionally it works better, and the useful part is that the terminal is where errors go, so I can see them.
But I have had some problems with Synaptic in Lucid ("cannot build tree. Aborting" or the like), which I should investigate further.  Might just be that a dependency is labeled as recommended, as I stopped Aptitude from installing several "recommended" packages.

@Ibidem

There are a couple of things you could try, but more details about your error messages would probably be useful:

```
$ sudo rm -vf /var/cache/apt/*.bin
```

and/or:

```
$ cd /var/lib/dpkg/
$ sudo mv status status.broken
$ sudo cp status-old status
$ sudo aptitude update
```

---

