---
title: "Easiest way to install .tar.bz2 files."
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by colobix on 2008-08-21
Hey you guys.
Untill now I have used nautilus to install .tar.bz2 package files, but that's a hell of a pain because u have to sort the files in the right directories which takes forever. Isn't there any easier way to install them? Maybe with a command in terminal or a program that audomaticly installs them?

Plz answer.
Thank you.

---

### Post by jerome1232 on 2008-08-21
I'm confused are you talking about just extracting bziped tar archives?

Or building a program from source (which can't be done from nautilus...)

If your talking about just extracting them from a terminal

```
tar xjf [archive-to-be-extracted]

or if you want it to go somewhere specific

tar xjf [archive-to-be-extracted] -C [target directory]
```

for more information on using tar
```
man tar
```

edit: made the examples more generic

---

### Post by colobix on 2008-08-21
Thanks but i mean to install the files.
When I have downloaded a program from the web or something.
How can I do it as easy as possible?

---

### Post by jerome1232 on 2008-08-21
If they are pre-built binaries all you have to-do is extract them somewhere, if they are source files then you have to build them after you extract them.


being a tar.bz2 doesn't tell me which one that is, it could be either.

---

### Post by aysiu on 2008-08-21
What's the program?

---

### Post by DavidTangye on 2008-08-21
> **colobix said:**
> Thanks but i mean to install the files.
When I have downloaded a program from the web or something.
How can I do it as easy as possible?Tar files are simply compressed (normally) sets of 'real' files, originally so they could be streamed to tapes for backup (tar = Tape ARchive).

If you are getting files and installing them you need to be very careful, as you are not installing proper packages, so version dependencies are not being checked at all. Further down the track you will be back here reporting that something is broken/will not work/works oddly or upgrades fail.

There are no set rules and few conventions for what to do with any software bundled into tars. It depends entirely on what the bundler decides. Hopefully he has either 

[LIST]
[*]provided instructions where you got the tar from, and/or
[*]included a README or similar file in the tar. Unpack it from the tar and read it carefully.
[/LIST]
 To repeat: tar are inherently dangerous. The package manager ie Synaptic is safe.

---

### Post by colobix on 2008-08-21
It's a metacity theme from [http://www.gnome-look.org](http://www.gnome-look.org)
Sometimes (like now) I dont know where to extract them, so I wish there was a program out there to install archives like that automaticly where they belong.

---

### Post by jerome1232 on 2008-08-21
metacity themes, you should be able just to right click your desktop, hit change background, select the themes tab, drag and drop it in.

---

### Post by colobix on 2008-08-21
OH nice. Is it the same with the screensavers too? and what about x11 mouse themes? I know that was a little off topic but ok:)

---

### Post by aysiu on 2008-08-21
> **jerome1232 said:**
> metacity themes, you should be able just to right click your desktop, hit change background, select the themes tab, drag and drop it in.
Yes, and do not extract the .tar.bz2 first.

Drag and drop it in just as you downloaded it.

---

### Post by colobix on 2008-08-21
Ok thanks alot :)

---

### Post by davidbruington on 2008-09-08
I'm trying to install a GTK theme, file extension *.tar.bz2, and when I try to install it as described, it says the file does not appear to be a valid theme. I've tried several different themes, and I get the same error. am I possibly missing a required program or something?

---

### Post by aysiu on 2008-09-08
> **davidbruington said:**
> I'm trying to install a GTK theme, file extension *.tar.bz2, and when I try to install it as described, it says the file does not appear to be a valid theme. I've tried several different themes, and I get the same error. am I possibly missing a required program or something?
Maybe it's not packaged properly, or there's a .tar.gz compressed inside the .tar.bz2?

---

