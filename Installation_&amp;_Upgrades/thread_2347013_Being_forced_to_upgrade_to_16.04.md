---
title: "Being forced to upgrade to 16.04?"
date: 2016-12-20
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2016-12-20
My installation of 14.04LTS was working just fine, then I had an update that included Firefox and many other apps and such (240Mb worth). When they downloaded and installed -- and I rebooted, as required -- things went really crazy.

At bootup, I get "Some things didn't download - run the update now?" I click Do It and ten seconds later I am asked to do it again. During that ten seconds, a terminal window pops up, I see a bit of downloading, and just as the window is closing again, I see that whatever it was downloaded, but that's all. I do NOT see if it downloaded properly. Then the "Some things didn't download - run the update now?" pop-up appears again.

Now Firefox fails to start and I get the "please report problem..."

Thunderbird fails to start and I get "please report to Mozilla...."

The system tools manager may or may not start. If it does, some of the settings will work, others will hang, turn grey, and then the entire window just disappears. The "Info" is one the simply disappears. I can't get it from the top Menu bar either under my username -> System Info.

If I open a terminal, I can get a few things to run, but most of the time any command I issue (with or without SUDO) will simply give me back the prompt after ten seconds or so.

Gimp will not run - it greys out and I get a failure notice that "something inside 14.04 broke".

Ubuntu Tweak will give me the splash screen, grey out and die.

Now, on bootup, I get "something internal to 14.04 failed" and I am asked to report it. I also see "A new version is availzable...." and before I can enter my password, the box disappears and I am not asked to upgrade again until I log out and back in.

Every app on my Unity bar will fail and I am asked to report the problem, which,of course, fails also.

So, apparently, I don't have the option of UPGRADE and thus save all my apps. I have to completely INSTALL 16.04 cold and wipe everything out.

Is this true or not? Can I recover from whatever it was that whacked my system? I know how to use apt-get, but that doesn't seem to help. Can that be used to do the 16.04 upgrade?

Bill

---

### Post by #&amp;thj^% on 2016-12-20
Make Sure you have a good **Back-up in Place First**.
```
sudo do-release-upgrade

```
Should get you to 16.04..._But first disable any PPAs you might have and also uninstall proprietary Drivers IE: Nvidia or Radeon _

---

### Post by WB0HYQ on 2016-12-20
Well, a backup is problematical. It won't run either. Kills itself in the middle of starting.

I'll give the command a try. Probably tomorrow as I've burned out on this one for today.

Bill

---

### Post by ian-weisser on 2016-12-20
I find that release-upgrading a broken system rarely fixes the system.

I suggest using a LiveUSB to back up your /home and valuable data. Then fresh-install either 14.04 or 16.04, your choice.

---

### Post by Impavidus on 2016-12-21
You have a long list of very diverse problems, which makes it hard to find the root cause. You could try **top** to find out if any program is taking all resources of your computer. The symptoms suggest it may be running out of memory, but how that's possible, I've no idea.

Try running Ubuntu from a live disk. If that works, use that to make backups. Clean install either 14.04 or 16.04. Release-upgrading a broken system doesn't fix it.

---

### Post by WB0HYQ on 2016-12-21
I agree, Ian. With a system this broken, installing an upgrade over it probably would leave behind artifacts that sould hamper the upgrade enough to make it fail.

The system is in the basement and is rarely used except when I troubleshoot my house LAN and the associated switches/routers/wireless APs. It doesn't have any really personal data on it so backup isn't necessary. Firefox has to run so I can communicate with the routers.

Bill

---

### Post by WB0HYQ on 2016-12-21
Thanks, Impavidus. As I said, this is a very old system. One that is so old, it max's out at less than a Gig of RAM. The HDD is an IDE drive and the video card is super-VGA. 14.04 ran on it just fine using the simple Unity interface with no bells & whistles. It is a utility machine - nothing more.

I have a 16.04 Ubuntu Live DVD so I can boot up with it and see what's up. I will probably end up flushing the HDD and upgrading that way.

Bill

---

### Post by vikram91 on 2016-12-21
Before upgrading consider removing some unwanted PPAs. The other day I had issues after applying updates. Finally upon some investigation I found that it was because some of the dependencies required by other packages were upgraded using Kubuntu PPA(the one I used to get Kubuntu desktop). And these packages required downgraded versions of these dependencies to work correctly. So I ended up in a broken packages state. 

So as soon as I purged the PPA using 'ppa purge"(important, highly useful command), the upgraded versions were downgraded and things that were not necesssary were removed.

So I suggest doing this on whatever PPA you have your suspicion(Just don't do it on main Ubuntu's repository):
```

sudo apt install ppa-purge
sudo ppa-purge ppa:yourppa/here
sudo apt-get install -f
sudo apt autoremove
```

After that just purge any broken applications and reinstall them:
```
sudo apt install aptitude
sudo aptitude purge yourbrokenpackagenameshere
```
 You should be fine.

---

### Post by WB0HYQ on 2016-12-21
Thanks, Vikram. I've printed your input and will get to it as soon as I can.

Bill

---

