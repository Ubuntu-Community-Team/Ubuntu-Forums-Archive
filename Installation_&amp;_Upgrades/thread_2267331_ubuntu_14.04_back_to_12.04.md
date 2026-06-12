---
title: "ubuntu 14.04 back to 12.04"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2015-02-28
I helped a friend (total beginner) with her laptop. Installed ubuntu 12.04 and everything worked great. She upgraded to 14.04 (thought she was just doing update) and now there are system problems. Myself, I am old school and always do fresh install... no upgrades, ect. For now, I would really like to get her back to 12.04 until I'm ready to do fresh install of 14.04. Is this simple or do I have to start all over?

---

### Post by Bucky Ball on 2015-02-28
You have to start over with a clean install of 12.04 LTS. You could do a clean install of 14.04 LTS and see if that fixes the issue (something may have gone wrong with the in-box upgrade). 14.04 LTS is supported until 2019, 12.04 til 2017. Good luck.

---

### Post by acefromspace on 2015-03-01
OK, disregard this thread... looked around and she really messed things up! Got into file system. I have learned a lession from this. The first thing you teach a beginner is what NOT to do. I like helping people and getting them to try lynux, but I need to write some basic guidelines (in layman terms) to explain a few things. For now, I'm going to tell her that after she logs on, she should not need to use her password again... that means you are messing with something you don't need to be doing. I need suggestions for beginners... what not to do. Would it be easier to setup so she doesn't need password to login, but don't tell her the password so she can't do much damage?

---

### Post by Bucky Ball on 2015-03-01
You could make yourself the owner when you reinstall, tweak the machine to how she wants it, then create a guest account for her and set permissions so she is not in the admin group. If the machine needs updating or any major changes need to be done, YOU are going to have to do them by logging in under your account is the only draw back.

You could, on the other hand, and my preference, reinstall with her as the owner and tell her to only do updates, not change things when she doesn't know what effect it's going to have. If a user can't install apps via Software Centre/Synaptics or update their own machine, that is not ideal. Yea, she might break things, but less so as she learns about what is what. There is a learning curve and without being able to install and update, she is not going to learn much quickly.

---

### Post by mörgæs on 2015-03-01
Agree with the post above. 

She only needs to learn one rune: When Buntu asks for a password then THINK. She should only enter the password when there is a good reason, say a software update.

---

### Post by acefromspace on 2015-03-06
There is no way I can trust her to have main password. I did a fresh install and only I know the password. How do I add another user (have never done this before)? Can she just use guest session?

---

### Post by deadflowr on 2015-03-06
> **acefromspace said:**
> There is no way I can trust her to have main password. I did a fresh install and only I know the password. How do I add another user (have never done this before)? Can she just use guest session?

Regular Ubuntu w/unity, or gnome-esque desktop?
Add a new user with the program User Accounts.
(Note you need to unlock the program to add a user, which you can do with your admin password)
The benefit of using User Accounts to setup a new user is that second users start out as standard/normal/non-admin users.

Which is all you need to set her up as.
She will then have her own password to control her own stuff, but only her own stuff, and cannot do a thing about messing with the system.

---

### Post by matt18 on 2015-03-06
no, there are issues with in box upgrade. I was just making a new thread about this for my issues. I have had to un-install MULTIPLE software packages and programs because upgradeding from inside 12.04 to 14.04 messed them all up. RAWtherapy, stellarium, libre office, sweet home 3d and some editing software are all jacked up. missing menues, wont open up and i they do, they crash and burn haha.

---

### Post by acefromspace on 2015-03-07
I did go to user accounts and unlocked with password... can't see how to add another user... tried clicking (left and right)... don't see it anywhere.

---

### Post by deadflowr on 2015-03-07
> **acefromspace said:**
> I did go to user accounts and unlocked with password... can't see how to add another user... tried clicking (left and right)... don't see it anywhere.
There should be a plus sign at the bottom of where the usernames are listed on the left side. 
This means add user.

(Note that if you click on your current or any other made user's name, a minus arrow will show, or show more prominently.
This means delete user, so unless you want to get rid of a user ignore the minus sign)

If you, by chance, do not see a plus or minus sign below the user's names in User Account, then something is wrong with the setup/install.

It should also be noted that when you do actually add a new user with user accounts, it'll add thew user, but not make you add a password, so the user's password will be marked as disabled.
A disabled password means a disabled account, so go ahead and click on the word "disabled" in the password field to open the password box to make a password. Once a password is made and accepted as at least Fair, click on Create(or OK, I forget which it says) and the new user will now be enabled with password.

I think you need to reboot for the new user to become fully usable.
I forget.
It might be you only need to logout and back in, but rebooting definitely sets the new user as fully-active.

---

### Post by tokyobadger on 2015-03-08
> **acefromspace said:**
> There is no way I can trust her to have main password. I did a fresh install and only I know the password. How do I add another user (have never done this before)? Can she just use guest session?
It's her computer ;-)  If she's a friend then I'm sure she'd trust you to show her what she's best off doing/not doing - give her a fish vs teach her to fish etc. Locking yourself in as admin could be an issue in the long run - ie you fall out as friends (due to "messing up"/"hijacking" her PC or more normal reasons).

We were all beginners - first time using a computer, first time installing an OS, first time driving, first time walking, first time wiping our own ... I think you get the picture ;-)

---

### Post by acefromspace on 2015-03-09
All is well... thank you for the help. Most people I have helped were more experienced with computers. I found the add user (plus sign) It's so small I missed it. Setup user, password, logged out, logged into her user and enetered password. Worked great. Will still help her with updates, ect. By the way... I am very happy with ubuntu 12.04 and even though I hated unity at first, I learned how to use it and like it now. It's also impressive to show new people interested in linux.

---

