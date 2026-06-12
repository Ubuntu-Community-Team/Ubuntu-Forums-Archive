---
title: "Is canonical having a problem?"
date: 2010-09-16
forum: Louisiana Team - US
---

### Post by ad5xj on 2010-09-16
Today I just got the Qt 4.6.2 update that was released by Nokia more than 6 months ago. Version 4.6.3 has been out for a while and is quite stable. I use it every day on my Ubuntu 10.04 installation. I had to get it from Nokia directly. They are about to release 4.7.0. 

Is canonical in trouble? Qt is an integral basis for Ubuntu 10. Why is it that a critical element of the OS takes more than 6 months to get an update that is two generations behind?

What gives? And it is not just Qt - Java and FireFox are just as far behind. FireFox has just released 3.6.10 but canonical has not even released 3.6 yet.

Why have canonical releases if they are not going to keep up with at least the last stable release of critical elements of the distro like Qt, Java, and Firefox.

---

### Post by cascade9 on 2010-09-16
Ummm..isnt 10.04 using firefox 3.6.9? 

[http://packages.ubuntu.com/lucid/firefox](http://packages.ubuntu.com/lucid/firefox)

As for Qt (and other updates for that matter)- inserting updates just because there is a newer version can lead to stability problems. Its not quite the way that ubuntu works anyway.....using Qt as an example, (AFAIK) 10.04 has got 4.6.2, while 10.10 will have 4.7.0. I could be wrong, but I'd guess that 10.04 will always have Qt 4.6.2, from now untill end of life. 

If it makes you feel any better, on some of my machines I'm using firefox 3.5.12. I'm upstream (in some ways) from ubuntu, but I've got an older version...as long as it works, and I get security updates, its all good IMO. Mind you, I dont go checking versions just to see if there is a newer version.  ;)

---

### Post by ad5xj on 2010-09-16
I agree that updating just because there is a new one available is not a good strategy. However, we are not talking about new releases. Qt 4.6.3 is 6 months old and very stable. Firefox 3.6 is nearly that old and also very stable.

What is the use of including things like Qt and Firefox if you are not going to keep them up to current stable releases? That is not a good release strategy - at least not from the consumer perspective - definitely from the Ubuntu perspective because it does not require any work or responsibility on the part of canonical. 

But what value is that? Why even have canonical if that is going to be the method? If canonical wants to leave updates up to the author, then say so - not taut using them for updates (however out of touch they are). That is not the stated message from Ubuntu. Canonical is supposed to be THE source for Ubuntu compatible software and updates. As it turns out updates get to be irrelevant after falling behind two or three releases, especially when we are talking about tools like Qt and Java.

It is a confusing and frustrating mantra for what is otherwise a leading edge OS.

---

### Post by Joe of loath on 2010-09-16
If you don't like the way Ubuntu updates, then go use Arch. That's always the stable side of bleeding edge.

---

### Post by Troublegum on 2010-09-16
btw: Firefox 3.6.* **is** packaged in Lucid.

You should do some reading: 
[http://en.wikipedia.org/wiki/Freeze_(software_engineering)](http://en.wikipedia.org/wiki/Freeze_(software_engineering))
[https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)

---

### Post by snowpine on 2010-09-16
ad5xj, you completely misunderstand the Ubuntu development process. You are assuming that Canonical frequently "backports" new applications to older releases. This is not the case; rather, new features are incorporated into the *upcoming* release (currently 10.10).

Ubuntu is a "snapshot" distro which means 10.04 has the latest stable software as of April 2010, 10.10 will have the latest stable software as of October 2010, 11.04 as of April 2011, etc.

You only get minor updates like security patches and bug fixes; major updates are reserved for the next Ubuntu release.

Now maybe you consider this strategy a "problem," but Ubuntu has always worked this way and is currently the #1 Linux distro for the desktop. It is also followed by Debian, Redhat, and many other successful Linux distros. 

It is totally normal for the software in 10.04 to be almost 6 months old because 10.04 is almost 6 months old. When you upgrade to 10.10 next month, you will get new versions of **everything**. :)

---

### Post by ad5xj on 2010-09-17
Thanks for your many replys. I am not mis-understanding anything. I do however take exception to the way canonical implements the "distro" concept.

---

### Post by snowpine on 2010-09-17
> **ad5xj said:**
> Thanks for your many replys. I am not mis-understanding anything. I do however take exception to the way canonical implements the "distro" concept.

If you understood, you would not take exception. :) Or, you would move on to a "rolling release" distro (like Arch) that gives you the latest updates as soon as they are available.

"Is Tropicana having a problem" that their orange juice doesn't taste like apples? ;)

---

### Post by cascade9 on 2010-09-18
Nice, simple explaination of the development process in post#6 Snowpine. 

> **snowpine said:**
> If you understood, you would not take exception. :) Or, you would move on to a "rolling release" distro (like Arch) that gives you the latest updates as soon as they are available.

I pretty much agree, though I do have to point out that not all 'rolling release' distros will give you updates at similar times....I'm using Sid (well, aptosid but near enough) andl still have firefox (iceweasel) 3.5.12. Arch would have pushed past that a long time ago. 

It really does sound like you do want a rolling release (or a 'development' release) ad5xj. Lots of choices around, arch is a long way for the only one- gentoo, PCLinuxOS, openSUSE 'factory', fedora 'rawhide', mandirva 'cooker' (though with madriva having issues at the moment I wouldnt be going there) and others I've forgotten or dont know about...

---

