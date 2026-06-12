---
title: "What desktop is this?"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by yonnie on 2016-04-26
Running Kubuntu... after running: update-manager -d, and waiting many hours, I get a bluish screen with a debian logo.  The new desktop is definitely not KDE, but during boot the display splash says Kubuntu.  What is this new to me desktop?  I was trying to upgrade from 14.04LTS to 16.04LTS, seems to have worked, but the desktop is not KDE type.

---

### Post by RobGoss on 2016-04-26
What version of Ubuntu are trying to install?

---

### Post by yonnie on 2016-04-26
The desktop is not KDE, it's an unknown.  The problem I'm asking about is the standy or suspend function.  I can't find how to turn it off.  The display goes black after about 5 minutes and then forces me to login again.  This is annoying.  I don't mind the screen trying to save power, but how do I stop the re-login crap?  Auto-Logn is turned on, the power-settings don't seem to have any settings that apply to this, where else is there adjustments to change this?

---

### Post by QIII on 2016-04-26
Hello!

Could you include an image, please?

---

### Post by ajgreeny on 2016-04-26
Possibly the plasma desktop, which is still KDE but just looks a bit different?

All this coming from someone who has not used KDE since version 3 so I may be leading you astray here, but I have looked at it in VBox and decided it is not for me so removed the VM..

---

### Post by yonnie on 2016-04-26
[ATTACH=CONFIG]268645[/ATTACH]camera:/Samsung%2520Galaxy%2520models%2520(MTP)@usb:010,005/store_00010001/DCIM/Camera/20160426_134620.jpg

---

### Post by bappy2 on 2016-04-26
it is unknown desktop

it is not KDE

---

### Post by yonnie on 2016-04-26
Other issues are I seem to have little to no control over settings.  I can't get the auto-login feature to work with login after snooze suspension.  And most important, I can't figure out how to edit network connections.  I can see settings, but can't edit or delete.  Appears to be able to add new ones, what a pita!

---

### Post by QIII on 2016-04-26
That looks exactly like Fedora 23 Workstation KDE spin.

I'll have a look at mine when I get home.

---

### Post by yonnie on 2016-04-26
Well, never mind the ethernet settings, think I figured that part out.  But how do I get a standard KDE desktop?

---

### Post by yonnie on 2016-04-26
There's a life-preserver in the "applications" menu and when I click on the it says "gnome help".  I had to re-run the update-manager -d" to get the system to operate without locking up.
So now the desktop is more interactive (when I click on things they work).  But I do not like this supposed "Gnome desktop", it is not the old Gnome that disappeared a few years ago, which I really liked.  Why call something Gnome, when it is not.  This is more like the Unity interface, which also stinks.

---

### Post by QIII on 2016-04-26
Yes, Gnome.  Not KDE.  Sorry 'bout that ...

---

### Post by yonnie on 2016-04-26
if I try sudo apt-get install kubuntu-desktop I get an attempt to install and then it says it's already installed.

---

### Post by deadflowr on 2016-04-26
Log out and in the login screen you should be able to select a desktop.

Unfortunately, it's hard to know what login screen you would have.
So I don't know where to look for it.

I am pretty sure you have to select a user first, if using gnome's login screen.
Then an cog-like icon should appear that you click on and the other desktop will show.
Or at least I think that it what happens.

---

### Post by Frogs Hair on 2016-04-26
The top panel looks like the gnome shell. When upgrading, the original distribution is upgraded even if you installed a different desktop environment later . You should have a selection(icon) on the top right of the greeter box where the password is entered .

---

### Post by grahammechanical on 2016-04-26
> Why call something Gnome, when it is not.

You are wrong there. It is Gnome 3 desktop environment & Gnome 3 shell. And it was the Gnome developers who stopped work on Gnome 2 DE & Gnome 2 panel in favour of Gnome 3. As Ubuntu uses the Gnome DE it also had to switch to the Gnome 3 DE but choose to use its own user interface shell called Unity which as you have noticed makes use of functions built into Gnome 3 DE.

I just have to tell you. When you insult my choice of desktop environment and user interface I get angry. You would too if people insulted your choice. Please do not insult other people's preferences. It is not the way things should done in the Ubuntu community.

---

### Post by ajgreeny on 2016-04-27
I totally agree with grahammechanical's comments above.

Choice is one of the great things about the *ubuntu family of OSs and Linux in general; you can more or less make the desktop look and behave the way you want. I don't particularly like the unity desktop either but I do not keep shouting that in the forums; I just use something else instead, in my case Xubuntu.

If you really liked the old gnome 2 so much, try Ubuntu-Mate, it uses the Mate desktop which is an updated fork of gnome 2 and looks identical so far as I can make out.

---

### Post by yonnie on 2016-04-27
changed to plasma at login screen.  Seems to be almost KDE.  Going to try a full upgrade via live usb.
Thanks for the help.  How do I mark this thread as solved?  Well, not yet, but I'll never find this thread again, so might as well close it.  Some unusually thin-skinned people responding, maybe it's a language translation problem, or an intolerance of other peoples preferences.

---

### Post by deadflowr on 2016-04-27
> Some unusually thin-skinned people responding, maybe it's a language translation problem, or an intolerance of other peoples preferences.

Nothing intolerant about posters wishing other poster follow [forum rules]("http://ubuntuforums.org/misc.php?do=showrules") about respecting other users.
Insulting a desktop insults users of that desktop.
> This is more like the Unity interface, which also stinks.

[s]That is not respectful in the least.[/s]
Sorry, meant to say that this doesn't seem very respectful.

---

### Post by yonnie on 2016-04-28
Deadflower, your response sems more like impositional religiosity on your part rather than the free-flow of opinion and discussion from the intercourse of communication.  In your case, only your opinion is important and anyone else is non-important.  So would the use of Unity or Gnome be better expressed as foul aroma?  A desktop interface should be intuitive easy and quick.  Although there has been much work and labor put into Unity, Gnome and Plasma, they fail with the above stated goals.  Solaris 10, System V and RedHat 7 were far easier desktops in many respects.  I understand there seems to be a goal of making phones, tablets and work-stations all use a common desktop, I'm not a member of that group.  A good working wheel was invented many centuries ago and by mutual agreement it was decided that round rolls better than square.

---

### Post by QIII on 2016-04-28
What deadflowr is imposing is the application of the Forum rules, which apply to all.

Everyone take a breath, calm down a bit and relax.

Opinions about the suitability of DEs are just that: opinions.  Statement of opinion as fact, especially when that opinion can be taken as an attack on the choices of others, is bound to cause friction and hard feelings.  That is counter to the notion of "ubuntu" and is, therefore, discouraged here.

Take care not to drift off into Unity bashing, lest other members of the staff choose to send this thread to Recurring Discussions.

---

### Post by mikodo on 2016-04-28
Hey; I expect you *know,* that saying the Ubuntu's desktop *stinks* on an Ubuntu Forum is disrespectful to Ubuntu and the people who use it, support it, like it, and frequent this forum.

*Free-flow opinion* or free speech, is endorsed and encouraged here. Not un-politeness.

[https://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](https://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

[I]"Ubuntu is often translated as humanity towards others"

[/I]That statement is taken seriously here.

'nuff-said

---

### Post by yonnie on 2016-04-28
This thread got so far off-track it's insane.  The main question that started it, What DE do I have got answered, so thanks for the help.

---

