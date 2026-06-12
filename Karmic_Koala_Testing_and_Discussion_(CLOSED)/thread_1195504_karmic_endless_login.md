---
title: "karmic endless login"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-06-23
I just installed karmic alpha 2 on my netbook tonight and was asked to do a partial distro upgrade.  I said ok and let it do its thing, but now whenever my machine boots, I auto login then get asked for a password for my keyring.  At this point it doesn't matter if I enter my password or close the dialog box, the machine will log out then auto log back in and keep doing this endlessly.  Any ideas why or is there a way to fix this?

---

### Post by andrewabc on 2009-06-23
No idea, but you could download/burn and test a daily cd because then the updates would already be incorporated and might not cause this problem.

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by keenish27 on 2009-06-23
good idea.  I'll give it a shot and see what happens.

---

### Post by Martey on 2009-06-24
It's a bad idea to do partial upgrades - other threads have covered why.

I suspect that the issue you are seeing might be related to Intel graphics - I was seeing a similar issue on my ThinkPad T500 (GM45), but was able to login after switching to my ATI card (it has 2 video cards).

Any chance that you are running compiz? I got an Apport report ("A program has recently crashed...") after logging in successfully.

---

### Post by ghindo on 2009-06-24
I'm experiencing similar issues.  With the latest two kernels (.30-9 and .30-10), after logging into GNOME, I get immediately booted back to GDM.

---

### Post by yelo3 on 2009-06-24
This happens to mee to, I think it'a MESA issue. you can use the emergency failsafe session and attach .xsession-errors here

---

### Post by tekstr1der on 2009-06-24
> **ghindo said:**
> I'm experiencing similar issues.  With the latest two kernels (.30-9 and .30-10), after logging into GNOME, I get immediately booted back to GDM.

Ditto. This just began happening after installing the mesa and opengl updates today. Any workaround found? Failsafe gnome session fails in same fashion.

---

### Post by taavikko on 2009-06-24
Check if adding new user and trying to login to that account works, if so, something is b0rked on your original users settings.

Recovery-> "adduser test" -> "/etc/init.d/gdm start" -> login

---

### Post by Vanishing on 2009-06-24
> **tekstr1der said:**
> Ditto. This just began happening after installing the mesa and opengl updates today. Any workaround found? Failsafe gnome session fails in same fashion.

Opps...saw this thread after I posted another similar issue on the board..:P
Yes..I have the same problem..curious about the work around too.:popcorn:

---

### Post by yelo3 on 2009-06-24
I've recompiled mesa without the 108 patch and it works

---

### Post by Vanishing on 2009-06-24
> **yelo3 said:**
> I've recompiled mesa without the 108 patch and it works

Can you show me how you did it?:D

---

### Post by yelo3 on 2009-06-24
It requires lots of space (2GB or more) & time:
- mkdir mesa
- cd mesa
- apt-get source mesa
- cd mesa-7.4.1
- gedit debian/patches/series (remove the line starting with 108 )
- gedit debian/changelog (edit in the first line the package version to 7.4.1-1ubuntu3+your_name)
- sudo apt-get build-deb mesa
- dpkg-buildpackage
- cd ..
- sudo dpkg -i *.deb (well it's better to install only the required packages!)
- rm -rf mesa-7.4.1 (to save space)

---

### Post by Vanishing on 2009-06-24
> **yelo3 said:**
> It requires lots of space (2GB or more) & time:
- mkdir mesa
- cd mesa
- apt-get source mesa
- cd mesa-7.4.1
- gedit debian/patches/series (remove the line starting with 108 )
- gedit debian/changelog (edit in the first line the package version to 7.4.1-1ubuntu3+your_name)
- sudo apt-get build-deb mesa
- dpkg-buildpackage
- cd ..
- sudo dpkg -i *.deb (well it's better to install only the required packages!)
- rm -rf mesa-7.4.1 (to save space)

Thank you!
I just downgraded mesa before seeing your post.:P lol
I'm gonna try it.:D

---

### Post by adult swim on 2009-06-24
> **yelo3 said:**
> It requires lots of space (2GB or more) & time:
- mkdir mesa
- cd mesa
- apt-get source mesa
- cd mesa-7.4.1
- gedit debian/patches/series (remove the line starting with 108 )
- gedit debian/changelog (edit in the first line the package version to 7.4.1-1ubuntu3+your_name)
- sudo apt-get build-deb mesa
- dpkg-buildpackage
- cd ..
- sudo dpkg -i *.deb (well it's better to install only the required packages!)
- rm -rf mesa-7.4.1 (to save space)
thanks for the workaround.  just a heads up, you accidently said sudo apt-get build-deb mesa instead of sudo apt-get build-dep mesa

---

### Post by tekstr1der on 2009-06-24
Well, before I saw the workaround posted, I went ahead and removed compiz. The default window manager is now "unknown" and I have no window controls available. If I use metacity --replace &, I get window controls back, but can't close the terminal window as the metacity command is still active. How do I change the default window manager? I see in the configuration editor that desktop > gnome > applications > window_manager is still set to /user/bin/compiz for default. Do I simply change that value to metacity?

EDIT: Okay, went ahead with the mesa recompile and reinstalled compiz. Works great, thanks.

---

### Post by graaant on 2009-06-24
> **yelo3 said:**
> It requires lots of space (2GB or more) & time:
- mkdir mesa
- cd mesa
- apt-get source mesa
- cd mesa-7.4.1
- gedit debian/patches/series (remove the line starting with 108 )
- gedit debian/changelog (edit in the first line the package version to 7.4.1-1ubuntu3+your_name)
- sudo apt-get build-deb mesa
- dpkg-buildpackage
- cd ..
- sudo dpkg -i *.deb (well it's better to install only the required packages!)
- rm -rf mesa-7.4.1 (to save space)

Worked great for me - thanks!

---

### Post by ghindo on 2009-06-25
It seems that this last round of updates have solved the problem, at least for me.  How about everybody else?

---

### Post by yelo3 on 2009-06-25
Yes, the changelog says it's fixed

---

### Post by celticbhoy on 2009-06-25
I also have this problem, but I cant get recovery mode to run. When I boot to recovery I just get a blank screen, and if I hit enter I get a normal boot. From GDM I can login to failsafe terminal, how do I connect to the internet from there to perform the fix?

---

### Post by taavikko on 2009-06-25
> **celticbhoy said:**
> I also have this problem, but I cant get recovery mode to run. When I boot to recovery I just get a blank screen, and if I hit enter I get a normal boot. From GDM I can login to failsafe terminal, how do I connect to the internet from there to perform the fix?

"/etc/init.d/networking start"
and do updates.

---

### Post by yelo3 on 2009-06-25
if you connect through wireless you have to execute
nm-applet &

and wait some seconds

---

### Post by celticbhoy on 2009-06-25
Thanx for the reply. Got it with a wired connection.

---

### Post by tjeremiah on 2009-06-25
how do you initiate the failsafe terminal to update?

---

### Post by celticbhoy on 2009-06-25
at the login screen select session and the option will be there

---

### Post by tjeremiah on 2009-06-25
> **celticbhoy said:**
> at the login screen select session and the option will be there

nope, dont see it with this now stupid gdm theme I installed some time ago. :(

---

### Post by celticbhoy on 2009-06-25
there should still be an icon or something that will get you a menu or list to select. If you cant find it can you remember what theme you installed

---

### Post by tjeremiah on 2009-06-25
> **celticbhoy said:**
> there should still be an icon or something that will get you a menu or list to select. If you cant find it can you remember what theme you installed

[http://gnome-look.org/content/show.php/Sunset+V2+Restyling?content=100942](http://gnome-look.org/content/show.php/Sunset+V2+Restyling?content=100942) This. Apparently after viewing the pic, there is one. Must not be visible to me because the resolution isnt accurate on my screen. Ill try to point the mouse downward hoping to hit session.

---

### Post by tjeremiah on 2009-06-25
sigh, actually no. There is no session button. I must of have the old version gdm of this theme. Is there anyother way to access to update?

---

### Post by celticbhoy on 2009-06-25
just to check does recovery console work for you

---

### Post by tjeremiah on 2009-06-25
> **celticbhoy said:**
> just to check does recovery console work for you

yes.

---

### Post by celticbhoy on 2009-06-25
Then the easy way is to use recovery console - root with networking and then run update manager.

---

### Post by lalitgaur on 2009-06-25
Hi 
I also seem to have gotten this problem after upgrading to alpha 2.
Can someone tell me how can I update it to the latest stable version.
I have access to only wireless and not wired network. 
Step by step please in both recovery as well as failsafe mode. I am currently away from desktop that has this problem. If you could list this I will try both of them once I get home.


Edit :
It worked. The following instructions for wireless.
```

1) On the lower left side of the login screen there is a session option.
2) Then click on the failsafe terminal. Enter name and password.
3) You should get a small terminal screen.
4) Type **nm-applet &** in terminal. Then wait for a few seconds. A few debug messages will come.
5) Type **update-manager** in terminal.
6) Click check in update manager.
7) After update manager finishes checking click on update.
8) After successful completion of update close update manager.
9) Type **exit** in terminal to exit failsafe terminal.
10) Log in to ubuntu using name/ password. It should work now

```

---

### Post by tjeremiah on 2009-06-25
> **celticbhoy said:**
> Then the easy way is to use recovery console - root with networking and then run update manager.

im kinda new in this whole linux thing, hasnt been a year yet. Can you please give me a step by step into doing this? By recovery mode, you mean when I select "fix broken packages", that will download updates?

---

### Post by tjeremiah on 2009-06-25
> **lalitgaur said:**
> Hi 
I also seem to have gotten this problem after upgrading to alpha 2.
Can someone tell me how can I update it to the latest stable version.
I have access to only wireless and not wired network. 
Step by step please in both recovery as well as failsafe mode. I am currently away from desktop that has this problem. If you could list this I will try both of them once I get home.


Edit :
It worked. The following instructions for wireless.
```

1) On the lower left side of the login screen there is a session option.
2) Then click on the failsafe terminal. Enter name and password.
3) You should get a small terminal screen.
4) Type **nm-applet &** in terminal. Then wait for a few seconds. A few debug messages will come.
5) Type **update-manager** in terminal.
6) Click check in update manager.
7) After update manager finishes checking click on update.
8) After successful completion of update close update manager.
9) Type **exit** in terminal to exit failsafe terminal.
10) Log in to ubuntu using name/ password. It should work now

```

the thing is that, due to my GDM, I dont see a session button :( I swear if i get out of this, ill never install such a theme.

---

### Post by philcamlin on 2009-06-25
never do partial upgrade...

---

### Post by tjeremiah on 2009-06-26
SOLVED : The trick to access session even if not visible was to press F10 :) I did the updates and everything is smooth and appears to be faster! Im still going to keep my promise and remove this stupid GDM.

---

### Post by psyke83 on 2009-06-26
> **tjeremiah said:**
> im kinda new in this whole linux thing, hasnt been a year yet. Can you please give me a step by step into doing this? By recovery mode, you mean when I select "fix broken packages", that will download updates?

No offense, but if you're new to Linux, why are you testing the development release? You'll have a lot more fun with Jaunty (without the headaches that accompany a development release).

However, if you like pain...

---

### Post by tjeremiah on 2009-06-26
> **psyke83 said:**
> No offense, but if you're new to Linux, why are you testing the development release? You'll have a lot more fun with Jaunty (without the headaches that accompany a development release).

However, if you like pain...

I like pain.

---

### Post by ghindo on 2009-06-26
> **psyke83 said:**
> No offense, but if you're new to Linux, why are you testing the development release? You'll have a lot more fun with Jaunty (without the headaches that accompany a development release).

However, if you like pain...What better way to learn than to dive right in?  As long as he knows the risks, of course.

---

### Post by psyke83 on 2009-06-26
> **ghindo said:**
> What better way to learn than to dive right in?  As long as he knows the risks, of course.

It's ok, he/she likes pain ;).

I just feel that we need some better documentation describing the prerequisites and risks when testing the development release; 23meg had an excellent thread about this for previous releases, and while Nullack posted an excellent thread on how to contribute for this release, it doesn't describe the risks.

I'm not singling out tjeremiah (as this doesn't apply), but if you look at this sub-forum you will see a lot of duplicate threads concerning the same issues, over and over again. If more people performed a search before posting a new thread on their issue, a lot less energy would be wasted from that one change alone; and that extra energy could be used to help identify and fix their issues more quickly.

Testing the development release can be unforgiving for a new user; I believe at a minimum that users should know how to perform basic maintenance via terminal, and should know more about the risks involved when performing partial upgrades. These may not be necessary to know when using the final release, but the development release is a different beast altogether.

Here's an idea: why don't we disable update-manager's "Partial Upgrade" capability during the development process? That would drastically reduce the number of issues for new users that are testing the development release. I predict this will not happen, but it begs the question: why are so many users performing partial upgrades with no apparent awareness of the risks?

---

### Post by douham on 2009-06-26
> **psyke83 said:**
> It's ok, he/she likes pain ;).

I just feel that we need some better documentation describing the prerequisites and risks when testing the development release; 23meg had an excellent thread about this for previous releases, and while Nullack posted an excellent thread on how to contribute for this release, it doesn't describe the risks.

I'm not singling out tjeremiah (as this doesn't apply), but if you look at this sub-forum you will see a lot of duplicate threads concerning the same issues, over and over again. If more people performed a search before posting a new thread on their issue, a lot less energy would be wasted from that one change alone; and that extra energy could be used to help identify and fix their issues more quickly.

Testing the development release can be unforgiving for a new user; I believe at a minimum that users should know how to perform basic maintenance via terminal, and should know more about the risks involved when performing partial upgrades. These may not be necessary to know when using the final release, but the development release is a different beast altogether.

Here's an idea: why don't we disable update-manager's "Partial Upgrade" capability during the development process? That would drastically reduce the number of issues for new users that are testing the development release. I predict this will not happen, but it begs the question: why are so many users performing partial upgrades with no apparent awareness of the risks?

+1 Psyke83. Lots of people are just going round and round in circles and we have ended up with many posts that are basically dupes. Also if people are just stuck with a general Linux problem try searching the main forums first

---

### Post by brm on 2009-06-27
> **psyke83 said:**
> ... if you look at this sub-forum you will see a lot of duplicate threads concerning the same issues, over and over again. If more people performed a search before posting a new thread on their issue, a lot less energy would be wasted from that one change alone; and that extra energy could be used to help identify and fix their issues more quickly.

The search function on ubuntuforums.org is rather hit-and-miss. The same is true over at Launchpad. Despite doing a careful search for similar bugs before filing a new one, at least half my bugs are later marked as duplicates --- and I thought I was not bad at search engine incantations :-).

Duplicate threads are the inevitable result of difficult searching.

---

