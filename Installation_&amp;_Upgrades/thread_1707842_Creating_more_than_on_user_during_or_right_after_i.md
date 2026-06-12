---
title: "Creating more than on user during or right after install"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by Jguy on 2011-03-15
Hello,

I have a requirement to create more than one user (one initial user with sudoer privs and one "user" user that has no special privs) upon installation of xubuntu 10.04 or 10.10 (doesn't matter). My goal is to create a "automatic" installation process with as little user interaction as possible through use of preseeding and remastersys so that all the programs and their configurations are set upon first boot. If this is not possible, (which I don't believe it is, but it's Linux!) then I think I can make use of a bash script that will run on first boot of the operating system and then delete itself so that it does not run again. My questions are:

* Is there anyway to create more than one user upon or during installation?
* If no to the above, how would I go about making a bash script that runs on first boot and deletes itself after being ran?

Thank you for any help you can provide.

---

### Post by kagerato on 2011-03-15
The default Ubiquity-driven installer for Ubuntu doesn't give you the option of creating multiple users, purely for simplicity.

You can use remastersys to generate an installable image of your preconfigured system.  That will accomplish your goal as long as you don't mind the configuration being identical on the source and target systems.

It is also possible to customize an Ubiquity installation to run custom post-installation commands.  [https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation) talks about that a bit.  I've never done that myself; personally, I find Ubiquity over-engineered for what it does.

If you find another installer that you prefer, you could of course use that.

I would not recommend creating self-deleting (suicidal) scripts or startup services.  Although it is feasible to make it work, if you really want to.  There's no magic to it; you just need to register a classic init.d style startup script on the default runlevel, and have its start() or stop() behavior issue the rm command after completing its task.  As there is no restriction in Unix on processes deleting their own source executables (or scripts in this case), on the next reboot, it'll be permanently gone.

The concern with that method is that it seems magical to the user; one-time untraceable effects and all that.

There are yet other ways.  You could create a non-suicidal init script which uses proper conditional logic to check for the existence of a user, and only generate one when it is not present.

All in all, it depends a lot on your use case.  To me, it seems overkill to create any scripts at all just for one user, but it's up to you what path to pursue.

---

### Post by Jguy on 2011-03-16
Thanks kagerato. This helps.

I thought about using remastersys, and that maybe the way I go irregardless, it seems to be the easiest. My ultimate goal is to make the process as automatic as possible as we have a lot of machines to install xubuntu on and configure and not a lot of time (about 35 machines are required, and we can only work on them for two days until they need to be done in two months). I do not mind that the configuration is the same across all machines, it's logical because all of our machines are almost identical.

---

