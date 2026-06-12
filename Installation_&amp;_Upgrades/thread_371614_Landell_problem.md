---
title: "Landell problem"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by sovereign_soul on 2007-02-27
Hi,

Landell is a possible alternative to GTalk for Linux. I tried to install it from the deb package available at [http://www.dcc.ufam.edu.br/~boa/edgy/](http://www.dcc.ufam.edu.br/~boa/edgy/) . After satisfying the dependencies, the program gets installed without any errors. However, whenever I try to use it, it gives an error - 

xxxxx@zion:~/landell
exec: 32: -a: not found

What does this error mean , how can it be rectified ??

I'm using Ubuntu 6.10 on a HP laptop.

---

### Post by solardeity on 2007-03-07
okay you should install mono

open synaptic and type mono in the seach area... install mono

after that i would sudo dpkg-reconfigure dash

set no

done

---

### Post by duartemolha on 2007-03-12
I still have problems with farsight-rtp conflit and cannot correct dependency errors...
would anybody be so kind to provide a howto manual for this?

Best regards

Duarte

---

### Post by raul_ on 2007-03-22
I try to install it but it complains about not having libdbus-1-2 and i have libdbus-1-3

PS: a soft link doesn't solve it

---

### Post by moshy on 2007-03-26
> **raul_ said:**
> I try to install it but it complains about not having libdbus-1-2 and i have libdbus-1-3

PS: a soft link doesn't solve it

Are you installing this from source or from the .deb?

I had this problem and fixed it by downloading the source from the sourceforge page instead of the deb. Then in the configure file, find the section towards the end where it checks for required dll's or something. Just do Find "dll". There you can see it looks in the directory /usr/lib/mono/1.0/ or something. You have to change the 1.0 to 2.0.

---

### Post by raul_ on 2007-03-26
Installing from source results in Dependency Hell =\ i'll give it a try though

---

### Post by raul_ on 2007-03-26
```
checking for TAPIOCACLIENT... configure: error: Package requirements (tapioca-client-0.3) were not met:

No package 'tapioca-client-0.3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TAPIOCACLIENT_CFLAGS
and TAPIOCACLIENT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

And i installed it from the link posted above

---

### Post by raul_ on 2007-03-26
Well, I eventually got it installed. The only problem is...no MSN protocol =\ beats me....about that exec 32 error, here is the solution

```

sudo su root <----NECESSARY

rm /bin/sh && ln -s bash /bin/sh


```

to get back to dash do the same thing and change bash to dash. After that, you'll get some error about not having an icon...you'll have to do

```

ln -s /usr/share/icons/hicolor/scalable/apps/landell.svg /usr/share/icons

```

if that doesn't work, switch the order, i'm not sure now

I NEVER had so much trouble installing an application. I had to switch from installing packages with aptitude, dowloading .debs, running ./configure to check for other dependencies...SHEESH

---

### Post by ntetreau on 2007-04-01
Hi, thanks for the help, I was able to download and login to gtalk after compiling svn.  I still don't know if voice will work but in the mean time, I get an empty window when I open the preferences.  If you had this problem, any workaround?

Nic

---

### Post by lbharti on 2007-12-17
How did you fix the problem for tapica-client? I am receiving the same error as you
Thanks for the help

---

### Post by coolarm on 2008-05-25
Hi All,

I am trying to install Landell. I want to know if you installed only telepathy-sharp, tapioca-sharp and Landell from the svn checkout or did you also install that entire list of software from tapioca-glib installation page([http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide)).

I did try installing the entire lot previously and got an error regarding ndbus when I tried to open Landell. Now I am trying to install it afresh.

I too badly need the gtalk-voip in linux.
Kindly reply

---

