---
title: "Lilo - Botched install!!"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by jfreak53 on 2010-06-18
Ok, so I have had Jaunty installed for quite some time now, no probs.  I went to do a much needed system update on installed apps.  Of course it was a partial since a lot of them required other things to be updated first, it's been like 4 months since last one ha ha.

So I update no probs. I was using 2.6.28-14 kernel version, it update me to 2.6.28-15.  Now I have upgraded kernels many times, not first timer, but this is a first to me.  So I have this wierd system setup, don't ask.  Where I use lilo instead of grub, just take it as it comes guys, I have to.  At any rate, it upgraded all fine, and I restarted, play the blues :guitar:

I got a "No setup signature found" error and lilo won't boot.  So I did some searching on web and everyone says to boot up CD and re-install lilo.  Well with grub I've done this many times, no prob bob, but lilo won't work.

So I used my super auto grub CD to try to re-do things.  Since grub config and grub was still installed on my Linux partition I tried it right.  No go of course, grub says it can't find the partition nor can it mount it.  So I tried the beta of lilo on the grub cd and it don't work either.  Botched it up worse, first it wouldn't do anything on my second drive, just sat there black screen.  Then I did it a second time, let's screw it up some more right ):P.

Now it doesn't even find a boot loader in the MBR ha ha.

So at any rate, how in the sam heck do I fix this thing?  Short of downloading 10.04 and re-installing everything??  Don't want to do this, too much work when I can just upgrade and keep my stuff installed and setup.

So I tried running jaunty from CD and re-loading lilo.  So everything is working fine right, I mounted drive and apt-get install lilo and ran lilo.  So lilo even telling it what config file to use and where won't find things and won't re-install.  So just for grins, even though I thought it wouldn't work I mounted my second drive linux partition, the one with the boot info on it, you ready, to root "/".  Then I couldn't unmount ha ha ha.

So I reset and here I am in windows.  So any ideas?? ha ha

---

### Post by oldfred on 2010-06-18
I have never used lilo, but this script shows your entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by jfreak53 on 2010-06-19
Ok thanks for the info.  I got into it and about 2 minutes into it I said awww screw it ha ha.

So I downloaded UBU 10 and copied my home dir out, then re-installed!  So now it's working great and I love this new 10!

Plus I hadn't been paying any attention that Google now has Chrome for UBU, it's awesome!

Thanks again for the help. ):P

---

