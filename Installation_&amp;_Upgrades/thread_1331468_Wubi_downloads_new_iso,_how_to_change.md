---
title: "Wubi downloads new iso, how to change?"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by mocoloco on 2009-11-19
I've created a customized disc using the [Ubuntu Customization Kit]("http://uck.sourceforge.net/"). It all worked great but I decided to try a Wubi install with that disc, and was surprised to find that if the PC is connected to the internet Wubi will actually download a torrent of the Ubuntu iso and use that. This means if a user installs from Wubi they won't get the setup from my customized disc, unless they're not connected to the internet. So my questions are:
[LIST=1]
[*]How do I change Wubi to never download an iso and only use what's on the disc?
[*]Out of curiosity, why does it do that?  Seems like a waste of bandwidth if it's got files right there on the disc.
[/LIST]

---

### Post by darkod on 2009-11-19
You have to put the ISO (not extracted) in the same folder where wubi.exe is when you are trying to run it. Then it should use the ISO. I read about it, never tried it, never needed wubi.

PS. I don't know if the name of the iso has to be the same as ubuntu official iso, try both options.

---

### Post by wojox on 2009-11-19
Never used Wubi mocoloco, but I assume it's an .exe file since it installs on Windows? Probably something hard coded into it.

---

### Post by mocoloco on 2009-11-19
Thanks for the suggestion darkod but I know Wubi itself creates an iso out of the files on disc and does that for you, but it looks like it defaults to downloading a new iso first if there's a net connection.  I'm hoping someone familiar with Wubi can tell me where to change that, specifically is there some external files the exe uses I can alter, or would I need to recompile a new exe?

There used to be a separate Wubi forum in here that the Wubi devs would hang out in. I would post there but it appears to be gone now.

---

### Post by darkod on 2009-11-19
As I said, I never needed to use it myself, but I know exactly what you are asking. I saw exactly the same question I think on wubi section on ubuntu website.

And it said: if you have the iso in the folder where wubi is it will NOT try to download.

That's what you want so give it a shot. If you already have it as iso, extract just wubi, put wubi.exe and the iso and the same folder and try.

---

### Post by darkod on 2009-11-19
How to use manually downloaded iso?
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20use%20a%20manually%20downloaded%20ISO?")

As I said, not sure if it will work with custom iso but you can try. Make the iso name as the official desktop iso if needed.

---

### Post by mocoloco on 2009-11-19
Ok, I see the confusion, you're thinking I'm doing a one time thing.  I have created a disc that I want to hand out to multiple persons.  I won't be able to create and place an iso in the wubi folder manually for each person if they choose to use Wubi.

Along those lines, although I could write something that will create an iso and place it in the right folder, then have it autorun before Wubi runs, that would be the long route. Since Wubi already does that if it can't connect to the internet (as I've seen testing it), I just need to tell it to not even try the download at all.

---

### Post by darkod on 2009-11-19
Or maybe some kind of self-extract package with wubi.exe and the iso inside. Anyway, you seem on top of things... :)

---

### Post by mocoloco on 2009-11-19
I want to look through the source. I can only find [source for up to version 8.10 on sourceforge]("http://sourceforge.net/projects/wubi/files/"), for 9.04 and 9.10 it only has the .exe.  What's up with that?

I'm not much of a coder but want to check it out, maybe file a bug since I think the behavior should be to use the available files on disc first before attempting to download an iso.

Still hoping some wubi devs will chime in.

---

### Post by mocoloco on 2009-11-19
So I figured out what's going on, it's the md5sum. Wubi downloads the Ubuntu md5sum and checks it against the one on the disc, and if they don't match it assumes it's bad and downloads a new iso. If I run wubi --skipmd5check then it works fine even when connected to the internet.

I was able to download and look at the source for version 8.10, and I can see where I would stop the md5 check (or I could just have it check the right one), but like I mentioned I can't find the source for the current version of 9.10. I would be wary about using the 8.10 source, since it includes grub4dos and Ubuntu 9.10 now uses grub2, so it would probably be a dead end to try that.

So now my question is where can I get the source for 9.10?  Wubi guys, what say you?

---

### Post by mocoloco on 2009-11-21
Bumpin' the question.  Where can I get the source for Wubi 9.10?

---

### Post by wilee-nilee on 2009-11-21
If you look on the web there are wubi 9.10 downloads but as with anything be careful. This page may be of some help.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by garvinrick4 on 2009-11-21
In the last few versions of Ubuntu you just have to download an .iso file one cd about 698 meg or so. BURN it to a disk at a medium to slow speed not 24x and when it is doe put in CD tray, do not make it boot, just put it in CD tray. Pick WUBI answer 2 questions and it
is downloaded any where from 5 to 20 minutes according to your prcessors.
 Boot is attached to DOS4GRUB in Windows and is second in line in boot, arrow down and
you are in. They have made it so simple. If you screw it up at any time just uninstall in
windows it is right next to Users in C: drive. Nice to learn with, real nice.
 Same disc can be used for dual boot with partiontions when and if you are ready.
Only tough part about Linux is drivers now and again but you work it out. No more needing
to put WUBI download in same folder at all. You did have to do so previous was not wrong
just out of date on WUBI a touch.  Have fun

---

