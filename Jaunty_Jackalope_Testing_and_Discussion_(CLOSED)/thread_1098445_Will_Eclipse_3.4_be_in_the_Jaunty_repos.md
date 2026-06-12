---
title: "Will Eclipse 3.4 be in the Jaunty repos?"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cdwillis on 2009-03-17
Not sure if this should be posted here, but out of curiousity is the newest version of Eclipse going to be in the repos for jaunty? I just installed the 6th alpha of jaunty and the version of eclipse I installed was still 3.2. 

If it's not being included, why?

---

### Post by tepsipakki on 2009-03-17
no, because the package is coming from debian, and the team packaging it is short of manpower. You can check the debian-java list for a package to test, it should be available somewhere IIRC.

---

### Post by tepsipakki on 2009-03-17
the package in question is here:

[http://launchpad.net/~pktoss/+archive/ppa](http://launchpad.net/~pktoss/+archive/ppa)

---

### Post by nyarnon on 2009-03-17
Just curious is PDT included?

---

### Post by Nullack on 2009-03-17
In the meantime, just install eclipse / netbeans if the ide's are behind in the repos manually from upstream.

---

### Post by lean on 2009-03-17
The big reason for me, for not using the built-in Eclipse is that you cannot install plugins.
If this has changed, then updating the built-in would be a really good idea.
The upstream version works wonderfully, so it is not a big problem IMHO.

---

### Post by MacUntu on 2009-03-17
> **lean said:**
> The big reason for me, for not using the built-in Eclipse is that you cannot install plugins.
If this has changed, then updating the built-in would be a really good idea.
The upstream version works wonderfully, so it is not a big problem IMHO.

IIRC you can install plugins but you need to be root.

Eclipse is really easy to install so I don't care.

---

### Post by Polygon on 2009-03-17
also, random question, why does eclipse REQUIRE openjdk or ecj or whatever the non standard sun-java package is? I already have sun-java installed, and i don't want alternative java packages on my system causing conflicts and all that.... if the new version does get package the dependencies should be sun-java OR whatever that other package is (name escapes me at the moment)

---

### Post by Peter Frank on 2009-04-13
I downloaded Eclipse 3.4 from upstream. Everything else has worked fine, but one headache - After Eclipse is closed, the process "Eclipse" is still staying in the background, eating up more than 100MB of RAM. It can't be terminated in Gnome-system-monitor, but has to be KILLED. Anyone also using the upstream version, could you please check whether you have this problem? Thanks in advance.

---

### Post by Peter Frank on 2009-04-13
Sorry I forgot to mention that I'm using Intrepid instead of Jaunty. I reached here by Google so didn't realize it's a Jaunty testing discussion.

---

