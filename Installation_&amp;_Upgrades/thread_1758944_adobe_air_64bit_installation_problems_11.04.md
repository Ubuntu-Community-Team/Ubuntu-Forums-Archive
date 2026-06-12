---
title: "adobe air 64bit installation problems 11.04"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by slammer on 2011-05-15
i am trying to install adobe air on ubuntu 11.04 64bit. the AdobeAIRinstaller.bin fails with:

"An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator."

Obviously i am running it as root, there is no output in the terminal.

i have tried the .deb version with --force-architecture but that failed with dependency problems:

"dpkg: regarding adobeair.deb containing adobeair:i386, pre-dependency problem:
 adobeair:i386 pre-depends on lzma | xz-utils
dpkg: error processing adobeair.deb (--install):
 pre-dependency problem - not installing adobeair:i386
Errors were encountered while processing:
 adobeair.deb"

i installed xz-lzma and got yet more dependency issues:

"dpkg: dependency problems prevent configuration of adobeair:i386:
 adobeair:i386 depends on libgtk2.0-0 (>= 2.6).
 adobeair:i386 depends on libxslt1.1.
 adobeair:i386 depends on libxml2.
dpkg: error processing adobeair:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobeair:i386"


so i searched and found instructions to make it a 64bit .deb, this now fails with this error:

"dpkg: error processing adobeair_64bit.deb (--install):
 adobeair: 1:2.6.0.19140 (Multi-Arch: no) is not co-installable with adobeair:i386 1:2.6.0.19140 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 adobeair_64bit.deb"

which seems to suggest the 32bit is already installed, however, dpkg -r reports:

"dpkg: warning: there's no installed package matching adobeair"

even though it tab completes adobeair.

I am at a loss as to what to do next. Any help would be very much appreciated. Thanks.

---

### Post by lechien73 on 2011-05-15
Have you tried following the instructions here:

[http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html)

I presume they would be similar for 64-bit 11.04.

---

### Post by slammer on 2011-05-15
> **lechien73 said:**
> Have you tried following the instructions here:

[http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html)

I presume they would be similar for 64-bit 11.04.

Thankyou for your response. I have worked through that guide and now the installer.bin doesn't even try to install, it gives a warning that it is not compiled for 64bit but should work and links back to the adobe website (which also doesn't work). 

I get these errors in the terminal:

./AdobeAIRInstaller.sh 
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgiozeitgeist.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiozeitgeist.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
root@Satellite-A300:/media/downloads/linux software# ./AdobeAIRInstaller.sh 
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgiozeitgeist.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiozeitgeist.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

It has made no difference to either of the .deb files.

---

### Post by mikefreeman on 2011-05-16
I am in exactly the same spot as the original poster. I've done all steps mentioned here (and then some - I found some Adobe AIR related files in various places and deleted them by hand, which may have been a bad idea, and this did not help the problem at all). I cannot get past this co-installation error with the .deb file, nor can I get the .bin to install, as gives me an error suggesting I don't have permission (even when I use sudo).

My thinking is that one of the install attempts created files or a file entry somewhere (something akin to a Windows registry?) telling the base system it is installed, but since the error occurred, it was not completely installed, so it isn't recognized as an installed package by apt or synaptic.

I wish Adobe would just make a 64-bit package. How hard could it really be? Sheesh!

---

### Post by Hyperion_1984 on 2011-05-18
I have the same problem here. I've also tried to install adobe air through a ppa ([https://launchpad.net/~dajhorn/+archive/adobeair](https://launchpad.net/~dajhorn/+archive/adobeair)) without success.

---

### Post by slammer on 2011-05-18
> **Hyperion_1984 said:**
> I have the same problem here. I've also tried to install adobe air through a ppa ([https://launchpad.net/~dajhorn/+archive/adobeair](https://launchpad.net/~dajhorn/+archive/adobeair)) without success.

I also found that repo but it doesn't have any version for Natty 11.04. It would seem it is possible to install, here is a google cache of someone that claims to have achieved it:

[https://webcache.googleusercontent.com/search?q=cache:_ANdG7G7sbEJ:www.zubon.org/log/591&hl=en&client=ubuntu&hs=Rik&gl=uk&strip=1](https://webcache.googleusercontent.com/search?q=cache:_ANdG7G7sbEJ:www.zubon.org/log/591&hl=en&client=ubuntu&hs=Rik&gl=uk&strip=1)

It would seem we just need to know how to clear the 32bit version from dpkg, anyone any ideas?

---

### Post by slammer on 2011-05-18
With the help of someone elsewhere I have removed the rogue package with this:

sudo dpkg -r adobeair:i386

The 64bit deb now installs!!! Tweetdeck still doesn't install, which may be to do with 64bit flash but i don't really care now at least i have removed the issue with dpkg.

---

### Post by Hyperion_1984 on 2011-05-19
Wow! Thanks Slammer, it works!

Still, can you explain what was wrong?

---

### Post by slammer on 2011-05-19
> **Hyperion_1984 said:**
> Wow! Thanks Slammer, it works!

Still, can you explain what was wrong?

Thanks but I can take no credit for it, I got the information from someone on another forum. It does seem that dpkg was confused with the i386 package, thinking it was installed when it is not, this command removes any reference to it, if you look at the terminal output it mentions something along those lines. I even got tweetdeck working eventually - it doesn't support anything but gnome or kde, i am using openbox, for anyone with the same problem this:

export GNOME_DESKTOP_SESSION_ID=1

or this:

export KDE_FULL_SESSION=1

in a terminal (or better in ~/.config/openbox/autostart.sh) allows it to work.

---

### Post by Hyperion_1984 on 2011-05-20
I think you can now comment this thread as "solved"

---

### Post by slammer on 2011-05-20
> **Hyperion_1984 said:**
> I think you can now comment this thread as "solved"

thanks, i was wondering how to do that?

---

### Post by tim.hoeffel on 2011-07-15
[QUOTE=slammer;10833279]With the help of someone elsewhere I have removed the rogue package with this:

sudo dpkg -r adobeair:i386


I've following this thread and trying to keep up. I have the air.deb file, and ran the line above from terminal but got this message: 

"dpkg: warning: there's no installed package matching adobeair:i386". 

I've tried opening it with the software center, which doesn't work. How do I open it from the terminal? Or is there more?

---

### Post by slammer on 2011-07-15
> **tim.hoeffel said:**
> [QUOTE=slammer;10833279]With the help of someone elsewhere I have removed the rogue package with this:

sudo dpkg -r adobeair:i386


I've following this thread and trying to keep up. I have the air.deb file, and ran the line above from terminal but got this message: 

"dpkg: warning: there's no installed package matching adobeair:i386". 

I've tried opening it with the software center, which doesn't work. How do I open it from the terminal? Or is there more?

Are you trying to install or remove it? This command is to remove it. If you want to install adobe air see this page:

[http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/](http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/)

---

