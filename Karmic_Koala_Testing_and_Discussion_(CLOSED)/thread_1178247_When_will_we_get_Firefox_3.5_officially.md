---
title: "When will we get Firefox 3.5 officially?"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2009-06-04
I'm running the beta build at the moment (from PPA), but I'd like to know when it's going to be officially added to Karmic as the default browser?

The reason I'm wondering is that obviously the Ubuntu-firefox plugin doesn't work for the the PPA version and it's a pain not being able to open what you've downloaded.

---

### Post by super.rad on 2009-06-04
Firefox-3.5 is already in the repo's, guess it'll be made default soon (maybe for alpha 2)
> **Mazza558 said:**
> it's a pain not being able to open what you've downloaded.
what do you mean by that? I'm able to open things I've downloaded

---

### Post by Dougie187 on 2009-06-04
I as well am able to open what I have downloaded. But it won't "officially" be released until mozilla "officially" releases it. Right now there are betas all over the place that you can use though.

Also, from what I know the ubuntu-firefox plugin doesn't have anything to do with opening downloads. From what I understand it was just for little tweaks that "speed up" firefox.

---

### Post by castrojo on 2009-06-04
FYI

[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)

---

### Post by durand on 2009-06-04
> **Mazza558 said:**
> it's a pain not being able to open what you've downloaded.

I've also got this problem with opera but I'm not sure if it's related.

---

### Post by jmmL on 2009-06-04
> **durand said:**
> I've also got this problem with opera but I'm not sure if it's related.

Do people mean that they don't have read permission on downloaded items? I'm confused; I'm not seeing this at all.

---

### Post by durand on 2009-06-04
> **jmmL said:**
> Do people mean that they don't have read permission on downloaded items? I'm confused; I'm not seeing this at all.

Doesn't seem like it.

---

### Post by Starks on 2009-06-04
Example: You download a deb in Firefox 3.5 or 3.6 and when you double click it, gdebi won't pop up.

---

### Post by mc4100 on 2009-06-04
> **Starks said:**
> Example: You download a deb in Firefox 3.5 or 3.6 and when you double click it, gdebi won't pop up.

Clicking in nautilus or Firefox's download manager?

---

### Post by jmmL on 2009-06-04
> **mc4100 said:**
> Clicking in nautilus or Firefox's download manager?

Ahh, I've just tried it for myself. There's no option to "open" it from within firefox's download manager. I've never noticed this before because I mostly open stuff from my desktop.

Within firefox's download manager:
double clicking does nothing
the option to open is greyed out under the right-click menu

From nautilus:
everything works as expected; rwx permissions are as expected.

---

### Post by linux6994 on 2009-06-04
I you download the 3.5b4 you will get a firefox directory after extraction that can be placed anywhere. In that directory is the new version of firefox, running the firefox from there will bring it up.

---

### Post by psyke83 on 2009-06-04
> **linux6994 said:**
> I you download the 3.5b4 you will get a firefox directory after extraction that can be placed anywhere. In that directory is the new version of firefox, running the firefox from there will bring it up.

Yes, but why do you want to do that? We're supposed to be testing the official Ubuntu packages.

---

### Post by seeker5528 on 2009-06-04
> **Starks said:**
> Example: You download a deb in Firefox 3.5 or 3.6 and when you double click it, gdebi won't pop up.

Works for me. I did have 3.0.10 running while I opened the beta to check it out, since I didn't remember seeing any behaviour like that, in previous runnings I have not seen any indication that either version of the browser behaves differently if the other version is already running.

Is the 'Open containing folder' option greyed out too?

The only things I see this for are things that have been moved or deleted.

EDIT: Closed 3.0.10 and tried again, still works for me. 3.5b4 from the repositories, not from a PPA.

Later, Seeker

---

### Post by Mazza558 on 2009-06-05
I just get a file association window with no applications to choose from and a "browse" button when I try to open anything from the downloads manager.

---

### Post by skfd on 2009-06-05
Sorry for interruption, but how can I *upgrade* Firefox 3.0 to 3.5? All I can do is to install fresh and empty instance of Firefox 3.5.

---

### Post by psyke83 on 2009-06-05
> **skfd said:**
> Sorry for interruption, but how can I *upgrade* Firefox 3.0 to 3.5? All I can do is to install fresh and empty instance of Firefox 3.5.

The packages are separate so that both versions can co-exist on a system. For this reason you can't "upgrade" version 3.0, only remove it.

---

### Post by skfd on 2009-06-05
I see. But the problem is -- I want to use 3.5 as *the only* Firefox (because of Weave). Isn't there really no way to upgrade? Maybe there is a launchpad PPA to use as a source for this?

---

### Post by philinux on 2009-06-05
I dont understand. When I tried 3.5 in Jaunty it copied my 3.0 profile to use as it's own, with bookmarks and addons, therefore both browsers exist separately. I could now just uninstall 3.0.

---

### Post by pferraro on 2009-06-05
> **philinux said:**
> I dont understand. When I tried 3.5 in Jaunty it copied my 3.0 profile to use as it's own, with bookmarks and addons, therefore both browsers exist separately. I could now just uninstall 3.0.

The point is, uninstalling firefox-3.0 also removes the firefox meta package.  The question being asked is: when will the firefox meta package be updated to depend on firefox-3.5 instead of firefox-3.0.

The anticipation of this upgrade should also interest users of the gnome-globalmenu as it causes firefox-3.5 to crash on startup if multiple xulrunner versions are installed.

---

### Post by super.rad on 2009-06-18
Anymore news on this? Surely it would be good to get 3.5 as the default as early as possible for testing/bug reporting

---

### Post by mdmadph on 2009-06-18
> **skfd said:**
> I see. But the problem is -- I want to use 3.5 as *the only* Firefox (because of Weave). Isn't there really no way to upgrade? Maybe there is a launchpad PPA to use as a source for this?

Hasn't Weave been dead for a long time now?

---

### Post by SKLP on 2009-06-18
A bit off-topic maybe, but shouldn't Ubuntu switch to something like Epiphany(webkit), since the mozilla guys does not seem to care at all about their linux users ([https://bugzilla.mozilla.org/show_bug.cgi?id=311340](https://bugzilla.mozilla.org/show_bug.cgi?id=311340), it NEVER gets fixed )

---

### Post by super.rad on 2009-06-18
God can you imagine the amount of complaints? Just switching from pidgin to empathy has made a 15 page thread of rants
But yeah I would love to see Epiphany Webkit as the default browser

---

### Post by Changturkey on 2009-06-18
Epiphany's nice, but it needs polish. I believe they are converting to the webkit backend for the 2.28 series..

---

### Post by super.rad on 2009-06-18
> **Changturkey said:**
> Epiphany's nice, but it needs polish. I believe they are converting to the webkit backend for the 2.28 series..
Yeah if your running karmic you can install the webkit development version, it's a lot faster than the gecko version

---

### Post by xebian on 2009-06-18
> **SKLP said:**
> A bit off-topic maybe, but shouldn't Ubuntu switch to something like Epiphany(webkit), since the mozilla guys does not seem to care at all about their linux users ([https://bugzilla.mozilla.org/show_bug.cgi?id=311340](https://bugzilla.mozilla.org/show_bug.cgi?id=311340), it NEVER gets fixed )

You can try Webkit now by using Arora, or not sure if Konqueror is now WebKit but isn't WebKit  based on KHTML which is Konqueror.  Anyway the new Konqueror is getting there.

---

### Post by xebian on 2009-06-18
I just read RC1 is out so it must be just around the corner.

---

### Post by super.rad on 2009-06-18
> **xebian said:**
> You can try Webkit now by using Arora, or not sure if Konqueror is now WebKit but isn't WebKit  based on KHTML which is Konqueror.  Anyway the new Konqueror is getting there.

why not just try epiphany-webkit or midori? Or even chrome/chromium

---

### Post by xebian on 2009-06-18
> **super.rad said:**
> why not just try epiphany-webkit or midori? Or even chrome/chromium

Because I use Kubuntu.

AFAIK chromium-browser is using GTK?

---

### Post by super.rad on 2009-06-18
> **xebian said:**
> Because I use Kubuntu.

AFAIK chromium-browser is using GTK?

Ah right, didn't realise. 
I've got both installed at the moment and Kubuntu is looking much better (as usual), really liking KDE 4.3

---

### Post by xebian on 2009-06-18
> **super.rad said:**
> Ah right, didn't realise. 
I've got both installed at the moment and Kubuntu is looking much better (as usual), really liking KDE 4.3

There is another WebKit based browser called rekonq.  It has the same base as Arora that's why they look almost the same.  There is a ppa build but could not find it ATM.

---

### Post by super.rad on 2009-06-18
I thought rekonq was a webkit version of konqueror?
It's in karmic repo's now
EDIT: Nope you're right it's the same base as Arora
> rekonq is a KDE browser based on Webkit. Its code is based on Nokia QtDemoBrowser, just like Arora.
Much prefer Arora over rekonq though

---

### Post by SKLP on 2009-06-18
> **Changturkey said:**
> Epiphany's nice, but it needs polish. I believe they are converting to the webkit backend for the 2.28 series..
Sure they need polish but so does Firefox, just look at the clipboard bug i posted. It's a terrible bug which havent been fixed for several years.

---

### Post by SKLP on 2009-06-18
> **xebian said:**
> You can try Webkit now by using Arora, or not sure if Konqueror is now WebKit but isn't WebKit  based on KHTML which is Konqueror.  Anyway the new Konqueror is getting there.The point is not to try webkit but to (put rather bluntly) get rid of firefox( In which such basic features as copy/paste are not even working correctly).
But I guess Firefox is good to have as default because of its famous brand and so on.
Would just be great if they could fix such a basic feature...

---

### Post by Foaming Draught on 2009-06-18
I see it as a good and safe feature that the clipboard is cleared, along with cookies and history, when Firefox is closed.  If I want to copy and paste, I know that I have to keep Firefox open.

And some of Firefox' add-ons are indispensable to me and not implemented in other browsers.  As for speed:  how does a second or fraction of a second impair real-world working when a faster browser (if there is one) doesn't have the features which I need?

---

### Post by Reiger on 2009-06-18
> **Foaming Draught said:**
> I see it as a good and safe feature that the clipboard is cleared, along with cookies and history, when Firefox is closed.  If I want to copy and paste, I know that I have to keep Firefox open.

That seems counter-intuitive to me. The clipboard is a shared system (well, X) resource and shoud be respected as such. If the user finds a particular piece of information so important as to copy it into a shared resource for the purpose of re-using it in other tools; by extension the original source should _not_ actively seek to destroy that information. The thing about clearing cookies and history looks like you have the `private browsing mode' turned on (all the time), because otherwise that's a pure shot-in-the-foot.

As for safety. Ehrm, what safety? If the user deposits resources in a shared resource then the user deems that information safe enough to be there. Otherwise he/she would take time to copy the information manually by re-typing it. If Firefox ever uses the clipboard to temporarily store pieces of information outside of the user's control, then that's an inherently insecure design: cleaning up the mess afterwards is not going to fix that.

> And some of Firefox' add-ons are indispensable to me and not implemented in other browsers.  As for speed:  how does a second or fraction of a second impair real-world working when a faster browser (if there is one) doesn't have the features which I need?

True but besides the point of deciding what to include as default, though. Add-ons are for people not satisfied with the default. And yes, seconds or a fraction of seconds do matter in how your perceive a browser. You are human with the remarkable sensitivity to notice intervals in the range of miliseconds (IIRC 22ms is about as fast as our brains react to touch; and at any rate you can see people blink if you watch them intently: something which takes an amount of time in the order of miliseconds). So you are definitely going to notice/feel how sluggish browser X is when you are used to browser Y which does page rendering about half a second faster in the general case.

---

### Post by Changturkey on 2009-06-18
> **SKLP said:**
> Sure they need polish but so does Firefox, just look at the clipboard bug i posted. It's a terrible bug which havent been fixed for several years.

Well I think if Epiphany had more users, or Webkit in general, then more bugs/features would be fixed/added.

---

### Post by meborc on 2009-06-19
> **Changturkey said:**
> Well I think if Epiphany had more users, or Webkit in general, then more bugs/features would be fixed/added.

no, if the bug is reported, bigger user base will not help in fixing it... only bigger developer community can do that :)

don't confuse users with developers

---

### Post by MacUntu on 2009-06-19
You know that (in most cases) developers are a subset of users? So increasing the number of users might (not necessarily) increase the number of developers. ;)

---

### Post by Changturkey on 2009-06-19
> **MacUntu said:**
> You know that (in most cases) developers are a subset of users? So increasing the number of users might (not necessarily) increase the number of developers. ;)

Exactly what I was gonna say/mean't. More interest created by more users = more potential developers = more momentum.

---

### Post by plun on 2009-06-20
On-Topic....):P


>   Engineering

Firefox 3.5/Gecko 1.9.1 Development Update

    * see yesterday's platform meeting notes as well 

**Firefox 3.5 RC**

    * QA and Firefox teams actively testing
    * released an update to our beta channel users bringing them to rc1build2
    * finishing rc2build2 now, will update beta channel again soon
    * **targeting release / post to website for download on Friday**
    * see the Mozilla Developer News blog for more details 


[https://wiki.mozilla.org/Firefox3.5/StatusMeetings/2009-06-17](https://wiki.mozilla.org/Firefox3.5/StatusMeetings/2009-06-17)

---

### Post by andrewabc on 2009-06-20
> **plun said:**
> On-Topic....):P





[https://wiki.mozilla.org/Firefox3.5/StatusMeetings/2009-06-17](https://wiki.mozilla.org/Firefox3.5/StatusMeetings/2009-06-17)

So that means possible final release Friday? Or another RC?

I presume ubuntu is waiting for 3.5 final before making it default (not 3.0.x) in development?

---

### Post by plun on 2009-06-21
> **andrewabc said:**
> So that means possible final release Friday? Or another RC?

I presume ubuntu is waiting for 3.5 final before making it default (not 3.0.x) in development?

Its another RC version and its also uploaded to Karmic.

[https://lists.ubuntu.com/archives/karmic-changes/2009-June/002959.html](https://lists.ubuntu.com/archives/karmic-changes/2009-June/002959.html)

Mozilla then uses a "its ready when its ready" approach... no exact times or timetables.

---

### Post by jppr on 2009-06-21
FF 3.5 is now rc2 and fast

---

### Post by plun on 2009-06-21
Yup....  Superman Firefox...:D


[http://en-us.www.mozilla.com/en-US/firefox/3.5/whatsnew/](http://en-us.www.mozilla.com/en-US/firefox/3.5/whatsnew/)


[[img]http://ubuntu-pics.de/thumb/16832/3_5rc1firstrun_robobg_NqRDCX.jpg[/img]](http://ubuntu-pics.de/bild/16832/3_5rc1firstrun_robobg_NqRDCX.jpg)


--

---

### Post by jppr on 2009-06-21
:)

---

### Post by ruik on 2009-06-21
> Watch a video in your browser without needing any plugins or external media players.

[http://tinyvid.tv](http://tinyvid.tv)

Cool. :)

---

### Post by Thirtysixway on 2009-06-23
> **Foaming Draught said:**
> I see it as a good and safe feature that the clipboard is cleared, along with cookies and history, when Firefox is closed.  If I want to copy and paste, I know that I have to keep Firefox open.

Doesn't this happen with any program on Ubuntu?  If I copy something from gedit and close gedit, it's no longer in the clipboard.  Or at least it used to...

---

### Post by amano on 2009-06-23
That's known. Firefox isn't a native GNOME program and the clipboard issue is a sign for that. Most people use hacks like Parcellite from the repos. They work around those programs...

---

### Post by Foaming Draught on 2009-06-24
I tried 3.5 from Karmic's repos a while ago, but it didn't support my add-ons then.  Now, all of my add-ons (Adblock Plus, Image Zoom, Colorfultabs and ForecastFox) work and I notice a definite speed lift compared to 3.0.11.

(And I installed Parcellite from the repos at someone's suggestion, the clipboard is now persistent after closing whichever program I've cut from.)

---

### Post by andrewabc on 2009-06-24
> **Foaming Draught said:**
> I tried 3.5 from Karmic's repos a while ago, but it didn't support my add-ons then.  Now, all of my add-ons (Adblock Plus, Image Zoom, Colorfultabs and ForecastFox) work and I notice a definite speed lift compared to 3.0.11.

(And I installed Parcellite from the repos at someone's suggestion, the clipboard is now persistent after closing whichever program I've cut from.)

Are you using your same bookmarks and awesomebar database?
That is one reason why a new firefox install seems fast, is because it doesn't have a 25mb database for websites you have visited. Once that gets filled up, you'll be back to slowness. :)

At least that is what I notice anytime I try typing something into awesomebar, it can take a while for something to show up while it searches.

---

### Post by snkiz on 2009-06-24
Most of my addons work under 3.5/6, although I did hack the install.rdf files. I miss ubufox (desktop integration not just gnome), it causes strange behavior in the betas. I wish they would put ubufox in the ppa with the firefox betas. It can't be that hard to keep compatible.

---

### Post by lovinglinux on 2009-06-24
Never mind. Wrong forum.

---

### Post by snkiz on 2009-06-24
use a ppa if you want 3.5, the package in the repos is out of date. It is only put in there because of customer demand. Ubuntu can't be constantly packaging and testing dev builds to put into their stable releases. Besides its not like Mozilla will just drop the old version as soon as the new one comes out.  The move from 2.x > 3.x saw I think 4 or 5 five security updates for 2.x after 3.x came out.

---

### Post by zekopeko on 2009-06-24
> **lovinglinux said:**
> It has been suggested ([source](http://ubuntuforums.org/showthread.php?t=1194961)) that 3.5 final won't be available on Jaunty. The version on the repositories is 3.5b4pre.

If that is true, I'm inclined to use Swiftfox. You can install Swiftfox from it's own [repository](http://getswiftfox.com/deb.htm). Swiftfox uses the most recent version of Firefox and it is installed side-by-side with it. Nevertheless, it uses the same profiles as Firefox.

personally i wouldn't use swiftfox. it doesn't provide source code so you can never be sure what's been done with it. not to mention that it's non free.

---

### Post by lovinglinux on 2009-06-24
> **zekopeko said:**
> personally i wouldn't use swiftfox. it doesn't provide source code so you can never be sure what's been done with it. not to mention that it's non free.

Thanks for the info. I will stay with Firefox then.

---

### Post by andrewabc on 2009-06-24
> **lovinglinux said:**
> It has been suggested ([source](http://ubuntuforums.org/showthread.php?t=1194961)) that 3.5 final won't be available on Jaunty. The version on the repositories is 3.5b4pre.


I would hope they would update the 3.5 in jaunty to final instead of beta. Then if users wanted it they could install it instead of using 3.0.x. Yes they will not be updating 3.0.x to 3.5. They rarely update any software after release.

As long as they update the current 3.5beta in jaunty repos to final version, then anyone on ubuntu can easily install newer version.

---

### Post by lovinglinux on 2009-06-24
> **andrewabc said:**
> I would hope they would update the 3.5 in jaunty to final instead of beta. Then if users wanted it they could install it instead of using 3.0.x. Yes they will not be updating 3.0.x to 3.5. They rarely update any software after release.

As long as they update the current 3.5beta in jaunty repos to final version, then anyone on ubuntu can easily install newer version.

That would be great. It would be enough for me until Karmic is out. Is there a way to know if this will happen?

EDIT: Sorry for my intrusion. I didn't noticed this was at Karmic Koala Testing and Discussion forum.

---

### Post by plun on 2009-06-30
Released.......;)

[http://www.mozilla.com/en-US/firefox/3.5/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5/releasenotes/)

Hopefully soon in Karmic and Jauntys repo.

---

### Post by psyke83 on 2009-06-30
> **plun said:**
> Released.......;)

[http://www.mozilla.com/en-US/firefox/3.5/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5/releasenotes/)

Hopefully soon in Karmic and Jauntys repo.

Good news. Honestly though, we should have been using the 3.5 betas and release candidates in Karmic as our primary browser to aid bug reporting.

---

### Post by jfanaian on 2009-06-30
> **psyke83 said:**
> Good news. Honestly though, we should have been using the 3.5 betas and release candidates in Karmic as our primary browser to aid bug reporting.

I was very confused when I installed karmic alpha 2 and found firefox 3.0 still on there. I'm surprised it wasn't updated. Let's hope they get on it now that there is an official release :).

---

### Post by jaapz on 2009-06-30
I so hope they put it in the repos as fast as possible :P And with that i mean NOW xD

---

### Post by High Roller on 2009-06-30
Is there a Jaunty PPA with the stable release that will include security updates?  I've set my Update Manager to automatically download and install security updates.  My understanding is that PPAs don't differentiate between initial release and security updates and therefore a security update would require manual intervention.

I've seen a PPA that indicates it's updated daily.  Probably don't want that as it could potentially produce a broken update tomorrow.

---

### Post by psyke83 on 2009-06-30
> **High Roller said:**
> Is there a Jaunty PPA with the stable release that will include security updates?  I've set my Update Manager to automatically download and install security updates.  My understanding is that PPAs don't differentiate between initial release and security updates and therefore a security update would require manual intervention.

I've seen a PPA that indicates it's updated daily.  Probably don't want that as it could potentially produce a broken update tomorrow.

Firefox 3.5 is not a security release. Ubuntu's [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") policy does not allow major updates such as this, but you may see a backport released for Jaunty, if it is approved.

---

### Post by plun on 2009-06-30
> **psyke83 said:**
> Firefox 3.5 is not a security release. Ubuntu's [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") policy does not allow major updates such as this, but you may see a backport released for Jaunty, if it is approved.

I believe it will be upgraded also for Jaunty, an old beta version is used within Jauntys repo dated 20090330.

[http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)

---

### Post by psyke83 on 2009-06-30
> **plun said:**
> I believe it will be upgraded also for Jaunty, an old beta version is used within Jauntys repo dated 20090330.

[http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)

Yes, perhaps it'll show up in -proposed or -backports first, though. Either way, it's definitely not going to be assigned as the default browser in Jaunty.

---

### Post by tjeremiah on 2009-06-30
how do i remove shiretoko?

---

### Post by SergeantOreo on 2009-06-30
So.. in other words, are we going to have to download and install Firefox 3.5 manually?

**Edit:** Sorry, I just saw that this is in the Karmic sub-section; not for Jaunty discussion.

---

### Post by froggyswamp on 2009-06-30
Folks, I just built the final 3.5 release for x64 with optimization (-O2) and it's almost twice slower than x32, thus it's better for the x64 version of Karmic to stick the x32 bit version of Firefox.
btw same experience with mozilla's builds of x32/64.
Mozilla should pay more attention to x64, we don't live in 2003 any longer.

---

### Post by Teamgeist on 2009-06-30
Firefox 3.5 just hit the Karmic repos and will be updated in Jaunty.
To have FF 3.5 in Jaunty you'll have to install it via ```
sudo apt-get install firefox-3.5

``` It is a snapshot of one of the beta right now but will be updated in a couple of days.

Read here:
[http://www.asoftsite.org/s9y/](http://www.asoftsite.org/s9y/)

---

### Post by tim1 on 2009-06-30
> **Teamgeist said:**
> Firefox 3.5 just hit the Karmic repos and will be updated in Jaunty.
To have FF 3.5 in Jaunty you'll have to install it via ```
sudo apt-get install firefox-3.5

``` It is a snapshot of one of the beta right now but will be updated in a couple of days.


"Just hit"?

The firefox-3.5 package has even been in jaunty.

Personally, I'll wait until they update the firefox package, because the firefox-3.5 package will copy the Firefox profile and I'm not sure how they'll handle when 3.0 is replace in the repos.

---

### Post by jppr on 2009-06-30
[https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5+nobinonly-0ubuntu1)

---

### Post by Teamgeist on 2009-07-01
> **tim1 said:**
> "Just hit"?

The firefox-3.5 package has even been in jaunty.

Personally, I'll wait until they update the firefox package, because the firefox-3.5 package will copy the Firefox profile and I'm not sure how they'll handle when 3.0 is replace in the repos.

The final version just hit the Karmic repos.

As can be read in the link I provided the firefox 3.0 package in Jaunty will not be updated to 3.5.
The Firefox-3.5 package from the jaunty repos will be updated to the 3.5 final version soon.

---

### Post by ghindo on 2009-07-01
> **tjeremiah said:**
> how do i remove shiretoko?Shiretoko *is* Firefox 3.5, so you probably shouldn't remove it.  (Shiretoko is the codename for Fx 3.5.)  The Shiretoko package will (I think) be renamed simply "Firefox" once the final release hits the Ubuntu repos and is made the default browser.

Just be patient. ;)> **froggyswamp said:**
> Folks, I just built the final 3.5 release for x64 with optimization (-O2) and it's almost twice slower than x32, thus it's better for the x64 version of Karmic to stick the x32 bit version of Firefox.
btw same experience with mozilla's builds of x32/64.
Mozilla should pay more attention to x64, we don't live in 2003 any longer.[They're working on it.]("http://en.wikipedia.org/wiki/Firefox#64-bit_builds")  Firefox is a pretty big project with various other features and capabilities taking priority.  Again, just be patient and it will come ;)

---

### Post by alexcckll on 2009-07-01
Are Canonical going to release Firefox 3.5 for us basic 8.04 LTS users?

Or do I have to wait till next year to get an up-to-date Firefox?

Am running a Lenovo Thinkpad R61i with 8.04 preinstalled.

---

### Post by ghindo on 2009-07-01
> **alexcckll said:**
> Are Canonical going to release Firefox 3.5 for us basic 8.04 LTS users?No, Fx 3.5 won't be released for 8.04.x.  See:> **psyke83 said:**
> Firefox 3.5 is not a security release. Ubuntu's [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") policy does not allow major updates such as this

---

### Post by 23meg on 2009-07-01
> **alexcckll said:**
> Are Canonical going to release Firefox 3.5 for us basic 8.04 LTS users?

Or do I have to wait till next year to get an up-to-date Firefox?

Am running a Lenovo Thinkpad R61i with 8.04 preinstalled.

[http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html](http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html)

---

### Post by Merk42 on 2009-07-01
Am I the only one that thinks this should be stickied at the top?  Not like a topic sticky, but like the "Jaunty Jackalope has been released" sort of banner that appeared back in April.

---

### Post by plun on 2009-07-01
> **Merk42 said:**
> Am I the only one that thinks this should be stickied at the top?  Not like a topic sticky, but like the "Jaunty Jackalope has been released" sort of banner that appeared back in April.

Yup... info is a "disaster" and also to read the community cafe about it...):P 

I don't think so many read Planet Ubuntu...

---

### Post by ccw on 2009-07-01
Is the default useragent going to change?

karmic firefox-3.5 3.5+nobinonly-0ubuntu1 identifies itself as:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090701 Ubuntu/9.10 (karmic) Shiretoko/3.5

---

### Post by psyke83 on 2009-07-01
> **ccw said:**
> Is the default useragent going to change?

karmic firefox-3.5 3.5+nobinonly-0ubuntu1 identifies itself as:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090701 Ubuntu/9.10 (karmic) Shiretoko/3.5

Hopefully it will when the official branding is enabled (the browser name is set back to Firefox with the official artwork).

---

### Post by alexcckll on 2009-07-01
Umm - so let me get this straight... this isn't even showing up on your regular Jaunty user's Update Manager yet - but Release Management are still working on it?

Ah well - reckon I'll wait till next October...

---

### Post by mavar on 2009-07-02
> **ghindo said:**
> No, Fx 3.5 won't be released for 8.04.x.  See:

Some packages are considered exceptions in the SRU - [https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions](https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions).

Firefox is in the list of approved exceptions.

Hopefully, we would get an official release for 8.04

---

### Post by pjalegria on 2009-07-02
Im waiting to...:lolflag:

---

### Post by Merk42 on 2009-07-02
I've figured it out guys! Firefox 3.5 comes with a new logo, and we all know Canonical is against visual changes!

---

### Post by ubfu on 2009-07-02
> **ghindo said:**
> No, Fx 3.5 won't be released for 8.04.x.  See:

So it no hope to install on 8.04 ? :(
I heard it's faster than 3.0.

---

### Post by corinthoneto on 2009-07-02
this time Fedora team is ahead...Fedora 11 have firefox 3.5 officialy in your repositories... :(   Wake up Canonical!!! Please!

---

### Post by oldsoundguy on 2009-07-02
And for those that use versions where 3.5 will NOT show up in the repos, there is always Source Forge's Ubuntuzulla.  NOT THERE YET!!

It will do the work for you .. just install (when it gets there)!!

(3.5 works GREAT in Windows.  It SMOKES anything MS uses by a MILE in speed and ease and safety!!)(the new "plug in less" video is way too cool!!)

---

### Post by brm on 2009-07-02
> **corinthoneto said:**
> this time Fedora team is ahead...Fedora 11 have firefox 3.5 officialy in your repositories... :(   Wake up Canonical!!! Please!

It's been "officially" in my Karmic repositories for a day or two:

```
 apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5+nobinonly-0ubuntu1
  Candidate: 3.5+nobinonly-0ubuntu1
  Version table:
 *** 3.5+nobinonly-0ubuntu1 0
        800 http://ca.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status
bruce@Xenophon:~/Documents/computing$

```

Which of us is asleep? :-)

---

### Post by Merk42 on 2009-07-02
> **brm said:**
> It's been "officially" in my Karmic repositories for a day or two:

```
 apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.5+nobinonly-0ubuntu1
  Candidate: 3.5+nobinonly-0ubuntu1
  Version table:
 *** 3.5+nobinonly-0ubuntu1 0
        800 http://ca.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status
bruce@Xenophon:~/Documents/computing$

```

Which of us is asleep? :-)

Fedora 11 is the latest stable release.
So the Ubuntu equivalent would be 8.04 or 9.04

---

### Post by Reiger on 2009-07-02
> **brm said:**
> Which of us is asleep? :-)
Try the same for the package `firefox' (which is a meta package). That one still refers to 3.0.11. This means that the default Firefox (which is pulled in by abrowser or firefox) is still 3.0.11. ...

---

### Post by psyke83 on 2009-07-02
> **mavar said:**
> Some packages are considered exceptions in the SRU - [https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions](https://wiki.ubuntu.com/StableReleaseUpdates/MicroReleaseExceptions).

Firefox is in the list of approved exceptions.

Hopefully, we would get an official release for 8.04

Yes, but that exception may only apply to the new version of Firefox that was released in 2007 - see the date of ratification on the wiki page.

Look at the blog that 23meg linked to - it hasn't been decided where the update will appear for Hardy and Intrepid, so you're not guaranteed to get Firefox 3.5 as an official update in the repositories. However, I have no doubt that it will be available via other means (in a PPA, for example).

---

### Post by Slug71 on 2009-08-04
Firefox stable is now at 3.5.2. Still nothing for Karmic though :(

---

### Post by plun on 2009-08-04
> **Slug71 said:**
> Firefox stable is now at 3.5.2. Still nothing for Karmic though :(

No its seems to be giant trouble with this... "branding" maybe...:D


Some nice vulnerabilitys in both Firefox and Adobe Flash which is not fixed yet....:-\"

---

### Post by wayne_cat on 2009-08-04
> **plun said:**
> No its seems to be giant trouble with this... "branding" maybe...:D


Some nice vulnerabilitys in both Firefox and Adobe Flash which is not fixed yet....:-\"

No way ... they need more time to implement the new Ubuntu Multisearch spyware :twisted:

---

### Post by dentaku65 on 2009-08-04
> **wayne_cat said:**
> No way ... they need more time to implement the new Ubuntu Multisearch spyware :twisted:

rotfl :D

---

### Post by Kaisersoze on 2009-08-05
This is starting to become a joke.. Still no official firefox 3.5 on Jaunty? Come on? Do you expect to recruit new linux users flashing old software?

Using Jaunty and lovng it... but to be honest im disapointed with the lack of software update...

---

### Post by pjalegria on 2009-08-05
I have to agree with you, im disapointed with the lack of software update... :(

---

### Post by 23meg on 2009-08-05
> **Kaisersoze said:**
> This is starting to become a joke.. Still no official firefox 3.5 on Jaunty? Come on? Do you expect to recruit new linux users flashing old software?

Using Jaunty and lovng it... but to be honest im disapointed with the lack of software update...

This is the Karmic testing forum. Firefox 3.5 is available in Jaunty in Universe branded as Shiretoko. There won't be a branded Firefox 3.5 in Jaunty and this has been made clear multiple times.

---

### Post by cheesypoof on 2009-08-05
Will the firefox package point to 3.5 in karmic when it is finished? Apologies if this has already been stated.

---

### Post by wayne_cat on 2009-08-05
> **cheesypoof said:**
> Will the firefox package point to 3.5 in karmic when it is finished? Apologies if this has already been stated.

[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)

---

### Post by Slug71 on 2009-08-14
Loving 3.5.2! :) It seems snappy.

---

### Post by nanotube on 2009-08-14
> **EApubs said:**
> Actually you can install the latest,genuine firefox from a python script called ubuntuzilla

[http://www.earth-org.com/blogs/2009/08/install-genuine-firefox-3-5-latest-on-ubuntu/](http://www.earth-org.com/blogs/2009/08/install-genuine-firefox-3-5-latest-on-ubuntu/)

the instructions on that blog are wrong. you shouldn't run ubuntuzilla with sudo.

why not link directry to [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) which is certain to have correct instructions, instead of some random blog post? :)

---

### Post by oldsoundguy on 2009-08-14
> **nanotube said:**
> the instructions on that blog are wrong. you shouldn't run ubuntuzilla with sudo.

why not link directry to [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net) which is certain to have correct instructions, instead of some random blog post? :)

+1 and can I have an AMEN!

BE SAFE folks!  Use only known, quality sites or the repositories.  DO NOT leave the door open to the ever so slight possibility of putting something nasty into your computer .. even though nothing exists in the wild at present, why tempt fate?

---

### Post by philinux on 2009-08-14
When you download the ubuntuzilla deb package and double click it gdebi with ask for your root password anyway.

---

### Post by bear24rw on 2009-08-14
im pretty sure that the firefox package is now 3.5.2

---

### Post by qamelian on 2009-08-14
> **bear24rw said:**
> im pretty sure that the firefox package is now 3.5.2
You're correct. It is in the Karmic repos since at least yesterday.

---

### Post by jppr on 2009-08-14
i use 3.5.3pre and 3.6a2pre  [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

---

