---
title: "How to make upgrades less painful?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by shannon.jacobs on 2010-04-30
I want to support Ubuntu, and I want Ubuntu to succeed, but... Each of the recent upgrades has been more painful than the last one, and it seems like the same old problems are persisting. In Koala it was the sound cards, and though I've just started my struggles with the newest release, it is very obvious that the server-load problems are still there. Hey, you Ubuntu people don't have to invent BitTorrent technology, you just need to make it the transparent default.

Why do these problems persist? What can we do to improve the situation?

It seems to me that most of the problem is that Ubuntu's economic model is broken. They need more testing for new features, and the model needs to be funded so that the features which are added are tested thoroughly. I suggest that they need a system where we the users put our money where our mouths are, so to speak. We should be allowed to subscribe to a budget for proposed new features, where those budgets included sufficient testing. 

Actually, I used to be a professional programmer, but I don't want to program these days, even to help Ubuntu, because I know just how difficult and stressful it is to do program well. However, I'd be willing to put some money out to help improve Ubuntu--but I also want to know just what I'm buying into.

There are various ways this could be done, but here is a link about one version of [charity funding]("http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html") I was thinking of a while back. As it applies here, the Ubuntu foundation would act as the charity brokerage, and we would donate by buying charity shares in proposed features (including MORE testing).

[http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html](http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html)

---

### Post by wilee-nilee on 2010-04-30
I think we forget that very little of the manufactures of sound card....etc support open source, it is actually quite amazing what works in my opinion. 

Don't blame the OS when it may be a mixture of the small footprint of open source, and little or no support from manufacturers of hardware. And don't forget your on a forum that people come to fix problems so if all your reference point is from the UF you will not have a balanced view.

---

### Post by mistofeles on 2010-04-30
> **shannon.jacobs said:**
> I want to support Ubuntu, and I want Ubuntu to succeed, but... Each of the recent upgrades has been more painful than the last one, 

Here some comments about 10.04 installation.

**1**. **netbook** does not upgrade. Out of disk space (eeePC901).
  - Why doesn't it upgrade piece by piece. Make a list of programs in the HD, remove them and get new ones from the net following the list.

**2**.  **server installation:**
**2.1**. Please someone: Add a bell to the installation program so that the program notes the administrator every time it needs manual data.
**2.2**. in RC server version there was no Likewise-Open. The version which I installed with "apt-get install likewise-open", 5.4.0.24111 was so buggy that at the moment I'm reinstalling the base Ubuntu because of the damages are too large to be fixed manually. There is a lot more better version 5.4.0.7985 at LW pages. And even that seems to be pre-release and unsupportted.

Still I'm feeling that Likewise is the best thing that has happened to Linux in many years. Samba has become too complicated and the documentation is years behind.
Let's hope they keep strictly in mind, where LW and Samba is needed and don't try to make LW to answer every need man can invent.

---

### Post by movieman on 2010-04-30
> **mistofeles said:**
> Why doesn't it upgrade piece by piece. Make a list of programs in the HD, remove them and get new ones from the net following the list.

If you upgrade the programs and then remove the old ones, if something goes wrong in the middle you may be able to reboot and fix it. If you remove the old programs and then upgrade, if something goes wrong your SOL. Also, you couldn't then upgrade any program you had to run during the upgrade, since you'd have deleted it.

That said, I'm sure it could be smarter about disk usage to ensure it won't run out part-way through.

---

### Post by Herman on 2010-04-30
> I think we forget that very little of the manufactures of sound card....etc support open source, it is actually quite amazing what works in my opinion. 
I agree.

Butt ... I have sound some problems too, and but the strange thing is, my sound was working just peachy in Karmic and in pre-release versions of Lucid, but now that I have finally installed the newly released version, all of a sudden - no sound.

I'm not too worried about it at the moment because my goal for the time being is to tweak my OS for a fast boot time. Maybe the sound will be fixed in an update.

My best friend's computer was just at my place to be fixed, and we were able to get most of his problems solved except his sound in Karmic. He has sound in Hardy Heron but no sound in Karmic. We were waiting for this New release hoping that updating his Karmic to Lynx might fix it, but now I'm not so sure.

How come Ubuntu goes backwards? That's what I find hard to understand and hard to explain to my friends. If it was working before, it should keep working and maybe even be improved. I mean, someone must know how to do it if it was working in an older version. I understand that programmers are only human too.

I think the 'System'--'Administation'--'System Testing' is a good program and all I can suggest is that maybe more of us should be running these tests and submitting the results. Then at least developers wil be aware of what hardware we're using and which hardware we're having trouble with. 

We could work to make more people aware of the System Testing program, by reminding others who post in with problems to run a test and submit it. All we need is a launchpad account to submit our hardware tests.

EDIT: Hey, I finally was able to get my sound working, all I did was play around in 'sound preferences' a little more, and I think it was when I clicked on the 'Output volume slider that it suddenly started working. The Output volume slider had been set at about 50%, and just clicking on it was enough to do something to stimulate it and induce it to start working all of a sudden. ... Weird! ... , oh well, at least it works, I'm happy now. Maybe we'll be lucky with my friend's one too. :)

---

### Post by ssam on 2010-04-30
> **shannon.jacobs said:**
> I want to support Ubuntu, and I want Ubuntu to succeed, but... Each of the recent upgrades has been more painful than the last one, and it seems like the same old problems are persisting. In Koala it was the sound cards, and though I've just started my struggles with the newest release, it is very obvious that the server-load problems are still there. Hey, you Ubuntu people don't have to invent BitTorrent technology, you just need to make it the transparent default.

Why do these problems persist? What can we do to improve the situation?

It seems to me that most of the problem is that Ubuntu's economic model is broken. They need more testing for new features, and the model needs to be funded so that the features which are added are tested thoroughly. I suggest that they need a system where we the users put our money where our mouths are, so to speak. We should be allowed to subscribe to a budget for proposed new features, where those budgets included sufficient testing. 

Actually, I used to be a professional programmer, but I don't want to program these days, even to help Ubuntu, because I know just how difficult and stressful it is to do program well. However, I'd be willing to put some money out to help improve Ubuntu--but I also want to know just what I'm buying into.

There are various ways this could be done, but here is a link about one version of [charity funding]("http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html") I was thinking of a while back. As it applies here, the Ubuntu foundation would act as the charity brokerage, and we would donate by buying charity shares in proposed features (including MORE testing).

[http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html](http://eco-epistemology.blogspot.com/2009/11/economics-of-small-donors-reverse.html)

there is [http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations) or if you want to help a particular application, you can usually find a donate link on their site.

there has been quite a lot of work to make it very easy to jump in and fix bugs in ubuntu. there is groundcontrol that lets you check out the source code for a project, edit the code, and push the changes to a branch on you launchpad account.

---

