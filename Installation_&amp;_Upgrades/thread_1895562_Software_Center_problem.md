---
title: "Software Center problem?"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by BeMyManikin on 2011-12-15
I went on to the Software center to install an emulator and it says "Failed to download package files. Please check your Internet connection." It even says that when I tried to download another form of software from there as well that isn't gaming related. Thanks for the help in advanced.

---

### Post by jaimeaux on 2011-12-15
> **BeMyManikin said:**
> I went on to the Software center to install an emulator and it says "Failed to download package files. Please check your Internet connection." It even says that when I tried to download another form of software from there as well that isn't gaming related. Thanks for the help in advanced.
 
This may be a stupid question, but have you checked your internet connection? 
 
I had a problem like that, but it turns out I just needed to restart my router.

---

### Post by BeMyManikin on 2011-12-15
> **jaimeaux said:**
> I had a problem like that, but it turns out I just needed to restart my router.
I just tried that, but it still says the same thing.

---

### Post by bluexrider on 2011-12-15
open your Software Sources and change the server from "Main" to "Other" then use "find best server"

then in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BeMyManikin on 2011-12-16
[FONT=Arial]HELL YEAH!!! Worked like a charm! But when I did the update you said to do it had this in it:
[/FONT]> [FONT=Arial]W: A error occurred during the signature  verification. The repository is not updated and the previous index files  will be used. GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/")  oneiric Release: The following signatures were invalid: BADSIG  16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key  <ftpmaster@ubuntu.com>

W: Failed to fetch [/[/FONT][FONT=Arial][http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  [/FONT][FONT=Arial]

W: Failed to fetch [/FONT] [FONT=Arial][http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [/FONT] [FONT=Arial][http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead. [/FONT][FONT=Arial]
[/FONT][FONT=Arial]Is that normal? If not, I'll just post it in another area to get it resolved.
THANK YOU AGAIN![/FONT]

---

### Post by oldos2er on 2011-12-16
The 'moonlight' PPA doesn't have an Oneiric repository, assuming you're running Oneiric 11.10.

---

### Post by bluexrider on 2011-12-16
> **oldos2er said:**
> The 'moonlight' PPA doesn't have an Oneiric repository, assuming you're running Oneiric 11.10.

 Oldos2er's right, there is no repository for Oneiric using the "moonlight" PPA so my recommendation would be to edit your sources file and "comment it out" using # or at least editing the sources by "unchecking" the box beside the source line.

---

### Post by BeMyManikin on 2011-12-17
> **bluexrider said:**
> Oldos2er's right, there is no repository for Oneiric using the "moonlight" PPA so my recommendation would be to edit your sources file and "comment it out" using # or at least editing the sources by "unchecking" the box beside the source line.
Yeah... and how would I go about doing that? I am new to Ubuntu after all.

---

### Post by bluexrider on 2011-12-17
> **BeMyManikin said:**
> Yeah... and how would I go about doing that? I am new to Ubuntu after all.

in terminal

```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```under tab "other software"

scroll until you find monlight-team PPA and uncheck the box next to it. close then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BeMyManikin on 2011-12-17
it still says after the update
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by bluexrider on 2011-12-17
> **BeMyManikin said:**
> it still says after the update


```
gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192 gpg --export --armor 3E5C1192 | sudo apt-key add -
```

---

### Post by BeMyManikin on 2011-12-19
It says this after the code you gave.
> gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
gpg: no valid OpenPGP data found.

---

### Post by bluexrider on 2011-12-19
ok I'll look again

---

### Post by bluexrider on 2011-12-19
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192
```

---

### Post by BeMyManikin on 2011-12-20
ok it says now
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.wjqbBZy2Wd --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com recv-keys 3e5c1192
usage: gpg [options] [filename]

I have no idea what that means.

---

### Post by oldos2er on 2011-12-21
Are you still getting the BADSIG error from **sudo apt-get update** ? If so, run these commands one at a time: $ ```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

---

### Post by BeMyManikin on 2011-12-22
> **oldos2er said:**
> Are you still getting the BADSIG error from **sudo apt-get update** ? If so, run these commands one at a time: $ ```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```
OH YEAH! When I do the sudo apt-get update
I don't get the error message anymore THANK YOU!

---

