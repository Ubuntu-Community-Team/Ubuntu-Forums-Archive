---
title: "Upgrading from Ubuntu 10.04 LTS"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by lincoln6 on 2015-12-09
Hi there,

My laptop runs dual operating systems, Windows and Ubuntu (both have features I appreciate). However, it has recently come to my attention that the version of Ubuntu I'm currently running, Ubuntu 10.04 LTS is hopelessly out of date and in need of an upgrade. Many websites and web services have been rendered inoperable, difficult to access, or for some reason marked as "untrusted" due to decreased compatibility with new software.

Accordingly, I looked up the instructions for upgrading from Ubuntu 10.04 LTS to a supported operating system, which brought me to this page with information on upgrading to Ubuntu 12.04 LTS: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

I followed the instructions up to the point of opening up my Update Manager, at which point, I was presented with the following error message: "Your Ubuntu release is not supported anymore: You will not get any further security fixes or critical updates. Please Upgrade to a later version of Ubuntu Linux."

In other words, I was blocked from upgrading my Ubuntu operating system ... because my Ubuntu operating system is outdated and I need to upgrade it.

I have backed up my Ubuntu data on a flashdrive using Deja Dup, and I'm considering installing the latest version of Ubuntu directly onto my laptop. However, I'm a bit concerned about my ability to restore my current Ubuntu data on a new Ubuntu operating system once installed. I'm also worried that attempting to install a new version of Ubuntu will not overwrite the current, outdated version, but will create a third operating system on my computer alongside both the Windows OS and the old Ubuntu. My poor laptop doesn't have sufficient memory to support the two operating systems currently running on it, let alone a third one.

I am not any kind of a programmer, just someone who likes the Ubuntu operating philosophy and finds its features extremely useful, so a lot of the tips on the main wiki go right over my head. I would greatly appreciate any suggestions in helping me upgrade my Ubuntu operating system.

---

### Post by oldfred on 2015-12-09
Export a list of installed applications as well as all your files in /home. 

If you choose the Something Else install option, you can select the current / (root) partition for the new / and /home if separate partition. It then auto finds existing swap. If /home is a separate partition do not tick the format box and it will just reuse it, update settings and keep all your data. You still want backups.

But how old is system. New version now use Unity which requires a somewhat better system and good graphics. 
My older laptop I did not install Ubuntu but Unity was so slow as to be unusable.  Plus I prefer the older menu system, so I installed gnome-panel or fallback.
Most other users may suggest Lubuntu if an older system.

This is 12.04, but similar with newer versions:
 [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by lincoln6 on 2015-12-10
Many thanks for the advice. Unfortunately, as I mentioned, I'm not a programmer, and I have no idea how to do any of what you suggested there. What tool would I use to export my applications, and under which root menus and sub menus would I find it? Or do I need to do it from a terminal, and if so what code would I launch the exporting tool?

I got my computer used about four years ago, pretty old for a laptop. I keep expecting it to die on me, but it just keeps chugging away. It sounds like I'd be best served by installing Gnome Classic once I figure out how to upgrade my Ubuntu OS; which is fine with me, as it will save me the trouble of having to teach myself another new desktop navigator. Thanks for the tip.

---

### Post by Dennis N on 2015-12-10
You should consider installing Ubuntu MATE. It's desktop is very similar in appearance to the gnome 2 desktop of Ubuntu 10.04, which extends to the menus and settings dialogs and the way they work. You would feel immediately right at home. 

You would be using new versions of your applications that come with it or that you install later, and what you want to do is save your own files first to a flash drive, then write them back.

---

### Post by Dennis N on 2015-12-10
Here is a link to the Ubuntu MATE web site so you can read more, and install the latest version (download link at the top):

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

### Post by oldfred on 2015-12-10
To get list of installed apps:
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

It is just a text list, but very long as it includes all the dependencies. But you may want to houseclean first or manually edit list. Especially if it includes old kernels.

---

### Post by ian-weisser on 2015-12-10
> **lincoln6 said:**
> In other words, I was blocked from upgrading my Ubuntu operating system ... because my Ubuntu operating system is outdated and I need to upgrade it.

Let's rephrase that. You missed the years-long window to upgrade from 10.04 to 12.04. You are not alone. Been there, too.
'Upgrade' is still an option, but is no longer supported and is more difficult than it would have been in, say, 2014. 'Reinstall' is the remaining supported option.

This is a community, and our ability to support every possible upgrade path is simply impossible for volunteers. Therefore, we limit supported upgrades to a few well-tested and published paths. 


> **lincoln6 said:**
> I'm a bit concerned about my ability to restore my current Ubuntu data on a new Ubuntu operating system once installed.
Restoring *data* may or may not be trivial. It depends upon what applications use the data, and how that application may have changed...not the version of Ubuntu.
Restoring *applications* is generally simple...if they are packaged in the newer version of Ubuntu. Happily, that is easy to check.


> **lincoln6 said:**
>  I am not any kind of a programmer
Well, you are about to learn a lot about the inner workings of your system, regardless of whether you wish to.
Do not fear the inner workings. As long as your data is backed up, and you have the proper recovery media, go ahead and play and experiment and break things.

---

### Post by lincoln6 on 2016-02-09
Thank you once again everyone for your replies. I've been away for a while dealing with issues of employment, transportation, and other drama. However, in the intervening time, I've also successfully upgraded to Ububtu 14.04, so that's that taken care of, thankfully. In the end, I was able to enlist the aid of a programmer friend who ended up pretty much doing the work for me, and was able to restore most of my previously saved material with negligible trouble. I'm exceedingly grateful for his help, as I was badly out of my depth with it all.

It seems like I was very unclear with my meaning when I said that part about not being a programmer itself (highly ironic, as we'll see in a minute). Perhaps what I should have said instead is that I'm a complete neophyte at programming. What I intended to convey was that I understand next to no programming jargon whatsoever, and am not already familiar with operations more sophisticated than "open a terminal, write the following string of characters, and press enter." I need to have these things explained to me in the most basic layperson's terms or I'm at a total loss, which sometimes causes issues for me in trying to decipher installation guides.

Fortunately, in this case, it all worked out, and I greatly appreciate everybody chipping in with your advice. It's entirely my fault that I failed to make the nature of my problem sufficiently clear (like I said, ironic given the nature of said problem.)

---

### Post by Bucky Ball on 2016-02-09
Glad you got it fixed. Please see the first link in my signature and mark this old thread as solved, thanks. Good luck.

---

