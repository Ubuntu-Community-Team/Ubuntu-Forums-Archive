---
title: "I cant install tor"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by programmingbro on 2013-12-28
I type this  > gpg --keyserver keys.gnupg.net --recv 886DDD89  > gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -  > apt-get update  And here is problem.. When i type   > sudo apt-get install tor tor-geoipdb  I got error   > Reading package lists... Done Building dependency tree        Reading state information... Done Package tor is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package tor has no installation candidate  Please some help

---

### Post by Frogs Hair on 2013-12-28
You might want to post the installation instructions you are following. When experimenting with Tor  I have down loaded the browser bundle, extracted the package some where in the home folder. and used the start sh script to start the browser. The bundle has included Firefox the last two time Ive tried it. If you want to install from the repository wait for a member that uses it.

 [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

---

### Post by Jim_Granite on 2014-01-03
This sequence needs to be [updated with the information in this thread]("http://ubuntuforums.org/showthread.php?t=2182827"), in order to add three critically needed features:
A. Separate the TBB icon from the Firefox icon
B. Vidalia control panel should show up when the TBB is started
C. Update instructions must be supplied (not just initial installation instructions)
** As always, improvements are welcome ... **

0. These setup steps have to be repeated about a half-dozen times a year, due to constant updates in the Tor Browser Bundle.

Location of the latest Tor Browser Bundle for Linux is here:
- [https://www.torproject.org/download/download-easy.html](https://www.torproject.org/download/download-easy.html)

The latest 64-bit Linux version is here:
- [https://www.torproject.org/dist/torbrowser/linux/](https://www.torproject.org/dist/torbrowser/linux/)
The current file name (for 64-bit Linux) is:
- tor-browser-gnu-linux-x86_64-2.3.25-16-dev-en-US.tar.gz

1. **Obtain the latest 64-bit Linux Tor Browser Bundle (tbb):**
mkdir /tmp/tor
cd /tmp/tor
wget [https://www.torproject.org/dist/torb...5_en-US.tar.xz]("https://www.torproject.org/dist/torbrowser/3.5/tor-browser-linux64-3.5_en-US.tar.xz")

1. **Extract the tar.xz file:**
$ tar -xvJf tor-browser-linux64-3.5_en-US.tar.xz 

3. **Test that it works out of the box **(you just want to see that it comes up at this step):
$ ./tor-browser_en-US/start-tor-browser

** 4. Check previous installation setup**  (it is critical that instructions show how to install,and how to update the TBB, which is updated often):
$ alias tbb
=> alias tbb='ibus exit; /usr/bin/tor &'

$ which tor
=> /usr/bin/tor

$ ls -l /usr/bin/tor
=> -rwxr-xr-x 1 user1 root 65 Aug 17 05:50 tor

$ cat /usr/bin/tor
=> #!/bin/bash
=> 
=> sh /usr/bin/tor-browser/start-tor-browser

** 5. Replace the old tbb with the new tbb (save the old one just in case):**
$ DATE=$(date +"%Y%m%d")
$ sudo mv /usr/bin/tor-browser /usr/bin/tor-browser_$DATE
$ sudo cp -r ./tor-browser_en-US/ /usr/bin/tor-browser
$ cd /usr/bin
$ sudo chown -R $USER tor-browser
$ sudo chmod -R +x tor-browser

** 6. Test the newly relocated TBB:**
$ tbb
* This should bring up the Tor browser - but - unlike installing TBB  on every other operating system on the planet, two problems will remain:*
A. Unfortunately, the desktop TBB won't be separate from the Firefox icon (which is extremely inconvenient and very dangerous)
B. Unfortunately, the Vidalia control panel won't come up so you'll have no control over your results.

**NOTE**:
Unfortunately, due to Ubuntu bugs which I still don't fully understand,  Tor will be constantly confused with  Firefox (which it isn't); this  lack of distinction will eventually lead  to human mistakes, which can  easily lead to severe repercussions, even death,  if you're attempting  to maintain privacy. This is bad; very bad. But there is  nothing you  can do about it except never trust which browser comes up  when you use  TBB on Ubuntu 13.10 with Unity. Always manually  doublecheck, and, when  you make mistakes (which are inevitable since the  use model is the  opposite of every other use model in Unity), then you  must create a new  persona on the web, and perhaps move to a new country  (depending on  why you wished to be anonymous) because you have instantly  compromised  your identity, simply by the use of Ubuntu as an operating  system.

In addition, again for reasons that I really do not understand, Vidalia  on every other operating system except Ubuntu 13.10  will come up with  its panel; but it won't come up without herorics on  your part in Unity.  I had the Vidalia control panel working; but it is  no longer working  and I don't even know what I had done that finally had gotten it  working, it  was that complicated. Unfortunately, with the latest TBB  update, Vidalia no longer shows up. So, I'm back to where I was before I  had somehow (heroically) gotten it working. Again, these heroics are  not needed for any other operating system, except for Ubuntu 13.10 (that  I know of).

---

### Post by QIII on 2014-01-03
So, you go to a *third-party site *to install software that causes problems with a distro and this means that there is a bug ... in the distro?

---

