---
title: "java on frech 9.10 help...."
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by meomike2000 on 2009-11-29
have a fresh install of ubuntu 9.10 install and was trying to get java workin, went to the sun website then to java and tested my java and it says that my version is 6.15 and that i need to upgrade to 6.17, well i did as i always would and downloaded the updated version, followed the instructions. this has always worked in other versions but not this time..... any help would be great

thanks in advance mike.

---

### Post by TennTux on 2009-11-29
Mike. I'm thinking you havn't quite given us enough info to go by. After reading your post I'm not exactly sure what your trying that does not work. Are you trying to compile Java, are you trying to run a Java app or are you trying to run a Java Applet in a web browser??? And just to be a little clearer on what version your running what is the complete results of running ```
java -version
``` from the command line?

---

### Post by meomike2000 on 2009-11-29
ok, hopefully this will clear things up....

i have just installed a fresh, new, not upgrade, copy of 9.10 on my machine.
when i go to a web site that requires java, i get errors, so i went to the java web site, [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp), and under the big blue button that says FREE JAVA DOWNLOAD, i click on ,DO I HAVE JAVA?, link and after the test is complete, i get a message saying that i have version 6 update 15 and that i need to upgrade to version 6 update 17.....

i downloaded the linux self extracting file and followed the instructions as i have many times to upgrade but this time it will not take.....

as for the version this is what i get....

> 
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)


hope this helps to clear things up a little......

thanks mike....

---

### Post by phillw on 2009-11-29
> **meomike2000 said:**
> ok, hopefully this will clear things up....

i have just installed a fresh, new, not upgrade, copy of 9.10 on my machine.
when i go to a web site that requires java, i get errors, so i went to the java web site, [http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp), and under the big blue button that says FREE JAVA DOWNLOAD, i click on ,DO I HAVE JAVA?, link and after the test is complete, i get a message saying that i have version 6 update 15 and that i need to upgrade to version 6 update 17.....

i downloaded the linux self extracting file and followed the instructions as i have many times to upgrade but this time it will not take.....

as for the version this is what i get....



hope this helps to clear things up a little......

thanks mike....

That's the version I'm running and I have no issues - can you post the site that is giving you a problem,

Thanks,

Phill.
P.S. You're not running NoScript or one of the apps to block Java ?

---

### Post by meomike2000 on 2009-11-29
the site is [www.nthaklik.com](www.nthaklik.com), a site that i am workin on that is mostly ajax......

and i dont have the problem on my laptop, but it is ubuntu 8.04,
when i installed the laptop i followed the same setup on the java site to get it working.....

no i dont have no java blockers that i know of, and java and javascript is enabled in firefox.......

did the firefox pluggins directory get moved or does somebody know the location of the directory as this is the directory that you have to create the symbolic link in during the java update, as this could be my problem, i think that the directory should be /usr/lib/firefox-addons/plugins ?

does anybody know if this is correct?

---

### Post by phillw on 2009-11-29
I've just managed to crash my Ffox 3 times by going to the test-java site. So, I'm pretty stuck as to where to go from here - I'll see if i can get the update manually.

I may be a while ....

Regards,

Phill.

---

### Post by phillw on 2009-11-29
> **meomike2000 said:**
> the site is [www.nthaklik.com]("http://www.nthaklik.com"), a site that i am workin on that is mostly ajax......

and i dont have the problem on my laptop, but it is ubuntu 8.04,
when i installed the laptop i followed the same setup on the java site to get it working.....

no i dont have no java blockers that i know of, and java and javascript is enabled in firefox.......

did the firefox pluggins directory get moved or does somebody know the location of the directory as this is the directory that you have to create the symbolic link in during the java update, as this could be my problem, i think that the directory should be /usr/lib/firefox-addons/plugins ?

does anybody know if this is correct?

I've just tried to register on the site 

> **Warning**:  include(conf.php) [[function.include]("http://www.nthaklik.com/signup/function.include")]: failed to open stream: No such file or directory in **/home/mike/web/newnthaklik/signup/error_create_user.php** on line **6**

**Warning**:  include() [[function.include]("http://www.nthaklik.com/signup/function.include")]: Failed opening 'conf.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/home/mike/web/newnthaklik/signup/error_create_user.php** on line **6**
 			 			
			 			 		 		 			

I'm NOT having a good day :-\

Phill.

---

### Post by phillw on 2009-11-29
I don't have time for this tonite - I've got to ensure i translate all their commands into sudo as su to root is disabled on my system.

Also, I think that ossec, my security system, may be blocking the script from doing too much to my computer (I have it also set up as a server)

soz I can't help - try the programming area - one of the guyz or glaz over there may know what is going on.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Phill.

---

### Post by meomike2000 on 2009-11-29
well thanks for the help any how.......

---

### Post by meomike2000 on 2009-11-29
that error on line 6 was mine, thanks for finding it for me, but why would you have been on the error page i dont know, how far into the signup did you get before the error if you might tell me.....




just a note, this is not the machine that has the web site on it..... that machine works fine.......

---

### Post by phillw on 2009-11-29
> **meomike2000 said:**
> that error on line 6 was mine, thanks for finding it for me, but why would you have been on the error page i dont know, how far into the signup did you get before the error if you might tell me.....




just a note, this is not the machine that has the web site on it..... that machine works fine.......

I had completed the personal details - address, etc - pressed submit.

Regards,

Phill.

---

### Post by meomike2000 on 2009-11-29
thanks for the info, i have tested that from my laptop, found couple errors, that site is a migration from an older version, still has some bugs, not even complete yet..... thank you for your help even though was off topic.....

mike

---

### Post by TennTux on 2009-11-29
I'm not going to be as much help as I was hoping I would be, but I seem to recall that on the Sun Java sight, somewhere, there is a Java Applet test page. Does this work correctly? Or can you create the simplest "Hello World" java applet and see what happens when you try to access it? Can you see the Java Console? Are there error messages? How about the Java Control Panel? System->Preferences->Sun Java Control Panel? Are your policy(s) set up correctly?

I suspect you have tried some or all of these, but figured it wouldn't hurt to mention them.

---

### Post by meomike2000 on 2009-11-29
yes there is a test page on the sun website, link is located under the download button, in the middle, for the latest java update, version 6 update 17, when i too this i get an oops and i need to upgrade to version 6 update 17 and that my current version 6 update 15. no i do not have the panel under sys/admin. i dont have the console under tools on fire fox. as i said i tried to do the upgrade via the instruction on the linux self extract version, this has worked for me on other versions of ubuntu. did the plugins directory get changed for fire fox, does anybody know?
i ask this again because the sym link for the update is in the pluggins directory but firefox still dont use it.......

thanks in advance mike.....

---

### Post by meomike2000 on 2009-11-29
well after many tries to get this update to take i got it, not real sure how though, while working on setting up networking i did a restart and under system/preferences the sun java plug in control panel showed up, went there and added the new version, tested again at the java site and all works well, also the error console shows up under tools in firefox now as well.....

thanks to all that helped,
mike

---

