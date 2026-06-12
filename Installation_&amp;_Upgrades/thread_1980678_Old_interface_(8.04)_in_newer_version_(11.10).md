---
title: "Old interface (8.04) in newer version (11.10)"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2012-05-15
I'm familiar with using kubuntu  8.04 version and just Installed 11.10 (encrypted, from alternate CD). Now I want to use the old interface (8.04) in the new version (11.10).  I installed gnome something and things screwed up more.   It looks like i will have to reinstal 11.10 (how stupid, but easiest), and need to find a way to add back the old interface from 8.04 .   Thanks in advance for your help.  (very naive user who cares about security/privacy, and simplicity).

---

### Post by SeijiSensei on 2012-05-15
If you're talking about Kubuntu and the KDE desktop environment, the old 3.x KDE desktop is long gone, replaced by KDE 4.  If you want to upgrade, you should install Kubuntu 12.04 since it, too, is a "long-term support" release like 8.04 was.  I'm afraid you're going to be stuck with KDE 4; support for KDE 3 has long since ended.

KDE 4 has no serious security or privacy issues.  It will require that you spend a bit of time getting used to the new desktop, but at base, most of the things you are used to from KDE 3 will carry forward to KDE 4.

---

### Post by spcwingo on 2012-05-15
There's Trinity, which is a fork of KDE 3.

[http://www.trinitydesktop.org/]("http://www.trinitydesktop.org/")

---

### Post by bjngchn on 2012-05-16
Ok, then maybe the only easy solution is get familiar with 11.10.  Konqueror is replaced with: Rekonq Is there a way to disable javascript permanently in Rekonq? Is there a way to remove all search engine references?  What is Adept replaced with in Rekonq?  Is there Klipper alternative in 11.10? (want to remove it).  A few things don't work, and I'm asked to send a bug report. I don't want to send a bug report. A new installation should work without any problems.   Is it important to have support (like LTS?) for normal users? I never needed anything like this. If there is something I don't understand I ask people, search G, or post in forums. If something doesn't work remove or reinstall things.

---

### Post by SeijiSensei on 2012-05-17
Install 12.04 LTS, not 11.10.

I don't use Rekonq or Konqueror; Firefox is one of the first things I install on a new Kubuntu system.  You can certainly disable javascript on Firefox, or install the Noscript add-on to provide more fine-grained control.  Personally I can't imagine trying to navigate web sites without javascript since so many sites expect it to be available.

I have no idea about search engine references.  I can't imagine trying to navigate without Google either.

I presume you can remove Klipper; it's not something I even think about.  I'm pretty comfortable with KDE as it comes out of the box once I've installed a few additional applications like GIMP and SMPlayer.

---

### Post by oldos2er on 2012-05-17
In rekonq, click the settings "wrench" (or spanner, if you prefer), WebKit, untick the 'Enable Javascript' box.

Also in the settings window you'll see 'Search Engines' where you can enable/disable the ones listed.

---

### Post by bjngchn on 2012-05-17
Thanks for answers.  Is there a version of 12.04 with full disk encryption (32-bit and together with an encryption for the home dir)? Is it easy to install (as easy as 11.10)?    If I install 11.10  with f.d.e using alternate CD, and upgrade to 12.04 with Adept equivalent (what is it?), will I keep all encryption, or lose it?  8.04 was more than enough. Just prefer an encrypted disk which is safe against data theft.   What does this say (from [http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download) ): ====== Alternate CD  Also available is the alternate CD. This CD does not include the Live Installer, but instead uses a text-based installer. Download links:      * 12.04 Alternate CD, 32bit     * 12.04 Alternate CD, 64bit ====== What is text based installer, what is live installer? I need guided installer. I'm naive so I can't do anything complicated.

---

### Post by darkod on 2012-05-17
Didn't you said in your first post that you installed 11.10 encrypted using the alternate CD?

Well, that's the same. The alternate cd for 12.04 is the same text based installer. If you did it with 11.10 you can do it with 12.04 the same.

---

### Post by bjngchn on 2012-05-18
Ok installed 12.04 with full disk encyption + home dir encryption.  It looks similar to 8.04 so at first it looks good, but it doesn't work at all:  1. Adept is missing. It is replaced with Muon. When I search Adept I get tons of entries. Search for chess, or game, or firefox; there will be several installable stuff. In Muon almost all searches give empty result. How will I download firefox, and other programs? It is impossible.  2. Search for firefox (left bottom corner). There is only one result: firefox installer. I click on it. in a few seconds it says: installed (or done, or something similar). So I search/browse for firefox. I can't find anything. Nothing happens at all.   3. Using  Rekonq browser I download firefox for linux from Mozilla web site. I extract it with Ark. I see files: firefox, and firefox-bin , among many files. Neither works. Nothing happens. No error, nothing.  4. There is no CD in the laptop. But it makes a noise quite often similar to reading a CD.  I suspect, maybe it is the hard disk running so hard for encrypting things?  (There was no problems with Md5sum or recording to CD.)   I suspect if I can get Adept, all problems will be solved automatically.

---

### Post by SeijiSensei on 2012-05-19
I almost always install from the command prompt with apt-get:

```
sudo apt-get install firefox smplayer gimp
```

for example.

You can also install synaptic if you'd like a more full-featured package manager.  Just add "synaptic" to the line above.

Don't install software like Firefox directly from the coder's site.  It won't be updated automatically the way packages in the repositories are.

---

### Post by bjngchn on 2012-05-19
This command doesn't work anything.  sudo apt-get install synaptic   ........................................................................................................................................................RESULT: Reading packagae lists....Done-------------------------------------- Building dependency tree---------------------------------------------------- Reading state information....Done------------------------------------------- Package synaptic is not available, but it is referred by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. ---------------------------------------------------------------------------- Same happens with:  sudo apt-get install firefox---------------------------- -------------------------------------------------------------------------- If I eliminate Muon will all this nastiness disappear? Why are things made more complicated (for me impossible). Track people better? -------------------------------------------------------------------------- Also want to understand why there is a CD sound when there is no CD. Is it harddisk or does computer not know there is no CD? --------------------------------------------------------------------------

---

### Post by bjngchn on 2012-05-21
Ok, after some help there seems to be no big problems anymore.

---

