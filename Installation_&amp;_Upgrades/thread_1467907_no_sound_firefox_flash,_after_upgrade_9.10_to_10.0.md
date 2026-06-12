---
title: "no sound firefox flash, after upgrade 9.10 to 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by flecktor on 2010-05-01
upgraded ubuntu 9.10 to ubuntu 10.04 

sound works good with amarok and on startup.

no sound on firefox flash. 

what to do?

---

### Post by flecktor on 2010-05-01
tried this :
[http://support.mozilla.com/en-US/kb/Flash-based+videos+and+sound+do+not+play+correctly](http://support.mozilla.com/en-US/kb/Flash-based+videos+and+sound+do+not+play+correctly)
just upgraded the flash player 
from adobe.(the apt for +9.04)

---

### Post by E1ephant on 2010-05-01
BUMP...Same problem:confused:
not amd64

---

### Post by F W Adams on 2010-05-01
I was previously on 8.04 and lost sound on upgrading to 10.4

I followed post #2 and selected flashplayer .deb for 8.04. It did not solve the problem immediately but on exiting firefox and then restarting it the problem was solved.

---

### Post by jubalj on 2010-05-04
I've got the same problem. No sound in flash video under firefox but video under chrome plays fine!

I've tried following instructions in #2, but i get the following;

> $ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.


Trying to install the 9.04 flash from adobe site I get the following error:
> Unknown channel 'lucid-partner'

The channel 'lucid-partner' is not known

If I try and install the deb for 8.10, in gdebi i get:
> STATUS: Error: Conflicts with the installed package 'flashplugin-installer'

Any suggestions on how to resolve this?

cheers
Jubal

---

### Post by giosoftware on 2010-05-06
Hi all.
I have the same problem of [jubalj]("http://ubuntuforums.org/member.php?u=318643") after upgrade to ubuntu 10.04.
Sound work with chrome but doesn't work in firefox.
Now I have the flash plug in version 9,0,31,0 installed

Thanks to all

---

### Post by giosoftware on 2010-05-06
Hi again
I fix the problem installing the plug in from the adobe page choosing the option:
APT for Ubuntu 9.04+

bye and good luck :-)

---

### Post by confused_user on 2010-05-06
> **giosoftware said:**
> Hi again
I fix the problem installing the plug in from the adobe page choosing the option:
APT for Ubuntu 9.04+

bye and good luck :-)

same here, installing apt for ubuntu 9.04+ and restart the browser works

---

### Post by ian.xerl on 2010-05-07
Me, too, I installed Kubuntu 10.04 (amd 64 architecture) and the flash videos don't have any sound. Neither in Chrome or Konquerer. Sound works in other programs.

I tried to deinstall and reinstall the flash plugin from the repositories, but it doesn't help.

I went to adobe's website and tried to install the latest plugin via "APT for Ubuntu 9.04+" but I get the error message "unknown channel lucid-partner"

When I try to install ".deb for Ubuntu 8.04" the error message is that I have the wrong architecture (64 instead of 32).

Maybe I should download the tar.gz file, but I don't know how to install that...

Any suggestions? Jan

---

### Post by ian.xerl on 2010-05-08
I found the solution for my problem here:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/543035](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/543035)

It's just a matter of sound settings: PCM mixer slider was set to 0%. Turn it up and flash video will have sound.

(I never thought this could be the issue, since sound worked fine in all other applications... I lost 2 hours trying to install the latest/best flash plugin... all for nothing... grrrrrrr)

---

### Post by arak on 2010-05-08
Here is how I solve the problem.  First I found that I had two Shockwave's running.  I deleted an obsolete one (Ver9) and it was fixed. 

Here is how I did it.  In Firefox,type about:plugins.

If you find you have two "shockwaves" you need to delete the old one. Go into about:config and in the item "plugins" put true next to the one that says show full path.  Now go into About:plugins and you will see the path of the obsolete plugin.  Use sudo nautilus to rename the old plugin.  It is important that you rename the "so" to something else.

Reboot and see if it works as mine did.

Let me know if this fixes your problem.

---

### Post by mosteo on 2010-05-12
I guess there are several problems with the same symptoms. In my case, installing adobe-flashplugin (which got rid of flashplugin-nonfree) fixed it.

---

### Post by brunotc on 2010-05-15
What worked for me was removing the ~/.pulse directory, which apparently contained stale pulseaudio settings. So, in short:

[FONT=Courier New][SIZE=3]rm -rf ~/.pulse[/SIZE][/FONT]

---

### Post by jubalj on 2010-05-16
> 
If I try and install the deb for 8.10, in gdebi i get:

STATUS: Error: Conflicts with the installed package 'flashplugin-installer' 

I was able to resolve this by "apt-get remove flashplugin-installer" which also uninstalls the non-free flash. Then it installed fine from the adobe site, and sound now works.

Although I suspect mosteo's solution of installing adobe-flashplugin might be a better way to go. Havent given it a try yet.

---

### Post by tlfcbb on 2010-05-24
> **arak said:**
> Here is how I solve the problem.  First I found that I had two Shockwave's running.  I deleted an obsolete one (Ver9) and it was fixed. 

Here is how I did it.  In Firefox,type about:plugins.

If you find you have two "shockwaves" you need to delete the old one. Go into about:config and in the item "plugins" put true next to the one that says show full path.  Now go into About:plugins and you will see the path of the obsolete plugin.  Use sudo nautilus to rename the old plugin.  It is important that you rename the "so" to something else.

Reboot and see if it works as mine did.

Let me know if this fixes your problem.
After trying everything this worked for me.  This is why the Ubuntu forums are the best - someone has come up with the solution.  Great help as always.  Thanks guys.

---

### Post by picrard on 2010-10-03
> **ian.xerl said:**
> I found the solution for my problem here:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/543035](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/543035)

[U][SIZE=4][COLOR=Red][B]It's just a matter of sound settings: PCM mixer slider was set to 0%. Turn it up and flash video will have sound.
[/B][/COLOR][/SIZE][/U] 
(I never thought this could be the issue, since sound worked fine in all other applications... I lost 2 hours trying to install the latest/best flash plugin... all for nothing... grrrrrrr)

Thanks a lot...this helped me too....
what of the stupid mistakes :mad:

it has cost a longer duration to solve this problem... for me ... :mad::mad::mad:

thank you:)

---

### Post by vyk on 2011-04-07
Info on [this site]("http://www.willmcgugan.com/blog/tech/2010/5/2/no-audio-in-flash-on-ubuntu-1004/") helped me fix the problem.

In short: if on typing the url 'about: plugins'(no space between ':' and 'p') you notice two Shockwave Flash plugins find them and delete one.
   To find the plugins you could use - sudo find / -name libflashplayer.so

I deleted the one in the '/usr/lib/firefox-addons/plugins' folder and all was hunky dory after.

---

