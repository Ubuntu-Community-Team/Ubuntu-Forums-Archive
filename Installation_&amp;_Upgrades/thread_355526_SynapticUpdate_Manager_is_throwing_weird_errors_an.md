---
title: "Synaptic/Update Manager is throwing weird errors and I can no longer install packages"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2007-02-07
I noticed the updates icon by the clock yesterday, and clicked it like I always do.  It installed around 9 new packages and everything was fine.  Later in the day it had some more updates so I also installed them.  They all worked except the package "samba".  It tells me to open synaptic and find the broken package and fix it.  When synaptic opens it tells me there is one broken package, and I found it.  It agrees that "Samba" is broken.  When I try to update it or to remove it it gives me this error:
"E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb: subprocess new pre-removal script returned error exit status 102"

The update manager also gave me a command to try, I believe it was:

"sudo apt-get install-update -f"  or something to that effect, but it didn't help either.

Anyone see this problem before?  Everything was fine until yesterday.

Running Ubuntu 6.06LTS

---

### Post by taurus on 2007-02-07
Applications -> Accessories -> Terminal
```
sudo apt-get --install -f
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nexus_2006 on 2007-02-07
Ok, your first line is like the one I was trying to remember.  I tried it and it said that install was an unrecognized command.  I ran the other three, and they all worked, but apt-get upgrade gave me the following error:

```
nexus@Lithium:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.
```

So I tried apt-get -f install and everything was normal for a minute, then this came out:

```
Fetched 2845kB in 26s (108kB/s)
Preconfiguring packages ...
(Reading database ... 122191 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ivodalves on 2007-02-16
Hi,

I've the exactly same problem!

How can I fix this?

Ivo

---

### Post by elraun on 2007-02-17
i'm also having this problem. how can i install the specified version of samba-common?

"samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed"

---

### Post by eapache on 2007-02-17
According to the error it's giving, the samba package depends on version 3.1 of the samba-common libraries. You have version 3.2 installed (a more recent version) so it's crashing because of unmet dependencies (it would probably still work, but synaptic won't take that chance).

I'm running Ubuntu 6.10 with Samba 4.1 installed, so I'm not having this problem, but it looks like a problem at the update server's end. It seems that they updated one package, but not the other. I'd wait a few days and recheck for updates. They should have updated the second package by then.

---

### Post by picker77 on 2007-02-18
I'll throw in my "me too". I'm having exactly the same problem with a supposedly "broken" file in the latest Samba update. Can't see anybody else on my network, but I can still get out to the internet.

I get the same "broken Samba package" error, and the "error 102" as everyone else. Lots of posts the past few days on this since the latest update was released.

I sure hope the brain trust comes up with something soon on this. It appears to be a widespread problem with this latest update.

---

### Post by sachakagan on 2007-03-15
I have exactly the same problem, and the instructions from Taurus in this thread do not fix it. I see that the last post is three weeks old... Did someone give the solution on another forum thread?

(I also tried to just upgrade to Edgy but it won't do it, always because of the same broken samba issue...)

Thanks in advance for your help...

---

### Post by sachakagan on 2007-03-17
I found back a thread with a solution that seems to work, and that's quite easily implemented: check out there: [http://www.ubuntuforums.org/showthread.php?t=363153](http://www.ubuntuforums.org/showthread.php?t=363153)

---

