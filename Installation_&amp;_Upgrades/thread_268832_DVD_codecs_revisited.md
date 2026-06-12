---
title: "DVD codecs revisited"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by bleeping seauty on 2006-09-30
I really like ubuntu. It was a friendly install on both my P4 intel computer and P3 laptop. But, I'm really struggling with getting commercial DVDs to play. I've tried for the last 4 or so weekends. I've tried all available threads, guides, tips, etc. I've added restricted repositories, checked and rechecked needed package lists, and more.
Basically, on loading a DVD, totem opens, and then just freezes ( the computer goes on fine). Similar things happen on kaffine and vlc. The Application just crashes before opening Mplayer and ogle.
Any ideas are greatly appreciated.
Thanks

---

### Post by henriquemaia on 2006-09-30
Check vobcopy and see if you can mirror the dvd onto your disk.

---

### Post by TheFlamingBush on 2006-09-30
henriquemaia i dont really know what that means!....

i just tried what bleaping seauty did with a commercial CD, of HHGTTG, :)....and got the same problem:

*Totem could not play 'file:///media/cdrom0/VIDEO_TS/VIDEO_TS.BUP;?'*.


the playlist has a few queried actions i think with VOB, IFO, and BUP....not that i know what that means..


any suggestions?

---

### Post by henriquemaia on 2006-10-01
Vobcopy is a program to make backups of your DVDs, but it's not important. 

Totem shouldn't be playing a DVD as "file://bla_bla" but as "dvd://"

Check my screenshot. I evoked **xine**, a media plalyer, like this:

```
xine dvd://
```and xine starts playing the DVD.

---

### Post by henriquemaia on 2006-10-01
Have you installed the libdvdcss (decryption library for playing commercial DVDs)?

If no, read more here on how to do it:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by TheFlamingBush on 2006-10-01
> **henriquemaia said:**
> Have you installed the libdvdcss (decryption library for playing commercial DVDs)?

If no, read more here on how to do it:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

thanks henrique!....i downloaded the new codecs and replaced the ones i had in their, although it did say that it was a downgrade!.....so i think i had the relevant codecs in place but we shall see! ;)


well same problem im afraid.....seems that totem just doesnt support the DVD codecs in commercial cd's.....but MPlayer does! SO NO PROBLEMO...JUST HAVE TO RESET MY PREFERENCES SOMEHOW! :-k 



how do you like Xine as opposed to totem?....is it better?....is this a silly question?;)

---

### Post by henriquemaia on 2006-10-01
Totem is more newbie friendly, but xine is way powerful. Once you start understanding xine, you really get fond of it.

But Totem is more appealing in his looks.

As for Totem not reading DVDs, my Totem reads them. So there's a different issue there.

---

### Post by Lord Illidan on 2006-10-01
Perhaps you need to install totem-xine from apt-get

---

### Post by TheFlamingBush on 2006-10-01
> **Lord Illidan said:**
> Perhaps you need to install totem-xine from apt-get

Hmmm i see that i have it.....but i also see that i cant download the firefox plug in because it says :

[I]'totem-xine-firefox-plugin:
  Depends: totem-xine (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed'[/I]


shame as i was really keen to watch a stream and some movies through my browser, and i use Firefox. is there anyway to get the stream to run through my browser?....I guess i could undo the 1.4.3 Oubuntu, but isnt that devolving the system?....:-k 

Hmmmm!

---

