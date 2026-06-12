---
title: "Barebone installation help"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by nami on 2008-05-31
Hi

I have just installed a barebone installation using the 10Mb Ubuntu mini cd.  I have also installed enlightenment and can load it by typing startx.  How do I install entrance as the login manager?

---

### Post by geo909 on 2008-05-31
Well I don't realy know but I guess that something like
```
sudo apt-get install entrance
``` would work..
Did you try it?

---

### Post by nami on 2008-05-31
> **geo909 said:**
> Well I don't realy know but I guess that something like
```
sudo apt-get install entrance
``` would work..
Did you try it?

Yes that was one of the first things I tried.   It said that it "can't find package entrance".

---

### Post by geo909 on 2008-05-31
OK, sorry if I mention things obvious to you:

Maybe the package is on a repository that you don't have enabled. Did you check that? Can you also check that the package is named exactly "entrance"?

EDIT. After some googling I found this after a mini how to
about installing enlightenment packages in ubuntu:

> To set entrance (E17's login manager) as the default we execute these commands:
```
$ cd /etc/X11
$ cp default-display-manager default-display-manager.bak
$ echo `which entranced` > default-display-manager
$ update-rc.d entrance start 99 2 3 4 5 . stop 01 0 1 6 .
```

If you have problems starting entrance (like I did) try this command:
```

$ echo /usr/local/lib >> /etc/ld.so.conf
$ ldconfig
```

Voila!

BUT! This is a very old guide. It talks about ubuntu 5.10! So if you will use it, do that 100% on your own risk, I just copy-pasted it and hdo not have the slightest idea what it does.

The guide was in Greek, so I don't give the link

---

### Post by geo909 on 2008-05-31
There's this one, too:


[http://gopalarathnam.com/weblog/2006/11/20/getting-entrance-e17-display-manager-to-work-on-ubuntu.html]("http://gopalarathnam.com/weblog/2006/11/20/getting-entrance-e17-display-manager-to-work-on-ubuntu.html")

---

### Post by nami on 2008-05-31
I think that is the main problem.  I can't figure out which repository to add to my sources.list as I have everything currently enabled, which can only mean that I need to add a repository which is not already there.

Any ideas?

---

### Post by geo909 on 2008-05-31
Take a look at [this]("http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/09/E17-repository-for-Ubuntu-Gutsy-Gibbon")

Have you installed enlightenment by compiling the source?
I understand that enlightenment and entrance should be on the same
repositories..

EDIT: There is a guy around here who seems to know many things about enlightenment stuff and ubuntu.
His name is "Rui Pais", maybe you should send him a message to tell him about your thread.

---

### Post by nami on 2008-05-31
That is strange because without making any changes to the sources.list I was able to install enlightenment like so:

sudo apt-get install enlightenment

But it would not let me do:

sudo apt-get install entrance

I will check out the link

---

### Post by nami on 2008-05-31
Thanks for the info, finally got it working.  here are the basic steps if anyone is interested.  But remember this is a barebone installation so most of the programs you're used to are missing which you are free to install later

get the barebone 10mb cd

install the barebone system by typing in cli

after the installation in finished, do the following

sudo apt-get update && sudo apt-get upgrade

wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)

sudo apt-key add repo_key.asc

deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) hardy e17

sudo apt-get update

sudo apt-get install xorg xterm entrance e17

sudo /etc/init.d/entrance start

only problem i have having is that i don't have any resolution options, i am stuck at 800x600

---

### Post by geo909 on 2008-05-31
So, what was it, the repo, the key?
(Asking from curiosity)

---

### Post by nami on 2008-05-31
Both the repo and key were missing.

---

