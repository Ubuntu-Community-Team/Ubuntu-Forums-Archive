---
title: "Pentium 4 slow in Ubuntu 14.04 LTS"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by ngant on 2014-09-24
I'm sure this is not a new question, but I've tried some of the  tweaks for speeding up Ubuntu and at least one made it worse and I had to do a re-install.  I increased memory which seem to help a little bit.

Memory is now 2.0 GiB, installed Ubuntu in a Intel® Pentium(R) 4 CPU 1.80GHz box  w/40Gig hard drive.

Would you recommend:

1.uninstall unity and compiz?
2.Remove Zeitgeist?
3. install gconf-cleaner?
4. Install bum to remove ‘unnecessary’ system services?
5.Adjust Swappiness?

---

### Post by mikewhatever on 2014-09-24
I'd recommend switching to Xubuntu or Lubuntu. They are more suitable for old P4 machines.

---

### Post by Vladlenin5000 on 2014-09-24
> **mikewhatever said:**
> I'd recommend switching to Xubuntu or Lubuntu. They are more suitable for old P4 machines.

^^^^
This. 

Regarding your list, your #1 would immediately result in no desktop, *if* it booted that is... And about your #5, with just 2GB of RAM you want to have at least 2~2.1GB as a swap partition and not reduce "swapiness".

---

### Post by ibjsb4 on 2014-09-24
I have installed Lubuntu on similar spec boxes with good results.

I always set swap to zero.
swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible 
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Gconf editor has been replaced with dconf, forget gconf :)

Instead of removing unnecessary system services, just don't install them in the first place.
An example would be Lubuntu-desktop.  You could instead just install lubuntu-core without the recommended packages.  Compare the two:
[http://packages.ubuntu.com/trusty/lubuntu-desktop](http://packages.ubuntu.com/trusty/lubuntu-desktop)
[http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

Or lighter yet is the LXDE desktop.
[http://packages.ubuntu.com/lucid/lxde](http://packages.ubuntu.com/lucid/lxde)

Remove Zeitgeist?  I never installed it :)

---

### Post by ngant on 2014-09-24
Yes, I think I will reinstall with Xubuntu or Lubuntu next time.  

OTOH I have a laptop w/2GiB memory, Intel Core 2 Duo CPU T7280@2.00Ghzx2 and 121GB drive and Ubuntu 14.04 LTS works very well in this box.  Apparently a 1.8GHz cpu is not adequate for 14.04LTS, even with a 2GiB memory upgrade(over double my previous memory, with only very little more speed to show for it).

---

### Post by mastablasta on 2014-09-25
the issue for slowness is likely the GPU chip. Unity uses hardware 3D acceleration to draw windows. so if you have a descent AGP card (something like AMD or Nvidia with 256MB or more and it's own GPU unit) it should work quite fluently.. Intel Core 2 Duo likely has better GPU chip as well as being faster.

if you can't get the card just use Xubuntu... or turn off unity and use gnome flashback, or use Mate or... so many choices.

---

### Post by Vladlenin5000 on 2014-09-25
As already commented, the GPU can be and often is a problem. We don't have information about it yet. Assuming it is the typical Intel integrated graphics contemporary of the CPU - 32-64MB reserved @BIOS - then I would say short, very short for a modern 3D desktop environment. A contemporary decent AGP card exactly as mentioned in the previous post makes a huge difference.

Now, I also I have bad news (not that the previous ones were good...):
A 40GB HDD must be old, very old, therefore _atrociously slow_. This I believe is the main cause of your perceived slowliness.



> I have a laptop w/2GiB memory, Intel Core 2 Duo CPU T7280@2.00Ghzx2 and  121GB drive and Ubuntu 14.04 LTS works very well in this box.   Apparently a 1.8GHz cpu is not adequate for 14.04LTS, even with a 2GiB  memory upgrade(over double my previous memory, with only very little  more speed to show for it).

Certainly you understand there's a world of difference between an old single core P4 and a Core2Duo with even higher clock. Here you're talking about a typical medium-to-high end notebook from 2006-7 whereas before you were talking about a a 15 or so years old entry level desktop. It's not just the clock difference that matters. Actually, that's the least of your problems.

---

### Post by frank18 on 2014-09-25
> **ngant said:**
> I'm sure this is not a new question, but I've tried some of the  tweaks for speeding up Ubuntu and at least one made it worse and I had to do a re-install.  I increased memory which seem to help a little bit.

Memory is now 2.0 GiB, installed Ubuntu in a Intel® Pentium(R) 4 CPU 1.80GHz box  w/40Gig hard drive.

Would you recommend:

1.uninstall unity and compiz?
2.Remove Zeitgeist?
3. install gconf-cleaner?
4. Install bum to remove ‘unnecessary’ system services?
5.Adjust Swappiness?


Suggest Xubuntu 14.04LTS;i have also DELL  P4 2.00Ghz  2 Mem ram and it runns great with Xubuntu  also get Chrome web browser it runs better then with FFox.

---

### Post by ngant on 2014-09-29
Just did a Xubuntu 14.04.1 LTS install, got DVD today from osdisc.com.  Definitely improved everything.  FFox is running okay for me.  Will consider a bigger hard drive but right now I'm enjoying the overall increase in page loading and applications.

---

### Post by ibjsb4 on 2014-09-29
Good deal :)  Don't forget ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

