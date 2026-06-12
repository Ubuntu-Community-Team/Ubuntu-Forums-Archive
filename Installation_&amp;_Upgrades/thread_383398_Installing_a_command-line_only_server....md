---
title: "Installing a command-line only server..."
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by sambront on 2007-03-13
I'm trying to install a command-line server using the alternate Ubuntu 6.10 CD. When installing, I've tried "install server", "install server-expert", and "install command-line", and the install starts, but then when the install is done, Gnome starts as well.

Also, can I do a LAMP install using the alternate CD? When using the regular server install CD, I had the option to do DNS or LAMP, but I don't get that question with the alternate CD.

By the way, I'm using the alternate CD because I'm installing to Parallels, and the regular server CD apparently throws errors when you do that, and the workaround is to use the alternate CD. I'm not sure what the difference is, exactly.

Thanks.

---

### Post by rjfioravanti on 2007-03-13
i would recommend just uninstalling gnome and then installing apache and php

apt-get makes all that really easy

---

### Post by sambront on 2007-03-13
I want to install the absolute bare-bones system. Apparently there is a command-line only server install, but I can't figure out how to do it. The install of the server disc is the exact opposite of the desktop disc: it's frustrating and inconsistant.

Does anybody know how to install a command-line only server install of Ubuntu 6.10? ubuntu.com says it can be done, but none of the instructions on how to do so actually work.

I think I'll end up installing 6.06. The upgrade to 6.10 should be pretty easy, right? will "apt-get dist-upgrade" work for a command-line only system?

Thanks.

---

### Post by rjfioravanti on 2007-03-13
You may not need to do that. It sounds like what happened is it went ahead and installed the ubuntu -desktop package, which is bundled with gnome and a bunch of gnome apps

I believe all of these can be removed with 

```

sudo apt-get autoremove ubuntu-desktop

```

Then if you still feel like you are bloated, go into aptitude

```

sudo aptitude

```

and use that utility to browse your installed packages and remove whatever you feel like you don't need. They are well organized and every package has a description so you know what they are for and can get a good idea of whether you need them or not

---

### Post by sambront on 2007-03-13
Thanks for the replies.

I have a concern, and an issue.

Concern: I though about just removing the gnome desktop, but I figured even doing that would leave something behind, and I don't want anything to interfere with whatever I do after installing the server (i.e. I plan on installing some other WM and desktop).

Issue: I am installing this to a 2GB partition, and the server install that I'm using finishes, and then won't let me login because I'm already out of disc space. So a bare-bones system would not have this problem.

Finally, I like the idea of the server already having LAMP built in.

I'll keep your suggestion in mind, thanks. But just so I know, would installing the 6.06.1 command-line only server, and then doing apt-get dist-upgrade bring me to 6.10?

Thanks again.

---

### Post by rjfioravanti on 2007-03-13
re: your issue, can you start in safe mode? from there you may be able to remove packages and free up disk space

re: your concern, generally people accept that apt-get handles dependencies very well, and would not leave behind stuff that is not needed, or that would interfere later

If you do go ahead and install 6.06  (what do you have now?) then you can upgrade to 6.10 using dist-upgrade as you said, but first you will have to edit your /etc/apt/sources.list file to point to the 6.10 repositories. There is information on how to do that elsewhere on the forum

---

### Post by chris308 on 2007-03-14
I'm actually doing the "command-line" sever installation tonight for a test.  Sounds like you just downloaded the wrong iso.  Look on the mirrors for 6.06 or 6.10 server image to download.  It will install a lean minimal system with no Xserver or desktop environment.  So far so good on my installation this evening.

Here is the image I'm using:  [http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-server-i386.iso]("http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-server-i386.iso") 

Hope this helps.

---

