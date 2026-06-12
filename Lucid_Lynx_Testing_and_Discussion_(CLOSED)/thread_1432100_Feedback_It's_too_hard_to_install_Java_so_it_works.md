---
title: "Feedback: It's too hard to install Java so it works in firefox !"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Andre-D on 2010-03-17
I am testing 10.04 
- it's too hard to get a working Java in Firefox, you have removed Sun's Java, and installing OpenJRE does nothing good, as firefox does not seem to know about it..

when I have trouble with it, It's way too hard for new users, please fix.

---

### Post by cariboo on 2010-03-17
Installing the ubuntu-restricted-extras meta package always works for me.

---

### Post by wilee-nilee on 2010-03-17
> **Andre-D said:**
> I am testing 10.04 
- it's too hard to get a working Java in Firefox, you have removed Sun's Java, and installing OpenJRE does nothing good, as firefox does not seem to know about it..

when I have trouble with it, It's way too hard for new users, please fix.

cariboo is correct the restricted extras install what you need, along with other stuff.

---

### Post by Keyper7 on 2010-03-17
EDIT: Nevermind, bad mood today.

---

### Post by 23meg on 2010-03-17
This forum is not the correct place to provide feedback, if that's what you want to do. If you want problems fixed, please [report them]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by Andre-D on 2010-03-17
> **wilee-nilee said:**
> cariboo is correct the restricted extras install what you need, along with other stuff.

yes, but this at least gettig Java, must be *easy* for anybody.
things like this give Linux a reputation of being hard to use..

- I just hope people that can do something about it are reading this.
- this is not a bug, so I cannot submit it as a bug.

---

### Post by katie-xx on 2010-03-17
Hiya Andre
Ubuntu 10.04 has bundled Firefox 3.6 as the default browser so you are right, IMHO, to ask if there is an issue with Java.
There is.

> 
MORE TECHNICAL  INFORMATION                  
        
                                                                                                                                                                                           Starting in Firefox 3.6, [Mozilla foundation will  drop support on OJI (Open Java Virtual Machine Integration)]("http://java.com/ffplugin-releasenotes") and will  only support the standard NPAPI and NPRuntime interfaces. The Java  Plug-in which is in Java version 6 update 10 or newer versions supports  the NPAPI and NPRuntime interfaces. Therefore, starting with Firefox  3.6, Java-based applets will NOT work unless you are running Java  version 6 Update 10 or newer. 
You really need to go here to get the heads up. [http://java.com/en/download/faq/firefox_newplugin.xml](http://java.com/en/download/faq/firefox_newplugin.xml)

> 
 this is not a bug, so I cannot submit it as a bug.


Well someone did :) 

[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/496097](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/496097)



I hope that helps


Kate

---

### Post by wojox on 2010-03-17
Heres what I use: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by cariboo on 2010-03-17
I have the lastest IcedTea plugin installed, and don't seem to have any problems with java. See screen-shot. I'm running Firefox 3.6

---

### Post by katie-xx on 2010-03-17
Hi and very interesting.
Can you get these applets running with icedtea ? 
[http://www.bmreports.com/bwx_reporting.htm](http://www.bmreports.com/bwx_reporting.htm)
I couldnt.


Kate

---

### Post by glasen on 2010-03-17
Works perfectly for me. I've installed the following packages :

[LIST]
[*]openjdk-6-jre
[*]openjdk-6-jre-headless
[*]openjdk-6-jre-lib
[*]icedtea6-plugin
[/LIST]

All versions are "6b18~pre2-1ubuntu1".

---

### Post by buzzmandt on 2010-03-17
> **katie-xx said:**
> Hi and very interesting.
Can you get these applets running with icedtea ? 
[http://www.bmreports.com/bwx_reporting.htm](http://www.bmreports.com/bwx_reporting.htm)
I couldnt.


Kate

my about:plugins shows icedtea just as the previous screenshot does and bmreports:

---

### Post by cariboo on 2010-03-17
> **katie-xx said:**
> Hi and very interesting.
Can you get these applets running with icedtea ? 
[http://www.bmreports.com/bwx_reporting.htm](http://www.bmreports.com/bwx_reporting.htm)
I couldnt.


Kate

You mean like in the screen-shot?

---

### Post by katie-xx on 2010-03-18
Yes they are running ok for you. 
I cant get them running on Firfox 3.6 and quite a few other people cant either without installing the appropriate Java updates.
The OP asked a reasonable question and there is a bug filed and accepted.
My real concern is the hostile reception the OP received after posting an entirely reasonable question
 
Kate

---

### Post by Uncle Spellbinder on 2010-03-18
> **wojox said:**
> Heres what I use: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

+1

And it's fast, simple, works perfectly. What more could anyone want?

---

### Post by philinux on 2010-03-18
> **Uncle Spellbinder said:**
> +1

And it's fast, simple, works perfectly. What more could anyone want?

Hardly easy for a "new" ubuntu user. ;)

---

### Post by rogerdean on 2010-03-18
I agree with you Kate. I've seen a couple of Lucid Development threads recently where discussion of (what I consider to be) reasonable issues is being discouraged. This isn't a tone I've noticed on Ubuntu forums before, which are otherwise fairly happy and free-wheeling, and I hope it's just a phase.
Roger

---

### Post by katie-xx on 2010-03-18
I really think the point is getting missed here.
The OP posted in good faith and it was, IMHO, an entirely reasonable and valid post.
In addition, someone else had already filed a bug report on this very subject and it has been accepted as such.
I think we should all be able to agree there was nothing wrong with the original post.
We all know how to update the java runtime and plug ins but that has nothing at all to do with the OPs complaint. 
Amazingy when I asked the respondents if they could open a heavily java dependent site using what is available in the repositories .. they replied by saying yes .....but using the latest updated runtimes!!!! 
 
The OP was given a hostile reception and at least one of the respondents told the he or she to go elsewhere.
 
I dont think thats very nice and doesnt fit very well with the mostly friendly and helpful sprit of this particular forum.
 
Not too much more to say really except I hope the links given to the OP help.
 
 
Kate
 
oops: Missed your post Roger sorry

---

### Post by Uncle Spellbinder on 2010-03-18
> **philinux said:**
> Hardly easy for a "new" ubuntu user. ;)
Point taken. But if one follows it exactly, you can't miss. One of the best step-by-step tutorials I've seen, actually.

---

### Post by linusr on 2010-03-18
> **katie-xx said:**
> Yes they are running ok for you. 
I cant get them running on Firfox 3.6 and quite a few other people cant either without installing the appropriate Java updates.
The OP asked a reasonable question and there is a bug filed and accepted.
My real concern is the hostile reception the OP received after posting an entirely reasonable question
 
Kate

Using java in Ubuntu had been an real pain from Karmic.

For me, java plugin works if I start Firefox from terminal. If I start via shortcut(application menu) all I get is blank applets!!

It's got to be some configuration, possibly I made installing Eclipse/NetBeans... but still it's so weird

If I use Java from Sun website and decide to install Eclipse from repo, because of dependency opendjdk will get installed!!!

And this makes me think if Netbeans/Eclipse/Java should really be in official repo?

---

### Post by philinux on 2010-03-18
> **Uncle Spellbinder said:**
> Point taken. But if one follows it exactly, you can't miss. One of the best step-by-step tutorials I've seen, actually.

Yep I agree. Now I could follow it no problem. 3 years ago stepping away from Win ME it would have been a bit daunting.

---

### Post by cariboo on 2010-03-18
The current java version in the repositories works great on a default install. If you have to install a different version to support an application that isn't in the repositories, I agree it can be a bit of a dog's breakfast to install.

---

### Post by katie-xx on 2010-03-19
> **cariboo907 said:**
> The current java version in the repositories works great on a default install. If you have to install a different version to support an application that isn't in the repositories, I agree it can be a bit of a dog's breakfast to install.
 
No that isnt the case.
The default install is Firefox 3.6 and the correct plug in is not available from the repositories.
That is why the OP posted in the first place.
This has been reported as a bug and accepted as one ....check out the link posted earlier.
If there has been a change made since then ..ok. This wasnt the case last night when I checked.
 
Kate

---

### Post by emarkay on 2010-03-21
> **katie-xx said:**
> No that isnt the case.
The default install is Firefox 3.6 and the correct plug in is not available from the repositories.That is why the OP posted in the first place.This has been reported as a bug and accepted as one ....check out the link posted earlier.If there has been a change made since then ..ok. This wasnt the case last night when I checked.
 Kate

Interesting - Kate, your referenced site hangs FF in a new Beta i install, with just the "restricted extras" installed.

I see that "Sun Java 6" is no longer available as reported, but what is the workaround for your site and has a bug been filed to specifically address this issue in FF/Java?

Oh nevermind, see this thread for Java issues:
[http://ubuntuforums.org/showthread.php?p=9004764](http://ubuntuforums.org/showthread.php?p=9004764)

---

### Post by jrusso2 on 2010-03-21
Maybe someone can explain this to me.   A couple years ago much was made of Sun Java being Open Source but it is not default.

Why is this?

---

### Post by Andre-D on 2010-03-21
good question indeed...

---

### Post by emarkay on 2010-03-21
OK - now I am confused.
All these posts relate to Java and Firefox, and there are problems...

[http://ubuntuforums.org/showthread.php?t=1430555](http://ubuntuforums.org/showthread.php?t=1430555)
[http://ubuntuforums.org/showthread.php?p=9004693](http://ubuntuforums.org/showthread.php?p=9004693)
[http://ubuntuforums.org/showthread.php?t=1425789](http://ubuntuforums.org/showthread.php?t=1425789)
[http://ubuntuforums.org/showthread.php?t=1425111](http://ubuntuforums.org/showthread.php?t=1425111)

What is the status and how does a "noob" get a simple Java App to run in FF in Lucid, (other than having to know to install "Ubuntu Restricted Extras")?

This official Java page provides a test to verify Java:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
I see it running OK ("Java 6 Update 18"), however this page has some apps that hang FF:
[http://www.bmreports.com/bwx_reporting.htm](http://www.bmreports.com/bwx_reporting.htm)

Thanks

---

### Post by Longinus00 on 2010-03-22
Installing icedtea6-plugin works fine here.

---

### Post by Longinus00 on 2010-03-22
> **jrusso2 said:**
> Maybe someone can explain this to me.   A couple years ago much was made of Sun Java being Open Source but it is not default.

Why is this?

[http://en.wikipedia.org/wiki/Icedtea#History](http://en.wikipedia.org/wiki/Icedtea#History)

---

### Post by ankspo71 on 2010-03-22
Lucid is playing hocus pocus. Sun java6 has come and gone once or twice already and now it's back again. :p Icedtea and openjdk is working fine for me, as far as web java applets go, so I'll keep them installed. I don't recommend installing icedtea and Sun java at the same time because it kept my firefox 3.6 from starting, so be careful of that.

openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-6-jre-cacao
icedtea6-plugin
all was installed with ubuntu-restricted-extras
(this is a 32bit system)

---

### Post by aviramof on 2010-03-22
i'm using ubuntu-restriceted-extras and icedtea for java.

---

### Post by Brandon Williams on 2010-03-22
The one java app I have to use does not work correctly with openjdk and icedtea, so I really must use sun's runtime and plugin. I was surprised to see that neither this thread nor any of the others I could find said anything about getting sun's plugin to work on lucid (or with firefox-3.6 in general). Maybe my search string wasn't good enough. Anyway, here's how to do it. 

First, open 'Software Sources', click the 'Other Software' tab, and verify that the lucid partner repo is enabled. If it doesn't show up on the list, add it: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Next, install sun-java6-plugin and uninstall both icedtea6-plugin and openjdk-6-jre.

And finally, due to [this bug](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174), run the following command:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/mozilla-javaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 1
```
This is the only step that is specific to firefox-3.6 and lucid.

Restart firefox and check about:plugins to verify that the correct plugin version is loaded.

If icedtea and openjdk work for the apps you use, then I recommend that you continue to use them rather than switching to the sun versions. However, if you use apps that do not work correct with ubuntu's default java installation, the above should work.

---

### Post by Andre-D on 2010-03-22
openjdk does *not* work for several Norwegian banks, nor does it work with "norsk-tipping" - (Norwegian governments gambling monopolist)

Anyway, all answers aside, my main point stands strong:
[SIZE="5"]
This is scaring away new users because it's so hard to get a simple thing as Java to work in Ubuntu ?[/SIZE]

I think this is a big *miss* from the Ubuntu team, and would like to know how I can make them aware of that ...

---

### Post by ankspo71 on 2010-03-22
I don't know if you already have, but you can report it to the Ubuntu bug site. For example, the procedure for reporting icedtea6-plugin is:
```
ubuntu-bug icedtea6-plugin
```You type that into the terminal and it will generate a bug report for you and automatically direct your browser to the page that it gets reported to. While you are there, give them some example sites where java does not work for you. If they get a couple of sites to look at, it might give them better ideas on how to improve the code. 

If you would like to know if it is a problem with Ubuntu's version of firefox, go to the firefox homepage and download the firefox-3.6.tar.bz2 . Save it to your desktop, extract it to the desktop, then click on the ' firefox ' file inside that folder. Installation will not be neccessary. When it opens, it will automatically load your addons and plugins. Test it on the same sites that gave you trouble. If it does give you trouble, then the problem is with java. If it doesn't give you trouble, then likely the problem is with Ubuntu's version of firefox. 
```
ubuntu-bug firefox
```(Also include java version information.)
I hope to see this sorted out before the final release and I hope this helps find the problem. I believe the other poster found instructions for you to install Sun java6 with Firefox 3.6. Give that a try, but if that also gives you trouble then report that too.

---

### Post by Andre-D on 2010-03-22
such reports ends only up being labelled "not-a-bug" and that's it.

---

### Post by emarkay on 2010-03-22
OK, so my "Lucid Java Issues" thread was merged into here - fine.

What is the status of Java in Lucid at the Beta stage?

What problems are users encountering?

What other software from the repos needs to be installed, beyond the default, to get a majority of the Java Apps out there functioning?

Finally, after all that, who is still having Java issues - please post the info and URL, and applicable Bug # if possible here in this thread.

Also, Andre D - "*such reports ends only up being labeled "not-a-bug" and that's it."*
Can you elaborate - Launchpad is generally pretty good at getting even the most confused and questionable submission into a legit Bug Report.

---

### Post by Reiger on 2010-03-22
First of all that Google site is incomplete. It will for instance fail to use your new Java through JNLP (Java Webstart) which is kind of the recommended way for Java applications from the internet to run locally. The reason is that there about a dozen java related tools/executables that need to be set to preferred through update-alternatives... 

...

And then the Google site is plain outdated considering there is a new version of SUN's Java (1.6 update 18) in the repositories anyway.

---

### Post by Brandon Williams on 2010-03-23
The fact that openjdk and icedtea are the default java implementations is indeed not a bug. It makes sense for Ubuntu to default to using a fully open source java implementation. After all, openjdk is mostly the same code as sun-java6, it passes the technology compatibility kit tests, and it works for the vast majority of java applications. I went back and tried icedtea on the site that I referenced in my post yesterday, and it works in lucid (it didn't in karmic), so I know that the software continues to improve over time.

All of this having been said, openjdk does not work for all java applications. Some users will have to install sun's version that contains some non-sun proprietary code. After [the current packaging bug](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/532174) has been fixed (hopefully before the final lucid release), this will be a simple process: 1. ensure that the partner repository is enabled, 2. remove icedtea and openjdk, 3. install sun-java6. This is the same process for getting flash and acrobat reader installed, so I'm having a hard time seeing anything so difficult in these three steps that a new user would be scared away from Ubuntu. If there is a specific source of difficulty that I'm just missing here, please let me know what it is.

> What is the status of Java in Lucid at the Beta stage?

What other software from the repos needs to be installed, beyond the default, to get a majority of the Java Apps out there functioning?

If you install icedtea6-plugin, it works for the majority of Java Apps out there. There are no extra steps required other than installing the package.

> What problems are users encountering?

Finally, after all that, who is still having Java issues - please post the info and URL, and applicable Bug # if possible here in this thread.

Some apps still do not work with icedtea, so it's necessary to install sun-java6-plugin from the partner repo instead. There is a problem with the packaging (see the bug I linked to above) that requires a single command to be run on the command line. After that, the sun plugin is recognized by firefox-3.6.

---

