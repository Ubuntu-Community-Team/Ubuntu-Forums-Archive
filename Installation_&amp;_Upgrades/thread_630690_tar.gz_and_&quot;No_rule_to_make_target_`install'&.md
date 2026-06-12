---
title: "tar.gz and &quot;No rule to make target `install'&quot;"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by jennica on 2007-12-03
I am relatively new to Linux, I'm using Kubuntu and I am having a hard time figuring out how to install something. I'm trying to install Krusader [[http://krusader.sourceforge.net/]](http://krusader.sourceforge.net/]) and it says I can't "make" or anything. Is there an easier way to installing tar.gz files?

It also says 

> checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

And I've looked around and I can't find anything to help.

---

### Post by Pumalite on 2007-12-03
sudo apt-get install build-essential
Then try again.

---

### Post by jennica on 2007-12-03
it says it is already the newest version.

---

### Post by Pumalite on 2007-12-03
Post your commands to install this file.

---

### Post by jennica on 2007-12-03
I tried ./configure
and tar -zxvg [file]

I just looked up ways to try and install a tar.gz

I can't figure it out

---

### Post by Pumalite on 2007-12-03
Normally one downloads to the Desktop. Then in Terminal:
cd ~/Desktop
tar xvzf <filename>.tar.gz
cd <filename>

---

### Post by aysiu on 2007-12-03
> **jennica said:**
> I am relatively new to Linux, I'm using Kubuntu and I am having a hard time figuring out how to install something. I'm trying to install Krusader [[http://krusader.sourceforge.net/]](http://krusader.sourceforge.net/]) and it says I can't "make" or anything. Is there an easier way to installing tar.gz files?

It also says 



And I've looked around and I can't find anything to help.
**Step 1**
Delete the .tar.gz

**Step 2**
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 3**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install krusader
```

**Step 4**
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jennica on 2007-12-03
can you download anything that way?

thank you very very much.

---

### Post by aysiu on 2007-12-03
> **jennica said:**
> can you download anything that way?

thank you very very much.
Can you install any application that way? No, but you can for most applications. They have to be available in the software repositories.

Check out Step 4 for more details.

---

