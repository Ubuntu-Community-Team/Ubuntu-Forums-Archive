---
title: "Upgrade 10.04 to 12.04 and keep fluxbox"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by flemur13013 on 2012-04-04
Hi - I have ubuntu 10.04 64bit running fluxbox and would like to upgrade to 12.04 and keep using fluxbox. Mainly I want newer libs so I can use newer versions of apps.

Questions:
1- What's the difference between the "desktop" ISO and "alternative" ISO?
Edit: A: "alternate" assumes you can't run X or a graphical interface w/o some setup.

2 - Will fluxbox run under ubuntu 12.04 as it's installed, or would I have to also install the "classic gnome desktop" (or some such name); I've seen places which claim that fluxbox won't run under the new gnome (=v3?) supplied with 12.04, and other places that say it's no problem.
(gdm+fluxbox is better than lubuntu; fluxbox is easier/better/faster/ smallerfootprint).

3 - what I've read about upgrades says 10.04 -> 11.10 but NOT 10.04 -> 12.04. 
Is that correct? (that to upgrade from 10.04 to 12.04 you have to upgrade from 10 to 11.x first, then 11.x to 12.04).

4 - Is there a way to get a list of currently installed components that were  optionally installed via apt-get/synaptic? (IOW, omit the software installed by default).
Edit: partial A:  $ dpkg --get-selections > list-of-ALL-installed-software

TIA!

---

### Post by zvacet on 2012-04-05
> what I've read about upgrades says 10.04 -> 11.10 but NOT 10.04 -> 12.04. 
 Is that correct? (that to upgrade from 10.04 to 12.04 you have to upgrade from 10 to 11.x first, then 11.x to 12.04).

No,that is not correct,because 10.04 and 12.04 are both LTS so you can upgrade directly from 10.04 to 12.04.If you want to do upgrade your fluxbox should work,because you are upgrading not making new install.
For installed packages witch are not part of default install you will need list of default packages.I don't believe you have it.ypou can get list of all installed packages by running

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

---

### Post by flemur13013 on 2012-04-05
Thanks - 

I discovered that one can theoretically upgrade directly from 10.04 to 12.04, and then discovered that you CAN'T upgrade from the "desktop" install 12.04b CD that I downloaded, so I downloaded the "alternate" (why not give it a decent name that means something, like "non-graphics/upgrade"?) 12.04b install CD....for no apparent reason, because you can't really upgrade from it, either.

I did this ludicrous process to (try to) upgrade from 10.04 to 12.04 using the stupidly named "alternative" CD:

$ sudo mkdir -p /media/cdrom
$ sudo mount -o loop ubuntu-12.04-beta2-alternate-amd64.iso /media/cdrom
$ gksudo "sh /media/cdrom/cdromupgrade"

It then asks me if I want to DL the latest software from the internet: I say "NO" because I know the other, regular desktop CD (that I can't upgrade from) works fine on my system and I'm assuming/hoping that the "alternative" has the same SW that works.

Then it gives error messages and wants to send an error report, which makes firefox say "Invalid OpenID transaction".  Wonderful stuff, so far!  Did the error report get sent?  Who knows. Who cares. (Repeat again, just to make sure).

So I answer, "Yes" to download from internet? and it wants to DL 1.2G of stuff, so apparently the CD isn't used at all and it was just a waste of time downloading either/both of them since I have to DL the whole damned thing **again** (plus 500MB more), which would be the **third time**. So apprently you can't upgrade your OS without internet access.

The **sill****y procedures**, **buggy mickey-mouse software, **but most of all the** truly ****horrible**:lolflag:** documentation **of the silly procedures and the micky-mouse software make me sick of linux...I programmed with C/Unix/Motif for many years and it's really gone downhill since then.

---

### Post by zvacet on 2012-04-05
Few releases ago desktop CD support upgrade.I didn´t saw it ( it wasn´t displayed) when I need it,but now I can see it.So you will have to be able to upgrade from desktop CD.Alternate CD is made (between other things) for offline upgrades.Maybe problem is because you try to upgrade to beta version and of  course you will get many updates.My suggestion is to wait until and of April ( and maybe few days after that) and then try to upgrade to stable release.

---

### Post by flemur13013 on 2012-04-05
After spending about 1.5 hours downloading 1.2G of stuff that should've been on the install/update CD, in the wanky little user-hostile too-small non-resizable installer window I got these love notes:

Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/a/alsa-lib/lib32asound2_1.0.25-1ubuntu10_amd64.deb Wrong CD-ROM
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/e/eglibc/libc6-i386_2.15-0ubuntu6_amd64.deb Wrong CD-ROM
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/f/fakeroot/fakeroot_1.18.2-1_amd64.deb Wrong CD-ROM

What a load of crap. And there's 1.2 G of that crap on my disk somewhere (not in /tmp) after the installer failed.

Edit: And those smiley faces automagically appeared from a cut/paste of error message text!  (smiley face was merely the text "2 8 )", w/o spaces, following the 201...)

So, yet more buggy/klugey software, probably on the linux system that runs this website.  I'll be surprised if I don't go back to Windows fulltime after this bs since I still have to use it for graphics and video.

---

### Post by flemur13013 on 2012-04-05
After a reboot the 1.2 G of crap is still there...somewhere. And synaptic and apt-get are now broken because of the failed upgrade.

So, back to Win7 (w/blackbox, of course) where you don't have to (attempt to) upgrade the entire system just to upgrade some crummy backup software (the user-hostile grsync, which would regularly hang and crash and make Xorg use 50% CPU. Check out "Vice-versa", windows backup SW to see what you're missing: it's got a REAL GUI!). I was running windows graphics and audio software thru wine anyway (photoshop, audition, iview and foobar)  because the best comparable ubuntu/linux apps are so terrible.  And yes, ext4 filesystems fragment, probably just as much as NTFS filesystems.

Have fun!

---

### Post by andrew.46 on 2012-04-05
> **flemur13013 said:**
> Edit: And those smiley faces automagically appeared from a cut/paste of error message text!  (smiley face was merely the text "2 8 )", w/o spaces, following the 201...)

Just below the Submit button there is an option to disable smilies.

---

