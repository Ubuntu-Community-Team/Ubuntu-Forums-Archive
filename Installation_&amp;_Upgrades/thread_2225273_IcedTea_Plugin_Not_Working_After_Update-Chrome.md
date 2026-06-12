---
title: "IcedTea Plugin Not Working After Update-Chrome"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by jcjanko on 2014-05-20
For reference, I am a Linux newbie/beginner, using 14.04. I could not find anything about this exact issue recently, so if it is a recurring issue I did not see it.

I was on my computer and need to use WizIQ for online tutoring. I always check my system before each session to ensure there are no problems. So I just updated my computer (there was a Chrome update listed), and Java no longer works. The WizIQ website shows Java as "failing," so I tried the Java website. It to says I need to download Java. I was using the IcedTea plugin. Therefore:

-I uninstalled and reinstalled IcedTea, nothing
-Uninstalled and installed Oracle Java 8, nothing
-Uninstalled and installed Oracle Java 7, nothing

I then checked my other computer that I had not yet updated. I first tested WizIQ, and it passed. I then checked the Java tester, and it passed, showing the IcedTea plugin. So I updated the system, confirmed there was a Chrome update, installed the updates, and it failed at both websites.

NOTE: Everything works fine in Firefox throughout all of these steps, but Chrome is the only compatible browser for my sessions for other reasons. Also, when I say "install/uninstall," I am using directions from forums like this one, and askubuntu, so that may be an issue.

I just completely wiped out any mention of Java from my system again, and started from scratch. Nothing is working. I have been checking the plugins, and I have JavaScript allowed, but when I go to "Disable individual plugins..." there is no mention of Java (not sure if there should be). 

I apologize if I missed something simple. I am going to uninstall and reinstall Chrome, as I am sure that will work, but doesn't solve the problem in the long run.

---

### Post by jcjanko on 2014-05-20
OK, I reinstalled the old version of Chrome, and everything works great. It shows 12 plugins, including Java, so this is clearly a Chrome issue.

---

### Post by monkeybrain20122 on 2014-05-21
Google has dropped support for all NPAPI plugins for Chrome/Chromium, that pretty much means all media plugins on Linux. So other than flash and html5 nothing will work on Chrome any more (e.g Apple trailers)

---

### Post by jcjanko on 2014-05-21
OK, that makes sense. Thanks!

If anyone else has this problem, I was able to (so far) get all of the tests to pass with Opera. You just need to go to the Settings Manager for flash and always allow for WizIQ before testing, otherwise it will freeze.

---

