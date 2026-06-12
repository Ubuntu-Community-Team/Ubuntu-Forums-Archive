---
title: "Just downloaded the 10.04 A3 ISO"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Woolio1 on 2010-02-25
Gentlemen.

I just downloaded the Ubuntu 10.04 A3 ISO, and I'm wondering: Is there anything I should know about before partitioning my hard drive and installing it? I've read about all the bugs, et cetera, but I want to know if there's anything REALLY UBER IMPORTANT that I should know. 

Planning on installing it on my Dell Mini 10, it's a sandbox for this kind of stuff. Any hardware incompatibilities? It's the Desktop edition, I assume it'll work.


Henry Ericson
Not a spy.

---

### Post by The Toxic Mite on 2010-02-25
Being an alpha release, it'll be obviously buggy. If you're into testing though, I'd recommend submitting bug reports onto Launchpad while testing Lucid.

Good luck :-)

---

### Post by NightwishFan on 2010-02-25
I have some major issues with X, but nothing I can't handle. It also seems like disk performance is weird. Even on a preempt kernel I get sound dropouts when a database is loading.

I am using it day to day however **because** of the new preempt kernel. It simplifies me compiling one with those exact settings on my own.

---

### Post by qra0 on 2010-02-25
I don't know. The Kubuntu installer doesn't work for some reason.

---

### Post by cariboo on 2010-02-25
Check out the [Release Notes]("http://www.ubuntu.com/testing/lucid/alpha3"), scroll down to Known Issues. As usual there is always useful information.

---

### Post by Didius Falco on 2010-02-26
> **cariboo907 said:**
> Check out the [Release Notes]("http://www.ubuntu.com/testing/lucid/alpha3"), scroll down to Known Issues. As usual there is always useful information.

It's just as important for those who've been on Alpha 2 and upgraded through updates. Of particular interest is this section:
 > **Issue when  upgrading from Lucid Alpha 2**

    
 If you installed Lucid prior to  Alpha 3, you may have libmysqlclient16 7.0.9-1 installed.  This  package was present in the Ubuntu archive by mistake and was retracted,  but because it has a later version number than the real libmysqlclient16  package, the real package will not be installed automatically on  upgrade.  To ensure that you have the official package installed on your  Lucid system and will receive security support for it throughout Ubuntu  10.04 LTS, please run sudo apt-get install libmysqlclient16/lucid  and follow the instructions.


---

