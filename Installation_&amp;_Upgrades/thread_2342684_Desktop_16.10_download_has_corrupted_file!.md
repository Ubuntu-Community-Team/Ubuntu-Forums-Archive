---
title: "Desktop 16.10 download has corrupted file!"
date: 2016-11-08
forum: Installation &amp; Upgrades
---

### Post by yogich246 on 2016-11-08
Hi, gang...

The 16.10 Desktop download link yields a corrupted file ...TWICE: [https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.1&architecture=amd64](https://www.ubuntu.com/download/desktop/thank-you?country=US&version=16.04.1&architecture=amd64)

The 2 downloads were done hours, apart. Hash isn't even, close (whatever close, is)!

---

### Post by Bucky Ball on 2016-11-08
What are you checking the downloaded MD5SUM against? Where are you downloading the 'correct' one for comparison?

The quickest and safest way to get the ISO is via a torrent. You'll find the link on the 'Alternative Dowloads' page.

---

### Post by yogich246 on 2016-11-09
I totally forgot to mention... sorry, about that ...that the 1st download was, a torrent. The 2nd, was using the download link, following my clicking the large 'Download' button at the top of the page. I ended up using wget, for that, with the same result. I then went to an alternate, USA mirror** ([http://mirror.pnl.gov/releases/yakkety/](http://mirror.pnl.gov/releases/yakkety/))** and that one, booted, at least. I used the requisite method of checking the hash, and the final download checked, out, burned the DVD, executed the boot....  but when it got to the point where it usually asks if I want to test or install, the screen was black & I could not change, that. I also could not check to see what the error was, of course, because there was no terminal, capability. I did, try, anyhow, just to make double-sure. At the time, I was connected to a 50" HDTV via HDMI. I subsequently changed to a regular monitor, that I have used, quite a bit, and experienced the exact-same, result.

I am currently using an online-upgraded Ubuntu, and have never experienced anything approaching, this. I have been using Ubuntu for some time, now, upgrading as they offer new ISOs.

---

### Post by Bucky Ball on 2016-11-09
> **yogich246 said:**
> ... the 1st download was, a torrent.

From where? Your thread is morphing into one about install problems. It started as an issue with not being able to download an ISO with hash that checked out. You still have that problem or you now have a clean one and it's not booting or you are now having issues installing?

If the latter, better to start a new thread with a descriptive title for your installation/black screen issues. It will improve your chances of support. :)

---

### Post by CantankRus on 2016-11-09
In your first post you are talking about downloading 16.10 yaketty, yet your link points to 16.04 xenial.
Are you downloading the right checksums.

---

### Post by Bucky Ball on 2016-11-09
> **CantankRus said:**
> In your first post you are talking about downloading 16.10 yaketty, yet your link points to 16.04 xenial.
Are you checking the right hash.

Well picked and good point. Had me confused as if OP downloaded the torrent and torrented the ISO from the official Ubuntu site it is highly unlikely the hash is going to be different. That is one of the main benefits of going for the torrent ...

* Yep, just checked myself. Looks like you're downloading 16.04 ISO and checking against the 16.10 hash, or something. Suggest you try again matching the correct iso with correct hash ...

When you've worked out where the problem is, please mark thread as solved (if you get there) and start a new thread for any issues you have trying to install. Thanks.

---

### Post by yogich246 on 2016-11-10
You asked for more information. There it, is. :?

And, this is why I seldom post to forums. lol

Gotcha. Sometimes, my eyes play tricks, on me.

Hm. IDK...will look, again. Thx, for that.

> **Bucky Ball said:**
> Well picked and good point. Had me confused as if OP downloaded the torrent and torrented the ISO from the official Ubuntu site it is highly unlikely the hash is going to be different. That is one of the main benefits of going for the torrent ...

* Yep, just checked myself. Looks like you're downloading 16.04 ISO and checking against the 16.10 hash, or something. Suggest you try again matching the correct iso with correct hash ...

When you've worked out where the problem is, please mark thread as solved (if you get there) and start a new thread for any issues you have trying to install. Thanks.

All I know, is... whatever the hash might have been --right one or not-- the torrent download didn't work. (And I'm marking this one, solved, since I will be staying with 15.10.)

[SOLVED] but I cannot find the place to say, that! I haven't posted, here, in months.

---

### Post by Bucky Ball on 2016-11-10
To mark the thread as SOLVED use 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post.

Feel free to stay with 15.10 but be aware it is no longer supported. You won't get a lot of support with it here but you will find some things online. The longer you leave it, the more unstable it will get as there aren't, and haven't been for awhile, any updates/upgrades for it, and that includes security updates. The longer you remain on that release and online the more of a security vulnerability your system will become.

The choice is, of course, yours, so good luck whatever way you go. :)

---

