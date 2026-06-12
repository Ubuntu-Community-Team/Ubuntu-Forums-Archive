---
title: "[SOLVED] Updating Versions of Software in the Repository"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by fballem on 2008-05-27
A question, since I've had the issue come up a couple of times where the Repository does not contain the latest version of software.

What is the process for requesting an update to the Repository, and once requested, what is the process by which the Repository is actually updated?

For me, the issue has arisen with Eclipse (repository 3.2.2, current 3.3.2) and HPLIP (repository 2.8.2, current 2.8.5). In the first case, there are some plug-ins that require 3.3.x and in the second case, my printer is not supported in 2.8.2, but is in 2.8.5).

Many thanks,

---

### Post by mister_pink on 2008-05-27
Unfortunately stuff doesn't usually get updated in the repos until the next version of ubuntu is out unless its a security or bug fix thing.

You have several options:
1. Check if its in backports
2. Uninstall the version you have and manually install the newer one.
3. Not recommended at all: See if its in the intrepid repo and install it from there. I think you'd have to enable the intrepid repo, install just that update, lock its version then remove the repo again.

I just looked, and the version of eclipse in the intrepid repo is the same as hardy, and the HPLIP version is 2.8.4:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=hplip](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=hplip)
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=eclipse](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=eclipse)

---

### Post by fballem on 2008-05-27
Thanks for the information. Could you please tell me how to 'encourage' them to look at using HPLIP 2.8.5, which is the first version that supports my printer?

---

### Post by mister_pink on 2008-05-27
Probably the best place to start is going on the irc channel and asking there. 
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

---

### Post by jw5801 on 2008-05-27
> **fballem said:**
> Thanks for the information. Could you please tell me how to 'encourage' them to look at using HPLIP 2.8.5, which is the first version that supports my printer?

Look on launchpad and search for the maintainer of that package, then contact them. The odds are pretty slim though, keeping all the software in the repositories at the most recent version is just not worth developer time, usually things get a mass upgrade with a newer version of Ubuntu.

If you need bleeding edge versions, your best bet is to compile it yourself.

EDIT: Even Intrepid is currently using 2.8.4. The most recent versions of software will never make it into a distro such as Ubuntu, it takes a bit of time to filter down and make it into the repositories. Have a look at the launchpad page for it [here](https://launchpad.net/ubuntu/+source/hplip) if you're after some more info. If you need the latest version now, then you'll need to compile it yourself.

---

### Post by cookdav on 2008-05-27
@fballem:

Eclipse is java-software, so it is distro-independent.
I just downloaded/installed the full EE-edition of 3.3.2 
last week from: [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)


HPLIP supports self-installation.  Go to
[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
and download their automatic installer.
(They claim it works on Ubuntu 8.04 and it seems to
when I tried it,)

Then, do 'sh hplip-2.8.5.run' as they say.

[Part way thru, it will ask you to stop 'adept_notifier'...to do that, open
another Konsole window and
issue cmd 'ps -al' to find the PID (#) for adept_notifier,..
say that was e.g. '6360', then issue the cmd 'sudo kill 6360'. Then
go resume the installation in the first Konsole window.]

Note: The newer version SHOULD now be installed, except that
Synaptic and apt do NOT know it (since new raw-files were just
copied into the system)..they think you still have v2.8.2.
Better, to fix that, do the three cmds:
cd hplip-2.8.5
sudo checkinstall
sudo dpkg -i --force-overwrite hplip_2.8.5-1_i386.deb
[If the result doesn't work, you can always use Synaptic to remove and
then re-install the base 2.8.2 versions of 'hplip' and 'hplip-data'.]

Hope these help...

Dave

---

### Post by fballem on 2008-05-27
Dave:

Thanks for the information on Eclipse - a couple of questions, being a newbie:

1. I know that the download is binary and will be untarred (is that even a word) into a directory. What is the best location for the executable (it strikes me that it should be in usr/local/bin/eclipse)?

2. What permissions should I set up on the directory containing the binary for Eclipse?

I found a bug in HPLIP 2.8.5 (my brand new cp1518 is a paper weight at the moment). I am working with the developer on Launchpad to figure this one out, but I am comfortable installing it - in fact, I've gotten pretty good at it after having done it so often! I think you're installing on Kubuntu (assumption, based on you using Konsole). When I do the install, I use the automatic mode and I don't get asked to stop adept. I'm running ubuntu using GNOME (I think I'm getting this right).

Many thanks,
Flavelle

---

### Post by jw5801 on 2008-05-28
> **fballem said:**
> Dave:

Thanks for the information on Eclipse - a couple of questions, being a newbie:

1. I know that the download is binary and will be untarred (is that even a word) into a directory. What is the best location for the executable (it strikes me that it should be in usr/local/bin/eclipse)?

2. What permissions should I set up on the directory containing the binary for Eclipse?

I found a bug in HPLIP 2.8.5 (my brand new cp1518 is a paper weight at the moment). I am working with the developer on Launchpad to figure this one out, but I am comfortable installing it - in fact, I've gotten pretty good at it after having done it so often! I think you're installing on Kubuntu (assumption, based on you using Konsole). When I do the install, I use the automatic mode and I don't get asked to stop adept. I'm running ubuntu using GNOME (I think I'm getting this right).

Many thanks,
Flavelle

This is Linux so you can put it wherever you'd like! :)

Generally speaking though it's not simplest to create extra directories in /usr/bin. In case you aren't aware binaries go in a bin directory, libraries in a lib directory and source files in a src directory. There are a few of these groups around your root filesystem. One is right at the base at /, generally we don't install to there, only the important things go there. Next you'll see one at /usr/, you'll notice that /usr/bin/ has quite a few things in it, this is because it's the default install place for apt (the debian package system). You'll also notice that there is another at /usr/local/. The way I've set up my system (it seems to be quite a neat way to do it) is to have anything I've manually installed have /usr/local/ as it's root, that way I can easily check everything that I've installed that apt can't see. So important binaries go in /bin (and /sbin), apt installed things go in /usr/bin, and manually installed things go in /usr/local/bin.

So in summary, I'd put the binary by itself in /usr/local/bin. If you create a subdirectory in /usr/bin then you'll need to add that subdirectory to your path before you can access anything in it without giving a full path. As far as permissions go, it needs execute permissions.

Since this program is java, it may have a few different .jar files that it needs to run. In that case I'd be more inclined to leave those in your home directory (or whereever you like, /opt/eclipse/ is probably also a good place) and put a wrapper script in /usr/local/bin so that you can call it in one command that's on your path.

That's just the way I would do it though. And that's the beauty of Linux, you can do it however you'd like!

EDIT: And yes, untarred is a word.

---

### Post by fballem on 2008-05-28
> **jw5801 said:**
> This is Linux so you can put it wherever you'd like! :)

Generally speaking though it's not simplest to create extra directories in /usr/bin. In case you aren't aware binaries go in a bin directory, libraries in a lib directory and source files in a src directory. There are a few of these groups around your root filesystem. One is right at the base at /, generally we don't install to there, only the important things go there. Next you'll see one at /usr/, you'll notice that /usr/bin/ has quite a few things in it, this is because it's the default install place for apt (the debian package system). You'll also notice that there is another at /usr/local/. The way I've set up my system (it seems to be quite a neat way to do it) is to have anything I've manually installed have /usr/local/ as it's root, that way I can easily check everything that I've installed that apt can't see. So important binaries go in /bin (and /sbin), apt installed things go in /usr/bin, and manually installed things go in /usr/local/bin.

So in summary, I'd put the binary by itself in /usr/local/bin. If you create a subdirectory in /usr/bin then you'll need to add that subdirectory to your path before you can access anything in it without giving a full path. As far as permissions go, it needs execute permissions.

Since this program is java, it may have a few different .jar files that it needs to run. In that case I'd be more inclined to leave those in your home directory (or whereever you like, /opt/eclipse/ is probably also a good place) and put a wrapper script in /usr/local/bin so that you can call it in one command that's on your path.

That's just the way I would do it though. And that's the beauty of Linux, you can do it however you'd like!

EDIT: And yes, untarred is a word.

The trouble with Linux is that you can do it however you like ... and if you don't know what you're doing, and I don't yet, you can get into a whole lot of trouble. Your suggestions make sense and sounds like a good way for me to proceed.

In the case of Eclipse, assuming that I put the eclipse executable in /usr/local/bin and everything else in /opt/eclipse, do you have a wrapper script to use the options, and if so, may I borrow it as a starting point for mine?

Many thanks,
Flavelle

---

### Post by jw5801 on 2008-05-28
> **fballem said:**
> The trouble with Linux is that you can do it however you like ... and if you don't know what you're doing, and I don't yet, you can get into a whole lot of trouble. Your suggestions make sense and sounds like a good way for me to proceed.

In the case of Eclipse, assuming that I put the eclipse executable in /usr/local/bin and everything else in /opt/eclipse, do you have a wrapper script to use the options, and if so, may I borrow it as a starting point for mine?

Many thanks,
Flavelle

I haven't got one no, that was just generic advice. :)

Do you actually need anything other than the executable is the first question I'd ask. Try moving it to another directory and executing it, if it still works fine then just copy the executable to /usr/local/bin and you'll be set. If it complains about missing files, then copy all the files (including the executable) to /opt/eclipse/ and make a file called /usr/local/bin/eclipse as your wrapper script.

A pretty basic one is:
```
#!/bin/bash

# Wrapper script to execute eclipse, including options
cd /opt/eclipse/
./eclipse $@

```

$1 is the first variable you pass on the commandline ($0 is the command you enter), $2 is the second, etc. $@ expands to $1 $2 $3 $4 ... $n. So yeah, pretty simple to write. I'm not sure whether the change of directories is necessary or if you can just execute '/opt/eclipse/eclipse $@' but it's not a bad habit to be in.

---

### Post by fballem on 2008-05-28
> **jw5801 said:**
> I haven't got one no, that was just generic advice. :)

Do you actually need anything other than the executable is the first question I'd ask. Try moving it to another directory and executing it, if it still works fine then just copy the executable to /usr/local/bin and you'll be set. If it complains about missing files, then copy all the files (including the executable) to /opt/eclipse/ and make a file called /usr/local/bin/eclipse as your wrapper script.

A pretty basic one is:
```
#!/bin/bash

# Wrapper script to execute eclipse, including options
cd /opt/eclipse/
./eclipse $@

```

$1 is the first variable you pass on the commandline ($0 is the command you enter), $2 is the second, etc. $@ expands to $1 $2 $3 $4 ... $n. So yeah, pretty simple to write. I'm not sure whether the change of directories is necessary or if you can just execute '/opt/eclipse/eclipse $@' but it's not a bad habit to be in.

Once more into the breach, with many thanks for the help along the way!

Flavelle

---

