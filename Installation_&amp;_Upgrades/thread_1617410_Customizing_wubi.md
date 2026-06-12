---
title: "Customizing wubi"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by practitec on 2010-11-09
Hi,

I'm looking for some help with customizing wubi for ubuntu lucid. I'm trying to create a wubi.exe that would download our customized livecd-image from our server. I've read the wubi guide in wiki.ubuntu.com but it doesn't go to specifics about customizing the thing.

I've succesfully downloaded the source and compiled it to create a working normal wubi.exe that downloads the image from ubuntu's servers. But if i try to customize /data/isolist.ini to include an entry for our custom livecd (url for metalink, metalink md5, metalink md5 signature) and then compile the thing, the wubi.exe gives me an error "no module named PublicSubkey".

i suspect this has something to do with the signature checks, the wubi guide tells me that i could skip all the keys & signatures stuff by editing settings.nsh in the /data folder, but settings.nsh doesn't exist? ive included the wubi logfile as an attachment.

Help would be much appreciated!

---

### Post by bcbc on 2010-11-09
It says it can't find module PublicSubkey - under 'src/openpgp/sap/pkt'. Did you get any build errors that indicate that it didn't succeed? Or difference between compiling the default wubi.exe vs your custom version?

You might find someone who can help in #ubuntu-devel on irc.

---

