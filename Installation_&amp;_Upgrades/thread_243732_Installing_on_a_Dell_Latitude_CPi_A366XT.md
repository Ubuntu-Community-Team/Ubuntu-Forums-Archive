---
title: "Installing on a Dell Latitude CPi A366XT"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by Daneel24 on 2006-08-25
Hi... I have this old Dell Latitude CPi A366XT laptop, and I wanted to learn a bit more about Linux so I'm trying to install Ubuntu on it. But it seems I don't even get to the first step in the installation. The CD boots nicely, I click "Start or install Ubuntu", it loads a lot of stuff and everything seems ok. Eventually I get a mouse pointer and an Ubuntu logo, then it goes all black. I can still hear it working but nothing happens after that.

The thing I downloaded was "ubuntu-6.06.1-desktop-i386.iso". I also chose the option to check the CD for defects, that worked fine and there were no problems.

On the compatibility page it said that Dell Cpx was compatible with one of the older versions. Maybe this one isn't, I don't know... Could someone help me with this and tell me what my options are? Please understand that I'm a complete newbie :)

---

### Post by JoeJon117 on 2006-08-25
Hi, I was actually pretty surprised to see this post as I just installed Ubuntu on the EXACT same machine last week, the Dell CPi. I also experienced the problem you described, and I have determined that the Dapper kernel just doesn't want to co-operate with the CPi  chipset. Thankfully, there is a way to correct this problem. What you need to do is install Ubuntu 5.10 "Breezy Badger" and upgrade to Dapper Drake. The various mirrors for Breezy can be found about halfway down this page:

[http://www.ubuntu.com/download/releasenotes/510](http://www.ubuntu.com/download/releasenotes/510)

After intalling Breezy, you will notice a few things, one being that the resolution of Ubuntu does not perfectly fit the screen. You may  need to resize some windows from time to time. Unfortunatly, I have been unable to find a solution to this problem, even after uprading to Dapper Drake. The second thing you'll notice is that Ubuntu does not recognize the system sound card. A possible fix may be found on this page, but I have not had the time to try it, so it may or may not work:

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

You'll also notice that Ubuntu runs a little slugglishly on the CPi. This is not surprising as this it is an 8 year old machine. Don't worry though, because it still runs fast enough to be useable. I don't recommend running Xubuntu in an attepmt to correct this problem, because it doesn't make a significant difference and the normal Ubuntu desktop is much more useful. 

Now that Breezy is installed, you'll want to go to the Update option under the System menu at the top of the screen. Here you can update to Dapper Drake and everything will work perfectly fine, other than the previously mentioned sound and display problems. 

Good Luck and I hope you enjoy working with Ubuntu!

---

### Post by Daneel24 on 2006-08-25
Ok, thanks a lot! Funny about the sound though, because I could clearly hear some sound playing when the Ubuntu logo appeared, just before it hanged... oh well, I'll try it and see what happens :)

---

### Post by Daneel24 on 2006-08-26
Ok, installation of 5.10 worked without any problems. However when I try to start it up, it goes something like this:

> ...
Mounting local filesystems...   ok
Setting up networking...        ok
Starting hotplug subsystem...   

And then it just hangs, no disk activity :( there seems to be a lot of threads regarding this particular problem already, so I'll see if I can find some solution. You did not have this problem?

---

### Post by Daneel24 on 2006-08-26
Pressed Ctrl-C immediately the Hotplug part came up (didn't work if I did it a few seconds after, it was just unresponsive) so I could finish the installation. Could also upgrade now without any problem, except that it took about four hours not counting download time :roll:  The sound and network works just fine and I have no issues with resolution.

---

