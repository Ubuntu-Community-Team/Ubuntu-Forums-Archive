---
title: "Openssl : post compilation warnings"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by s_raghu20 on 2008-03-17
Hi,

I have compiled my own copy of openssl, installed in my home directory.  It was initially required due to rails on ruby requirements.

Well, after the initial setup, rails works fine. Lately I have started a bit of ssh and svn usage and every time I invoke a command that uses ssl libraries (thats my guess), it dumps one or more warning lines on the screen.

 ```

raghav@hpubuntu:~$ svn
svn: /home/raghav/lib/libcrypto.so.0.9.8: no version information available (required by /usr/lib/libpq.so.5)
svn: /home/raghav/lib/libssl.so.0.9.8: no version information available (required by /usr/lib/libpq.so.5)
svn: /home/raghav/lib/libssl.so.0.9.8: no version information available (required by /usr/lib/libneon.so.26)
svn: /home/raghav/lib/libcrypto.so.0.9.8: no version information available (required by /usr/lib/libneon.so.26)
Type 'svn help' for usage.

```

As is visible, the command performs its normal function, but these warnings clutter a lot.

The other day I was taking my first steps with capistrano, and these warnings kept coming in the way time and again. Confusing me more and more...

Has anyone seen something like that ? 
Did I make a mistake in my compilation process ?
Any remedies for this ?

I tried with openssl 0.9.8g, Could there be anything with the versions ? 

pls suggest

regards
raghav..

---

### Post by s_raghu20 on 2008-03-18
Hi Guys,

Any ideas on this one... 

regards
raghav..

---

