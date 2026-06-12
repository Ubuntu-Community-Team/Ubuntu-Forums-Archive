---
title: "Four Noble upgrade questions"
date: 2024-10-25
forum: Installation &amp; Upgrades
---

### Post by JamButty on 2024-10-25
Most new LTS upgrades are very straightforward. Noble is definitely not.

1. Why is gedit, the number 1 most popular text editor per inmotionhosting.com/blog/ubuntu-text-editors/
in Jan. 24, on the list for apps for removal in Noble?

2. I was informed that some third-party software had been disabled during the install, but I could "re-enable them after the upgrade with the 'software-properties' tool"
The only 'software-properties' I found on a search at the top of the "show-apps" screen were
software-properties-drivers.desktop
software-properties-gtk.desktop
software-properties-livepatch.desktop

none of which were in any way helpful. It also suggested the 'package manager' which I understood to be Synaptic. Under Synaptic there was no specific subsection for the described situation.
There was "not installed" which was useless as it has thousands of entries.
"Not installed (residual config)" seemed closest and did have 1 third party bit I recognized.
Is there any more direct way to see only those items that correspond to the "third-party software had been disabled during the install" ?

3. At the end just before reboot, it offered to delete unneeded files but warned the process could take hours, so I skipped that. Is there any way to return to that, see what is being deleted and continue that skipped process?

---

### Post by Rubi1200 on 2024-10-25
I can only offer an insight for number 3: in my test upgrade the cleanup did not take hours, perhaps 10 minutes at most. 

I assume they warn it could take hours because some systems may need more work than others.

---

### Post by grahammechanical on 2024-10-25
> 2. I was informed that some third-party software had been disabled  during the install, but I could "re-enable them after the upgrade with  the 'software-properties' tool"

Are you sure the message said: "software" and not repositories?  Yesterday I upgraded an install of 24.04 LTS to 24.10. I forgot to disable some third party repositories that I intended to disable and I got the same message as you did. After the upgrade was completed I checked and the third party repositories had been disabled.

I also think that you will find that "software-properties tool" is developer language for the Software and Updates utility. It has an Other Software tab where we (the ordinary user) can Add; Remove and Edit third party repositories. That is what I used for checking the status of those two third party repositories.

The good news is, you can always ask for your money back. :)

Regards

---

### Post by tea for one on 2024-10-25
> **JamButty said:**
> 1. Why is gedit, the number 1 most popular text editor per inmotionhosting.com/blog/ubuntu-text-editors/
in Jan. 24, on the list for apps for removal in Noble?
I'll have a crack at question 1
Upstream Gnome (The GNOME project) introduced a new default text editor [https://gitlab.gnome.org/GNOME/gnome-text-editor](https://gitlab.gnome.org/GNOME/gnome-text-editor).
Ubuntu 24.04 simply included it. I imagine that the Ubuntu team did not want the extra work of purge and replace with another text editor.
Gedit is still available via the universe repository.
Default applications rarely please 100% of users, but it's pretty easy to find and install a suitable alternative.
For example, I would bet that a majority of Gnome users never use Totem (Videos) and install VLC, Celluloid, SMPlayer, Parole, Kaffeine etc

---

### Post by JamButty on 2024-10-25
1. tea for one -I've been using the new Gnome text editor since last night. Seems fine so far. Initially I thought Gedit was being retired without a replacement. And, guilty, I do use VLC rather than totem.

2.  grahammechanical - Don't think it said "repositories". The four main repositories are all still enabled. The one disabled bit I found thru Synaptic I no longer needed and whatever else got axed is unlikely to be something I use routinely, so I will find out out eventually if any of the bits I use rarely has gone to the great software beyond.

3.  Rubi1200 - I like to unjunk as much as possible, but as long as it does not affect performance, it is not a big issue.

Thanks for the responses!

---

### Post by ian-weisser on 2024-10-25
> **JamButty said:**
> 
2. I was informed that some third-party software had been disabled during the install, but I could "re-enable them after the upgrade with the 'software-properties' tool"
The only 'software-properties' I found on a search at the top of the "show-apps" screen were


I'm very familiar with that notification, as third-party software is the most common cause of broken upgrades.
It said that some third party software *sources* had been disabled. Not the software itself. That's normal during a release-upgrade.
You use the software-properties-gtk (Software & Updates) application to 1) Review if you still need the non-Ubuntu software from that source, and 2) To delete or re-enable the source, as appropriate.

If you don't use the software anymore, then delete the source AND the software. Two different actions.
If you do us the software, decide if you still need it from the non-Ubuntu source. Maybe the Ubuntu repos have the version you want now.

---

### Post by corradoventu on 2024-10-26
gedit has been replaced by gted giving partly same functions but you may easily install also gedit.
The problem usually depends from some software listed in  /etc/apt/sources.list.d/third-party.sources; jou may disable it removing the word beb in the 1st line ... Types: deb

---

