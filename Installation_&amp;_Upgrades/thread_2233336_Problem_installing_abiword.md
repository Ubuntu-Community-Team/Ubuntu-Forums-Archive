---
title: "Problem installing abiword"
date: 2014-07-08
forum: Installation &amp; Upgrades
---

### Post by matt42 on 2014-07-08
Hi, I just installed Xubuntu 14.04.  Soon after, I tried installing skype, but I kept getting errors.  Trying to solve the problem, I may have damaged or accidently replaced some packages.

Now Abiword does not work.  I've tried repairing it, but with no luck.  Here's the dump from Software Center:

The following packages have unmet dependencies:

abiword: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
         Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
         Depends: libreadline6 (>= 6.0) but 6.3-4ubuntu2 is to be installed
         Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
         Depends: abiword-common (>= 3.0.0-4ubuntu1) but 3.0.0-4ubuntu1 is to be installed

In addition, when I try to use apt-get, I get the following:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I've really tried looking around the web for solutions, but I'm confused and over my head on this one.

This is a new installation, but I have previously had no difficulties installing and using these two apps on Xubuntu.  Don't know if I damaged something, or a recent xubuntu update damaged something...

Any ideas appreciated.

---

### Post by ian-weisser on 2014-07-08
> **matt42 said:**
> [...]when I try to use apt-get, I get the following:
E: Could not open lock file /var/lib/dpkg/lock - open (13: [COLOR=#ff0000]**Permission denied**[/COLOR])
E: Unable to lock the administration directory (/var/lib/dpkg/), [COLOR=#ff0000]**are you root?**[/COLOR]

This usually means you forgot to use sudo on the command line.
Or you had another package manager open at the same time. Avoid that.



> **matt42 said:**
> 
The following packages have unmet dependencies:
abiword: Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
         Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
         Depends: libreadline6 (>= 6.0) but 6.3-4ubuntu2 is to be installed
         Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
         Depends: abiword-common (>= 3.0.0-4ubuntu1) but 3.0.0-4ubuntu1 is to be installed

Stop using Software Center to try to fix the system. It's great at showing you what's available, but it's not intended to be a repair tool.

Open a terminal.
Run the command **sudo apt-get-update && sudo apt-get upgrade**

If it works without error, your problem is probably fixed.
If errors, then cut-and-paste the complete output here (it will be long). Use [code] tags.

---

### Post by matt42 on 2014-07-08
Thanks for the tips.  I used:

sudo apt-get update && sudo apt-get upgrade

and both worked, except that this message was displayed:
W: Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I then tried again to install abiword...and got another dependency error:

matt@matt-ThinkPad-X200s:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 abiword : Depends: libabiword-3.0 (>= 3.0.0) but it is not going to be installed
           Recommends: abiword-plugin-grammar but it is not going to be installed
           Recommends: abiword-plugin-mathview but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by ian-weisser on 2014-07-08
You are trying to install Abiword from a PPA, instead of from the Ubuntu Repositories.
And the PPA does not exist anymore. 404 means the same thing in apt as in a web page - 'does not exist'

1) Go into Software Center --> Software Sources menu and uncheck the PPA.
2) Open a terminal and run the command  **ls /var/cache/apt/archives/ | grep abiword**
    If it has any output at all, post the output here.

I recommend against PPA usage, unless you understand the error messages, for precisely this reason.

Then try **sudo apt-get update && sudo apt-get upgrade** again.

---

### Post by matt42 on 2014-07-09
>1) Go into Software Center --> Software Sources menu and uncheck the PPA.

Did this....ok

>2) Open a terminal and run the command  **ls /var/cache/apt/archives/ | grep abiword**
    >If it has any output at all, post the output here.

Tried this....no output...good?

>Then try **sudo apt-get update && sudo apt-get upgrade** again.[/QUOTE]

This above command works fine...but when I try to then say sudo apt-get install abiword, I get the same error messages:

The following packages have unmet dependencies:
 abiword : Depends: libabiword-3.0 (>= 3.0.0) but it is not going to be installed
           Recommends: abiword-plugin-grammar but it is not going to be installed
           Recommends: abiword-plugin-mathview but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I've also noticed that when I boot, I'm getting error messages that xubuntu has broken files, but it can't fix itself...this is frustrating, and I'm tempted to just back up my files and reinstall, as I think I did something wrong along the way....

---

### Post by ian-weisser on 2014-07-09
Reinstalling is not a cure-all. It depends on what you did and what the error messages say.

Do you have the Universe repositories enabled?

---

### Post by matt42 on 2014-07-10
Hi,

Sorry for the delay, I do have the universal repositories enabled.

Also, of note, I was getting error messages when booting xubuntu, but those messages are now gone.  Not sure why, but a good sign.

I am currently using LibreOffice writer, and I'm becoming resigned to using it, as I'm unsure how to proceed from here.

I wonder if I accidently wrote over or uninstalled some libraries or something that abiword needs, but I guess I don't understand linux well enough to know why this can't be resolved easier.

Matt

---

### Post by ian-weisser on 2014-07-10
Try installing one of those not-going-to-be-installed dependencies, like abiword-plugin-grammar and see what the error message says.

Resolving a problem like this is very easy. It merely requires a simple understanding of the package manager, and close attention to the dpkg error messages. We have helped lots of people who have borked their system by unwise software choices.

My system has _never_ had a problem like yours in the 8 years Ubuntu has been my primary OS. It's not common.

---

### Post by matt42 on 2014-07-11
Here's what happened:

matt@matt-ThinkPad-X200s:~$ sudo apt-get install abiword-plugin-grammar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 abiword-plugin-grammar : Depends: libabiword-3.0 (>= 3.0.0) but it is not going to be installed
                          Depends: abiword (= 3.0.0-4ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by matt42 on 2014-07-11
Update: reinstalled 14.04, and now abiword works just fine.

---

