---
title: "ISO will run on one PC but not another"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by superchief on 2012-03-24
Hi Guys,

This is a question that i am sure you all get here a lot however i am in somewhat of a hurry to get Windows XP off the laptop and get ubuntu / any linux on there.

So here is the gist of what i have done and the disc image i am using is: ubuntu-11.10-desktop-i386 (32 bit):

1. Downloaded image on windows 7, burnt to disc, loads ok in windows 7. Inserted disc into windows xp laptop...it spins for a while, recognises the name of the cd but says it is invalid. I assume that windows 7 can load the CD and i can view files in explorer so should windows xp.

2. Downloaded image on windows xp machine, burnt to disc, loads ok in windows xp. Tried to load and boot off the cd on the windows xp laptop and it just outright refuses.

Now my first thought is BIOS issue. However this is still a boot CD, it loads a windows xp boot CD fine and any other disc i try...except this one. I thought about purchasing a cd from Ubuntu but i am unwilling to do so given that this doesn't work.

Could it be that my laptop is simply a little old and i need to go back to an earlier version of ubuntu and then upgrade or should i try another linux install? I do have a very old copy of knoppix somewhere around here.

Any help anyone can give would be great and i apologise if this has been asked before.

Thanks peeps

---

### Post by Paddy Landau on 2012-03-24
If the computer boots all CDs apart from this one, it says to me that there is something wrong with the CD.

The first thing to do is test your download. [Find the MD5 sum]("https://help.ubuntu.com/community/UbuntuHashes") for the version you downloaded, and [check whether or not the MD5 sum is correct]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows"). (I have had an instance where the download itself was corrupt.)
 
If that checks out, you need to check that the CD itself has burned correctly. When you boot the CD, hold down the Shift key. If you get a line saying "boot:"; just press Enter. You should get a menu asking for your language, then a list of options. Choose the one that says, "Check disc for defects".

Let us know what happens.

---

### Post by superchief on 2012-03-26
Hi Guys,

The boot CD worked on another pc just fine, i went down as far as version 8.04.

However the CD refused to work on this laptop....and then i did a network boot install of it.
It took a while to get going and working and there were a few learning curves to go around but finally there, got this laptop off xp and now on ubuntu.

Thanks guys

P.S I had to search around for the network boot installation instructions for ubuntu, are they anywhere easy to find or is it worth putting them on the install page because that information would have been very handy, just a suggestion, not an issue...and happy to know the laptop is working faster than ever.

---

### Post by mörgæs on 2012-03-26
Good that it worked. Please mark the thread 'solved'.

In general, if the latest Buntu is too slow it is not recommended to switch to older releases. It is far better to try the latest L/Xubuntu.

---

