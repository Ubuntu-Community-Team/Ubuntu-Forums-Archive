---
title: "just upgraded to 22.04 - no firefox and cannot install"
date: 2022-08-16
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-08-16
I just upgraded to 22.04 and everything seemed dandy.  Then I found that firefox was no longer there.  I tried to install it but got errors.  I think it has something to do with snap but am not sure.  I have tried to dodge snap but, I guess, its the thing now. 

Anyway, appreciate any help on this one.  I tried to install it with apt and that failed due to necessary stuff that wasn't there.  

Thank you.................

---

### Post by &amp;KyT$0P# on 2022-08-16
Are you able to use the [official Mozilla build]("https://www.mozilla.org/firefox/all/#product-desktop-release") of Firefox for Linux 64-bit?

---

### Post by jgw on 2022-08-17
thank you for the reply!

I wasn't clear with this.  I just did a search for "firefox" on home.  Here is a search for "firefox" result:

```
/home/greg/.mozilla/firefox
/home/greg/.cache/mozilla/firefox
/home/greg/.config/autostart/firefox.desktop
/home/greg/Documents/hgjkbl9g.default-release/SiteSecurityServiceState.txt
/home/greg/.mozilla/firefox/ym6yt3gk.default-release/extensions/private-relay@firefox.com.xpi
/home/greg/.mozilla/firefox/ym6yt3gk.default-release/extensions/sabconnectplusplus-firefox@bhack.net.xpi
/home/greg/.mozilla/firefox/ym6yt3gk.default-release/storage/default/https+++accounts.firefox.com]
```

I got this from files and it was about 3 times bigger.  I copied it and got this.  Anyway, I have a LOT of firefox stuff on this computer.   I am going to run sudo apt install firefox and try and copy the results here. 

```
greg@greg-hp-8200:~$ sudo apt install firefox
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 firefox : PreDepends: snapd but it is not installable
E: Unable to correct problems, you have held broken packages.
greg@greg-hp-8200:~$ 

```

I also ran synaptic to fix packages.  It said it did, it didn't.  I suspect I should remove ALL the firefox stuff I can find and try again?

---

### Post by deadflowr on 2022-08-17
Have you blacklisted or marked as hold (or any other method that would prevent installing) snapd?

---

### Post by &amp;KyT$0P# on 2022-08-17
> **jgw said:**
> I wasn't clear with this.

You were clear enough.  If you want to keep Firefox and avoid snapd, the simplest way is to get Firefox directly from Mozilla, where it is distributed as a tar.bz2 that you can just extract and run.  It is much more difficult to install Firefox through apt (the package you attempted to install is not Firefox, but an installer for the snap package of Firefox).

---

### Post by SeijiSensei on 2022-08-17
Even easier is to add the Mozilla "PPA" to your sources list. Both it, and Thunderbird if you use it, will be automatically upgraded to the newest release version when you upgrade your system.

[https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)

---

### Post by &amp;KyT$0P# on 2022-08-17
> **SeijiSensei said:**
> add the Mozilla "PPA" to your sources list.

That's exactly what I had in mind when I wrote "It is much more difficult to install Firefox through apt": as noted in your link, that method requires advanced user knowledge of apt pinning, which is likely beyond the knowledge level of someone who needs to ask for help what to do with the error in post #3.

---

### Post by grahammechanical on 2022-08-17
I would like to add some information. 

If we upgrade to 22.04 from 20.04 or 21.10 then the deb packaged version of Firefox will be removed and the snap packaged version of Firefox installed in its place. It seems that Ubuntu 22.04 forwards we will always get the snap version of Firefox whether we install through APT or Ubuntu Software.

As mentioned above there are other ways to get the deb version of Firefox and both versions can co-exist. Snap packages need the snapd package. People who do not like snap packages usually remove the snapd package.

Regards

---

### Post by jgw on 2022-08-17
Thanks for all the replies!

Here is what I did.  First I saved all my old firefox stuff.  Then I used the ppa thing to install firefox (and it worked!)  Then I took my old firefox file, added it to the neew firefox and then added its name on the two files in firefox (installs.ini and profiles.ini and turned it on and everything was dandy!

Thanks again for all the help!

---

