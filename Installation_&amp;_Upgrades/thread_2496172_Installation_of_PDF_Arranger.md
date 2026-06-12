---
title: "Installation of PDF Arranger"
date: 2024-03-17
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2024-03-17
Hello everybody,

I used to used PDF Shuffler all the time with success -- it worked very well for me. But it appears that PDF Shuffler has been replaced by PDF Arranger. I am using Lubuntu 22.04.4 LTS (Jammy). Because it is Lubuntu, there is no formal "Software Center" to use to download and install apps as I recall there used to be with other forms of Lubuntu in the past. I want to install PDF Arranger, but I want to install it safely and I want ask a couple of questions before the installation.

1) Is PDF Arranger in the repos for Ubuntu?

2) Is PDF Arranger a safe app to install in Ubuntu?

3) Can PDF Arranger be installed in Ubuntu using Terminal Commands, and if the answer is "yes" what are The Terminal Commands?

4) Is using Terminal Commands the safest way to install PDF Arranger in Ubuntu?

Thank you,

Able

---

### Post by deadflowr on 2024-03-17
Yes it's available, at least on 22.04, in the repositories.
Packages in the Ubuntu repositories are generally safe to install.

Installing through the terminal is no less safe than installing through some gui app like synaptic or Ubuntu Software.
It is, however, probably the quickest.

The package is pdfarranger
It installs like any other package
```
sudo apt install pdfarranger
```

---

### Post by Holger_Gehrke on 2024-03-17
Unless something is wrong with your installation, there should actually be two graphical package installers on Lubuntu - Discover which is a lot like the Software center and Muon which is more like Synaptic. Both are described in [chapter 4 of the Lubuntu manual]("https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html").

Holger

---

### Post by AbleTassie on 2024-03-18
Thank you very much DeadFlower and Holger,

I installed PDF Arranger using the Terminal Command and it seems to work very well. I also checked and I do indeed have Muon Package Manager and Discover under System Tools; I was not aware that they had taken the place of previous package installers.

Able

---

