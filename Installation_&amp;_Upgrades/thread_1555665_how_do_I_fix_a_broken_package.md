---
title: "how do I fix a broken package?"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by theovn on 2010-08-18
Hello,

When I try to update Ubuntu 10.4 I get a broken link error.
In the Synaptic Package Manager I found that the flashplugin-nonfree package caused the problem.

"sudo apt-get -f install" gives:
	dpkg: error processing flashplugin-nonfree (--remove):
	Package is in a very bad inconsistent state - you should
	reinstall it before attempting a removal.

How should I install this, if "apt-get -f install" does not work?

Thank you for helping,
Theo van Nee

---

### Post by Herman on 2010-08-18
You should reinstall it before attempting a removal?
That doesn't make sense to me.
What if you remove it before attempting to re-install it? 

Here's a link that might help, [What to do when apt-get fails - Linux.com]("http://www.linux.com/archive/feature/48910")

Most times when I have broken packages I try a series of different commands, especially some of the commands suggested in the above link, and sooner or later the problem is resolved, but it's often unclear which of the commands or combinations of command actually were the useful ones that worked.

If nothing works, sometimes I just wait a few days and try again, hoping the problem has been solved by somebody else.

Sometimes I get errors telling me the .deb file in /var/cache/apt/archives is corrupt and there's a short read from it or something like that. Completely removing it and re-installing with a new one freshly downloaded from the internet sometimes helps. 
I'm not sure, but possibly some commands like the ones below might help,
```
sudo dpkg --purge flashplugin-nonfree
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install flashplugin-nonfree
```

---

### Post by theovn on 2010-08-21
Thank you for your response, Herman.
I have tried your suggested code with the following results:
Command:
	sudo dpkg --purge flashplugin-nonfree
Result:
	Package in very bad inconsistent state &#8211; you should reinstall it before attempting a removal.

This indeed is quite weird as you mentioned already in your reply!

Command:
	sudo apt-get update
Result:
Seems to work allright
Command:
	sudo apt-get upgrade
Result:
	Reading state information... Done
	You might want to run 'apt-get -f install
Command:
	sudo apt-get install flashplugin-nonfree
Result:
	flashplugin-nonfree has unmet dependencies. Try 'apt-get -f install'
Command:
	sudo apt-get -f install
Result:
	Package is in a very bad inconsistent state &#8211; you should reinstall it before attempting a 	removal.

So unfortunately I am not getting any further.	

I have also tried up to point 5 of the suggestions in the link you mentioned, which also didn't work.
I am a bit reluctant to go any further, as I don't know much about it.

Next week I am going on a month's holiday, so you won't get any replies from me than.
After my holidays I will dive into it a bit further (or reinstall Ubunutu 10.4, if I don't see any other posibilities).
I will also have a further look at your website, which seems interesting to me.
For now: thanks for your help so far.

---

### Post by jmfal on 2010-08-21
Hi Theovon,

I know your frustrated, relax, try this

 ```
   sudo apt-get install --fix-missing
```

if this doesn`t work put 2 spaces between install and  --

no success try

  ```
   sudo dpkg --configure -a
```

if you get some kind of response from the commands and still hav e problems try to do a complete reinstallation then uninstall it as some dependencies might hve been met so that you can 
good luck

---

### Post by Herman on 2010-08-21
:D   Hey, I just found some information on this problem that I wasn't aware of earlier,
 see this link, [flash-plugin nonfree]("http://ubuntuforums.org/showthread.php?t=1475441&page=2&highlight=flashplugin+nonfree") - Ubuntu Web Forums, and read post #11 there.

That refers to another thread, here, [[all variants] Known Lucid Lynx issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1469475") , where we are advised to do,
```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```Thanks for reminding me about this. My mother just finished upgrading from Karmic to Lucid and she phoned me a few days ago with the same problem, so now I can tell her how to fix hers too. Hopefully it will be the right solution this time.

Regards, Herman :)

---

### Post by theovn on 2010-08-26
Thank you for your replies jmfal and Herman,

The first reply did not solve my problem, but Herman's reply did!
Thanks very much for diving into my problem and helping me out.

Regards,
Theo van Nee

---

