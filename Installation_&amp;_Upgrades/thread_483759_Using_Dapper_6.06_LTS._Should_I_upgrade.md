---
title: "Using Dapper 6.06 LTS. Should I upgrade?"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by coolcar on 2007-06-25
Greetings All,

I have been using Dapper Drake 6.06 LTS on my home Desktop for a couple of months now and am very happy using it :p Although I must admit that I still have a XP partition for Itunes etc ;)

I have been thinking of upgrading to Feisty Fawn 7.04 via Edgy 6.10. On the upgrade community documentation I was unable to find the the pros of upgrading, Probably because we as the Ubuntu community are a bit slack on marketing the features of the next release. 

I am a bit undecided :confused: and would like to know if I lose all the browser plug-ins that I have installed. (Actually I am using Firefox 2.04 - thanks to Ubuntuzilla project scripts :KS). The printer drivers, fonts, Adobe etc will they have to be reinstalled ?

I know that I would be having a 3 year support till June 2009 with Dapper 6.06 but if the features and benefits of upgrading are worth the trouble then I might go ahead. Also do I have a rollback option to uninstall the patches?

Thanks, Regards and Best Wishes !

---

### Post by liquidfunk on 2007-06-25
Unless there is something you really need in 7.04 I wouldn't bother. I'm using 6.10 and I'm happy using it, I have no need to upgrade. Although, I am sure the rest will agree, it is better to use the 7.04 disc than to update over the net. Slower to get back on your feet again, but at least you won't run into as many errors.

---

### Post by dfreer on 2007-06-25
All of your browser plugins, along with bookmarks etc will be saved if you keep your ~/.mozilla directory. If you *reinstall*, you will most likely need to reinstall printer drivers, fonts, Adobe etc. If you *upgrade*, you won't need to. However, I would recommend doing a reinstall over an upgrade any day ;)
The only really new features in my mind are newer packages (you could install them manually or add a newer repo just for them), restricted drivers manager (which makes installing an ATI or nvidia card quite a bit easier for new users), the new codec downloader (double-click a file, say mp3, and it will search for the appropriate codec and install it if you wish), and a new theme among others.
Another advantage is a newer kernel, which mean better hardware support (for example, in my hp dv6000 laptop the headphone jacks did not work in ubuntu until feisty came with a newer kernel).

So here's my advice: If you aren't experiencing any problems with your system, don't upgrade. If you ARE having hardware problems, such as hardware not supported by the older kernel, you can try the upgrade to see if your hardware will work.

---

### Post by mosaic2s on 2007-06-25
my question too is same.

running 6.06 quite nicely. have managed to settle some bugs too through documentation provided.

So far I need ntfs read write support that is said to be more stable in 7.04. should i upgrade or clean install?

The CD of 7.04 delivered just now. Many thanks.

---

### Post by liquidfunk on 2007-06-25
Personally I would do a clean install. I've had problems going from 6.10 to 7.04.

---

### Post by Shazaam on 2007-06-25
Why not multi-boot? That is what I am going to do when GG comes out.:D

---

### Post by Pumalite on 2007-06-25
That's the best bet!. Then you can make your own judgement.

---

### Post by andrew.46 on 2007-07-09
Hi,

 Your post scare me a little:

> **liquidfunk said:**
> Unless there is something you really need in 7.04 I wouldn't bother. I'm using 6.10 and I'm happy using it, I have no need to upgrade. Although, I am sure the rest will agree, it is better to use the 7.04 disc than to update over the net. Slower to get back on your feet again, but at least you won't run into as many errors.

as your computer hardware is almost identical to mine!! I also have a Dell GX27 (or 260?) that runs Dapper 6.06 beautifully. I installed 2 x 512 ram sticks, an LG DVD burner onto the base system which I bought from eBay.

 Like you I am staying where I am and waiting for the next LTS in ?2009.

                   Andrew

---

### Post by Rui Pais on 2007-07-09
> **Shazaam said:**
> Why not multi-boot? That is what I am going to do when GG comes out.:D

Another solution is to duplicate the actual installed dapper (make news partitions and copy from a livecd  with ***rsync*** or ***cp -a*** to the new partitions) and then use that copy to upgrade... if Feisty (or GF in future) runs ok you can discard old dapper or keep it as a backup.

---

### Post by Keen101 on 2007-07-09
Waiting for the next LTS release is a neat idea. But, I see no reason not to upgrade. I had some wireless problems that were fixed with 7.04. Although I did have to disable network manager first. (which was not in 6.06) 7.04 seems to have an easier way of installing restricted codecs. In my opinion you have nothing to lose if you decide to upgrade. The longer you wait to upgrade, then when you do want to upgrade you will have to upgrade through 4 or 5 distributions first. It is your choice in the end, but I got rid of my problems when i upgraded. Of course i did loose 1 or two add-ons from firefox, but that is because they were for the old version, and have not been updated yet.


-Good Luck
-Keen101 :)

---

