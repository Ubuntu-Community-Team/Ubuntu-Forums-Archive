---
title: "Keeping Firefox updated in Ubuntu"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by andrew89 on 2010-02-05
Hello,

I recently installed Ubuntu 9.10 (64-bit), and would like to update Firefox to version 3.6.  It is currently at version 3.5.7.

I did some searching on the internet, and it seems that Firefox's "check for updates" option is disabled because Synaptic handles the updating process.  However, Synaptic doesn't show any updates for Firefox, because it does not have "Ubuntu branding", whatever that means.

I also found some answers to my question along the lines of "add the Mozilla daily build repo, and update Firefox that way".  But I don't want the nightly builds, I would like Firefox to automatically update to the latest stable, publically-released version, as is the case with standard Windows installations.

If I were to uninstall Firefox via Synaptic, and install it via the installation package available on the official Firefox site (which is v3.6), will I retain all of my customisations - plugins, bookmarks, cookies, etc?  If so, will I be able to update Firefox in the future using the "Check for updates" feature, and will it update to versions beyond 3.6.x?  I saw some solutions that involved adding a different repo, but would only allow automatic updates on the 3.6.x line.

Thanks for the help - I've already gotten loads of information by just reading the forum, and any help on this matter would be great! :)

---

### Post by tommcd on 2010-02-05
Here is the simple way to do it:
Download the FF 3.6 .tar.bz file to your /home directory.

Open a terminal (applications > accessories > terminal) and run:
```
tar -xvjf fire
```
and hit the TAB key. It should autocomplete the name of the FF 3.6 you downloaded. Then hit enter. If it does not autocomplete the name of the FF 3.6.tar.bz, then make sure the FF3.6 is in your /home directory.

Once you have untarred the FF 3.6 tarball, cd (change directory) into the newly created firefox directory in your /home directory:
```
cd firefox/
```

Then cd into the firefox/plugins directory:
```
cd plugins/
```

Then run:
```
ln -s /usr/lib/mozilla/plugins/* .
```
(Note the period "." at the end of that command)
This will link to all your FF plugins in /usr/lib/mozilla/plugins.

Then cd up to the firefox directory:
```
cd ..
```
Then run:
```
./firefox &
```
You can just copy & paste these commands right off this page into your terminal if you want.
You should now be running FF 3.6. You can create a shortcut on your desktop by right-clicking on the firefox icon in the firefox directory and choosing to create a desktop shortcut for it.

This will not affect the FF you have installed from the Ubuntu repos at all. That is the advantage of this.
Note: this will only work for 32bit Ubuntu. It may not work for 64bit Ubuntu.

And welcome to the Ubuntu forums!!

EDIT: Sorry, I just noticed that your post said you are running 64bit Ubuntu. I think 64bit Ubuntu includes the 32bit compatibility libs, so this may work. You may need to change the path to the mozilla plugins to something like: /usr/lib64/mozilla/plugins.

---

### Post by andrew89 on 2010-02-05
Thanks for the quick and informative reply!

There's still a couple of issues:
1) I would like Firefox 3.6 to be the default browser on my system, and for it to automatically update to, for example, version 3.7 whenever that becomes available.  Shouldn't there be some Mozilla-based repository that I can install from, that doesn't include beta / nightly builds?
2) Whenever I run the ./firefox & command in the terminal, I get errors of the following form.

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]

I imagine that this is a 64-bit problem.  However, this problem still persists whenever I miss out the plugins step.

I use the Weave Firefox plugin, so I should be able to quickly restore my settings if I uninstall the old version (3.5.7) first.  So, I can uninstall that and then install 3.6 if that helps.

I'm a bit confused as to why upgrading to the most recent release isn't simple - surely this should be what most users will want?

Thanks for all the help so far!

---

### Post by Silvertones on 2010-02-05
This is very easy

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by andrew89 on 2010-02-05
People in the ubuntuzilla support forum say that it doesn't work with 64-bit Ubuntu, only with 32-bit.  They suggest using the daily builds repo. :S

---

### Post by tommcd on 2010-02-06
> **andrew89 said:**
> 
I'm a bit confused as to why upgrading to the most recent release isn't simple - surely this should be what most users will want?

It is up to the Ubuntu developers to add FF 3.6 to the Karmic repos. Until that happens you will need to install FF directly from mozilla.com, or use 3rd party repos.
Part of the problem is that the FF in Ubuntu is not the same as the FF from mozilla.com. As with everything else in Ubuntu, the FF that you get is the Ubuntu-ized version of FF. Producing the Ubuntu-ized FF takes longer than just using FF straight from mozilla (as Slackware does, which is why Slackware stable has updated to 3.6, and Ubuntu has not.)
The proceedure I outlined works on 32bit Ubutnu. I run FF 3.6 that way on my 32bit Ubuntu.
A quick search for Ubuntu ppa repos that include FF 3.6 found this tutorial from Ubuntu-Geek:
[http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa.html)
He does not mention anything about 32 bit or 64 bit Ubuntu in the tutorial. I can not verify if this works on 64 bit Ubuntu. That ppa repo does include sections for 32bit and 64bit though. So I would think it should work.

---

### Post by andrew89 on 2010-02-07
Thank you, everyone, for all your help - ultimately it was [tommcd]("http://ubuntuforums.org/member.php?u=34402") who was able to give me the repo I needed.  Will this repo give me automatic updates when Firefox 3.7 is released?

Also, as a curiosity, what customizations is Ubuntu making to the Firefox package?

---

### Post by tommcd on 2010-02-07
> **andrew89 said:**
> Thank you, everyone, for all your help - ultimately it was [tommcd]("http://ubuntuforums.org/member.php?u=34402") who was able to give me the repo I needed.  Will this repo give me automatic updates when Firefox 3.7 is released?
I'm not sure, but I would think it probably would when you get your regular Ubuntu updates.
> **andrew89 said:**
> 
Also, as a curiosity, what customizations is Ubuntu making to the Firefox package?
From what I can find, it seems to integrate FF with the rest of the system (which is why I referred to it as Ubuntu-ized), and some other things. If you click: Tools > Addons > Extensions, in the FF menu you can see it there as "Ubuntu Firefox Modifications". It can be disabled apparently. 
Here is a thread about it:
[http://ubuntuforums.org/showthread.php?t=826536](http://ubuntuforums.org/showthread.php?t=826536)

---

### Post by snowpine on 2010-02-07
Hi Andrew, the simplest and easiest way is to wait for the Ubuntu developers (you trust them, right?) to test the latest Firefox and add it to the Ubuntu repositories. This will most likely happen in April with the release of 10.04 Lucid Lynx. 99.99% of websites still support Firefox 3.5.7. ;)

---

