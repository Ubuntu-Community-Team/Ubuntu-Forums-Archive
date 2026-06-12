---
title: "Repositories out of date"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by softdelete on 2012-02-18
Hi, 
I'm running oneiric ocelot on my laptop. I haven't been running it for long so I only added 1 other repository than the default when I installed QGIS on my laptop. I'm getting a message that says my repositories are out of date. How can I know which ones and how can I update them? 

Thank you 

Sorry if its a repeat, I did my best to find a post on this in the threads first.

---

### Post by plucky on 2012-02-18
> **softdelete said:**
> Hi, 
I'm running oneiric ocelot on my laptop. I haven't been running it for long so I only added 1 other repository than the default when I installed QGIS on my laptop. I'm getting a message that says my repositories are out of date. How can I know which ones and how can I update them? 

Thank you 

Sorry if its a repeat, I did my best to find a post on this in the threads first.


Welcome to the forum.

Open a terminal and run ```
sudo apt-get update
``` and post any errors to the forum.
If no errors,then run ```
sudo apt-get upgrade
``` to install the updates.Again post if any errors.

Good Luck

---

### Post by softdelete on 2012-02-18
hey, there doesn't seem to be any errors with the ubuntu repositories, this seems to be the only issue: 

W: GPG error: [http://qgis.com](http://qgis.com) oneiric InRelease: File /var/lib/apt/lists/partial/qgis.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/qgis.com_ubuntu_dists_oneiric_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/qgis.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch [http://qgis.com/ubuntu/dists/oneiric/main/i18n/Index](http://qgis.com/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/qgis.com_ubuntu_dists_oneiric_main_i18n_Index

Would there be any situation when the repositories from where the OS updates would expire?

---

### Post by plucky on 2012-02-18
What is 

[http://qgis.com](http://qgis.com)? because when you click on it it doesn't go to any particular website.

Disable it in your Software Sources and try again.

Good Luck

---

### Post by softdelete on 2012-02-18
That's quantum GIS the one repository I put in myself. 
Anyway, would there be any situation when the repositories from where the OS updates would expire?

---

### Post by plucky on 2012-02-18
> **softdelete said:**
> That's quantum GIS the one repository I put in myself. 
Anyway, would there be any situation when the repositories from where the OS updates would expire?

I don't understand the question.

Expire?

The repositories will close when the OS reaches End OF Life

See [Here](https://wiki.ubuntu.com/Releases)

Good Luck

---

