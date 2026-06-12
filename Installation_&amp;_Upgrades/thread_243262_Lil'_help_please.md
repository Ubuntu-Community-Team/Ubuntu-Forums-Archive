---
title: "Lil' help please"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by omega_c on 2006-08-24
Ok, i posted [this]("http://ubuntuforums.org/showthread.php?t=241633") few days ago, because neither totem nor rythmbox would play mp3s, .avi files, .ogg files, nothing.

A couple of people post replies, only two of which i kinda understood, (i still dont get what the command line or anything is... confusing.) telling me to run this and this and this. I ran one or two, nothing happend... still wouldn't play anything.

My computer froze up twice during the 15 minutes that it took me to do one of the things... i got really fed up, and yeah.

Point is, i then went into synaptic package manager and downloaded a program called 'vlc media player'

It plays music and videos. :grin: 

Ok, I'm happy. Except for one thing.

I can't play dvds. My computer wont read (or i cant find) the dvd. It shows the drive, but says that there is nothing in it. ](*,) 

So here's my question: How can i get ubuntu to play my dvds? (and, if someone has a simple [ie: step by step, key by key, instructions] way to update totem and rythmbox so that they'll play music and videos, i'd be very happy.)

I know i'm asking a lot, but... Everyone here knows more about ubuntu than i do...


Thanks!

---

### Post by ciscosurfer on 2006-08-24
Check this link then go to RestrictedFormats
[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

---

### Post by adds2one on 2006-08-24
OK, I will try and take this very slowly.

When you first install Ubuntu there are some things that do not come pre-installed, such as multimedia codecs and support for copyprotected DVDs.

To get these you need install some things. Don't worry, this is easy. :) 

Some nice people have created a helpful thing called Automatix. This is a utility to help you get all the basic things that you will need that don't come with Ubuntu by default installed quickly and easily.

First you will need to open a terminal (don't be afraid!) by Applications->Accessories->Terminal and then follow these instructions:

Edit your sources.list:

```
sudo gedit /etc/apt/sources.list
```

Add the following to your sources.list:

```
deb http://www.getautomatix.com/apt dapper main
```

Next you must get our GPG key in order to authenticate our repository:

```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

```

To finish off:

```

sudo apt-get update
sudo apt-get install automatix
```

Now go Applications->System Tools->Automatix

click ok past the first three screens and then you wil want to choose what to install. For you make sure you tick all the multimedia codecs and the support for copyprotected DVDs. Other things that are handy are the plugins for Firefox like Flash for example. Xine and totem and mplayer are other things you may want to check off.

Then click OK and it will all install. At the end you will be asked if you want to restore your sources.list file. Just say OK.

Now you should have no problem playing mp3's in anything and watching your DVDs.

---

### Post by omega_c on 2006-08-24
ok, thanks

I'm not on my ubuntu computer yet, but when i am, i'll try it!

---

### Post by ciscosurfer on 2006-08-24
You should still read up on restricted formats so you understand exactly why they are not included all releases of Ubuntu 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by adds2one on 2006-08-24
> **ciscosurfer said:**
> You should still read up on restricted formats so you understand exactly why they are not included all releases of Ubuntu 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good advice.

---

### Post by omega_c on 2006-08-25
Ok, thanks.

I actually read that the first time, and now I understand why...

I was curious before as to why Ubuntu wouldn't... Thanks!

---

