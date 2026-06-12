---
title: "Something wicked happened - Bad repository location?"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2011-09-07
I've been getting errors like the following:

```
    Ign [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) natty-security InRelease
    Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) natty Release.gpg
      Something wicked happened resolving 'mirrors.us.kernel.org:http' (-5 - No address associated with hostname)
    Err [http://mirrors.us.kernel.org](http://mirrors.us.kernel.org) natty-updates Release.gpg
      Something wicked happened resolving 'mirrors.us.kernel.org:http' (-5 - No address associated with hostname)

```

Also, when I try to use the Ubuntu Software Center to change
Software Sources, it times out.

Is there something I should do or check into?

So, I edited /etc/apt/sources.list by hand and substituted the
following repository location:

```
    [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/)
```

Now all seems well.  However, that's probably not the correct
solution.  Is this a problem on my machine?  Or, is this something
that Ubuntu needs to fix?

- Dave

---

### Post by Toz on 2011-09-07
I think this is related to recent hack on kernel.org. In fact, I can't access the site yet so its probably still down. Have a look at this news item: [http://www.theinquirer.net/inquirer/news/2106955/linus-torvalds-linux-31-rc5-github-kernelorg-breach]("http://www.theinquirer.net/inquirer/news/2106955/linus-torvalds-linux-31-rc5-github-kernelorg-breach")

---

### Post by Old_Grey_Wolf on 2011-09-07
> **dkuhlman said:**
> 
Also, when I try to use the Ubuntu Software Center to change
Software Sources, it times out.

Is there something I should do or check into?

So, I edited /etc/apt/sources.list by hand and substituted the
following repository location:

```
    [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/)
```

Now all seems well.  However, that's probably not the correct
solution.  Is this a problem on my machine?  Or, is this something
that Ubuntu needs to fix?

That was an appropriate solution. I would have recommended something similar. 

Does the Software Center still time out?

---

### Post by Old_Grey_Wolf on 2011-09-07
> **Toz said:**
> I think this is related to recent hack on kernel.org. In fact, I can't access the site yet so its probably still down. Have a look at this news item: [http://www.theinquirer.net/inquirer/news/2106955/linus-torvalds-linux-31-rc5-github-kernelorg-breach]("http://www.theinquirer.net/inquirer/news/2106955/linus-torvalds-linux-31-rc5-github-kernelorg-breach")

Yes, several of the servers with http ://mirror.[*location*].kernel.org are off-line since 1 September.

---

