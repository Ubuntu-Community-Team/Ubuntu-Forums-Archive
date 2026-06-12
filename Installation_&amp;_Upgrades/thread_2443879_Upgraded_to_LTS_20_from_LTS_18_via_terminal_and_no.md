---
title: "Upgraded to LTS 20 from LTS 18 via terminal and now not able to login"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by priyavrat17 on 2020-05-21
When I am entering password in my login screen I am getting below message:
Oh no! Something has gone wrong. A problem has occurred and system can't recover. Please contact a system administrator.

I can see login screen is updated seems like it is upgraded to LTS20 but I cant login. Please help me.

---

### Post by ubfan1 on 2020-05-21
Try login at a virtual terminal (at the login/error screen, switch to a vt with ctrl-alt-F3) -- username /password, and see how much free disk space you have with df
See [http://parthpatel02.blogspot.com/2015/12/oh-no-something-has-gone-wrong-problem.html](http://parthpatel02.blogspot.com/2015/12/oh-no-something-has-gone-wrong-problem.html)
for additional troubleshooting.

---

### Post by priyavrat17 on 2020-05-21
Hi, I have around 700gb free. I just tried creating a new user in my system and I am able to login to that user in new ubuntu 20. But for old user I still see same error. All customizations and configurations are there in old user , I want to login into that user.

---

### Post by ubfan1 on 2020-05-21
So you have narrowed the problem down to your original login directory.  Check the ownership of all the files ls -al to ensure none are owned by root (and chown as necessary). If not file ownership, then it may be something in a "dot" directory (.cache, .local, .config, etc.)  Find the problem by mv ing the "dot" files into a temporary storage location, l(make a directory named "oldfiles") .  mv a dot file out of storage and try to login.  If successful, mv another one until you fail at login.  mv the dot file back to storage, and mv out the top level and one subdirectory at a time until you find the one causing you problems, ...  Of course, if you find you have all your configs and settings, you may stop the search, and just ignore anything left in the oldfiles storage.  Most likely the problem will be in the .cache directory, but could be anywhere.  It may be less work to simply redo your configs like in a new installation.

---

### Post by priyavrat17 on 2020-05-22
I tried for so many folders and directories.. even compared with the new users directory. I have reset whole gnome in old user via command but still the problem persists. It seems the only way which is left to me is to backup all the files via new user and delete this old user. But its really bad seeing this. Hope something works.. still exploring and trying to find out.

---

### Post by priyavrat17 on 2020-05-24
Hey, It finally worked. Earlier I was checking if any file/directory is having root owner, found some and changed ownership still I was getting same error. Now what I did , I moved each of the hidden directory such as .local,.config,.cache etc and finally it worked. Thanks a ton man you saved my lovely laptop.

---

