---
title: "Does Apport work on Intrepid?"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PmDematagoda on 2008-07-02
I was just wondering if Apport currently works for anyone because when I tried to get the crash logs for the GNOME System Monitor I was supposed to be using Apport, but it never showed up in the first place even though it was installed and is supposedly enabled. So my question is, does Apport work for anyone on Intrepid?

---

### Post by chrisccoulson on 2008-07-02
Are you just not getting notified of the crash, or are the crash reports not being generated at all (ie, are there any reports being generated in /var/crash)?

What is the output of:
```
cat /proc/sys/kernel/core_pattern
```

---

### Post by PmDematagoda on 2008-07-02
The output of the command:-
```
core
```

About Apport, no, it doesn't notify me of any crashes at all and nor are there any .crash files in /var/crash.

---

### Post by chrisccoulson on 2008-07-02
PmDematagoda - Thanks for the response. That explains why it is not working. Apport is not having the core dumps piped in to it.

/proc/sys/kernel/core_pattern should contain something like this (only when Apport is enabled):
```
|/usr/share/apport/apport %p %s %c
```

What is the output of the following:
```
sudo /etc/init.d/apport restart
cat /etc/default/apport
```

---

### Post by PmDematagoda on 2008-07-06
Sorry for the late reply chrisccoulson, but I was having a few issues with the Intrepid install due to hard drive problems, so I had to reinstall it. And when I ran your second command, this was turned up:-
```
# set this to 0 to disable apport, or to 1 to enable it
enabled=0

# set maximum core dump file size (default: 209715200 bytes == 200 MB)
maxsize=209715200
```
looks like I have to enable it, but it seems strange since I definitely saw it in the wiki that Apport was supposed to be enabled by default on development releases.

---

### Post by autocrosser on 2008-07-06
I just checked mine & it was disabled also----interesting.

---

### Post by Rocket2DMn on 2008-07-08
I see that PmDematagoda already found the bug report that I ran across a week or so ago but didn't do anything with - [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/244331](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/244331)
I haven't tried to fiddle with apport, so I won't touch the bug unless you want me to.  If you want to confirm the bug, I will finish the triage on it.

---

### Post by chrisccoulson on 2008-07-08
> **Rocket2DMn said:**
> I see that PmDematagoda already found the bug report that I ran across a week or so ago but didn't do anything with - [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/244331](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/244331)
I haven't tried to fiddle with apport, so I won't touch the bug unless you want me to.  If you want to confirm the bug, I will finish the triage on it.

I've confirmed but not privileged enough to finish a triage on it, so you can go ahead

---

### Post by Rocket2DMn on 2008-07-08
Done.

---

### Post by ikt on 2008-07-08
this explains everyzing.. :)

---

### Post by Gourgi on 2008-07-28
bumping this...
i just installed intrepid alpha 3
should i enable apport on not ?
is there a specific reason why apport is disabled ?
reading this [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport) i believe apport should be enabled through development releases

---

### Post by PmDematagoda on 2008-07-29
> **Gourgi said:**
> bumping this...
i just installed intrepid alpha 3
should i enable apport on not ?
is there a specific reason why apport is disabled ?
reading this [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport) i believe apport should be enabled through development releases

According to an excerpt of a message by Martin Pitt in the ubuntu-devel mailing list:-
```
>  * Apport was not triggered for the Ubiquity crash, so no crash report was
>    generated and I had to file the bug report manually, later, with
>    incomplete info.  It's disabled in /etc/default/apport, but I thought
>    Ubiquity was an exception to this.

casper still tries to enable the gconf keys, but we now use the
/etc/default/apport file for disabling (since that won't waste a lot
of resources on crashes in stable releases). I'll fix this, as soon as
"bzr get lp:~ubuntu-core-dev/casper/trunk" likes me again (it
currently crashes with a "Corrupt Knit error blabla some ancient GNU
arch revision; figuring out with the #bzr guys).

Also, I fixed the apport retracers last night, so I'll reenable apport
by default right after Alpha-3.
```

So my advice is to just leave it and let the Apport fixes come along, however if you have a serious crash, then I suppose it wouldn't be bad to manually enable Apport.

---

### Post by Rocket2DMn on 2008-07-29
Awesome, thanks for that info.

---

