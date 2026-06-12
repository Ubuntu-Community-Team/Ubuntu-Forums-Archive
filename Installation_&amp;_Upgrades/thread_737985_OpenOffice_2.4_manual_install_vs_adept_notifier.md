---
title: "OpenOffice 2.4 manual install vs adept notifier"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by lovas on 2008-03-28
Hi everyone

After installing OpenOffice 2.4 manually (downloaded, extracted, dpkg-ed all) adept notifier in gutsy keeps me notified all the time about the availability of the "new" version 2.3. Yes, I know it's some beauty spot kind of issue, but it's still annoying.
Also the same happened w 2.3.

Any idea to make the notifier understand it's the newer package? :)

thanks

ps: perhaps there was a topic like this, but i haven't found any useful

---

### Post by Nicram on 2008-03-28
You have to block new version in Synaptic

---

### Post by lovas on 2008-03-31
I've not used synaptic yet...
Is there the same functionality in adept?

---

### Post by Bubba64 on 2008-03-31
Open Office 3.0 will be in Hardy update supposedly in final release but as of now 2.4 is in Hardy beta.
[http://ubuntuforums.org/showthread.php?t=740652](http://ubuntuforums.org/showthread.php?t=740652)

---

### Post by lovas on 2008-03-31
Well, anyway, it's ok (thanks), but seems to be not a solution in this case.

---

### Post by Bubba64 on 2008-03-31
> **lovas said:**
> Well, anyway, it's ok (thanks), but seems to be not a solution in this case.
In this case it may not matter but let people know what distribution your running. There are instruction on this forum as to how to get a direct targz from Open Office in Debian and links to instructions on how to install. Personally I have never been able to get them to work myself. If your willing to upgrade to Hardy either now or on the official release then you can get better versions of OO. I haven't saved the threads on instructions sorry.

---

### Post by lptr on 2008-04-17
Same here after manual installation of .deb package from OpenOffice.org. 

[https://answers.launchpad.net/ubuntu/+question/29777](https://answers.launchpad.net/ubuntu/+question/29777)

If anybody knows, how I can get rid of the Synaptic message in the right lower edge in 'system tray' then please let me know.

Thanks in advance

rob*

---

### Post by calc on 2008-04-17
> **Bubba64 said:**
> Open Office 3.0 will be in Hardy update supposedly in final release but as of now 2.4 is in Hardy beta.
[http://ubuntuforums.org/showthread.php?t=740652](http://ubuntuforums.org/showthread.php?t=740652)

I'm not sure how you came to the conclusion that OpenOffice.org 3.0 will be in hardy from the thread you quoted... and it won't be in hardy. OpenOffice.org 3.0 isn't scheduled for release until Sept 2, 2008 which is shortly before Intrepid (8.10) release.

---

### Post by merike on 2008-05-10
If you are trying to get adept to not upgrade from 2.4 to 2.3 then this did it for me:
```
sudo aptitude forbid-version openoffice.org-base=1:2.3.0-1ubuntu5.4
```
It did remove some packages though:
```
The following packages are unused and will be REMOVED:
  iestonian ispell libcompizconfig-backend-gconf libgnome-menu2 libgnome-window-settings1
```
It keeps adept from marking openoffice packades as upgrade, instead you have upgradable and no changes.

---

### Post by lptr on 2008-05-12
merike, 

thanks for reply.

I tried 
```
 sudo aptitude forbid-version openoffice.org-base=1:2.3.0-1ubuntu5.4
```But sorry to say. Even then Adept tries my manually installed OO 1.2.4 to up/downgrad to 1.2.3.

Adept actualizer tells me 
```
openoffice.org-calc            actualizeable   no change
openoffice.org-draw            actualizeable   no change
openoffice.org-headless            actualizeable   no change
openoffice.org-hypennation       not installed   install
openoffice.org-impress            actualizeable   no change
openoffice.org-math            actualizeable   no change
openoffice.org-writer            actualizeable   no change
```and at the bottom line the excalmation is always there.

```
# apt-get upgrade
...
Reading state information... done
The following pakets are held back:
  openoffice.org-calc openoffice.org-draw openoffice.org-headless openoffice.org-impress openoffice.org-math openoffice.org-writer
0 actualized, 0 new installed, 0 to remove and 6 not actualized.
```How can I get rid of this?

Any ideas?

rob*

---

### Post by thripsi on 2008-05-26
You can use the apt pinning mechanism.
For details see thread: [http://ubuntuforums.org/showthread.php?t=478748]("http://ubuntuforums.org/showthread.php?t=478748")

My /etc/apt/preferences looks like:

```

Package: openoffice.org-base
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-calc
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-draw
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-headless
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-impress
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-math
Pin: version 2.4.0-9286
Pin-Priority: 1001

Package: openoffice.org-writer
Pin: version 2.4.0-9286
Pin-Priority: 1001

```

---

### Post by lptr on 2008-05-26
Thank you. This solved my problem. Exclamation mark is gone now.

---

