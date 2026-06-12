---
title: "Update issue !!!"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ibrahim.k on 2010-03-07
Hi,
I have installed the latest kernel version for the next ubuntu release
 (alpha luiced)2.6.32-11-generic


But the update manager is still asking me to install updates realeated to the kernel 
2.6.31.17.30

why is that happening ?? I have the final version and all the problems were solved after installing it (sound problems for example)

---

### Post by NightwishFan on 2010-03-07
Perhaps manually remove the old kernel?

---

### Post by ibrahim.k on 2010-03-07
How can I remove the old one ? am sorry i don't know how

---

### Post by NightwishFan on 2010-03-07
Thats ok. Open System -> Administration -> Synaptic and remove the package corresponding with the old kernel. It should be called something like linux-image-2.6.31-17-generic. 

Make sure you do not remove your running kernel which is 2.6.32 right?

---

### Post by ibrahim.k on 2010-03-07
yes i can find linux-image-2.6.31-17
but when i mark it for complete removal I press apply then he tells me that 
to be installed
linux-image 2.6.31-19 generic
and to be upgraded
linux-generic
linux-image

what should i do ?

---

### Post by NightwishFan on 2010-03-07
What kernel version are you running? Type this in a terminal and post back here:
```
uname -a
```

Perhaps manually unmark the 2.6.31-19 as well. Just ensure you have at least 1 kernel installed before you hit apply.

Also, how did you update to Lucid?

---

### Post by ibrahim.k on 2010-03-07
this is the output.
Linux ibrahim-laptop 2.6.32-11-generic #15-Ubuntu SMP Tue Jan 19 18:16:27 UTC 2010 i686 GNU/Linux


this is how i updated
i have installed three files .deb files and in a terminal 
sudo dpkg -i
I cant remember the rest of it.

---

### Post by NightwishFan on 2010-03-07
You may not want to use the Lucid kernel on Karmic unless you know what you are doing. The linux-generic package for Karmic will target the 2.6.31 kernel. That is why it still wants to use it.

---

### Post by ibrahim.k on 2010-03-07
I want to use that kernel because sound problems are gond also the remote control for my laptop is now working with that kernel and the multimedia keys all of them are working unlike the older version...
what do you suggest now please ? I hate that i am always being asked to update and install the older version, is there anything wrong the way i have updated ?
thank you very much

---

### Post by NightwishFan on 2010-03-07
You really should target the whole of lucid, rather than just the kernel. If you would rather stick with karmic, you can:

First ensure you are really running Karmic, and delete the Lucid kernel you have installed, and add a backports PPA with this command.
```
sudo apt-add-repository ppa:guido-iodice/lucid-kernel-for-karmic
```

Then just reload the package manager and run an update.

OR

You could just remove the linux-generic and related metapackages, but this may or may not cause issues with updates. Again make sure that you have at least one kernel if you do this.

---

### Post by ibrahim.k on 2010-03-07
after using this command 
sudo apt-add-repository ppa:guido-iodice/lucid-kernel-for-karmic

I got this 

ibrahim@ibrahim-laptop:~$ sudo apt-add-repository ppa:guido-iodice/lucid-kernel-for-karmic
[sudo] password for ibrahim: 
sudo: apt-add-repository: command not found
ibrahim@ibrahim-laptop:~$

---

### Post by NightwishFan on 2010-03-07
Sorry my friend, it is "add-apt-repository". Typing error.

---

### Post by ibrahim.k on 2010-03-07
this is the output i think there is something wrong with my internet connection right ?

ibrahim@ibrahim-laptop:~$ sudo add-apt-repository ppa:guido-iodice/lucid-kernel-for-karmic
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 33CBAC9E20540CA1848C81826516D5B4666270B8
gpg: requesting key 666270B8 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keyserver.ubuntu.com'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
ibrahim@ibrahim-laptop:~$ 
thnx

---

### Post by NightwishFan on 2010-03-07
Yes, it could not connect to the key server. I am unsure if that is not a global issue since I am running Debian and can not use that command to test it myself.

Check the Software Sources to see if it added anyway. Not having the GPG key just means that you can't verify the files. It should be ok.

---

### Post by ibrahim.k on 2010-03-08
I can't understand if this is good but items in the update manager are still the same


ibrahim@ibrahim-laptop:~$ sudo add-apt-repository ppa:guido-iodice/lucid-kernel-for-karmic
[sudo] password for ibrahim: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 33CBAC9E20540CA1848C81826516D5B4666270B8
gpg: requesting key 666270B8 from hkp server keyserver.ubuntu.com
gpg: key 666270B8: public key "Launchpad guiodickarmic" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ibrahim@ibrahim-laptop:~$

---

### Post by dino99 on 2010-03-08
choose here (at your own risk, maybe some dependecies issues) the kernel you want:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

you have to install 3 packages: *all.deb, header (386 or 64) and image (386 or 64)

386 or 64: is your install 64 bits (64) or 32 bits (386).

---

