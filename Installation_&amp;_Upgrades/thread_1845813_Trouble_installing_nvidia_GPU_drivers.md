---
title: "Trouble installing nvidia GPU drivers"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by lanzd on 2011-09-17
Hello, I just upgraded to a nvidia GeForce GTX 560 ti video card and am unsure how to install the drivers. I've seen another thread discussing this issue but it is old and I need help following the steps.  And I'm not even sure if it applies.  

The thread I've been reading is [http://ubuntuforums.org/showthread.php?t=1681040](http://ubuntuforums.org/showthread.php?t=1681040)

Now I've downloaded what I believe to be the correct driver for my card off of the nvidia site here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I chose GeForce 560 ti as the product, linux 32 bit, english US and get the file 

NVIDIA-Linux-x86-280.13.run

I've tried running the file in the terminal and it gives a message saying it requires root access.  So I logged into root and ran the file and then get a message saying I currently seem to be running an x server, please exit x before installing.  

I'm not entirely sure what x is, from what I've been reading I think its part of the gui interface for unbuntu.  But I have no idea how to exit it.  Any relevant information I've found seems to involve temporarily disabling the gui and I tried one method but It completely locked up my system.  I then reinstalled ubuntu after deleting the old partition. (It was a barebones install in the first place so I didn't lose anything).  

Thank you for any help.  And sorry if I'm a little dumb with this stuff.  I'm very new to ubuntu or even linux for that matter.

Dan

---

### Post by lanzd on 2011-09-17
Dang it, I just realized after I submitted I had mis-clicked into the wrong thread.  I'm going to repost this in the proper forum so this can be deleted.  Sorry.

---

### Post by MAFoElffen on 2011-09-17
> **lanzd said:**
> Dang it, I just realized after I submitted I had mis-clicked into the wrong thread.  I'm going to repost this in the proper forum so this can be deleted.  Sorry.
Actually, this is the corrrect thread.  Follow the directions from post #280 from my sticky:
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

It has all the current workarounds incorporated into the instructions.

Before installing, if you go to a terminal and run
```

sudo service gdm stop

```
It will shutdown the X-session to a TTY text session, so that the grapghics is shutdown during the install.

As for ID'ing whether you have the correct driver, in a terminal run
```

lspci -v | grep VGA

```and it will display the Device PCI ID Code of your card.  Use this code when you look up your card and what driver series it uses:
 [A. Supported NVIDIA GPU Products]("ftp://download.nvidia.com/XFree86/Linux-x86/173.14.30/README/appendix-a.html")
 Adapt the instructions to the driver your need.

---

