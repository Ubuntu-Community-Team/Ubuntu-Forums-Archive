---
title: "OEM Install and Image Deployment"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by dabone on 2008-07-24
I'm looking to start offering 8.04 as a os choice to my customers. I know how to do the oem install, but my question is what would be a good way to deploy an Image of this to the new machines? For windows deployment I currently use a PXE boot enviroment and use WIM images. (The upside to this is that my PXE server is a Centos box, not a windows server).
I need a cost free way of deploying ubuntu images to multiple size hard drives over a network. The hardware that the image will deploy to will be fixed, (Seperate Image for each motherboard). 

G4U is out, I need a deployment image that doesn't do a bit for bit copy. Also, It needs to be scripted so the techs can just select a motherboard and then the partitons get created and imaged.


Any solutions for this currently? Dell has to be doing this somehow..


Thanks,
Mark

---

### Post by axor1337 on 2011-11-03
Hey Mark 
I was searching for a solution to the same problem and saw your post. Did you ever find a solution? 
we sell refurbished computers and have a few with no oem windows keys and want to sell them with Ubuntu 11.10. I want to set up a scripted disk to do oem installs.

---

