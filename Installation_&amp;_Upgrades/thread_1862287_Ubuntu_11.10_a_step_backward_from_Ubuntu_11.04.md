---
title: "Ubuntu 11.10 a step backward from Ubuntu 11.04"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by IntoFlow on 2011-10-16
After an upgrade from 11.04 to 11.10, I decided to just go ahead and do a clean install from a boot CD of 11.10.

My computer is pretty solid, 4GB ram 2ghz Sony Vaio.

11.10 is slower than 11.04. It shuts down like four times slower. 11.04 shut down in 8 seconds. Booting isn't anything impressive either.

And when it does boot, it takes a long time for the Applications to actually appear when I press the Super Key.

This wasn't the case in 11.04.

Also, copying large amounts of files from a HD to the PC locks up my computer. I've never had my Ubuntu freeze as much as it does with 11.10. Even typing in LibreOffice and doing other stuff in the background freezes things. And when it does freeze, I've got to force shut down from the power button.

What's up?

---

### Post by IntoFlow on 2011-10-16
As a sidenote, my 11.04 ran flawlessly. It NEVER crashed on me. It was solid as a rock. Everything that I wanted it to do, it did.

---

### Post by viperdvman on 2011-10-16
This is why I'm waiting until November to to install Oneric alongside Natty (my primary Ubuntu). If I remember right, Natty had plenty of problems after its release... and I installed my Natty toward the end of May and it's had no problems for me.

I would either just wait it out like I am, or if you already have 11.10 installed, update that little bugger every day.

Do remember that 11.04 ran Unity on top of GNOME 2.x using GTK+ 2 on a 2.6.38 kernel, while 11.10 is running Unity on top of GNOME 3.x using GTK+ 3 on a 3.0.x kernel... it's a much bigger change to Ubuntu's base than when 11.04 came out. So there are gonna be some teething issues.

I hope we can get it worked out. But for now, I'm waiting until early November when most of the biggest release bugs will be fixed.

*(note: I'm installing Oneric _alongside_ Natty because Oneric's gonna be a trial install. It's gonna be hard to pull me away from GNOME 2.x, but at least having Oneric installed alongside Natty in my 3rd OS partition will give me a space to try out both the more mature Unity and GNOME Shell GNOME Fallback in an Ubuntu environment, as they are the future of Ubuntu, and I doubt GNOME 2.x will still be available after Apr 2013 when Lucid's support ends)*

---

### Post by haqking on 2011-10-16
> **IntoFlow said:**
> As a sidenote, my 11.04 ran flawlessly. It NEVER crashed on me. It was solid as a rock. Everything that I wanted it to do, it did.

So it begs the question why upgrade then ?

Most people problems on here since 11.10 is the lack of trying it out before installing, or upgrading blindly.

You upgraded and have had problems, it happens.  Why did you choose to if it did everything you wanted and was solid and ran flawlessly ;-)

---

### Post by docbop on 2011-10-16
> **haqking said:**
> So it begs the question why upgrade then ?

Most people problems on here since 11.10 is the lack of trying it out before installing, or upgrading blindly.

You upgraded and have had problems, it happens.  Why did you choose to if it did everything you wanted and was solid and ran flawlessly ;-)


Dammit stop making sense.  ¯\(°_o)/¯

---

### Post by Slim Odds on 2011-10-16
> **haqking said:**
> So it begs the question why upgrade then ?

Most people problems on here since 11.10 is the lack of trying it out before installing, or upgrading blindly.

You upgraded and have had problems, it happens.  Why did you choose to if it did everything you wanted and was solid and ran flawlessly ;-)

Well said.... so many people just get "upgrade fever".

If you want solid, stick with an LTS release, and even then, install it after the release has been out a couple of months.

---

### Post by bailenforcer on 2011-10-16
I upgraded yesterday and it's a nightmare. I am running a quad core and it runs like a ancient 8088 now. The other post said 4 times slower, well I can say it takes between 20 to 30 seconds to open firefox now and it used to open in a second or two. The entire system lags horridly. Back to firefox the back button is useless as it saves nothing to go back to, even hovering over a link you can't tell if it's a link of just sentence. The entire computer runs so slow sometimes if I select something I can go get a cup of coffee come back and it still hasn't loaded. Is there any way to go back to the previous version? 11.1 has made the computer useless now. I want my 11.04 back!!

---

### Post by haqking on 2011-10-16
> **bailenforcer said:**
> I upgraded yesterday and it's a nightmare. I am running a quad core and it runs like a ancient 8088 now. The other post said 4 times slower, well I can say it takes between 20 to 30 seconds to open firefox now and it used to open in a second or two. The entire system lags horridly. Back to firefox the back button is useless as it saves nothing to go back to, even hovering over a link you can't tell if it's a link of just sentence. The entire computer runs so slow sometimes if I select something I can go get a cup of coffee come back and it still hasn't loaded. Is there any way to go back to the previous version? 11.1 has made the computer useless now. I want my 11.04 back!!

only with a reinstall.

next time dont blindly upgrade

---

### Post by IntoFlow on 2011-10-16
lol yeah, point taken. I'm sure issues will get resolved with time. =)

---

### Post by haqking on 2011-10-16
> **IntoFlow said:**
> lol yeah, point taken. I'm sure issues will get resolved with time. =)

indeed ;-)

fresh install and then play with 11.10 in a VM to get used to it, when you want to try it on real hardware then do a dual boot possibly or a Live CD/DVD etc before a full upgrade.

Peace

---

### Post by jimbo99 on 2011-10-16
There's something deep down wrong with 11.10.  I too did an upgrade.  I upgraded because I was constantly getting an upgrade prompt.  I'd clear it and get it again in a minute.  On multiple computers at that.

During the install I got the SAME type of messages I received from the last 3 upgrades and the same screw ups.  This I guess is making me a pro--not that I want to be one.  Really, it would behoove Canonical to stop right now and for the next few releases (yes I said few) that they get their acts together and resolve all these upgrade issues.  Leaving this up to the average person is going to do nothing but turn people away from Linux.  That's a guarantee.

On my system during the install I got some message about some library issue, and then I got the message that the upgrade had been aborted that that my system might be in an unusable state.  Right, seriously, Canonical is supposed to abort the update without giving me tools to resolve the issue, and then tell me that I may not be in a usable state?  That's bad, flat out.

Anyway, this sort of thing happened last upgrade.  This time around I issued the dpkg --configure -a and then restarted the upgrade before rebooting.  The second time around it appeared to complete the install.  When I rebooted though it was stuck and the logo screen and wouldn't progress.  I knew to switch to a terminal window and to reinstall the video drivers.  That got me to a desktop, but the performance was INSANELY SLOW.

After some investigation I found that Akonadi was loading a launcher in memory about 25 times and I was getting errors about neopunk (or whatever it is called).  So, I shut those off.  Performance improved but there's still this nagging lag.  This damn thing is so slow.  I also noticed the hard drive light was constantly on.  After making akonadi not load at start up the drive thrashing has ended, but I still have this slow down and lag.  Programs that would load in a blink of an eye are noticeably slower.  Even opening a new tab in Chrome is lagged out where you can observe the tab portion actually grow in size till it expands to it's designed full size.  I've removed Chromium browser and reinstalled it.  I removed samba and reinstalled it.  No luck.

After removing akonadi the thrashing is gone but the lag remains.  I also can't load kjots because it relies on that.  When I turned it on and looked to see if kjots notes were there they were missing.  I found the .book file but there's no way in kjots open the .book.

So, yeah, a big step backwards.  This time there's clear evidence that Canonical did not put the work in up front and have been relying on the users to fix their screw ups.  Unfortunate!

---

### Post by Gatemaze on 2011-10-16
I think all issues will be resolved in a couple of months or so. For the time being stick with 11.04 if it works flawlessly.

---

### Post by Wampyra on 2011-10-16
> **jimbo99 said:**
> Really, it would behoove Canonical to stop right now and for the next few releases (yes I said few) that they get their acts together and resolve all these upgrade issues.
Yea, but IntoFlow did a fresh install, so it's not an upgrade problem it's THE problem :p

> **jimbo99 said:**
> 
On my system during the install I got some message about some library issue, and then I got the message that the upgrade had been aborted that that my system might be in an unusable state.  Right, seriously, Canonical is supposed to abort the update without giving me tools to resolve the issue, and then tell me that I may not be in a usable state?  That's bad, flat out.
Same thing with me. +Flash dev package failed to install



I can't connect over pppoe anymore, even tho it worked perfectly first 2 days. It stopped by itself!

PLUS: How in the hell can you get the applications browser on the launcher? I hate typing the name when i know [where] in which category it should be [yup, i'm that lazy]

I think I'm gonna go back to Natty tomorrow and have good old problems with GPU drivers ;)

---

### Post by haqking on 2011-10-16
> **jimbo99 said:**
> There's something deep down wrong with 11.10.  I too did an upgrade.  I upgraded because I was constantly getting an upgrade prompt.  I'd clear it and get it again in a minute.  On multiple computers at that.

**During the install I got the SAME type of messages I received from the last 3 upgrades and the same screw ups.**  

So for the last 3 upgrades you had the same issues and yet you continue to do the same thing ?

If you always do what youve always done you will always get what you always got...as my grandad used to say.

Backup, try a live CD/DVD first to see if you like it.

Dual boot or VM to try it out.

Only install (usually best to do a fresh install instead of an upgrade) when you are ready.

In future turn off the the upgrade message, you dont have to upgrade or be reminded to.

---

### Post by Wampyra on 2011-10-16
> **haqking said:**
> In future turn off the the upgrade message, you dont have to upgrade or be reminded to.

How do u do that?
Thanks!

---

### Post by haqking on 2011-10-16
> **Wampyra said:**
> How do u do that?
Thanks!

update manager, settings and turn the release upgrade option to never.

depending on the version you currently have of course this may be in a slightly different place

---

### Post by Wampyra on 2011-10-16
> **haqking said:**
> update manager, settings and turn the release upgrade option to never.

I remember looking for it, but knowing me, I probably found about 1,000 other things there that i would never need. Thank you for a hint!

---

### Post by cacao on 2011-10-16
> **haqking said:**
> So it begs the question why upgrade then ?

Most people problems on here since 11.10 is the lack of trying it out before installing, or upgrading blindly.

You upgraded and have had problems, it happens.  Why did you choose to if it did everything you wanted and was solid and ran flawlessly ;-)

So true.. o _o

---

### Post by oldgeekster on 2011-10-16
> **haqking said:**
> So for the last 3 upgrades you had the same issues and yet you continue to do the same thing ?

If you always do what youve always done you will always get what you always got...as my grandad used to say.

Backup, try a live CD/DVD first to see if you like it.

Dual boot or VM to try it out.

Only install (usually best to do a fresh install instead of an upgrade) when you are ready.

In future turn off the the upgrade message, you dont have to upgrade or be reminded to.Bet your Grandpa was an Einstein fan too: >  *Insanity*: doing the same thing over and over again and expecting different results. --Albert EinsteinOver the years actually executing that simple word "backup" has become so easy, so inexpensive, it is simply ridiculous not to practice it these days. <mega sigh>

Then one thinks of how easy it is to simply download the iso of a new release, burn a CD and run it in Trial mode... Or how easy to install "BootIn" and do the same thing of a USB stick. (If your system doesn't have a CD - chances are almost 100% it has the bios support for booting off of a USB drive).

VirtualBox is a *very* useful program to learn/use.  (I like the Oracal VM VirtualBox with VBox Guest Extensions set up for every virtual machine). That is exactly how I tested the Ocelot 11.10 beta 2 until satisfied I wanted to give it a try... When April 2012 approaches, I will be doing the same for the next (LTS) release.

None of this does any good for those having problems now who FAILED to backup their systems prior to trying to live on the bleeding edge of Ubuntu - but it just might rub enough salt into the open wound that they will remember to do so next time.;)

---

### Post by richkraft on 2011-10-18
I think we all perform the upgrade assuming that some testing has been done prior to the release.  That assumption is obviously flawed.

---

### Post by emanuel.landeholm on 2011-10-22
I upgraded to 11.10. Huge mistake...

No more GNOME classic. GNOME 3 or unity, pick one.
Flash video runs for five seconds, stutters, stops, runs for five seconds...
Scrolling in Firefox is physically painful. It really hurts.
Cannot turn off GNOME 3 indicator app so no indicator in avant window manager.

Back to 11.04. :-)

---

### Post by Slim Odds on 2011-10-22
> **richkraft said:**
> I think we all perform the upgrade assuming that some testing has been done prior to the release.  That assumption is obviously flawed.

So, based on this comment, it seems that you assume that NO testing goes on? That's a flawed assumption.

The number of possible combinations of software, settings, configurations, etc. that the upgrade tool needs to deal with is near infinite. Maybe you can teach us all how we can test all of those to perfection.

---

### Post by cap10Ibraim on 2011-10-22
what's your pc specs ?

---

### Post by registerkar on 2011-10-22
I am a Linux Lover...& a strong believer in Linux...But yesss....Ubuntu 11.10 is indeed a step backward in time...

---

### Post by Slim Odds on 2011-10-22
> **registerkar said:**
> I am a Linux Lover...& a strong believer in Linux...But yesss....Ubuntu 11.10 is indeed a step backward in time...

I know that some people are having problems and get very defensive when I mention that I upgraded without issue, but:

1) You don't have to use Ubuntu if you don't want to (11.10 or any other)
2) You don't have to upgrade to each and every release
3) You don't have to upgrade immediately when a release comes out

New releases of ***ANY*** OS have inherent risk associated with them, especially from the perspective of **in-place upgrades**.

Everyone upgrading an OS should understand this.

But of course, they cannot blame themselves for a poor choice, so they have to rip the Ubuntu developers instead.

---

### Post by haqking on 2011-10-22
> **Slim Odds said:**
> I know that some people are having problems and get very defensive when I mention that I upgraded without issue, but:

1) You don't have to use Ubuntu if you don't want to (11.10 or any other)
2) You don't have to upgrade to each and every release
3) You don't have to upgrade immediately when a release comes out

New releases of ***ANY*** OS have inherent risk associated with them, especially from the perspective of **in-place upgrades**.

Everyone upgrading an OS should understand this.

But of course, they cannot blame themselves for a poor choice, so they have to rip the Ubuntu developers instead.


Big +100

---

### Post by emanuel.landeholm on 2011-11-12
> **cap10Ibraim said:**
> what's your pc specs ?

Well, quoting is an art form you have yet to master. ;-)

My specs are

Acer Aspire 5000 notebook computer running Ubuntu 11.04. Specs here: [http://elandeholm.blogspot.com/2011/01/ubuntu-on-acer-aspire-5000-okay-this-is.html](http://elandeholm.blogspot.com/2011/01/ubuntu-on-acer-aspire-5000-okay-this-is.html)

HP Compaq dc5750 desktop microtower computer running Ubuntu 11.04. Specs here: [http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=12454&prodSeriesId=3252512](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodTypeId=12454&prodSeriesId=3252512)

Computer at my office: a relatively recent HP desktop computer, specs to be posted later. :)

Dell dimension 5100: to be posted...

---

