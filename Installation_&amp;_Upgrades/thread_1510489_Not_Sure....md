---
title: "Not Sure...?"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by rob45 on 2010-06-15
Im new at running ubuntu...ive been running 9.10 and 10.04 as both upgrade from 9.10 and full install....i cant honestly see a great improvement from 9.10 to 10.04.But then im not running any fancy graphics card...stuck with the on board graphics of the unichrome igp thingy..?

Any way ive done alot of browsing in these forums...not because ive needed any help but because im that sad...and of course any info could come in usefull in the event that my system suddenly suffers from some unknown problem.

Im running a system thats built from ye old bits of gear abandoned by my son...chucked in to a tower...but hey..it works.
The motherboard is a via km400,it did have a gig of memory but one of the sticks died so i just have the 512/5..wotever in, its kingston brand .I have an 80gb hard disc i do have another even smaller one of 30gb but if i connect both they dont get picked up....think i need a new ide lead? Sound is provided by sound blaster 24bit.
I have a athlon amd???proccessor thing...that runs at 2.08...

I connect to the internet using a dongle 3G...pretty good.:)

Anyway the reason im posting this thread is because of a few problems im having....yea yea i know i said i wasnt having any probs ...just one or two niggly little things realy....something i could have learned to live with...put up with...but i dont want to.

ok heres a list...like i said not major issues just niggling little things....

1/ Being asked for my pass word at login screen...even though i chose to have the system boot straight into desktop...without requiring a password.

2/Password being asked for at login screen ,being asked for again....and again and again...in a never ending loop.

3/Password being rejected...not authenticated....at log in screen.

4/Not being offered upgrade to 10.04 desktop....despite installing all updates...about 300 in total for 9.10.

5/ Now this one really ..really bugs me.....Having two of everything in boot screen?


6/Sudo apt-get....not getting...


7/Being denied access to apply simple things...like having my internet connection automaticly connect to internet....Not enough privliges.

8/Some times system boots straight to login some times to the boot screen ...where i can choose which of my two identical systems to boot in to.....or have the choice to boot into the safe mode..with again the choice of two identical options.....wots the point???

9/Being unable to choose to boot into boot screen options....lol

10/Hours And Hours of My Time Wasted.


I m not expecting any suggestions...because most stuff does eventually sort its self out..resulting in normal operation of system.....until the whole loop starts again.....

All except for the double choice boot screen and im sure there is some perfectly simple explantion/reason why a double boot screen is required....it just irritates me.

And just in case your wondering....i love ubuntu......:)

---

### Post by oldos2er on 2010-06-15
By default there are two boot options for each kernel, one for recovery mode, and one for "normal" user mode.

If you post the terminal output from the apt-get errors, I'm sure someone could help solve that problem.

To upgrade from 9.10 to 10.04, run ```
update-manager -d
``` in a terminal.

---

### Post by rob45 on 2010-06-15
As far as im aware...i shouldnt be asked which OS i want to boot ,because im only running one OS,which was 9.10...fully updated,i ran sudo get-apt install dist- upgrade...as by instructions read via the help file. All updates were performed using sudo apt-get,because i was having problems with the update manager.

The boot screen presented me with two generic options,both the same,two safe mode,both the same,two memtest,both the same and one for memtest console......as im only using 9.10 this shouldnt be happening....maybe it does happen behind the scenes...somewhere unseen...but as they say ignorance is bliss.

Why would i need two installations of exactly the same OS?

Im sorry i cant provide you with the information that you asked for because im running from livecd at the moment..i have uninstalled 9.10 so i could ask a few questions.

I appreciate you taking the time to try to help/advise on my problems..

---

### Post by oldos2er on 2010-06-15
> **rob45 said:**
> Why would i need two installations of exactly the same OS?


Were you using legacy grub or grub2? Anyway, it's a moot question now since you uninstalled 9.10.

---

### Post by rob45 on 2010-06-15
hi..i was using grub2 as far as i know.
I am planning on re installing ubuntu,i just wanted to clear up a few things..i dont think i was having any major issues just the few odd things that are more irritating than troublesom....like my pic being the wrong way round....lol.
 sorry.

---

### Post by oldos2er on 2010-06-15
There's nothing to be sorry for. Grub2 is a little trickier to configure than legacy grub if you're new to it. See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Hopefully you'll have a better experience next time around.

---

