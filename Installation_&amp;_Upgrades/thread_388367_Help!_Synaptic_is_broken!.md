---
title: "Help! Synaptic is broken!"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by waveslider on 2007-03-19
Someone please help!

I attempted to install VirtualBox through Automatix, and now apt-get / Synaptic are broken! When I open the Synaptic package manager, there are no packages/software displayed, and I get the following error message:

"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Can anyone *please* help me??

---

### Post by louis_nichols on 2007-03-19
This can be solved in a number of ways and they all require that you restore your sources.list. I'm pretty sure automatix backs up your original list, so you can start by using that. I'm not sure how the file will be renamed, but it will be fairly intuitive. So what you need to do is look into the folder /etc/apt for the original file, that automatix replaced. Then, you will have to execute this command:

```
sudo cp /etc/apt/*name-of-original-list* /etc/apt/sources.list
```
If the original file is not there, you can just copy paste some defaults from the net. This is easy. Just go to [ubuntu source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/") and follow instructions to obtain a list, and then copy and paste its contents in the file /etc/apt/sources.list (make sure you delete everything else in the file first).

OK. That was the hard part. Nex, just use these commands to restore your system to a working state:
```
sudo apt-get update && sudo apt-get -f install
``` This will most likely remove the trouble causing package, but that is actually the purpose.

---

### Post by waveslider on 2007-03-19
Louis,

Thank you very much for your help. I tried your advice (restoring my original /etc/apt/sources.list and running sudo apt-get update && sudo apt-get -f install), but I still seem to have the same problem.

The output I got was:
Fetched 152kB in 1m11s (2115B/s) 
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release)  Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
tom@Waveslider:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.


Any ideas how I can fix this? I've backed everything in my home directory up, just in case. But I'd rather not reinstall the whole OS if that can be avoided. 

Thanks!

---

### Post by jackrobinson on 2007-03-19
do this:
```
wget http://www.virtualbox.org/download/1.3.6/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb
sudo dpkg -i VirtualBox_1.3.6_Ubuntu_edgy_i386.deb
sudo apt-get remove virtualbox
```

---

### Post by louis_nichols on 2007-03-19
What jack suggests is a possible solution, with the advantage that it will allow you to install virtualbox. However, I suspect that it is the deb package of virtualbox tself that caused all this in the first place, so this solution might not work.

Another thing you can try to restore your system, but without having virtualbox, is this:

```
sudo apt-get remove virtualbox
```

---

### Post by waveslider on 2007-03-19
Louis,

Thanks, man. I tried that, but it didn't work because Synaptic said it couldn't find the Virtual Box package.

Jack,

Thanks - that seems to have worked! I'm so glad I don't have to reinstall Ubuntu.

---

### Post by Ordep_ on 2007-03-19
I'm having the same problem but with OpenOffice.org 



E: The package openoffice.org-core04u needs to be reinstalled, but I can't find an archive for it.



should I try the same???

---

### Post by jackrobinson on 2007-03-19
> **Ordep_ said:**
> I'm having the same problem but with OpenOffice.org 



E: The package openoffice.org-core04u needs to be reinstalled, but I can't find an archive for it.



should I try the same???
yes first locate where the package came from (a third repository which you manually added or external source) and then download it, install it and then remove it. However be careful with OO. It has many core dependencies.

---

### Post by Kateikyoushi on 2007-03-19
Try the same and get the package from packages.ubuntu.com

---

