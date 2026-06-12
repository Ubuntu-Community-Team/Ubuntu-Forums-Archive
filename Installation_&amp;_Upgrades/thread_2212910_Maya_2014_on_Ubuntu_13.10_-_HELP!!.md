---
title: "Maya 2014 on Ubuntu 13.10 - HELP!!"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by acron2 on 2014-03-23
I am having difficulty installing Maya on Ubuntu
I've been tryint to install maya on my ubuntu with a lot of difficulty
1. I tried following instructions on the Autodesk website which said to simply run "*sudo rpm -ivh --force Maya2014_64-2014.0-986.x86_64.rpm adlmapps7-7.0.51-0.x86_64.rpm adlmflexnetclient-7.0.51-0.x86_64.rpm*" I kept getting "error: Failed dependencies: /bin/sh is needed by Maya...."
I looked up this error and apparently someone said that it's to do with the rpmDB being corrupted, so I reinstalled that with no result
2. I tried simply sunning the "./setup" and it seemed to work for a bit, actually bringing the installer window and asking for serial numbers and all that. I put in my productID and serial that I got for the windows version and it all gets accepted, but then when I click the install button, the installation just fails
3. I tried using alien, converting rpms to debs, installing them manually 1-by-1 by double clicking and going through the software installer, then doing the "sudo apt-get install" for each package, It seemed to be working, it was creating the files and directories where it's supposed to go, but I still wasn't able to actually RUN maya
4. I found a script on here: [https://gist.github.com/insomniacUNDERSCORElemon/5555214](https://gist.github.com/insomniacUNDERSCORElemon/5555214) but when I tried running it it had errors and wouldn't work, so I followed along with the commands but I get to the "license" section and I don't know what to do
I've been at this for like a good solid week and I really need maya for projects

Please can someone help me out.

---

