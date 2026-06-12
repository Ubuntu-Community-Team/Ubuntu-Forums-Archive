---
title: "&quot;make your way to the partition menu&quot;"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by toryst478 on 2005-09-02
hello,
i am trying to do a full install duel boot on my 60 gig hd w/ windows xp. i have navigated the live cd and pretty impressed w/ ubuntu but i cannot find the partition menu during install process.  i have dabbled w/ linux in the past (mandrake) and this is by far the most user friendly distro. i would like to have ubuntu fully installed next to xp and eventually wean myself off of m$.  i have scoured the forums and have learned ALOT!!  however i'll be darned if i can find how to get to the partition menu in the installation cd. thanks in advance for any help.

ps--in my past experiences w/ linux i have found that this is by far the most helpful and polite community IN THE WORLD!!!!!

---

### Post by matthew on 2005-09-02
I seem to recall the installation goes something like this:

Boot from cd and begin installation
After a few moments, you are asked to select your language.
Then you are asked to select a country, with the choices including countries where your language is spoken.
The installer will then ask you for your keyboard layout.
Then it detects some of your hardware, and loads the rest of itself from the CD.
Next the installer will try to detect your network hardware and set up networking
Then you get to partition your disks

If you haven't already seen the wiki page on dual booting, here it is
[http://wiki.ubuntu.com/WindowsDualBootHowTo](http://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by toryst478 on 2005-09-02
[QUOTE=matthew]
Next the installer will try to detect your network hardware and set up networking
Then you get to partition your disks

If you haven't already seen the wiki page on dual booting, here it is
[http://wiki.ubuntu.com/WindowsDualBootHowTo](http://wiki.ubuntu.com/WindowsDualBootHowTo)[/QUOTE]

thank you matthew for the quick reply,
the problem i am having is that during the live install it does not give me the option to partition hd. it autodetects everything and continues to the live installation straight thru to the ubunto main screen. i have tried live-expert (which is a little TOO involved) and the sysrescuedisk w/ qtparted (which freezes my mouse inside the app--i continue w/ kb and freezes entire app).  i have also been to the link you provided and scoured the forums with the same results. it is looking like if i want ubuntu on my box then i have to reinstall xp. if it were just me in the household i would have no probs wiping out windows and keep a dedicated linux box but the m$ addiction is powerful.

---

### Post by matthew on 2005-09-02
Here is another option. This is a pretty old thread, from the previous edition of Ubuntu, but the info will still apply. This is how I installed Ubuntu the first time. Take a look at it.

[http://www.ubuntuforums.org/archive/index.php/t-16353.html](http://www.ubuntuforums.org/archive/index.php/t-16353.html)

In the howto the author tells you to goto [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php) and download and burn a system rescue cd that has a lot of great recovery tools on it, including a disk partitioner. The great thing about this cd is that it is smaller than the Ubuntu live or Knoppix so it's not as long of a download. You can use this to partition your hard drive. Follow the author's instructions slowly and carefully and you shouldn't have any trouble.

I have go to go to bed...I'm exhausted. I'll check in tomorrow. Let me know when you have had a chance to try this out. Hopefully it will work well for you.

---

### Post by menawollas on 2005-09-02
[QUOTE=toryst478]
the problem i am having is that during the live install it does not give me the option to partition hd. [/QUOTE]

I think that might be your problem. You don't install the live cd - cos its designed to run  off the CD!  \\:D/ 

What you need is the install CD  ](*,)

---

### Post by matthew on 2005-09-02
[QUOTE=menawollas]I think that might be your problem. You don't install the live cd - cos its designed to run  off the CD!  \\:D/ 

What you need is the install CD  ](*,)[/QUOTE]
I'm pretty sure you can install off of the live cd, it just isn't as straightforward as from the install cd...like the partitioner thing.

---

### Post by az on 2005-09-02
[QUOTE=matthew]I'm pretty sure you can install off of the live cd, it just isn't as straightforward as from the install cd...like the partitioner thing.[/QUOTE]


No, you cannot.  This is actually a big feature to be implemented in Breezy.  It is called Ubuntu Express and it is coming along....


You need to boot off the installation cd, and not the live cd.

---

### Post by toryst478 on 2005-09-02
[QUOTE=menawollas]I think that might be your problem. You don't install the live cd - cos its designed to run  off the CD!  \\:D/ 

What you need is the install CD  ](*,)[/QUOTE]

wow!! i just found out that this is correct!! i was for some reason under the impression you can do a full install w/ the live cd but the mirror sites do show the different versions.  just shows the importance of reading EVERYTHING lol. thank you everyone for the quick replies and helpful tips. i say again...the linux community is THE most polite and helpful community in the world. very refreshing.

---

### Post by matthew on 2005-09-02
[QUOTE=azz]No, you cannot.  This is actually a big feature to be implemented in Breezy.  It is called Ubuntu Express and it is coming along....


You need to boot off the installation cd, and not the live cd.[/QUOTE]
Ah, okay. My bad.

---

