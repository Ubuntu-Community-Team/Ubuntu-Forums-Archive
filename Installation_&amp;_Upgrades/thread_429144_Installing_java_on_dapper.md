---
title: "Installing java on dapper"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by j4ckofalltr4des on 2007-04-30
I have Java downloaded and installed, but I cant create a symbolic link to the mozilla-firefox plugin directory. Simply because there isnt a plugin folder in the mozilla-firefox folder. Maybe Im looking in the wrong place (the exact directory path im using is /etc/mozilla-firefox/) or maybe java is full of crap and its directions are wrong. any help would be aprritiated.

---

### Post by simonn on 2007-04-30
How did you install java?

What does the following return:

```

$ ls /etc/alternatives/*firefox*

```

---

### Post by zvacet on 2007-05-01
Here you have instructions how to install plugin

[http://java.com/en/download/help/5000010500.xml]("http://java.com/en/download/help/5000010500.xml")

---

### Post by j4ckofalltr4des on 2007-05-01
Yeah those were the directions I was using. and for the most part were correct till I discovered my mozilla firefox folder doesnt have a plugins sub directory. 

as for the code and was it returned: 

/etc/alternatives/firefox-homepage
/etc/alternatives/mozilla-firefox_nphelix.so
/etc/alternatives/mozilla-firefox_nphelix.xpt 

/etc/alternatives/firefox-homepage-locales:

then a list of index files.

---

### Post by j4ckofalltr4des on 2007-05-01
disregard. I found it. Apritiate the help.

---

### Post by j4ckofalltr4des on 2007-05-01
New problem. Im in directory /usr/lib/mozilla/pluginsand Im trying to make the symbolic link to the java plugin like so:

In -s /home/ryan/jre1.6.0_01/plugin/i386/ns7/libjavplugin_oji.so (also done with ns7-gcc29)

and it come up with: Bash: In: command not found

Any ideas?

---

### Post by simonn on 2007-05-02
It's ln, short for link, not In.

---

### Post by jamesstansell on 2007-05-02
Simonn had the answer for your In: command not found question.  Eventually you can probably get it working with those instructions.

But if you use the deb method it will take care of the linking and more for you.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

That link doesn't mention sun-java6 for dapper but I believe it is available in the dapper-backports multiverse repository.

---

