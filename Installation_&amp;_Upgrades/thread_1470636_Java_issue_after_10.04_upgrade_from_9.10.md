---
title: "Java issue after 10.04 upgrade from 9.10"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by daxm on 2010-05-03
I upgraded one of my VMware VMs that was running 9.10 to 10.04 and it seems everything is working except my ability to connect to WebEx meetings.  My guess is that it is a WebEx programming issue but I thought I'd post here too in case someone knows a work around.

When I attempt to "start" my WebEx meeting I immediately get this error:
"The requested URL /tc0505lb/webcomponents/docshow/docshow.do_siteurl=ciscosales&jvm=1.6.0_18&isJavaClient=true was not found on this server."

My pre-Ubuntu 10.04 upgraded VM is able to start a WebEx meeting just fine.

---

### Post by daemonk on 2010-05-04
Hi There,

I am having the same issue, have you managed to find any solutions?

Thanks
D

---

### Post by daxm on 2010-05-04
I have not found a solution yet.  I just reverted to my 9.10 VM for now.

---

### Post by frantid on 2010-05-04
check the release notes, they removed sun java from the repositories --  you need to add it separately -- directions in the release notes.

---

### Post by daxm on 2010-05-04
I just read the release notes and did as instructed.  I have to say though that I already had sun-java6-jre installed but I went ahead and installed sun-java6-sdk too.  Same problem.

---

### Post by doas777 on 2010-05-04
> **daxm said:**
> I just read the release notes and did as instructed.  I have to say though that I already had sun-java6-jre installed but I went ahead and installed sun-java6-sdk too.  Same problem.
did you also update your alternatives?
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by daxm on 2010-05-04
Okay.  I added that repository too.  I reviewed the apt-get install sun-java* options and I don't see what "extra" java options to install to fix this issue.

---

### Post by tshack on 2010-05-08
Hello,

It seems the issue is a result of WebEx not playing nice with openjdk and icedtea.  The following resolved the issue for me:

**1) Remove the icetea plugin**
sudo apt-get remove icedtea6-plugin

**2) Add the following repository**
sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”

**3) Update aptitude's list of available packages**
sudo aptitude update

**4) Install "real" Sun Java**
sudo aptitude install sun-java6-jdk

**5) Make sure Sun's jre is the default**
sudo update-alternatives –config java

... and select /usr/lib/jvm/java-6-sun/jre/bin/java

**6) Install the plugin**
sudo apt-get install sun-java6-plugin

(Note: This step may not be necessary)

**Check to make sure things are working**
Go to [http://www.webex.com/lp/jointest/](http://www.webex.com/lp/jointest/)

... and attempt the test meeting.

---

### Post by daxm on 2010-05-10
Thanks tshack!  That solved it for me!
:guitar:

---

### Post by whoopn on 2010-05-10
tshack, thanks for that (most of it works now)!

I have another issue, if I try to do the view remote desktop functionality in webex it doesn't work.  So I request view and it asks the remote user but doesn't show the desktop when they ok the view.

Ideas?

---

### Post by rg_stephens on 2010-05-23
Yes!! it worked for me

---

