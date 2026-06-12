---
title: "Ubuntu 6.06 to 6.10 upgrade using edgy.tar.gz problem"
date: 2021-12-04
forum: Installation &amp; Upgrades
---

### Post by ontpro623 on 2021-12-04
I'm trying to upgrade ubuntu 14.04 to 14.10 using the utopic.tar.gz extracted. It launches fine except that it edits the sources.list to match the one back in 2014, and the message which pops up says "third party sources disabled in your sources.list". Back then, it was then archive.ubuntu.com . The problem is that these releases are so old that they are moved back to the old-releases, and the upgrader does not know that. I am thinking there is SOME way to modify this, since the upgrade tool is being launched from a folder with all the other files which were extracted, so somewhere in there it contains the sources.list changer or whatever. I'm unsure how to fix this, because the alternate CDs were discontinued. I tried everything such as editing sources.list in the middle of the preparation stage to change archive to old-releases but it won't work and always gives an error.

**Please do not say "WHY ARE YOU UPGRADING AN OLD VERSION OF UBUNTU IT'S UNSAFE IT'S NOT GOOD GO TO A NEW ONE". Such comments will be disregarded and maybe be recommended for removal.**

---

### Post by mikewhatever on 2021-12-04
I don't know if we support the 6.xx or 14.xx releases here, as they are old and unsupported. It also looks like you are trying too hard to be vague.
It is easy to find how to change the sources and what to. That said, I'd not be surprised if the archives are long gone.

---

### Post by ontpro623 on 2021-12-04
If you have nothing helpful to say, then don't mention it. It wastes our time. I'm sorry if this was rude but you should read the entire post before commenting something.

---

### Post by coffeecat on 2021-12-04
> **ontpro623 said:**
> 
**Please do not say "WHY ARE YOU UPGRADING AN OLD VERSION OF UBUNTU IT'S UNSAFE IT'S NOT GOOD GO TO A NEW ONE". Such comments will be disregarded and maybe be recommended for removal.**

Hmmmm. [-(

Firstly: please do not try to moderate here. We have forum staff for that.

Secondly: forum members are free to give their advice whether you like it or not. Telling you that running an unsupported version of Ubuntu is unsafe would be excellent advice, which you would do well to heed.

Thirdly: If you "recommend removal" of any posts that which contain valid advice and which conform to the forum Code of Conduct, your "recommendation" will itself be disregarded by forum staff. 

Lastly: Although we do not have a formal forum policy disallowing support for EOL releases, we strongly discourage it except for certain rare use-cases, for example where someone needs to use an EOL release for research or educational purposes, or for running an obscure piece of software that will only install on an EOL release. *But in all cases we hope and expect that the user will act responsibly and not connect the system to the internet.* On this forum we have a responsibility to new users of Ubuntu, who constitute a significant part of our membership, to ensure that they are not influenced by bad practices, such as connecting an obsolete operating system to the internet. 

I will leave this thread open for now, if only to see and read comments from other forum members. Heaven knows, I need the entertainment. To all other forum members: please feel free to comment despite the OP's apparent resistance to being told that running old releases is a very bad idea.

---

### Post by grahammechanical on 2021-12-04
There is no need to shout. Your title does not match the content of your post. What are you running? Is it Ubuntu 6.06 or Ubuntu 14.04?

If you are running 14.04 you can get Extended Security Maintenance (ESM). It will extend the life of 14.04 up to April 2024. I do believe it is free for up to 3 machines. But do not take my word for that.

[https://ubuntu.com/blog/ubuntu-14-04-and-16-04-lifecycle-extended-to-ten-years](https://ubuntu.com/blog/ubuntu-14-04-and-16-04-lifecycle-extended-to-ten-years)

If you are indeed running Ubuntu 6.06, Dapper Drake and want to upgrade it to 6.10, Edgy Eft then You need to manually edit your sources.list file. This document shows you how.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Consider this example:

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse

In 6.06 the CODENAME would be "dapper." You must replace it with "edgy" for every repository and you have to record the http address as old-releases.ubuntu.com. You save the file and then run whatever update/upgrade manager Ubuntu had back in 6.06.

Regards

---

### Post by ontpro623 on 2021-12-04
Super sorry about the title. I had changed it but completely forgot the title

---

### Post by ontpro623 on 2021-12-04
Everyone who is replying: Ignore the title and focus on 14.04 to 14.10 only

---

### Post by MAFoElffen on 2021-12-04
Well.... No matter the version or the why... I'm sure you have your reasons. I can think of many, which some would be research, nostalgic practice, etc, etc...

My recommends, in my honest opinion, you are going about it wrong.. The repo's for the old releases are "http://[COLOR=#ff0000]old-releases.[/COLOR]ubuntu.com". Using the old Debian release upgrade method/techinique, you just change your target URL in your sources list to the new target URL and release, then update and upgrade...

Just a thought. It works for me...

---

### Post by DuckHook on 2021-12-04
Expanding on coffeecat's excellent comments:

[list=1]
[*]This is a recurring topic that crops up on this forum with depressing regularity. I posted on a similar thread three weeks ago. No point in rephrasing what was said then, so:> **DuckHook said:**
> …The main reason that Linux experiences less malware has little to do with its inherent robustness as an OS; it has far more to do with the fact that Linux users tend to be geeks and therefore are more security conscious to start with. The median Linux user is simply safer and better informed.

This advantage has traditionally kept the Linux ecosystem tighter and cleaner than proprietary ones. The benefits are: fewer bot farms, smaller attack surfaces, less demand for dangerous fluffware, better code auditing… the list is as long as my arm. These benefits are significant and far reaching.

But they are also fragile in the sense that they are dependent on Linux users continuing to practice good computing hygiene. When newbies or the misinformed drag their bad Windows habits into Linux, then say hello to Linux botfarms, c&c servers, ransomware nodes and the army of assorted nasties that have turned Windows into a malware cesspool.

I'm at the point where I no longer want foolish newbies or no&#8209;rules&#8209;for&#8209;me types piling into Linux if they insist on ignoring good practice and security hygiene. They pollute our entire ecosystem. And the two most important rules of good practice/hygiene are: never run anything EoL and update fast and furiously.

It's not that hard. Disputing this is like insisting that the earth is flat.
[*]Since you are attempting to network upgrade, it is self&#8209;evident that you are connecting your obsolete version to the Internet. I don't care if you are happy to be a danger to yourself. But your actions make you a danger to the rest of us. This makes your actions our business whether you like it or not.
[*]The only way to run an obsolete version with at least a modicum of safety is to disconnect yourself from the Internet.
[*]The best way to do this is to run the dead version in either a VM or a container like LXD in which ***the virtual NIC is disabled***.
[*]FWIW, I have a 12.04 version running on my box, but it is isolated within a LXD container with the NIC disabled. I also run a Win XP instance within a VM, again with the NIC disabled. Both of these OSes would be the equivalent of uncaged rabid animals if left connected to the Internet, and I would rightly be considered a menace to public computing. They are safe (and I am acting responsibly) only insofar as they are sandboxed nine ways to Sunday and completely isolated.
[/list]
You give no reason or background for your request. We can only hope that you are behaving responsibly and are not a menace to public computing.

---

### Post by T6&amp;sfpER35% on 2021-12-04
> If you have nothing helpful to say, then don't mention it

man .. go away

---

### Post by tea for one on 2021-12-04
> **coffeecat said:**
> Heaven knows, I need the entertainment.

Me too - I hope that this thread has legs.

The previous effort expired after 10 posts. [https://ubuntuforums.org/showthread.php?t=2469154](https://ubuntuforums.org/showthread.php?t=2469154)

---

### Post by QIII on 2021-12-05
I have closed the other thread.

I will show a little less forbearance than my colleagues with this thread.

Closed.

---

