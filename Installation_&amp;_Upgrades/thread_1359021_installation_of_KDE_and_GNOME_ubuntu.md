---
title: "installation of KDE and GNOME ubuntu"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by pushkar_k on 2009-12-19
I have kubuntu installed on my PC and I want to install both KDE and GNOME on my PC. The usual method requires some packages that are downloaded from internet . However my internet connection has limited downloading so I can't use that option. I have cds of both ubuntu and kubuntu. Is there a way to install both KDE and GNOME sessions of ubuntu using those cd's ?

---

### Post by lemming465 on 2009-12-20
Depends on which CD's they are.  The live CD's work by cloning their pre-installed filesystems, so a live ubuntu CD can't usefully modify an already installed kubuntu system.  However, the *alternate install* CD's work in the traditional debian manner using archives of package files.  If you have the ubuntu alternate install CD, register it using *apt-cdrom add* (which adds it to /etc/apt/sources.list as a repository), and then do *aptitude update; aptitude install ubuntu-desktop*, perhaps with the network disconnected.

---

### Post by pushkar_k on 2009-12-21
> **lemming465 said:**
> Depends on which CD's they are.  The live CD's work by cloning their pre-installed filesystems, so a live ubuntu CD can't usefully modify an already installed kubuntu system.  However, the *alternate install* CD's work in the traditional debian manner using archives of package files.  If you have the ubuntu alternate install CD, register it using *apt-cdrom add* (which adds it to /etc/apt/sources.list as a repository), and then do *aptitude update; aptitude install ubuntu-desktop*, perhaps with the network disconnected.


thanks a lot :).
actually I don't know what a live cd is , but both of the cds I have are downloaded from Internet from ubuntu and kubuntu sites . I will try to do using apt-cdrom add. thanks.

---

### Post by lemming465 on 2009-12-21
I guess this week the terminology at a typical [download mirror sites]("http://releases.ubuntu.com/karmic/") is *desktop* CD or image.  Short version: if your CD boots to a GUI desktop, it's the wrong flavor.  It's the "alternate install CD" flavor which can allow *upgrading from older installations without network access; *.  This is only a difference in initial distribution style; once installed, all ubuntu and kubuntu variants are basically the same.  They differ only by which subset of the roughly 19,000 debian packages are actually installed.  Admittedly, this can be a very great difference!

---

### Post by pushkar_k on 2009-12-21
ok, then I have desktop CD and hence there's no way to install both KDE and GNOME ubuntu without network access. anyway **thanks** for letting me know this.

---

### Post by lemming465 on 2009-12-21
If you don't have the network bandwidth to either download "ubuntu-desktop" yourself, or the "alternate ubuntu installer" CD ISO image, your next best option is a friend with more bandwidth.  It should also be possible to [get Canonical to ship you one of the alternate installer CD's for free]("https://shipit.ubuntu.com/specialrequest").  Be sure to ask for the "alternate ubuntu" CD, as by default they'd want to send you a desktop CD, which you already have, and which won't help.  Or for a small fee there is usually a business somewhere who can burn and mail one to you.

---

### Post by pushkar_k on 2009-12-22
ok , thanks. I tried to get cd shipped by cannonical from the link given by you, bt there is no option to specify type of cd we want. The form for special request includes quantiy required and reason for that. So, I will try to get the cd from some friend . Is there specific link for the alternate cd ?

---

### Post by lemming465 on 2009-12-22
If you use the canonical special request form, there is a box for your reason.  I'd request quantity 1 and just note that you need an ubuntu alternate install CD due to lack of bandwidth to download it.

---

### Post by pushkar_k on 2009-12-22
ok. I asked for link because it would be lot better to get cd downloaded from my friend than to have Canonical bear unnecessary expenses for that . So , if there is no way to download alternate install cd I would go for shipping request.

---

### Post by jimbojones666 on 2009-12-22
I just Installed Ubuntu Ext4 and it seems to have GNOME as my desktop. Just wondering if it's worth it to switch to KDE? Or any other one, if they're better. Total noob with Ubuntu, btw.

---

### Post by pushkar_k on 2009-12-23
> **jimbojones666 said:**
> I just Installed Ubuntu Ext4 and it seems to have GNOME as my desktop. Just wondering if it's worth it to switch to KDE? Or any other one, if they're better. Total noob with Ubuntu, btw.

ya totally. KDE uses same base system but its GUI is very different and its really awesome. Just watch screenshots of kubuntu which is ubuntu with KDE . To get KDE you just have to download some packages . The name of package is kde-desktop or something. To find out exact name , go into help of ubuntu and search "KDE". You will get name of package there. And then you can download required packages from Internet . After downloading you can select either GNOME or KDE for each log in sessions , so you can have both of them. Its really worth to use KDE. I use kubuntu 9.10 which has some more features than 9.4. You can find out more about KDE from experts .

---

### Post by lemming465 on 2009-12-23
Pushkar_k is right; Gnome versus KDE is not an either-or choice.  If you install the "kubuntu-desktop" package on top of an ubuntu install, which I often do, your login screen will give a choice of which kind of session you log into.  You can use either gdm or kdm as the login manager, then either KDE or Gnome as the window manager (aka session, meaning look & feel), then either KDE or Gnome applications.  They play fairly nicely with each other these days, due to the standardization work of those nice folks at freedesktop.org.

Try it and see what you think.

---

### Post by pushkar_k on 2009-12-23
I have heard from my friends that the latest versions of cds that are shipped on request contain both GNOME and KDE. Is that true ? Is there way to find that out from cd before installation ?

---

### Post by lemming465 on 2009-12-24
No, the CD's are strictly based on a single window manager and its favorite applications, e.g. Gnome-based ("ubuntu") or KDE based ("kubuntu").  They don't have room for both.  Even the larger DVD's don't have full sets of both.

You can tell what a running system has (including a memory-only desktop live CD you booted) by running *dpkg-query --list*.

To see what is included in a CD or DVD ISO file you are contemplating downloading, start at the [ubuntu complete download page]("http://www.ubuntu.com/getubuntu/downloadmirrors"), pick your favorite nearby high-bandwidth mirror site, and get the *manifest* file.  E.g. for me a good choice is Argonne Labs in Illinois USA; to see which packages are in the AMD-64 live desktop CD I'd download [this]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/9.10/ubuntu-9.10-desktop-amd64.manifest").

---

### Post by pushkar_k on 2009-12-24
thanks a lot. Actually the cd that my friend has got has both kubuntu and ubuntu logos on it. That's why I asked about it. Thanks.

---

