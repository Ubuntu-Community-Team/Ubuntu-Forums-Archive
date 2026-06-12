---
title: "Expert vs Regular"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by jones_jj on 2005-07-25
I was wondering what is the differences between expert mode installation and regular (a few user interaction) installation.

One difference that I see is in expert mode you are asked to add root password and in the regular installation you are never asked to add a root password.  Another difference that I have noticed when I have done an expert and a regular install the expert install after the install is complete and you log-in and and you go to the System/Administration menu and you go to say Users and Groups it will ask you for a password, I'm assuming it is the root password, but it gives and error:  failed to run users-admin...So then when I try it again using my username it gives the same error.  But when I do the regular install I never see this error.  I will just use my username's password and all is good.

Why does something like this happen when using expert installation mode vs. the regular installation mode?  I would think the expert installation mode would be similar to the regular installation mode except for you are given more control when doing it in expert mode.  Does it have something to do with the fact that you add root password and a regular user in expert mode that throws off permissions for doing normal admin tasks as a normal user?

Thanks for the help and feedback

---

### Post by Natja on 2005-07-25
Hi,

I _suppose_ that when you install Ubuntu in expert mode, the user you create during installating is _not_ added to sudoers. Try adding this user to sudoers, it should work

---

### Post by jones_jj on 2005-07-25
How would I go about adding it to sudoers?

---

### Post by az on 2005-07-25
Is there a bug in bugzilla about this?

bugzilla.ubuntu.com

If there is not, perhaps you should file one.   Or at least ask on the developmental mailing list.

If you are in the process of installing and reinstalling to play around, you should try the latest Breezy install cd to see if this phenomenon still happens before taking it to the devel mailing list.


Anyway, the expert mode is only there if you have problem with the default automated install.  There is no "advantage" to using an expert install, otherwise.

Now, a custom "server" install is different.  It just gives you a bare system and you chose what packages to run.  You need to be a bigger expert to do that, instead of just answering a few more questions during the install.

---

### Post by Natja on 2005-07-25
Try following this thread : [http://ubuntuforums.org/showthread.php?t=33084&highlight=sudo+add](http://ubuntuforums.org/showthread.php?t=33084&highlight=sudo+add)

It should help you fixing your problem.

As Azz said, you should look on [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) if this problem is already filed. If not, you should report it

---

### Post by jones_jj on 2005-07-25
Thanks I will have to look at bugzilla to see if anyone else is having any of the same issues that I'm having or not.  I will also have to try and add my username to the sudoers file and hopefully that will fix things.  Thanks again. :-)

---

### Post by jones_jj on 2005-07-26
I just wanted to let everyone know that I finally figured everything out after puzzling through it for a little while.  I did an expert mode so that I could have a bit more control, and I just had to add my username to the sudoers file and all is good in the little land of Ubuntu.  Next task is trying to learn how to do a little bit more on the security side.  I am more use to how RedHat does things, so this will take a little time to get use to.  I will probably post more questions when I have them...luck you guys.    :)   Thanks

---

