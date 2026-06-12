---
title: "shutdown dialogue was changed?"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by loell on 2009-04-02
does anybody know why the shutdown dialogue was changed from a dark modal dialogue box to a normal modal one?

---

### Post by phenest on 2009-04-02
I can't remember it being different. How was it different? I do know I don't like the current way it appears. It should be more like the dialogue where you enter your password. Is that what you mean?

---

### Post by doas777 on 2009-04-02
by "dark" do you mean like when gksu darkens the screen when prompting for password?

---

### Post by loell on 2009-04-02
yes, it was somewhat dark and transparent like gksu, ever noticed that with the shutdown dialogue before? It's not critical I know, but I thought it was  a nice touch.

---

### Post by phenest on 2009-04-02
The logout dialogue should be the same. Report as bug?

---

### Post by vaibhav on 2009-04-02
Maybe it's being compared with 8.04's.

---

### Post by loell on 2009-04-02
> **phenest said:**
>  Report as bug?

not unless if it has become a design feature, reporting it as bug won't do much.

---

### Post by Bou on 2009-04-02
> **loell said:**
> yes, it was somewhat dark and transparent like gksu, ever noticed that with the shutdown dialogue before?

It never was dark, but it sure was translucid and rounded round the edges, without window title - just like gksu.

I think you should file a bug, yeah. It's really ugly in its current state.

---

### Post by forumache on 2009-04-02
it was made intentionally like that.

you should read the changelogs before applying updates.

now it is a normal dialog box, as you can work until the timeout expires.

---

### Post by Bou on 2009-04-02
Why would you want to work until a countdown expires, when you can just cancel it and start again when work is done?

---

### Post by forumache on 2009-04-02
> **Bou said:**
> Why would you want to work until a countdown expires, when you can just cancel it and start again when work is done?

I really don't know. I know that by typing

aptitude changelog fast-user-switch-applet

I get: 

fast-user-switch-applet (2.24.0-0ubuntu10) jaunty; urgency=low

  * 84_session_management.patch:
    * ...
    * Change the logout dialogs to be standard dialogs instead of special
      ones and shorten the text in them.  Also make them appear on all desktops
      and in the window switcher list incase they get lost.
    * ...

which makes me think that it was intended.

You can report it as a bug, but is was something intended (I don't know the reason why, I can simply guess).

I guess with all the things, x% of the users will agree, y% will disagree and z% will simply don't care. Ubuntu developers took an informed decision (I hope)

Beauty is in the eye of the beholder ;)

P.S. If you really want to object to this change, subscribe to [https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/352288](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/352288)

---

### Post by Polygon on 2009-04-02
i personally think it works better this way. It was kinda weird looking just having the window without any border.

---

### Post by Bou on 2009-04-02
Hey forumache, thanks for the link dude.

---

### Post by phenest on 2009-04-02
> **Bou said:**
> Why would you want to work until a countdown expires, when you can just cancel it and start again when work is done?

Yes, the timer is pointless, therefore having it as a standard dialogue is pointless. The point of invoking the dialogue in the first place is because you want to shutdown the computer, and not to give yourself 60 seconds to finish something or let it do it itself.

I've added my comment to the bug report.

---

### Post by doas777 on 2009-04-02
my guess is that this was designed for multi-user rigs. if one user requests a shutdown, the other users are informed, and given a minute to save their work, or in the worst case, cancel the shutdown if need be. i presume you would only be able to cancel if you had sudo rights.

the same may be true of the sceen darkening. i personally don't get a darker screen when I shutdown intrepid, but I *think* the dark screen is supposed to present that the dialog is running in another shell, to protect it from access by presumably malicious code. I could see an admin wanting to be able to write scripts that shut down gnome gracefully, when rebooting a server via ssh or whatever, so they would have to be able to access the dialog.

just a thought, who knows. I *Might* be right...

---

### Post by phenest on 2009-04-02
> **doas777 said:**
> my guess is that this was designed for multi-user rigs. if one user requests a shutdown, the other users are informed, and given a minute to save their work...

How will the others know if your still using it?

---

### Post by doas777 on 2009-04-02
> **phenest said:**
> How will the others know if your still using it?

in this supposed scenario, the dialog would display on all TTYs. One user would click shutdown, and the others would see the effeccts of that action.

---

### Post by amano on 2009-04-02
The old Shutdown dialog was a Ubuntu specific modification/replacement. Maybe they decided that the changes weren't worth carrying a delta to GNOME und Debian and decided to go with the GNOME standard dialog?

---

### Post by loell on 2009-04-02
> **phenest said:**
> Yes, the timer is pointless, therefore having it as a standard dialogue is pointless. The point of invoking the dialogue in the first place is because you want to shutdown the computer, and not to give yourself 60 seconds to finish something or let it do it itself.

I've added my comment to the bug report.

could you link the report?

timer is pointless!? :mrgreen:

it's designed to develop bad habits on people, leaving their computer while not yet turned off, giving potential others to cancel, and play sudoku. :twisted:

---

### Post by ktp on 2009-04-02
> **loell said:**
> could you link the report?

timer is pointless!? :mrgreen:

it's designed to develop bad habits on people, leaving their computer while not yet turned off, giving potential others to cancel, and play sudoku. :twisted:

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/352288](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/352288)

---

### Post by Polygon on 2009-04-02
> **phenest said:**
> Yes, the timer is pointless, therefore having it as a standard dialogue is pointless. The point of invoking the dialogue in the first place is because you want to shutdown the computer, and not to give yourself 60 seconds to finish something or let it do it itself.

I've added my comment to the bug report.

the timer is because they changed the way you shut down, (went from those big buttons to that tiny little menu). I assume it was becuase people maybe clicked the wrong icon and wanted to cancel what they did, because i know in intrepid i accidentally hit the wrong icon and im like 'god darn it i didn't want to shut down i wanted to log out....'

and that way if someone just hits shutdown and leaves, without clicking the OK button, it will still shut down. mac os x has done this for a while.

---

### Post by ktp on 2009-04-02
> **Polygon said:**
> the timer is because they changed the way you shut down, (went from those big buttons to that tiny little menu). I assume it was becuase people maybe clicked the wrong icon and wanted to cancel what they did, because i know in intrepid i accidentally hit the wrong icon and im like 'god darn it i didn't want to shut down i wanted to log out....'

and that way if someone just hits shutdown and leaves, without clicking the OK button, it will still shut down. mac os x has done this for a while.

I am fine with time but why can't I change it.  I don't need 60 seconds.

---

### Post by olskar on 2009-04-03
I think Mac OS have two minutes for the same thing, at least they had :)

But they also have the option to hold the Option key when they go to click on Restart, ShutDown, Log Off to bypass the timer. A nice little feature!

---

### Post by phenest on 2009-04-03
> **doas777 said:**
> in this supposed scenario, the dialog would display on all TTYs. One user would click shutdown, and the others would see the effeccts of that action.

I think you missed my point. Only one person can use a computer at a time. So the others won't know unless you actually tell them.

---

### Post by phenest on 2009-04-03
> **Polygon said:**
> the timer is because they changed the way you shut down, (went from those big buttons to that tiny little menu). I assume it was becuase people maybe clicked the wrong icon and wanted to cancel what they did, because i know in intrepid i accidentally hit the wrong icon and im like 'god darn it i didn't want to shut down i wanted to log out....'

and that way if someone just hits shutdown and leaves, without clicking the OK button, it will still shut down. mac os x has done this for a while.

How does the timer help if you click the wrong icon? There is a cancel button.

And why why would I invoke the dialogue and then walk away? That would mean my computer is still logged in and it's unattended. Not good for security.

---

### Post by phenest on 2009-04-03
> **olskar said:**
> I think Mac OS have two minutes for the same thing, at least they had :)

But they also have the option to hold the Option key when they go to click on Restart, ShutDown, Log Off to bypass the timer. A nice little feature!

With Ubuntu, if I invoke the dialogue, and click shutdown, the dialogue disappears. So isn't that bypassing the timer too?

---

### Post by uBeer on 2009-04-03
> **Polygon said:**
> the timer is because they changed the way you shut down, (went from those big buttons to that tiny little menu). I assume it was becuase people maybe clicked the wrong icon and wanted to cancel what they did, because i know in intrepid i accidentally hit the wrong icon and im like 'god darn it i didn't want to shut down i wanted to log out....'

and that way if someone just hits shutdown and leaves, without clicking the OK button, it will still shut down. mac os x has done this for a while.

Yes, I had this as well a few times, so it makes sense to me to have some sort of a confirmation that you want to shut down. On the other hand am I still irritated by seeing it when I know that I choose the right thing.

A good thing as well that you have to think about what you're doing. The dialog reminds me that I have to check that I have saved all my work.

---

### Post by doas777 on 2009-04-03
nothing to see here

---

### Post by Polygon on 2009-04-03
> **phenest said:**
> How does the timer help if you click the wrong icon? There is a cancel button.

And why why would I invoke the dialogue and then walk away? That would mean my computer is still logged in and it's unattended. Not good for security.

because if there was not a timer, even if someone did hit shutdown, and thought they hit the 'ok' button, or simply got distracted, it eventually logs out. It would be worse if he pressed 'log out' and didnt hit the 'ok' button, and his computer was jsut sitting there still logged in, waiting for someone to hit the OK, which leaves it open to MORE security issues, rather then a 60 second window in which someone has to go over to your computer and hit 'cancel'.

---

### Post by phenest on 2009-04-03
But if you've gone to the trouble of invoking a dialogue, why walk away when you've only got to click one more thing? And what stops some else, during that 60 seconds, from clicking cancel and using your account?

And what if some one invokes the shutdown dialogue, either by accident or is distracted, walks away not realising, only to come back to find the computer is turned off, and sits there scratching their head wondering why?

---

### Post by phenest on 2009-04-03
And... what if you invoke the dialogue, by accident or distracted, then it disappears under another window, and you haven't noticed it's there, then the computer suddenly wants to shut down.

And going back to the original question, what's the point of it being an ordinary dialogue window when, if it gets hidden under another window, there is no telling how long you have left.

---

### Post by forumache on 2009-04-03
> **phenest said:**
> And... what if you invoke the dialogue, by accident or distracted, then it disappears under another window, and you haven't noticed it's there, then the computer suddenly wants to shut down.

Try to make it disappear under another window, I dare you ;)

It is a "Always on top" window, it should always be visible. Even if you minimize it, it will jump back. You can move it in a corner if you want.

My point is, it is too late now to change anything. There will be always dissatisfied users. You can organize a poll, wait for results to weight your way then link to it from the bug report I posted earlier.

---

### Post by phenest on 2009-04-03
> **forumache said:**
> Try to make it disappear under another window, I dare you ;)

It is a "Always on top" window, it should always be visible. Even if you minimize it, it will jump back. You can move it in a corner if you want.
Fair enough. But what about my other points?
> **forumache said:**
> My point is, it is too late now to change anything. There will be always dissatisfied users. You can organize a poll, wait for results to weight your way then link to it from the bug report I posted earlier.

It's never too late. And it's not about being dissatisfied, but there will be a situation(s) where it's a security risk. This either needs to be configurable, or have ideas thrown at the developers.

To home users like me (and maybe you), it makes very little difference (if any), but in an office environment, it's not secure.

Perhaps having a password box appear if some one clicks cancel.

---

### Post by loell on 2009-04-03
> **forumache said:**
> 
It is a "Always on top" window, it should always be visible. Even if you minimize it, it will jump back. You can move it in a corner if you want.


this is also the thing that i'm finding it odd, why provide a minimize button, if it's gonna restore back anyway?

---

### Post by Polygon on 2009-04-03
in vista, and ubuntu, and any other os where you can accidently misclick because of their bad decision to remove the giant icons and put them in a teeny little menu , and have your computer do something you don't want is HIGHLY annoying


you say if there is a timer, then its a security risk cause someone can intercept the computer before the timer goes to 0

its an even BIGGER security risk if it has no timer, as if you walk away, then it never shuts down / logs off, and someone can come hours later and find your computer still waiting for someone to press 'ok'.

and its ANNOYING if it does the action without any confirmation, because what if you wanted to just log off, but instead you suspended your computer?

The best compromise is having a timer. Stops people from accidentally doing something they don't want, and if they walk away then in 60 seconds then it does whatever they invoked. And someone would have to be a ninja to intercept the computer in 60 seconds after someone left. Like i said, mac os x is meant to be simple and they also have the "60 second" timer shutdown/logoff thingy.

you can't please everyone

---

### Post by philinux on 2009-04-03
Personally I really like the little drop down menu, it's quicker. And, before, the dialogue used to appear under firefox or whatever was running.

That being said I cant see the point of the countdown timer. And these dialogue boxes could be nicer.

---

### Post by loell on 2009-04-03
> **Polygon said:**
> 
The best compromise is having a timer. Stops people from accidentally doing something they don't want, and if they walk away then in 60 seconds then it does whatever they invoked. And someone would have to be a ninja to intercept the computer in 60 seconds after someone left. Like i said, mac os x is meant to be simple and they also have the "60 second" timer shutdown/logoff thingy.

you can't please everyone

I'm not yet convinced though that the timer is the complementation of the misclicks of the shutdown menu. as a personal experience i haven't yet mistakenly clicked **Log-out** instead of **Shut-down** since its three items apart.

now, if they just wanna copy a mac feature, then fine i guess, just so long as timer is easily adjustable. and modal boderless window would still really be my preference.

---

### Post by hyl4me on 2009-04-03
With the lastest update,  you can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

---

### Post by loell on 2009-04-03
> **hyl4me said:**
> With the lastest update,  you can Right-click on the Shutdown button at the corner > Preferences > Uncheck "Show confirm dialogs for logout, restart and shutdown".  Then, you won't see annoying dialog. :)

thanks for letting us know.. :)

/updating..

---

### Post by zekopeko on 2009-04-03
i liked the old one's (the one's without window borders). it made you pay attention. like gksudo. i would like the old one's back.

---

### Post by Polygon on 2009-04-03
for me, the confirmation window without borders did not act like gksu, it was just a window without borders, it didn't make the screen all dark.

and loell, even though they are three items apart, log out and suspend are right next to each other. Its still easy to misclick, and for me, if i suspend my computer, i just lost any work that i was working on because suspend has never worked for me in ubuntu, and it just cuauses my comp to freeze :3

---

