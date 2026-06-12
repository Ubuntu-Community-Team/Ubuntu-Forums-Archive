---
title: "How do you rsync?"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by zephyrus17 on 2008-08-02
How does this thing work? It's very confusing.

I used the terminal and typed: ```
rsync -zhhP rsync://cdimage.ubuntu.com/hardy/daily-live/current/hardy-desktop-i386.iso
```

And all I got was this: ```
@ERROR: Unknown module 'hardy'
rsync error: error starting client-server protocol (code 5) at main.c(1383) [receiver=2.6.9]

```

Help?

---

### Post by zephyrus17 on 2008-08-04
Bumper!

---

### Post by p_quarles on 2008-08-04
Given the error you got, it looks like a problem with the server. 

It sounds like you are following instructions you got from somewhere. Do you mind posting those?

---

### Post by zephyrus17 on 2008-08-04
[RsyncCdImage]("https://help.ubuntu.com/community/RsyncCdImage")

That's what I followed. However, the path it provides seems non-existant, so I tried using the path I got from following the link higher in the webpage and into the Ubuntu release that I wanted. Obviously, that didn't help.

---

### Post by p_quarles on 2008-08-04
I think that was meant to be a pre-release daily snapshot of Hardy Heron. Now that Ubuntu 8.04 is out, the snapshot server would have been taken down or used for something else.

---

### Post by zephyrus17 on 2008-08-04
So what method or server do I use to update my iso? it's really tedious to do all the update downloads each time I install the OS.

---

### Post by p_quarles on 2008-08-04
You'd have to build your own.

Ubuntu releases updated CD images every few months, though, so that helps with some of the update burden.

---

### Post by zephyrus17 on 2008-08-05
But I'd rather not download the whole ISO again. at that website, there's a "." (dot) at the end of the server. Is that supposed to be there?

---

### Post by utUtu on 2008-08-05
> **zephyrus17 said:**
> How does this thing work? It's very confusing.

I used the terminal and typed: ```
rsync -zhhP rsync://cdimage.ubuntu.com/[COLOR="Red"]hardy[/COLOR]/daily-live/current/hardy-desktop-i386.iso
```

And all I got was this: ```
@ERROR: Unknown module 'hardy'
rsync error: error starting client-server protocol (code 5) at main.c(1383) [receiver=2.6.9]

```

Help?

you should cut and paste the command from the wiki so to avoid typos
Compare your command with this. Notice the ones I marked in red. Don't forget the '.' at the end and it assumes your local image is in the directory where you issued the command.
```

rsync -zhhP rsync://cdimage.ubuntu.com/[COLOR="Red"]cdimage[/COLOR]/daily-live/current/hardy-desktop-i386.iso .


```

---

### Post by zephyrus17 on 2008-08-11
I tried it with intrepid with ```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/intrepid-desktop-i386.iso intrepid-desktop-i386.iso
``` and it works.

But with ```
rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/hardy-desktop-i386.iso hardy-desktop-i386.iso
``` it just gives a > rsync: link_stat "/daily-live/current/hardy-desktop-i386.iso" (in cdimage) failed: No such file or directory (2)

Which means the hardy one has been taken down. Where can I get a server for the hardy one?

---

### Post by zephyrus17 on 2008-08-18
Anyone? Please?

---

### Post by level323 on 2008-09-02
The original request is a valid one and, if there was a way to build updated ISO's from the previous version, that would save everybody a lot of bandwidth.

The ubuntu [mirrors list]("https://launchpad.net/ubuntu/+archivemirrors") shows a lot of mirrors supporting rsync, but it seems that you'll need to tweak rsync's command line options to get it to work as desired. Try adding the options:

-I
-L
--keep-dirlinks
--copy-unsafe-links

For example, the following command worked for me:

```

rsync -avhhPIL --keep-dirlinks --copy-unsafe-links --progress tw.releases.ubuntu.com::ubuntu-releases/8.04.1/ubuntu-8.04.1-alternate-i386.iso .

```

But this story doesn't have as happy an ending as you might think. I don't think you'll find rsync's sync algorithm to be much of a bandwidth saver in this case, because I'm not sure how cleverly rsync handles chunks of data that (within a file) that are identical on both the sides, but are at different offsets on each side (as can commonly be the case when comparing a newer disk image with an older disk image). I know the rdiff/librsync tool deals with this issue very efficiently, but as librsync is the future successor to rsync, this may be one of rsync's limitations that librsync is designed to overcome. 

If that is the case, then using rsync to efficiently build a newer disk image from an older one might not be all that efficient after all. Someone with more knowledge about the inner workings of rsync can chime in any time here, but I'm suspicious that rsync's sync algorithm only skips over parts from the sending side that already exist on the receiving side AND are at the correct offset (position) in the file.

Cheers

---

