---
title: "Upgrade Server Safely from 5.10 to LTS"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by tim.n9puz on 2007-03-19
I have two servers (no GUI) running Ubuntu 5.10. With it's end of life here I would like to upgrade both to the LTS release. What I've found on the forums so far is targeted at desktops or at least servers running a GUI.

What is the safest course for updating servers running non-GUI versions of 5.10 to 6.06 LTS?



(Apologies if this is clearly covered somewhere. I always seem to get a lot of irrelevant results when I search the forums.)

---

### Post by zvacet on 2007-03-19
I never work with servers,but I belive commands are same.
```
sudo aptitude  dist-upgrade 
```

---

### Post by tim.n9puz on 2007-03-21
> **tim.n9puz said:**
> I have two servers (no GUI) running Ubuntu 5.10. With it's end of life here I would like to upgrade both to the LTS release. What I've found on the forums so far is targeted at desktops or at least servers running a GUI.

What is the safest course for updating servers running non-GUI versions of 5.10 to 6.06 LTS?

(Apologies if this is clearly covered somewhere. I always seem to get a lot of irrelevant results when I search the forums.)

My upgrade is complete with only a minor annoyance. My original hesitation was that the information I found in the documentation all had warnings of things related to one of the GUIs, etc. or used commands specific to a particular GUI. Neither of my two servers run any GUI so I was a bit hesitant having never done a version upgrade like this on Ubuntu or any Debian based system.

Okay, here's what I did including recovering from a minor problem. Hopefully it's of use to someone else in a situation similar to mine.

1. I did this with no one using the system except myself.

2. Edited /etc/apt/sources.list and changed all references of "breezy" to "dapper".

3. As mentioned in one GUI version of the upgrade I ran the following command:

   [FONT="Courier New"]sudo apt-get update && sudo apt-get dist-upgrade[/FONT]

*Note: the update portion worked fine but part way through the dist-upgrade step my link to the update server dropped and I got a failed message saying files were missing.*

4. I ran just the [FONT="Courier New"]sudo apt-get dist-upgrade[/FONT] command a second time and it retrieved the remaining files and then did the configuration.

5. Everything seemed to be running. I could access the files on the server via Samba, secure ftp and ssh connections all worked. 

6. Just to be safe I did a full power up restart and retested. All is well and it reports I am indeed running 6.06.1 LTS with the 2.6.15-28-386 kernel. =D>

Tim

---

### Post by enystrom on 2007-06-12
Tim,

Your post was very helpful, thank you.  It worked fine for me with a similar configuration.  Strangely, my connection also dropped right near the end, forcing me to re-run apt-get dist-upgrade, but now all is upgraded!

Thanks,

-Eric

---

