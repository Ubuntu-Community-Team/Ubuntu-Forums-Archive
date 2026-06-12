---
title: "Packet manager error"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by slwx on 2010-11-19
Hi, 
I've been getting this error, and I don't know how to handle it. I've just been using ubuntu for a few months and I'm not really an expert.
When I boot, I get a error sign in my panel:

An error occurred, please run package manager to see what is wrong.

Error message: 'Error: opening the cache(E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf),

E:Error occurred while processing python-openid(NewVersion1)

E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages

E:The package lists or status file could not be parsed or opened.)' This usually means that your installed packages have unmet dependencies.

any ideas?
thanks, 
Mathi

---

### Post by sikander3786 on 2010-11-19
Hi.

Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by slwx on 2010-11-20
Hi, 
thanks for reply.

mathias@mathias:~$ cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    

    #voor aircrack:
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe main restricted multiverse #Added by software-properties

I have indeed been messing arround with this file, to install aircrack package. What can i reset it to?

Thanks, 
Mathi

---

### Post by cogier on 2010-11-20
I am not an expert but you seem to be trying to get software for different versions of Ubuntu.

It looks as if you are running Dapper (6.06) which is a little old. Have you considered upgrading? You may be trying to load software "#voor aircrack:" that your system can't handle. The bottom lines of your output refer to Ubuntu 9.04.

---

### Post by slwx on 2010-11-20
That version of aircrack didnt work, It was the wrong one. I followed instructions to install it, which told me to switch /etc/apt/sources.list files. 
But I don't know what to reset the file to..

I've also been getting more errors now, cant install any software with software centre :s

---

### Post by sikander3786 on 2010-11-20
Your sources.list appears to be totally messed up.

You didn't mention which version of Ubuntu are you using?

Whichever it is, select it and generate a new sources.list here.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Then backup your existing sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
```

Delete it.

```
sudo rm /etc/apt/sources.list
```

Create a new one, paste your sources into that, save and close.

```
gksudo /etc/apt/sources.list
```

Now run apt-get update and see if any errors are there.

```
sudo apt-get update
```

Good Luck!

---

### Post by slwx on 2010-11-20
Worked fine, 
Thanks for replies!

---

### Post by sikander3786 on 2010-11-20
> **slwx said:**
> Worked fine, 
Thanks for replies!
Nice to hear that :-)

You can mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page.

Happy Ubuntu-ing!

---

