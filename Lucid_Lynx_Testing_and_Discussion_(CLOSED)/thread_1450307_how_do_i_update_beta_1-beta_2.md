---
title: "how do i update beta 1-beta 2?"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by e1ektrob0y on 2010-04-08
So i'm using beta1 and i see that beta2 is released but i have no updates. i didn't want to do a clean install from beta 1 to beta 2. am i supposed to 
```
update-manager -d
``` to get the updates?

thanks...

---

### Post by descendent87 on 2010-04-08
If you're going to use the testing versions please at least read the stickies at the top of the forum

---

### Post by e1ektrob0y on 2010-04-08
I have been watching the stickies since yesterday waiting for the release of beta2, where someone mentioned all that is needed if your already running beta 1 is an update. I have read that in several places actually and it doesn't seem to be the case at the moment.

you've been REALLY helpful though, thanks a lot fella??????????????????????

---

### Post by Merk42 on 2010-04-08
descendent87 is probably referring to the [Ubuntu 10.04 Beta 2 Released - Read Before Testing!](http://ubuntuforums.org/showthread.php?t=1450110) which says:

> **23meg said:**
> ...[list]
[*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their pre-decided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install Beta 2**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. Refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for further details.[/list]...

emphasis in original source

---

### Post by VMC on 2010-04-08
> **e1ektrob0y said:**
> So i'm using beta1 and i see that beta2 is released but i have no updates. i didn't want to do a clean install from beta 1 to beta 2. am i supposed to 
```
update-manager -d
``` to get the updates?

thanks...

If you have been updating since beta1 and there are no more updates, then your at the beta2 level. An if you keep updating, eventually you'll arrive at the RELEASE level, once it has been released.

One word of caution, though. Since your using ```
update-manager -d
```, make sure you don't try partial upgrades until you understand this [thread]("http://ubuntuforums.org/showthread.php?t=1343434").

---

### Post by Didius Falco on 2010-04-08
I'd suggest using the terminal and using this command:

```
sudo aptitude -q update && sudo aptitude -q safe-upgrade
```

This will prevent partial upgrades, which are a major problem-causer.

Regards,

Didius

---

### Post by e1ektrob0y on 2010-04-08
thankyou very much Merk42 and VMC :) my question is answered...and it was that easy...

---

### Post by ranch hand on 2010-04-08
You have to realize that the freze for this release was on the 1st of the month;

[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

If you think back you will realize there have been very few update since that time.

The ISO needs tested (the sticky for that has been removed as we are done with that test).  There can be no large changes to the content for the testing to be good.

Then the image itself needs double checked (32bit CD and 64bit DVD) the website built and deployed.

All this for the same information you had a week ago.

We will do it all again in a couple of weeks.

---

### Post by egalvan on 2010-04-08
> **e1ektrob0y said:**
> I have been watching the stickies since yesterday waiting for the release of beta2, where someone mentioned all that is needed if your already running beta 1 is an update. I have read that in several places actually and it doesn't seem to be the case at the moment.

**you've been REALLY helpful** though, thanks a lot fella??????????????????????

And since **you've been REALLY watching **the stickies,
then I'm sure you saw this?????????????????????

Direct quote from the  FAQ
[I]
[B]I haven't been getting updates for a while. Is it that there's nothing new in Lucid, or is there a problem with the servers?

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).[/B]
[/I]

Have you checked YOUR mirror?

---

### Post by e1ektrob0y on 2010-04-08
> **egalvan said:**
> 

Have you checked YOUR mirror?

HELP!! I'm being attacked :O just relax man. it was a simple question that had a simple answer. now the thread is solved. what is it that you are trying to prove?

---

### Post by atlee on 2010-04-09
> **egalvan said:**
> And since **you've been REALLY watching **the stickies,
then I'm sure you saw this?????????????????????

Direct quote from the  FAQ
[I]
[B]I haven't been getting updates for a while. Is it that there's nothing new in Lucid, or is there a problem with the servers?

The archive mirror you're using is probably lagging behind. You can see the status of the mirrors at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).[/B]
[/I]

Have you checked YOUR mirror?

I would also say chill it man, don't pick on the aussie guy, hes asking a simple question that requires a simple answer and not a back chatting answer. @Elgavan do you always read the small black writing on all your contracts word for word? i know you don't so simple theory answered.

---

### Post by descendent87 on 2010-04-09
> **e1ektrob0y said:**
> I have been watching the stickies since yesterday waiting for the release of beta2, where someone mentioned all that is needed if your already running beta 1 is an update. I have read that in several places actually and it doesn't seem to be the case at the moment.

you've been REALLY helpful though, thanks a lot fella??????????????????????

Sorry wasn't meaning to get at you but this question has been asked 100's of times recently & 23meg has answered nearly every common question about using testing releases and stickied them but seems nobody reads them before asking the same questions.

---

### Post by dcstar on 2010-04-09
> **egalvan said:**
> 
.........
Have you checked YOUR mirror?

Yeah, every time I back the car out of the driveway........     :popcorn:

---

### Post by atlee on 2010-04-09
> **descendent87 said:**
> Sorry wasn't meaning to get at you but this question has been asked 100's of times recently & 23meg has answered nearly every common question about using testing releases and stickied them but seems nobody reads them before asking the same questions.

This is meant to be a friendly open minded forum, all i have seen in the past few days is peoples rudeness with replies, changing titles of peoples threads and closing and deleting threads without notice when they are normal topics that needs answers, not everyone here is a tech head with Linux, most Linux people choose Ubuntu because it's one of the easiest to manage and setup.

---

### Post by ranch hand on 2010-04-09
> **atlee said:**
> This is meant to be a friendly open minded forum, all i have seen in the past few days is peoples rudeness with replies, changing titles of peoples threads and closing and deleting threads without notice when they are normal topics that needs answers, not everyone here is a tech head with Linux, most Linux people choose Ubuntu because it's one of the easiest to manage and setup.
Every thing that you say is true.  It is also true that we were all, at one time noobs.  I am a noob.

This is my second testing cycle.

One thing to keep in mind is that some of us have been at this since the first week of November.

Others are just coming on and some seem to think they need to arrange a "pecking order".

This is silly.  It does, however, make all of us a little cranky.  Which is also silly.

There are some things that all of us should read or re-read no occasion.  One is the stickies in the ABT forum on how to behave, research, and ask questions.  The other are all the stickies on this forum.

They are well written and insightful.  Full of very useful information.

These are things that folks new to this forum and folks in the forum need to keep in mind.

Those in the forum, particularly experienced folk, should also think back on the kind of questions they asked when they first started in Linux and how helpful others were in spite of it.

---

### Post by zenarcher on 2010-04-09
Well said, ranch hand.

Cheers,
zenarcher

---

### Post by Johnsie on 2010-04-09
Be nice people

---

### Post by jp_coll2003 on 2010-04-09
The point being people, is that anyone who asks simple questions about updating on a beta should not really be using a beta ?? Just my own thoughts and no disrespect to anyone new or not.

---

### Post by Muflon on 2010-04-09
> **jp_coll2003 said:**
> The point being people, is that anyone who asks simple questions about updating on a beta should not really be using a beta ?? Just my own thoughts and no disrespect to anyone new or not.

If you don't ask you don't learn.

Muflon

---

### Post by Uncle Spellbinder on 2010-04-09
The only stupid question is the one not asked.

---

### Post by ezsit on 2010-04-09
> The only stupid question is the one not asked. 

I would rephrase this as: "there are no stupid questions, just stupid contexts." Meaning, if someone asks a question and the answer is posted in an obvious place, then the questioner appears stupid for asking that question in that context.

I am a librarian, and I am sure people who work in retail can relate to this. I work at a reference desk, with signage above the desk stating that this is the REFERENCE DESK. 

Everyday people come up to the desk and ask: "Is this the Reference Desk?" 

Now, the question is not stupid, but when asked while standing directly below a sign indicating the answer, the questioner appears incredibly stupid.

---

