---
title: "ubuntu karmic and updating."
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LunaticHiatus on 2009-10-21
I'm currently trying to do a partial upgrade of ubuntu karmic and I get something along the lines of that I am not connected to the internet. Yet i know I am. I tried to upgrade wirelessly and while plugged in. Same error. Whats going on?

---

### Post by mick222 on 2009-10-21
read the sticky on karmic it advises not to do partial update.

---

### Post by lovinglinux on 2009-10-21
> **mick222 said:**
> read the sticky on karmic it advises not to do partial update.

+1

Better place to talk about Karmic issues is [Karmic Koala Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=359) forum.

---

### Post by 3rdalbum on 2009-10-21
Your local mirror might not actually have all the files yet, which is causing some file requests to get a "404 not found" response.

Try switching to the main Ubuntu server for your updates, at least until release.

---

### Post by anewman on 2009-10-22
> **mick222 said:**
> read the sticky on karmic it advises not to do partial update.

All very good reading that *after* we have been given the prompt, which says the complete opposite if you have actually read it.

---

### Post by qamelian on 2009-10-22
> **anewman said:**
> All very good reading that *after* we have been given the prompt, which says the complete opposite if you have actually read it.
I have read the prompt. It doesn't instruct you to do a partial upgrade, it offers to let you do one. Unfortunately, it makes the offer assuming more knowledge of what a partial upgrade might entail than is necessarily realistic in every case.

---

### Post by flipper9 on 2009-10-22
> **qamelian said:**
> I have read the prompt. It doesn't instruct you to do a partial upgrade, it offers to let you do one. Unfortunately, it makes the offer assuming more knowledge of what a partial upgrade might entail than is necessarily realistic in every case.

This was brought up in the sticky thread.  The general answer from geeks (and I'm one myself) is that we don't really care about the home user as we're geeks.  LOL 

Seriously though, we need to either make that an "advanced" or hidden option from a decidedly non-advanced user tool that Update Manager is or at the very least explain what a partial upgrade is and what the consequences are (either through a HELP button or some mechanism).

---

### Post by qamelian on 2009-10-22
> **flipper9 said:**
> This was brought up in the sticky thread.  The general answer from geeks (and I'm one myself) is that we don't really care about the home user as we're geeks.  LOL 

Seriously though, we need to either make that an "advanced" or hidden option from a decidedly non-advanced user tool that Update Manager is or at the very least explain what a partial upgrade is and what the consequences are (either through a HELP button or some mechanism).

I do care about the home-user, but the answer is to educate them, not baby them.

---

### Post by flipper9 on 2009-10-22
You'll find that "seasoned" users don't care about "non-seasoned" users and choose to blame them for when things go wrong.  Which is fine, but self-reflection about how the system is designed would be in order instead of blaming others.  This kind of attitude is what keeps Linux as a whole in the position it is in today.  It neglects the middle-user (the "power user") that has enough knowledge to do wonderful things with technology, but not the extreme expertise of years of experience.

---

### Post by philinux on 2009-10-22
Has anybody ever seen a partial update once a release goes live?

I've been ubuntuing for 2.5 years now and I've never seen one offered.

---

### Post by ptn107 on 2009-10-22
> **philinux said:**
> Has anybody ever seen a partial update once a release goes live?

I've been ubuntuing for 2.5 years now and I've never seen one offered.

You hit the nail on the head.  Updates offered to stable Ubuntu releases will NEVER trigger a partial upgrade.

---

### Post by 23meg on 2009-10-22
> **flipper9 said:**
> This was brought up in the sticky thread.  The general answer from geeks (and I'm one myself) is that we don't really care about the home user as we're geeks.  LOL 


Nobody ever said that.

---

### Post by flipper9 on 2009-10-22
> **23meg said:**
> Nobody ever said that.

Well, I have to respectfully disagree.  There seems to be a lot of forgetting about the regular end-user, blaming them for not reading and now knowing better, and basically dismissing any issues that are brought up that "seasoned" users already know about.  

My goal is to encourage people to move from Windows to Ubuntu/Linux, and even Mac Os for that matter.  We need to focus on the end-user, what they want, and make it happen without losing the ability to have a powerful system that we "geeks" can hack to our hearts content.  I think Ubuntu goes a long way towards that goal; hence why I use it not to mention that I like the features and capabilities it has.

I think Microsoft is finally "getting" that idea, and Apple has had that for quite awhile.  Just look at how polished Win7 and Mac OsX are.  They just work.  People are happy and use them.  Where is Ubuntu right now?  We're becoming more popular, but how can we do better?  Remember the ignorant end-user, the lazy end-user, the end-user that won't read directions, the end-user that is not willing to Google/Troubleshoot/Fix things with the terminal/etc.

---

### Post by 23meg on 2009-10-22
The "end-user", as you define her, shouldn't be running a pre-release version of Ubuntu. There's no point in that. All the criticism you seem to misinterpret as "forgetting about the end user" is directed at people running the development branch without knowing and making an attempt to learn the essential good practices, not at the "end user" that stable releases of Ubuntu is aimed at. 

You should bear in mind that the "geeks" who test the development branch, and help others do so, are expending a volunteer effort to sort out problems before the release is deemed stable and reaches the "end user", so that the "end user" doesn't have to suffer from those problems.

---

### Post by flipper9 on 2009-10-22
It's more than just development releases.  This concerns also bug reporting, regular updating, anything about the system.  The RC is out, said to be stable for general use...but if people start having problems, people will say "well...you should have googled the problem, read the release notes, should have known better...", etc..  We just have to assume that the 99% of other users that are currently using Windows/Mac as they start to use Ubuntu aren't going to follow the rules about bug reporting, reading HOWTO manuals, and trying to figure out how to use their system.  That's what I think is holding back Linux (and by proxy Ubuntu) from getting a stronger foothold.

Right, and I'm a "geek" myself that can deal with the problems.  I'm just trying to point out areas where we can improve.  I appreciate all the hard work that people put into OSS and Ubuntu in particular.  Just trying to be a voice to help improve and move us forward.

---

### Post by ranch hand on 2009-10-22
This is not a lack of caring.  I have read your posts.  I believe that you have a lot more experience with Linux than I do.

My join date is before I ever installed Hardy, my very first use of any Linux.  I did research and then asked a lot of really stupid questions.  I also got an internal USR5610c fax modem working with the help of very experienced people on these forums.  Seeing that nothing except "lspci" would find the modem it was a little challenging.  I did not blame Ubuntu for this.

I knew there was going to be problems and people told me to go with a USB modem but I stuck with the internal.  I could hook up to dial up tomorrow and it would work.

There are a few things you have to take on your self.  This is called being an independent human being.  It is YOUR box.

[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

The above is the release notes for the RC.

That link is from;

[https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000126.html](https://lists.ubuntu.com/archives/ubuntu-announce/2009-October/000126.html)

These are not put out by people that do not care.  They are put out by busy people who do care.  They also realize that YOU do not have to read any of it.  That is YOUR choice not to care what you are doing and then blame someone for not telling you.

Here is an alternative to having these problems;
A> Use a stable release.

B> Go to this link and buy it, I am sure that it is great, better, for instance than the "support" that came with this box from Dell.
[http://shop.canonical.com/product_info.php?products_id=528](http://shop.canonical.com/product_info.php?products_id=528)

Seems like a reasonable price too.

All this information is out there.  The user needs to cowboy up and make a hand, as they say here.

---

