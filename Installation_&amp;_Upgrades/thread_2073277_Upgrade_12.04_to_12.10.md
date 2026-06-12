---
title: "Upgrade 12.04 to 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2012-10-19
I have upgraded to every new release since 8.04 with little problem. Now I am trying to move from 12.04 to 12.10 Quantal and things are hanging up.

How can I use synaptic to do this upgrade? Can't seem to find it there.

I am wired, did all updates first, ran tweak janitor. Got message on update manager that the upgrade was available. Hung on file 1299 of 1889.

---

### Post by SwiftPengu on 2012-10-19
> **s9032g@comcast.net said:**
> I have upgraded to every new release since 8.04 with little problem. Now I am trying to move from 12.04 to 12.10 Quantal and things are hanging up.

How can I use synaptic to do this upgrade? Can't seem to find it there.

I am wired, did all updates first, ran tweak janitor. Got message on update manager that the upgrade was available. Hung on file 1299 of 1889.
Are you getting any error messages?
Did the installation hang during the downloading of the 1299'th file, during installing or during setup?

---

### Post by s9032g@comcast.net on 2012-10-19
The screen showed during downloading. However I suspect that it was during installation. Now trying sudo apt-get upgrade. That hangs too.

How do I disable third party repositories? Synaptic just gives me a runaround.

---

### Post by 2F4U on 2012-10-19
Since you are currently on a LTS, you have to reconfigure it first to show you any new version. Then you can use Update Manager to perform the update:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading)

---

### Post by Cheesemill on 2012-10-19
> **s9032g@comcast.net said:**
> I am wired.
This could be your problem :)

Seriously though, if it's hanging at the download stage it could just be the usual problem with overloaded servers that happens every new release.

---

### Post by s9032g@comcast.net on 2012-10-19
24FU AND CHEESEMILL

I did fully update 12.04. Being wired for an update is always, I believe, recommended.

Now I ran sudo apt-get update. I seemed to be going well but then it hung up. I had to get off using the power key. Now when it comes up it says I have 12.04, I get on line ok. BUT no top bar showing usual choices, and no unity panel, so no terminal
 How can i get back to a terminal?

---

### Post by s9032g@comcast.net on 2012-10-19
Shortcut to terminal CTL+alt+T does not work.

I may have to do a complete reinstall from a dvd. It's a mess.

---

### Post by darkod on 2012-10-19
What about Ctrl+Alt+F1?

And did you try a 12.10 live cd before you started the upgrade? Some issues that exist come to light when using the live cd first.

Also, are you upgrading because you need to, or because it's the latest release that came out yesterday? Is there anything that you can't install or add to 12.04 so you have to use 12.10?

12.04 is LTS and will have support for 5yrs, while 12.10 is normal relase and only 18 months. You don't have to jump from release to release every 6 months, you are only elarging the possibility things to go wrong.

---

### Post by s9032g@comcast.net on 2012-10-19
ctl+alt+f1 does not work either.

No, I did not try a cd first. Just an upgrade.

Why move? I guess I am just interested in Ubuntu and willing to take chances. Usually goes very well.

Now I am trying to burn a dvd with windows. That was going well until 647 of 753 mbs was reached, the that hung up.

Is this thing ready for prime time????

---

### Post by Slim Odds on 2012-10-19
> **Cheesemill said:**
> This could be your problem :)

Seriously though, if it's hanging at the download stage it could just be the usual problem with overloaded servers that happens every new release.
Especially ON RELEASE DAY!!!

Never, ever, upgrade on release day unless you want problems. :(

---

### Post by Slim Odds on 2012-10-19
> **s9032g@comcast.net said:**
> ctl+alt+f1 does not work either.

No, I did not try a cd first. Just an upgrade.

Why move? I guess I am just interested in Ubuntu and willing to take chances. Usually goes very well.

Now I am trying to burn a dvd with windows. That was going well until 647 of 753 mbs was reached, the that hung up.

Is this thing ready for prime time????
No, but it is ready to be released.

---

### Post by s9032g@comcast.net on 2012-10-19
Burned an iso and did a complete reinstall. Ok now.

---

