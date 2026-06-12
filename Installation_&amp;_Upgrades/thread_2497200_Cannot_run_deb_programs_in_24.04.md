---
title: "Cannot run deb programs in 24.04"
date: 2024-04-26
forum: Installation &amp; Upgrades
---

### Post by barmak2 on 2024-04-26
Hi all,

Do you know how to run .deb programs in 24.04?
Yes, I made them executable......
Thanks.

---

### Post by #&amp;thj^% on 2024-04-26
An example of what your now trying would be helpful.

Are you speaking on how to install them?

---

### Post by barmak2 on 2024-04-26
Two of the programs I cannot install are: 

[COLOR=#000000]windscribe_2.9.9_amd64.deb
or
[/COLOR]
[COLOR=#000000]google-chrome-stable_current_amd64.deb[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by #&amp;thj^% on 2024-04-26
For Google Chrome:
```

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```

For Windscribe, I'll assume you have already downloaded the .deb...if not use:
```
wget https://github.com/Windscribe/Desktop-App/releases/download/v2.10.8/windscribe_2.10.8_guinea_pig_amd64.deb
```
Now for that install use:
```
sudo dpkg -i '/home/me/windscribe_2.10.8_guinea_pig_amd64.deb' 

```
Now you need to fix your broken install:
```
sudo apt -f install

```
You should be good to go now.

---

### Post by Autodave on 2024-04-26
Or just download *gdebi *and install using that.

---

### Post by barmak2 on 2024-04-27
Thank you, 1fallen. I did it.

---

### Post by TheFu on 2024-04-27
> **barmak2 said:**
> Thank you, 1fallen. I did it.

You should be aware that manually installing programs like this means you need to manually keep them patched.  I bet Google-Chrome does that through some reminder (Chrome is always watching what you do online), 

I don't know what windscribe is, but if it is a VPN, you'll need to manually check at least monthly for updates/patches.  Don't expect it to automatically upgrade/patch.

Directly installing .deb files is a good way to break a Linux computer. Usually it will be fine for 3-6 months before dependency issues arise and other parts of your installation start having issues patching.  When that happens, you'll need to remove/purge these packages, update the system and search for newer versions of those packages.

The better way to handle installs of non-Canonical Repo packages are to use a trusted PPA. This extends the OS package management to include the trusted add-on repo, so when they update the packages there, your normal weekly patching will get their updates just like they came from Canonical with crypto-graphic signatures.

I struggle when people choose to install a browser from a huge internet marketing company.  Oh well, your choice for your privacy.

---

### Post by deadflowr on 2024-04-27
> You should be aware that manually installing programs like this means you need to manually keep them patched. I bet Google-Chrome does that through some reminder (Chrome is always watching what you do online),

Chrome adds their repo to the system upon initial install so it'll get updates whenever you run an update.
But that's a specific design of chrome, +1 to needing to watch others that don't do that.

---

### Post by #&amp;thj^% on 2024-04-27
FWIW Windscribe Future Updates

The app will notify you of any future updates, and you can install them with a single click, directly from the app.

---

### Post by MAFoElffen on 2024-04-28
This seems solved... But I thought an additional explanation should probably be mentioned here, for others who might be reading this later.... 

The Linux learning experience of this is that .deb files are not 'executable' files. You don't 'run them'. They are a type of archive file, usually used to install something. They could also contain scripts to fix something... and sometimes, since that is possible, may contain something malicious, if used for such nonsense. That is why we try to be careful of the sources we download and say we trust. Debian branch Linux uses .deb file archives. other types Distro's use other formats. 

You do not need to install anything 'additional' onto Ubuntu to use them. there is 'dpkg' (as 1fallen demonstrated) and the Software Center.

A lot of people do not realize that the 'apt' utility can be used to install local .deb files, for example
```

sudo apt install /home/me/windscribe_2.10.8_guinea_pig_amd64.deb

```
If you give it a path, even if in the same folder, by using ./file_name.deb, the path tells apt that it is local, instead of being from a repo.

---

