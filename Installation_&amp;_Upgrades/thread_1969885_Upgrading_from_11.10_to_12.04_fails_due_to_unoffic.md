---
title: "Upgrading from 11.10 to 12.04 fails due to unofficial packages"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by creepa1982 on 2012-04-30
Dear all, 

I have trouble upgrading from ubuntu 11.10 to 12.04 on a Lenovo Thinkpad T420. I get the error: 

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug update-manager' in a terminal.
----

uname -a gives me: 
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

so it is probably a problem with unofficial software packages. 

I am unsure which packages need to be reverted. I attached the dist-upgrade log files to this post. I would be very grateful if someone can have a look at them and maybe give me a hint on how to track down the problem. 

Thanks!

---

### Post by grahammechanical on 2012-04-30
You can try loading Update Manager and clicking on Settings. This may be due to having a PPA or two in your software sources. It could be that these unsupported applications do not yet have repositories for Precise (12.04).

Is always best to move the OS as close to a default installation as possible and to updated it before running the upgrade.

Regards.

---

### Post by tommcd on 2012-04-30
It always amazes me just how many people will add a boatload of these unsupported PPA repos to their sources; and then they somehow expect the Ubuntu upgrade manager to seamlessly make sense of it all and upgrade the whole OS to the next version without problems. And then they wonder why it fails!
If you want a seamless upgrade, then stick to the default Ubuntu sources. For a totally problem free upgrade, just do a clean install of the next version of Ubuntu. This is the fastest, easiest, and most problem free method of upgrading Ubuntu.

I never use any of those PPA repos. I have used every single version of Ubuntu since the inaugural 4.10. I always do clean installs. I never do dist-upgrades; and I never have had a problem with this ever.

---

### Post by creepa1982 on 2012-05-01
Hey guys, thanks for your replies. 

The only third party ppa I remember using was this one: 

add-apt-repository ppa:oibaf/graphics-drivers

I also found this thread [http://askubuntu.com/questions/125500/upgrade-to-12-04-failed-due-to-held-back-packages](http://askubuntu.com/questions/125500/upgrade-to-12-04-failed-due-to-held-back-packages)

sudo ppa-purge ppa:oibaf/graphics-drivers goes through but the upgrade still has the same problem. So I'm wondering whether I have to uninstall specific packages. 

Just to be clear, I don't randomly add ppas. The reason I added this one was because all graphics were messed up with a clean install. Also it's not my expectation that the upgrade runs smoothly. I simply ask for suggestions to proceed with it because I rather not redo all my settings in /etc, some I probably don't even remember I did. 

I guess I'm stuck though, so I'll have to go with a clean install. 

Thanks for your suggestions.

---

