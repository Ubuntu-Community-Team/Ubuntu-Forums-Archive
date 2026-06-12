---
title: "How to perform minimal update (from 12.10 up to 13.04)"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by darekch on 2013-05-10
I want to update my Ubuntu (from 12.10 up to 13.04). Unfortunatly update-manager wants to install 162 **new** packages (vs update of 930 packages). Problem is I want minimal update and I don't want to install some of **new** packages, i.e. abiword, gnome-bluetooth etc. I did minimal installation of 12.10 to avoid packages that aren't necessery. How can I perform minimal update of my Ubuntu? I have Lubuntu 12.10. I also hope that minimal update would perform faster.
Here's similar question without an answer: [http://askubuntu.com/questions/151746/how-to-make-a-minimal-upgrade](http://askubuntu.com/questions/151746/how-to-make-a-minimal-upgrade)

---

### Post by Megaptera on 2013-05-10
Hi,
You're asking with about an 'in situ' upgrade from 12.10 to 13.04 - some people (me included!) have issues with upgrades rather than re-installs. I suggest backing up all your important docs, pics, vids etc to external media & then do a new minimal install of 13.04.

---

### Post by darekch on 2013-05-11
I never had problem with upgrade, if there was it was so minor that I don't remember. Reinstalling is not an option as there would be too much work to configure things again.

Anyone know the solution?

---

### Post by grahammechanical on 2013-05-11
What you want to do would be very risky in my opinion. The Upgrade process has worked out what libraries need to be replaced. You may find that some original applications will be broken because they do not work with the newer libraries. Believe me there are many code differences between 12.10 and 13.04.

Why do you want to upgrade to 13.04? You get enough support for 12.10 to get you to 14.04 but with 13.04 you will have to upgrade to 13.10 and then to 14.04 because 13.04 and 13.10 only have 9 months support. You will be doing a lot of upgrading over the next six months.

You could end up having to fresh install as the simplest way of fixing a broken installation

Regards.

---

### Post by darekch on 2013-05-12
> **grahammechanical said:**
> The Upgrade process has worked out what libraries need to be replaced.
Are you sure? If so why abiword wants to be installed? 

> **grahammechanical said:**
> Why do you want to upgrade to 13.04?
I want newest version of applications. With LTS version of Ubuntu I get only security fixes and not bug-fixes nor new versions with new features.

---

### Post by ibjsb4 on 2013-05-12
Do you have the meta package lubuntu-desktop installed?  If so, remove it then do an update/upgrade.

---

### Post by darekch on 2013-05-12
I don't have lubuntu-desktop installed. I also don't have abiword installed.

---

### Post by fantab on 2013-05-12
Do a clean install with [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).

---

### Post by Megaptera on 2013-05-13
> **darekch said:**
>  How can I perform minimal update of my Ubuntu? I have Lubuntu 12.10. I also hope that minimal update would perform faster.  

Could you clarify please? Is it Ubuntu or Lubuntu you're asking about? Thanks :)

---

### Post by darekch on 2013-05-18
I was talking about Lubuntu.

I performed an update through update-manager so this is unimportant now.

---

### Post by ibjsb4 on 2013-05-18
> **darekch said:**
> I performed an update through update-manager so this is unimportant now.

Then please mark your thread solved

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by darekch on 2013-05-18
Hmm... but to be precise I didn't resolve the problem - I didn't perform minimal update. I just did update and all packages were installed. Now what I can do is to uninstall them manually (what I partially did). Thus I'm not sure if it's good think to mark this as solved.

---

