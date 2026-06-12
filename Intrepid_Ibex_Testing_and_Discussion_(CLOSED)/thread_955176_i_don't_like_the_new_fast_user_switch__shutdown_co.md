---
title: "i don't like the new fast user switch / shutdown combo applet."
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Polygon on 2008-10-21
I do not like how they have combined the functionality of the fast user switch applet and the quit button applet.

One, its redundant. I already have a pidgin taskbar icon telling me my status, why do i need an applet to tell me the same thing?

two, its more annoying. I have accidently hit hibernate when i really meant to hit restart, because of the fact that all the shutdown actions are in a list now. Has ubuntu not learned anything from vista? There was an entire blog post by a microsoft developer documenting the disaster that is the vista shutdown menu, which is basically the same thing as the ubuntu shutdown menu now

Not only that, but if i don't want to use the new combo applet, i am forced to use two applets instead of one. One to log off or switch users, and another for the shutdown actions. 

Why can't we have the old quit button back? It was nice, simple, and when you clicked it you have nice large icons which makes it easy to identify and also makes it harder to accidentally click something due to the large size.

If it isn't broke...don't fix it!

---

### Post by FuturePilot on 2008-10-22
I agree. I prefer the old one. They said it was confusing which is why they got rid of it but I don't see how that can be. If anything this new thing is more confusing. Not to mention that when you click on an action in the fast user switcher it doesn't ask confirmation, it just does it. Accidentally clicking on something when you meant something else is very annoying.

---

### Post by shad0w_walker on 2008-10-22
Totally agree on the new logout/shutdown menus. Biggest regression in the release I've seen so far. Everything else has been quite nice, admitedly the whole 'Empathy being lame and relying on libpurple if I want more than just MSN' thing is seriously stupid, but overall i've liked the updates.

I'm looking around at the moment to see if I can possibly jack the old menu from 8.04 and transplant it into 8.10 with out major headaches.

---

### Post by mojo636 on 2008-10-22
I think the new applet is great, makes things much easier. I have not hit the wrong button as yet but if i do well it is not much of an inconvenience.

---

### Post by mindwarp on 2008-10-22
> **Polygon said:**
>  There was an entire blog post by a microsoft developer documenting the disaster that is the vista shutdown menu, which is basically the same thing as the ubuntu shutdown menu now


Did you actually read that article?  It was about simplifying it by not having so many dialogs.  Clicking the power button, then bringing up a new dialog didn't make much sense.  Nobody can stop people from clicking the wrong buttons, but I don't want a bunch of confirm dialogs when I can indeed click the correct buttons.  You lost the minute it took to reboot because you misclicked.  Life goes on.

---

### Post by mc4100 on 2008-10-22
> **mindwarp said:**
> Did you actually read that article?  It was about simplifying it by not having so many dialogs.

Link to blog post?

Edit: It think I found [it]("http://www.joelonsoftware.com/items/2006/11/21.html").

---

### Post by pelle.k on 2008-10-22
I **love** the new fast user switch applet, it lets me do these things, and do it fast.

---

### Post by scaine on 2008-10-22
I'm not running Intrepid on anything other than my main (desktop) PC.  On a laptop, what happens when you press the power button now that they've changed the behavior to this list (which I quite like actually, but I can see both sides of this fence)?

In power options, there used to an option like "when I press the power button :" and one of the options was "ask".

If that's still there, it must bring up the old buttons?  How else could it prompt?

---

### Post by mc4100 on 2008-10-22
> **scaine said:**
> I'm not running Intrepid on anything other than my main (desktop) PC.  On a laptop, what happens when you press the power button now that they've changed the behavior to this list (which I quite like actually, but I can see both sides of this fence)?

In power options, there used to an option like "when I press the power button :" and one of the options was "ask".

If that's still there, it must bring up the old buttons?  How else could it prompt?

It's still there ... er, there was a bug that caused pressing the power button, when "ask me" was specified, to bring up the list of logout options:
```
gnome-session-save --logout-dialog
```Pressing the power button should, however, bring up the list of shutdown options:
```
gnome-session-save --shutdown-dialog
```
... but I don't know if it's fixed yet.

---

### Post by lonniehenry on 2008-10-22
brings up the following box.  I like the new user switcher shutdown combo.  It makes more sense the separate ways that were available in the past.  Like most things in linux it is easy to change to meet your preferences.

---

### Post by bash on 2008-10-22
I just want to say as well that I greatly appreciate the new switch/shutdown combo. I think it is a **great** improvement over the old way. 

Concerning the people complaining about Empathys lack of features, one of the developers (or a person closely following developement) said in one of the threads here that empathy is still early on in its development. They relying on libpurple is more of a "we don't offer this yet so we use libpurple for the moment to provide basic support".

---

### Post by pelle.k on 2008-10-22
Maybe i should say that even though i prefer the new one, the best thing for everybody would be if both were available.
Better yet, if you could configure what should be visible :P

---

### Post by Hairy_Palms on 2008-10-22
i love the new dialog, i hated the old one, it was very slow to load, cluttered, i didnt need seven options in one huge screen-central mess to turn off my PC, the new ones are more like the old gnome upstream dialogs, but much better looking and easier to use, i cant speak for the fast user switch applet, one of the first things i do after installing is remove that and the logout button from my panel.

---

### Post by Hairy_Palms on 2008-10-22
Just read that article about vistas start menu. made me think, i dont agree with all of what was said, but one thing seemed to make sense to me, combining the sleep and hibernate buttons, if they were combined, then the power management software detected if the system was running from battery or mains, and sleep if its on mains power and hibernate if on battery. imho  hibernating a desktop system is a pointless thing to do, its not any faster than a full startup, so just shutdown.

---

### Post by zombiepig on 2008-10-22
I'm a fan of it too. What I'm really waiting for though, is when empathy no longer appears in the task bar. It's really redundant, I can change my status quickly now, and when I want to see the contact list I can load up the main empathy window from the applications menu. And even better, I can add a few megaphone applets to the panel for people I chat to a lot. 

So I say death to the empathy task bar icon! :)

---

### Post by OutOfReach on 2008-10-22
I hate this new version, the one in Hardy is much better.
I always expect to get a shutdown dialog when I press the button on the top right corner, but all I get is a log out dialog. :/

---

### Post by pelle.k on 2008-10-22
> I always expect to get a shutdown dialog when I press the button on the top right corner, but all I get is a log out dialog. :/
If that is all you're after, why not install the shutdown applet instead?

---

### Post by Polygon on 2008-10-22
> **pelle.k said:**
> If that is all you're after, why not install the shutdown applet instead?

thats the whole point, there should be ONE button for all of this. There was really nothing wrong with the way it was done in hardy. 6 buttons:

log out
lock screen
shutdown 
restart
hibernate
suspend

But now, we need two applets to have the same functionality

one:

shutdown
hibernate
suspend
restart

and another

log out 
switch user
guest session


I do not want to have two applets on my tasbkar, i want one. Not to mention that the new fast user switch applet doesn't even LOOK like a power button anymore, as long as your running pidgin or some IM program. The applet is just now too complicated. I think the pidgin status thing should have an option to be turned off, or be a separate applet all together.

and also, on the fact that the new applet shows pidgin status, you cant even set a custom status with the applet, so most users will want to use the offical pidgin icon rather then the crippled ugly fast user switch applet (seriously, who thought that a red triangle symbolizes being away?)

any what i meant by the vista blog thing, is that it was talking about simplifying the interface. Now, we have a confusing combo applet that has a dual purpose, but only manages user switching. And if we go to system, we have 3 choices rather then one. Even with vista, all you have to do is click the triangle and all the options are presented to you. Shut down, log out, restart, suspend, hibernate. We need something like this, and i personally think that what we had before was fine.

---

### Post by OrangeCrate on 2008-10-22
Frankly, it took me literally a split second to understand what they did, and I never gave it a second thought, until I saw this thread.

I use just one panel, with the Main Menu icon, and it tells me clearly (one above the other) what it gives me the option to do - Shut down, or log out.

I think it's much cleaner than Hardy's "mega box", and personally, I like it.

---

### Post by Polygon on 2008-10-22
that isnt part of the discussion. What we are talking about is the removal of the 'quit' button applet and its functionality being combined with the fast user switch applet. I know it makes sense if there are entries in the system > shutdown or system > logout thing, thats fine. Its just i want one applet to manage shutting down or logging out. Currently all we have is the fast user switch applet, which is annoying (for me) cause now i have two things telling me what my pidgin status is, and there is no way to turn that off.

---

### Post by pelle.k on 2008-10-22
> which is annoying (for me) cause now i have two things telling me what my pidgin status is, and there is no way to turn that off.
Here you go;
```
gconf-editor /apps/fast-user-switch-applet/show_presence_info
```

---

### Post by OrangeCrate on 2008-10-22
> **Polygon said:**
> **that isnt part of the discussion.** What we are talking about is the removal of the 'quit' button applet and its functionality being combined with the fast user switch applet. I know it makes sense if there are entries in the system > shutdown or system > logout thing, thats fine. Its just i want one applet to manage shutting down or logging out. Currently all we have is the fast user switch applet, which is annoying (for me) cause now i have two things telling me what my pidgin status is, and there is no way to turn that off.

Sure it is, and that's what I commented on...

> thats the whole point, there should be ONE button for all of this. There was really nothing wrong with the way it was done in hardy. 6 buttons:

log out
lock screen
shutdown
restart
hibernate
suspend

But now, we need two applets to have the same functionality

one:

shutdown
hibernate
suspend
restart

and another

log out
switch user
guest session


I do not want to have two applets on my tasbkar, i want one.

I like the two applets, rather than the one, if you missed my point.

---

### Post by alienexplorers on 2008-10-22
I liked the old style found in Hardy.  It is much better than having two seperate buttons.  Since I am the only user of this system having a seperate button for logout, switch user, and guest session is of little use to me.  I can accomplish all I need with restart and shutdown.

---

### Post by Lateforgym on 2008-10-23
Im not sure if this applies, but the old red icon can be added back and it is called "Switch User". Right click on the task bar and add back the "Switch User" Icon, even though it looks different, when it shows up on the bar it will look like the old icon. That way you dont have to have the Grey power off button or the Green running guy (if your the only user). 

You will may have to move all the icons around. This is done by right clicking on the icon, and unchecking the lock into place, then right clicking again and hitting move. You may have to do this with the little divider too.

---

### Post by Polygon on 2008-10-23
the point is, i  want the old quit button applet back. I either have to use two applets to get the same functionality that was present in hardy, or use a gconf hack which 99% of ubuntu users will never see or find out to get rid of the redundant pidgin status thing thats attached to the fast user switch applet, and have to deal with the fact that it does not look like a power button or anything for shutting down the computer.

---

### Post by Gourgi on 2008-10-23
> **pelle.k said:**
> I **love** the new fast user switch applet, it lets me do these things, and do it fast.

+1 
definitely love it

---

### Post by saro on 2008-10-24
2 applets ? try 3.

1) shutdown, restart, suspend, hibernate
2) logout, switch user
3) lock screen

This is ridiculous. I liked the old way of having all these in one applet. They could have atleast left it in place so that ppl who liked it can add it to their panel.

I am sorry, I dont like the new switch user applet, it takes too much real estate (two icons at the least), dont like the memu it pops up (if I want a menu I would just click on system menu) and the icons that it uses are also ugly.

Just my opinion.

---

### Post by syxbit on 2008-10-24
i love it.
but i think it's an ubuntu thing, as it's not offical gnome.
too bad. i want this in Arch :(

---

### Post by OutOfReach on 2008-10-24
> **Polygon said:**
> thats the whole point, there should be ONE button for all of this. There was really nothing wrong with the way it was done in hardy. 6 buttons:

log out
lock screen
shutdown 
restart
hibernate
suspend

But now, we need two applets to have the same functionality

one:

shutdown
hibernate
suspend
restart

and another

log out 
switch user
guest session


I do not want to have two applets on my tasbkar, i want one. Not to mention that the new fast user switch applet doesn't even LOOK like a power button anymore, as long as your running pidgin or some IM program. The applet is just now too complicated. I think the pidgin status thing should have an option to be turned off, or be a separate applet all together.

and also, on the fact that the new applet shows pidgin status, you cant even set a custom status with the applet, so most users will want to use the offical pidgin icon rather then the crippled ugly fast user switch applet (seriously, who thought that a red triangle symbolizes being away?)

any what i meant by the vista blog thing, is that it was talking about simplifying the interface. Now, we have a confusing combo applet that has a dual purpose, but only manages user switching. And if we go to system, we have 3 choices rather then one. Even with vista, all you have to do is click the triangle and all the options are presented to you. Shut down, log out, restart, suspend, hibernate. We need something like this, and i personally think that what we had before was fine.

Exactly! You spoke my mind. The dialog in hardy was perfect, I saw no reason to remove/change it.

---

### Post by zombiepig on 2008-10-24
> **OutOfReach said:**
> Exactly! You spoke my mind. The dialog in hardy was perfect, I saw no reason to remove/change it.

As far as I know, the old dialog was specific to ubuntu, with upstream and other distros using the split logoff/shutdown dialogs. Session management underwent a large change in the latest gnome release, so the ubuntu-specific changes would have required a re-write. Now, ubuntu is following the same behaviour as upstream (always a good thing IMO!).

I think that's the reasoning behind the change...

---

### Post by Polygon on 2008-10-24
ubuntu does not follow upstream in many places, i think we should code or make work the old applet back, cause honestly, having 2 or three applets replace one is just stupid

---

### Post by billenbois on 2008-10-24
i like the new one.. but then again im using kde 4 now ;p

---

### Post by Keen101 on 2008-10-24
I don't mind the new switcher too much, but i really prefer the old way better.

Both options should be available. I just remove the switcher from the panel since i don't want it. but, the switcher does have one new feature the old button did not.... it has a link to a guest mode, which is kind of nice.

here is my opinion in bold:

[B]1. The new switcher should stay, but probably have some tweaks. (i can remove it from the panel if i don't want it)

2. the old button should be fixed.

3. has the ugly grey icon from gnome icons theme been fixed yet in >System >Shutdown...?[/B]

---

### Post by andrewabc on 2008-10-24
So far I like the new shutdown at top right corner.
I always either shutdown or restart (the odd time to logout when something screws up).
So for me to move my mouse to top right, click, then to move a couple pixels down to do what I want is great.

It is better than moving mouse to top right, click, then move mouse back to center of screen to select what I want to do.

---

### Post by Polygon on 2008-10-24
i woulden't care if they made it so it looked like a power button, and then had all of the options in a list, but currently i have to see my name or the little 'users' icon, which is just going to confuse new users

---

### Post by cl333r on 2008-10-24
I have to agree on this:
> 
One, its redundant. I already have a pidgin taskbar icon telling me my status, why do i need an applet to tell me the same thing?

I have to figure out why I'd need a status indicator outside pidgin at all. I don't know what it's for, newcomers will surely be confused.

---

### Post by andrewabc on 2008-10-24
I just installed intrepid RC

What is so difficult about the attached image? As far as I can tell all the options are there (except switch user).

What is the status indicator you guys are talking about? Does it only show when running pidgin?
Oh, I see how it changes. That is very stupid. Remove pidgin status from shutdown button. It has no purpose being there.

Sigh, pidgin HTTP login still does not work for me (it never has). I'm on a fixed IP address and only port 80 works.

---

### Post by PatrickVogeli on 2008-10-25
I think there's nothing wrong about the fast switch applet or the split applets to turn off/restart and swith user/logout. But: 

One: I don't like the fast switch applet, so I just remove it from my panel. Anyway, some small icons would make it much nicer (as in the gnome menus)

Two: I have a laptop. I only have one user. I never switch users. Fast switch applet with a long name? what's that for?

Three: I just put the shutdown menu in the panel and I get the four options I will use: Shutdown, Restart, Suspend and Hibernate.

So, why do I dislike the whole situation? With the new icon names used in the shutdown menu, the menu looks bad. It doesn't use the gnome-session-halt/restart/suspend/hibernate icons, but it shares a harddrive icon for hibernate, or a refresh icon to restart. At least suspend escaped from this and uses a new name: sleep, so I can rename gnome-session-suspend to sleep and it's ok (themes from gnome-look.org don't have a sleep icon..)

[http://ubuntuforums.org/showthread.php?t=958184](http://ubuntuforums.org/showthread.php?t=958184)

So, basically: if we want to use shutdown menu as always have done, we get an ugly, unprofessional look. Yeah, we have a choice: to use the switch applet we don't need/like or to use an ugly shutdown menu. Nice, isn't it? All about choice..

Patrick

---

### Post by Polygon on 2008-10-25
so, how do we go about fixing this? do we report like 2 or 3 seperate bugs for each of the applets or do we just report one?

---

