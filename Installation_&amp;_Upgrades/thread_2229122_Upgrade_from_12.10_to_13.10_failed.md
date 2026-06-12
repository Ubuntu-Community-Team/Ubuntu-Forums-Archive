---
title: "Upgrade from 12.10 to 13.10 failed"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by BarryM on 2014-06-11
I have just tried to upgrade from 12.10 to 13.10. During the upgrade process I got two critical error messages (one was inittrans something or other failed to install), and at the end the clean-up and and reboot failed. I closed by switiching off the PC using the on/off button, then restarted. The machine reboots and starts loading Ubuntu OK, but I get screensfull of error messages (too fast to read) then get to the log-in screen, after which everything seems to load Ok, if rather slowly. I can shut down OK and everything seems to work.

What do I do now? Should I simply try to upgrade to 14.04, or is there some way of fixing my 13.10 that I need to do first? Or, as a last resort, should I do a clean install of 14.04? I did take the precaution of backing up all of my data before upgrading, but I am not sure how to back up things like my firefox password repository and Thunderbird e-mail archive.

Any suggestions?

---

### Post by gifford on 2014-06-11
Sorry about your difficulties. Ubuntu 13.10 reaches end of life cycle in July so my recommendation would be a clean install of 14.04.
As for the firefox passwords, I do not have the answer as Chrome is the browser I use. For Thunderbird, there is much on the internet 
for how to back it up. I do the "dirty" and not recommended procedure of taking the default folder found in home/.thunderbird and use
it in the new installation. It includes all identities, emails, and accounts. It has worked without a problem for me.

---

### Post by BarryM on 2014-06-11
Really, I can't think why I didn't think of looking online for the Firefox backup problem. A quick google of Firefox Password Backup took me to [https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles) with step by step instructions for how to back up your entire profile (which I have now done).

Do you think upgrading to 14.04 is worth a try before going down the clean install route?

---

### Post by monkeybrain20122 on 2014-06-11
Clean install always. You already have a broken upgrade and upgrading from a broken upgrade would only get more broken. I don't understand why you want to avoid clean install, it takes about 15 minutes and upgrade takes hours which also has a high probability of failure. 

You should also make a separate /home, that way a fresh install would just write over the root partition and leaves all your data and settings intact.

As for Firefox back up, all you need is to copy the .mozilla folder ( a hidden folder in your home, press ctrl+h or choose "show hidden files" in file manager menu to show it) and then put in your new home directory after you install 14.04 to overwrite the new one (close Firefox when you do that) But if you have a separate /home then Firefox settings would be automatically saved.

---

### Post by LastDino on 2014-06-11
Well, fresh install is way to go for smoother OS life. Anyhow, 14.0.1 isn't out yet to consider upgrade a viable option tbh.

---

### Post by BarryM on 2014-06-11
Thanks for the advice, what was worrying me was the loss of data having to restore it all. I will, of course have to reinstall all of my additional programs, I suppose.

When you say make a separate /home, do you mean in a different partition, or just copy everythig to my backup (external) drive and restore it when the 14.04 is up and running. Sorry, I know I am sounding a bit thick, but I am not that well versed in tinkering with file systems. I am basically just the sort of chap who wants a computer that I can use for mainly office type functions and leave the intricacies of how it us set up to others. And, frankly, at 67 I 'm a bit old to start learning new tricks!

Also I have got to replace my Windows XP installation with Windows 7 (apologies for using rude words like Windows in this forum), on a separate hard drive (hda, Ubuntu is on hdb). I imagine I should do that first as I suspect it will mess up GRUB and I'll have to get that back if I am ever to run a decent operating system again, which I presume a fresh installation of 14.04 will sort out for me?

By the way, for file copying to backup drives and such like I use a useful little program called Beyond Compare (Scooter Software), which displays hidden files and folders by default. Makes life a lot easier. The Linux version will happily allow you to copy files to and from a Windows drive.

---

### Post by LastDino on 2014-06-11
He means create a separate /home. If you've enough disk space, you should allocate something like 50-100GB. Your ''/'' can be of 20-24GB.

I don't think any Windows ''hate group'' are here so fire away all the windows words you can think of :P
And yes, generally installing windows first is the good option. Of course, you can achieve things other way around too, especially since you've 2 drives to work with. If I was you, I would simply remove one while doing installing on other.

Most mainstream OS are decent, some may give you some hiccups but that has more to do with hardware compatibility and rest is up to user taste. Feel free to try.

---

### Post by kansasnoob on 2014-06-12
Upgrading from 12.10 to 13.10 should not have been possible unless you manually edited software sources. Just for fun post the output of:

```
lsb_release -a
```

---

### Post by BarryM on 2014-06-12
Yes, I must admit I was a little surprised when the updater gave me the option to upgrade direct from 12.10 to 13.10, but I just assumed it would be OK.

the output from lsb_release -a is:

LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

 I hope that means something to you, because I don't know what it means.

Thanks to everyone who's commenting!

---

### Post by BarryM on 2014-06-29
I see it's 2 weeks since my last post, and I have finally got my /home/ directory moved to its own partition and working happily. It was not without event, since I created a 50GiB partition and it wasn't big enough so I had to increase it to 100GiB and repeat the transfer process.

By the way, I found a helpful step by step guide to partitioning and migtrating my /home directory to its own partition at [http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/).

One last question, do I need to do anything special when I install 14.04, like invoking the custom installation option, or will the automatic installation process recognise my /home partition and leave it alone?

---

### Post by oldfred on 2014-06-29
You do have to use the Something Else option. 
You select your current / (root) and choose it as the new / partition and format as ext4. That will overwrite everything. You can choose to not format it but it still will overwrite everything that has changed. So if you modified system with custom grub menus or fixed Ethernet addresses you may want to back those up sperately.
You then select your current /home partition to mount as /home, but DO NOT select format or any changes so it just is reused with all your user settings and files for programs.

If you have installed lots of apps you may want to export a list of apps and reinstall those. The data for the apps are all in /home and will be there, but the app will not be, unless one of the defualt ones normally installed.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by BarryM on 2014-07-01
Well, after a hectic morning getting Windows 7 installed on my sda drive, I now have Ubuntu 14.04 up and working on my sdb drive, and all seems to be going fine. I must say that, having created the /home partition, it was a lot easier than the windows install process! The blank screens on initial start-up after installation are a bit disconcerting, but patience pays off.

The only thing that bothers me is that my /home directory has something like 70GiB on it, which strikes me as being a bit excessive. I seem to have a vast number of hidden text files .goutputstream-(6 characters) with a size of 0bytes and dating back over several years (most recent 10th June 2014 and oldest 12 Nov 2012). I wonder if these should have been cleaned up somewhere along the line?

I think I can safely flag this thread as solved now. Thanks to everyone who helped.

---

