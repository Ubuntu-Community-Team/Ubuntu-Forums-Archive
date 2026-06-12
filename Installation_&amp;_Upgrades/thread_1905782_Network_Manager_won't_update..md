---
title: "Network Manager won't update."
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by landstander on 2012-01-07
Specs:
------
OS: Ubuntu Lucid 10.04 (LTS) 64bit
PC: ASUS EeePC netbook 1005PR
Mem: 2GB

The problem (in short):
-----------------------
The update manager returns to the update screen with all the same updates listed after selecting "install updates".

The problem (in detail):
------------------------
When selecting the update manager icon from the panel, it starts up and lists a bunch of security updates. When "install updates" is selected it asks for the administrative password. After entering my password a small window appears that states "reading package information", when this is done the "reading package information" window goes away and nothing else happens. What should happen is that it should install the files listed and then report that the computer is up to date. What happens instead is that the same list of files are shown in the update manager window and we are back at square one.

Things I've tried in order to fix the problem:
----------------------------------------------
typing from the command prompt:
sudo apt-get update
sudo dpkg --configure -a

I've also tried rebuilding the /var/cache/apt/archives directory by deleting its contents and repeating sudo apt-get update

I've tried updating using synaptic but it shows that no updates are available which is strange since the update manager seems to think there are updates available.

Questions:
----------
How can this problem be fixed? Is there anything else that can be done to solve the problem?

Thank you for your time.

---

### Post by zvacet on 2012-01-09
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by landstander on 2012-01-09
zvacet,

I could have swarn that I tried that already but I guess I didn't because it worked. So why wouldn't the update-manager perform the update && upgrade when I clicked "install updates"? Is this a bug in the update-manager, or did I forget to re-enable something someplace in its settings, or is it something else?

Thank you again for your help.
Before I mark this thread as solved I would like to wait for a reponse to the above questions so the problem can be prevented from reoccuring.

---

### Post by raja.genupula on 2012-01-10
1st its looks like as a BUG . have you tried **re installing** update manager from Synaptic ? 

Give a try and one more thing is from synaptic look for the current installed version of the update manager and download the previous one from Ubuntu packages (google will help you) and install it after removing the current.

1st do reinstallation of current one and if it wont work then go for the second one i told you. 

All the best.

---

### Post by landstander on 2012-01-10
Thanks for the encouragment raga.

When the problem was still happening I did reinstall the update-manager, but that did not fix it. So I did as zvacet suggested and just ran the update && upgrade from the command line which worked fine.

However it is still unclear why the update-manager behaved the way it did and since the problem is no longer happening I can no longer bug test it any further. Has any one else had this problem? Is it a bug? I guess I could look it up but I'm to busy to do that.

*shrug* oh well. I guess I'll just mark it as solved until it happens again.

---

