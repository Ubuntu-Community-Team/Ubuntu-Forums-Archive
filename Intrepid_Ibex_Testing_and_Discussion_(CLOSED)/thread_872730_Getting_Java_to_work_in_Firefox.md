---
title: "Getting Java to work in Firefox"
date: 2008-07-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-07-28
I have ubuntu-restricted-extras installed which includes Java. How do I get Java working in Firefox?

---

### Post by alienexplorers on 2008-08-17
Did you add the plugin to the /usr/lib/firefox-addons/plugins directory.

---

### Post by Exsecrabilus on 2008-08-18
Well if you installed the *ubuntu-restricted-extras* package, you already have a Java web browser plugin. But you might want to install the propriety Java, since OpenJDK that gets pulled in with *ubuntu-restricted-extras* is open-source, yet not fully compatible with many websites. Install the *sun-java6-plugin* package.

---

### Post by phenest on 2008-08-18
Sorry. I read up on this a bit more, and because I'm running the 64 bit Ubuntu, there is no plugin for Firefox. Not a biggie anyway as there is only one site I visit that uses it.

---

### Post by dinxter on 2008-08-18
if you install icedtea-gcjwebplugin this is the plugin for firefox that uses openjdk 6 which is on the way if not already fully sun java compatible ( i think only the snmp classes are still closed though i may be wrong ). and works fine on my amd64 with firefox 3

---

### Post by phenest on 2008-08-18
Hmmm. I haven't had any success myself. Firefox doesn't show Java with about:plugins. I've read several how to's and concluded I needed 32 bit Firefox. But if you've done this with 64 bit Firefox, I'd be interested how you did it.

I have a fresh install of Hardy 8.04.1. Where do I go from there?

---

### Post by hufferd on 2008-08-18
> **phenest said:**
> Hmmm. I haven't had any success myself. Firefox doesn't show Java with about:plugins. I've read several how to's and concluded I needed 32 bit Firefox. But if you've done this with 64 bit Firefox, I'd be interested how you did it.

I have a fresh install of Hardy 8.04.1. Where do I go from there?


I myself had this same issue and had no luck at all with getting java to work in firefox.  on the 8.04 64 bit distro..... My fix and most don't agree with this....  Was to go back to the 8.04 32 bit OS it will run on a 64 bit machine.  Since I have done that everything has been working fine with out issue
:guitar:

---

### Post by phenest on 2008-08-18
Well now I feel dumb. I just installed the icedtea-gcjwebplugin package with no joy. Then I discovered Java was disabled in Firefox's preferences. Now it shows up in about:plugins.:redface:

The one web site I want to use is [BT's speedtester page]("http://www.speedtester.bt.com/"). I can't get it to work.:confused:

---

### Post by dinxter on 2008-08-18
as far as i remember simply installing icedtea-gcjwebplugin should do it with no other messing around (icedtea-gcjwebplugin pulls in openjdk automatically and install as a xulrunner 1.9 addon which firefox 3 should use) the plugin should show up as gcj  web browser icedtea plugin 1.0 in firefox (tools->addons->plugins) no special 32bit workarounds or nswrapper is needed

---

### Post by dinxter on 2008-08-18
we've all been there or thereabouts :)

---

### Post by Gina on 2008-08-20
I couldn't get the BT speedtest site to work in Linux - had to use the legacy OS to check my BT profile :(

---

### Post by phenest on 2008-10-16
Somehow, I lost my Java plugin. At some point it's been uninstalled (don't know how that happened), so I tried installing it again:
```
steve@precision:~$ sudo apt-get install icedtea-gcjwebplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  icedtea-gcjwebplugin: Depends: icedtea6-plugin but it is not going to be installed
E: Broken packages

```

---

### Post by dinxter on 2008-10-16
yep, the plugins been renamed to icedtea6-plugin and the previous name is just a dummy package. if your repos are up to date? it should be in there, i think it only arrived in the last couple of days. might just have to wait for a sync or something

---

### Post by dinxter on 2008-10-16
actually, i just tried installing the icedtea-gcjwebplugin package directly and it does seem broken, install icedtea6-plugin directly works fine though. this should probably be reported as a bug against the icedtea-gcjwebplugin transitional package if it hasnt been already

---

### Post by dinxter on 2008-10-16
bunged bug report [here]("https://bugs.launchpad.net/ubuntu/+source/icedtea-gcjwebplugin/+bug/284299")

---

### Post by SnakeHips on 2008-10-19
I have the Java up and running on AMD64 though the cpu takes a major hammering on some site's...

Linux 2.6.27-7-generic on x86_64
pete@desk:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

---

### Post by w0ng on 2008-10-19
> **SnakeHips said:**
> I have the Java up and running on AMD64 though the cpu takes a major hammering on some site's...
I've installed openjdk-6-jdk and icedtea6-plugin, but some websites that require java completely freeze for me.

For example, my uni page: [http://learn.mq.edu.au](http://learn.mq.edu.au)
- I can view that page fine.
- Clicking the "Check Browser" link -> freezes on "Loading applet..."
- Entering my Username/Password and pressing "Login" -> Firefox completely freezes up
- I exit Firefox via "Force Quit"
- firefox process still runs afterwards -> have to "killall firefox"

Now, after removing icedtea6-plugin and accessing [http://learn.mq.edu.au](http://learn.mq.edu.au) again....
- "Check Browser" link loads up instantly
- Able to "Login" using Username/Password without CPU hammering or freezes

---

### Post by bpl07 on 2008-10-19
One thing I noticed on my system was that a lot of the library files were missing the link to libjvm.so and libmawt.so.  Do an ldd on each of the .so files in /usr/lib/jvm/jre/openjdk*/lib/amd64 to see if you're missing them too.  I fixed it by adding symlinks to libjvm.so and libmawt.so, which are located in subfolders of ./amd64.  Not sure if it's a bug or not, just something I noticed.

---

### Post by SnakeHips on 2008-10-23
> Now, after removing icedtea6-plugin and accessing [http://learn.mq.edu.au](http://learn.mq.edu.au) again....
- "Check Browser" link loads up instantly
- Able to "Login" using Username/Password without CPU hammering or freezes

You removed the plugin and it works better ???

---

