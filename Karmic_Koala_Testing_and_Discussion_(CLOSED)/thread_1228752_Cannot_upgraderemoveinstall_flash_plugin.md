---
title: "Cannot upgrade/remove/install flash plugin"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tim1 on 2009-08-01
Something with the last update went wrong and now I cannot upgrade anymore, and the old flash plugin isn't actually installed, just the package.

>  sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adobe-flashplugin
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  adobe-flashplugin
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/4018kB of archives.
After this operation, 147kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 137950 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-2jaunty1 (using .../adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anybody here know how to fix this?

---

### Post by jfernyhough on 2009-08-01
Try a

$ sudo aptitude purge adobe-flashplugin
$ sudo aptitude install adobe-flashplugin

---

### Post by kostkon on 2009-08-01
Try also a
```
sudo apt-get clean
```
to clean the cache and force it to re-download the updated flash package.

---

### Post by mrsurb on 2009-08-01
I had a similar problem - it seems that the adobe-flashplugin installer gets into a halfway state where it can't be installed or uninstalled - like the couch halfway up the stairs in Douglas Adams' novel Dirk Gently's Holistic Detective Agency.

Anyway, I solved it my following the instructions here: [http://ubuntuforums.org/showpost.php?p=7630139&postcount=35](http://ubuntuforums.org/showpost.php?p=7630139&postcount=35) - though I also had to "sudo aptitude download" a few other packages that dpkg wanted.

---

### Post by xebian on 2009-08-01
> **tim1 said:**
> Something with the last update went wrong and now I cannot upgrade anymore, and the old flash plugin isn't actually installed, just the package.

```
Preparing to replace adobe-flashplugin 10.0.22.87-2jaunty1 (using .../adobe-flashplugin_10.0.32.18-1jaunty1_i386.deb) ...

```


Does anybody here know how to fix this?

You should avoid using non-official packages when you can use the one from the repo - flashplugin-nonfree.  
Remove and purge such offending package and install the official jaunty package - flashplugin-nonfree.

---

### Post by W4l0ck on 2009-08-01
take off the -f flag, and do a apt-get clean

---

### Post by kostkon on 2009-08-01
> **xebian said:**
> You should avoid using non-official packages when you can use the one from the repo - flashplugin-nonfree.  
Remove and purge such offending package and install the official jaunty package - flashplugin-nonfree.
The *adobe-flashplugin* *is* an official package, offered by the ubuntu *Partner* repo. Very useful especially for Hardy users, since the *flashplugin-nonfree* in the Hardy repos is Flash 9.

---

### Post by dinxter on 2009-08-01
there'll be a file called something like
/var/lib/dpkg/info/adobe-flashplugin.prerm
try editing the line,
VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"
and removing iceape. then try upgrading again

---

### Post by mrsurb on 2009-08-01
dinxter - yes, that will work for this upgrade, but the next time abode-flashplugin is upgraded it will look for the same files and fail. The method that I recommended above (forcing installation of mozilla-plugin-flash over the top) will generate the missing alternatives files.

---

### Post by YukaToshi on 2009-08-01
Yeah, I had this problem too. I solved it with;

```
sudo aptitude -f purge adobe-flashplugin

**OR**

sudo aptitude -f purge flashplugin-installer
```

---

### Post by dinxter on 2009-08-01
> **mrsurb said:**
> dinxter - yes, that will work for this upgrade, but the next time abode-flashplugin is upgraded it will look for the same files and fail.

postrm script fails because of a broken dependencies link for icecape, removing that check from the postrm allows the old package and symlinks to be removed before upgrading to the new version. the new version then installs all the relevant symlinks for /etc/alternatives, including iceape. it shouldnt fail once fixed ( in theory :) ). possibly a simpler way would just be to try and fix the broken link pre update

```
update-alternatives --install "/usr/lib/iceape/plugins/flashplugin-alternative.so" "iceape-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so 50
```

---

### Post by paul_in_london on 2009-08-01
When I got the "update-alternatives"/dpkg errors trying to upgrade to v10.0.32.18-1 of adobe-flashplugin (and before I saw this thread), I did this:

```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm

```

and then I was able to install the new deb. It pulled in a couple of dependencies as well.

See the bottom of this page:

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/371890](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/371890)

This was ok for firefox and opera. To get chromium to use the new version I did:

```
sudo rm /usr/lib/chromium-browser/plugins/flashplugin-alternative.so
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/chromium-browser/plugins/
```

---

### Post by xebian on 2009-08-01
> **kostkon said:**
> The *adobe-flashplugin* *is* an official package, offered by the ubuntu *Partner* repo. Very useful especially for Hardy users, since the *flashplugin-nonfree* in the Hardy repos is Flash 9.

Official partner package != official Ubuntu package.

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. [COLOR="Red"]This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.[/COLOR]
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner


```

---

### Post by xebian on 2009-08-01
> **paul_in_london said:**
> When I got the "update-alternatives"/dpkg errors trying to upgrade to v10.0.32.18-1 of adobe-flashplugin (and before I saw this thread), I did this:

```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm

```

and then I was able to install the new deb. It pulled in a couple of dependencies as well.

See the bottom of this page:

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/371890](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/371890)

This was ok for firefox and opera. To get chromium to use the new version I did:

```
sudo rm /usr/lib/chromium-browser/plugins/flashplugin-alternative.so
sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/chromium-browser/plugins/
```

This won't work for 64-bit users because the chromium-browser uses the 32-bit flash.

---

### Post by taavikko on 2009-08-01
> **xebian said:**
> Official partner package != official Ubuntu package.



It's not official in the sense that devs cannot easily fix the problems.
The packages are from the partners.

---

### Post by dinxter on 2009-08-01
as far as i can see the problem is,
- postinst update-alternatives the links
- something else removes links it shouldnt do
- postrm fails because the links should be there

but i see no reason why it shouldnt continue without any unexpected consequences, if the alternative doesnt exist and we're trying to remove it then ignoring that isnt a problem. instead of,
```

for p in $VARIANTS; do 
            update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
done
```

check that the link we're about to try and remove exists, if not then we dont need to do anything as thats what we want anyway. something like, 
```
for p in $VARIANTS; do 
            if [ -e /etc/alternatives/"$p-flashplugin" ]; then
            update-alternatives --remove "$p-flashplugin" /usr/lib/flashplugin-installer/libflashplayer.so;
            fi
        done
```

though in practice hard coding the alternatives directory might not be the best way, just an example

---

### Post by dinxter on 2009-08-01
a generally better approach might just be to have update-alternatives simply return 0 if the requested operation fails, but in a way that leaves the state as expected, as in the case,
- request update-alternatives --remove
- alternative doesn't exist so we return an error
but although the operation isnt successful the outcome is as we expect so it isnt a problem. 
or have an error code returned that signifies that the operation has failed but in a way that we can safely ignore. at the moment i can only see codes 0,1 and 2 which dont seem to cover this sort of case

---

### Post by Starks on 2009-08-01
Install this version then try upgrading.

[http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_i386.deb](http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_i386.deb)

---

### Post by DougieFresh4U on 2009-08-01
Using 64 bit, I am getting this:
```
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```
But, flash is working using Firefox as youtube vids are working ok. Can not get flash to work using 'Swiftfox'.

---

### Post by Starks on 2009-08-01
Dougie, try this before upgrading:

Jaunty 64bit: [http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_amd64.deb](http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_amd64.deb)

---

### Post by DougieFresh4U on 2009-08-01
> **Starks said:**
> Dougie, try this before upgrading:

Jaunty 64bit: [http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_amd64.deb](http://lug.mtu.edu/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.22.87ubuntu2_amd64.deb)

Gave it a try and this is what I got. Should I remove any thing, if so how/
Thanks

---

### Post by Starks on 2009-08-02
Purge adobe-flashplugin and flashplugin-installer.

---

### Post by LanJan on 2009-10-14
I too have this problem.
running XUBUNTU, with the new beta upgrade.

What is worse, is that this problem is preventing 207 other upgrades from executing.

---

### Post by dinxter on 2009-10-14
whats the error you get when you run from the command line?

---

