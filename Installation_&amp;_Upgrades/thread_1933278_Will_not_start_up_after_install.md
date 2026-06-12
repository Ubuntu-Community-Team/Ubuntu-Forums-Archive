---
title: "Will not start up after install"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by Spacemonkey8999 on 2012-02-29
Hi,

I just got a new (refurbished) HP Pavilion dv7. After booting up the pre-installed Windows 7 and confirming all the hardware checked out, I went about wiping the hard drive and installing Ubuntu 11.10 64 bit. After installing and booting up for the first time it hangs after throwing:

```
Bad LUN
Bad target number # (repeated)
```

OR

```
Checking battery state...
```

From here I can I can press alt+f1 to get to tty1 and it works just fine, minus xWindows, Gnome, or Unity. So I am thinking a GPU issue?  It is an:

AMD A6-3400M with integrated ATI Radeon HD

What really confuses me is I got it to start off the live disk pretty easily following: [http://journalxtra.com/linuxsanity/ubuntu-fixing-the-blank-screen-on-installation-bug-2532/](http://journalxtra.com/linuxsanity/ubuntu-fixing-the-blank-screen-on-installation-bug-2532/)
But when I try to issue the same commands through GRUB I still come to the same issue.


Thanks in advance and let me know if more info is needed,

--Matt

---

### Post by Spacemonkey8999 on 2012-02-29
Full specs at:

[http://www.woot.com/blog/viewentry.aspx?id=22188](http://www.woot.com/blog/viewentry.aspx?id=22188)

---

### Post by Bucky Ball on 2012-02-29
If it is graphics you could try adding 'nomodset' to the kernel line, or indeed, installing with that option set. When you boot from the CD and get to Try Ubuntu and the other options, hit F6 (from memory). There  you should find the option 'nomodset'. Set it and install.

For the first fix I suggested, boot your machine from the install already on the hard drive, when you get to the list of OSs on the machine (grub list);

Hit 'E' to edit the kernel you want to boot (probably the first one);
Find the kernel line with 'nosplash' at the end (could be something else but 'splash' will be there somewhere);
To the end of that line add 'nomodset';

I think you then hit 'B' to boot but the instruction are down the bottom of that screen anyhow.

You could also boot as normal and when you hit alt+F1 try:

```
startx
```

---

### Post by Spacemonkey8999 on 2012-02-29
Thanks for the speedy reply but it still just hangs... Now at the blank screen with the blinking '_'.

The problem also still persists after getting up-to-date by running:

```
sudo apt-get update
sudo apt-get upgrade
```

startx throws:

```
Fatal server error:
no screens found
```

---

### Post by Bucky Ball on 2012-02-29
```
Fatal server error:
no screens found
```I would try adding 'nomodset' to the kernel line at boot.

So you are actually online when at the command line??? 'sudo apt-get update' actually updates the machine? Doubt either of those commands are going to be much help just at the minute ...

You could also try searching for AMD A6-3400M or ATI Radeon HD or both with 'ubuntu' tagged to it and see if you can find any terminal commands for installing the drivers from where you are, if you are online.

* Or, you might try this:

[http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/](http://alexsleat.co.uk/2011/03/04/how-to-fix-fatal-server-error-no-screens-found-ubuntu/)

... or search through here:

[http://au.search.yahoo.com/search;_ylt=A0oGkmQlxU1PQCsA4mML5gt.?p=fatal%20server%20error%20no%20screens%20found%20ubuntu%2011.10&fr2=sb-top&fr=altavista&rd=r1](http://au.search.yahoo.com/search;_ylt=A0oGkmQlxU1PQCsA4mML5gt.?p=fatal%20server%20error%20no%20screens%20found%20ubuntu%2011.10&fr2=sb-top&fr=altavista&rd=r1)

---

### Post by Spacemonkey8999 on 2012-02-29
> So you are actually online when at the command line??? 'sudo apt-get update' actually updates the machine?
Yep, the live disk worked beautifully and as far as I can tell the network drivers are up to par.  That's the most baffling part! X, gnome, and Unity all worked while running off the live disk...

Thanks for the tips, I had just started looking into messing with xconf and all that.  After reading through and trying things out I'll post how it went. In the mean time more advice is always appreciated if any one comes up with anything.

Thanks again!

---

### Post by Bucky Ball on 2012-02-29
I meant are you online when you boot up from the hard drive and get to the command line ... ;)

---

### Post by Spacemonkey8999 on 2012-02-29
Yep, USB key out and I am still free to apt-get and ssh as I please (wired, not wireless). Just no fancy browser... :(

---

### Post by Spacemonkey8999 on 2012-02-29
Okay, so here is how it ended:

I tooled around with the xconf file and installing the third party ATI drives via the command line.  This more or less worked, it was very slow to start up and the screen would freeze for a second or two rarely.  Sorry the steps are not better recorded but I was only poking around to see if I could make progress.  I am sure by following the instructions posted in previous links better, one could get better results.

BUT! I went ahead and grabbed 12.04 and it worked perfectly, right out of the box! (As of writing this 12.04 is currently in beta and you can get the daily release over at: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/))

Once the stable, full, release is out I will confirm it with that.  But for now... solved?

Again, thanks and I hope this helps others!

---

### Post by Bucky Ball on 2012-02-29
That's good news, BUT, expect breakages on updates and DON'T use this for a production machine or expect stability and reliability (ie important work is not a good idea). You might want to give the current LTS release a whirl, 10.04 LTS (v. stable, current LTS, support until April 2013, one click upgrade via update manager to 12.04 LTS when that is released and eventually stable). 

Have fun. ;)

PS: When it is officially released in April there is no guarantees it will be stable then, at least for a few months after release, even though it might be called a 'stable' release. It is an LTS release though so you are on the right track (Ubuntu 12.04 LTS will be supported for five years, as the server versions of the LTS releases have been in the past).

---

