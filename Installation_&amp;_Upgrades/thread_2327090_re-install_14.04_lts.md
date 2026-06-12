---
title: "re-install 14.04 lts"
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by AlyssaVS on 2016-06-07
I would like to re-install 14.04 on a system that already has 14.04 dual partitioned with windows 7. Can someone give me the steps to do this safely? I am hoping I won't have to touch the windows side if possible, everything is working fine there.

Thank you in advance for your time.

---

### Post by ajgreeny on 2016-06-07
Do as you did before when you installed but this time it is **very important** that you choose the "Something Else" option at partitioning stage.

That will show you all the current partitions on your system and allow you to find the Ubuntu partition(s).
By default Ubuntu installs with just a root partition /, and a /swap partition, but if you customised your first installation with a separate /home partition you will need to make sure that the old home is used again and has mountpoint /home but is not formatted.

have a look at [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) but scroll about a third of the way down the page for the detail of installing the system.

I hope that helps, but come back with more questions if you need more clarification.

---

### Post by AlyssaVS on 2016-06-07
Thank you! I will do this.

---

### Post by AlyssaVS on 2016-06-07
Since I do have just the two (root and swap) partitions set up should I format or not?

---

### Post by ajgreeny on 2016-06-08
The answer to that may depend on the reason for your reinstall; was something amiss in the original OS, or is there some other reason for reinstalling?

I have never done so but it is possible to install one OS over another without formatting the partitions by unticking the Format box in the partition list when you reuse them in the Something Else operation.  In theory that means that your personal files in your old home will be untouched, but **DO NOT DEPEND UPON THAT**, make sure you have backups in case it all goes to worms.

I have a separate /home partition but even with that being left untouched when I reinstall or do a distro upgrade, eg from 14.04 now to 16.04 in future, I do make sure to keep regular backups of all my /home; so far I have never needed it in 11 years of Ubuntu except when moving from an old machine to a new one, but you bet your life, if I missed making the backups, that's when it would all go wrong!

If you decide to try doing things that way make sure to let us know how it works for you.

---

### Post by AlyssaVS on 2016-06-09
> **ajgreeny said:**
> The answer to that may depend on the reason for your reinstall; was something amiss in the original OS, or is there some other reason for reinstalling?

I have never done so but it is possible to install one OS over another without formatting the partitions by unticking the Format box in the partition list when you reuse them in the Something Else operation.  In theory that means that your personal files in your old home will be untouched, but **DO NOT DEPEND UPON THAT**, make sure you have backups in case it all goes to worms.

I have a separate /home partition but even with that being left untouched when I reinstall or do a distro upgrade, eg from 14.04 now to 16.04 in future, I do make sure to keep regular backups of all my /home; so far I have never needed it in 11 years of Ubuntu except when moving from an old machine to a new one, but you bet your life, if I missed making the backups, that's when it would all go wrong!

If you decide to try doing things that way make sure to let us know how it works for you.

I am reinstalling because of a problem I had trying to get my desktop to display ubuntu correctly with this new monitor (works fine with Windows 7, attached to smart tv). A last ditch effort. I actually posted some questions about that several weeks back. I could only boot in recovery mode to get it to display correctly and every time I attempted to update I got an error message saying "failed to download package files". 

Changing the update server didn't work. Using the commands "sudo apt-get update" and "sudo apt-get upgrade" didn't work. I tried several troubleshooting options recommended here but nothing worked. (I'd copy/paste them but I don't see the thread anymore).

I am now having the same problem again after a couple of re-installation attempts. I went with the option of not formatting since I was unsure. At first everything displays fine. And then it updates and reverts back to the initial problem... zoomed way in. Everything is backed up on an external drive. I am considering a re-install with formatting now since that didn't work. I am also considering trying a different desktop environment or different distro altogether, but am unsure if it would make a difference with an issue like this.

Any thoughts would be much appreciated! Oh , and I am currently typing this on the Windows side... :(

---

### Post by ajgreeny on 2016-06-10
[http://ubuntuforums.org/showthread.php?t=2319625](http://ubuntuforums.org/showthread.php?t=2319625)

Is that the thread you are talking about?  It looks like it might be, but if so I'm not sure I can help you further; that thread got a bit mixed up and started with a resolution problem, not solved and ended with a wifi or update problem, also not solved.

One problem per thread please or you will find people give up on their attempts to help.

---

### Post by AlyssaVS on 2016-06-10
I understand. I will refrain from mentioning other issues while attempting to get help. If I recall I simply asked for the name of few examples of a product and didn't realize it would be taken as a "problem." And then a moderator stepped in and made it a new thread. Just FYI, sometimes to the casual user there is one thing happening to them that has multiple parts. It is not always obvious that they need to begin a whole new thread. 

And here I was only mentioning it because you specifically said that the answer depended on why I was re-installing. I wasn't asking you to solve the earlier problem. I was asking about re-installing a new OS or desktop because of the problem I described. You asked me why I was reinstalling. This is frustrating!!!!!

---

### Post by ajgreeny on 2016-06-11
I asked why you were reinstalling because it could have been totally pointless if there was a hardware problem of some sort that needed solving.

I accept that it may seem strange to you not to try and sort out all the problems you have in a single thread, but as I say, it can get very confusing for everybody if you do that and will usually make the solution to each much slower to achieve.

---

