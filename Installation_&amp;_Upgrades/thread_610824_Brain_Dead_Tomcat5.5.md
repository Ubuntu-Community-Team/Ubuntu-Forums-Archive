---
title: "Brain Dead Tomcat5.5"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by michaeljbergin on 2007-11-12
Where is the tutorial for this brain dead tomcat setup that's distributed with Ubuntu or some even half way useful documentation.  For that matter where is the documents that explain this ridiculous Java setup?  It would also be nice if someone could point me to documentation stating where this entire brain dead java setup came from and why ubuntu found it necessary to completely voilate the semantics of UNIX when dealing with Java?

---

### Post by MrFSL on 2007-11-12
If you are looking for documentation, there is a wealth found at:

[http://help.ubuntu.com](http://help.ubuntu.com)

> found it necessary to completely violate the semantics of UNIX when dealing with Java?
Care to elaborate?

> It would also be nice if someone could point me to 
...most of us here are users, trying to help other users. Take a deep breath... it'll be alright... or use a different distro if you are unhappy with Ubuntu.

---

### Post by sgordon on 2007-11-18
Well, there is lots of general docs at:

[http://tomcat.apache.org/](http://tomcat.apache.org/)

I must admit to some frustration trying to (e.g.) setup wordpress on ubuntu, since the Debian/Ubuntu install deviates from the 'easy' install that wordpress tries to be, hence leaving me with little docs.

Tomcat I've found to be fairly standard, but I'm have had a lot of experience with Tomcat on a few platforms, so perhaps I'm at an advantage!

Java is still quite immature for regular users, the extra power in the platform can be a barrier to those just starting out in some ways.

michaeljbergin, what issues are you seeing? I'm trying to write some start guides to Java, Tomcat and J2EE. Topics to cover I'd like to hear and maybe some of us can help you on here.

  Si

---

### Post by michaeljbergin on 2007-12-09
I'm very glad to hear there are docs being put together for this.  I'll try to give you a rundown of what I personally found frustrating getting started.

1. I don't like that GCJ is the default Java on Ubuntu.  Its arguable if GCJ is Java, in my opinion it is not and should not be confused with it.  If it has to be included then why use such a non-standard language implementation?  Yes, I know its open source but it has compatibility issues with the canonical platform and is less known.  I really feel like GCJ is being forced on me with Ubuntu when I install it and I don't like that.  Personally I don't want ANYTHING from GCJ on my machine, nothing compiled by it and none the tools.

2. The reason I was complaining about "breaking UNIX semantics" is due to the mechanisms used to insert the selected JRE/SDK.  If I add export PATH="/myajva/bin:$PATH" to my profile and then open a terminal and run java -version it should be running the java executable in /myjava/bin if one exists whereas in Ubuntu the java symlink to the alternative is always added to the path first.  Obviously this is not breaking UNIX as I was ranting before but it drives me nuts when distros do this.  I don't see the purpose, its not any easier for me and its something Ubuntu specific that I will now have to learn instead of being able to leverage my existing knowledge of UNIX.

3. As far as the Tomcat installation goes I wasn't even able to find out where the logging messages were going.  I've been working with Tomcat since about 2000 so I have a good amount of experience with it and again don't want to have to relearn anything.  I was quickly frustrated with this and didn't spend too much time mucking with it.  I checked the log directories in the two tomcat directories I found and the general logs in /var/log but found nothing.

4. The most important point in this as far as I'm concerned is that if you're going to provide a non-standard platform then there should be an option to use a standard one as well.  I don't want GCJ in, on or anywhere near my computer let alone my production servers so I don't want it installed.

Thanks for getting back to me

---

### Post by scorp123 on 2007-12-09
> **michaeljbergin said:**
>  I don't want GCJ in, on or anywhere near my computer let alone my production servers so I don't want it installed. Yeap, I feel your pain. Same story here. What I'd suggest to you are the following things:

- get rid of "dash" and make sure "/bin/sh" points to "bash": ```
sudo dpkg-reconfigure dash
``` ... when it asks you if you want "dash" as "/bin/sh" answer 'No' here. Why would you want this? "dash" tends to break compatibility with some elaborate scripts you might have in your environment, and if that happens it's a real pain to troubleshoot this. I found out the hard way that if you disable "dash" and have "/bin/sh" point again to "bash" all problems disappear (of course before finding that one out I wasted hours and hours trying to "fix" scripts that weren't even 'broken' ...). So as you mentioned having "production servers" I will assume that you too have a bunch of important scripts that here and there perform certain jobs for you .... Trust me: You don't want "dash" and you don't want to troubleshoot those weird problems you could maybe run into. Just make sure the system uses plain old standard "bash" and all your scripts will behave the same way like they do on any other *nix that has a "bash" binary. Disabling "dash" is one of the first things I do after a fresh Ubuntu installation.

- install the Sun JDK, e.g.:```
sudo apt-get install sun-java6-jdk
``` ... For this the "multiverse" repos should be enabled (check your /etc/apt/sources.list). Once you got the Sun JDK you have to make sure it's enabled: ```
sudo update-alternatives --config javac
``` ... A dialogue will present all Java compiler environments that are available on the system. Usually it will list GCJ --which unfortunately may happen to be the default-- and the Sun JDK if it is installed. Pick the Sun JDK and voila, your Ubuntu installation should now make use of it and not GCJ any more.

- For good measure, make sure the Java runtime binaries are pointing to the correct JVM too: ```
sudo update-alternatives --config java
``` ... Ideally it should already point to the Sun JRE ... Just make sure it points to the JVM you want.

Hope this helped ...

---

