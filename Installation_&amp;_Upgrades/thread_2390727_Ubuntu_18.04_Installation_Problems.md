---
title: "Ubuntu 18.04 Installation Problems"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2018-05-01
I backed up everything from my laptop preparatory to migrating to Ubuntu 18.04.  I then installed Ubuntu 18.04 and then restored the backup:

NOTHING IS WORKING!

I cannot get into Ubuntu Forums because the new install does not recognize the saved signon information that I have restored.  So I have to sign in from a system I haven't upgraded yet.
I cannot get into Thunderbird because the new install does not recognize the saved profile information that I have restored and Mozilla provides documentation on how to do stuff with Windoze and they do not have the resources to actually answer questions!
And the same for EVERY OTHER PRODUCT ON THE SYSTEM!  The .thunderbird/profile.ini file points at the correct folder but stupid Thunderbird keeps demanding that I reeenter EVERYTHING FROM SCRATCH!
Every piece of software I had installed on the system before migrating now has to be reinstalled because the stupid install image only understands how to erase the whole disk! And that is despite what was on the system before was the slightly customized version of 17.10 that System 76 distributes!

I have followed the process and restored every file to my home directory,  why does the new system ignore all of that?

---

### Post by oldfred on 2018-05-02
Have not yet converted Thunderbird to use my 18.04 install. I still have 16.04 as main working install.

But with Thunderbird & Firefox I always have to start them so they create a new profile. Then I copy my profile into their folder & edit profile.ini to use mine.
I now have dual boot and keep the profiles in a shared data partition /mnt/data used on all my systems. And then I just start Thunderbird & then copy my profile over the new one just created.

I think if you just copy your profiles into your system, you have to manually select to use that profile, rather than the default one it creates when first started.

---

