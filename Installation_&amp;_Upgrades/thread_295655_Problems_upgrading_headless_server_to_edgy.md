---
title: "Problems upgrading headless server to edgy"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by sjwk on 2006-11-08
What is the recommended way to upgrade 6.06 server edition to Edgy?

Most people running server probably don't have it running a graphical desktop of any kind (and probably also don't want it to be!)

I have about a dozen ubuntu servers and decided to do an experimental upgrade of one of my test machines.

It doesn't run X, but does have most of the libraries installed for remote graphical apps, so (after installing update-manager and then, after searching the forums, the python-vte and gtk2 packages) was able to get it to run, displaying to my Windows/cygwin workstation.  Great.

Then I click on 'upgrade' and it fails and quits out.  Because something essential was missing?  No - well, not unless you think a hicolor icon for update-manager is essential, and clearly the gtk libraries *do*...

Moving on, I hunted out and installed the hicolor-icon-theme package which fixed that.  Now I can continue...

Rerun and click upgrade once more...  looks good, it whirrs away updating package sources and downloading files.  Then suddenly a fatal error saying that it can't guess what meta-package I'm using and since it can't decide if I'm using ubuntu desktop, kubuntu or xubuntu, it's just going to give up now and quit.

OK, well.  I don't *want *a desktop, but out of interest what packages does it want to install if I tell it to install ubuntu-desktop?  Ah.  I see, it has already half updated the system and now the sources all refer to edgy and it won't install those because they clash with the dapper package versions..

So, to finish a long and rambling post...

Could I please add the following to a wish list:
[LIST]
[*]Some upgrade instructions for server edition
[*]If it isn't possible to upgrade, something in the documentation to say so
[*]An upgrade utility that doesn't require a graphical interface just so that you can click on an 'upgrade' button
[*]An upgrade utility that checks that it has the information it needs *before* it starts updating key files, or has the ability to reverse the changes it's made if it comes up with a problem
[/LIST]

Is it even possible to upgrade server?  Or does it require a fresh install?  I know that Edgy is not considered a recommended upgrade for critical servers, but I had expected it to work on a more or less fresh system with no complicated third party drivers or flashy graphics...  the upgrade info does say:
> This release will be supported for 18 months on both desktops and servers

Don't get me wrong, this is intended as constructive criticism...  I really like ubuntu (I've tried most of the mainstream distributions in the last 14 years) and I'm appreciative of the work that has gone into it, and if I had the time to help out in some way, to a level that would do it justice, then I would, rather than just complain :)

I'm now hoping that having done the first bit, dist-upgrade will finish the job... but if not, reinstall-time!

Cheers,
Steve.

---

### Post by an.echte.trilingue on 2006-11-08
Why don't you want to just edit your /etc/apt/sources.list to point to edgy repositories and 

```
sudo apt-get update
sudo apt-get dist-upgrade
```


???

---

### Post by sjwk on 2006-11-08
Because the instructions say that you really should use update-manager and that if you do it manually, bad things happen, everything breaks and the sky will fall in. (or words to that effect!)

But yes, I am.  My point was that if the method detailed in the instructions don't work, it should say so, and say how you *should* be doing it.  Perhaps I'll try another clean update and write a quick howto, but no point if someone else has already done so..

---

### Post by an.echte.trilingue on 2006-11-08
> My point was that if the method detailed in the instructions don't work, it should say so, and say how you should be doing it.

I agree with you absolutely.  One thing I really don't like about ubuntu is their insistance on things like that.

If you suggest that setting a root password and using su might work for some people in some cases instead of sudo or sudo -i, people jump all over you, with the refrain that "somebody who knows more than me said it can do bad things!"  This statement has no basis in reality, and if you call people on that fact, then they try to claim that sudo is "more elegant," despite the total absence of any objective evidence for this!

Then there is this update manager.  OK, lets think about this one.  Every upgrade previous to this last one went as flawlessly for the community as a typical debian update tends to do, and it was based on apt-get.  There is all sorts of trouble around this upgrade and it was based on the new update manager tool, yet the wiki says about apt: **Please note - this method is much less reliable.**  Are they high?  To date no other linux distro has come up with a better package manager than apt-get, and they mean to tell me that this update manager causes fewer problems?  I would edit that myself but I am sure it would be reverted right away.

I think I understand what is going on: Ubuntu is trying to create a branding while making everything GUI so that people beyond the enthusiast crowd want to use it.  I respect this, and I thank them for it.

However, in doing this Ubuntu and the Ubuntu community are stifling choice (what if su root would work better for some? they would never know about it if they follow advice here) and honesty (how about: the update manager is still a work in progress, but we think it is really good and will work if you try it).

My advice:  the community here is really helpful, but if you think you might know better, do what you think.  Fight the groupthink, that's for MS.

</rant>

---

