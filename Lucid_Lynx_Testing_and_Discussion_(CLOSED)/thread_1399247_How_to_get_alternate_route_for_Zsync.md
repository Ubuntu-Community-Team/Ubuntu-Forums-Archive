---
title: "How to get alternate route for Zsync"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-05
I'm only able to download at **25k/bs**. 1/4 speed of what is normal.

How do I tell zsync to take an alternate route?

I see the rsync [here]("https://launchpad.net/ubuntu/+cdmirrors"), but no zsync anywhere.

I know how for repositories, but don't know for zsync.

Its somewhere along this stream, apparently:
```
zsync http://cdimage.ubuntu.com/daily/current/lucid-alternate-i386.iso.zsync
```
 I'm guessing its before cdimage, like us.cdimage or jp.cdimage.

Anyone know?

Thanks.

---

### Post by xebian on 2010-02-05
> **VMC said:**
> I'm only able to download at **25k/bs**. 1/4 speed of what is normal.

How do I tell zsync to take an alternate route?

I see the rsync [here]("https://launchpad.net/ubuntu/+cdmirrors"), but no zsync anywhere.

I know how for repositories, but don't know for zsync.

Its somewhere along this stream, apparently:
```
zsync http://cdimage.ubuntu.com/daily/current/lucid-alternate-i386.iso.zsync
```
 I'm guessing its before cdimage, like us.cdimage or jp.cdimage.

Anyone know?

Thanks.

Go to the mirrorlist and look for *.zync files.  copy the URL and use that instead to zsync <url>

---

### Post by VMC on 2010-02-05
> **xebian said:**
> Go to the mirrorlist and look for *.zync files.  copy the URL and use that instead to zsync <url>
That's what I said. There **was not** any zsync. Only rsync links.

---

### Post by xebian on 2010-02-05
> **VMC said:**
> That's what I said. There **was not** any zsync. Only rsync links.

You are confusing yourself.  Aside from the similar names they are entirely different.  rsync is like http or ftp protocols.  The rsync link is to a server that is rsync enabled.

zsync files are just little files that the zsync client in your box uses to compare/figure out what you are missing, and then gets and reassemble to an iso locally.

These *zsync files are in the http/ftp links.

But it looks like you are looking for lucid files which are not mirrored IIRC.

---

### Post by VMC on 2010-02-05
> **xebian said:**
> You are confusing yourself.  Aside from the similar names they are entirely different.  rsync is like http or ftp protocols.  The rsync link is to a server that is rsync enabled.

zsync files are just little files that the zsync client in your box uses to compare/figure out what you are missing, and then gets and reassemble to an iso locally.

These *zsync files are in the http/ftp links.

But it looks like you are looking for lucid files which are not mirrored IIRC.

We are in the Lucid forum. If you can find another zsync let me know.

EDIT: I think I want these [mirrors]("https://launchpad.net/ubuntu/+archivemirrors") instead, but still no zsync files for lucid.

---

### Post by VMC on 2010-02-05
Ok I found a good zsync mirror. I needed to search using google linux page. The ubuntu mirrors above didn't reveal anything.

This mirror has a current lucid daily: [http://spo1.linux.edu.lv/mirrors/cdimage.ubuntu.com/daily/current/](http://spo1.linux.edu.lv/mirrors/cdimage.ubuntu.com/daily/current/)

The download went much faster. Average 90kb/s

---

### Post by vishalrao on 2010-02-06
ah thanks! i should start using zsync too and try this mirror also :D

---

