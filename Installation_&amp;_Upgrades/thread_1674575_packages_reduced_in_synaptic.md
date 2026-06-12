---
title: "packages reduced in synaptic"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by EthioJOB on 2011-01-24
Hi,

Recently I installed Ubuntu 10.10 on my new PC and hastily installed a packege with  codecs and stuff i found on the net (they were meant for 10.04). I think, though i'm not sure, this has led to the reduction of available packages in synaptic. I cross-checked this my comparing it with the available packages on the live cd. so far no real harm has come, but i don't like it. i want to revert this if possible. i believe it limits my installing options, though i don't have a connection right now. any advice?

---

### Post by mikewhatever on 2011-01-24
This is very vague help request. Do you know that any of the packages are missing? Can you name them?

---

### Post by ajgreeny on 2011-01-24
What was it that you actually installed?

It is hopeless just to say "a package with  codecs and stuff i found on the net" as that tells us absolutely nothing.

Installing a package of some sort will not, or certainly should not, affect the number of packages that are now available to you using synaptic, though it may have been something, eg a script of some sort, that installed packages from the repos without your realising it, thus giving the impression that fewer packages are now needed for your system.

---

### Post by EthioJOB on 2011-01-24
Well the names are not the kind you'd remember easily (lots of lib-, dots, letters and numbers); but for example when i did a search for gimp, it returned with only very few results (interestingly, no packages with the word 'gimp' came up). On the other hand, when i checked synaptic on the live cd, it came with more and sensical amount of packages (and a major one with 'gimp').

One thing I thought peculiar was that most of the packages are marked green (as in installed, i think). This is one of the things that didn't make sense to me. And yes, the live cd's version showed that the majority of available packages were not installed; or at least they weren't marked in green or in any other way.

It could be possible that i've misunderstood something. But as i said, the absence of some packages, at least when i compared them to the live cd, as well as the green markings of the packages somehow point to a minor issue here. 

If you want specific clarifications please ask.

---

### Post by EthioJOB on 2011-01-24
> **ajgreeny said:**
> What was it that you actually installed?

It is hopeless just to say "a package with  codecs and stuff i found on the net" as that tells us absolutely nothing.

The package I installed was *Ubuntu_restricted_Extra_10.04_Offline_Installer_For_Ubuntu_10.04.tar.gz*, though i don't remember from where i downloaded it exactly.

> Installing a package of some sort will not, or certainly should not, affect the number of packages that are now available to you using synaptic, though it may have been something, eg a script of some sort, that installed packages from the repos without your realising it, thus giving the impression that fewer packages are now needed for your system.
As I said i'm not sure that this is the reason in the first place. Its just it, and installing Keryx, are the major activities I did since I installed Maverick. The reasons could be other and/or unrelated. Let's forget the cause for a while. I just want to know what happened to Synaptic's package lists, or at least how to revert it.

Although there was a script - *install.sh*, and its contents was as follows

```
#!/bin/bash
########################################
# This script is to install "UBUNTU_RESTRICTED_EXTRAS_10.04" on Ubuntu 10.04 (along with few more useful packages)
# on a system without internet connection
# Edited for ubuntu 10.04 by an ubuntu user (thanks to hacktolive.org)
########################################

#Initial message
echo "UBUNTU_RESTRICTED_EXTRAS_10.04" offline installer
echo for Ubuntu 10.04
echo
echo by an ubuntu user
echo
sleep 3

#Install packages
echo Please do not interrupt the installer...
echo "Installing Restricted Packages"
sleep 3
sudo dpkg -i packages/*

#Final message
echo
echo
echo
echo
echo
echo
echo
echo The package "UBUNTU_RESTRICTED_EXTRAS_10.04" should now be installed!
echo
echo All packages has been installed! You can close this window now...
sleep 1d
exit
```

---

### Post by ajgreeny on 2011-01-24
Assuming you have internet access, why did you install ubuntu-restricted-extras that way, why not using the repositories in the normal way?

The package you had must simply have been a tarball of the package and all the dependencies of it, ie flashplugin-installer, various gstreamer packages for multimedia, the mstcorefonts, and a few other things.

It will not have affected what is available via synaptic in any way, so open synaptic again and use the refresh button top left to update the database of available packages, and see if that helps.  Gimp should definitely be in the list!

---

### Post by EthioJOB on 2011-01-25
> **ajgreeny said:**
> Assuming you have internet access, why did you install ubuntu-restricted-extras that way, why not using the repositories in the normal way?

The package you had must simply have been a tarball of the package and all the dependencies of it, ie flashplugin-installer, various gstreamer packages for multimedia, the mstcorefonts, and a few other things.

It will not have affected what is available via synaptic in any way, so open synaptic again and use the refresh button top left to update the database of available packages, and see if that helps.  Gimp should definitely be in the list!

Its because I don't have internet access. And you're right, it was a tarball of dependencies, etc. as you said (it wasn't complete tough). I would like to refresh it but as I said, I don't have an internet access. I'm yet to find a workaround to this.

I reinstalled Maverick just in case and the results were the same. It gives you an impression that this is normal, but still as one who wants to understand and use Synaptic I would still like to know why the package list is changed.

---

### Post by poodoopealeoaph on 2011-01-25
Without internet access, you will not have full access to all of the synaptic packages. Usually your lists for synaptic packages are downloaded with your regular updates. So, if you don't have a regular connection, whatever you did may have messed things up slightly. I would try to find a way to connect to the internet, update with your update manager, reboot, then try to check your synaptic while still connected to the internet.

I say this because I couldn't find most of the required packages right after install that I needed. After connecting and updating though, i found that my synaptic had a lot more packages.

P.S.- there is no need for anyone to make someone feel dumb for having an issue with their ubuntu install. So, this just goes out to the other two people that have responded to you. Quit being such douches just because you know a lot about ubuntu. You don't have to constantly try to be so smart that you can't even give a simple answer like I did. People like you guys are the reason why the general public hate the "smart kid" in class. You are basically trying way too hard to be "smart" when all you are doing is just being the complete opposite of helpful by circling the question without actually answering anything.

---

### Post by EthioJOB on 2011-01-25
> **poodoopealeoaph said:**
> Without internet access, you will not have full access to all of the synaptic packages. Usually your lists for synaptic packages are downloaded with your regular updates. So, if you don't have a regular connection, whatever you did may have messed things up slightly. I would try to find a way to connect to the internet, update with your update manager, reboot, then try to check your synaptic while still connected to the internet.

I say this because I couldn't find most of the required packages right after install that I needed. After connecting and updating though, i found that my synaptic had a lot more packages.

P.S.- there is no need for anyone to make someone feel dumb for having an issue with their ubuntu install. So, this just goes out to the other two people that have responded to you. Quit being such douches just because you know a lot about ubuntu. You don't have to constantly try to be so smart that you can't even give a simple answer like I did. People like you guys are the reason why the general public hate the "smart kid" in class. You are basically trying way too hard to be "smart" when all you are doing is just being the complete opposite of helpful by circling the question without actually answering anything.

Well now that makes things more clear. Guess I have to stop worrying about it. My question is - is it normal for package list that appeared in the Live CD not to appear or seem reduced in the installed OS?

---

