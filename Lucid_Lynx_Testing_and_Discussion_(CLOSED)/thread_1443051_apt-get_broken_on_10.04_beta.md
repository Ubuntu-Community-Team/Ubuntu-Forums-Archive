---
title: "apt-get broken on 10.04 beta ?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emshains on 2010-03-30
Whenever I try to run apt, I get this:
```
:~$ sudo apt-get install flac lame
Reading package lists... Done
Segmentation fault (core dumped)
```

So does this mean I have a hardware or a software problem ? Could it be a dead hard drive ?

---

### Post by Bachstelze on 2010-03-30
If apt-get segfaults, it's not a good sign... Does this happen whenever you use it, or just with those packages?

---

### Post by emshains on 2010-03-30
Whenever I use it. The strange thing is, aptitude works. So I can only use a deb tool which hasn't got super cow powers :(

---

### Post by carlosgs91 on 2010-03-30
,

---

### Post by km0r3 on 2010-03-30
[Wikipedia:]("http://en.wikipedia.org/wiki/Core_dump")
> In [computing]("http://en.wikipedia.org/wiki/Computing"), a **core dump** consists of the recorded state of the working [memory]("http://en.wikipedia.org/wiki/Computer_storage") of a [computer program]("http://en.wikipedia.org/wiki/Computer_program") at a specific time, generally when the program has terminated abnormally ([crashed]("http://en.wikipedia.org/wiki/Crash_%28computing%29")).[[1]]("http://en.wikipedia.org/wiki/Core_dump#cite_note-0")

I think you should report that to Launchpad.
[]("http://en.wikipedia.org/wiki/Core_dump#cite_note-0")

---

### Post by overdrank on 2010-03-30
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by solitaire on 2010-03-31
I'm getting a similar error... 
but apt-get / synaptic seems to run as normal.
It looks like (in my case at least) the program runs but does not exit cleanly.

---

### Post by emshains on 2010-03-31
It's wierd. Last night it wasn't working at all, this morning it asked me to run dpkg --configure -a or something like that, didn't give me any seg faults at all. Since I've been having problems with the package"alsa-driver-linuxant", I, instead of running the dpkg, I ran aptitude and removed the faulty package, haven't rebooted yet, but I will in a minute. But apt-get works.

Anyway, going to bare this month until the final release and then make a fresh install. 

As for the reports, I've been reporting like crazy for the last week, but I don't think it will make much of a difference.

---

### Post by leorolla on 2010-03-31
Suggestion: try
```
sudo aptitude update && sudo aptitude reinstall apt

```

If it crashes again, run
```
apport-cli

```and it will find any crash reports to upload.

Otherwise
```
ubuntu-bug apt

```to file this bug.

---

### Post by emshains on 2010-03-31
Thanks, but apt-whatever is working now. But I sure as hell will file a bug report.

---

### Post by dino99 on 2010-03-31
thats makes me thinking about corrupt cache, so clean it first.

---

### Post by leorolla on 2010-03-31
If it really crashed apport-cli might found the crash reports automatically.

---

