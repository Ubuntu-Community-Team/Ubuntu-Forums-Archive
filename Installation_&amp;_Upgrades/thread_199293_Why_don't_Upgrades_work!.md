---
title: "Why don't Upgrades work?!?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Mr. Wizard on 2006-06-18
How do I install the 69 updates Ubuntu 5.10 most uselessly informs me are available?  I can't get it to do a damn thing about them!  All I get when I try to Show them is get an irritating single drumbeat sound in response.  Of course, there is absolutely no help whatsoever associated with the Package Manager (?) icon...

So far, after a few months of trying to do something useful with Ubuntu when I am in the mood to be frustrated, I am wondering why I bother.  I've learned numerous OSes by just sitting down and using them, sometimes with a little help from some sort of "Getting Started" guide, often a few pages of photocopied notes some site manager threw together.  The lack of good documentation is one of the most serious drawbacks to Ubuntu, IMHO.

At present, I've ordered the 6.06 discs, but I'd like to try to upgrade my way there from this installation without f*cking up the contents of the Windows XP Pro x64 side of the dual boot system.  At least the Winblows side is good for something...  I really want to avoid having to ever use Vista, but I am becoming resigned to th fact that Microsloth seems to still have a practical monopoly in the functional, popular OS department.  I note that a group of Web developers I chatted with at their place of business recently were all raving about how great Linux is, but when they were showing me stuff, I saw nothing but Windows running on their machines.  Hmmm...

Assuming someone is kind enough to explain what is preventing me from updating the system in question, I'd really like to know where I can find a "drop-in" C/C++ and AMD64 development system -- programming for a platform is generally a very good way to learn about it quickly.  I've looked at the GNU stuff on Windows, but don't see the point.  If I had a working development system running under Ubuntu, I might (eventually) get over my inherent distaste for anything that has a poorly designed interface. :-/

---

### Post by hashimoto on 2006-06-18
As the upgrading does not work from the icon, my guess is that you did an expert install. You had to give a roo/super user password during that install. Right?

If so, you as a standard user, do not have the right to use administrative programs (you should, though). This seems to be a bug in the expert install.

To fix, do the following:
Open terminal and log in as root by doing:
```
su
``` and give your super user password
then:
```
visudo
```
at the end of that file add:
```
yourusername    ALL=(ALL) ALL
```
Then save and exit.
The administarive programs should now work.

Hope this helps!

---

### Post by angkor on 2006-06-18
[QUOTE=Mr. Wizard]How do I install the 69 updates Ubuntu 5.10 most uselessly informs me are available?[/QUOTE]

Usually opening up a terminal and typing:

```
sudo apt-get update
sudo apt-get upgrade
```

You will be prompted for your user password, if your user has admin priviliges.

does the trick. 

For the rest of your question (?) I don't know.

---

