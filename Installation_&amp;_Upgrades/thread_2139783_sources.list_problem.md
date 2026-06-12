---
title: "sources.list problem"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2013-04-27
Hi again I have a problem with sources.list It came as below. I blocked out the lines to stop the problem below

this is line 63:

##mkvtoolnix
##deb [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) raring (this is line 63)
##deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) raring

if I take away the ## I get a problem:

pedro@pedro-bedro:~$ apt-get update
E: Malformed line 63 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

What should line 63 be???

---

### Post by sammiev on 2013-04-27
# mkvtoolnix
# deb [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) raring (this is line 63)
# deb-src [http://www.bunkus.org/ubuntu/precise/](http://www.bunkus.org/ubuntu/precise/) raring

Likely should look like this.

---

### Post by snowpine on 2013-04-27
As I mentioned[ in response to your other thread]("http://www.linuxquestions.org/questions/ubuntu-63/sources-list-4175459775/"), you should follow the directions in the link below (assuming you trust this 3rd-party software source):

[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html)

Specifically, for your 13.04 install, the recommended sources.list lines (according to that link) are:

```
deb http://www.bunkus.org/ubuntu/raring/ ./
deb-src http://www.bunkus.org/ubuntu/raring/ ./ 
```

**But** that is not the complete instructions; read the link. :)

---

### Post by Pedroski55 on 2013-04-27
I tried that, but it didn't work

---

### Post by snowpine on 2013-04-27
> **Pedroski55 said:**
> I tried that, but it didn't work

You are a fast reader, read and tried the complete instructions in only 1 minute! ;) Post the exact error messages so we can help you troubleshoot **or** better yet contact the developer of this unsupported 3rd-party software through his/her website. :)

---

### Post by papibe on 2013-04-27
Hi Pedroski55.

Does [this]("http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu") help?

Regards.

---

