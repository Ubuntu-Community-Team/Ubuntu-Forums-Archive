---
title: "skype x64"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-09-22
Anyone try installing skype x64 on karmic?  It keeps failing for me.

---

### Post by rtalcott on 2009-09-22
Working fine for me...installed and I have been using it for voice + video.
rt

---

### Post by LKjell on 2009-09-22
use dpkg -i to install. There is a bug if you just click on the deb file.

---

### Post by keenish27 on 2009-09-22
> **LKjell said:**
> use dpkg -i to install. There is a bug if you just click on the deb file.

Thanks so much.  It works now =D

---

### Post by fballem on 2009-09-30
> **LKjell said:**
> use dpkg -i to install. There is a bug if you just click on the deb file.

Could I please have the complete command to install skype - assuming that I'm in the folder where the .deb is located?

Thanks,

---

### Post by Guruji on 2009-09-30
> **fballem said:**
> Could I please have the complete command to install skype - assuming that I'm in the folder where the .deb is located?

Thanks,

```
sudo dpkg -i *.deb
``` 

EDIT:if you have more .deb files in the same folder replace * by the exact name of the skype .deb file

---

### Post by fballem on 2009-09-30
> **Guruji said:**
> ```
sudo dpkg -i *.deb
``` 

EDIT:if you have more .deb files in the same folder replace * by the exact name of the skype .deb file
Thanks - that worked.

---

### Post by Dougie187 on 2009-09-30
Does it still have the same issues that it had in jaunty with pulse?

---

### Post by Merk42 on 2009-09-30
Is this thread referring to 2.0 or 2.1 beta?

---

### Post by rajeev1204 on 2009-09-30
> **Merk42 said:**
> Is this thread referring to 2.0 or 2.1 beta?

2.0 doesnt have an x64 version.

---

### Post by Merk42 on 2009-09-30
> **rajeev1204 said:**
> 2.0 doesnt have an x64 version.

Well that clears that up, I guess I had been using the 32bit version of 2.0 in my 64bit Jaunty.

---

### Post by cszikszoy on 2009-09-30
> **Dougie187 said:**
> Does it still have the same issues that it had in jaunty with pulse?

No, 2.1 beta works very well with pulse audio.  That was actually one of the major features of 2.1, the fact that it now properly works with pulse.

---

### Post by Tibuda on 2009-09-30
> **rajeev1204 said:**
> 2.0 doesnt have an x64 version.

Neither does the new version. The 64bit deb package depends on ia32-libs. This is the last 32 binary in my system. I got 64bit Flash from Adobe Labs. At least it works with Pulseaudio.
```
$ dpkg -I skype-ubuntu-intrepid_**2.1**.0.47-1_amd64.deb 
 new debian package, version 2.0.
 size 19949742 bytes: control archive= 4363 bytes.
      32 bytes,     1 lines      conffiles            
     786 bytes,    17 lines      control              
    9350 bytes,   130 lines      md5sums              
 Package: skype
 Version: 2.1.0.47-1
 Section: non-free/net
 Priority: extra
 Architecture: amd64
 Depends: **lib32stdc++6** (>= 4.1.1-21), **lib32asound2** (>> 1.0.14), **ia32-libs** (>= 1.6), **libc6-i386** (>= 2.7-1), **lib32gcc1** (>= 1:4.1.1-21+ia32.libs.1.19)
 Installed-Size: 25096
 Maintainer: Skype Technologies <info@skype.net>
 Description: Skype - Take a deep breath
  .
  Skype is a little piece of software that lets you make free calls to anyone else on Skype,
  anywhere in the world. And even though the calls are free, they are really excellent quality.
  .
  * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
  * Call ordinary phones and mobiles at pretty cheap rates per minute.
  * Group chat with up to 100 people or conference call with up to nine others.
  * Free to download.
```

---

### Post by patasenko on 2009-09-30
There is no native 64bit skype version yet. 

> Myth: There is a 64-bits version of skype available for download.

No, there is not yet. However, we assembled a "helper" package which will pull corresponding 32-bits libraries. This is made entirely for your convenience, so you don't have to go and hunt for these packages yourself. This brings some compatibility issues with some (especially video) libraries. Check the forum for more details.
We are working on providing a native 64-bits version of Skype
taken from [http://share.skype.com/sites/linux/2009/09/some_explanations.html]("http://share.skype.com/sites/linux/2009/09/some_explanations.html")

---

### Post by Merk42 on 2009-09-30
Well just tried it, doesn't work for me.

I probably have to do some retarded rain dance with PulseAudio or something.

---

### Post by Regenweald on 2009-09-30
Works seamlessly with pulse here. Hoping for a native x64 at some point.

---

### Post by rajeev1204 on 2009-09-30
> **Regenweald said:**
> Works seamlessly with pulse here. Hoping for a native x64 at some point.

A native 64 bit wont show any appreciable benefits over 32 bit anyway,i dont think as of now a voip application will derive any benefits from being native 64 bit,but its a boon that we have a 64 bit package so its easier to install.

But iam wrong probably.Games being 64 bit yes,video audio encoding /ripping yes,but voip no idea.
Maybe someone might shed some light on this advantage for voip.

---

### Post by fballem on 2009-10-01
> **Dougie187 said:**
> Does it still have the same issues that it had in jaunty with pulse?

The 2.1 beta seems to be working quite well - even with pulse.

---

### Post by danwood76 on 2009-10-01
> **rajeev1204 said:**
> 
audio encoding /ripping yes,but voip no idea

Bit of a contradiction there, you of course realise that the VOIP uses an audio encoding and decoding algorithm, so this would mean a sliker app using less recources to do the same job. (though I doubt that coming from skype)

---

### Post by FrancoNero on 2009-10-01
skype beta works fine here on jaunty and karmic (no avatars in jaunty, known issue)

---

### Post by ljrmorgan on 2009-10-01
My only problem with skype on 64-bit is that for some reason the menu that drops down when you click on the icon in the system tray has dark writing on a dark background, and is practically unreadable.

I also had a bit of difficulty getting my USB mic working, though that turned out to be because I had disabled my on-board sound card. It's fine now though.

---

