---
title: "waiting for apt-get to exit"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by r_anjit on 2011-02-21
[COLOR="RoyalBlue"][/COLOR]
[FONT="Lucida Console"][/FONT]

When ever I try to use ubuntu software center to install something by downloading over the net , I get this message "waiting for apt-get to exit" which never does and I am not able to install the package. 

Secondly when I try to reload the repository of synaptic I get this message

----------------------------------------------------------------------------
"E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory"
----------------------------------------------------------------------------

Please help ;

Thanks in advance.

---

### Post by whatthefunk on 2011-02-21
Kill it.

```
top
```

This will bring up a list of all active processes.  Find apt-get and get the PID, the first number.  Press "q" to exit top.  Then do:

```
kill PID
```

Where PID is the number you got earlier.

---

### Post by mörgæs on 2011-02-21
In general I would recommend using Synaptic (and/or the command line) rather than Software Centre, which is both slow and buggy.

---

### Post by MikeConklin on 2011-09-07
I think you may have checked "install security updates without confirmation" You just have to wait for the important security updates to finish installing. When the internet connection is slow things will hang like that.

---

### Post by Hakunka-Matata on 2011-09-07
> **MikeConklin said:**
> I think you may have checked "install security updates without confirmation" You just have to wait for the important security updates to finish installing. When the internet connection is slow things will hang like that.

Check out the following thread, post# 4.  [http://ubuntuforums.org/showthread.php?t=1840420](http://ubuntuforums.org/showthread.php?t=1840420)   See HyperLink there.

> 
                                  **Re: Something wicked happened - Bad repository location?**             
                                                                     Quote:
                                                                      Originally Posted by **Toz**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11228186#post11228186")                 
                 *I think this is related to recent  hack on kernel.org. In fact, I can't access the site yet so its probably  still down. Have a look at this news item: [http://www.theinquirer.net/inquirer/...rnelorg-breach]("http://www.theinquirer.net/inquirer/news/2106955/linus-torvalds-linux-31-rc5-github-kernelorg-breach")*
                                 
**Yes, several of the servers with http ://mirror.[*location*].kernel.org are off-line since 1 September.**
                                                                                               __________________
                ](*,)
[FONT=Comic Sans MS][COLOR=Green]Enjoy the freedom of  using whatever OS works for you. Don't make changes to your computer's  OS or partitions without a backup. Try a 'Live' CD/USB if available or  use a test machine; before, installing an OS. Read the release notes.[/COLOR][/FONT]             
                                                                                              *                                              Last edited by Old_Gray_Wolf; 50 Minutes Ago at 12:43 PM.*

---

