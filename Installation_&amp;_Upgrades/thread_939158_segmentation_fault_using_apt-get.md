---
title: "segmentation fault using apt-get"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by dhjdhj on 2008-10-05
I had to give up on Fedora which I had been using for years and so this weekend I installed Ubuntu (seems very nice, BTW) and am busy trying to get everything I had in Fedora working again in Ubuntu.

Stuff like LAMP, ruby and so forth....was going well.

While trying to install a package called xnest, apt-get generated a segmentation fault. After following instructions from various forums, I deleted some cache files related to apt-get.

Now, I can no longer run apt-get at all. As soon as I start it, I get a seg fault. I tried

apt-get install apt --reinstall --force-yes

which looked like it was going to work but it then died almost immediately (looked like dying while reading packages).

As I was writing this report to try and get help, I ran the above program again, paying more attention so that I could better report exactly the failure....but the second time I ran it, it worked perfectly!

So now I'm sitting here reporting an error that is no longer an error.

I'd really appreciate some insight into what exactly happened...surely I don't have to type commands into Ubuntu twice to get them to actually work (grin)

Thanks,
David Jameson

---

