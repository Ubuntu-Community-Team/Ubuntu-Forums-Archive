---
title: "Creation and deployment of custom preinstalled OEM image"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by thing on 2006-12-30
I want to preinstall ubuntu on custom built end user pcs instead of Windows so customers can enjoy Ubuntu Linux out of the box.

Thus, my goal is to create a master image with a preinstalled ubuntu that can be readily deployed to any end user pc with any configuration.

Preferably the preinstalled image should be located on a server that clients connect to on network boot and start deploying the image automatically. Otherwise, a simple cd/dvd based automatic installation will do.

My planned route for creating master image is:
1) install oem installation from alternate cd, make customisations (as little as possible), run sudo oem-config-prepare to prepare for end user, shutdown
2) boot with livecd and grab ext3 file system as the master image ( dd if=/dev/hda1 of=/masterimage.iso )

My planned route for deployment on end user pc is:
1) partition disk (ext3 plus 512mb swap)
2) deploy master image to disk ( dd if=masterimage.iso of=/dev/hda1 )

Creating the master image is easy. I would like comments on whether it is recommendable.

Deploying the image across multiple pcs with multiple configurations is more challenging.

Questions:
1) How do I handle the partitioning automatically so that it adjusts to various disk sizes? Command lines / script is most welcome!
2) Is 512mb swap acceptable regardless of physical memory (could be ranging from 256 mb to 2 gb depending on the end users choice)
3) Is this overall approach a good route or is there a better route?

Thanks!

---

### Post by Sef on 2006-12-31
> 2) Is 512mb swap acceptable regardless of physical memory (could be ranging from 256 mb to 2 gb depending on the end users choice)

I would go with 1 gb swap since swap is supposed to be twice your ram.  Above 1 gb ram, you don't need swap much unless you are doing heavy gaming or video editing.

---

### Post by noyaforte on 2007-10-02
When I tried the following command, I received an error message, "no such file or directory"

2) deploy master image to disk ( dd if=masterimage.iso of=/dev/hda1 )


Why?

---

