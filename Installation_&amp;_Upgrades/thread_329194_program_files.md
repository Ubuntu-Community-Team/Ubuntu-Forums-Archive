---
title: "program files"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by rbhigday on 2007-01-01
What directory is the default for when you install programs?

---

### Post by taurus on 2007-01-01
Usually the /bin or the /usr/bin...

---

### Post by rbhigday on 2007-01-01
> **taurus said:**
> Usually the /bin or the /usr/bin...

thanks will try that when I get home trying to see if i can make amsn autoload and could not find the files, still learning, slowly but surely :)

---

### Post by taurus on 2007-01-01
Did you install amsn from the repos or did you install it by hand?

---

### Post by rbhigday on 2007-01-02
> **taurus said:**
> Did you install amsn from the repos or did you install it by hand?

from the repo I have not figured out how to install from my pc yet as I have a new amsn on my hd but not read how to install from hd yet.

---

### Post by taurus on 2007-01-02
So you've downloaded amsn and you want to know how to install it!  What format it is in anyway?
What's the output of this command from a terminal?

```
ls -la ~/Desktop
(assuming you've downloaded it to your ~/Desktop directory...)
```

---

### Post by rbhigday on 2007-01-02
> **taurus said:**
> So you've downloaded amsn and you want to know how to install it!  What format it is in anyway?
What's the output of this command from a terminal?

```
ls -la ~/Desktop
(assuming you've downloaded it to your ~/Desktop directory...)
```

rbhigday@richard-laptop:~$ ls -la ~/Desktop
total 1992
drwxr-xr-x  2 rbhigday rbhigday    4096 2006-12-31 23:29 .
drwxr-xr-x 32 rbhigday rbhigday    4096 2007-01-02 17:10 ..
-rw-r--r--  1 rbhigday rbhigday 2025614 2006-12-31 23:28 amsn-0.96-2.tcl84.x86.package

how do I install the amsn?

---

### Post by taurus on 2007-01-02
Where did you download that package anyway?

Try something like these to see if it works or not!

```
cd ~/Desktop
chmod 755 amsn-0.96-2.tcl84.x86.package
./amsn-0.96-2.tcl84.x86.package
```

---

### Post by rbhigday on 2007-01-02
from the amsn site, thanks will give it a shot and post the results :)

Here is the site[http://www.amsn-project.net/]("http://www.amsn-project.net/")

---

### Post by rbhigday on 2007-01-02
> **taurus said:**
> Where did you download that package anyway?

Try something like these to see if it works or not!

```
cd ~/Desktop
chmod 755 amsn-0.96-2.tcl84.x86.package
./amsn-0.96-2.tcl84.x86.package
```

Thanks worked like a charm

Will this work for most programs I dl for unix by just changing the name?

---

### Post by taurus on 2007-01-02
Not necessary...  It depends on the file format because most of the time, you need to build it from source if you want the latest version of an app.  

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

