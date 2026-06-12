---
title: "What could be improved in the testing and contribution stickies?"
date: 2008-06-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 23meg on 2008-06-11
Those of you who frequented the Hardy development / testing forum may recall the following two sticky threads:

[How To Test Hardy, File Bugs and Repair Breakage]("http://ubuntuforums.org/showthread.php?t=600644")
[Contribute To Hardy!]("http://ubuntuforums.org/showthread.php?t=603316")

Since we're entering the phase in the development of Intrepid in which testing and other forms of contribution from the forums community is going to be meaningful, I'm preparing to post "Intrepid versions" of those.

Before I do that, I'd like those of you who read them to take a look back at them and tell me what could be improved. Did you benefit from these guides at all? What information is missing that you think should be there? Is there anything that's factually wrong which should be corrected? Is there anything that you think is absolutely unneeded and is just taking up space and confusing people? Do you think the two thread scheme is good, or should there be more or less threads, possibly with a different organization? And why?

I do have a list of suggestions and some mental notes from the last cycle regarding things that should be added, but now is probably a good time to hear the feedback altogether in one place once more. Please think in terms of the benefits the changes you suggest will bring to the wider community of testers rather than just yourself, and if only stating a personal preference, please provide reasoning.

---

### Post by olskar on 2008-06-11
The only thing I can think of is perhaps a little info about OpenPGP keys, how and why to get those and perhaps something about the Code of conduct. That is my suggestions but I do not know if it fits in those threads, its up to you to decide :)

Edit: And perhaps something so easy as a little bit more air/space in the text, makes it easier to read

---

### Post by psyke83 on 2008-06-11
23meg,

Your guides are excellent; unfortunately I don't think many users will read them fully before upgrading (or posting). I have some small suggestions that may (or may not) help:

1. Put the actual instructions on how to upgrade to the development release as the *final* step in your guide. Do not indicate at the start of the guide where to find these instructions; let readers naturally discover it. This will hopefully improve the chances of new users reading the prerequisites about package breakage, etc., before upgrading.

2. Try to discourage use of update-manager for daily updates. It's my opinion that the interface is non-intuitive regarding "Partial Upgrade" scenarios, leading the user to believe that you can only perform a partial upgrade, or none at all (when in fact there is a third, non-intuitive answer). Also, they will not learn why packages get held back as they do not have access to the verbose output from apt-get or aptitude.

3. Take a look at this section:

> When upgrading to the latest state of Hardy, if you note that APT is reporting packages being held back or removed, this is completely normal. Developers work only on source packages locally; once a source package is uploaded, it takes a certain amount of time for it to be picked up by the build daemons, built, and placed into the archive. At certain times, dependencies of certain packages can't be satisfied, simply because they haven't been built and placed in the archive at the time. In the early stages of development, do not file bugs about missing dependencies and packages."

I think it would be better to use more explicit language. You need to emphasize to users that it is not safe to perform a "Partial Upgrade" or "dist-upgrade" unless they are absolutely certain it will remove obsolete packages. Many users will adopt a daily habit of using "dist-upgrade", and such behaviour can result in a broken system, especially on a day when several interdependent packages are getting built/uploaded over a wide timespan.

4. This is not a comment specifically for the content of your stickies, but how they are referred to in the forum.

I have been a little downhearted to see multiple threads occur asking the same questions in different ways, when a) the answer is often contained in an older thread that was not checked by the user, and b) the answer should be obvious to someone that read the sticky threads and did some minimum research before upgrading to the development release.

To this end, I would suggest that if a user asks a question such as "why is package X held back?", instead of giving them the specific reason for that case, refer them to the sticky to give them the means to find out the answer for themselves. That will hopefully encourage users to understand the development process better and prevent them coming back the next day asking the same question about package Y.

Thanks for all your hard work, it is much appreciated!

---

### Post by ronacc on 2008-06-11
You have things nicely covered in those stickeys , I only have two sugestions , 1 and a request to the "how to test" that people use the "search this forum" dropdown to see if their issue is already being discussed . 2 as the forum becomes more active watch what is generating multiple threads and add a "common issues" sticky dealing with them . now if we can only get people to read the stickes especialy the "warning" :)

---

### Post by lonniehenry on 2008-06-11
23meg,  thank you for all of your great instructions over the years.  I feel that your instructions lead right to the heart of the problem and the solution.  That said, try to emphasize that the entire sticky needs to be read before doing any updates, upgrades, testing.  Most of the problems that people have are caused by their lack of understanding of the process.  You give clear instuctions, but they don't read them thoroughly. Referring problems to the right parts of the sticky will maybe help users to read them more carefully. 
Thank you for your service to the forums.

---

### Post by Raptor45 on 2008-06-11
I definitely think its important to stress NOT doing dist-upgrades and partial upgrades. As stated before, a large number of testers seem to get into the habit of simply doing them whenever the notice comes up, without knowing to check what is being affected.

---

### Post by autocrosser on 2008-06-11
I really value your help & contributions over the years--I agree with several of the above points--

Stress that partial-upgrade & Dist-upgrade are not the best method--The prospective tester should be able to look at packages & make a "good" informed choice.

As for "Prospective tester"--it sure would be nice to have a "test" to insure that the "tester" is really able to test a new release---not just create noise on the forum :roll: (I think we all know about that kind of user--note: wishful thinking!!!)

Now back on-topic :) Maybe a way to "force" someone to really read the sticky before he/she can post to the forum?

More moderator checking to decrease "noise"

psyke83's first suggestion--reformat in a way to promote the "prospective tester" to really read the info before enabling him/her with ways to test.

olskar's comment about the Code of Conduct--maybe only people that have read/signed a release of some kind can post?

We as a group really need to find ways to be more productive & help the Dev's meet their mission goals--I try to be as active as my time allows......And I try to stay on topic as much as possible whilst having fun with everyone here. I really enjoy doing this & find my time here well-spent--with a great group of people!!!!:biggrin:

---

### Post by caryb on 2008-06-12
I would like to see a sticky that is dynamic with up & coming changes & time lines, I.E. package x is in the repo's but will break Y it is envisaged that this will be fixed by the 20th June etc. I think some feedback from the devs will go a long way to stop the animosity to long term breakages if it is known that it will happen. 

I don't know if this is possible but it would put us on the same page.


Cary

---

### Post by plun on 2008-06-12
- Making a thread sticky among normal threads would be great.
10 "break threads" about the same is too much.

- Invite devs to communication threads about challengies.

I think it was "jwaltonen" which came in about Gnome-gvfs during Hardy and
it was great.


- Use an icon for the must read thread about testing.


*Intrepid Ibex Testing and Discu**_sss_**ion *

Well, my english but 3 s  ........

---

### Post by psyke83 on 2008-06-12
> **caryb said:**
> I would like to see a sticky that is dynamic with up & coming changes & time lines, I.E. package x is in the repo's but will break Y it is envisaged that this will be fixed by the 20th June etc. I think some feedback from the devs will go a long way to stop the animosity to long term breakages if it is known that it will happen.

I honestly think that's a bad idea, because it won't address the problem of users blindly doing a dist-upgrade or partial upgrade. During the development release, held-back and uninstallable packages will be a daily occurrence. Users don't need to be told "don't upgrade evolution-data-server, as a required update to evolution-common has not been uploaded yet", they need to read the stickies, learn the development process and understand why it's bad to allow critical packages to be uninstalled in the first place!

However, keeping users updated to specific packaging bugs is a good idea, such as a recent problem in which debconf failed to upgrade unless findutils was upgraded first (see [here]("http://ubuntuforums.org/showthread.php?t=814169")); such a scenario is a good candidate for a "daily issues" sticky.

---

### Post by philinux on 2008-06-12
During Hardy testing I thought the stickies were excellent.

As long as people read em.

Also add to the scary warning  - advise people to use a spare machine or a dual boot, or virtualbox.

---

### Post by Gina on 2008-06-15
Is dual boot safe though?  I read of a couple of testers who lost data from other partitions.  I don't know enough about virtualbox to know if this approach is completely safe (in a perfect world it would be but...) I use a separate machine and would definitely recommend that.

Before I go, I would like to add my thanks and congratulations to 23meg for a great contribution to these forums :)

---

### Post by philinux on 2008-06-15
> **Gina said:**
> Is dual boot safe though?  I read of a couple of testers who lost data from other partitions.  I don't know enough about virtualbox to know if this approach is completely safe (in a perfect world it would be but...) I use a separate machine and would definitely recommend that.

Before I go, I would like to add my thanks and congratulations to 23meg for a great contribution to these forums :)

Virtualbox is completely safe the only thing thats missing is accelerated graphics. Dual booting should be too.

---

### Post by Gina on 2008-06-15
I know dual boot ***should*** be safe but I thought I read of at least a couple of testers for whom it wasn't.  As I see it, there is a small but finite possibility that any other file system that is visible could be written to by rogue software.  My experience of software development is that very nasty bugs can creep in.

Should add - I remember the stickies when we started testing Hardy but thought I'd go and check in case I could add any suggestions but I can't find them now.  The stickies in the Hardy development forum changed.

---

### Post by psyke83 on 2008-06-15
> **Gina said:**
> I know dual boot ***should*** be safe but I thought I read of at least a couple of testers for whom it wasn't.  As I see it, there is a small but finite possibility that any other file system that is visible could be written to by rogue software.  My experience of software development is that very nasty bugs can creep in.

You're absolutely right. I tend to take risks with a dual-boot configuration for the development release, but you can't rule out the possibility of an installer/partitioning bug. 

I suppose a dist-upgrade from Hardy is less risky, however, as no partitioning should take place...

---

### Post by ronacc on 2008-06-15
a seperate machine used only for testing is the only safe way .I have twice had the installer/partitioner take the whole drive when it was told to take only a specific partition , and a couple of people during hardy developement reported having every drive in their box wiped .I test only on a dedicated test box .It is rare but could be disasterous for the unprepared .

---

### Post by psyke83 on 2008-06-16
I saw something else in your sticky thread that can cause problems:
> 
**Manual Upgrade**

[LIST]
[*]Open your /etc/apt/sources.list file with a text editor, replace all instances of "gutsy" with "hardy", and save the file
[*]Issue "sudo apt-get update && sudo apt-get dist-upgrade" and wait for the packages to be downloaded and changes to be applied
[*]Reboot
[/LIST]


This advice works only if the repository is in a consistent state at the exact moment a user attempts to perform a dist-upgrade. In fact, I think we can only guarantee this upgrade method with any degree of certainty when moving from stable release to stable release (i.e. when the repository has settled), which is not the case during the development process.

This gives you all the more incentive to put the upgrade instructions as the last step in the sticky, and make sure users understand why vital packages can get uninstalled as part of a dist-upgrade or Partial Upgrade - and why it should be avoided - before upgrading.

Yes, we need to test the robustness of packages when dist-upgrading, but only within a reasonable scope. When the dist-upgrade process causes vital packages to get removed due to unfulfilled dependencies, it's not a bug. It's user error.

---

### Post by Gina on 2008-06-16
Yes, carefully read the text on the screen and if it says "... not upgraded" or "... packages will be removed" beware and don't say "Y"es to the proceed question where there are packages not upgraded or if you're not certain any packages to remove are replaced by new ones.  I think that could be put better but I think you'll get the message :lol:

---

### Post by ronacc on 2008-06-16
a simple way of saying it is  " when in doubt don't " .

---

