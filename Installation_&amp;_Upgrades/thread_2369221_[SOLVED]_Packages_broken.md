---
title: "[SOLVED] Packages broken"
date: 2017-08-20
forum: Installation &amp; Upgrades
---

### Post by Shideneyu on 2017-08-20
Hi,

To be able to install some software, I wanted to downgrade those three packages, and I did this really big mistake:

```
sudo dpkg --purge libstdc++-4.8.2-19ubuntu1
sudo dpkg --purge libstdc++-4.8-dev:amd64

```

Since then I have this dependency error:

```
&#10140;  Downloads sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libstdc++-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
                     Depends: libgcc-4.8-dev (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
 libstdc++6 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



```


And this:
```
&#10140;  Downloads sudo dpkg --configure -a
Setting up cpp-4.8 (4.8.5-2ubuntu1~14.04.1) ...
dpkg: dependency problems prevent configuration of libstdc++-4.8-dev:amd64:
 libstdc++-4.8-dev:amd64 depends on gcc-4.8-base (= 4.8.2-19ubuntu1); however:
  Version of gcc-4.8-base:amd64 on system is 4.8.5-2ubuntu1~14.04.1.
 libstdc++-4.8-dev:amd64 depends on libgcc-4.8-dev (= 4.8.2-19ubuntu1); however:
  Version of libgcc-4.8-dev:amd64 on system is 4.8.5-2ubuntu1~14.04.1.
 libstdc++-4.8-dev:amd64 depends on libstdc++6 (>= 4.8.2-19ubuntu1); however:
  Package libstdc++6:amd64 is not configured yet.


dpkg: error processing package libstdc++-4.8-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.4-dbg:
 libstdc++6-4.4-dbg depends on libstdc++6 (>= 4.4.7-8ubuntu1); however:
  Package libstdc++6:amd64 is not configured yet.


dpkg: error processing package libstdc++6-4.4-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++-4.8-dev:amd64
 libstdc++6-4.4-dbg



```

Whatever happen, I cannot get synaptic working (to fix the broken dependencies) because I have this error:

```

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I'm really stucked. What can I do ?

---

### Post by vocx on 2017-08-20
First of all, please edit your post and use "CODE" tags for the terminal output. You currently show the output in "QUOTE" tags, which is not the same. In the forum's advanced editor, the two buttons are next to each other so many people confuse them.

> **Shideneyu said:**
> Hi,

To be able to install some software, I wanted to downgrade those three packages, and I did this really big mistake:
...
I'm really stucked. What can I do ?

Why did you do this? What program were you trying to install, that you seemingly needed an older version?

I imagine the standard C++ library (libstdc++) is a very important part of the system, so you should not try to change it without knowing exactly what you are doing. Surely there is a safer or more orthodox way to get the software you need.

Did you try reinstalling those packages with "apt"?

```

sudo apt install --reinstall libstdc++-4.8.2-19ubuntu1
sudo apt install --reinstall libstdc++-4.8-dev
# ... etc.

```

Possibly you could get the same result by installing the debian package from the repositories. So go to [https://packages.ubuntu.com/](https://packages.ubuntu.com/), go to your specific Ubuntu version, which seems to be 14.04, and download the packages that you think would restore your system, according to the error messages you get.
```

libstdc++-4.8-dev
gcc-4.8-base
libgcc-4.8-dev
libstdc++6

```

Once you have a deb package you can install it with "dpkg". For example,
```

sudo dpkg -i gcc-4.8-base_4.8.2-19ubuntu1.deb

```

---

### Post by Shideneyu on 2017-08-20
Thank you for your answer. I did exactly what you adviced me to. Unfortunately the apt-get command does not work since there is a broken dependancy, so I have to install the dependancy manually.

However, there is a dependancy loop. Each time that I resolve every depencies, I come back to the start.

See by yourself:

```
&#10140;  Downloads sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libstdc++-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
                     Depends: libgcc-4.8-dev (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
 libstdc++6 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

&#10140;  Downloads sudo dpkg -i gcc-4.8-base_4.8.2-19ubuntu1_amd64.deb 
dpkg: warning: downgrading gcc-4.8-base:amd64 from 4.8.5-2ubuntu1~14.04.1 to 4.8.2-19ubuntu1
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack gcc-4.8-base_4.8.2-19ubuntu1_amd64.deb ...
Unpacking gcc-4.8-base:amd64 (4.8.2-19ubuntu1) over (4.8.5-2ubuntu1~14.04.1) ...
Setting up gcc-4.8-base:amd64 (4.8.2-19ubuntu1) ...


&#10140;  Downloads sudo dpkg -i libgcc-4.8-dev_4.8.2-19ubuntu1_amd64.deb 
dpkg: warning: downgrading libgcc-4.8-dev:amd64 from 4.8.5-2ubuntu1~14.04.1 to 4.8.2-19ubuntu1
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack libgcc-4.8-dev_4.8.2-19ubuntu1_amd64.deb ...
Unpacking libgcc-4.8-dev:amd64 (4.8.2-19ubuntu1) over (4.8.5-2ubuntu1~14.04.1) ...
Setting up libgcc-4.8-dev:amd64 (4.8.2-19ubuntu1) ...

``` 

So it's suppsoed to have filled the dependancies, however now I get:

```
 &#10140;  Downloads sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 cpp-4.8 : Depends: gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1) but 4.8.2-19ubuntu1 is installed
 gcc-4.8 : Depends: gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1) but 4.8.2-19ubuntu1 is installed
           Depends: libgcc-4.8-dev (>= 4.8.5-2ubuntu1~14.04.1) but 4.8.2-19ubuntu1 is installed
 libasan0 : Depends: gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1) but 4.8.2-19ubuntu1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

So I resolve those:

```
 &#10140;  Downloads sudo dpkg -i gcc-4.8-base_4.8.2-19ubuntu1_amd64.deb 
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack gcc-4.8-base_4.8.2-19ubuntu1_amd64.deb ...
Unpacking gcc-4.8-base:amd64 (4.8.2-19ubuntu1) over (4.8.2-19ubuntu1) ...
Setting up gcc-4.8-base:amd64 (4.8.2-19ubuntu1) ...


&#10140;  Downloads sudo dpkg -i libgcc-4.8-dev_4.8.5-2ubuntu1-14.04.1_amd64.deb 
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack libgcc-4.8-dev_4.8.5-2ubuntu1-14.04.1_amd64.deb ...
Unpacking libgcc-4.8-dev:amd64 (4.8.5-2ubuntu1~14.04.1) over (4.8.2-19ubuntu1) ...
dpkg: dependency problems prevent configuration of libgcc-4.8-dev:amd64:
 libgcc-4.8-dev:amd64 depends on gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1); however:
  Version of gcc-4.8-base:amd64 on system is 4.8.2-19ubuntu1.


dpkg: error processing package libgcc-4.8-dev:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgcc-4.8-dev:amd64

```

So I resolve this again:
```
&#10140;  Downloads sudo dpkg -i gcc-4.8-base_4.8.5-2ubuntu1-14.04.1_amd64.deb 
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack gcc-4.8-base_4.8.5-2ubuntu1-14.04.1_amd64.deb ...
Unpacking gcc-4.8-base:amd64 (4.8.5-2ubuntu1~14.04.1) over (4.8.2-19ubuntu1) ...
Setting up gcc-4.8-base:amd64 (4.8.5-2ubuntu1~14.04.1) ...


&#10140;  Downloads sudo dpkg -i libgcc-4.8-dev_4.8.5-2ubuntu1-14.04.1_amd64.deb
(Reading database ... 491358 files and directories currently installed.)
Preparing to unpack libgcc-4.8-dev_4.8.5-2ubuntu1-14.04.1_amd64.deb ...
Unpacking libgcc-4.8-dev:amd64 (4.8.5-2ubuntu1~14.04.1) over (4.8.5-2ubuntu1~14.04.1) ...
Setting up libgcc-4.8-dev:amd64 (4.8.5-2ubuntu1~14.04.1) ...

```

And.... I'm back to the start.

```
&#10140;  Downloads sudo apt-get install -f                                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libstdc++-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
                     Depends: libgcc-4.8-dev (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
 libstdc++6 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.5-2ubuntu1~14.04.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```


So to answer your first question, I think that I've done that in the past so I decided to give it a go to what I had in mind because I thought I've already done it. But that was a mistake. I wanted to use textsudio and it has a libstdc++6 conflict. I'll see this issue later, I want to fix my computer now this is my priority.

EDIT: To resume what are the commands I do to resolve conflicts:

```
sudo dpkg -i gcc-4.8-base_4.8.2-19ubuntu1_amd64.deb
sudo dpkg -i libgcc-4.8-dev_4.8.2-19ubuntu1_amd64.deb 




sudo dpkg -i gcc-4.8-base_4.8.5-2ubuntu1-14.04.1_amd64.deb
sudo dpkg -i libgcc-4.8-dev_4.8.5-2ubuntu1-14.04.1_amd64.deb
```

---

### Post by Shideneyu on 2017-08-20
So some packages require **[COLOR=#000000][FONT=&amp] gcc-4.8-base [/FONT][/COLOR][COLOR=#000000][FONT=&amp](= 4.8.2-19ubuntu1)[/FONT][/COLOR] **and some other require [COLOR=#000000][FONT=&amp][B]gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1)
[/B]
[/FONT][/COLOR]How can I fix this dependancy loop ? By the way, I fear that restarting my computer means that I won't be able to boot to my session anymore. So I'm actively trying to find a solution.

---

### Post by Shideneyu on 2017-08-20
Alright I fixed it by running those commands.

```
sudo dpkg -i cpp-4.8_4.8.2-19ubuntu1_amd64.deb
sudo dpkg -i gcc-4.8_4.8.2-19ubuntu1_amd64.deb
sudo dpkg -i libasan0_4.8.2-19ubuntu1_amd64.deb
```

Thank you !

---

### Post by vocx on 2017-08-20
> **Shideneyu said:**
> So some packages require **[COLOR=#000000][FONT=&amp] gcc-4.8-base [/FONT][/COLOR][COLOR=#000000][FONT=&amp](= 4.8.2-19ubuntu1)[/FONT][/COLOR] **and some other require [COLOR=#000000][FONT=&amp][B]gcc-4.8-base (= 4.8.5-2ubuntu1~14.04.1)
[/B]
[/FONT][/COLOR]How can I fix this dependancy loop ? By the way, I fear that restarting my computer means that I won't be able to boot to my session anymore. So I'm actively trying to find a solution.
I noticed in your previous post you installed 4.8.2, but then installed 4.8.5, and then 4.8.2 again. So obviously you are going in circles.

What about just removing everything? The compilers "gcc" and "-dev" files, are not a required by the system, they are only used if you want to compile C and C++ code. So just remove them, go into a stable system, then see if you actually need to install them later.

Also, why do you have these two versions? Did you install an additional repository with updated compilers?
```

apt policy gcc-4.8-base

```
```

gcc-4.8-base:
  Installed: (none)
  Candidate: 4.8.5-4ubuntu2
  Version table:
     4.8.5-4ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```
For my 16.04 system there seems to be only one version in the repositories.

There seems to be only one version of texstudio in my system, so presumably it should work fine with the normal "libstdc++6" dependency.
```

texstudio:
  Installed: (none)
  Candidate: 2.10.8+debian-1
  Version table:
     2.10.8+debian-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

---

