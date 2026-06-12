---
title: "First black screen, now graphs errors! Need help NOW!"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by mu:te on 2007-04-11
Aight so here is the thing. I wanted to set up an ATI Driver yesterday, unfortunately  it can be very had to find a good Linux Guide website on the Internet, even harder to find one who is int out dated. 

So basically, this guide I followed a simple guide who said that I should edit some registry entries and put "pglx" something into it. Well, after few attempts and changing few changes I restarted my computer. 

Well, when it was "loading" ubuntu again I just got some black screen who asked me for username, password ect. and it basically it was Full blackscreened terminal. but I never saw any fancy graph index loading screen with the ubuntu logo and stuff.

Well, after probably few hours, 5-6 or so I finnnnnallly managed to fix it. Dont know how, but I did.

Anywho, now that I was able to log in my screen began to act funny. For an example if my firefox browser isint in the middle of the screen its just get fu** up. Basically, everything on the sideways is fu**ed up. Its very very annoying because I cant do anything. If Ill open the tool > settings on firefox I cant see any letters. Just some crashy letters. 

Im going to try and put and image with this letter, unfortunately I cant edit the picture because Im not going to risk it and put firefox down, because I would probably never find it again.

[IMG]http://img183.imageshack.us/img183/8547/screenshot1se4.png[/IMG]

---

Aight added some image, not sure what if it works because the whole picture looked crashy to me. Hope to get an answer a.s.a.p.

---

### Post by mu:te on 2007-04-11
I lowered the screen result to 800 * 600 and its okay now but I rather have a bit higher res., could anyone help me fix this?

---

### Post by mu:te on 2007-04-15
Can anyone please help me with this? Its kind of annoying to have that low res.

---

### Post by westli on 2007-04-15
Well... it looks like you hosed your /etc/xorg.conf file.  If you made changes to it and don't remember what you did, you're just going to be poking around in the dark.  If you backed it up before you started doing anything, you can delete the newest one and rename the backup to xorg.conf.

Read everything you can about that file and try to fix it, or just reinstall.  If your /home is on a separate partition, you can reinstall without losing all your settings, otherwise, try to back up all your documents, bookmark files, etc onto a CD or to a partition that isn't going to wiped out by a reinstallation.

Many's the time I tweaked my linux installation into oblivion years ago.  I try to save myself that pain by leaving a trail of breadcrumbs I can follow back.

When you need help like this, it helps to mention which distro you are using.

---

