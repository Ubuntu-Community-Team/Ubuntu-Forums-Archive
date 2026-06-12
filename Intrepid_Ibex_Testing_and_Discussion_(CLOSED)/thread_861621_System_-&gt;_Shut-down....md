---
title: "System -&gt; Shut-down..."
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-07-16
What does everyone think about the revamped System menu?

I mean, specifically, the three separate options for managing your session: Lock Screen, Log Out and Shut Down...

First, let's talk about the good points:

Personally, I love the new lock-screen option: I always wished there was an easier way to do this without using the keyboard short-cut. It's a good thing for security.

I also like the way the shut-down option gives feedback, like, "you are logged in as..." and "... will automatically shut-down in ..."


That said however, shut-down gives me five options, (Suspend, Hibernate, Restart, Cancel and Shut Down), all on one straight line, inside a weird window with a close button, which, to be honest, I'm rather scared to press (What will it do!?). 


I thought the reasons for making new entries were it was meant to be simpler for the people who "walk-away", but I think they made it a hell of lot more confusing for everyone else.

Anyone else see this as a regression? Who preferred the old "Dim-the-screen-because-this-is-really-important" vs the new "here-is-a-small-box-and-quick!-look-because-you-have-t-minus-sixty-seconds-to-notice-it"


I know it isn't about what "I" like, which is why I'm asking. Is this new way good; is it here to stay?

---

### Post by BwackNinja on 2008-07-16
I liked the old way a bit better too, the lock screen thing there is nice too (though I may never use it). The old one had pictures :D and did seem more important-looking. Now it just seems like another window and I'm guided by much smaller text filled buttons instead of the large pictures I'm used to. May be better in the long run, but for now it just seems a bit odd.

---

### Post by Nullack on 2008-07-16
I think the blueprint is decent, the implementation so far is bugged though

---

### Post by olskar on 2008-07-16
Got a link to blueprint? :)

---

### Post by ronacc on 2008-07-16
here is a link to the blueprint  [https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy](https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy)    you can thank BwackNinja for the link , I just cut and pasted it .

---

### Post by mc4100 on 2008-07-16
Lol, from the link ....
"Revamp the logout dialog"
I didn't even notice... o_0

---

### Post by cariboo on 2008-07-17
I prefer the previous version, the way it is set up now, a newbie is never going to be able to figure how to shut down his computer unless there is a huge arrow pointing it.

Jim

---

### Post by ronacc on 2008-07-17
the Ubuntu dev's never seem to follow the "if it ain't broke don't fix it " principle .

---

### Post by Gina on 2008-07-17
I prefer the old system as in Hardy - can't see what's wrong with it.

---

### Post by ronacc on 2008-07-17
if you read the linked blueprint the devs think the old way confuses newbes . yeah right and a shutdown that dosen't shutdown don't confuse them!

---

### Post by plun on 2008-07-17
> **ronacc said:**
> here is a link to the blueprint  [https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy](https://blueprints.launchpad.net/ubuntu/+spec/exit-strategy)    you can thank BwackNinja for the link , I just cut and pasted it .

Destroying Spit and polish....:)

[https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish](https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish)

[IMG]http://pici.se/pictures/WKJXYAbXZ.png[/IMG]

:confused:

---

### Post by Gina on 2008-07-17
> **ronacc said:**
> if you read the linked blueprint the devs think the old way confuses newbes . yeah right and a shutdown that dosen't shutdown don't confuse them!Precisely!!! :confused:

---

### Post by BwackNinja on 2008-07-17
Poor spit and polish, it looked nice and took advantage of the murrine rgba engine...

At least this wasn't the only thing that it did (but then again, there is killall-gksu which is taking away all gksu windows, another thing spit and polish did) but they're still trying to get the spec for notification icons changed, which would allow for a fully working rgba-driven desktop (other than openoffice, unless 3.0 works around this problem).

---

### Post by madjr on 2008-07-17
the devs know what **blackbox** testing is ?

---

### Post by almostlinux on 2008-07-17
clearly these are the gnome defaults ... guess it would be replaced with ubuntu custom once gnome is frozen

---

### Post by scradock on 2008-07-17
On a related matter, the "Leave Now" panel applet (person walking off-screen to right....) now gives only a subset of the options we've all been talking about, so you literally can't access shutdown or restart from it any more. It used (Oh, two days ago) to lead to the standard exit-choices screen; now there are 3 buttons, Switch user (which closes the X session and dumps you at the login screen); Cancel, which closes the dialog without changing anything, and Log out - which does precisely what Switch user does.....

The only way to use it to restart or close down is to choose these from the menu on the login screen. Waste of time, if you ask me.......

---

### Post by BCurtisWX on 2008-07-17
I don't think this was clarified, but when I go to the actual "shutdown" button, it just sends me to the login screen, and I have to hit shutdown from THERE in order to shut the computer down.  I really hope its just my computer causing that issue, but its really bad.

---

### Post by ronacc on 2008-07-18
its not your computer its some idiots idea of how shutdown should now work.

---

### Post by z0idberg on 2008-07-18
Oh, so it was a feature! I just assumed something was broken...

Some of the blueprint seems to make sense (I must admit I didn't study it very closely), but to me it seems they're overthinking things. Actually, when I found this thread I immediately suspected someone had been reading the Joel Spolsky article and sure enough; he is quoted in the specification! I can't help but sometimes think of the Ubuntu developers as kind of like the wizards in Terry Pratchett's Discworld books; as soon as they hear about a new idea or concept, they will immediately pursue that idea with great enthusiasm, generally spreading chaos and disaster wherever they go :).

The specification says:
> "For many occasions where the computer needs restarting, such as a kernel update, Ubuntu can offer a transitory interface for doing it (such as an alert, or a menu item in the relevant program). The remainder of cases will be rare enough that people will not mind logging out before choosing the Restart command (or, alternatively, using a terminal command).
One example I can think of is someone who is dual-booting Ubuntu and Windows. Especially someone who is just trying Ubuntu out might want to reboot often. And even if that isn't reason enough... like people said already: Shutdown that doesn't shutdown makes no sense. Why fix it if it ain't broken?

---

### Post by Nullack on 2008-07-18
Surely it cant be a feature. The UI makes no sense with those options. It has to be a bug, or someone put LSD into the water supply.

---

### Post by spamzilla on 2008-07-18
If this crazy idea gets into Intrepid final, I guess I'll have to get used to using terminal to shutdown or suspend/hybernate.

+1 for this idea to be reverted.

---

### Post by Gina on 2008-07-18
> **scradock said:**
> On a related matter, the "Leave Now" panel applet (person walking off-screen to right....) now gives only a subset of the options we've all been talking about, so you literally can't access shutdown or restart from it any more. It used (Oh, two days ago) to lead to the standard exit-choices screen; now there are 3 buttons, Switch user (which closes the X session and dumps you at the login screen); Cancel, which closes the dialog without changing anything, and Log out - which does precisely what Switch user does.....

The only way to use it to restart or close down is to choose these from the menu on the login screen. Waste of time, if you ask me.......I mentioned this BUG in another thread.  It's a real pain.  Totally useless for a final release as most new users would think there was no way to shutdown from there and simply turn off the computer. VERY BAD INDEED.  Surely this must be an interim while they sort out the new proper system.

Not that there was anything wrong with the old system - I thought it looked nice and colourful (at least using the human-murrine theme).

I do wish they wouldn't waste time changing something that's fine - at least in my opinion and those of many others!  There are other things that could do with refining.

---

### Post by olskar on 2008-07-18
And they are removing the "Big Red Button"? How many of you goes into System->Quit when turning off? I know I don't..
I also don't like the idea of making the account switching applet invisible if not needed, if it is not needed let people remove it from the panel instead! To me it looks like an unpleasant development having lots of things that are "invisible if not needed".

---

### Post by Hairy_Palms on 2008-07-18
they are the gnome default dialogs, theyve always been in ubuntu if you tick 
/apps/panel/global/upstream_session in gconf i personally prefer them, the shutdown button shutsdown the computer in hardy, so this is an ibex bug if its sending you to the GDM screen. the buttons should do exactly what they say on the label,
that said, i think having switch user under logout is counter-intuitive.

---

### Post by philinux on 2008-07-18
I put the big red button back on the panel. 

Only to find out the truth, there is no shutdown. :confused:

I have a launcher now with sudo reboot.

This "feature" has got to go and soon.

[edit] A bug has been raised for this.
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/248677](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/248677)

---

### Post by ronacc on 2008-07-18
there actualy is a shutdown it is hidden under options on the gdm login screen , and the purpose of this is to not confuse newbes ??????????? sounds like  Nullack is right about LSD in the water supply  or else they are smoking something a lot better than I can get ahold of .

---

### Post by philinux on 2008-07-18
> **ronacc said:**
> there actualy is a shutdown it is hidden under options on the gdm login screen , and the purpose of this is to not confuse newbes ??????????? sounds like  Nullack is right about LSD in the water supply  or else they are smoking something a lot better than I can get ahold of .

Yep, thats been there since the dawn....

---

### Post by ronacc on 2008-07-18
I was refering to the fact that that shutdown works as opposed to the one under the system menu or the quit button which dosent.

---

### Post by philinux on 2008-07-18
> **ronacc said:**
> I was refering to the fact that that shutdown works as opposed to the one under the system menu or the quit button which dosent.

Sorry quite. Very convoluted. I added a comment to the above bug that restart does exactly the same. :confused:

---

### Post by Gina on 2008-07-18
I have been to launchpad and added my comments as follows :- > Same here. Quit goes to the logout screen with NO shutdown or restart option. Most newer users would just switch off assuming no simple way to shut down or restart. Experienced users will know how to use the command line or that going to the logout/login screen provides an Options button that THEN (at last) gives options of shutdown or restart.

If this isn't fixed by final release then Ubuntu will get the reputation of not having a software shutdown/restart facility and users will resort to using the hardware buttons on the front of their computers! THIS IS NOT GOOD!!
I feel strongly about this.

---

### Post by autocrosser on 2008-07-18
Looks like the gnome devs have been smokin' the same stuff that Microslosh devs have been using for years now ;)

Honestly, this is just as bad as having to shut down at the Start menu......

I want to see three buttons--Log-out, reboot & shut-down

How simple is that?

---

### Post by ronacc on 2008-07-18
I filed this as bug# 248677  , I see several of you have confirmed and commented thanks . ;)

---

### Post by Gina on 2008-07-18
And thank you ronacc for filing the bug :)

---

### Post by stijngysemans on 2008-07-18
this is standard gnome, as mentioned above. this is not a feature. the blueprint you are referring to is not implemented yet.
No need to file a 'bug', ubuntu will get is normal logout back after a while. This happened also on hardy en gutsy.

---

### Post by plun on 2008-07-18
> **autocrosser said:**
> Looks like the gnome devs have been smokin' the same stuff that Microslosh devs have been using for years now ;)



Well, I hope they found better stuff to smoke in Istanbul....:)

The Microslosh stuff seems to be dangerous.

---

### Post by olskar on 2008-07-18
> **stijngysemans said:**
> this is standard gnome, as mentioned above. this is not a feature. the blueprint you are referring to is not implemented yet.
No need to file a 'bug', ubuntu will get is normal logout back after a while. This happened also on hardy en gutsy.

Glad to hear!

---

### Post by ronacc on 2008-07-18
strange I have run every dev version of ubuntu from dapper on from the day of repo opening and have never bumped into this particular behavior before .

---

### Post by galileon on 2008-07-18
do i even need to say I think its a bad idea? okay, here goes: ITS A BAD IDEA! its gonna confuse the hell outta me!

---

### Post by Mr. Picklesworth on 2008-07-18
It should be noted that the 'normal' dialog is also quite clumsy. It is not discoverable, for example, that System -> Quit allows one to enter sleep mode, lock the screen or switch users. None of those three options bear any relation to ending the session; merely pausing it.

Also, that dialog still needs a "save my session" checkbox; session saving is another very hidden feature...

---

### Post by autocrosser on 2008-07-19
Yes--very interesting--I've been around from Warty & have not seen a dialog like this one--guess I never saw it in Dapper, Edgy, Feisty, Gutsy or Hardy--I use the testing as a daily & this is a new one on me.......:neutral:

> **stijngysemans said:**
> this is standard gnome, as mentioned above. this is not a feature. the blueprint you are referring to is not implemented yet.
No need to file a 'bug', ubuntu will get is normal logout back after a while. This happened also on hardy en gutsy.

---

### Post by linux6994 on 2008-07-19
Thanks for clarifying the new shutdown method, I thought I was going nuts. I have the same scenario on both of my desktops. Progress is the same everywhere "3 steps forward and 2 steps back":)

---

