---
title: "computer wont let me upgrade to 12.04"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by idontknow626 on 2012-06-02
ok, so i friend of mine had upgraded my system to the raw version of 12.04. so when it finally came out, i tried to upgrade but my computer fights me at EVERY turn. can anyone help me?

P.S. when i try to do a torrent, the load screen shows up, but shows nothing and i cant download anything from TPB or anything like that. can anyone help me with this aswell?

---

### Post by darkod on 2012-06-02
As far as I know, if you were running the Alpha or Beta of 12.04 you don't do an upgrade when it's released. You only update the packages.

sudo apt-get update
sudo apt-get upgrade

---

### Post by idontknow626 on 2012-06-16
awesome, thanks man. can you tell me why i cant download torrents?

---

### Post by darkod on 2012-06-16
I have no idea about torrents. What are you using, transmission?

Can you at least upload the .torrent file to transmission, but it doesn't download, or you can't even upload the .torrent there?

Because if the problem is not starting to download, it could be ISP related (maybe they are blocking torrents in some way), or it could be port related for best results. Usually the port that transmission is using needs to be forwarded to your computer, and sometimes you need to make sure the computer doesn't change the IP address if the port is forwarded using the IP.

---

### Post by patryk007 on 2012-06-16
> **darkod said:**
> sudo apt-get update
sudo apt-get upgrade
The recommended way to upgrade by command line is called **do-release-upgrade **([click]("https://help.ubuntu.com/10.04/serverguide/installing-upgrading.html")).

---

### Post by darkod on 2012-06-16
> **patryk007 said:**
> The recommended way to upgrade by command line is called **do-release-upgrade **([click]("https://help.ubuntu.com/10.04/serverguide/installing-upgrading.html")).

Correct. But also read the first line of my post that you left out from your quote. If you are already running the Alpha or Beta versions of 12.04 (installed maybe before the final release was out), you simply need to do the update (apt-get upgrade) to get the latest packages. At least that's what I have read about updating from the Alpha/Beta.

You are not actually performing upgrade from one version to another since you are already running 12.04 (Alpha or Beta).

The OP said he's already running 12.04.

---

### Post by idontknow626 on 2012-06-23
yes im using transmission. ill go to a site to download a torrent, and when i click the link to download the transmission window opens but nothing is in the window

---

### Post by darkod on 2012-06-23
> **idontknow626 said:**
> yes im using transmission. ill go to a site to download a torrent, and when i click the link to download the transmission window opens but nothing is in the window

Have you tried not doing it automatically from the website?

First download the .torrent file on your computer.
Then open Transmission yourself, and add the torrent manually.

Does that help?

---

