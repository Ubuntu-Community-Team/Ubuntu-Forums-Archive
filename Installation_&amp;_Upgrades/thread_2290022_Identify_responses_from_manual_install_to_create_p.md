---
title: "Identify responses from manual install to create preseed file"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by roland-logikalsolutions on 2015-08-08
All,

I would post this in one of the deeper forums, but few seem to go there. I have searched hopelessly for documentation on recognized ubiquity responses. The documentation at this link: 

[https://help.ubuntu.com/community/InstallCDCustomization#Changing_isolinux.cfg_to_identify_your_preseed](https://help.ubuntu.com/community/InstallCDCustomization#Changing_isolinux.cfg_to_identify_your_preseed)

Says to install debconf-utils and run debconf-get-selections (or something like that) after doing a manual install to get all responses. This returns an empty file.

I need to identify my manual responses (all of them) to create a preseed file. I'm working with Ubuntu 15.04 64-bit. I have spent days looking for this answer. All of the examples from previous Ubuntu versions appear to be useless with 15. No matter what I provide in the preseed I am still prompted to confirm partitioning and for the user password, then confirmation of that. Every example I can find for an unattended install is for an older version and the stuff just doesn't work with 15.

Appreciate any assistance you can provide.

---

