---
title: "Java 6 update 18 released!"
date: 2010-01-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-01-14
This release has a lot of new stuff and even 3 Ubuntu-specific bugs fixed, but also lots of performance enhancements and tweaks.
Hope Lucid will update sun-java6-jre/jdk to this version. The current version in Lucid is Java 6 update 16.

[http://java.sun.com/javase/6/webnotes/6u18.html](http://java.sun.com/javase/6/webnotes/6u18.html)

---

### Post by CoreyB. on 2010-01-14
I read somewhere that there was 350+ fixes in Update 18.

---

### Post by kevpan815 on 2010-01-14
How come it's not yet available on [http://www.java.com/?](http://www.java.com/?)

---

### Post by kahumba on 2010-01-14
java.com usually takes some time to update to the latest version. I remember once it took it about a week.

---

### Post by Ibidem on 2010-01-14
The "Install" link is broken for both the JRE and the JDK.

---

### Post by CoreyB. on 2010-01-14
> **kevpan815 said:**
> How come it's not yet available on [http://www.java.com/?](http://www.java.com/?)

[Java SE Downloads - Sun Developer Network (SDN)]("http://java.sun.com/javase/downloads/index.jsp")

---

### Post by gradinaruvasile on 2010-01-14
Lol i got the update from some ppa hours ago...

---

### Post by Ibidem on 2010-01-14
> **gradinaruvasile said:**
> Lol i got the update from some ppa hours ago...
And which ppa might that be?

---

### Post by PRC09 on 2010-01-19
Found this....


[https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)

---

### Post by xtoudi on 2010-01-19
> **PRC09 said:**
> Found this....


[https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)

it's only for Karmic...

---

### Post by Starks on 2010-01-19
> **xtoudi said:**
> it's only for Karmic...
You're going to let that stop you? It works fine with lucid.
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main

---

### Post by xtoudi on 2010-01-19
> **Starks said:**
> You're going to let that stop you? It works fine with lucid.
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/voronov84/andreyv/ubuntu](http://ppa.launchpad.net/voronov84/andreyv/ubuntu) karmic main

hmmmm do not know .... let mi think ... why not? ;-)

---

### Post by PRC09 on 2010-01-19
I am using jaunty(32 bit) and it works fine on here.Just add the sources,the key and do a system update,found the java files and installed fine.....

---

### Post by jp_coll2003 on 2010-01-21
still cant get youtube videos working by any method including this latest flash using the source on page 1. very frustrating. amd64 lucid user. 2 gig ram laptop

---

### Post by kahumba on 2010-01-21
> **jp_coll2003 said:**
> still cant get youtube videos working by any method including this latest flash using the source on page 1. very frustrating. amd64 lucid user. 2 gig ram laptop
If it is really very frustrating you then I'd suggest not testing Lucid cause there's (many) more frustrations to come (since it's in Alpha), volunteer testing should be something that you take easy in the first place.

---

### Post by sports fan Matt on 2010-01-21
Funny in the over 2 years I've used Ubuntu, I have never had an install of Sun Java.  I guess everything works just fine without it:)

---

### Post by afv on 2010-01-22
> **jp_coll2003 said:**
> still cant get youtube videos working by any method including this latest flash using the source on page 1. very frustrating. amd64 lucid user. 2 gig ram laptop

Java is not Flash. You don't need Java to watch YouTube videos. :)

---

### Post by jp_coll2003 on 2010-01-23
Sorry. I just realised that the original message was about the new Java version. I was refering to this link on page one where not only does it give a new version of java but also a new version of flash. 

As to the gentleman's view that I should keep away from alphas if I find it frustrating, isn't that what makes life interesting. Keep it real everyone. Its only open source and no one has died. for a minute, I thought I was in a Debian forum LOL

---

### Post by jp_coll2003 on 2010-01-23
[https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)

---

### Post by zika on 2010-01-23
> **jp_coll2003 said:**
> [https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)Not for Lucid...

---

### Post by portis on 2010-01-24
How about this one.
It also fixes java plugin problem with firefox-3.6

[https://launchpad.net/~portis25/+archive/test/+packages](https://launchpad.net/~portis25/+archive/test/+packages)
> **zika said:**
> Not for Lucid...

---

### Post by zika on 2010-01-24
> **portis said:**
> How about this one.
It also fixes java plugin problem with firefox-3.6

[https://launchpad.net/~portis25/+archive/test/+packages]("https://launchpad.net/%7Eportis25/+archive/test/+packages")
Is this plugin 64-bit?
I think it is not.

---

### Post by portis on 2010-01-24
Why do you think that?

file /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 
/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not stripped

> **zika said:**
> Is this plugin 64-bit?
I think it is not.

---

### Post by zika on 2010-01-24
> **portis said:**
> Why do you think that?

file /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 
/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, not strippedI was looking at dependencies... I might be wrong.
It seems that You are right! Thank You.

---

### Post by eyelessfade on 2010-02-02
What happend to sun-java?
[http://packages.ubuntu.com/search?keywords=sun-java6-jdk&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-jdk&searchon=names&suite=all&section=all)

---

### Post by CoreyB. on 2010-02-02
> **eyelessfade said:**
> What happend to sun-java?
[http://packages.ubuntu.com/search?keywords=sun-java6-jdk&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=sun-java6-jdk&searchon=names&suite=all&section=all)

Has Sun java always been missing from lucid?

---

### Post by jppr on 2010-02-02
java sun-6 is gone ;) and, icedtea6 and openjdk-6 is coming. yesterday i did a clean / fresh installation

---

### Post by eyelessfade on 2010-02-03
Don't like this at all. openjdk is not done yet. Why couldn't they wait until then? Canonical include acroread which is crap, but not sun-java?

---

### Post by Space_Balls on 2010-02-06
They might be moving Sun-java to the partner repository?

Either way, I'm not very happy about the change, since I'm having problems with webstart+OpenJDK.

---

### Post by Slug71 on 2010-02-25
Still no Java in Lucid, wtf?

---

### Post by jppr on 2010-02-25
> **Slug71 said:**
> Still no Java in Lucid, wtf?

java sun-6 is gone 3 weeks ago :popcorn:

---

### Post by afv on 2010-03-30
> **jppr said:**
> java sun-6 is gone 3 weeks ago :popcorn:

And it's back.
[https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.19-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.19-0ubuntu1)

---

### Post by CoreyB. on 2010-03-30
> **afv said:**
> And it's back.
[https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.19-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.19-0ubuntu1)

It's still in the [partner repo]("https://launchpad.net/ubuntu/+source/sun-java6"), nothing has changed.

---

