---
title: "Sharing Apps &amp; Software between 2 versions on same HDD"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by Mel_Blakey on 2015-01-18
Hello All..
I started off with Ubuntu 14.4 x 64, then updated to 14.10 x 64.

After experiencing quite a few grey screens & freezing (*this was not limited to just Firefox*), I thought that maybe 64 Bit was taxing my Lappy and I decided to give the 32 Bit version a try.

Because I saw no improvements in 14.10 I decided to revert back to 14.4 because, at least it's LTS.

So, I now have both 14.10 & 14.4 on the same HDD in seperate partitions and most of the additional software that I have installed is on the 14.10

I use mobile broadband and my monthly allowance is getting pretty low and have I am getting close to my limit. So, I need to be frugal now.

My question is this: Can I transfer the apps & software that I have on the 14.10 to the 14.4lts??? as this the Distro that I would lke to keep*.

I managed to copy the Home directory over without a hitch using Grsync.

[COLOR=#2f4f4f]My Lappy:
HP Compaq presario CQ57
2 Gb Ram
AMD C-50 Processor × 2
Gallium 0.4 on AMD PALM[/COLOR]

* I am open to suggestions as to which one I should keep. Because whilst the Grey Screen & Freezing has reduced, it has not gone away. So, I'm quit happy to accept that it could be my machine / setup that is causing this problem!


I spent around 2 hours searching this issue yesterday. So unless someone has snook in today I don't think that the answer is already on hear.

Thanks in advance!

---

### Post by egeezer on 2015-01-18
This might give you a start:

In your 14.10 installation, use

```
                         dpkg --get-selections > ~/my-packages

  
```

And in the 14.04:

```
                         sudo dpkg --set-selections < my-packages
 sudo apt-get -y update
 sudo apt-get dselect-upgrade
  
```

There is an example at;

                        [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

my-packages will be a text file, so you can edit out anything you don't want.  I don't think there are deep enough differences between 14.04 and 14.10 that anything will be in trouble.

---

### Post by ian-weisser on 2015-01-18
> **Mel_Blakey said:**
> Can I transfer the apps & software that I have on the 14.10 to the 14.4lts??? as this the Distro that I would lke to keep*.

Yes and No.

Yes: Scripts and interpreted applications (like applications that are merely Python and Shell and Perl)...if the dependencies permit it.

No: Compiled binaries.

---

### Post by Mel_Blakey on 2015-01-18
Thanks for replying.

Its getting a late now in UK and I'm tired...So, I'll give that a try tomorrow and report back here with the results.

Once again Thanks!

---

### Post by Mel_Blakey on 2015-01-23
> **Mel_Blakey said:**
> I'll give that a try tomorrow and report back here with the results
Well I'm sorry that I didn't come back on. But, the following morning my trusty lappy went pop. It died and no matter what I did could not bring it back to life. So, I bought an identical (& just as broken) machine off Ebay and yesterday managed to build a good machine out of both of them ;)

Anyway, it solved my little issues as I chucked both 2Gb memory cards in it and is running like a dream now on Ubuntu 14.04 LTS x 64.
I had a slight issue at install which I'll post about elswhere.

The main reason that I've come back to this post through, is to thank you guys for your very quick replys and offers of help & advice.

So **THANKS!**

---

