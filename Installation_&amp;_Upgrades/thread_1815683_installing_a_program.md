---
title: "installing a program"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by vinceCOOK on 2011-07-31
Hello,

can somebody do me a massive favour and try to install this music tool below.
(maybe you have a virtual box....and the minutes spare to try it)

It is a music synthersizer for Lucid 10.04 ubuntu. "Psychosynth"

I have a very recent Lucid Ubuntu 10.04 system here but i can't get this music tool installed or running.

I have followed the simple website instructions and also the advice in the thread below. Many other people have succeeded in getting the music tool working.

If you succeed, please can you detail the exact commands you typed. Thanks.

here below is the music tool website

[http://www.psychosynth.com/index.php/Main_Page](http://www.psychosynth.com/index.php/Main_Page) (downloads section explains Lucid install and they also explain a manual approach)

"i have no idea what they mean about Keys and apt get in the manual approach......sorry...."

here is the thread of other people who succeeded with installing and running it. They said there is somekind of problem with the PPA?

[http://openubuntu.com/index.php/topic,381.0.html](http://openubuntu.com/index.php/topic,381.0.html)

i greatly appreciate your help

Vince.

---

### Post by oldos2er on 2011-07-31
> **vinceCOOK said:**
> 
[http://www.psychosynth.com/index.php/Main_Page](http://www.psychosynth.com/index.php/Main_Page) (downloads section explains Lucid install and they also explain a manual approach)

"i have no idea what they mean about Keys and apt get in the manual approach......sorry...."


You need to copy and paste the commands given under 'Easy setup' one at a time into a terminal. If the commands fail, then please post the full output here so we can see what's going on.

---

### Post by vinceCOOK on 2011-08-01
Hello,

The "easy install" commands DO fail and there are errors.

I will try to post the outputs here.

Vince.


I was just hoping somebody would try to install the music tool
themselves just to see how easily they achieved it?...
(that is why i mentioned virtualbox)

thanks

Vince.

---

### Post by fdrake on 2011-08-01
i never tried this program before so i'll give it a shoot and i'll let you know how it goes.

---

### Post by fdrake on 2011-08-02
the 2 packes don't exist anymore so you have problems when you run ./congigure. (libboost-serialization1.35-dev libboost1.35-dev)

this is the problem i get when i run configure

```

./configure
checking for boostlib >= 1.42... configure: We could not detect the boost libraries (version 1.42 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See http://randspringer.de/boost for more documentation.
checking whether the Boost::Filesystem library is available... yes
configure: error: Could not link against  !


```
i tried to compile boostlib from this website [http://www.boost.org/users/history/version_1_42_0.html](http://www.boost.org/users/history/version_1_42_0.html), but even after compiling ./configure doesn't work. any ideas.

---

### Post by vinceCOOK on 2011-08-02
i know in the notes it says BOOST is no longer needed in Lucid.

ALso, some other extensions to do with Lib(files) are no longer needed in Lucid

I greatly appreciate your efforts...


as you can see, this Reactable synth (psychosynth is a clone) in hardware is 14,000 dollars and on android and i-phone Reactable synth is just 4 dollars...

but i don't have android.......... so i found this (Psychosynth) Linux clone which is a free version.

Thanks

Vince.

---

