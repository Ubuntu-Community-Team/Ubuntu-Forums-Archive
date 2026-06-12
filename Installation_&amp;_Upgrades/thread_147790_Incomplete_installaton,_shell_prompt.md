---
title: "Incomplete installaton, shell prompt"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by SPlutard on 2006-03-20
I'm installing Ubuntu on an old laptop of mine. The hardware, as far as I know, meets the necessary requirements, though it's layout is modest. Before I started installing, it did have a weird partition on the HD, but I assumed that would be eliminated by the Ubuntu installation. 

I put the disk in and completed part 1 of the standard install with no problem. However, after I restarted without the disc, it started installing more things as normal, but it eventually came up with an error, saying something like "There has been an error with the installation. There may be a problem with your HD or its size. Ubuntu is not fully installed and may not work properly until you fix these errors manually."

Then, it stopped installing and a black screen (reminiscent of a DOS menu) came up & asked me to login. I did, and then it spit out the time & date & some other data, and then just left me with a blinking shell prompt....

First: what do I enter into the shell (`$: _)?
Second: How can I fix the errors manually so that things work properly in the long run?

Sorry for the long & convoluted post, but I hope someone can help. I was/am really excited to start working with Linux, and hope I can get it up and running.
Thanks!

---

### Post by Zelut on 2006-03-20
Well without detailed error messages it is fairly hard to say how to proceed.  I would, off the top of my head, have two things I would try..

1) you could try to re-install again & see if a second time around has any luck.  Are you sure you have sufficient HDD space? (2-2.5G generally).

2) It sounds similar to an issue I had with an installation a while ago.  I actually tried the following command, which worked, but I can't guarantee as I'm unsure you're error.  At the prompt you can try the following commands:

**sudo dpkg-reconfigure -a**
(this will try to reconfigure all the packages, and it may jumpstart itself to what it needs)
[B]sudo apt-get update
sudo apt-get upgrade[/B]
(these last two require an internet connection, so you will need to be wired)

---

