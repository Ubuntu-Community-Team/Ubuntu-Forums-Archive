---
title: "Why do I need gcc, g++, cpp, libstdc++ 4.3 when 4.3 is available"
date: 2008-06-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-06-08
Hi all, 
 Why do I need gcc, g++, cpp, libstdc++ 4.3 when 4.3 is available . Look at 

```

shirish@Mugglewille:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
The following packages have been kept back:
  apt{a} apt-utils aptitude cpp-4.2{a} g++-4.2{a} gcc-4.2{a} gcc-4.2-base 
  kdebase-data{a} libept0{a} libstdc++6-4.2-dev{a} 
The following packages will be upgraded:
  cpp-4.3 g++-4.3 gcc-4.3 gcc-4.3-base libgcc1 libgfortran3 libgomp1 
  libstdc++6 libstdc++6-4.3-dev 
9 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 11.5MB of archives. After unpacking 12.3kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libgomp1 4.3.1-1ubuntu1 [13.5kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main gcc-4.3-base 4.3.1-1ubuntu1 [102kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libstdc++6 4.3.1-1ubuntu1 [333kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libgfortran3 4.3.1-1ubuntu1 [231kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main cpp-4.3 4.3.1-1ubuntu1 [3088kB]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main gcc-4.3 4.3.1-1ubuntu1 [2925kB]
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main g++-4.3 4.3.1-1ubuntu1 [3401kB]                                 
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libstdc++6-4.3-dev 4.3.1-1ubuntu1 [1352kB]                      
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main libgcc1 1:4.3.1-1ubuntu1 [25.6kB]                               
Fetched 11.5MB in 6min52s (27.8kB/s)                                                                             
Reading changelogs... Done
apt-listchanges: Do you want to continue? [Y/n]? Y
apt-listchanges: Mailing root: apt-listchanges: changelogs for Mugglewille
sendmail: RCPT TO:<postmaster@ubuntu> (550 not local host ubuntu, not a gateway)
(Reading database ... 359644 files and directories currently installed.)
Preparing to replace libgomp1 4.3.0-5ubuntu1 (using .../libgomp1_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace gcc-4.3-base 4.3.0-5ubuntu1 (using .../gcc-4.3-base_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement gcc-4.3-base ...
Setting up gcc-4.3-base (4.3.1-1ubuntu1) ...

(Reading database ... 359644 files and directories currently installed.)
Preparing to replace libstdc++6 4.3.0-5ubuntu1 (using .../libstdc++6_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.3.1-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 359644 files and directories currently installed.)
Preparing to replace libgfortran3 4.3.0-5ubuntu1 (using .../libgfortran3_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement libgfortran3 ...
Preparing to replace cpp-4.3 4.3.0-5ubuntu1 (using .../cpp-4.3_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement cpp-4.3 ...
Preparing to replace gcc-4.3 4.3.0-5ubuntu1 (using .../gcc-4.3_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement gcc-4.3 ...
Preparing to replace g++-4.3 4.3.0-5ubuntu1 (using .../g++-4.3_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement g++-4.3 ...
Preparing to replace libstdc++6-4.3-dev 4.3.0-5ubuntu1 (using .../libstdc++6-4.3-dev_4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement libstdc++6-4.3-dev ...
Preparing to replace libgcc1 1:4.3.0-5ubuntu1 (using .../libgcc1_1%3a4.3.1-1ubuntu1_i386.deb) ...
Unpacking replacement libgcc1 ...
Processing triggers for man-db ...
Setting up libgcc1 (1:4.3.1-1ubuntu1) ...

Setting up libgomp1 (4.3.1-1ubuntu1) ...

Setting up libgfortran3 (4.3.1-1ubuntu1) ...

Setting up cpp-4.3 (4.3.1-1ubuntu1) ...
Setting up gcc-4.3 (4.3.1-1ubuntu1) ...
Setting up g++-4.3 (4.3.1-1ubuntu1) ...
Setting up libstdc++6-4.3-dev (4.3.1-1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 10 updates [-9].

```

If not needed I could just purge the 4.2 series of gcc and others apart from apt and stuff . 

Looking forward to comments and suggestions on the same.

---

### Post by jpkotta on 2008-06-08
So gcc-4.3 etc. installed correctly?  You just want to free up space?  I would think purging the old toolchain would be OK, but it shouldn't cause problems to have several different toolchains in the same installation.  I usually have a 4.x and a 3.x toolchain installed.

---

### Post by xebian on 2008-06-09
If you don't know why you will be needing it then there is a good chance you probably don't need it.

---

### Post by psyke83 on 2008-06-09
> **ShirishAg75 said:**
> If not needed I could just purge the 4.2 series of gcc and others apart from apt and stuff . 

Looking forward to comments and suggestions on the same.

I assume you mean 4.2 in the topic? Since this is the development release and breakage is to be expected, I would imagine it's not uninstallable yet because some packages still depend on gcc-4.2-base. Solution: patience.

---

### Post by scradock on 2008-06-09
Isn't the problem really that the 4.2 series is broken, and won't install?

It's not exactly a case of keeping the old tool-chain in case the new one breaks, it's why bother to hang on waiting for the older one to be fixed.

Asking Synaptic to upgrade gcc-4.2-base results in a message asking if I want to remove a slew of programs including apturl, ubufox, totem, and gnome-app-install. On the other hand, it won't remove it either.....

---

### Post by psyke83 on 2008-06-10
> **scradock said:**
> Isn't the problem really that the 4.2 series is broken, and won't install?

It's not exactly a case of keeping the old tool-chain in case the new one breaks, it's why bother to hang on waiting for the older one to be fixed.

Asking Synaptic to upgrade gcc-4.2-base results in a message asking if I want to remove a slew of programs including apturl, ubufox, totem, and gnome-app-install. On the other hand, it won't remove it either.....

No, it's because libffi4 still depends on gcc-4.2-base, which is a dependency of some of those other packages.

Sorry, but... ;)
[rant]You should know stuff like this if you choose to use a development release.[/rant]

---

### Post by ShirishAg75 on 2008-06-10
I did see that libiff4 thing, I was just wanting to make sure that others have issue with that. 

Its not necessary that you may have the same issues that other have and vice-versa.

Also you forget there would be some people like me who even after a long time do get unsure about something or the other.

---

### Post by scradock on 2008-06-10
> **psyke83 said:**
> No, it's because libffi4 still depends on gcc-4.2-base, which is a dependency of some of those other packages.

Sorry, but... ;)
[rant]You should know stuff like this if you choose to use a development release.[/rant]
Sorry, I didn't realise this was an exclusive club.

I am a reasonably intelligent user of Ubuntu. I choose to get involved in the "testing", and I ask questions in the appropriate forum. I am not all-knowing, nor am I stupid. 

<irony>If testing is only for those who "know" stuff like that, why open it to users? Shouldn't development be done behind closed doors, so that only those who know can be involved?</irony>

I hope we all know the answer - testing works better if lots of people get involved, and hopefully the developers benefit from information about what doesn't work in more situations than they can cover themselves.

Thanks for the information about why gcc-4.2-base won't upgrade or remove. I will file that away in case I need it.

---

### Post by psyke83 on 2008-06-10
> **scradock said:**
> Sorry, I didn't realise this was an exclusive club.

I'm sorry if you interpreted my reply that way. My post in this topic may be relevant: [http://ubuntuforums.org/showthread.php?t=821839](http://ubuntuforums.org/showthread.php?t=821839)

If you watch this forum over the following weeks/months, you'll see this pattern of duplicate postings. I'm happy that users are learning how to work with the development release, but I would be much happier to see users learn the prerequisites first, and then contribute something even more substantial. Either way, it's not an exclusive club by any means... and it was just my opinion anyway.

---

### Post by scradock on 2008-06-10
> **psyke83 said:**
> I'm sorry if you interpreted my reply that way. My post in this topic may be relevant: [http://ubuntuforums.org/showthread.php?t=821839](http://ubuntuforums.org/showthread.php?t=821839)

If you watch this forum over the following weeks/months, you'll see this pattern of duplicate postings. I'm happy that users are learning how to work with the development release, but I would be much happier to see users learn the prerequisites first, and then contribute something even more substantial. Either way, it's not an exclusive club by any means... and it was just my opinion anyway.
Thanks - I have been watching, and occasionally taking part in, the testing forums for gutsy, hardy and now intrepid. I have seen more extreme rants, but as I'm only trying to help it is still irritating to be put down. 

I know I can't help with writing/patching programs; what I can do, and am trying to do, is to draw attention to what seems like unintended behavior in upgrades as they are released in testing, so that they can be checked and if necessary fixed. I am learning a lot in the process, and I'm sorry that my limited understanding limits how helpful I can be to the testing process. But how else can I learn, except by watching, and taking part in discussions?

In the current thread I simply thought it was worth pointing out that, for me at least, the "old" tool-chain -4.2 was not working anyway, which made the discussion of whether it was needed now the new one was working somewhat irrelevant. Now I, and probably many other watchers, know more about why and how the old chain is broken, which is good. Thanks for telling us.

---

### Post by ronacc on 2008-06-11
By all means keep on testing and ask questions when you need help or info , no ONE of us knows everything but collectively we can usually solve most issues . Search the forum(s) to see if your question has already been answered , duplicate posts clutter up the forum but also point up recuurent problems that mabye need addressing .The annoying posts are the ones that whine about things being broken and then threaten to go back to ( pick something ) , this is alpha / beta things are expected to be broken ')

---

### Post by scradock on 2008-06-14
> **ronacc said:**
> By all means keep on testing and ask questions when you need help or info , no ONE of us knows everything but collectively we can usually solve most issues . Search the forum(s) to see if your question has already been answered , duplicate posts clutter up the forum but also point up recuurent problems that mabye need addressing .The annoying posts are the ones that whine about things being broken and then threaten to go back to ( pick something ) , this is alpha / beta things are expected to be broken ')
I'm for sure not threatening to go back to anything else - I have two alternate 8.04 installs to use if Intrepid doesn't boot some day. I don't think I whine a lot - just try to point out if an upgrade seems not to install or work as expected.

I'm happy to see that the apt upgrade has now been fixed, which means that the original bug #236360 has been dealt with.

As far as this thread goes, the libffi (version 4) that was blocking upgrades of the -4.2 tool-chain has been replaced by libffi5, and the tool-chain now installs and upgrades correctly. Well done, devs!

As of June 12th I have no dependency problems with Intrepid - Update Manager starts with a clean slate.

Like others, I enjoy the uncertainty that goes with testing - one of my main reasons for being a Ubuntu user is seeing how it improves, often from one day to the next.

---

### Post by ShirishAg75 on 2008-06-15
Hi all, 
 Scraddock can you tell how are you able to get all the updates/upgrades. I'm still getting this :-

```

shirish@Mugglewille:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  conduit kcontrol kicker libffi4 libpt-1.10.0 
The following packages will be REMOVED:
  libldap2{a} 
The following packages will be upgraded:
  cpp-4.2 g++-4.2 gcc-4.2 gcc-4.2-base kdebase-data libldap-2.4-2 libstdc++6-4.2-dev 
8 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 9116kB of archives. After unpacking 14.4MB will be freed.
The following packages have unmet dependencies:
  kcontrol: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu3 is to be installed.
  kicker: Depends: kdebase-data (< 4:3.5.10) but 4:4.0.80-1ubuntu3 is to be installed.
  libffi4: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-0ubuntu2 is to be installed.
  libpt-1.10.0: Depends: libldap2 (>= 2.1.17-1) but it is not installable
  conduit: Depends: python-gtkmozembed which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
conduit

Keep the following packages at their current version:
cpp-4.2 [4.2.3-2ubuntu7 (now)]
g++-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2 [4.2.3-2ubuntu7 (now)]
gcc-4.2-base [4.2.3-2ubuntu7 (now)]
kdebase-data [4:3.5.9-0ubuntu7.2 (now)]
libldap-2.4-2 [2.4.7-6ubuntu4.2 (now)]
libldap2 [2.1.30.dfsg-13.5 (now)]
libstdc++6-4.2-dev [4.2.3-2ubuntu7 (now)]

Score is 323

Accept this solution? [Y/n/q/?] 

```
 
Any solution to the above is welcome.

---

### Post by psyke83 on 2008-06-15
Please search the forum first. The answers are in these threads:

[http://ubuntuforums.org/showthread.php?t=809837](http://ubuntuforums.org/showthread.php?t=809837) - KDE is broken.
[http://ubuntuforums.org/showthread.php?t=826197](http://ubuntuforums.org/showthread.php?t=826197) - read this thread and look over 23meg's old sticky threads (which will get updated soon)

Also, in this thread I mentioned that libffi4 was the reason for held back packages, although it seems to be fixed now.

The simple answer to your question is to wait for all the necessary packages to be uploaded.

---

### Post by ShirishAg75 on 2008-06-15
pyske83, that's the reason I precisely asked when scraddock says its working fine for him from 12th of June. The mirror I have is supposed to be only 5-6 hours not 3 days or mote behind hence asking to know the same.

I just upgraded to gwget 0.99-3ubuntu1, launchpad reports it as being available since last 3 hours. So my mirror should most probably have all the stuff.

Scraddock claimed it worked, other than conduit I don't know what else I can do.

---

### Post by psyke83 on 2008-06-15
> **ShirishAg75 said:**
> pyske83, that's the reason I precisely asked when scraddock says its working fine for him from 12th of June. The mirror I have is supposed to be only 5-6 hours not 3 days or mote behind hence asking to know the same.

I just upgraded to gwget 0.99-3ubuntu1, launchpad reports it as being available since last 3 hours. So my mirror should most probably have all the stuff.

Scraddock claimed it worked, other than conduit I don't know what else I can do.

I can see no evidence that Scraddock uses Kubuntu or any KDE packages. Therefore, why would he experience dependency conflicts for packages not installed on his system? I urge you to read the links I posted previously.

Aside from that, I recommend you don't use a different mirror for the development release, as there tends to be more lag compared to the official releases.

---

### Post by 23meg on 2008-06-15
You can always check whether your mirror is up to date at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).

---

### Post by scradock on 2008-06-15
Right, psyke83: I'm not using kde or any of the k... apps.

My own troubles started when I tried to stop spamassassin being installed and I found myself wrestling with evolution-based dependencies. Now I've removed evolution and apt has been fixed.....

Now that libffi5 is available I don't need libffi4, so the -4.2 tool-chain installed correctly. Maybe ShirishAg75 should try removing libffi4?

ShirishAg75 - my personal technique is to use Synaptic - once Update manager has done its standard stuff and left some packages un-installable. I open the Upgradeable list (Status) and mark one package to install. The resulting message tells me whether that will work without removing anything I don't want to lose. If there is no sign of trouble I'll let the upgrade happen.

Of course, if something is really broken it's also clear from the Synaptic message, and I can just wait for it to be fixed.

I'm sure that real experts can do it all faster and more securely using aptitude, but my limited forays with that didn't get me any further than using Synaptic. If it's broke, don't touch it. If it can be fixed, fix it. Next.....

---

