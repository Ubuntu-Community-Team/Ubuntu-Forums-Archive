---
title: "Need help with a College math plugin for jre6/firefox. (ALEKS)"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by jackechanprime on 2010-09-11
Ok, so ALEKS is a jre6 based plugin for Firefox. It's a online math homework system which seems to be a horror story to get to actually run on ubuntu. (I've seen a multitude of threads already of people with problems getting it to run -at all-) The bottom line is, the way my pre-calc class is formatted is that if i don't complete what this program wants me to do, i automatically fail the course. I've already pursued multiple help avenues, including the ALEKS corporation whom prefer the business stance of believing that Linux doesn't exist, ergo offer little-to-no real help with it. My professor himself is unable to render assistance through ignorance/time constraints, and nothing i've been able to dig up elsewhere has helped with the problem. (i even tried the college's tech support team, no gold... ;_;. )

So the actual problem is this: I have the program installed (which was in itself a hairball and a half to get done) BUT there are some interface errors which are critically interfering with the program's operation. Like i said, it's a math homework program. The first error is that the internal script for the actual answer interface is not running and/or rendering, at all. As such, even though the rest of the program is running happily in the background, i cannot actually enter any form of answer. The second problem is almost identical to the first. Another script is not functioning, but this one is the one that handles page to page navigation within the program. the "next, done, back, explain, submit, etc. etc." buttons interface is not running/rendering. Obviously, the most troublesome of that bunch is the "submit" button's absence, making it doubly impossible to actually complete my homework when i cannot A) answer the question, and B) submit my answer.

Anyway, dealing with scripts and java in general is waaaaaay over my head. I really need some help here. Like i said, if i cant get this program running, i automatically fail the course, and i mean NO EXCEPTIONS. if i cannot get ALEKS online, i have to consider some pretty ugly alternatives. At the moment i'm spending 10hour sundays in the school library where they have the plugin running on the student computers, which are a critically limited resource (and have been all in use on more than one occasion.) Obviously that cannot remain the case, and if this cannot be resolved I'll probably have buy windows and get it running that way... which makes me want to gag. (not to mention makes my wallet scream in pain.)

PLEASE help.
~Q

---

### Post by lykeion on 2010-09-11
Since I had nothing better to do I actually tried out the Aleks program to see if it would work for me.
I'm using Ubuntu Lucid, Firefox 3.6.9 with Sun Java Plugin 1.6.0_20 (libnpjp2.so) 
and I had no problem with getting the Aleks plugin to work. I couldn't reproduce the input errors either, everything worked like it should.

To install the plugin I followed this guide:
[http://samanathon.com/how-to-install-the-aleks-java-plugin-in-firefox-ubuntu-710-gusty-gibbons/](http://samanathon.com/how-to-install-the-aleks-java-plugin-in-firefox-ubuntu-710-gusty-gibbons/)

Since earlier I have removed the OpenJDK and IcedTea plugin and installed Sun Java 6 JRE & Plugin
To do this in a terminal enter:
```
sudo apt-get remove icedtea6-plugin openjdk-6-jre
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
```
Then I downloaded the jar file (aleksPack10.jar) and copied it to /usr/lib/jvm/java-6-sun/jre/lib/ext/
```
wget http://www.aleks.com/aleks/java/aleksPack10.jar 
sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun/jre/lib/ext/
```
Then I started Firefox and browsed to [http://www.aleks.com](http://www.aleks.com) and signed in for a Free trial.

---

### Post by jackechanprime on 2010-09-11
Sounds about right. That's the basic sort of thing that i did to get mine working, and yet when i try to actually do any work in it, the answer box/interface doesn't render and/or run, as well as the buttons.

Any idea what could be causing that?

---

### Post by lykeion on 2010-09-12
Other than using OpenJDK instead of Sun Java I can't think of any reasons to the problems you are describing. 
Also since I can't reproduce them myself it's really hard to troubleshoot.

The Aleks website have a troubleshooting page. Have you tried it?

[http://www.aleks.com/support/troubleshooting](http://www.aleks.com/support/troubleshooting)

---

### Post by jackechanprime on 2010-09-13
O_o and now... it's working? Nothing changed... and now the error described above has vanished. It had persisted for over 2 weeks, and now it spontaneously vanished. What the hell. O_o Oh well, i guess i should take it as a blessing, except that now I'm even more totally stumped. I didn't change anything or even do a system update, and it's running fine now.

and also, i removed openJDK using the "completely remove" command in synaptic package manager, on the entire dependency tree ;). once i figured out it was interfering with aleks i nuked it right off the bat... but that was a week ago.

thanks
~Q

---

