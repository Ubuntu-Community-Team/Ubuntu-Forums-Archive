---
title: "Upgrade to Gutsy 64 - Java wont work in firefox!"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by gtdaqua on 2007-10-25
I upgraded from 7.04 64bit Kubuntu to 7.10 64 bit Kubuntu. Flash didnt work after upgrade and somehow I made it work. But cant make java work inside firefox! 

there is no "libjavaplugin.so" in /usr/lib/firefox/plugins. It is located in /usr/lib64/mozilla/plugins and /usr/lib/mozilla/plugins (but the file is displayed in red colour when I list it in terminal.)

Looks like 32bit users have no problem!!

---

### Post by rsambuca on 2007-10-25
You can install the blackdown java plugin:

sudo apt-get install j2re1.4-mozilla-plugin

---

### Post by gtdaqua on 2007-10-25
i got java working by 
```

sudo update-alternatives --config java

```

and selecting the ia386 version. Other versions work too. But when I try to verify my java version from Java website from [this]("http://www.java.com/en/download/installed.jsp") page and click the "verify" button, firefox terminates! 

Why does this happen? I installed the blackdown java plugin too. Still the same result. Can this not be simpler? Like, 'it just works'..

---

### Post by Soarer on 2007-10-25
I couldn't get the Blackdown plugin to work reliably.

If you look at[ this thread]("http://ubuntuforums.org/showthread.php?t=580792&highlight=icedtea") it tells you how to get the IcedTea plugin, which works for me. On the page you mention it passes & doesn't crash.

I uninstalled Blackdown first, then had to do a few things from the IcedTea readme, but for some it just works after an FF restart.

---

### Post by jenhsun on 2007-10-25
> **Soarer said:**
> I couldn't get the Blackdown plugin to work reliably.

If you look at[ this thread]("http://ubuntuforums.org/showthread.php?t=580792&highlight=icedtea") it tells you how to get the IcedTea plugin, which works for me. On the page you mention it passes & doesn't crash.

I uninstalled Blackdown first, then had to do a few things from the IcedTea readme, but for some it just works after an FF restart.

Ya, I use IcedTea instead of Sun's because of the same issue.

---

### Post by gtdaqua on 2007-10-25
No. No good. 

Plugin works - but firefox quits if i try to verify my installation. It closes ALL instances of firefox. Guess this would happen if i visited a java-enabled website which tries to use my java! 

this is simply a disgrace to all of us 64-bit users. 64-bit has been around for a long time and still major players are "YET" to support us!

---

### Post by jenhsun on 2007-10-25
> **gtdaqua said:**
> No. No good. 

Plugin works - but firefox quits if i try to verify my installation. It closes ALL instances of firefox. Guess this would happen if i visited a java-enabled website which tries to use my java! 

this is simply a disgrace to all of us 64-bit users. 64-bit has been around for a long time and still major players are "YET" to support us!

Just try icedtea .....

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

---

### Post by gtdaqua on 2007-10-26
I already tried IcedTea from that post. Didnt work out.

I am planning to go 32bit Gutsy from tomorrow.

---

### Post by Soarer on 2007-10-26
If you would share the steps you took, and the results you got, with IcedTea we may be able to help you get it working. After all, it works for some of us.

---

### Post by jenhsun on 2007-10-26
> **gtdaqua said:**
> I already tried IcedTea from that post. Didnt work out.

I am planning to go 32bit Gutsy from tomorrow.

I think I might know what's gong on.
You did upgrading from 7.04 to 7.10, I think that's why.
The plugin architecture between these two version might be different.
If I were you, I will backup data and have a clean installation.
By the way, it's looked like yours is 64 bits, I suggest you try 64 bits ISO.

IcedTea works for me. I use Synaptic and done.
Never did any weired tweaking at all.
Take a look at this thread
[http://ubuntuforums.org/showthread.php?t=580792](http://ubuntuforums.org/showthread.php?t=580792)

---

### Post by galileon on 2007-11-03
I installed icetea as explained above, but this site doesn't work properly - you can't see the graph on the right, and changing the numbers and clicking plot doesn't do anything.

Any ideas?

Cheers,
galileon

edit: sorry, here's the link: [http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html](http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html)
btw, I have installed 32bits firefox with flash and java using the script mentionned in the sticky thread, and it works like a charm - so i'll use 32bits when i need this particilar site...cheers tho.

---

### Post by Soarer on 2007-11-04
Which site are you referring to? I have Iced Tea installed & could try it out to see if it works here.

---

### Post by galileon on 2007-11-04
Sorry, I didn't paste the link before apparently:
[http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html](http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html).

---

### Post by Soarer on 2007-11-04
Same for me. No graph & nothing happens when hitting 'plot'.

Mind you, I have no idea what it si supposed to do :)

---

### Post by galileon on 2007-11-04
i've included what it looks like under 32bits firefox when you change the values...

i can live without java in 64bits firefox, but thanks a lot for checking it for me,

cheers,

nawal.

---

### Post by bjtaylor01 on 2007-11-22
Just in case it is not clear to others this works fine for me:

sudo apt-get install icedtea-java7-bin icedtea-java7-jre icedtea-java7-plugin 


Then I went to the sources.list
cd /etc/apt/
sudo vim sources.list

And added:
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Then saved it. (vim command  :wq!)
sudo apt-get update
sudo apt-get upgrade

Then I reopened firefox and went to a java enabled page and it worked fine.

---

### Post by galileon on 2007-11-22
Cheers bjtaylor01!

Could you spare a moment to try that link (which I gave above) please?

[http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html](http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html)

It's meant to produce a plot like the one I attached above, when the button is pressed. It didn't work for me with 64bits firefox + icedtea... I'm using firefox32 for it for the moment.

Thanks a lot,

nawal.

---

### Post by daviddesancho on 2007-12-12
Java works smoothly in my system when I try visiting the link 
[http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html](http://webphysics.davidson.edu/physletprob/ch10_modern/radial.html)
after trying the solution given by bjtaylor01.

> **bjtaylor01 said:**
> 
Just in case it is not clear to others this works fine for me:
sudo apt-get install icedtea-java7-bin icedtea-java7-jre icedtea-java7-plugin 

Then I went to the sources.list
cd /etc/apt/
sudo vim sources.list

And added:
#iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

Then saved it. (vim command  :wq!)
sudo apt-get update
sudo apt-get upgrade

Then I reopened firefox and went to a java enabled page and it worked fine.

This may not be a final solution, but for now it is more than ok.
Thanks very much

---

