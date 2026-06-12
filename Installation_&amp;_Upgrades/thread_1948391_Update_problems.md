---
title: "Update problems"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by StoneAgeMan on 2012-03-28
Hi
 Pleased to meet you all! My First Posting:

Every time I try to get upgrades automatically or manually. The updates appear to download but then I get the following message  
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I had problems (caused by "planned maintenance by my ISP). which involved rebooting the router, which is the only thing I can think of that may have caused it.

:confused:

S.A.Man

---

### Post by cortman on 2012-03-28
Hi StoneAgeMan! Welcome to the forums, but please leave your club behind. :)

What version of Ubuntu are you running?
If you are indeed running 10.04 Lucid Lynx, follow the instructions on this [blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/"), and post back with the results.
Good luck!

---

### Post by raja.genupula on 2012-03-28
> **cortman said:**
> Hi StoneAgeMan! Welcome to the forums, but please leave your club behind. :)

What version of Ubuntu are you running?
If you are indeed running 10.04 Lucid Lynx, follow the instructions on this [blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/"), and post back with the results.
Good luck!

+1 cortman.
if any problem still ```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by StoneAgeMan on 2012-03-28
Thanks cortman,
Both for the welcome and pointers.
Problem Solved  Very Grateful to you.
 As you will probably realise I am an old  dog trying to learn new tricks.
 But I think I will like it here rubbing shoulders with some younger experts.
S.A.Man

---

### Post by cortman on 2012-03-28
> **StoneAgeMan said:**
> Thanks cortman,
Both for the welcome and pointers.
Problem Solved  Very Grateful to you.
 As you will probably realise I am an old  dog trying to learn new tricks.
 But I think I will like it here rubbing shoulders with some younger experts.
S.A.Man

Well, big +1 to the old dog for trying to learn new tricks! We're always glad to help, although few of us are experts.
Good luck, and thanks for marking [SOLVED]!

---

