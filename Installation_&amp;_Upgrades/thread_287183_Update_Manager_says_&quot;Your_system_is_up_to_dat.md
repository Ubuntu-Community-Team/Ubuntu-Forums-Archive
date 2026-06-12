---
title: "Update Manager says &quot;Your system is up to date&quot;."
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Carbonfish on 2006-10-28
Hi all,

I have attempted to upgrade to Edgy a couple of times using the Update Manager (gksu "update-manager -c") and the update manager grinds through it's process and then informs me that my system is up to date.

Well, since I am typing this using Dapper, my system is not "up to date".

Should I run the apt-get dist-upgrade?

Also, I have been reading the forums with great interest and am now wondering if I should wait awhile before upgrading at all.

The only "improvement" that I *really* have to have is Firefox 2, and I can get the tar.gz file for that from Mozilla.

What do you all think?

TIA for your feedback,

KC

---

### Post by TheWizzard on 2006-10-28
to be honest, why upgade in the first place?

dapper is a fine working system and, if the backports work properly, doesn't leave you with out dated software. edgy is supposed to be "edgy", so it may cause you problems (although most of what a read in the forums indicate that edgy is pretty stable). 

if you upgrade i'd recommend a clean install. always.

---

### Post by Carbonfish on 2006-10-28
Thanks for the reply Wizzard,

You may be right. As long as the repositories continue to be updated for Dapper I will be happy, and Dapper is very stable. I guess that I'll just go to Mozilla and get the tar.gz file for Firefox and wait and see how Edgy shakes out.

KC

---

### Post by cptnapalm on 2006-10-28
A good idea.  I myself did the upgrade, even though I really had not initially planned on doing so.  A lot of stuff didn't work properly, initially.  Then again, the update took so long due to slow download speed (so many people doing their upgrades) that I had to suspend my laptop between download sessions.  This may have caused problems.

The only really aggravating thing was that I had courier-* installed and the newer versions could not be straight forwardly upgraded.  *THAT* was a serious pain, due to some limitations of the apt system.

For 3D acceleration, I had to add a small section to the bottom of my xorg.conf.

I had to manually add the usplash-ubuntu package as it was not installed by default.  Really, though it should have been installed by default, it was not that big of a deal.

Although there is not much in everyday usage which has changed, by having to deal with the problems, I did see how much "under the hood" stuff has.  There is a LOT which is very different, upstart being the most obvious.

How are things after everything?  Better.  It is better than Dapper, once worked out properly, though kinks remain.  Time from boot to login screen is FAR shorter.

One thing I would love to see in edgy+1 would be consistent keyboard shortcuts for closing apps in X.  For example, to close Firefox, it is Ctrl-Q, for Synaptic it is Ctrl-W, and for the terminal it is Ctrl-D.  The most rational one is the terminal's Ctrl-D as that is the Unix EOL (or is it EOF...).  Hit that on a shell login and it will log you out.  So it makes the most internally sane choice.

---

### Post by Carbonfish on 2006-10-28
> **cptnapalm said:**
> 

One thing I would love to see in edgy+1 would be consistent keyboard shortcuts for closing apps in X.

I thought the same thing about Dapper and mentioned it one day here on the forums and someone asked me what was wrong with good old alt F4. They had a good point. I've been using that ever since and it seems to close any open app.  ;) 

As far as the upgrade to Edgy goes I still don't have any idea why *gksu "update-manager -c"* didn't do the trick, but since it didn't, I think that I'll wait a few and see if any of these new release growing pains get resolved.

Anybody who has any idea why the update manager thought my system was "up to date" and didn't offer to upgrade my sys., I would appreciate your insight.

Thanx,

KC

---

### Post by LuisC-SM on 2006-10-28
> **Carbonfish said:**
> ......

Anybody who has any idea why the update manager thought my system was "up to date" and didn't offer to upgrade my sys., I would appreciate your insight.

Thanx,

KC

U must click again on the "Search" Button (Mine is in spanish so I'm guessing u have 2 buttons... Search and Install), then on the top u will see the "new version" upgrade button.

Regards

Luis C. Suárez

---

### Post by Carbonfish on 2006-10-28
Thanks Luis, but I tried that. I read that someone else said that the upgrade command did nothing when they tried it. Perhaps the server was maxed or something... I don't know. Anyhow, I think I'll give it a few days, or maybe a week or two before I do the upgrade thing and see if things get a bit smoother after the "rush" is over. :cool:

---

### Post by LuisC-SM on 2006-10-29
Well, YAW.

I must say 2 things:

1. The solution given before, worked for me... and
2. I'm so unhappy this had worked for me, 'cause I hosed my daughter's pc and I don't see the way to fix it and now she'll go back to M$winXP, so that is really frustating for me. ](*,) ](*,) ](*,) ](*,) 

So I believe it is a lot better to wait a litte longer until devs have everything fixed (as in dapper)

Regards

Luis C. Suárez

---

### Post by nzmoose on 2006-10-29
all good and true. for those who still dare the upgrade, try:

gksudo "update-manager -c -d"

the -d make all the ifference

see?

---

### Post by TheWizzard on 2006-10-29
> **Carbonfish said:**
> Thanks for the reply Wizzard,

You may be right. As long as the repositories continue to be updated for Dapper I will be happy, and Dapper is very stable. I guess that I'll just go to Mozilla and get the tar.gz file for Firefox and wait and see how Edgy shakes out.

KC

if you build from source, please use checkinstall. this nice programm makes a deb-file for you which you can install. in this way the package manager "knows" you installed the package. otherwise it may be quite hard to remove the program later.

you can also wait and see if firefox appears on the dapper backport repos.

---

### Post by Carbonfish on 2006-10-29
> **TheWizzard said:**
> if you build from source, please use checkinstall. this nice programm makes a deb-file for you which you can install. in this way the package manager "knows" you installed the package. otherwise it may be quite hard to remove the program later.

you can also wait and see if firefox appears on the dapper backport repos.

Good advice Wizzard. Thanks.

KC

---

