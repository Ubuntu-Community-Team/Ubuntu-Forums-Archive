---
title: "Install Java on Ubuntu 10.4"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by PaulNL on 2010-04-06
Hello all,

I have installed Ubuntu 10.4 and all works perfect (for me) but.... i can't get java to work.

When i install icedtea it won't work on websites i get a gray screen. On 9.04 i had the java jre6 and did not had any problem.

Can someone tell me how to install java on ubuntu 10.4  (synaptic won't work also) 


Paul

---

### Post by mikewhatever on 2010-04-06
Well, have you installed sun-java, and if not, then why? Do you get any errors?

---

### Post by PaulNL on 2010-04-06
Yes i have installed java but is won't work.

my wife like playing games so i think i test i but on ff it won't work

Paul

---

### Post by lvleph on 2010-04-06
Use linux Mint. However, Linux Mint 9 doesn't come out until May, since it uses Lucid as its base. All of these things (java plugin, flash plugin, video codecs, etc.) come preinstalled.

---

### Post by mikewhatever on 2010-04-06
Hm..., and how about sun-java6-plugin?
It looks like Sun's java is not updated in Ubuntu repositories, and the version available for Lucid is quite old. Here is a howto for the latest version. [http://ubuntuforums.org/showthread.php?t=1445413](http://ubuntuforums.org/showthread.php?t=1445413)

---

### Post by philinux on 2010-04-06
Thread moved.

---

### Post by Brandon Williams on 2010-04-06
The version of sun-java6-plugin for lucid in the partner repo is 6.19, which is just a few days old. I recommend using that version, since you'll get automatic updates when the java version revs in the future. Instructions for installing the version from the partner repo are [here](http://ubuntuforums.org/showpost.php?p=9008918&postcount=32).

---

### Post by ratcheer on 2010-04-06
I installed the latest Java version from Sun into Lucid, last week. It is working, perfectly.

Tim

---

### Post by zika on 2010-04-06
[http://ubuntuforums.org/showpost.php?p=9082403&postcount=53](http://ubuntuforums.org/showpost.php?p=9082403&postcount=53)

---

### Post by Brandon Williams on 2010-04-07
For those who are recommending installing sun java either direct from sun or from a user ppa, it would be helpful for you to explain why you recommend that. The preferred source for sun-java6-* is the standard canonical partner repository, and that is what should be recommended unless there is a good reason to use something else. If there is a good reason, then you should spell it out, so that other users can make an informed decision about which version to use.

---

### Post by ratcheer on 2010-04-07
> **Brandon Williams said:**
> For those who are recommending installing sun java either direct from sun or from a user ppa, it would be helpful for you to explain why you recommend that. The preferred source for sun-java6-* is the standard canonical partner repository, and that is what should be recommended unless there is a good reason to use something else. If there is a good reason, then you should spell it out, so that other users can make an informed decision about which version to use.

I use the direct download from Sun because, e.g., for JRE 6 Update 19, "This release contains critical security updates to the Java runtime.  Please update now to take advantage of these enhancements." [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Here are the release notes with information on all security and bug fixes: [http://java.sun.com/javase/6/webnotes/6u19.html](http://java.sun.com/javase/6/webnotes/6u19.html)

Java is in the middle of everything, these days, so I want the latest up-to-date version available.

Tim

---

### Post by Uncle Spellbinder on 2010-04-07
Synaptic offers JRE 6 Update 19

---

### Post by Brandon Williams on 2010-04-07
> **Uncle Spellbinder said:**
> Synaptic offers JRE 6 Update 19

And this update arrived in the partner repo about 2 days after it was first released. In my experience, this has been true for any java release that has important security fixes; less true for releases that don't (although those drop in the partner repo within a reasonable time frame, too).

---

### Post by ratcheer on 2010-04-07
I guess that is just the way I am. If I want to run Sun Java, I prefer to get it from Sun. I do the same for Adobe Flash, Mozilla Firefox, and nVidia video drivers (get them from their respective companies). YMMV

Tim

---

