---
title: "How to uninstall/reinstall ubuntu 10.10"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by derek826 on 2010-11-03
Hi, so i installed ubuntu 10.10 about  a day ago, then today the internet wouldn't work.  So i, trying to fix it, accidentally deleted the Network Manager applet.  So i cant figure out a way to get internet back. if anyone knows how to put it back onto my ubuntu, that would be nice. since i don't have internet im thinking that im probably going to have to download to a flashdrive on another computer.  If no one knows how to do that then how do you uninstall ubuntu, and then reinstall it. Please post.

-Thanks

---

### Post by akand074 on 2010-11-03
If you can connect via a wired connection you can open up the Terminal and run this command to connect to the internet (I think):

```
sudo dhclient eth0
```

You could also check these links if you need more help:

[https://help.ubuntu.com/community/Ne...ionCommandLine]("https://help.ubuntu.com/community/NetworkConfigurationCommandLine")
[http://www.ubuntugeek.com/ubuntu-net...mand-line.html]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html")

Also you could just download it on another computer and transfer it over:

[http://packages.ubuntu.com/search?suite=maverick&searchon=names&keywords=network-manager](http://packages.ubuntu.com/search?suite=maverick&searchon=names&keywords=network-manager)

You might also be able to install it using a live CD, I'm not quite sure how to do that. You could try making a google search. I found lots of pages about the same issue from one quick search.

---

### Post by garvinrick4 on 2010-11-03
Not a big enough reason to reinstall fix it. And no uninstall in Ubuntu just use manual install and install in same partition formatting will take
care of uninstalling. The ubuntu forum links will have your same problem and its fixes. I will bet this has happened to a lot of users. Stick to it derek826.
Here is a link:
[http://ubuntuforums.org/tags.php?tag=nm-applet](http://ubuntuforums.org/tags.php?tag=nm-applet)
Open a terminal
```
nm-applet
```

---

