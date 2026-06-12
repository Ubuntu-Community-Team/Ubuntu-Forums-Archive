---
title: "Eclipse does not start"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by Marshlurker on 2006-12-27
Hi all,

unfortunately eclipse does not start. Typing "eclipse" in the Konsole shows:
```
$user@$host:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...found
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.

```

I already tried reinstalling java (via automatix) and eclipse (via adept).
Any ideas?

---

### Post by raul_ on 2006-12-27
Try installing java-gcj and pthreads packages. They should be available in the repos

---

### Post by Marshlurker on 2006-12-27
I installed these packages:
java-gcj-compat
java-gcj-compat-dev
kaffe-pthreads

Still, eclipse won't start, although the jvm is obviously found:
```
$user@$host:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.

```

---

### Post by Marshlurker on 2006-12-27
Ok, i solved the problem, but i think the solution is a bit dirty. ;-)

I needed to change the following lines in **/usr/bin/eclipse**:
```
elif [ -x /usr/bin/kdialog ]; then
    DIALOG=/usr/bin/kdialog
```
to
```
#elif [ -x /usr/bin/kdialog ]; then
#    DIALOG=/usr/bin/kdialog
```

I found the solution here:
[http://kanotix.com/PNphpBB2-viewtopic-t-23024.html]("http://kanotix.com/PNphpBB2-viewtopic-t-23024.html")
Thx Jeti!

---

