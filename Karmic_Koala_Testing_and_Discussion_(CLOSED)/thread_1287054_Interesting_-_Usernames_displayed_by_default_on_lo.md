---
title: "Interesting - Usernames displayed by default on login now."
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-09
To me this eliminates 50% of any security that one may have in place on their system.

This is not haw it was done previously and I would think that this should be configurable in "Administration >  Login Window".

Comments?

---

### Post by Dark Aspect on 2009-10-09
> **emarkay said:**
> To me this eliminates 50% of any security that one may have in place on their system.

This is not haw it was done previously and I would think that this should be configurable in "Administration >  Login Window".

Comments?

Its not hard to find out someone's username. It might limit some security but I HIGHLY doubt that it eliminates 50% of your login security.

---

### Post by FuturePilot on 2009-10-09
If someone with malicious intent has physical access to your machine, it's game over anyway.

---

### Post by emarkay on 2009-10-09
Aw come on, I know that - I am talking about the "script kiddie" sort of PITA annoyance.  I just prefer the option to type in BOTH my username and password.

---

### Post by Longinus00 on 2009-10-09
> **emarkay said:**
> Aw come on, I know that - I am talking about the "script kiddie" sort of PITA annoyance.  I just prefer the option to type in BOTH my username and password.

While it may indeed be your preference, claiming it has some sort of security benefit is disingenuous at best.

---

### Post by emarkay on 2009-10-09
> **Longinus00 said:**
> While it may indeed be your preference, claiming it has some sort of security benefit is disingenuous at best.

Oh well, What do I know? My dad saves his cookies and passwords on his PC and he's never had a problem either...

I just want it the way it was before, for the reason I mentioned.  IIABDFI!

Bug Filed:  [http://ubuntuforums.org/showthread.php?t=1287054](http://ubuntuforums.org/showthread.php?t=1287054)

---

### Post by 16sinker on 2009-10-09
Why have the option to enable automatic login if your going to have to use that very same password to unlock the keyring. I use auto login to speed up boot time, since it takes up to 90 seconds to login to Karmic at this point. I'm hoping as the final release approaches the login time will be at least half that since Jaunty login time was under thirty seconds on this old computer I use.

---

### Post by ljrmorgan on 2009-10-09
> **emarkay said:**
> To me this eliminates 50% of any security that one may have in place on their system.

This is not haw it was done previously and I would think that this should be configurable in "Administration >  Login Window".

Comments?

From what I remember (haven't restarted for a few hours, and I never really pay attention), it doesn't display my username, it displays my full name.

If you go to System > Administration > Users and Groups then you can change it there. Would that solve your 'problem'?

---

### Post by garba on 2009-10-09
> **longinus00 said:**
> while it may indeed be your preference, claiming it has some sort of security benefit is disingenuous at best.

+1

---

### Post by partsdale on 2009-10-10
> **garba said:**
> +1
+1

---

### Post by Tibuda on 2009-10-10
```
ls /home
```
it displays all usernames. you can also browse it using nautilus from a live cd.

it is not a security issue.

---

### Post by emarkay on 2009-10-10
> **danielrmt said:**
> ```
ls /home
```it displays all usernames. you can also browse it using nautilus from a live cd.  it is not a security issue.

Agreed,  it's not a security issue and has not been categorized as such.

The point is on a powerup, you get a username and there should be an option to disable it/have it perform as was in Jaunty prior. So please quit with the smarmy "security" posts already!

---

### Post by days_of_ruin on 2009-10-10
Its only a security issue if you have your password written down right next to the computer, and rely on no one knowing your username. Btw, if anyone who has physical access to your computer knows about recovery mode they can **change** your login password in two minutes.

---

### Post by autark on 2009-10-10
It might not be a big security issue, but displaying the list makes it a little bit easier for people to find out things about your computer without even having physical access - just by watching your screen while you're logging in. 

 The user list can also be an annoyance if you have many users and you have to scroll to find yours.  Of course, the new behavior is probably going to be welcomed by most people, but it's a shame that there is no way to get the old behavior back, for those who prefer it that way, whatever their reasons. 

 This is one of the issues that make me think twice about moving to Karmic.

---

### Post by Mr. Picklesworth on 2009-10-10
> **autark said:**
>  The user list can also be an annoyance if you have many users and you have to scroll to find yours.  Of course, the new behavior is probably going to be welcomed by most people, but it's a shame that there is no way to get the old behavior back, for those who prefer it that way, whatever their reasons. 

I could have sworn Fedora switched to the "Other..." option when you started typing a username, so both use cases were covered. Either I'm forgetting, or that never landed upstream.

Oh well, for what it's worth, you can scroll to a certain user pretty quickly by typing out your first name when the list is selected. It's just like any other GTK list box; start typing and a little search box appears to the bottom right.

---

### Post by seeker5528 on 2009-10-10
> **autark said:**
> It might not be a big security issue, but displaying the list makes it a little bit easier for people to find out things about your computer without even having physical access - just by watching your screen while you're logging in.

If they could watch your screen, wouldn't it seem likely they could log your keystrokes?

Don't know what your are trying to say there. 

> The user list can also be an annoyance if you have many users and you have to scroll to find yours.  Of course, the new behavior is probably going to be welcomed by most people, but it's a shame that there is no way to get the old behavior back, for those who prefer it that way, whatever their reasons.

I doubt there are a high percentage of users that have *that* many user accounts.

As long as I can type my user name and am not forced to choose it off the list, I don't really care if the user list is there or not. There was a thread about the ability to type in a user name being broken, but I haven't seen that on any of my machines.

Later, Seeker

---

### Post by SixedUp on 2009-10-10
You can't get exactly the old behaviour, and the login configuration GUI is rather limited, but if you type the following into a terminal, on a single line, then you will get very close:

```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```

There is a bug open again Gnome to get rid of the annoying "Log In" button that you have to press to get to the login field, but I dont know if a solution for that will make Karmic.

---

### Post by Gramps on 2009-10-12
There is an extra step over the old way but in my opinion it is better than the user list way. Thanks SixedUp


> **SixedUp said:**
> You can't get exactly the old behaviour, and the login configuration GUI is rather limited, but if you type the following into a terminal, on a single line, then you will get very close:

```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
```

There is a bug open again Gnome to get rid of the annoying "Log In" button that you have to press to get to the login field, but I dont know if a solution for that will make Karmic.

---

### Post by naxa on 2009-10-12
i have a feeling like if we were mimicing a 8 year old windows login screen

---

### Post by JerecDrak2 on 2009-10-12
I just want to see my name with a capital letter, is that so much to ask?

---

### Post by autark on 2009-10-12
> **seeker5528 said:**
> If they could watch your screen, wouldn't it seem likely they could log your keystrokes?
 

I'm not afraid of that, it's the privacy implications of showing the user list I'm thinking of. If I have to log in somewhere in public, I don't want the list to be shown, is that so unreasonable?

---

### Post by zombiepig on 2009-10-12
Anyone know how to hide away the 'Other' option?

---

### Post by Mr. Picklesworth on 2009-10-12
Just so you folks know, /etc/passwd is pretty easily accessed and lists all users on the system. Pretty easy to figure out who has a password to log in from that.
(And, for that matter, I assume one could run a password cracker with a copy of /etc/shadow, against its one-way hash, and be completely unhindered by forced waiting that gets imposed by the login command).

---

### Post by cyberkilla on 2009-10-12
Only one user account on my laptop. Why must I first select my username before I can enter my password?

The enter key doesn't cut it, so I have to use the mouse to select it.

---

### Post by kaitwospirit on 2009-10-12
You're supposed to be able to use the enter key, if I remember correctly. It's a bug that the keyboard isn't working for that.

---

### Post by twisted_steel on 2009-10-12
> **kaitwospirit said:**
> You're supposed to be able to use the enter key, if I remember correctly. It's a bug that the keyboard isn't working for that.

That is correct.  See here: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/447049](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/447049)

---

### Post by Choad on 2009-10-12
> **FuturePilot said:**
> If someone with malicious intent has physical access to your machine, it's game over anyway.
QFT x 10000000000

seriously, there comes a point when you have to take a stand on usability vs. security

---

### Post by Longinus00 on 2009-10-12
> **JerecDrak2 said:**
> I just want to see my name with a capital letter, is that so much to ask?

System->Administration->Users and Groups

Click your name and hit properties to adjust it.

---

### Post by seeker5528 on 2009-10-12
> **autark said:**
> I'm not afraid of that, it's the privacy implications of showing the user list I'm thinking of. If I have to log in somewhere in public, I don't want the list to be shown, is that so unreasonable?

I think it's perfectly reasonable to *want* it not to be shown, no reason needed, 'nough said.

If you were to say you were concerned about what the user list may reveal about *you*, I wouldn't have given it a thought.

But the wording was:

"displaying the list makes it a little bit easier for people to find out things about your computer" 

Which left me scratchin' my head a little bit.

Later, Seeker

---

### Post by shaggy999 on 2009-10-12
I think I can see where showing a username list could cause a problem. Let's say you have a computer that you share with other people and you have accounts for each person. But then you had some kind of "porn-browsing" account. Beforehand nobody might know about this account unless they specifically hunt for it. But with the new login screen they get a list like this:

John
Mary
PornBrowser


Then everybody knows about it. Now in this situation I would say to use the "private browsing" mode of firefox in your own account, or switch to the "guest" account but it's an example of a problem that can arise when you show account names and why some people might not want them. Or if you absolutely have to have another account, don't call it "PornBrowser". But just seeing there's another account on there might make someone suspicious.

---

### Post by cyberkilla on 2009-10-13
From [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html:](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html:)
> 
Changing your GDM was once a simple processes with an excellent GUI behind it. With Ubuntu 9.10 Karmic Koala the **GDM has been rewritten to properly take advantage of xsplash**, Ubuntu's new X based boot. While these changes will significantly improve boot time, customizable GDMs are going to suffer. Ubuntu developers have already stated that a level of customization once offered with the old GDM will not be available for Karmic.

---
Update: It looks like the blog was wrong. Nevertheless, I'm still interested to know whether the following is true.
---
Does this mean there is no way, in the foreseeable future, to set a GDM theme which does anything more than swapping out the GTK/Metacity theme and wallpaper?

Not that I ever made GDM themes myself, but weren't there were xml files specifying the position of the login box, hostname, etc? Is there nothing of this nature now?

---

### Post by Mr. Picklesworth on 2009-10-13
> **cyberkilla said:**
> From [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html:](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html:)


Is this true? It's just an Ubuntu limitation? Damn. Why is it that every change Ubuntu makes to *anything* makes it more restrictive and less functional?

That is a really ugly release note.

No, it is not a change in Ubuntu specifically, or a limitation ;)
GDM *has* been rewritten. In fact, it was rewritten with GNOME 2.20, but Ubuntu has stuck with the old one until now.

The rewrite permits goodies like xsplash and is generally a better, more accessible and more consistent / integrated experience.

Nobody has written a configuration tool yet because the technology has changed quite a bit (specifically, it now uses modern GNOME desktop technologies instead of a flat config file for GDM alone). A more powerful one than the current would probably be accepted, at least into Ubuntu, if it was well enough designed.

Fedora does configuring GDM quite nicely, at least for appearance-related stuff. They have patched in a Make Default button to most of the gnome-control-center tools, so making a particular wallpaper or theme default changes GDM as well. I think, upstream, the hope is for something similar (where existing tools are reused) but more flexible and magical.

---

### Post by cyberkilla on 2009-10-13
> **Mr. Picklesworth said:**
> That is a really ugly release note.

No, it is not a change in Ubuntu specifically, or a limitation ;)
GDM *has* been rewritten. In fact, it was rewritten with GNOME 2.20, but Ubuntu has stuck with the old one until now.

The rewrite permits goodies like xsplash and is generally a better, more accessible and more consistent / integrated experience.

Fair enough:) Thanks for responding.

Might be of interest to some:
[http://library.gnome.org/admin/gdm/2.26/overview.html.en_GB](http://library.gnome.org/admin/gdm/2.26/overview.html.en_GB)
> The Face Browser is the interface which allows users to select their username by clicking on an image. This feature can be enabled or disabled via the /apps/gdm/simple-greeter/disable_user_list GConf key and is on by default. When disabled, users must type their complete username by hand.
I haven't had time to test it, but it seems to be specifically for this version of GDM.

---

### Post by SixedUp on 2009-10-13
> **cyberkilla said:**
> 
I haven't had time to test it, but it seems to be specifically for this version of GDM.

See my post a couple of pages back in this thread for how to enable this. It works OK, but you still need to mouse-click a "Log In" button before being able to enter your username and password as in previous releases. There is a usability bug open on Gnomes bugzilla requesting the button be removed or the sequencing altered, but not clear if that will be actioned, or if so, in time for Karmic.

---

### Post by cyberkilla on 2009-10-13
> **SixedUp said:**
> See my post a couple of pages back in this thread for how to enable this. It works OK, but you still need to mouse-click a "Log In" button before being able to enter your username and password as in previous releases. There is a usability bug open on Gnomes bugzilla requesting the button be removed or the sequencing altered, but not clear if that will be actioned, or if so, in time for Karmic.

Sorry, I must have missed it :) It's a shame it can't automatically realise that I'm the only user and focus the password box for me ;)

---

### Post by days_of_ruin on 2009-10-13
@OP, just install the old gdm then:
```
sudo apt-get install gdm-2.20
```

---

### Post by seeker5528 on 2009-10-14
> **Mr. Picklesworth said:**
> Nobody has written a configuration tool yet because the technology has changed quite a bit (specifically, it now uses modern GNOME desktop technologies instead of a flat config file for GDM alone). A more powerful one than the current would probably be accepted, at least into Ubuntu, if it was well enough designed.

If it's so modern, how come it doesn't pick up the available X sessions and give an option what session to choose? :twisted:

Later, Seeker

---

### Post by vbundi on 2009-10-15
I HATE how it does this now.

I never thought of installing old GDM, I do however have a fix if you want to use the new gdm still.

I got this from a Fedora forum as I noticed Fedora has been using it a while and I figured someone else had to hate it as much as I did.

gconftool-2 --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --direct --type bool --set /apps/gdm/simple-greeter/disable_user_list true


^ All one one line of course.

Obtained from [http://forums.fedoraforum.org/showthread.php?t=227336](http://forums.fedoraforum.org/showthread.php?t=227336)

It still sorta sucks.. you can't just hit user ENTER password ENTER.

So I may revert or revolt, as I hate this change...

+1 to the faster bootup tho.

---

### Post by vbundi on 2009-10-16
> **days_of_ruin said:**
> @OP, just install the old gdm then:
```
sudo apt-get install gdm-2.20
```

I have tried this, you must do it from netroot in recovery mode or it complains about gvfs permissions when installing gdm-2.20.  Unfortunately though, it doesn't work still... I get a "low graphics mode" error after installing gdm-2.20.

---

### Post by narcus on 2009-10-20
I too really miss the 9.04 behaviour. I'm so used to just type the password right away, now I'm typing my password for anyone next to me to see because it goes into the username field in clear text instead.

I saw your Bug 447615 was marked invalid. I think it should be a candidate for One Hundred Papercuts instead.

---

### Post by T.R. on 2009-10-28
I found a way to "fix" it, ```
sudo -u gdm gconftool-2 --type bool --set /apps/gdm/simple-greeter/disable_user_list 'true'
``` but this doesn't fix the fact that you have to do more to log in than in Jaunty.

I know Canonical is trying to make it "user friendly" but they're forgetting who their users are. If I wanted the developers to restrict what I can do with my system, even with minor things, I would have gone with Windows or Mac.

---

