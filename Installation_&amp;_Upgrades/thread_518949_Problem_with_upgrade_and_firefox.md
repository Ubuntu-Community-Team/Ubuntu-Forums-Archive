---
title: "Problem with upgrade and firefox"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by brownies on 2007-08-06
Hi all,

I had this problem: I did an automatic system upgrade (I'm using Feisty) the other day, and it upgraded Firefox, and other packages. Now, firefox doesn't work anymore. If I type firefox I get:

```
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found
```

Even if the package is actually installed. I've tried updating, reinstalling, doing apt-get remove then install again, etc etc. I've been using Ubuntu for a few years now, and Feisty since a time, and I don't know why I'm having this problem now.

Any ideas please?

---

### Post by nichipet on 2007-08-06
Off-hand, it sounds like firefox resides outside of your $PATH. Try:

```
sudo updatedb
locate firefox | more
```

It will give a long list, or it should at least, see if you can find the executable and then try starting FF with the full path (I think it should be /usr/bin/...).

---

### Post by 1/0 on 2007-08-06
What happens if you do:

$ /usr/lib/firefox/firefox-bin

?

---

### Post by JudasReanimated on 2007-08-06
I'm just going to shoot the moon with this, but try

sudo aptitude autoremove firefox

then 

sudo aptitude install firefox.

You may have to run that from the recovery console under root. Though I'm not familer with this problem, so my advice is from an inexperienced standpoint.

---

### Post by brownies on 2007-08-06
I couldn't find the firefox executable, I think it's not in the building anymore. On the other side, my path is:

```
 echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

And also, this is what happens with the other suggestion:

```
/usr/lib/firefox/firefox-bin
bash: /usr/lib/firefox/firefox-bin: No such file or directory
```

On aptitude, I think this should be the same that what I was doing, with remove & install in apt-get. Or am I wrong?

Thank you for your suggestions, and please tell me anything you think I could do to get my firefox back in Ubuntu, without having to reinstall.

---

### Post by nichipet on 2007-08-06
What happens when you try:

```
ls -l /usr/lib/fire*
```

That will show us everything related to /usr/lib/firefox. Sounds like the files are entirely missing.

---

### Post by brownies on 2007-08-06
This is what happens:

```
ls -l /usr/lib/fire*
total 2152
drwxr-xr-x 2 root root   4096 2007-08-06 13:52 components
drwxr-xr-x 5 root root   4096 2007-08-02 20:52 extensions
-rwxr-xr-x 1 root root   8625 2007-07-31 10:52 firefox
-rw-r--r-- 1 root root   7868 2007-07-31 10:53 libgfxpsshar.so
-rw-r--r-- 1 root root 123656 2007-07-31 10:53 libgkgfx.so
-rw-r--r-- 1 root root  82156 2007-07-31 10:53 libgtkembedmoz.so
-rw-r--r-- 1 root root  14232 2007-07-31 10:53 libgtkxtbin.so
-rw-r--r-- 1 root root  94520 2007-07-31 10:53 libjsj.so
-rw-r--r-- 1 root root 704560 2007-07-31 10:53 libmozjs.so
-rw-r--r-- 1 root root 278424 2007-07-31 10:53 libnssckbi.so
-rw-r--r-- 1 root root 103576 2007-07-31 10:53 libxpcom_compat.so
-rw-r--r-- 1 root root 699872 2007-07-31 10:53 libxpcom_core.so
-rw-r--r-- 1 root root   9988 2007-07-31 10:53 libxpcom.so
-rw-r--r-- 1 root root   7924 2007-07-31 10:53 libxpistub.so
drwxr-xr-x 2 root root   4096 2007-08-02 20:52 plugins
```

---

### Post by JudasReanimated on 2007-08-06
aptitude completely removes firefox and all unused dependencies. I prefer to use it instead of apt-get. From my understanding aptitude is better.

You could also try using Synaptic to repair the broken packages.

---

### Post by brownies on 2007-08-06
There is no aptitude autoremove, I did "aptitude autoclean firefox" and then "aptitude install firefox" but it didn't work. Maybe it's some other aptitude option? (purge, remove, clean? I'm not an aptitude user, I couldn't say)

---

### Post by nichipet on 2007-08-06
> **brownies said:**
> This is what happens:

```
ls -l /usr/lib/fire*
total 2152
drwxr-xr-x 2 root root   4096 2007-08-06 13:52 components
drwxr-xr-x 5 root root   4096 2007-08-02 20:52 extensions
-rwxr-xr-x 1 root root   8625 2007-07-31 10:52 firefox
-rw-r--r-- 1 root root   7868 2007-07-31 10:53 libgfxpsshar.so
-rw-r--r-- 1 root root 123656 2007-07-31 10:53 libgkgfx.so
-rw-r--r-- 1 root root  82156 2007-07-31 10:53 libgtkembedmoz.so
-rw-r--r-- 1 root root  14232 2007-07-31 10:53 libgtkxtbin.so
-rw-r--r-- 1 root root  94520 2007-07-31 10:53 libjsj.so
-rw-r--r-- 1 root root 704560 2007-07-31 10:53 libmozjs.so
-rw-r--r-- 1 root root 278424 2007-07-31 10:53 libnssckbi.so
-rw-r--r-- 1 root root 103576 2007-07-31 10:53 libxpcom_compat.so
-rw-r--r-- 1 root root 699872 2007-07-31 10:53 libxpcom_core.so
-rw-r--r-- 1 root root   9988 2007-07-31 10:53 libxpcom.so
-rw-r--r-- 1 root root   7924 2007-07-31 10:53 libxpistub.so
drwxr-xr-x 2 root root   4096 2007-08-02 20:52 plugins
```

I don't see firefox-bin in there. Just to try something, try:

```
/usr/lib/firefox/firefox
```

---

### Post by brownies on 2007-08-06
Sorry I didn't mention it, I had already tested that before. I get this:

```
/usr/lib/firefox/firefox
/usr/lib/firefox/firefox: line 157: /usr/lib/firefox/firefox-bin: No such file or directory
/usr/lib/firefox/firefox: line 157: exec: /usr/lib/firefox/firefox-bin: cannot execute: No such file or directory
```

Edit:

So that's my problem. I have the package, but I have not some of the files. I don't get them back even if I reinstall the package, if I remove it, etc. I suppose there has to be a solution, but which one? As for a start I don't know why this is happening. I didn't do anything strange to get to this state: I've been using Ubuntu for a few years now, and I've just run an automatic packages upgrade. What can I do?

---

### Post by brownies on 2007-08-06
I'm not sure what else to do. I've tried lots of things but I can't see: A) why this could happen, I have the packages and not the files... B) how to solve this.

Please can some package wizard help me with this?

---

### Post by brownies on 2007-08-08
I solved it. The solution was this one:

I first tried removing and installing firefox again (sudo apt-get remove firefox, sudo apt-get install firefox). After install it said the name of the deb package it had just downloaded, in this case, "firefox_2.0.0.6+1-0ubuntu1_i386.deb". I suspected this was a corrupted package, and that I needed to remove it from the cache.

So I uninstalled firefox again, then I did this:

```
sudo updatedb
locate firefox_2.0.0.6+1-0ubuntu1_i386.deb
```

This told me where the corrupted package was, so then I could do this:

```
sudo rm /var/cache/apt/archives/firefox_2.0.0.6+1-0ubuntu1_i386.deb
```

After that, I just installed firefox again, and voilá!! It just worked.

```
sudo apt-get install firefox
```

Thank you all for your suggestions, best regards!

---

### Post by JudasReanimated on 2007-08-08
whoops my bad, it's just aptitude remove, but yeah. I could've swore there was an auto remove, but I may be thinking of something else. Anyway try aptitude remove, it's from my understanding better than apt-get remove.

---

### Post by brownies on 2007-08-08
It seems I could have used: 

```
sudo apt-get remove firefox
sudo apt-get autoremove
```

But I didn't know. And anyway it's good to know how to do it by hand...

---

### Post by Odrodzona-Sarmacja on 2007-08-08
From what I gather about Ubuntu 7.04 its files on ext3 partitions constantly get corrupted due usage of faulty older version of gparted during installation process. The solution suppose to be to burn latest version of gparted livecd and check the ext3 partitions ubuntu 7.04 is on and correct whatever is to be corrected there.

However if something crashes gdm (like when using wine), then you still get Ubuntu's files and libraries  on root "/" ext3 partition cuted by Ubuntu 7.04 system. I didn't see anyone posting so far any satisfying explanation why Ubuntu 7.04 constantly corrupts files on ext3 partitions and hates so blindly and furiously file downloading and torrenting. When torrenting be smart and use preallocation, as Ubuntu 7.04 hates even more torrenting files, then the simple and strightforward file download from Ubuntu's repositories like that one, which happened in your case. It could be smart to download all files into fat32 partition, when using Ubuntu 7.04. Better safe then sorry ;)

You can try gparted lifecd in any case. Maybe it will help with your files being corrupted in future by Ubuntu 7.04 and maybe it will not.

---

### Post by brownies on 2007-08-10
Wow! Is there a problem with files getting corrupted in Ext3 in Ubuntu? I guess I could also go back to Ext2 too.

---

### Post by Odrodzona-Sarmacja on 2007-08-10
On my querry in

[http://ubuntuforums.org/showthread.php?t=520628](http://ubuntuforums.org/showthread.php?t=520628)

I've got following answer about files being corrupted by Ubuntu on ext3 partitions:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)

It is official bug, but it is not just Ubuntu os bug. It is the official and still open linux kernel bug. It is occuring only on some computers.

---

### Post by vexorian on 2007-08-12
from what I can see this problem could alsohave been caused by connection issues during the download?

I'll begin to recommend ext2 to people...

---

### Post by brownies on 2007-08-13
> **vexorian said:**
> from what I can see this problem could alsohave been caused by connection issues during the download?

Hmm... I think it could have been this too; I've had problems with my connection. But doesn't apt-get do any md5 checks, or anything like that?

---

