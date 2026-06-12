---
title: "Install latest version of rdesktop"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by Luuk_Prins on 2015-02-25
For anyone interested, this is how I managed to install the latest version of rdesktop with all options enabled:
First of all get the latest version from: [http://www.rdesktop.org/#download](http://www.rdesktop.org/#download)

At the time of writing 1.8.3!

Open a terminal and get to the folder where you downloaded rdesktop.

```

sudo apt-get update
 sudo apt-get install build-essential libx11-dev libssl-dev libgssglue-dev libpcsclite-dev
tar zxvf rdesktop-1.8.3.tar.gz 
cd rdesktop-1.8.3
./configure
make
sudo make install

```

I had to create a symlink from /usr/local/bin to /usr/bin to make it system wide accessible, but I think that was because I had already installed an old version through apt-get.
Apt-get will install rdesktop but an old version which has problems with the cursor in Windows 7 and up. I was able to fix the cursor problem installing the latest version.

Just wanted to share hope I can help others this way!

---

### Post by rnijenhu on 2015-09-15
Came across this post, had the same problem with win10, and made thankful use of it \\:D/ Rdesktop 1.8.x is available in 15.04 but 15 has no LTS (yet) and breaking my current (14 LTS) is not an option for me. So I did the install on a different location (/opt) and made a link in ~/bin with a slightly different name, now I can choose between the old and new release each time without breaking the system.

```


cd /tmp
sudo apt-get update sudo apt-get install build-essential libx11-dev libssl-dev libgssglue-dev libpcsclite-dev
wget https://github.com/rdesktop/rdesktop/releases/download/v1.8.3/rdesktop-1.8.3.tar.gz
tar zxvf rdesktop-1.8.3.tar.gz  
cd rdesktop-1.8.3 
./configure --prefix=/opt/rdesktop-1.8.3
make 
sudo make install

mkdir ~/bin
cd ~/bin 
ln -s /opt/rdesktop-1.8.3/bin/rdesktop rdesktop183 


```

---

### Post by ctav01 on 2016-04-06
Thanks @rnijenhu, this fixed a problem I was having.

Two small changes: I think there should be a "&&" after the "sudo apt-get update" and I changed the "cd ~/bin" to "cd /usr/bin" so the "rdesktop183" link was where it was more usable for me.

---

### Post by oldos2er on 2016-04-06
Old thread closed.

---

