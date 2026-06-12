---
title: "Intrepid sources gone?"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by jjdelc on 2010-11-07
I have a server with ubuntu Intrepid. I wanted to upgrade and install some stuff but when running apt-get update I get:

```

.....
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Err http://security.ubuntu.com intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com intrepid-updates/universe Packages
Ign http://us.archive.ubuntu.com intrepid-updates/universe Sources
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Err http://us.archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com intrepid/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://security.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
.....
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

When I go to [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) I see that there's no Intrepid among the available sources. I looked at other sources and they are also missing Intrepid.

---

### Post by dino99 on 2010-11-07
Intrepid is off now

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by plucky on 2010-11-07
This link might help.


[EOL Upgrades](https://help.ubuntu.com/community/EOLUpgrades)


Good Luck

---

### Post by owlcroft on 2010-11-08
Can someone please explain in more detail, for non-experts, what this signifies, and what *exactly* someone with an 8.10 system should be doing now?

---

### Post by uRock on 2010-11-08
You need to install a newer version. For longevity, Ubuntu 10.04 LTS is recommended.

---

### Post by StormNinja3 on 2010-11-10
I have newer versions of Ubuntu running on 2 laptops but my desktop is Intrepid 8.10 and I like it just fine.  I don't see why I shold have to completely roll over my Operating System.  This is  a headache that I don't need at the moment! :frown:

Incidentally, I have 10.04 on a laptop and I dislike it immensely.  I will not be going that route with my desktop.

Owlcroft, you can update your 8.10 to verison 9.04 Jaunty by doing the following:

Go to System> Administration>Update Manager.  Click Update Manager> give password when prompted> Then click the Update to Newer Version Button that you will see on the Upper Right corner of the update window...Version 9;04 will then start to download itself...

Unfortunately for me..I am in no mood to update...so I guess I'll sit on 8.10 a while longer...

---

### Post by uRock on 2010-11-10
9.04 is no longer supported either.

---

### Post by snowpine on 2010-11-10
> **StormNinja3 said:**
> I have newer versions of Ubuntu running on 2 laptops but my desktop is Intrepid 8.10 and I like it just fine.  I don't see why I shold have to completely roll over my Operating System.  This is  a headache that I don't need at the moment! :frown:

Canonical has limited resources and has made the decision that they can only comfortably support 5 releases at a time. Their developers need some free time to work on the *next* release, otherwise development will stagnate.

"End of life" date are [published well in advance]("https://wiki.ubuntu.com/Releases"). You knew when you installed 8.10 that support would end April 2010.

If 8.10 works well for your needs, you may of course continue to use it (with no support or updates from Canonical). Releases do not magically self-destruct on their "EOL" date. ;)

---

### Post by StormNinja3 on 2010-11-10
uRock,  I am aware that 9.04 is winding down(or has wound down) but the easiest way for the User to update would be to install 9.04 then roll it over to 9.10 and ultimately 10.04.

Snowpine, do not lecture me on the subject of end of support.  Yes.  I knew that support would end but that does not mean I have to like it or not grumble about the  issue; however, YOU do not know me or what my level of understanding of Linux Operating Systems.  YOU should know many complete novices migrate to Linux and have little to no understanding.  The learn as they go.  So deep six the superior attitude.

I have absolutely no intentions of discontinuing 8.10 at this time.

The next time you advise someone watch your TONE.  I will not be chastised nor do I need to be lectured on Canonical's   resources or lack thereof.  I appreciate that you were trying to be helpful in an informative way but you manner was arrogant and I encounter that enough on the Net.  I will not tolerate it here.

---

### Post by uRock on 2010-11-10
The OP could also upgrade from 8.10 directly to 10.04.

---

### Post by fixy67 on 2010-11-10
> **snowpine said:**
> Canonical has limited resources 
And has no enough storage capacity for storing all versions? 
I've used Ubuntu till today. Now I'm going back to "standard" Debian.
Thanks for canonical... 

In the last year I've tried the newer Ubuntu releases, but I had many problems with them.
(I've used it as host for virtualbox)

---

### Post by snowpine on 2010-11-10
> **StormNinja3 said:**
> Snowpine, do not lecture me on the subject of end of support.  Yes.  I knew that support would end but that does not mean I have to like it or not grumble about the  issue.  I have absolutely no intentions of discontinuing 8.10 at this time.

The next you advise someone watch your TONE.  I will not be chastised nor do I need to be lectured on Canonical's   resources or lack thereof.  I appreciate that you were trying to be helpful in an informative way but you manner was arrogant and I encounter that enough on the Net.  I will not tolerate it here.

I am just an ordinary guy/gal just like you, not an Ubuntu developer. Complaining on Ubuntu Forums will accomplish nothing. If you want to make a suggestion to the people in charge at Canonical, here's a link to the correct forum to do so: [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by snowpine on 2010-11-10
> **fixy67 said:**
> And has no enough storage capacity for storing all versions? 

End-of-life Ubuntu releases are moved to: [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

> **fixy67 said:**
> I've used Ubuntu till today. Now I'm going back to "standard" Debian.

Debian does the exact same thing: [http://archive.debian.org/debian/](http://archive.debian.org/debian/)

---

### Post by fixy67 on 2010-11-10
> **snowpine said:**
> End-of-life Ubuntu releases are moved to: [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)


Thank you! I will try it...

---

### Post by iglablues on 2010-11-10
Thanks snowpine, plucky, urock, and dino99. I had the exact same issue on my Ubuntu server and missed this thread (Googling the wrong part of the output from apt-get install tomcat6). Your information was very useful and saved me from banging my head against the wall (or trying to manually install Tomcat6). :)

---

### Post by StormNinja3 on 2010-11-10
I have no hard feelings towards you Snowpine.  Thanks for the link and Best Wishes.

---

### Post by owlcroft on 2010-11-11
OK, I upgraded incrementally but rapidly through 9.04, 9.10, and have arrived at 10.04; from what I see about 10.10, I think I'll just stay here for now.

Naturally, all the "helpful" changes in look and feel mean that I have hours of discovery and tinkering before me to try to get back to what I have been used to, but I've come to accept that as normal.  I do, though, wish I knew why all the window-operation buttons (close/hide/minimize) have moved from the upper right of windows to the upper left. . . .

---

### Post by StormNinja3 on 2010-11-11
I have read, so I don't know how true it is, that Developers wanted to give Lucid a "Mac" feel as the buttons are arranged in reverse side order in Apple's system.  But I understand how you feel.  Below are 4 links.  The first discusses general changes you will find in 10:04.  The second contains a method to reorder the buttons.  I believe this is also possible without resorting to the technique in the link;  if you set your machine to either Ambiance or Radiance Appearance Theme but you may still be interested in knowing/learning an alternative.

Note-the 1st link really discusses the OS when it was in Beta but it is still accurate as to what you'll encounter.

[http://www.webupd8.org/2010/04/ubuntu-1004-lucid-lynx-beta-2-released.html](http://www.webupd8.org/2010/04/ubuntu-1004-lucid-lynx-beta-2-released.html)

[http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html](http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html)

How to customize Ambient Theme

[http://www.unixmen.com/linux-tutorials/917-customize-1004-lucid-lynx-ambient-theme-tips](http://www.unixmen.com/linux-tutorials/917-customize-1004-lucid-lynx-ambient-theme-tips)

If your machine is a laptop(it doesn't matter if it is not-still useful info ). The 4rd link discusses 10:04 AFTER the Beta test w/screenshots and commentary from Users.

[http://gadgetmix.com/articles/ubuntu10-04-review/](http://gadgetmix.com/articles/ubuntu10-04-review/)

While you are exploring your new OS.  Verify that all your drives are detected.  I know from personal experience this is a known and serious issue with Lucid Lynx on some computers.

---

### Post by wap445 on 2010-12-14
I have Ubuntu 8.10 installed on my Dell Inspiron 6000. And there is an existing mouse click issue with all the later versions of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1137700&page=7](http://ubuntuforums.org/showthread.php?t=1137700&page=7)

I have tried almost all the techniques out there and nothing seems to help.

What do I do if upgrade is not an option for me?

---

### Post by el_chupacabra on 2011-01-01
Here is an example for the /etc/apt/sources.list that is still working:

```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted

deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ intrepid universe
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid universe
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://old-releases.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-security universe
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ intrepid-security multiverse

```

---

### Post by lithopsian on 2011-01-01
The simplest and safest, and perhaps quickest) step is just to do the step from Intrepid to Jaunty.  No reinstall, just click a button and wait an hour.  At this point there is very little to go wrong with this unless you've recompiled half your drivers or installed lots of weird stuff manually.  Then you can go again if you're feeling confident.

If you don't have much in the way of non-repository applications and your own data is safely tucked away on a separate partition or backup up, then you can just install 10.04 or 10.10 and wipe out what is already there.  Or if you have the space for a separate partition, install a new version next to the old one and get your data straightened out before you wipe Intrepid.

---

