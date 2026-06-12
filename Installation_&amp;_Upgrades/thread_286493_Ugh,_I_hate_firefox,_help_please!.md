---
title: "Ugh, I hate firefox, help please!"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by NewWaves on 2006-10-27
Alright, I downloaded ff 2.0 with the aid of a script. I really don't like FF 2.0 at all!  How can I remove it, and get 1.5 back?!  I tried removing all my firefox files manually and using apt to install 1.5 back in, but that didn't work!

Here's the script I used:

#!/bin/bash
echo "Updating repositories list
"
sudo apt-get update
echo "
Making sure libstdc++5 and the old Firefox are installed
"
sudo apt-get -y install firefox libstdc++5
echo "
Backing up old Firefox preferences
"
cp -R ~/.mozilla ~/.mozilla_backup
echo "
Changing to home directory
"
cd
echo "
Downloading Firefox from the Mozilla site
"
wget -c [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz)
echo "
Unzipping the .tar.gz file
"
sudo tar -C /opt -x -z -v -f firefox-2.0.tar.gz
echo "
Removing the unzipped .tar.gz
"
rm firefox-2.0.tar.gz
echo "
Linking plugins
"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
echo "
Linking launcher to new Firefox
"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
echo "
The new Firefox is installed."

Thanks for any help! This is really bugging me to no end! ](*,)

---

