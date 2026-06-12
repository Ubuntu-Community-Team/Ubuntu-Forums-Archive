---
title: "Help with Synaptic Package Manager"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by skexsis on 2005-03-10
I have installed the UbuntuLinux (yeah) and configured the network connection.  This is very difficult to grasp if all you know is windows.  Well anyways I cannot figure out how to download and install the latest version of FIrefox and Thunderbird.  I went into the Synaptic Package Manager to download the latest updates, but it will not allow me to do that.  It will list all the packages that have updates but it will not allow me to mark them for download let alone upgrade them.  Please hold my hand and help walk me through this.  Thank you to those who help (in advance).

---

### Post by maruchan on 2005-03-10
What happens when you go to the terminal window and type "sudo apt-get update" and then "sudo apt-get upgrade" ? Try that, then see if you still have the problem.

---

### Post by skexsis on 2005-03-11
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by LongTooth on 2005-03-11
First of all, if your running Warty, you'll have to add the Warty backports listing to your repository source list to upgrade to the latest Firefox 1.0. Do a search on how to add to your repository list. Its easier if you do it via Synaptic. 

Second, if this is a fresh Warty install, and I'm assuming it is because you want to upgrade Firefox, I would suggest you upgrade to Hoary. While not official, in my opinion is ready for use. Here's the steps to do so:

1. Synaptic
2. Settings
3. Repositories
4. Change all Warty to Hoary. 
5. Comment out any added listings you might have added.
6. Reload
7. Mark All Upgrades.
8. When ask use Smart Upgrade
9. Sit back and enjoy.

Reboot your PC or restart Gnome (ALT+CTRL+BACKSPACE)

You'll get the lates available programs. 

Good luck.

---

### Post by Recked on 2005-03-11
when you say change all Warty to Hoary do you mean to manually edit the exiting entries because nothing other than Warty comes up?

thanks

---

### Post by Gary Powers on 2005-03-11
Down load the Unofficial Users Guide here ([http://ubuntuguide.org/](http://ubuntuguide.org/))  and it will give you instructions on updating Firefox.  Same basic process for Thunderbird.

Towards the end of the Guide are instructions on how to upgrade to Hoary and I concur with Longtooth, you might as well get it done.  I have had no problems running it for the past three weeks.

Gary

---

### Post by Recked on 2005-03-11
Appreciate the help. Warty works fine on my older Toshiba 7020CT, but when I tried to upgrade to Hoary from a clean install I had resolution issues that I couldn't resolve so I thought perhaps if I installed Warty again and then upgraded that perhaps I could get the quicker boot etc. of Hoary without the resolution problems.

Is this a possibility?

thanks again

---

### Post by LongTooth on 2005-03-12
Can't comment on the resilution question. But about a month ago, when Hoary was not quite ready, I too did a 'dist-upgrade'. What a mess. This is the steps I took when I upgraded to Hoary. If you are thinking of reinstall Warty, before you do anything at all, change the repositories to read Hoary. Forget about adding any new listings to your repositories. Using Apt-get do apt-get update, apt-get upgrade, apt-get dist-upgrade. With Synaptic, the same steps which are interpreted as: Reload, Mark All Upgrades. When prompted, choose, Smart Upgrade (dist-upgrade). You'll have to reboot. Afterwards you can look into adding Flash, Java, Xmms, etc. In other words, tweaking you system. Good luck.

---

### Post by skexsis on 2005-03-18
I just did a clean install of Hoary and it works just as smooth as Warthog.  Even better it found my wireless card and I was able to configure the network setting better.  I should have done that from the start but I'm always weary of installing betas.  I lot of improvements in Hoary and the install is so much easier.  I install it on 2 of my laptops.  A Panasonic CF-71 and the Casio Casiopedia.  It found are the hardware without a hitch.  I am glad to be getting into the linux scene because Windows posted a letter about discountinuing support for Win98, ME, and Win2000 in June 06.  By then I should be very comfortable with configuring Ubuntu and modifying to my hearts content.

---

