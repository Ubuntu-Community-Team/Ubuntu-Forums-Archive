---
title: "DVD Play"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by jaime256 on 2008-02-13
Does anyone have an answer as to why none of the dvd's (originals) will not play in Ubuntu 7.10? I have tried all the codecs and players, but still get nothing. I was using the 32-bit and now the 64-bit version, but they are both the same. Except that none of the live 64-bit versions worked for me. But this is for another day. In any case I really don't want to have to go dig up and make all sorts of configurations. Anything in the add/remove section that may help? If not, anything else if fine. Thanks.

---

### Post by xarquid on 2008-02-13
Which DVDs are you referring to? The installation media or general DVD media (I.E. playing DVDs -- such as movies) on your P.C.?

If NOTHING is being read by your D.V.D. drive such as DVDs with files on them AND media DVDs -- we will need information such as what kind of DVD drive it is.

If your file system is installed your and DVD drive is reading data disks, just not DVD media disks (DVD movies..etc.) then it is a software/codec issue and we can go from there.

Please let us know the exact nature of the problem.

Also, what is the type of DVD drive you have? What codecs do you have installed? What media player are you attempting to utilize if you are trying to play media? What environment are you in (KDE or Gnome)? This will help us/me assist you further.

Thanks!

Craig Huffstetler / xq

---

### Post by jaime256 on 2008-02-13
It's a samsung DVD writer. I can read dvd's, I can't play dvd movies. I use Gnome and have tried to just add the codecs for gstreamer, restricted and also installed vlc, xine, mplayer, but still can't get the dvd movies to play. I can play .avi, mp3's, mpg. Again, I got all the gstreamer stuff checked and installed. I would like to just use Totem since that's what's on here. I used that on the previous version and it worked well, but not on this one.

---

### Post by xarquid on 2008-02-13
Hey again,

I believe you need libdvdcss2 which is most likely the reason for the not reading of the media.

After 6.04, they choose to take libdvdcss2 out of the universe library and only allow a non-Ubuntu repository to carry it. It is called the Medibuntu repository.

Here are some instructions about how to configure it in your /etc/apt/sources.list and then apt-get update and then finally apt-get install libdvdcss2 and then viola! You can play DVDs.

It's very easy once you get the Medibuntu repository added. And plus, once you get this baby in there -- it opens up many more possibilities for you. You'll be very happy it's your sources.list.

Instructions to add this to your sources.list:

**IF Ubuntu 7.04 "Feisty Fawn":**

> sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

**IF Ubuntu 7.10 "Gutsy Gibbon":**

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

### Important (DO NOT SKIP THIS AFTERWARDS):

Then, add the GPG Key:

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

-----------------

Sites to check out:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by blackdragon1157 on 2008-02-13
Have you followed the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")?  They've always worked for me.  I think that this is illegal in some countries however.

---

### Post by jaime256 on 2008-02-13
I did add the libdvd.. file manually a while back and still couldn't get this to work. I'll try the instructions again and see if that works this time around. If not I guess I can always plug back my 60 dollar dvd player which I hope not to do. :)

It's funny how I'm also installing Windows XP and it's also giving me the same problem. Sorry, can't help you, you don't have any codecs to play dvds, but if you "go to this site" you can purchase one. Man, the world is so ironic. I guess I might as well plug in my 60 dollar dvd player and call it a day for now. Wait, I think my old XBOX can play some dvd's too. Shame how these can play them, but none of my operating systems at the moment. :(

---

