---
title: "install 3rd party software"
date: 2020-06-29
forum: Installation &amp; Upgrades
---

### Post by isza on 2020-06-29
Hi,

I finally got Ubuntu Studio 20.04 up & running from a USB-Stick on my Mac Mini. 

Now I'd like to install 3rd party software which wasn't included in the bundle. When I try the downloaded (for Ubuntu) Skype, for example, I click on install, then I enter the authentication and instead of installing it shows the following message:

Unable to install Skype! The following packages have unmet dependencies:

What are unmet dependencies? How can they be made to meet the expectations?

Any help appreciated!

---

### Post by Holger_Gehrke on 2020-06-29
Dependencies are other bits and pieces of software - often libraries - that the software you're trying to install uses. Normally the package manager will take care of dependencies automatically. You'll only see an error like that when the packages depends on something that is not available for the system you're using, usually when running a new system and trying to install software that depends on really old stuff which has been removed from the system. In the case of skype you can use a snap package, those are isolated from the rest of the system and bring everything they need along. A simple 'snap install skype' in a terminal will download and install Skype.

Holger

---

