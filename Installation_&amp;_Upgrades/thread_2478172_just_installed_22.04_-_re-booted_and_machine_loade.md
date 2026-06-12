---
title: "just installed 22.04 - re-booted and machine loaded old firefox"
date: 2022-08-18
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-08-18
I have just installed 22.04 and am trying to set stuff up.  Not going well.  I also am using an ssd as my main drive instead of a hard drive to speed things up.  Anyway, the ssd is broken into two parts.  The first (for boot I think) is 537mb and the other is 9 hundred and some gigabytes (ssd is 1tb)  I also changed the label on the second one to "data4" then I tried to re-boot to see what happened.  I also changed the label to nothing and tried again.  I am still loading an "older version of firefox".  That is when it told me that I had opened an old version of firefox and it might screw everything up.  So, before I did anything I thought I had better ask to see what I should do now to stop it from loading an older version.  I have no idea why its doing this as I haven't done any more than what I have told you.  I don't think I did anything in the firefox setup to make it do this. 

Oh, this firefox is under snap (default) but I have not messed with it.

Thank you.............

---

### Post by &amp;KyT$0P# on 2022-08-18
It means the Firefox build with which you're currently trying to use your Firefox profile has an older build date than the last Firefox build you used that profile with.

You have a few options:

1) Install/use the exact same (or later) Firefox build as you previously used your Firefox profile with.

2) If both Firefoxes are the same major version (e.g. both 103.something), you can safely start this one with the [FONT=Courier New]--allow-downgrade[/FONT] command-line option.  (No idea how to do this with snap Firefox, as I don't use snapd or any snaps at all.)

3) Another possibility would be to create a new Firefox profile.  You will go back to all defaults this way, but you might be able to transfer your settings and important data following [this article]("https://support.mozilla.org/kb/recovering-important-data-from-an-old-profile").

---

### Post by jgw on 2022-08-18
Thank you for the reply!

what I did was to delete the on in snap and then installed one that was not on snap and everything is dandy.  I have no idea why it was doing that but installing it outside of snap did the trick. 

Thanks again!

---

