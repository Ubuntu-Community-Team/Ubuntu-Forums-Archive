---
title: "New Compiz (0.8*)"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by smbm on 2009-03-09
Just updated to the new Compiz.

Something seems to be up here though, the old no window borders problem.

I'm on Intel X3100.

Anyone else having problems?

---

### Post by kj74 on 2009-03-09
You upgraded too early, your compiz install is now broken. Some parts are still not build.

---

### Post by smbm on 2009-03-09
Fair enough, I was using Metacity anyway. 

No big deal.

I created another user to test things like new Compizs.

I'll look out for more updates.

---

### Post by smbm on 2009-03-09
> **kj74 said:**
> You upgraded too early, your compiz install is now broken. Some parts are still not build.

Just out of interest, where would one get information about what's built and what's not?

Cheers.

---

### Post by olskar on 2009-03-09
> **smbm said:**
> Just out of interest, where would one get information about what's built and what's not?

Cheers.

[https://launchpad.net/ubuntu/+builds](https://launchpad.net/ubuntu/+builds) :)

---

### Post by smbm on 2009-03-09
> **olskar said:**
> [https://launchpad.net/ubuntu/+builds](https://launchpad.net/ubuntu/+builds) :)

Good call.

I'll bookmark it now.

Cheers.

---

### Post by Eclipse. on 2009-03-09
Do not do partial upgrades or things like this will happen.You can also end up removing packages which are important.

Re-install ubuntu-desktop to make sure you have everything you should have.

---

### Post by smbm on 2009-03-09
It wasn't a partial upgrade, ubuntu-desktop was not removed, this isn't my first time running a development release.

---

### Post by Eclipse. on 2009-03-09
> **smbm said:**
> It wasn't a partial upgrade, ubuntu-desktop was not removed, this isn't my first time running a development release.

Then very werid, so you got offered compiz when it wasnt fully built from a full upgrade.

That seriously should not happen.

---

### Post by Fedup on 2009-03-09
> **Eclipse. said:**
> Then very werid, so you got offered compiz when it wasnt fully built from a full upgrade.

That seriously should not happen.

It may be weird, but its happened to me too..:( How do I get it back to normal?

---

### Post by smbm on 2009-03-09
I think what's happened is that the gconf config backend thing isn't ready yet and obviously something somewhere has gone screwy.

I definitely still have Ubuntu desktop.

There were more packages being removed than being installed but sometimes that just happens in my experience, especially when upgrading to brand new versions of software (IE 0.7 > 0.8). I figured they might have rolled the gconf backend stuff into a different package as everything else seemed in order.  

I decided to take a chance based on the knowledge that it wouldn't break much except compiz itself (which I don't use).

Like I said, no big deal (for me anyway).

I'd advise anyone that uses Compiz to hold off though.

---

### Post by smbm on 2009-03-09
> **Fedup said:**
> It may be weird, but its happened to me too..:( How do I get it back to normal?

Has it fallen back to Metacity or do you have no window borders?

---

### Post by Darkshade on 2009-03-09
When I ran "apt-get update && apt-get upgrade" a while ago (something that I can't prevent my hands from typing every hour or so) it said that compiz have been kept back. No idea how you installed it.

---

### Post by smbm on 2009-03-09
I used update manager, did it about 5 mins before I started this thread.

It all seemed pretty normal, no partial upgrade warning or anything.

---

### Post by philinux on 2009-03-09
I just fired up update-manager and I quit cos of the partial update. I'll hang on till tomoz.

---

### Post by PRGUY85 on 2009-03-09
Happened to me too with Partial Upgrade.

I have to learn not to click all updates that come around.

How do I solve this?  Wait for upgrade manager to fix it by itself on a future update?

---

### Post by autocrosser on 2009-03-09
I strictly avoid Partial Upgrades--I'll open Synaptic to see what the "upgrade" will remove & if I don't think that it looks good....I wait.

---

### Post by CarlAndrews on 2009-03-10
I also have the same result.

apt-get update && apt-get dist-upgrade
 
(I run this command at least once an hour when runing development releases of ubuntu - I love suprises and updates! :-> )

nothing about a partial upgrade.

no window boarders, to fix I used:
[alt]-[f2] and typed compiz-decorator

This or [alt]-[f2] and metacity --replace

will bring window boarders back but enabling visual effects (normal or extra) will not work. Of course I now know why after reading this thread.

I also still have ubuntu-desktop.



Thanks for all of your hard work.

---

### Post by lostinquestions on 2009-03-10
\Always apt-get upgrade, guys, don't use the package manager stuff or dist-upgrade during development unless you're prepared for breakage :D

---

### Post by CarlAndrews on 2009-03-10
Thanks!

I have always used dist-upgrade and not upgrade. The only other time I have had an issue was with I think it was Dapper and an Intel card. xorg was a little messed up for half a day (wide black band across the middle of the screen)

I will switch to 'apt-get update && apt-get upgrade' I just assumed that 'dist-upgrade' was the preferred choice to make certain to get all of the development updates.

Thanks again!!

---

### Post by lithorus on 2009-03-10
> **lostinquestions said:**
> \Always apt-get upgrade, guys, don't use the package manager stuff or dist-upgrade during development unless you're prepared for breakage :D
No, the other way around. Never just use apt-get upgrade. Always use a package manager (aptitude prefered here) and look out for things like packages that won't upgrade because of missing dependencies. The compiz issue is because the dependencies were not written specificially well and the ibcompizconfig0 got upgraded while some of the other compiz packages didn't. The dependencies of 'compiz' were not very specific on version numbers for the libraries.

The new compiz packages seems to have them right though.

Anyway it seems to have been straightened out now and at least it's working fine here :)

---

### Post by MacUntu on 2009-03-10
> **lithorus said:**
> No, the other way around. Never just use apt-get upgrade. Always use a package manager

Exactly. There are situations that cannot be easily solved with information stored in packages. Adding such logic to the package manager is much easier. 

In addition: Just look at what's going to happen. If compiz is marked for removing then it won't be there after the upgrade - hardly surprising! :D

---

### Post by ToasterThief on 2009-03-10
It seems to be solved now, at least when updating from the main server repository.

---

### Post by smbm on 2009-03-10
> **lithorus said:**
> The compiz issue is because the dependencies were not written specificially well and the ibcompizconfig0 got upgraded while some of the other compiz packages didn't. The dependencies of 'compiz' were not very specific on version numbers for the libraries.

That seems to be it. Thanks for your insight.

---

### Post by smbm on 2009-03-10
> **MacUntu said:**
> Just look at what's going to happen. If compiz is marked for removing then it won't be there after the upgrade - hardly surprising!

I think I should just reiterate that **at no point was it apparent that this was a partial upgrade and Compiz was not marked for removal or in fact actually removed at any point.**

---

### Post by smbm on 2009-03-10
> **ToasterThief said:**
> It seems to be solved now, at least when updating from the main server repository.

I am finding that too. Good to see everything is ship shape again.

---

### Post by Nullack on 2009-03-10
> **smbm said:**
> I think I should just reiterate that **at no point was it apparent that this was a partial upgrade and Compiz was not marked for removal or in fact actually removed at any point.**

Use synaptic, it tells you

---

### Post by smbm on 2009-03-10
> **Nullack said:**
> Use synaptic, it tells you

Update Manager normally does too. 

I'm not sure what happened there though.

I usually do use Synaptic but for some reason used Update Manager on this one occasion.

---

### Post by jackhynes on 2009-03-10
I did an Alt + F2 "upgrade-manager -d" then closed the option to partial upgrade and clicked the "a new distribution 9.04 is available" button.

If compiz was installed before and it's part of the session startup isn't that why it breaks in Jaunty -- cause it's not there.

---

### Post by Jay_Bee on 2009-03-10
I just updated and now compiz is so slow (intel x3100 with uxa) it's unusable. It updates the screen like every 3 seconds.

---

### Post by vredley on 2009-03-10
Same here. Switching to LXDE until the dust settles...

---

### Post by Technoviking on 2009-03-10
If you updated your compiz early and had some packages removed, Do the following to get your compiz working again.

```
sudo apt-get update
sudo apt-get install compiz
```
Then though the menu.
```
System --> Appearance --> Visual Effects --> Normal or Extra
```

Optional:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Stetzen on 2009-03-10
> **Jay_Bee said:**
> I just updated and now compiz is so slow (intel x3100 with uxa) it's unusable. It updates the screen like every 3 seconds.
 
And similar problem here. It's definitely not a simple compositing issue, because metacity with compositing enabled works fine. Disabling all compiz plugins do nothing - it is still slow. :(

---

### Post by Amaranth on 2009-03-10
Sounds like an upgrade at the same time caused you guys to get the Software Renderer. Compiz should not start in that case (it checks glxinfo for it) but perhaps you've set it to skip errors?

---

### Post by Stetzen on 2009-03-10
Definitely not. glxgears (and other 3d apps) work as they should, and glxinfo gives "direct rendering: Yes".

---

### Post by Amaranth on 2009-03-10
Do other 3D apps actually get full FPS? Games and such, not simple things like glxgears. It is possible to have direct rendering: Yes but still have software rendering. Otherwise, does this happen with EXA?

---

### Post by gwenn on 2009-03-10
Had the same problems with compiz.Just removed and reinstalled,then dpkg and now everything work fine.I'm using compiz fusion icon

---

### Post by Stetzen on 2009-03-10
Other 3d apps (tested on OpenArena) work as expected, with normal FPS. And it does not happen with EXA

---

### Post by smbm on 2009-03-10
I have a new and strange problem that I suspect may be related to this:

I created a test user on my system to test out Compiz as I don't usually use it on my main account. Since the new version has been installed I've tested it a couple of times and performance seems excellent. 

When I go back to re-enable desktop effects in my appearance applet (which was the method I used to disable them) on my account it doesn't let me. It says searching for drivers then flickers a couple of times and says desktop effects could not be enabled.

Clearly they are working on the test account but not on mine.

Does anyone have any tips as to how I can start to debug this?

Cheers

---

### Post by vredley on 2009-03-10
> **Amaranth said:**
> Do other 3D apps actually get full FPS? Games and such, not simple things like glxgears. It is possible to have direct rendering: Yes but still have software rendering. Otherwise, does this happen with EXA?

Problem "solved" with UXA disabled. In quotes because the display is very slow to update with EXA. So it seems to be a choice between UXA and Compiz at the moment.

---

### Post by Tich666 on 2009-03-10
> **vredley said:**
> Problem "solved" with UXA disabled. In quotes because the display is very slow to update with EXA. So it seems to be a choice between UXA and Compiz at the moment.

Consider yourself lucky.. 

For me it's the choice between dual monitors (laptop display and 22" TFT) and compiz in addition to the EXA / UXA dilemma because for some reason 3d acceleration only works up to a virtual screen size of 2048x2048 (which clearly isn't big enough for two WS monitors next to each other).

On Vista it works fine with aero on two screens which really causes me the most grief.

---

### Post by scaine on 2009-03-10
I'm with vredley - I've had to disable UXA on my Tosh U400 (GMA4500 graphics), as Compiz gives me about 1 frame every 5-6 seconds with UXA enabled.

However, it's very quick with UXA disabled.  Gonna have a wee look at Compiz Settings Manager and see what's new...

---

### Post by klange on 2009-03-10
> **Amaranth said:**
> Do other 3D apps actually get full FPS? Games and such, not simple things like glxgears. It is possible to have direct rendering: Yes but still have software rendering. Otherwise, does this happen with EXA?

There's always going to be a decrease when you're redirecting to a texture that is then rendered separately, I'd thought you'd know that, Amaranth. While in theory, it would be slightly slower than something like EXA, quite the opposite is true due to the decrepit state of the Intel driver (UXA can be anywhere from 1/100 to 100 times the speed of EXA right now, see above posts... personally, I get 400+FPS in glxgears with UXA and 40 with EXA, other apps follow suit).

@Tich: That's a hardware issue with limited workarounds, none of which the Council wants to put serious discussion into.

---

### Post by jackhynes on 2009-03-11
Compiz is very slow for me also, not sure how to disable anything though. It was exciting to see the first new notification bubble though!

---

### Post by quazi on 2009-03-12
Have you tried reseting the compiz options to default?  I know I've had problems in the past using older configurations with new versions of compiz.

---

### Post by Stetzen on 2009-03-13
I've just done a fresh install of alpha6, and a problem is still here, so it's nothing to do with compiz settings, the bug is in compiz itself (or in intel driver :))

---

### Post by rburkartjo on 2009-03-13
finally working great

---

### Post by Stetzen on 2009-03-14
it does not work for me, even with fresh install. Yhe bug is on the launchpad ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/340578](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/340578)), pleas help the developers to solve this issue!

---

### Post by Amaranth on 2009-03-16
You have to disable sync to vblank in ccsm, then it will work with UXA.

---

### Post by vredley on 2009-03-16
> **Amaranth said:**
> You have to disable sync to vblank in ccsm, then it will work with UXA.
Compiz is working perfectly again - thank you!

---

### Post by scaine on 2009-03-16
My Vblank was already "unset" (no tick) in CCSM/General Options/Display Settings/Sync to VBLANK, and I was only good for about 1 frame every 5-6 seconds when I used UXA.

However, there's been another big round of kernel updates recently, so I'll give it another shot.

---

### Post by Amaranth on 2009-03-17
This fix will be in the next compiz upload (it may already be available at this point). This option was supposed to be disabled but a file name changed so it was accidentally enabled again.

---

