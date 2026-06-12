---
title: "Windows Server 2008 PXE Ubuntu non netboot"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by DJNightchild on 2012-08-03
Dear Forum Members,

I've read a tutorial on a site how to deploy Ubuntu over an network by using pxelinux in windows 2008 deployment Services. ([link]("http://thommck.wordpress.com/2011/09/09/deep-dive-combining-windows-deployment-services-pxelinux-for-the-ultimate-network-boot/")) I was excited it worked with the netboot version.

The only downside I experienced was how the netboot version searched the internet mirrors for the files Ubuntu needed to install.

My question is: Is it possible to deploy a full Ubuntu live cd over my network (or using my server as mirror). 

Thanks in advance,

---

### Post by DJNightchild on 2012-08-04
Never mind, found the answer in the comments:

You can do this by having a copy of the full install version of Ubuntu  hosted by IIS on the same server as WDS. Then, when the setup asks for a  mirror to choose just point the installer to [http://WDSServer/VirtualDirectory](http://WDSServer/VirtualDirectory).  You should find more info on this in the Ubuntu help site. They will  probably recommend apache as a webserver but IIS is fine for this  purpose

---

