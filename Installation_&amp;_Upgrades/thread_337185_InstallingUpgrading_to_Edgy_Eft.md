---
title: "Installing/Upgrading to Edgy Eft"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2007-01-12
I have recently got a broadband connection (A Satellite ISP) to upgrade from a dial up connection since cable or DSL are not available in my area.  

I thought, "What better thing to do, than to download the new Ubuntu 6.10 (Edgy Eft) Release.  Only problem is I'm anxious to install it or upgrade but I don't have a CD-R to burn it to. 

I however have a few CD-RW's lying around, only thing is they can only hold up to 650 megabytes. The newest Ubuntu Edgy Eft Release is 698 Megabytes in size.  My Question is as follows:  

Is there a way to Install a Previous release of Ubuntu, Such as Dapper Drake and Mount the ISO in order to upgrade to Edgy Eft?  I do have Dapper Drake CD's and I'm wondering if this is possible.  

Thanks if anyone can let me know:)

Also I'd like to note that upgrading through the terminal is not an option, because my Satellite ISP uses a "Fair Access Policy" which limits bandwidth.  I'm only allowed to download 176 Megabytes, after that my speeds get cut down to that of Dial-Up or Slower, and I mus wait a few hours of not using the internet, before my speeds return to normal.

---

### Post by bscbrit on 2007-01-12
Yes, its quite straightforward.

Install Dapper or an earlier version.  Edit the repos file (/etc/apt/sources.list) and replace every copy of 'dapper' with 'edgy'.  Then the following commands:

sudo apt-get update
sudo apt-get dist-upgrade

If you encounter problems at the very end, check that it has upgraded xorg-server and all the fonts.  Don't know why, but sometimes these are missed.  Install them by name if you encounter a problem.

Finished!  :-)

---

### Post by muffinhead on 2007-01-12
Thanks, I appreciate the help. How big in megabytes is the upgrade exactly? If it is over 176 Megabytes, I won't be able to upgrade using the terminal console Due to my Satellite ISP's "Fair Access Policy".

That's why I asked if there is a command to allow me to mount the edgy ISO, and then upgrade that way, instead of updating using the internet;)

Thanks if you or anyone can help me out with this.

---

### Post by bscbrit on 2007-01-12
I don't know the exact figures - but I suspect that it will be something bigger than the 176 MB limit.  Sorry about that....:(

It should be possible to mount the ISO, but I have never done it this way so I cannot be sure.

---

### Post by muffinhead on 2007-01-12
Thanks, no problem:)  I'll search the forums quickly to see how to mount an ISO, and also see if I can upgrade this way.

---

