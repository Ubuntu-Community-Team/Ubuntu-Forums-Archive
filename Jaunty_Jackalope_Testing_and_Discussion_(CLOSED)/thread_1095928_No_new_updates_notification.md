---
title: "No new updates notification"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-14
I noticed on jaunty it never has an icon in system tray to notify about new updates.
I have to go to system->admin->update manager and it will show new updates. Even when update manager is open and shows new updates there is no icon in sys tray and does not list how many updates are available.

This should be brought back, so people know when they have new updates, and how many are available.
People not good with ubuntu will not know or be too lazy to go to system->admin->update manager

---

### Post by Stetzen on 2009-03-14
Yes, it looks like I'm observing this behaviour as well

---

### Post by lamborghiniwang on 2009-03-14
I can conform that too.

---

### Post by Kosimo on 2009-03-14
Did you create a new bug in launchpad?

---

### Post by Elfy on 2009-03-14
I think this is it

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/338501/](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/338501/)

also this [http://ubuntuforums.org/showthread.php?t=1089423](http://ubuntuforums.org/showthread.php?t=1089423)

Or this

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by gregwa on 2009-03-18
looks like this was resolved in this morning's updates...at least the icon showed up showing that "a package manager is working".

We'll see if it comes up later today.

---

### Post by pappfer on 2009-03-18
Same problem here and I'd like to add that after I go to update manager and install updates and then go back there after a restart, it offers many more updates again.
Why doesn't it install all the updates at the same time?

---

### Post by Bakon Jarser on 2009-03-18
> **pappfer said:**
> Same problem here and I'd like to add that after I go to update manager and install updates and then go back there after a restart, it offers many more updates again.
Why doesn't it install all the updates at the same time?

Could be that it is just displaying updates that it has already checked for automatically and when you restart it checks again.  When you first start update manager try hitting the 'check' button and see if it still does this.

---

### Post by andrewabc on 2009-03-18
> **pappfer said:**
> Same problem here and I'd like to add that after I go to update manager and install updates and then go back there after a restart, it offers many more updates again.
Why doesn't it install all the updates at the same time?

That is because of certain reasons.
Let's say you turn on computer and do work or whatever. It checks server and looks for updates. But you don't install them because you are just shutting down computer etc.
You turn on computer less than 24 hours later and it doesn't check for updates. You install available updates but do not check for new updates. Thus once you install updates, and check afterwards for new updates you may get some.

Anytime I plan on installing updates (for alphas) I check for updates before doing so because there may be more updates added since the last time the program checked for updates.

---

### Post by pappfer on 2009-03-18
I have to check updates everytime, because it does not pop up automatically.
So I always click on the check button but after a restart when I click on check button it brings up new updates again.

---

### Post by andrewabc on 2009-03-18
That is weird.

---

### Post by lalitgaur on 2009-03-18
I can confirm this too and has been going on for at least 10 days
Also the blue circle notification that shows restart required if a new kernel is updated doesn't appear too

---

### Post by Jay_Bee on 2009-03-18
**This is not a bug, this is by design.**
With the introduction of the new notification system Update manager was changed so it will pop up every 7(?) days if updates are available.
Restart icon in notification area was also removed and now you get a dialog after updates that require restarting are installed. 
For more details, check [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

---

### Post by allCuExpMa on 2009-03-27
Yeah i found that as well quite annoying, no notifier anymore, but at the other hand, it's a beta version, so it's suggested to run or look for updates daily anyway (or maybe more than ones a day)....
here is the solution, at least to get he "sys-tray" icon back
gconftool -s --type bool /apps/update-notifier/auto_launch false
and then kill and restart update-notifier and will get the icon for update-notifier back. (to check it straight away, run: sudo apt-get update)

T[m]

---

### Post by ktp on 2009-03-27
> **Jay_Bee said:**
> **This is not a bug, this is by design.**
With the introduction of the new notification system Update manager was changed so it will pop up every 7(?) days if updates are available.
Restart icon in notification area was also removed and now you get a dialog after updates that require restarting are installed. 
For more details, check [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

I just did update right now and I got both firefox needs to be restarted and system needs restart icons.  This whole thing needs to be looked at closely by UI team.  

On thing I hate is that notifications come up and go very fast.  I got two one for firefox restart and another for system restart, but there was no way I was going to be able to read both of them before they got closed.  Also they had text saying click here for more info, but notifications are not click-able.  

I know this is first stab at it and hope the UI time looks at it closely and most importantly take the our input into considerations.  Hack we are here using alpha/beta version so we can try to flush out these things before release.

---

### Post by DougieFresh4U on 2009-03-28
I am still not getting 'update'  icon. When 'system restart' is required, I get a messege box telling me of 'restart'.

---

### Post by olskar on 2009-03-28
> **DougieFresh4U said:**
> I am still not getting 'update'  icon. When 'system restart' is required, I get a messege box telling me of 'restart'.

You should not get them, as Jay_Bee says; it's by design. If you get them THAT is a bug

---

### Post by t.rei on 2009-04-02
> **allCuExpMa said:**
> 
here is the solution, at least to get he "sys-tray" icon back
gconftool -s --type bool /apps/update-notifier/auto_launch false
and then kill and restart update-notifier 

Confirmed to work like a charm, thanks.
For the lazy c/pers:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
killall update-notifier
update-notifier &
disown
sudo apt-get update
```Type those lines in that order into your terminal and you get the little icon back. 
Personally I liked the 'old' way of reminding me totally unobstrusively about restarting my computer soon alot better. This Dialog-Mania is getting a little "windows-vista'ish".

---

### Post by Polygon on 2009-04-02
they don't realize that this is annoying. Wait, actually they do, but for some reason, they decided to prematurely remove the update manager icon thingy and just have it pop up because the new way they were going to have updates present itself (using notify osd i'm guessing) is not ready yet.....

but will it BE ready? Hopefully they are not planning on shipping jaunty with this annoying behavior...its like using a mac...you are just doing your own thing then BAM update manager or whatever its called pops up and steals focus and just bothers you until it goes away.

and again, 7 days between update notifications is not right. It should be every day by default. Just like every other OS out there.

---

### Post by smbm on 2009-04-02
> **Polygon said:**
> update manager or whatever its called pops up and steals focus and just bothers you until it goes away.

I thought it popped up in the background? That is what the spec said it would do anyway.

---

### Post by Polygon on 2009-04-02
either way, its bad behavior. If it pops up underneath all of your windows, then it won't get noticed for a long time, even mark shuttleworth said that in one of the bug reports i think.

---

### Post by macroshaft on 2009-04-02
If it's not broken don't fix it! The way update manager works is one of the features I liked the most about Ubuntu. It should pop the icon up daily as needed and a restart icon that just sits there as a gentle reminded was also great. I don't want a windows-esque system that bullies me to reboot, or even worse reboots regardless of what you are doing!

I hope things are restored to work the way they used to, I don't care what's going on behind the scenes, just as long as it looks and acts the same.

---

### Post by Ramptu on 2009-04-02
I have to agree, I really liked the way the update notification icon worked before. I actually made a post (in the wrong forum) about how to get that back to functioning correctly because I thought I had messed something up when trying to get rid of the big black notification box. It was really annoying with pidgin msg's popping up everytime someone sent IM or logged on/off.

I hope they reconsider and put it back because after moving to Linux (which I love!) I have nothing. No Spybot, Spywareblaster, AVG, CCleaner, MRU Blaster to update and scan. I always got excited when that little update icon was beckoning me to click it. I felt empowered! I need something to do! ;)

---

### Post by kansasnoob on 2009-04-06
> **t.rei said:**
> Confirmed to work like a charm, thanks.
For the lazy c/pers:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
killall update-notifier
update-notifier &
disown
sudo apt-get update
```Type those lines in that order into your terminal and you get the little icon back. 
Personally I liked the 'old' way of reminding me totally unobstrusively about restarting my computer soon alot better. This Dialog-Mania is getting a little "windows-vista'ish".

I did this along with switching to The Stracciatella GNOME session:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

Which resulted in a much more pleasant experience for me, in large part because I am visually impaired!

I'm just very curious, before I'd recommend that procedure to others, how can that be reversed (in lazy c/pers speak) :p

---

### Post by esunday on 2009-04-06
I just noticed today that I haven't been getting update notices on my Jaunty beta setup, and I've been running it for more than 4 days I suppose.  I can force updates if I go to Update Manager, but I agree with the sentiment of several others here, one of the really nice features of Ubuntu is the way it takes care of the daily need for updates as they fly in ...

---

### Post by kansasnoob on 2009-04-06
Shameless bump!

As I said, before recommending what I've done I'd like to know how to reverse it if it doesn't please someone!

I mean the commands:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
killall update-notifier
update-notifier &
disown
sudo apt-get update
```

What commands would be necessary to revert?

I like the way mine is right now, but maybe not everyone will!

---

### Post by FuturePilot on 2009-04-06
> **kansasnoob said:**
> Shameless bump!

As I said, before recommending what I've done I'd like to know how to reverse it if it doesn't please someone!

I mean the commands:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
killall update-notifier
update-notifier &
disown
sudo apt-get update
```

What commands would be necessary to revert?

I like the way mine is right now, but maybe not everyone will!

Same exact process only
```
gconftool -s --type bool /apps/update-notifier/auto_launch **true**
```
true not false

---

### Post by kansasnoob on 2009-04-07
> **FuturePilot said:**
> Same exact process only
```
gconftool -s --type bool /apps/update-notifier/auto_launch **true**
```
true not false

Thanks. I wondered if it might be something that simple!

---

### Post by hufferd on 2009-04-07
> **Ramptu said:**
> I have to agree, I really liked the way the update notification icon worked before. I actually made a post (in the wrong forum) about how to get that back to functioning correctly because I thought I had messed something up when trying to get rid of the big black notification box. It was really annoying with pidgin msg's popping up everytime someone sent IM or logged on/off.

I agree I thought my install was botched or it was a bug till I saw this thread.... I like the way the notifications worked..... Why do they have to fix something that was not broken. ](*,)

Although I have to admit I kind of like that little black box with the pidgin notifications.  But I still want the update try icon too..  I saw a fix here I think I will use that in the mean time

---

### Post by hufferd on 2009-04-07
> **t.rei said:**
> Confirmed to work like a charm, thanks.
For the lazy c/pers:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
killall update-notifier
update-notifier &
disown
sudo apt-get update
```Type those lines in that order into your terminal and you get the little icon back. 
Personally I liked the 'old' way of reminding me totally unobstrusively about restarting my computer soon alot better. This Dialog-Mania is getting a little "windows-vista'ish".

Is this a permanent fix ? Another words will it keep coming back then when there are updates?

---

### Post by FuturePilot on 2009-04-07
> **hufferd said:**
> Is this a permanent fix ? Another words will it keep coming back then when there are updates?

yes

---

### Post by mamamia88 on 2009-04-07
thanks so much for the fix.   does the circle still come up when it has to restart?

---

### Post by FuturePilot on 2009-04-07
> **mamamia88 said:**
> thanks so much for the fix.   does the circle still come up when it has to restart?

Yep, that shows up for me when it needs a reboot.

---

### Post by george1984 on 2009-04-08
Thanks for the fix. Worked for me also.

---

### Post by hufferd on 2009-04-08
Thank you for the fix i did this on my machine and seems to work fine

---

### Post by jerrylamos on 2009-04-08
No notification of updates?

That's a Good Thing! for me.

After jaunty beta, updates screwed up two of my systems.  Nautilus died altogether on one (yes there's a launchpad bug) and Firefox fonts are screwed up on the other,

Wipe out install altogether, "fresh install" as of 20090403 much better on both.

My bet, updates screwed up both systems.  Beware.

Jerry

---

### Post by Lunx on 2009-04-08
> **macroshaft said:**
>  I don't want a windows-esque system that bullies me to reboot, or even worse reboots regardless of what you are doing!

100%  in support of that comment. The main reason I switched to Linux was exactly because of Windows thinking it could do what it wanted , when it wanted, and it not giving a toss about what I, the user wanted!. The final straw was an unexpected restart that saw me lose about an hour's worth of work on an essay for Uni. After it restarted I was greeted with a message saying updates had taken place which required a restart. If Canonical and the Ubuntu devs go down this route, then why did I bother making the change?

Put the icon back on my panel as a reminder updates are available and let *me* decide what I do with them, and when I do it.

Edit: Yes, I know at least with 'buntu I won't lose my work like I did in Windows :)

---

### Post by macvr on 2009-04-08
oh dont get me started on this crazy "NEW FEATURE"

the devs feel that not using the notification icon is a good thing but ***_the new feature uses the desktop as the notification area for updates!_***

how can using a larger area be less obstructive than a small icon!

bug regarding this :[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945?comments=all]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945?comments=all")
[COLOR="DarkRed"]devs explanations for changes>[/COLOR]
[COLOR="DarkRed"]1: icon is not easily distinguishable!!![/COLOR] >>> [COLOR="RoyalBlue"] just make an icon that is easy to identify![/COLOR]
[COLOR="DarkRed"]2: people find it difficult to remember the icons[/COLOR] >>> [COLOR="RoyalBlue"]they think people are so stupid that they cant remember 2 icons for update/restart![/COLOR]

why i find it difficult with this "new feature"> today i had a reminder that i needed a restart> i choose restart later... now there is no notification to remind me that i havent restart after an essential update... ! _so i need to remember about the restart or be reminded again tomorrow at the same time when i'll be working again that a restart is required!!!_
*at which time i'd probably choose to restart later! again*... so its just a vicious cycle when the restart is going to remind me again at the same time!

now jaunty is in beta so all crashes are acceptable...
but when it is distributed as a completed OS... how is this cycle of "non-obstructive" reminder helping? what if not doing the restart crashes my work system... and all my work is lost? is this an acceptable feature?
[I]
_if the restart is no so essential? why is the system even bothering to ask for a restart?_[/I]

worse is the devs think this is a lovely feature and that they wont fix this problem...! hope they dont revoke the gconf option too...

---

### Post by Polygon on 2009-04-08
> **macroshaft said:**
> If it's not broken don't fix it! The way update manager works is one of the features I liked the most about Ubuntu. It should pop the icon up daily as needed and a restart icon that just sits there as a gentle reminded was also great. I don't want a windows-esque system that bullies me to reboot, or even worse reboots regardless of what you are doing!

I hope things are restored to work the way they used to, I don't care what's going on behind the scenes, just as long as it looks and acts the same.

it does not reboot without your permission.....it now nags you even less then before, it just asks you if you want to restart, if you say no, then the thing dissapears and you don't see it again.

---

### Post by FuturePilot on 2009-04-08
> **Polygon said:**
> it does not reboot without your permission.....it now nags you even less then before, it just asks you if you want to restart, if you say no, then the thing dissapears and you don't see it again.

That doesn't make sense though. They claim that the new way is better for security. But say there was some kernel security updates that you installed and you need a reboot. But you don't want to do it right now so you say No when it asks. But then you're never notified again. And then you forget, and then the security updates never get applied because you forgot to reboot. Doesn't sound too good for security to me.

With the icon in the notification area it's a constant reminder that you need to reboot.

---

### Post by macvr on 2009-04-08
> **Polygon said:**
> it does not reboot without your permission.....it now nags you even less then before, it just asks you if you want to restart, if you say no, then the thing dissapears and you don't see it again.

whats the whole point of a restart required if its not needed and the notification disappears?

if the restart is going to remind u again at the same time the next day while u are working >u are going to click NO, so the next day and the next! until something crashes...

but if u have a notification icon reminder, u'll remember to restart at the end of the day, its as simple as that...

---

### Post by ktp on 2009-04-09
> **macvr said:**
> 
the devs feel that not using the notification icon is a good thing but ***_the new feature uses the desktop as the notification for updates!_***


I have to agree here...it seems like they, and I think they does not include most of the devs because I remember reading comments that even devs hate this, want to push this new notification system but at what cost.  I mean because of this new system, we could lose important updates, making it harder to manage windows, making it less productive, introducing regression by breaking update settings, and worst of all trying really hard to be Vista like with window popups.  

This is also not making the updates more noticeable or easy to install.  I think, and might be wrong, but this is making it harder since you have one chance to do it else you remember it and do it...until next time. 

Also, I would like to know how/what is saying the notification area is to busy and needs fixing by removing everything from there and replacing notification system with desktop popup windows.  I want more then one or two "exports" saying it because I never see more then one to three icons in my use, which I want there since almost every application that I use gives me an options to put it there or not.

Then again who am I to ask for such things.  I am just the user who should just use what is given.

---

### Post by ttk1opc on 2009-04-09
I thought it was just a bug, then I decided to google it and found this thread. I don't get it, what was wrong with the old? I liked it, I recognized the icon right away and sometimes click it like a kid on Christmas. I don't think the new system is that bad, other than it only popping up every 7 days, I used to tell people about how I get almost daily updates as a selling point, now it seems more like windows, with updates being treated less important.

---

### Post by Polygon on 2009-04-09
> **macvr said:**
> whats the whole point of a restart required if its not needed and the notification disappears?

if the restart is going to remind u again at the same time the next day while u are working >u are going to click NO, so the next day and the next! until something crashes...

but if u have a notification icon reminder, u'll remember to restart at the end of the day, its as simple as that...

i agree that we should have it the way it was in intrepid...but a restart is required because something (usually HAL, or the kernel) was updated and it can't update while those are being used, hence why you have to restart.

---

### Post by Incognito-Here on 2009-04-09
I agree. They definetely better to return old update system with daily updates and notification area icon, not this black unclickable ugly.

---

### Post by caryb on 2009-04-09
I just updated & rebooted and now is working:guitar:

Cary

BTW I'm talking about Kubuntu

---

### Post by amano on 2009-04-09
> **FuturePilot said:**
> That doesn't make sense though. They claim that the new way is better for security. But say there was some kernel security updates that you installed and you need a reboot. But you don't want to do it right now so you say No when it asks. But then you're never notified again. And then you forget, and then the security updates never get applied because you forgot to reboot. Doesn't sound too good for security to me.

With the icon in the notification area it's a constant reminder that you need to reboot.

I agree. There are some notifications that should be persistent within the indicator applet. The "Restart is required" should be one of them (of course until a restart is actually done). 

Would you mind filing a bug?

---

### Post by Polygon on 2009-04-09
i think the last one that i saw get submitted to launchpad got marked as 'invalid'...but feel free to try again. I'll add to it =)

---

### Post by FuturePilot on 2009-04-09
> **amano said:**
> I agree. There are some notifications that should be persistent within the indicator applet. The "Restart is required" should be one of them (of course until a restart is actually done). 

Would you mind filing a bug?

> **Polygon said:**
> i think the last one that i saw get submitted to launchpad got marked as 'invalid'...but feel free to try again. I'll add to it =)

I think it's really all part of this bug as there has been discussion about the reboot notification as well.
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945")

---

### Post by Vodkaneat on 2009-04-09
Yea I don't like it either, I believe it's part of the new Ubuntu design decisions, even Mr Shuttleworth has commented on the bud report stating: Confirmed &#8594; Won't Fix :(

---

### Post by rajeev1204 on 2009-04-09
hi

i posted this here as its not a technical post.
Why is it that for a community distro like ubuntu,user opinions are many a times ignored?

Mark shuttleworth - benevolent ubuntu dictator for life. :)



[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by riza hylviu on 2009-04-09
hi
hahahaaha
I switched from windows to ubuntu, and i love ubuntu ( windows survived just two months in dual boot), but running from a billionaire's arms to another ones arm....i am thinking to go debian..

---

### Post by perlluver on 2009-04-09
Meh, am I glad I use Slackware now.

---

### Post by saulgoode on 2009-04-09
> **rajeev1204 said:**
> Why is it that for a community distro like ubuntu,user opinions are many a times ignored?
Ubuntu is not a community distro.

---

### Post by Paqman on 2009-04-09
It's his job to make yes and no decisions about the distro. Given that there's a whole new notification framework being rolled out for Jaunty his decision isn't at all surprising.

---

### Post by Sealbhach on 2009-04-09
> **saulgoode said:**
> Ubuntu is not a community distro.
 
Correct. Mark has invested enough cash in Canonical to have the right to do whatever he likes with Ubuntu, imho.
 
 
.

---

### Post by swoll1980 on 2009-04-09
OMG He wants you to update Ubutu so you don't get pwned. Is it better than listening to a bunch of people wining about getting pwned?(because they didn't update) I would have to say yes... It's better.

---

### Post by balaknair on 2009-04-09
I have to agree that the update notification in Intrepid worked very well, and to me this seems like a step backward. You can still open pop-under window as they describe, just keep the notification applet intact. Or at least give an option for the notifications you want to see, perhaps when configuring System menu> Administration> Software Sources> Updates. There already is an option to 'Only notify about available updates', so why not add an option 'Open Update Manager Window'(as default behavior) and let people choose. 

Maybe someone can post a howto on getting the old notification settings back in Jaunty?
Especially the critical updates and restart required icons.

---

### Post by Mr. Picklesworth on 2009-04-09
I think Canonical needs to keep in mind that people who understood the notification area update notifications - and that includes countless non-technical users - actually liked them. Instead of reversing that for no apparent reason, they should find a way to teach it to every user. For example, using consistent icons between the notification and the update window and opening update-manager automatically /as well/. Killing off the "system needs restart" notification was particularly troublesome, for the same reason. What happens if a one-time user ran the update and didn't tell anyone?

They do the same every release with the shutdown / logout dialog, constantly unsatisfied with the "exit strategy." Last release they stuck with upstream's approach which *works for every other distro*, but they've reverted again to entirely annihilating that approach and having people use the user switcher applet for it instead (bringing us to countless regressions that can't possibly be fixed in time).

Canonical should adopt the following philosophy: Like valuable time, what works is sacred.

Having said that, I agree with Mark that [tidying is a decent idea]("https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/332945/comments/59"). I think we need a "hardware control area" for sound, networking, power and bluetooth stuff. (Could even be an upgrade for user interface, since then new devices and displays could appear there, too...)
With that out of the way, the notification area becomes less of a swamp and real notifications from applications can sit there happily.

---

### Post by Methuselah on 2009-04-09
Apparently the update manager pops under at most once a week not when updates are available.
It doesn't sound like a complete implementation and probably should have been held off until 9.10 and fully fleshed out.
Nonetheless, after making the big decision to go ahead with it for jaunty, I doubt they'd just arbitrarily reverse due to some pre-release complaints.

---

### Post by Yownanymous on 2009-04-09
Oh for God's sake... Getting rid of another useful feature... If they want people to stop using Ubuntu they're kind of going the right way...

---

### Post by FuturePilot on 2009-04-09
> **Mr. Picklesworth said:**
> I think Canonical needs to keep in mind that people who understood the notification area update notifications actually liked them. 

I agree. This new method is really targeted at a particular group of users. Probably people falling into the "average user" category who maybe don't update their systems that frequently or don't understand what the icon means in the notification area. For this particular group of users, this new method is probably a good idea and I can understand where they are trying to go with this (though I still don't completely agree with spamming the user with popup windows).

However, if you're a poweruser or advanced user and you know your way around Ubuntu, this probably sounds like the stupidest idea ever. Myself along with many other users were somewhat outraged to find our update notification icon gone. I have no problem with trying to clean up the notification area as it's badly abused by many applications, but they decided to start cleaning it up by removing the one application that has every right to stick an icon up there. The update and reboot notifications are probably two of the most important notifications and removing them I think is a mistake.

---

### Post by Methuselah on 2009-04-09
> 
I think Canonical needs to keep in mind that people who understood the notification area update notifications - and that includes countless non-technical users - actually liked them.


Precisely. Once you know what they mean, they are unobtrusive, reveal information at a glance, and provide an easy way to initiate the associated action.

I often comment that I feel calmer using Ubuntu than windows because on Ubuntu, dialogues do not arbitrarily open and demand my attention.
But, IIRC even Microsoft stopped opening update dialogues without warning.

When the dialogue pops under it does not immediately reveal anything if it is obscured by other windows and if I see a new window in my panel I'm going to be compelled to bring it forward to see what the fuss was about.
So it provides no immediate information and interrupts my work-flow whereas the lowly notification icon did the opposite of both.

It seems clear the Jaunty approach is half-baked.
They should have waited.

EDIT: Just to add that a lot of the work sounds exciting.
But this wasn't ready.

---

### Post by steeleyuk on 2009-04-09
One thing thats get to me with this idea about popping up the Window is this.

Its aimed at new and non-technical users. Fine. Why don't they enable security updates to download and install automatically and cut the middle step out. Thats effectively what users are going to do anyway. They'll see the apply button, type in their password and be done with it. I really can't see any new user trawling through a list of updates each time it pops up.

And I hate windows appearing automatically...

---

### Post by gn2 on 2009-04-09
> **Mr. Picklesworth said:**
> I think we need a "hardware control area" for sound, networking, power and bluetooth stuff.

Alt+F2 gnome-control-centre

---

### Post by swoll1980 on 2009-04-09
> **FuturePilot said:**
> 

However, if you're a poweruser or advanced user and you know your way around Ubuntu, 

Which is exactly why this shouldn't bother us. We will find away around this, and get things the way we want them. With all the other things we had to figure out, and work around to get things the way we wanted them, we're going to cry about this? Ubuntu is focused to be easy for new users, if catering to new users interferes with us, then it's our obligation to work around it, or move on.

---

### Post by balaknair on 2009-04-09
> **FuturePilot said:**
>  I have no problem with trying to clean up the notification area as it's badly abused by many applications, but they decided to start cleaning it up by removing the one application that has every right to stick an icon up there. The update and reboot notifications are probably two of the most important notifications and removing them I think is a mistake.

My sentiments exactly.

Why not give an option for the notifications you want to see, perhaps when configuring System menu> Administration> Software Sources> Updates. There already is an option to 'Only notify about available updates', so just add an option 'Open Update Manager Window'(as default behavior) and let people choose.

---

### Post by steeleyuk on 2009-04-09
If I remember correctly there is (or was) a way to turn it off in gconf-editor. Still, there's going to be a lot of threads about this asking how to turn it off.

---

### Post by Laibcoms on 2009-04-09
For sure it's here to stay.

Personally for me, I like the new one better, although it is a little bit too much currently but it's still new, just have to wait-and-see.

For the old one, there should be an option for those who prefers it.  The default will be the new notification since it's what and how they see Ubuntu down the road.

Choice, that's my take ^_^

---

### Post by 23meg on 2009-04-09
> **saulgoode said:**
> Ubuntu is not a community distro.

Could you elaborate?

---

### Post by balaknair on 2009-04-09
> **steeleyuk said:**
> If I remember correctly there is (or was) a way to turn it off in gconf-editor. Still, there's going to be a lot of threads about this asking how to turn it off.

Alt+F2--> gconf-editor--> apps> update-notifier--> Uncheck the option 'autolaunch'

This will get the old behavior back.

---

### Post by bapoumba on 2009-04-09
Threads merged.
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945/comments/59](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945/comments/59)

---

### Post by Dragonbite on 2009-04-09
> **rajeev1204 said:**
> hi

i posted this here as its not a technical post.
Why is it that for a community distro like ubuntu,user opinions are many a times ignored?

Mark shuttleworth - benevolent ubuntu dictator for life. :)



[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

Because Ubuntu is a company sponsored Linux distribution must like Red Hat and SUSE?! Fedora and openSUSE are "community" distributions but with heavy corporate influence and in part because the corporations provide the muscle of developer power behind it.

Or maybe Ubuntu is in the situation like Fedora/openSUSE?

---

### Post by ktp on 2009-04-09
> **Mr. Picklesworth said:**
> I think Canonical needs to keep in mind that people who understood the notification area update notifications - and that includes countless non-technical users - actually liked them. Instead of reversing that for no apparent reason, they should find a way to teach it to every user. 

Oh there is always a reason for a change.  And in this case, I could be wrong in my conclusion but based on all the comments and "reasons" given, it seems clear that they want to push the use of the new notification system and how can they say gnome you should adopt this system when the OS it self does not.  

I have no issues with pushing the use of the system but don't tell me this change is better for user experience when clearly it is not....hack it is less secure and instead of helping the user it makes it hard on him/her. Not to say because of this change, it is going to break every users automatically check for updates settings.

---

### Post by Ewingo401 on 2009-04-09
I just added an update manager launcher icon to my panel and open it up once a day.  It effectively recreates what the system was doing on its own before.  Yes the process is now manual as opposed to automatic, but after a couple days I hardly even notice, its just standard procedure to open the update manager after booting up now.

---

### Post by ktp on 2009-04-10
> **Ewingo401 said:**
> I just added an update manager launcher icon to my panel and open it up once a day.  It effectively recreates what the system was doing on its own before.  Yes the process is now manual as opposed to automatic, but after a couple days I hardly even notice, its just standard procedure to open the update manager after booting up now.

Might as well do this, unsupported but gives you the old behavior...icon as soon as updates available.  Need to restart after the change.

```
gconftool -s --type bool /apps/update-notifier/auto_launch false

```

---

