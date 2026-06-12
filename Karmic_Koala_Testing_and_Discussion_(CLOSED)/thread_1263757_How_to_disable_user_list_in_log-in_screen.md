---
title: "How to disable user list in log-in screen?"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autark on 2009-09-11
I don't want Ubuntu to list the available users in the log-in screen. I want the old behavior back, where the user had to enter the user name before entering the password. At least that should be an easily configurable option.   I have tried setting /apps/gdm/simple-greeter/disable_user_list to true, but that doesn't help.

---

### Post by BadBoy4Live on 2009-09-11
Open **System->Administration->Login Window**. Select the **Local** tab.
Change the theme to one without a list.

Them click close

Hope it helps

---

### Post by autark on 2009-09-11
Thanks, but I don't have "Login Window" in my System Administration menu. I have Login Screen, but that doesn't have this option.

---

### Post by Seventh Reign on 2009-09-11
This has been covered 100 times here already, but Karmic's GDM does not have that option available yet.  As of right now the only things you can change are auto/timed logins.  This will/should be changed by the time the official release comes in October.

---

### Post by philinux on 2009-09-11
> **BadBoy4Live said:**
> Open **System->Administration->Login Window**. Select the **Local** tab.
Change the theme to one without a list.

Them click close

Hope it helps

If you were using karmic you would know that this is not possible, as yet.

---

### Post by xebian on 2009-09-12
> **Seventh Reign said:**
> This has been covered 100 times here already, but Karmic's GDM does not have that option available yet.  As of right now the only things you can change are auto/timed logins.  This will/should be changed by the time the official release comes in October.

Probably even more but it's being ridiculous to logon as "vboxadd"

---

### Post by twobturtle on 2009-09-26
I had some luck executing the following in a terminal:
```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
--type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

Perhaps this will work for you?

(source: [http://forums.fedoraforum.org/showthread.php?t=205633](http://forums.fedoraforum.org/showthread.php?t=205633))

---

### Post by A1Dox on 2009-10-13
> **twobturtle said:**
> I had some luck executing the following in a terminal:
```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
--type bool --set /apps/gdm/simple-greeter/disable_user_list true
```Perhaps this will work for you?

(source: [http://forums.fedoraforum.org/showthread.php?t=205633](http://forums.fedoraforum.org/showthread.php?t=205633))

twobturtle, you're a star!  Just what I was looking for, and worked fine in the beta that I downloaded/installed yesterday. I did run a full update which changed an awful lot of the files installed from the original ISO, but other than that, this partition is still pretty much as it came "out of the box".

Thanks again,
Dox.

---

### Post by Akita on 2009-10-13
Disregard - checking the box as user or admin doesn't work. For the life of me I thought it used to. Oh well.

You can do this with the GConf config editor (as admin):

apps->gdm->simple-greeter

Check the "disable user list" box.

---

### Post by SabreWolfy on 2009-10-14
I agree that this is an annoying change. I can't understand why things like this are arbitrarily changed from one release to the next. If I'd wanted a face greeter, I'd have turned it on already. I'm happy to type my username. Not to mention I consider it a security risk to have all usernames exposed for anyone to see. Grr!

---

### Post by emarkay on 2009-10-14
> **SabreWolfy said:**
> I agree that this is an annoying change. I can't understand why things like this are arbitrarily changed from one release to the next. If I'd wanted a face greeter, I'd have turned it on already. I'm happy to type my username. Not to mention I consider it a security risk to have all usernames exposed for anyone to see. Grr!

Oh no - they said "SECURITY!!!"  - I got a LOAD of Bovine Fecal Matter over that word on the original post. (But I sort of, kindof, almost, agree... Oh noooo!)

[http://ubuntuforums.org/showthread.php?t=1287054](http://ubuntuforums.org/showthread.php?t=1287054)

Feel free to chime in there.  OP , can you mark this post "Solved"  :)

---

### Post by SabreWolfy on 2009-10-14
I'm with you that I prefer that my username is not displayed for all to see. Yes of course, as they say, you can boot a live CD and find usernames, etc., but nevertheless, I prefer that someone has to take the extra effort and have the extra knowhow. Besides, those approaches require access to the machine, etc. Showing usernames on login means that you just have to glance at the screen to find out the username. I'm also just peeved that the greeter is configured to show faces and names automatically.

---

### Post by Longinus00 on 2009-10-14
> **SabreWolfy said:**
> I'm with you that I prefer that my username is not displayed for all to see. Yes of course, as they say, you can boot a live CD and find usernames, etc., but nevertheless, I prefer that someone has to take the extra effort and have the extra knowhow. Besides, those approaches require access to the machine, etc. Showing usernames on login means that you just have to glance at the screen to find out the username. I'm also just peeved that the greeter is configured to show faces and names automatically.

The thing is, it doesn't default to show your "user name", at least not the name you login with. If you check System->Administration->Users and Groups, the name that gets displayed is actually what is under the "Name" column and not the "Login name" column, if they are the same then that's another matter. You can edit your real name to be "hillary clinton" and that's what you'll see at the login window. 

Other people will not be able to login to your computer via ssh or whatever using your real name so this is really not an issue.

---

### Post by adder1972 on 2009-10-15
> **Longinus00 said:**
> 
Other people will not be able to login to your computer via ssh or whatever using your real name so this is really not an issue.

If you don't want the user list to be shown, then it is an issue. Please try to post solutions to the original post's problem.

---

### Post by Longinus00 on 2009-10-15
> **adder1972 said:**
> If you don't want the user list to be shown, then it is an issue. Please try to post solutions to the original post's problem.

I was responding to his comment about how you can instantly know the username just from glancing at the list as this is incorrect. Turning off the user list is a separate issue.

---

### Post by SabreWolfy on 2009-10-16
I use my username as my "name".

Anyhow, aside from the security argument, I have had to create user accounts for about a dozen users in order to create SAMBA shares for them. So my greeter screen looks ridiculous. It even has a scroll-bar down the side. Silly. Let's stop dumbing Ubuntu down. Or at least make it an option as to whether you want a dumbed-down version.

---

### Post by kjdaly on 2009-10-23
So there's no way to do this then? I tried gconf but the "disable user list" option seems to be ignored.

---

### Post by slochewie on 2009-10-24
I tried disabling "disable user list" in gconf both as myself and as root and it definitely seems to be ignored. Annoying.

---

### Post by cyberkilla on 2009-10-25
Funny, it worked for me a few days ago. It showed "Other" and I had to type my username & pass. Still, the user list was not visible.

---

### Post by A1Dox on 2009-10-26
I've now disabled the userlist on two machines successfully. The first, I managed by finding this thread, copying the gconftool-2 command from the first page of the thread, and it worked fine. On the second machine, I used the configuration editor to set the apps/gdm/simple-greeter/disable_user_list checkbox and it didn't appear to do anything. I fired up the shell and ran the gconftool-2 command just like on the other machine, and whatever different instance of the flag it sets, has done the trick, again.

Just sayin.. ;)

Dox

---

