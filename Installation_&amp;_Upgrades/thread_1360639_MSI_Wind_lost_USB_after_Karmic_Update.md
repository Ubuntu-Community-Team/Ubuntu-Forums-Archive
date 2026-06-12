---
title: "MSI Wind lost USB after Karmic Update"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by bobbiescap on 2009-12-21
I Bought a U100 a while ago and put Ubuntu on it and have been very happy with it until a few days ago when I did some updates to Karmic and lost all my USB devices, including the integrated web cam and card reader.

It is a real pain because I have gone on holiday for a few weeks and accidentally left my install disc at home and the only internet access I have is a Huawei HSPDA modem which I am currently using on a borrowed Vista laptop because the Wind doesn't load it.

I can boot from a USB optical drive or flash drive so the BIOS is seeing them but not Ubuntu.

I have searched my fingers off on a painfully slow connection and found references to this problem but nothing in depth and no solutions, which I really need. I do not have the bandwidth to download an install CD but can probably grab some packages, if required.

I am really hanging out for somebody to supply a fix for this.

---

### Post by hansdown on 2009-12-21
Hi  bobbiescap.

You are not alone.

I came across numerous posts, mostly u100s, and a couple other netbooks.

A bug report was also found, so an update will likely appear soon.

---

### Post by bobbiescap on 2009-12-21
Thank you, I will sit on my hands until a solution comes out, just frustrating because of the situation I am in as I have a website to maintain and have all the data on the netbook. 

Going to go out later and see if I can find a Linux magazine with a copy of Karmic and I will just not update it as it worked fine until updates. I notice with other posts that the issue occurred with the upgrade from Jaunty but not so in my case.

I am getting over these strict release cycles where multiple issues often occur, I am going to have to curb my addiction to latest and greatest and stick to the next LTS version. Ubuntu has been making huge progress in bring Linux to everyday computing but is damaging itself by the Windows-esque practice of releasing operating systems with known bugs.

I applaud the efforts of everybody involved in this fantastic resource but on the subject of release dates lets get it right people, even if it is a couple of months late, people will cry less with that approach than with having dead systems after upgrades.

---

### Post by hansdown on 2009-12-21
I recently gave my U100 to a friend. I had 9.04 running very well.

Best of luck to you.

---

### Post by kstella on 2009-12-24
Oh no! :( I wish I'd known this before I upgraded. I found out just after I tried taking a picture with Cheese.

@hansdown, was USB working?

---

### Post by hansdown on 2009-12-24
Hi kstella.

USB seems to be working good.

---

### Post by kstella on 2009-12-27
Sorry, hansdown, I got confused. I thought you were talking about karmic (9.10).

bobbiescap, there's a temporary solution to the USB problem, though you might not like it; it entails disabling the webcam.

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Add "blacklist uvcvideo" to a new line at the very end, then save. [(Here's the post on launchpad where I found the solution.)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408/comments/19")

Do this, then reboot. After that, you'll be able to use USB and the card reader, though you won't be able to use the webcam.

I hope we Wind users won't have to wait till Lucid for the developers to fix this, and the brightness problem too. Still trying to figure the latter one out.

---

### Post by hansdown on 2009-12-27
Nice work kstella.

I haven't been able to keep up with the U100 stuff after giving mine away.

---

### Post by bobbiescap on 2010-01-06
Hi folks,
Sorry I have not replied before this, I am on holiday with my kids and not checking in too often.

I came away without my Karmic disc but bought a mag with a Jaunty remix on it with KDE 4.3. I loaded it and got USB back but then had issues with KDE, my wm of choice, so decided to bite the bullet and upgrade to Karmic and all works perfectly now so maybe the USB issue has been resolved.

I really love the little Wind and could not go back to a full sized computer for day to day computing, it does most things I want including basic graphic design and it has forced me to become less dependent on Photoshop and more adept with GIMP. The only letdown is the touchpad and I will probably install a Synaptics this year.

Hope you all had a great Christmas and New Year and that 2010 brings you what you are looking for.

---

### Post by hansdown on 2010-01-06
Happy new year bobbiescap.

The touchpad is hard to get used to. I used a usb wireless mouse.

Glad it's working better for you.

---

### Post by saleminkb on 2010-03-25
I'm using lucid UNR beta on a MSI Wind and the issue with USB/Webcam seems to be fixed.

---

