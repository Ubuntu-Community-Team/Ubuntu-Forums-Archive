---
title: "How can I tell which ver I'm running?"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by Lor Boo on 2007-04-01
I've run a few things:  now no longer certain which version i'm running?

system -> admin -> software properties says everything is 6.06...
i've tried to upgrade to 6.10... thought I had.. but still seeing 6.06..

So now I'm wondering - where do you find out which version your running?

Thanks

---

### Post by gjtoth on 2007-04-01
> **Lor Boo said:**
> I've run a few things:  now no longer certain which version i'm running?

system -> admin -> software properties says everything is 6.06...
i've tried to upgrade to 6.10... thought I had.. but still seeing 6.06..

So now I'm wondering - where do you find out which version your running?

Thanks


In a console:

lsb_release -a

or

uname -a

---

### Post by Lor Boo on 2007-04-01
Yeeks... That's not a command I would have simply stumbled across.

It begs the question - why no easier way?

Ah well,   The command came easy and states I'm running 6.06:

```

drinky@drinky:~$ lsb_release -a
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:co re-3.0-ia32:core-3.1-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-2.0-i a32:cxx-3.0-ia32:cxx-3.1-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3 .1-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:desktop-3.1-noar ch:desktop-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper
drinky@drinky:~$

```


I guess I need to mess with this a bit.
Here's something that has me stumbled...
I typed in: 

```

gksu “update-manager -c -d”
gksu: invalid option -- c
GKsu version 1.3.7

Usage: gksu [-u <user>] [-k] [-l] <command>

---then all the symtac options...--

```


I've also run 

[LIST]
[*]sudo apt-get dist-upgrade
[/LIST]

It did a few things....asked me if it were o.k. to install some things...
took about 45 to 70 seconds or so... and then back to the command prompt.


I then ran 
**gksu "update-manager -c" ** via Alt+F2
and then bang - I had the 'update verison' option within "Software Updates".

I hit that... it said it did a few things... lsb_release -a however doesn't show any changes.
where I going wrong?

---

### Post by Lor Boo on 2007-04-01
-bump-

---

### Post by gjtoth on 2007-04-01
> **Lor Boo said:**
> Yeeks... That's not a command I would have simply stumbled across.

It begs the question - why no easier way?

Ah well,   The command came easy and states I'm running 6.06:

```

drinky@drinky:~$ lsb_release -a
LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:co re-3.0-ia32:core-3.1-ia32:cxx-2.0-noarch:cxx-3.0-noarch:cxx-3.1-noarch:cxx-2.0-i a32:cxx-3.0-ia32:cxx-3.1-ia32:graphics-2.0-noarch:graphics-3.0-noarch:graphics-3 .1-noarch:graphics-2.0-ia32:graphics-3.0-ia32:graphics-3.1-ia32:desktop-3.1-noar ch:desktop-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper
drinky@drinky:~$

```


I guess I need to mess with this a bit.
Here's something that has me stumbled...
I typed in: 

```

gksu &#8220;update-manager -c -d&#8221;
gksu: invalid option -- c
GKsu version 1.3.7

Usage: gksu [-u <user>] [-k] [-l] <command>

---then all the symtac options...--

```


I've also run 

[LIST]
[*]sudo apt-get dist-upgrade
[/LIST]

It did a few things....asked me if it were o.k. to install some things...
took about 45 to 70 seconds or so... and then back to the command prompt.


I then ran 
**gksu "update-manager -c" ** via Alt+F2
and then bang - I had the 'update verison' option within "Software Updates".

I hit that... it said it did a few things... lsb_release -a however doesn't show any changes.
where I going wrong?

Did you perchance change your sources from dapper to edgy?  What I mean by that is open the sources list and everything that says dapper, change it to edgy, then run   sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean

That should do ya.... I hope.

---

### Post by Lor Boo on 2007-04-01
Hey guy... thank you much for the second post.

To be sure I'm in the right place....

I open up "Software Preferences"
There is shows me 16 line items listed as 'source'
The first item is : ```

**Ubuntu 6.06 LTS **(source) 
Officially supported

```

I would hit "Edit" and am then presented with a new window with Five options:
```

Type:   Source
URL:    [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
Distribution:   dapper
Components:  main
Comment: 

```
In here I simply change dapper to edgy (lower case / no caps)?
Simple as that?

---

### Post by Lor Boo on 2007-04-01
--bump--

---

### Post by gjtoth on 2007-04-01
> **Lor Boo said:**
> Hey guy... thank you much for the second post.

To be sure I'm in the right place....

I open up "Software Preferences"
There is shows me 16 line items listed as 'source'
The first item is : ```

**Ubuntu 6.06 LTS **(source) 
Officially supported

```

I would hit "Edit" and am then presented with a new window with Five options:
```

Type:   Source
URL:    [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
Distribution:   dapper
Components:  main
Comment: 

```
In here I simply change dapper to edgy (lower case / no caps)?
Simple as that?

as root, open /etc/apt/sources.list and edit the file as I described.

---

### Post by zvacet on 2007-04-02
system>about ubuntu will tell you wich version you are runing.If it is Edgy and you have Dapper source list you have to change it.
```
 sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```
Edit your source list and put # in front of CD-rom line

---

### Post by Lor Boo on 2007-04-02
Thank you much.

I changed the names to edgy and then ran:
 sudo aptitude update

It ran with this error:

```

Get:49 http://archive.ubuntu.com edgy-backports/multiverse Sources [1925B]
Fetched 6533kB in 51s (127kB/s)
Reading package lists... Done
W: GPG error: http://www.getautomatix.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: GPG error: http://wine.lowvoice.nl edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

```

So I just kept going... and ran:  sudo aptitude upgrade
which ran fine.

Next is: sudo aptitude dist-upgrade

It asked me:

```

upstart [Not Installed]
upstart-compat-sysv [Not Installed]
upstart-logd [Not Installed]

Leave the following dependencies unresolved:
bsh recommends xlibs
nautilus recommends fam
Score is -1932

Accept this solution? [Y/n/q/?] Y


```


it later stated that:
libfuse2 wine frostwire
is was not trusted.

An later on a few times it asked me about keeping my old file or switching to the one supplied by the package maintaner.  I all but the first time picked the one supplied by the package maintainer.

now I run sudo aptitude autoclean
cleaned up 183 megs... 
and I guess I'll reboot at this point.
Not sure how much this needs to be done..but this is a rather large change to the file system and years of MS have taught me - when in doubt, reboot -

I'll post if all is successful - (what a rambling post this is).

---

### Post by Lor Boo on 2007-04-02
All seams well.  The colours seam brighter?  but it's all good.

When I went to shut down, Gnome hung on me... so CTRL+ALT+F1... and then "reboot" from command prompt and yes - rebooted fine.

I seen new icons... old programs look a little different - more advanced graphics... 

Thank you much for the help.
I won't say I'm a noob any more...but I sure am green still :P


Night.

---

### Post by Lor Boo on 2007-04-08
Opps.. Well I see I didn't post back that it all worked.
It all worked, few little bugs to fix (like vmware is very happy about it...bla bla bla...)
but nothing serious.


 One remaining question.

Update manager just suggested that I do a 'Distribution Upgrade' through it rather than attempt
to just add whatever updates it has.

It wants to remove 45 packages and download 95...
I'm fine with the time etc.. what does the community think?

This a good idea to do and be done?
Or given what I've done above (- Thanks again gjtoth -) is it playing with fire?

Thanks

---

### Post by Lor Boo on 2007-04-08
- Bump -

---

### Post by Lor Boo on 2007-04-08
-- Bump 2 --

Even if your not sure... i'll prob let the system run it's distribution update...

Guess I really looking to see if there's a 
"Hell NO Don't do it man... I beg you!!"
person out there who sees an issue I don't.

---

### Post by Lor Boo on 2007-04-08
Ouch...well... can't hit it out of he park everytime.

I'll give it a swing and see where I land.

---

### Post by Lor Boo on 2007-04-08
All was well.
took about 10 minutes... 

have fun.

---

### Post by Lor Boo on 2007-04-11
Update - All did not work out well.... 
On reboot - error stated:  **No drivers available.  Fatal Error.  no screens found**

checking /etc/X11/xorg.conf  revealed errors on:
usr/lib/X11/fonts/ ....all of them not found.
usr/lib/X11/cyrillic also failed.

The big error appears to be "fglrx module does not exist"  -> ATI driver I think?
The result - X failed to load and I was dropped to the command line.
I know enough to find the errors...but not enough to fix them on my own.


[COLOR="DarkGreen"]Note: I did attempt to use one of the recovery kernel options which are presented earlier in the boot seqence, however I could not move between any of them?
I believe now the error is that my Logitech LX710 wireless keyboard / USB receiver (which I could use to edit BIOS settings), was not being recognized during that screen.  
Sadly I did not think that to be the case at the time and didn't test it. [/COLOR]

Anywho... I'm sure there was a fix for this, but I'm still so very green...and needing my computer I ran a restore from my backup disks to 6.06.
btw - I really liked the 'Mondo' backup program....nothing like bootable restore disks!

[COLOR="DarkGreen"]Note 2: Running the menu created by the backup program Mondo, my keyboard did not respond.  I attached a wired keyboard and all was fine.  If it was not so late at night, i'd have tried the wired keyboard with one of the recovery mode boot options... but didn't.[/color]



Anywho - i'll prob try again the weekend.  Especially now I know my backup's not only work.  but work so well :)

---

