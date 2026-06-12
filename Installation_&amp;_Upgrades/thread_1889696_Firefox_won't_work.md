---
title: "Firefox won't work?"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by Ruskin1 on 2011-12-01
I want to say before anything, I am new to Linux, Ubuntu, and this forum. I just installed Ubuntu 11.10 on my old Vista computer and Love it so far, but need some help. I searched for a thread like this and couldn't find one, so I am posting one. If you could help me, that would be brilliant.

I installed Ubuntu correctly and everything is working fine, however Firefox is not. Whenever I opened it for the first time, it went to google. I went to yahoo right after that, then it froze. not only did firefox freeze, is seemed the whole computer froze. The mouse could still move, but nothing else worked. I had to disconnect power. The second time, I turned on some music on Banshee and after a little screwing around opened firefox again. it opened to yahoo! again, and froze in about 3 seconds. I had to power down again. I tried ctrl +alt +backspace, that didn't work, Ctrl + alt + T, that didn't work, and I pressed X really fast, that didn't work. (People told me to do that.) I do not know what to do now. Can someone help? And other then that, I love it so far, and am happy to be part of a Ubuntu community!

---

### Post by staf0048 on 2011-12-01
Hi there and welcome!

Crazy experience you're having.  I've not run into it myself, but I'd suggest trying two things.

1st - lets see if it's a network problem.

If you type ctrl+alt+t it should open a terminal window.  Type in ```
sudo apt-get update
```

This will fetch a list of up-gradable packages from the Ubuntu servers (*Note that it will not actually upgrade them).

It should run fairly quickly, if the output doesn't give errors, you're network is "probably" ok.  There may be a better way to test this, but it's what I do.


2nd - if that all runs fine, trying upgrading to a new version of Firefox or try a completely different browser.  

Since you posted here you obviously have a working browser, so you can go to [http://www.mozilla.org/en-US/firefox/new/](http://www.mozilla.org/en-US/firefox/new/) and download a newer version there, extract the downloaded folder on your Ubuntu partition/computer and try running it from there (I don't believe you need to actually install it)

Alternatively you can go to the software center, do a search for Browsers and have your pick of any that are there.  

I hope one of these suggestions lead you to a solution.  All the best!

---

### Post by lovinglinux on 2011-12-04
Welcome to the forums, Ubuntu and Firefox world.

Since this is a new install, I would suggest verifying if you have the latest video driver for your card installed. You can do that using the "Additional Drivers", which can be found through the search functionality in your Dash. Just click the Ubuntu button and search for it.

It would be interesting to know some information about your system, like processor clock, ram capacity and video card model. Also, let us know if you are running Unity 2D o 3D. When you close all applications and look at your desktop panel at the top, does it have a shadow?

I would also suggest that you install these Firefox extensions, that will increase your security and help improving performance:

[AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865/)
[Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/)
[NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

I am still not sure about the source of your problem, but after we identify the source, take a look at my [Firefox optimization tutorials](http://ubuntuforums.org/showthread.php?t=1193567).

---

