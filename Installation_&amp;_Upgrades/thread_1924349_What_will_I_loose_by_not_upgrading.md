---
title: "What will I loose by not upgrading?"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by JoeFriday49 on 2012-02-12
I recently did an update in Ubuntu 10.04 from kernel 2.6.32.37 to 2.6.32.38 and lost my WIFI card, see posts:
[http://ubuntuforums.org/showpost.php?p=11640098&postcount=1](http://ubuntuforums.org/showpost.php?p=11640098&postcount=1)
and
[http://ubuntuforums.org/showpost.php?p=11641469&postcount=1]("http://ubuntuforums.org/showpost.php?p=11641469&postcount=1Well")

[COLOR=Black][Well]("http://ubuntuforums.org/showpost.php?p=11641469&postcount=1Well")[/COLOR] I have installed Startup Manager and can now automatically boot into the old working kernel (37) but since there appears to be no cure for the latest kernel (38 it seems I will be stuck on this old version.  (Still unassigned in Bug Report)

Question is, what do I loose by not upgrading and staying with the outdated kernel?
And another, is there a way to remove the non-working (38 kernel or should I just leave it alone?

I have 3 more machines and I'm afraid of updating them for fear of creating bricks...

---

### Post by Dennis N on 2012-02-12
If it were me, I would leave the newer one installed. If you uninstall it, update-manager will continue to offer it as an upgrade (which can be annoying) while you wait for further kernel upgrades that might fix the problem.

---

### Post by Old_Grey_Wolf on 2012-02-12
Have you tried the Realtek r8168 driver?

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Extract it somewhere and run this command from the folder you extract it to
```
sudo ./autorun.sh
```
-----------------

As far as staying with the older kernel, I have never seen Linux Mint upgrade the kernel. Maybe they do and I've just never seen it happen. I don't use Linux Mint that much.

---

### Post by JoeFriday49 on 2012-02-12
> **Dennis N said:**
> If it were me, I would leave the newer one installed. If you uninstall it, update-manager will continue to offer it as an upgrade (which can be annoying) while you wait for further kernel upgrades that might fix the problem.

Hadn't thought of that...  I'll just leave it be until the next release...
Thanks

---

### Post by JoeFriday49 on 2012-02-12
> **Old_Gray_Wolf said:**
> Have you tried the Realtek r8168 driver?

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Extract it somewhere and run this command from the folder you extract it to
```
sudo ./autorun.sh
```-----------------

As far as staying with the older kernel, I have never seen Linux Mint upgrade the kernel. Maybe they do and I've just never seen it happen. I don't use Linux Mint that much.

That's how I made the inital installation work...  With the release of this latest kernel WIFI quit and reinstalling the driver doesn't do anything.  It simply won't run under this new release.  There is a bug report about this issue here:
[https://bugs.launchpad.net/ubuntu/+bug/921141](https://bugs.launchpad.net/ubuntu/+bug/921141) 
It is listed as Confirmed and Unassigned...

I've never used Linux Mint either...  I did install it on an old clunker and get it running for a fellow, but that was a couple of years ago...

---

### Post by Old_Grey_Wolf on 2012-02-12
OK. I must have missed a post somewhere. 

In this thread [http://ubuntuforums.org/showthread.php?p=11640098#post11640098](http://ubuntuforums.org/showthread.php?p=11640098#post11640098)  it shows you are using the r8169 driver
rather than the r8168 driver.

---

### Post by JoeFriday49 on 2012-02-12
> **Old_Gray_Wolf said:**
> OK. I must have missed a post somewhere. 

In this thread [http://ubuntuforums.org/showthread.php?p=11640098#post11640098](http://ubuntuforums.org/showthread.php?p=11640098#post11640098)  it shows you are using the r8169 driver
rather than the r8168 driver.

Maybe you didn't...  Thought I'd tried everything on the Realtek site...  I'll investigate further...

---

### Post by JoeFriday49 on 2012-04-23
Just tested kernel 2.6.32-41...  Bug still exists in this latest release.

---

