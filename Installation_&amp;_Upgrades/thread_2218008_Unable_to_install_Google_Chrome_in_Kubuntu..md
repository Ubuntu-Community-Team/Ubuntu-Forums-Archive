---
title: "Unable to install Google Chrome in Kubuntu."
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Manish_Kumar_Singh on 2014-04-19
Yesterday I installed kubuntu 14.04 LTS. I am used to chrome and hence wants to install it. I have got the required files with me. When I open the file, there is error that 'depedencies not satisfied.' The installer is Q APT installer package. Because of this I'm also unable to download adobe flash or vcl. Please help me out og this. Thanks in advance

---

### Post by SeijiSensei on 2014-04-19
First, I'd see whether the open-source version of Chrome, called "Chromium," can satisfy your needs.  You can install it with "sudo apt-get install chromium-browser".

Proprietary applications distributed as binary "blobs" often expect to find specific versions of libraries that they need to run.  You'll need to install a version of Chrome known to work with your specific version of Ubuntu.

---

