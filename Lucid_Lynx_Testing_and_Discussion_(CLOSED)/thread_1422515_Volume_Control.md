---
title: "Volume Control"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kestal on 2010-03-03
So it appears that after trying to remove clutter from my lucid alpha 3 (up to date as of now), I somehow misplaced my volume applet that is in the notifications.

I removed and re-added the notification applet. The only thing in that applet is my nm-applet. Seeing as its no longer in the list of 'add to panel', I am at a loss.

Any suggestions?

---

### Post by ElSlunko on 2010-03-03
It's part of the indicator applet now.

---

### Post by kestal on 2010-03-03
> **ElSlunko said:**
> It's part of the indicator applet now.

Eee. Thanks.. I just noticed that. ._.

---

### Post by theozzlives on 2010-03-05
When upgrading from Karmic to Lucid, the Volume is not in the notification area or "add to panel". Where'd it go?

---

### Post by Merk42 on 2010-03-05
Into the indicator applet

---

### Post by theozzlives on 2010-03-05
> **merk42 said:**
> into the indicator applet

what?!

---

### Post by anders_c_ on 2010-03-05
install the "indicator-sound" package

---

### Post by zika on 2010-03-05
Even with indicator sound installed and up-to-date I do not have volume-control unless I start gnome-volume-control-applet (in StartUpApps, for example) myself...

---

### Post by ubername on 2010-03-05
The icon for the volume control does not seem to be in many of the themes now. Ambience and Radiance have it, clearlooks (for example) does not.

---

### Post by Robertjm on 2010-03-05
Right click on the menu bar and choose "Add to Panel" and then scroll down to the volume icon, or whatever it's called (I removed mine to write the post, and now I can't find it to add back).

---

### Post by ybytyruzu on 2010-03-05
I installed "indicator applet" (add to panel) and there is Volume control,but with the "envelope icon", and is no option to display only the volume control

---

### Post by anders_c_ on 2010-03-05
uninstalling "indicator-messages" should remove the envelope

---

### Post by zika on 2010-03-05
> **Robertjm said:**
> Right click on the menu bar and choose "Add to  Panel" and then scroll down to the volume icon, or whatever it's called  (I removed mine to write the post, and now I can't find it to add  back).There is no Volume in list for Add...

---

### Post by ybytyruzu on 2010-03-05
Yes, there is no Volume Control on Add to panel, is in Indicator Applet

---

### Post by Robertjm on 2010-03-05
Used to be a Thank You button, but I don't see it anymore so I'll just say, "Thank You" to ybytyruzu for his last post. I was stuck on finding that too! :-)

---

### Post by theozzlives on 2010-03-06
K, I found it but there's no speaker icon. No matter the volume control on my laptop is sufficient until they get it fixed. What's with the purple?! I wanna use my custom xsplash.

---

### Post by grandtoubab on 2010-03-06
That is a known bug
[https://bugs.launchpad.net/ubuntu/lucid/+source/indicator-applet/+bug/533026](https://bugs.launchpad.net/ubuntu/lucid/+source/indicator-applet/+bug/533026)

---

### Post by ronacc on 2010-03-06
I am constantly astounded at what some idiot thinks will be cute . I want my panel volume control back . I remove the indicator applet because it does nothing I want , I use my preffered chat program which is not empathy , I don't use evolution and I don't microblog .

---

### Post by ybytyruzu on 2010-03-07
I removed indicator-messages and now I only have the volume control indicator...:D

---

### Post by Mr. Picklesworth on 2010-03-07
> **ronacc said:**
> I am constantly astounded at what some idiot thinks will be cute . I want my panel volume control back . I remove the indicator applet because it does nothing I want , I use my preffered chat program which is not empathy , I don't use evolution and I don't microblog .

Just so you know, the indicator applet is gradually replacing the notification area / system tray. Volume control, battery and bluetooth are in there. Lots of applications have been moved to support it as well, including Rhythmbox and Transmission.

So, don't blame the applet for its contents or you'll find your panel descending into uselessness ;)

---

### Post by LKjell on 2010-03-07
> **Mr. Picklesworth said:**
> Just so you know, the indicator applet is gradually replacing the notification area / system tray. Volume control, battery and bluetooth are in there. Lots of applications have been moved to support it as well, including Rhythmbox and Transmission.

So, don't blame the applet for its contents or you'll find your panel descending into uselessness ;)

There should be a fall back mechanism otherwise a lot of stuff will break in Ubuntu.

---

### Post by dagrump on 2010-03-07
I feel as if I woke up to Steve "the mock-turtle necks" version of linux, you will take what we give & like it. I don't like the indicator applet, I used to remove it. Now if I remove I have no volume control.
This is becoming more effort to get things back to a usable state then it's worth. I'm worried WTH!! are they going to jack with next?

---

### Post by theozzlives on 2010-03-08
> **Mr. Picklesworth said:**
> Just so you know, the indicator applet is gradually replacing the notification area / system tray. Volume control, battery and bluetooth are in there. Lots of applications have been moved to support it as well, including Rhythmbox and Transmission.

So, don't blame the applet for its contents or you'll find your panel descending into uselessness ;)

Everything else is in the notification area, deluge, Amarock, battery, Network Manager... just not volume.

---

### Post by rajeev1204 on 2010-03-08
So what exactly is this indicator applet supposed to indicate ?

I havent figured it out since Karmic.Also, anyone know why the cd- in or aux which was present before in 9.04 has been removed from the volume control?

How does one use a tvtuner and get sound out of it ? Internal audio is through cd - in or aux sliders both of which are absent from it.

---

### Post by Mr. Picklesworth on 2010-03-08
> **rajeev1204 said:**
> So what exactly is this indicator applet supposed to indicate ?

Now, it indicates anything! We care about two separate categories right now: system and application indicators. Applications can create their own indicators, and messaging apps are encouraged to extend the messaging indicator (which is, itself, an application indicator).

> **theozzlives said:**
> Everything else is in the notification area, deluge, Amarock, battery, Network Manager... just not volume.

It's a gradual transition. Unlike a lot of other things, though, this *will* get done because there is interest in it all over the place. It's working with a spec from KDE4, for example :)

Lots of information here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

---

### Post by rajeev1204 on 2010-03-08
> **Mr. Picklesworth said:**
> Now, it indicates anything! We care about two separate categories right now: system and application indicators. Applications can create their own indicators, and messaging apps are encouraged to extend the messaging indicator (which is, itself, an application indicator).



It's a gradual transition. Unlike a lot of other things, though, this *will* get done because there is interest in it all over the place. It's working with a spec from KDE4, for example :)

Lots of information here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

Hello Mr Picklesworth,
So does this mean, it will indicate update notifications? I somehow want the update notifications somewhere instead of the update pop up window which is annoying.

When you say apps can create their own indicators, how exactly will this behaviour work?

thanks
rajeev

---

### Post by theozzlives on 2010-03-08
> **rajeev1204 said:**
> Hello Mr Picklesworth,
So does this mean, it will indicate update notifications? I somehow want the update notifications somewhere instead of the update pop up window which is annoying.

You can turn that off, and I tried my bluetooth and it's still in the Notification Area.

---

### Post by cyberkilla on 2010-03-09
FYI, if you use the GNOME vanilla session, you won't have a volume icon, but the indicator applet doesn't seem to work. The old volume icon should probably be added back for that straccialla (past caring about the spelling) session. Honestly, I don't know why they couldn't have just called it "GNOME Vanilla Session" or something less of a pain in the 4$$ to say.

---

### Post by ronacc on 2010-03-09
the indicator applet is yet another solution desperately looking for a problem to solve .

---

### Post by 23meg on 2010-03-09
> **ronacc said:**
> the indicator applet is yet another solution desperately looking for a problem to solve .

Quite the contrary; it's based on a very clear problem definition:

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation)

[http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray)

---

### Post by ronacc on 2010-03-09
> **23meg said:**
> Quite the contrary; it's based on a very clear problem definition:

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation)

[http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray)

yes , those individual icons are too useful , lets replace them with one cryptic one that pops up a menu full of irrelevant entries so that they have to search for the one they want . I assume you mean that problem .

---

### Post by 23meg on 2010-03-09
> **ronacc said:**
> yes , those individual icons are too useful , lets replace them with one cryptic one that pops up a menu full of irrelevant entries so that they have to search for the one they want . I assume you mean that problem .

No, I didn't mean that sarcastic, non-factual problem definition you just made up; I meant a series of real, concretely defined problems that you can read about in the links I provided. You may disagree with specifics of the implementation, but "solution looking for a problem" is simply, factually wrong, and it's rather annoying how that's being thrown around randomly without substantiation these days (quite like "bloated").

---

### Post by ronacc on 2010-03-09
I plead guilty to sarcasm . I tend to use it do describe things of which I disapprove . Beauty is in the eyes of the beholder and I find the indicator applet to be as ugly as sin both in concept and execution . *** disclaimer *** this is one mans opinion .

---

### Post by rajeev1204 on 2010-03-09
Nice off topic discussion.

---

### Post by Keyper7 on 2010-03-09
> **ronacc said:**
> I plead guilty to sarcasm . I tend to use it do describe things of which I disapprove . Beauty is in the eyes of the beholder and I find the indicator applet to be as ugly as sin both in concept and execution . *** disclaimer *** this is one mans opinion .

Sarcasm is cute but usually works better accompanying arguments instead of replacing them.

---

### Post by ronacc on 2010-03-09
> **Keyper7 said:**
> Sarcasm is cute but usually works better accompanying arguments instead of replacing them.

read this thread and you will find many arguments against the indicator applet , I did not see the need to reiterate them. On the subject of the OP the indicator applet takes a very useful and much used icon and buries that function (volume control)  inside of a dropdown menu containing ( for me personally )many totally irrelevant entries all of it hidden behind a cryptic envelope icon .

---

### Post by Mr. Picklesworth on 2010-03-09
Ronacc, I believe you mean the message indicator specifically as the point of your rant. The indicator applet is what currently draws a whole bunch of indicators on the panel, *including* indicator-messages.

---

### Post by 23meg on 2010-03-09
> **ronacc said:**
>  (volume control)  inside of a dropdown menu containing ( for me personally )many totally irrelevant entries all of it hidden behind a cryptic envelope icon .

You sound like you're either unsure as to what the indicator applet actually *is*, or currently have a badly broken one for some reason. Screenshots might help identify the issue, if any.

---

### Post by ronacc on 2010-03-09
> **23meg said:**
> You sound like you're either unsure as to what the indicator applet actually *is*, or currently have a badly broken one for some reason. Screenshots might help identify the issue, if any.

here is the screenshot , in the "add to pannel" menu it is labelded indicator applet, as you can see in the dropdown  irrelevant to me 1 chat brings up empathy , I don't use empathy .  2 mail , brings up evolution , I don't use evolution . 3 compose new message and contacts , I don,t use a PIM . 4 microblogging , I don't microblog (or any kind of blog). 5 the icon for volume control looks like a monitor not a speaker .

---

### Post by rajeev1204 on 2010-03-09
The indicator applet is utterly useless to me too.I dont use any of the applications inside it ,and as of now it just looks like a tray application where you can dock all these things.Well, i thought thats what shortcuts do too.Drag drop icon from menu

It has never indicated anything to me yet .

But yes, throw down a half baked implementation to users and then feel all overly sensitive about it isnt that smart either.
And why exactly does it look like an envelope ?? Wonderfully useful for new users.

Anyways, i hope the OP's question didnt get lost here.

---

### Post by Keyper7 on 2010-03-09
> **ronacc said:**
> read this thread and you will find many arguments against the indicator applet, I did not see the need to reiterate them.

Well, let's see. Concerning the indicator-applet, there are those those two complaints,

> **ronacc said:**
> I am constantly astounded at what some idiot thinks will be cute . I want my panel volume control back . I remove the indicator applet because it does nothing I want , I use my preffered chat program which is not empathy , I don't use evolution and I don't microblog .

> **dagrump said:**
> I feel as if I woke up to Steve "the mock-turtle necks" version of linux, you will take what we give & like it. I don't like the indicator applet, I used to remove it. Now if I remove I have no volume control.
This is becoming more effort to get things back to a usable state then it's worth. I'm worried WTH!! are they going to jack with next?

which seem to confuse the indicator-applet with indicator-messages. Then there is this,

> **rajeev1204 said:**
> I somehow want the update notifications somewhere instead of the update pop up window which is annoying.

which is a problem that was introduced *with* the indicator-applet but not *by* it. It is completely independent. And finally, we have

> **ronacc said:**
> the indicator applet is yet another solution desperately looking for a problem to solve .

> **ronacc said:**
> yes , those individual icons are too useful , lets replace them with one cryptic one that pops up a menu full of irrelevant entries so that they have to search for the one they want . I assume you mean that problem .

> **ronacc said:**
> I plead guilty to sarcasm . I tend to use it do describe things of which I disapprove . Beauty is in the eyes of the beholder and I find the indicator applet to be as ugly as sin both in concept and execution . *** disclaimer *** this is one mans opinion .

which are just random rants without any technical, factual or logical arguments behind them.

That's all I could find. No valid arguments whatsoever.

If I missed something, please quote it.

> **ronacc said:**
> On the subject of the OP the indicator applet takes a very useful and much used icon and buries that function (volume control)  inside of a dropdown menu containing ( for me personally )many totally irrelevant entries all of it hidden behind a cryptic envelope icon .

The dropdown menu of indicator-messages contains only entries concerning indicator-messages. The dropdown menu of indicator-sound contains only entries concerting indicator-sound. Both are directly accessible from the panel. The indicator-sound is as much as exposed as the old volume applet was. I'm not sure what you are talking about.

---

### Post by Keyper7 on 2010-03-09
> **ronacc said:**
> 5 the icon for volume control looks like a monitor not a speaker .

This is the icon for "no icon found". Seems like there's something missing in your icon theme.

---

### Post by rajeev1204 on 2010-03-09
Whats indicator sound ? I cant seem to find it in 'add to panel'.

I have a volume icon though in the indicator applet .
Hey i also see 'indicator applet session' now thats funny too.

Anyways keyper, ronacc has his opinion and he has expressed it .

He isnt under any obligation to elaborate more now is he. All he said to you was to read before posts about some of the indicator applet discussion.

Also ronacc , you seem to be missing an icon for volume.

---

### Post by Keyper7 on 2010-03-09
> **rajeev1204 said:**
> Whats indicator sound ? I cant seem to find it in 'add to panel'.

I have a volume icon though in the indicator applet .

The indicator-applet contains indicator-messages, indicator-sound and indicator-applications by default.

If you are not interested in the indicator-messages, uninstall the package indicator-messages.

---

### Post by tekstr1der on 2010-03-09
> **Keyper7 said:**
> ...The dropdown menu of indicator-messages contains only entries concerning indicator-messages. The dropdown menu of indicator-sound contains only entries concerting indicator-sound. Both are directly acessible from the panel. The indicator-sounds is as much as exposed as the old volume applet was. I'm not sure what you are talking about.

Is there any way to hide/disable indicator-messages while keeping indicator-sound and whatever the indicator is for power/battery state? As with others here, I previously removed the indicator applet as the indicator-messages component holds no useful value for me and I enjoy a clean panel interface without superfluous cruft.

---

### Post by Keyper7 on 2010-03-09
> **rajeev1204 said:**
> He isnt under any obligation to elaborate more now is he.

I never said he was.

> **rajeev1204 said:**
> All he said to you was to read before posts about some of the indicator applet discussion.

To be more accurate, he said that arguments could be found in those posts. That's not true.

> **tekstr1der said:**
> Is there any way to hide/disable indicator-messages while keeping indicator-sound and whatever the indicator is for power/battery state?

Uninstall the indicator-messages package.

---

### Post by 23meg on 2010-03-09
> **ronacc said:**
> here is the screenshot , in the "add to pannel" menu it is labelded indicator applet, as you can see in the dropdown  irrelevant to me 1 chat brings up empathy , I don't use empathy .  2 mail , brings up evolution , I don't use evolution . 3 compose new message and contacts , I don,t use a PIM . 4 microblogging , I don't microblog (or any kind of blog). 

Remove indicator-messages, then.

[QUOTE=ronacc]5 the icon for volume control looks like a monitor not a speaker .[/QUOTE]

That's a missing icon, an issue with your icon theme.

*(Edit: I was late to refresh the page; it seems Keyper7 clarified these before me.)*

---

### Post by tekstr1der on 2010-03-09
> **Keyper7 said:**
> Uninstall the indicator-messages package.

I did that. But this is a recommended package of both indicator-applet and ubuntu-desktop. More specifically, is there a way to hide/disable the indicator-messages envelop icon from being displayed in the panel whilst keeping other application indicators and not removing any distribution-recommended packages?

---

### Post by Keyper7 on 2010-03-09
> **tekstr1der said:**
> I did that. But this is a recommended package of both indicator-applet and ubuntu-desktop. More specifically, is there a way to hide/disable the indicator-messages envelop icon from being displayed in the panel whilst keeping other application indicators and not removing any distribution-recommended packages?

Edit: Picklesworth was more accurate than me, see below.

---

### Post by Mr. Picklesworth on 2010-03-09
> **tekstr1der said:**
> I did that. But this is a recommended package of both indicator-applet and ubuntu-desktop. More specifically, is there a way to hide/disable the indicator-messages envelop icon from being displayed in the panel whilst keeping other application indicators and not removing any distribution-recommended packages?

It's recommended, but it isn't a dependency; removing indicator-messages won't break ubuntu-desktop. (In fact, it takes nothing else with it).

---

### Post by sgosnell on 2010-03-09
OK, somebody help me out here.  I have the indicator-applet on the panel, but I don't see anything that remotely looks like a volume control, just Empathy, Pidgin, and Evolution.  How do I get a volume control in there?

---

### Post by Keyper7 on 2010-03-09
> **sgosnell said:**
> OK, somebody help me out here.  I have the indicator-applet on the panel, but I don't see anything that remotely looks like a volume control, just Empathy, Pidgin, and Evolution.  How do I get a volume control in there?

Whoops, sounds like a buggy install. Do you have the package indicator-sound?

---

### Post by BwackNinja on 2010-03-09
I can understand what they are saying about this being a *problem*, however, because I do not suffer from that problem that others do, the "too many icons in my systray all doing different things" problem. In fact, I believe that the problem isn't in the systray as a notification construct, but rather the abuse of it. I'd argue that most applications that have a notification icon really don't need it.

I have 3 icons in my systray and 2 of them are useless to me but I keep them anyway. I have nm-applet, which is useless to me because I'm using a wired connection. I have gnome-power-manager, which is useless to me because I'm on a desktop (always got power flowing, and if I don't, I think I'll know before it can tell me). And I have the volume control applet, which I never really click on - I just use it to always tell me what my volume is and I use buttons on my keyboard for actual volume control. I stopped using pidgin's status icon because all it told me that was useful was whether or not I had unread messages, which I replaced with a plugin that tells me in the taskbar.

Beyond this, however, I do agree with the inconsistancies being a problem for other people and using this as a nice, standardized, cross-desktop-environment implementation of notifications is nice and clean. Just not something that makes much of a positive difference in my life. Regardless of such benefits, however, it seems to just give applications something that they are even more able to abuse to provide functionality outside of their own windows. This, if it is more attractive than actually going to that window, means to me that there is a problem in window management or interface design somehow, not a problem in the notification area, the same thing that made the notification area attractive to use in the first place.

---

### Post by tekstr1der on 2010-03-09
> **Mr. Picklesworth said:**
> It's recommended, but it isn't a dependency; removing indicator-messages won't break ubuntu-desktop. (In fact, it takes nothing else with it).

I realize this. That's why I rephrased my question.

> **tekstr1der said:**
> More specifically, is there a way to hide/disable the indicator-messages envelop icon from being displayed in the panel whilst keeping other application indicators and not removing any distribution-recommended packages?

Thank you, though.

---

### Post by castrojo on 2010-03-09
> **BwackNinja said:**
> I have gnome-power-manager, which is useless to me because I'm on a desktop (always got power flowing, and if I don't, I think I'll know before it can tell me).

That's odd. I just did a Lucid install yesterday on my desktop and the battery icon wasn't there by default.

---

### Post by BwackNinja on 2010-03-09
I don't know why, but I have it. I've been due for a reinstall for a while, so I might do one later today if I don't have anything half-important to do.

EDIT: I've got it on "Always display an icon" rather than "Only display an icon when battery is present." I probably just wanted to be able to see the icon back when the icon was changed.

---

### Post by Sennaista on 2010-03-09
I think the problem is that you can't change the indicator-messages so that it points to your preferred applications. If I could replace Evolution with Thunderbird and Empathy with Pidgin then it would be a very useful thing to have. As it is now, I don't have any use for it.

---

### Post by 23meg on 2010-03-09
> **Sennaista said:**
> I think the problem is that you can't change the indicator-messages so that it points to your preferred applications. If I could replace Evolution with Thunderbird and Empathy with Pidgin then it would be a very useful thing to have. As it is now, I don't have any use for it.

It's a matter of indicator support being built into those applications (possibly with plugins), which is something anyone with the relevant knowledge (libappindicator makes that pretty simple) can do.

---

### Post by ybytyruzu on 2010-03-09
Hi there, the indicator-message work with Pidgin, but not with Thunderbird. Anyway, I removed it because I use Pidgin but with it original tray icon.

---

### Post by grandtoubab on 2010-03-09
I did it my way

Applications -> Sound and Videos -> sound control

right clic
-> add this to the board

---

### Post by bwallum on 2010-03-09
> **robertjm said:**
> used to be a thank you button, but i don't see it anymore so i'll just say, "thank you" to ybytyruzu for his last post. I was stuck on finding that too! :-)+1

---

### Post by theozzlives on 2010-03-09
Please people! I just wanted to know where the volume went. I don't use the indicator applet, and I have volume on my laptop so everything's cool.

---

### Post by ronacc on 2010-03-09
glad its cool with you , but you brought up a valid point that many others , myself included seem to take seriously .

---

### Post by colorprint on 2010-03-20
I have the same problem...
indicator-sound is installed, but there is no sound volume icon...

---

### Post by sdowney717 on 2010-03-20
In karmic I had a sound level adjuster.
In Lucid it is gone.
How can I get it back?

---

### Post by quebecsat on 2010-03-20
I also lost the volume control and the sound on my install. Everything was fine for about 1 or 2 hours after i finally fix the video problem on my machine and then i lost sound while listening at a playlist in rhytmbox.

I went to see what was wrong and the volume controls where not there anymore and i had no sound whatsoever.

I am now formating my PC to re install 9.10. 10.04 was a huge nightmare for me, i spent 16 hours tying to fix it without success. 

I won't upgrade back before at least one year, for sure.

---

### Post by 23meg on 2010-03-20
Install the indicator-sound package.

---

### Post by Doctor Mike on 2010-03-20
> **colorprint said:**
> I have the same problem...
indicator-sound is installed, but there is no sound volume icon...Had same problem
fixed by install, but you'all should be glad your upgrade from 9.10 to lucid didn't install a second grub like it did on my xp HDD (which was non-functional and could not be removed by grub remove iso utility or fixmbr windows rescue), but required me to use a backup image to restore windows + mbr (which I still need and want to have). Too bad nobody seems willing to respond to my post about it saying, 'yes, there should be a confirmation dialog box concerning grub install with new installation or new distro update'. Sorry off topic [http://ubuntuforums.org/showthread.php?t=1434189](http://ubuntuforums.org/showthread.php?t=1434189), but it's a good thing I'm a paranoid windows user or would not have been able to fix easily.

---

### Post by 23meg on 2010-03-20
Threads merged.

---

### Post by sdowney717 on 2010-03-20
I went to synaptic and it said it was installed, so I marked it for upgrade, applied and still no appletty thing

I added the sound icon adjustment for sound preferences, but I miss the old one.

How is this solved on the thread title?
What is the solution?

Also, I dont have a sound control even available under the menu.
But I have one I placed on the menu bar.
Ok, I added gnome-volume-control under the sound and video menu.
so something is there now that was not there before?

---

### Post by Mr. Picklesworth on 2010-03-20
Well, there's your problem: You don't have the indicator applet on your panel. Add the applet called "Indicator Applet" and it should all make sense.

---

### Post by Keyper7 on 2010-03-20
**And before you ask**: if you don't want the messaging menu, uninstall the indicator-messages package.

---

### Post by sdowney717 on 2010-03-20
Ok, Thanks very much. It is now there.

Its 79 degrees in Newport News VA today!

---

### Post by Doctor Mike on 2010-03-20
> **sdowney717 said:**
> Ok, Thanks very much. It is now there.

Its 79 degrees in Newport News VA today!Will trade my 41 leamington, ontario canada, oops gone down to 37 kkndlfknfnnv.dnfvk

---

### Post by mpt on 2010-03-20
> **dagrump said:**
> I don't like the indicator applet, I used to remove it. Now if I remove I have no volume control.

“Doctor, it hurts when I do this.” ;)

> *This is becoming more effort to get things back to a usable state then it's worth. I'm worried WTH!! are they going to jack with next?*

What, specifically, do you find not “usable” about the indicator applet?

---

### Post by lifestream on 2010-03-20
> **ElSlunko said:**
> It's part of the indicator applet now.

O_o;;; Honestly...

So now we're forced to have that envelope there. These icons are all over the place... 

Indication applet -> About -> "An applet to hold all of the system indicators".
Um. Uuuummm.... isn't that what the Notification Area applet is for? O_o;;;;

---

### Post by Keyper7 on 2010-03-20
> **lifestream said:**
> So now we're forced to have that envelope there.

No. Uninstall indicator-messages and it's gone without removing the audio applet.

> **lifestream said:**
> Indication apple. About: "An applet to hold all of the system indicators".
Um. Uuuummm.... isn't that what the Notification Area applet is for? O_o;;;;

Yes. The Application Indicators are supposed to replace the notification area icons and what you see now is a transition phase, as documented for example [here](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators), [here](http://gould.cx/ted/blog/Having_a_tidy_systray), [here](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/) and [here](http://blog.jpetersen.org/2010/02/17/application-indicators/), besides the dozens of other forum threads where this has been discussed to death before. Please do proper research before trying to be snarky.

---

### Post by 23meg on 2010-03-20
One more thread merged. Please do a forum search before starting threads.

---

### Post by ElSlunko on 2010-03-20
I wonder if anyone has suggested having a preference menu where you can show/hide applets in the Indicator Applet instead of having to delete them.

---

### Post by lifestream on 2010-03-20
> **Keyper7 said:**
> No. Uninstall indicator-messages and it's gone without removing the audio applet.



Yes. The Application Indicators are supposed to replace the notification area icons and what you see now is a transition phase, as documented for example [here](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators), [here](http://gould.cx/ted/blog/Having_a_tidy_systray), [here](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/) and [here](http://blog.jpetersen.org/2010/02/17/application-indicators/), besides the dozens of other forum threads where this has been discussed to death before. Please do proper research before trying to be snarky.

I'm not trying to be snarky, I'm just honestly concerned.
Thanks for the links, I will see if they are appropriate (usually they are not when I search).


Unfortunately, I cannot uninstall the indicator-applet without uninstalling ubuntu-desktop itself, which as I'm sure you'll agree, I shouldn't do :P *GULP!*
Also, there is not a Volume applet on the list of available applets.

---

### Post by 23meg on 2010-03-20
> **lifestream said:**
> Unfortunately, I cannot uninstall the indicator-applet without uninstalling ubuntu-desktop itself, which as I'm sure you'll agree, I shouldn't do :P *GULP!*

Why exactly are you trying to uninstall indicator-applet? That's the package for the applet that hosts the messaging menu and other system and application indicators. If what you don't want is the messaging menu, remove indicator-messages, not indicator-applet.

> **lifestream said:**
> Also, there is not a Volume applet on the list of available applets.

If what you want is the old volume control (which is not an indicator, but runs in the notification area), run "gnome-volume control applet".

---

### Post by 23meg on 2010-03-20
> **ElSlunko said:**
> I wonder if anyone has suggested having a preference menu where you can show/hide applets in the Indicator Applet instead of having to delete them.

Yes, many people have, but I don't see what the benefit of that would be.

The specification recommends providing an option in applications that make use of indicators to toggle the indicator icons, so for application indicators, that should be the way to toggle them. And system indicators should only appear if they are relevant; there should be no sound / bluetooth indicator if you don't have sound / bluetooth hardware, no battery icon on a desktop computer, etc. That covers all bases, yet you can still remove indicators you absolutely don't want in any case in the future with a package manager.

---

### Post by lifestream on 2010-03-20
> **23meg said:**
> Why exactly are you trying to uninstall indicator-applet? 
> **Keyper7 said:**
> No. Uninstall indicator-messages and it's gone without removing the audio applet.
S/he advised me to.

>  If what you don't want is the messaging menu, remove indicator-messages, not indicator-applet.

Nah, I just hate the whole indicator-applet and what it entails ;p

> 
If what you want is the old volume control (which is not an indicator, but runs in the notification area), run "gnome-volume control applet".
Oh! That's really great, thanks. One more icon back in the notification bar *cheers* :D *puts it in Startup Applications*

[SIZE="1"]Now if I could get Transmission back to the old way... *googles googles*[/SIZE]

> **Keyper7 said:**
> The Application Indicators are supposed to replace the notification area icons and what you see now is a transition phase, as documented for example [here](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators), [here](http://gould.cx/ted/blog/Having_a_tidy_systray), [here](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/) and [here](http://blog.jpetersen.org/2010/02/17/application-indicators/), besides the dozens of other forum threads where this has been discussed to death before.

Okay, I read those links, and they didn't tell me much other than how the Indicator Applet is supposedly much better than Notification Area, and how they want to change all the programs that we have, and all the programs that may come to be, into this supposedly awesome new indicator applet. 

Even if I had had the time to google those things, they would not have helped me much.

Hopefully I can get Transmission back to the old notification area, but I think it's way too much trouble for each single Ubuntu user who hates the indicator applet to google and google and google until they finally understand how to get the icons back to the old notification area *takes big gulp of breath* Not everyone can dedicate their whole days to searching.

---

### Post by 23meg on 2010-03-20
[QUOTE=lifestream]S/he advised me to.[/QUOTE]

No, Keyper7 advised you to remove indicator-messages, not indicator-applet.

[QUOTE=lifestream]Even if I had had the time to google those things, they would not have helped me much.[/QUOTE]

I assume what Keyper7 meant was doing a forum search, not a Google search, since there are many threads on the exact same issue where you could have found answers. 

[QUOTE=lifestream]Hopefully I can get Transmission back to the old notification area, but I think it's way too much trouble for each single Ubuntu user who hates the indicator applet to google and google and google until they finally understand how to get the icons back to the old notification area *takes big gulp of breath* Not everyone can dedicate their whole days to searching.[/QUOTE]

Then perhaps we should work towards making the indicator applet work well so that as few Ubuntu users as possible will "hate" it. If you'd like to help with that, explaining the reasons why you "hate" it, and filing bug reports if necessary would be useful.

---

### Post by lifestream on 2010-03-20
> **23meg said:**
> No, Keyper7 advised you to remove indicator-messages, not indicator-applet.
Oooooh! My bad! See, I didn't even know there were two different indicator-thingies, so I read his "uninstall" advice as "uninstall the indicator completley". :-P !




> I assume what Keyper7 meant was doing a forum search, not a Google search, since there are many threads on the exact same issue where you could have found answers. 
Well that's even worse, the only decent searches I get are Google. Anything else -- forget it. >__<;;;  But I will try, but like I said, I woudln't even know how to phrase the search. It's very difficult when you don't know what things are called.


> Then perhaps we should work towards making the indicator applet work well so that as few Ubuntu users as possible will "hate" it. If you'd like to help with that, explaining the reasons why you "hate" it, and filing bug reports if necessary would be useful.
That sounds good. Are they really looking for feedback on this, though? I am active in Brainstorm, if that matters.

I don't think it's that the Indicator applet works "badly", I think it's just that they're taking something that already works, and making something that... they want to work, but are introducing waayyy too soon to be useful to the greater audience.
(I don't like to report bugs because by the time I get to them, 100 people have already reported it :P)

---

### Post by 23meg on 2010-03-21
> **lifestream said:**
> Oooooh! My bad! See, I didn't even know there were two different indicator-thingies, so I read his "uninstall" advice as "uninstall the indicator completley". :-P !

indicator-applet and indicator-applet-session are packages for the actual host applets. Think of indicator-sound, indicator-messages and indicator-application as components of the Indicator Applet, and indicator-me and indicator-session as components of Indicator Applet Session that you can pick and choose. 

> **lifestream]Well that's even worse, the only decent searches I get are Google. Anything else -- forget it. >__< said:**
> 

Try "Search this Forum" on the upper right in the future. "sound" and "applet" would probably have brought you to this thread (that I merged other threads into).

[QUOTE=lifestream]That sounds good. Are they really looking for feedback on this, though? I am active in Brainstorm, if that matters.

Of course; see mpt's post above.

[QUOTE=lifestream]I don't think it's that the Indicator applet works "badly", I think it's just that they're taking something that already works, and making something that... they want to work, but are introducing waayyy too soon to be useful to the greater audience.
[/QUOTE]

If you don't think it "works badly", why were you trying to remove it? 

There's no way to make free software useful to great audiences without *shipping it*. If there are any regressions in functionality compared to previous versions, make sure they're reported; that's the entire point of running Lucid. (go to [https://bugs.launchpad.net/ubuntu/+source/indicator-applet](https://bugs.launchpad.net/ubuntu/+source/indicator-applet) and [https://bugs.launchpad.net/ubuntu/+source/indicator-applet-session](https://bugs.launchpad.net/ubuntu/+source/indicator-applet-session), and type some keywords into the search boxes if you suspect they've already been reported).

---

### Post by lifestream on 2010-03-21
> **23meg said:**
> indicator-applet and indicator-applet-session are packages for the actual host applets. Think of indicator-sound, indicator-messages and indicator-application as components of the Indicator Applet, and indicator-me and indicator-session as components of Indicator Applet Session that you can pick and choose. 
Oooooh (Man, I feel dumb, but now I get it. I would never think each program would have to have ANOTHER program to tell it how to behave in a notification area).



> 
Try "Search this Forum" on the upper right in the future. "sound" and "applet" would probably have brought you to this thread (that I merged other threads into).

You're right, it did bring me to the right places. I've been using google to search a lot, and it wasn't helping me. 


> If you don't think it "works badly", why were you trying to remove it? 
Just because it doesn't work how I would like it, doesn't mean that others won't, I guess, or the devs woudln't have created it :p You guys in this thread seem to be OK with it.

I use the notification area a lot. For example, I'll move my mouse cursor to Transmission, and it would give me my download/seed rates. I would also click it when I needed to see the Transmission window.

Now, however, I can't work that way anymore. When I need to know if I'm downloading/seeding, I HAVE TO click the Transmission icon, I can't just glance. So, I click the Transmission icon, then have to click "Show Transmission". Then I have to click the icon again, then "show transmission" again, and finally it appears... on my Docky or my panel... *minimized*, so... ofcourse, then I have to go to the Docky or the panel, to raise the window. THEN finally, I can see if I'm downloading/seeding and then I can see by how much. *phew!*

I absolutely don't want it like that. No. Way. I'm switching to Deluge, because that BitTorrent client still uses the traditional Notification Area.

I tried to* sudo apt-get remove indicator-transmission*, but it doesn't exist apparently. Since you guys said there's a indicator applet for each program, like indicator-sound and indicator-messages, I thought I could do that to transmission too *blush*

> There's no way to make free software useful to great audiences without *shipping it*. If there are any regressions in functionality compared to previous versions, make sure they're reported; that's the entire point of running Lucid. (go to [https://bugs.launchpad.net/ubuntu/+source/indicator-applet](https://bugs.launchpad.net/ubuntu/+source/indicator-applet) and [https://bugs.launchpad.net/ubuntu/+source/indicator-applet-session](https://bugs.launchpad.net/ubuntu/+source/indicator-applet-session), and type some keywords into the search boxes if you suspect they've already been reported).

How am I supposed to know this is a bug though? I thought that's how they *wanted* it to be! Just because I have a problem with it, doesn't mean they should change it for me, when others like it.

---

### Post by 23meg on 2010-03-21
> **lifestream said:**
> Oooooh (Man, I feel dumb, but now I get it. I would never think each program would have to have ANOTHER program to tell it how to behave in a notification area).

Applications decide *themselves* what to do in the application indicators area, preferably in accordance to [a set of guidelines]("https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines").

> **lifestream said:**
> I use the notification area a lot. For example, I'll move my mouse cursor to Transmission, and it would give me my download/seed rates. I would also click it when I needed to see the Transmission window.

Now, however, I can't work that way anymore. When I need to know if I'm downloading/seeding, I HAVE TO click the Transmission icon, I can't just glance. So, I click the Transmission icon, then have to click "Show Transmission". Then I have to click the icon again, then "show transmission" again, and finally it appears... on my Docky or my panel... *minimized*, so... ofcourse, then I have to go to the Docky or the panel, to raise the window. THEN finally, I can see if I'm downloading/seeding and then I can see by how much. *phew!*

[Bug #527458]("https://bugs.edge.launchpad.net/indicator-application/+bug/527458") might be of interest to you.

[QUOTE=lifestream]I absolutely don't want it like that. No. Way. I'm switching to Deluge, because that BitTorrent client still uses the traditional Notification Area.

I tried to* sudo apt-get remove indicator-transmission*, but it doesn't exist apparently. Since you guys said there's a indicator applet for each program, like indicator-sound and indicator-messages, I thought I could do that to transmission too *blush*[/QUOTE]

I didn't say that there's an indicator applet *package* for each program, though. [You can enable or disable the indicator menu of each application in their own settings]("https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines#How%20should%20people%20hide%20the%20menu?"), and if you want to remove the whole application indicator area, you'd remove the indicator-application package.

[QUOTE=lifestream]How am I supposed to know this is a bug though? I thought that's how they *wanted* it to be! Just because I have a problem with it, doesn't mean they should change it for me, when others like it.[/QUOTE]

You can check whether a particular behavior is intended or not by looking it up in the specifications (for the [messaging menu]("https://wiki.ubuntu.com/MessagingMenu"), and [application indicators]("https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators")). If you have problems filing bug reports, or have other questions, feel free to ask for assistance here.

---

### Post by Chrigi on 2010-03-22
Wah, thank's a lot :D I was really missing the volume applet and the battery applet was going crazy without the indicator applet.

But it's really, really ugly that the indicator applet has these wide spaces between the incons and you can't shift them together. Or is there a way?

And why is the brightness and network applet not part of the indicator applet but the battery and volume is? Very strange grouping... I'd grouped the Netwpork, Battery, Brightness and Volume together and the notification and indicator (envelope) together.

---

### Post by jerrylamos on 2010-03-22
> **23meg said:**
> Why exactly are you trying to uninstall indicator-applet? That's the package for the applet that hosts the messaging menu and other system and application indicators. If what you don't want is the messaging menu, remove indicator-messages, not indicator-applet.



If what you want is the old volume control (which is not an indicator, but runs in the notification area), run "gnome-volume control applet".

I use volume control applet all the time.  When I removed the "envelope" which I have never ever used, or ever will, it removed the volume control applet as well.  Why on earth are these bundled?  How do I get the volume control applet back?  I tried "gnome-volume control applet" and got "command not found".

Appreciate any help how to get the volume contol by itself back.  

I also have the same problem with the "chat" applet. We've been using pc's since 1982 both professionally and privately and we have never used "chat" and never intend to.  The "chat" applet appears to be "bundled" with the account & the switch off applet.  Why are these bundled at all? 

Thanks, Jerry

---

### Post by jerrylamos on 2010-03-22
> **mpt said:**
> “Doctor, it hurts when I do this.” ;)



What, specifically, do you find not “usable” about the indicator applet?

What's not usable is if I remove the envelope applet it also removes the volume applet.  I never use the envelope applet.  I use the volume applet (if I could get it back, now I'm having to use alsamixer) all the time.

What's not expected when I remove the chat applet (haven't used chat since I've been on pc's since 1982) it also removed the switch off/reboot applet.  I can do the same function with Ctrl-Alt-Del.

So what's not usable about the applets is they are bundled together in combinations I don't use.

This forum is marked [SOLVED] but not for me.  I still don't have the volume applet.

Jerry

---

### Post by 23meg on 2010-03-22
> **Chrigi said:**
> Wah, thank's a lot :D I was really missing the volume applet and the battery applet was going crazy without the indicator applet.

But it's really, really ugly that the indicator applet has these wide spaces between the incons and you can't shift them together. Or is there a way?

There's probably a way to adjust the amount of padding (could be theme-dependent), but the equal spacing is intentional.

> **Chrigi said:**
> And why is the brightness and network applet not part of the indicator applet but the battery and volume is? Very strange grouping... I'd grouped the Netwpork, Battery, Brightness and Volume together and the notification and indicator (envelope) together.

Network Manager couldn't be ported because it uses some non-standard widgets. That's probably going to be dealt with during the next cycle. The brightness applet is an independent applet that doesn't use the notification area, and I'm not sure if it fits within the definition of "system indicators".

> **jerrylamos]What's not usable is if I remove the envelope applet it also removes the volume applet.[/QUOTE]

Those are not independent applets said:**
> How do I get the volume control applet back?  I tried "gnome-volume control applet" and got "command not found".

Remove the "indicator-messages" package, right click your panel, choose "Add to Panel", add "Indicator Applet" back to your panel. If you want the old applet, that's "gnome-volume-control-applet", with the dashes.

---

### Post by jerrylamos on 2010-03-22
> **23meg said:**
> Remove the "indicator-messages" package, right click your panel, choose "Add to Panel", add "Indicator Applet" back to your panel. If you want the old applet, that's "gnome-volume-control-applet", with the dashes.

Thanks.  I didn't find the words "gnome-volume-control-applet" but somehow I got the volume control back.

Thanks, Jerry

---

### Post by Chrigi on 2010-03-23
@23meg
Yes, It seems like the padding is theme dependent. Using the old Human Theme, the padding is huge and doesn't fit with the rest of the applets but with the new Themes (e.g. Radiance), the padding is normal.

What I also have my problems with, is that the Notification Area hos no visual indicator that it's there. You just have to somewhat aim to the side of the WiFi icon, to hit it.

Oh, and my Brightness applet has some serious problems. Whenever I reboot it compacts itself to a very small stripe of pixels.

---

### Post by fabioleitao on 2010-03-23
This makes no sense, and it will be marked as a paper cut as soon as 10.04 gets released. Why those not related applications (or indicators) got together anyway?

I also am missing the volume control (what ever applet or indicator that is) because I have also removed the envelop 

I can get the volume control there by running the $ gnome-volume-control-applet & but it wont stick

The next session its not there anymore, even if I try saving the running applications in the session.

---

### Post by ElSlunko on 2010-03-23
> **fabioleitao said:**
> This makes no sense, and it will be marked as a paper cut as soon as 10.04 gets released. Why those not related applications (or indicators) got together anyway?

I also am missing the volume control (what ever applet or indicator that is) because I have also removed the envelop 

I can get the volume control there by running the $ gnome-volume-control-applet & but it wont stick

The next session its not there anymore, even if I try saving the running applications in the session.


Try adding it to Startup Applications.

---

### Post by fabioleitao on 2010-03-23
> **ElSlunko said:**
> Try adding it to Startup Applications.

Manualy adding it worked, now its back to the way it was on 9.10.

Still do not understand the decision to joins those unrelated functions together... was it discussed earlier?

---

### Post by 23meg on 2010-03-23
> **fabioleitao said:**
> was it discussed earlier?

Yes, many times. The following may help you understand the rationale:

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation)
[http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray)
[http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/)

---

### Post by jerrylamos on 2010-03-23
> **23meg said:**
> Yes, many times. The following may help you understand the rationale:

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators#Issues%20with%20the%20current%20situation)
[http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray)
[http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/](http://www.jonobacon.org/2010/02/10/kde-application-indicators-in-gnome/)

Whatever the rationale was, any number of us are tripping over the "joining" of applets with unrelated function.  In my view, volume for You Tube, BBC, ... has nothing to do with mail (which I do on the internet anyway) and I never do chat as in never ever so what does that have to do with shutdown/reboot/... which I do frequently?

I've got "volume" back, thanks to the suggestions in the forum, but not the "shutdown, reboot, ..." which I can do by Ctrl-Alt-Del.

So for me [SOLVED] means I have a couple workarounds.

Jerry

---

### Post by Chrigi on 2010-03-29
Either all indicators should be offered as single applets as well or there should be a config option to choose which ones to group together.

I only need the WiFi, Volume, Brightness and battery but I can't have volume and battery without the envelope, the brightness applet disappears all the time, WiFi si bundled with the notification area and the indicator applet icons are padded waaay to much if used with a different theme (New Wave) so it's impossible to get a nice unified look with other applets.
I say: This is messed up!!
What I'd like to have: indicator applet with Volume, WiFi, Battery, Brightness / notification applet with envelope, chat

---

### Post by NCLI on 2010-03-29
> **Chrigi said:**
> Either all indicators should be offered as single applets as well or there should be a config option to choose which ones to group together.

I only need the WiFi, Volume, Brightness and battery but I can't have volume and battery without the envelope, the brightness applet disappears all the time, WiFi si bundled with the notification area and the indicator applet icons are padded waaay to much if used with a different theme (New Wave) so it's impossible to get a nice unified look with other applets.
I say: This is messed up!!
What I'd like to have: indicator applet with Volume, WiFi, Battery, Brightness / notification applet with envelope, chat

Join the Ayatana mailing-list and suggest it then, nothing will change by complaining here.

---

### Post by 23meg on 2010-03-29
> **jerrylamos said:**
> Whatever the rationale was, any number of us are tripping over the "joining" of applets with unrelated function.  In my view, volume for You Tube, BBC, ... has nothing to do with mail (which I do on the internet anyway) and I never do chat as in never ever so what does that have to do with shutdown/reboot/... which I do frequently?

In the old notification area, which applications have historically abused with arbitrary interfaces used for arbitrary purposes, completely unrelated functions were always side by side as well, and you've had no way of ordering them. With the indicator applet, system indicators and application indicators are separately grouped, and you can remove the ones you don't want.

> **jerrylamos said:**
> I've got "volume" back, thanks to the suggestions in the forum, but not the "shutdown, reboot, ..." which I can do by Ctrl-Alt-Del.

You probably removed Indicator Applet Session from your panel, and/or removed the indicator-session package.

---

### Post by 23meg on 2010-03-29
> **Chrigi said:**
> Either all indicators should be offered as single applets as well or there should be a config option to choose which ones to group together.

I only need the WiFi, Volume, Brightness and battery but I can't have volume and battery without the envelope, the brightness applet disappears all the time, WiFi si bundled with the notification area and the indicator applet icons are padded waaay to much if used with a different theme (New Wave) so it's impossible to get a nice unified look with other applets.
I say: This is messed up!!

The plan is to eventually replace the notification area with the indicator applet. The current situation is suboptimal in that you need to have both the indicator applet and the notification area in many cases,  but there's no way to fix it without shipping the indicator applet and encouraging upstreams to implement indicator support (preferably with patches!).

[QUOTE=Chrigi]What I'd like to have: indicator applet with Volume, WiFi, Battery, Brightness / notification applet with envelope, chat[/QUOTE]

May I ask *why*? 

There's currently no way to do this, since Network Manager doesn't yet have indicator support due to its non-standard interface, and "envelope" (the messaging menu) and "chat" (the Me menu) are strictly indicator components with no past notification area counterpart, but if I know what exactly you're trying to accomplish and why, I may be able to suggest a different solution.

---

### Post by swoll1980 on 2010-03-30
Deleted my volume control on accident, and there doesn't appear any replacement in the gnome applets list. Doesn't seem like it should be this complicating to replace a volume control. Any ideas? And yeah I misspelled panel, no fixing it now.

---

### Post by Omoronovo on 2010-03-30
This happens if you remove Sound Recorder - reinstall Sound recorder from Synaptic and it will return, or you can install any of the other volume control applets (alsa search in Synaptic) for replacement.

---

### Post by swoll1980 on 2010-03-30
ok thanks alot.

---

### Post by garolou on 2010-03-30
try this...
go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

and save, and check it

---

### Post by swoll1980 on 2010-03-30
> **garolou said:**
> try this...
go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

and save, and check it
That works. Thanks, but it's not the same one I had before. All I did was tried to move it. I didn't realize it was in the notification area. I right clicked it and accidentally hit something, don't know what, and now it's gone. It's a shame that this is like this. I can see alot of people loosing their controls.

---

### Post by Mr. Picklesworth on 2010-03-30
> **swoll1980 said:**
> That works. Thanks, but it's not the same one I had before. All I did was tried to move it. I didn't realize it was in the notification area. I right clicked it and accidentally hit something, don't know what, and now it's gone. It's a shame that this is like this. I can see alot of people loosing their controls.

Sounds to me you were a victim of this terrifying bug: [https://bugs.edge.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553]("https://bugs.edge.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553"). (Terrifying due to the report's complete lack of momentum).

The applet you removed is called Indicator Applet. Just add that in and you should get back your volume control as well as message indicator, bluetooth, battery, and indicators created by a few other apps. That applet is basically the successor to the notification area, which is what used to house the volume control ;)

When you go to the Add to Panel dialog you'll see three of them. The story here is that the applet can display items of specific types (one of the reasons why it is replacing the notification area!). The shutdown menu and the Me menu at the top right are both indicators, hosted inside Indicator Applet Session. (You probably still have that on your panel). Just plain "Indicator Applet" has everything else (that's what used to be there), and Indicator Applet Complete has all of them in one place, if you're so inclined.

---

### Post by swoll1980 on 2010-03-30
Thanks that was it. It's all back to normal again. How do I add my self as affected on the bug report with out re-reporting the whole thing?

---

### Post by Mr. Picklesworth on 2010-03-30
If you're signed in to Launchpad, just click on the text near the top that says "This bug affects 6 people" (or something like that), or click the edit button right beside it, and say it affects you. You can also subscribe to the bug report from that page, to get news on its status ;)

---

### Post by swoll1980 on 2010-03-30
> **Mr. Picklesworth said:**
> If you're signed in to Launchpad, just click on the text near the top that says "This bug affects 6 people" (or something like that), or click the edit button right beside it, and say it affects you. You can also subscribe to the bug report from that page, to get news on its status ;)

OK I marked my self as affected thanks for your help.

---

### Post by 23meg on 2010-03-30
Another volume control thread merged into this one.

---

### Post by dblade on 2010-04-08
> **garolou said:**
> try this...
go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

and save, and check it

Thanks for this.  As long as there's an option for 'everybody else', I've got no complaints :)

---

### Post by bgruber on 2010-04-10
> **23meg said:**
> With the indicator applet, system indicators and application indicators are separately grouped, and you can remove the ones you don't want.

Can you really remove the ones you don't want? Cause I can't figure out how, and all of the comments on here about how to remove the message indicator involve uninstalling it. What if your machine is used by multiple people and one person wants to use the message indicator and the other does not?

I have read the documents regarding the motiviations behind the indicator applet. I think I understand why they're doing it. Problem is, the applet doesn't actually seem to solve any of the problems it aims to, but it does introduce several new ones.

---

### Post by breadlord on 2010-04-26
Apologies if this seems off topic, but I might be looking in all the wrong places, and I can't find any usage documentation for the notifier applet.

I don't have a problem using the notifier applet, BUT it has an included icon set for amarok, which doesn't include the menu options for last.fm streams. These options are the main reason I have amarok in the system tray.

How do I blacklist individual icons so that the notifier won't take over amarok's system tray icon, but I don't have to uninstall the notifier?

---

