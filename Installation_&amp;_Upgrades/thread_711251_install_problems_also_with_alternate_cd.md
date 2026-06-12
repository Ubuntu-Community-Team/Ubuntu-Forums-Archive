---
title: "install problems also with alternate cd"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Toneri on 2008-02-29
I have P35 based mobo, q6600 and yippee... a 8800GT which seems to be just the wrong combo in trying to install ubuntu.

With live cd I got to the blank screen part some others seem to be getting to also... after that nothing happens.

When looking for answers here, I was guided to try alternate install with it's text based installer to get around the problems.

Now, with alternate cd I get to the point where I should partition my drive. Problem is that the installer finds only my primary sata hd which I have my Vista in. The smaller sata hd which I have reserved for ubuntu, is not in the list. Bios and m$ products have no problems in finding the hd in question.

Any suggestions how to get the installer to find my hd?

---

### Post by dstew on 2008-02-29
It might be related to the Ubuntu driver not able to access the drive. [This thread]("http://ubuntuforums.org/showthread.php?t=707918") discussed a similar problem, with an installed system.

You might try the [gparted live CD]("http://gparted-livecd.tuxfamily.org/") and see if that can see your drive. If it does, you can partition it with gparted. They try your install disk and see if it works.

---

### Post by Pumalite on 2008-02-29
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Report back

---

### Post by Toneri on 2008-03-01
> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Report back

did... twice already. The Gparted live cd refuses to run on every option. I'm downloading the image the third time and if it's still the same, I'll try to get help from their forums first on that and get back here after that...

---

### Post by Toneri on 2008-03-01
yup,

Gparted didn't run and by their forum help I tried partedmagic which had worked on some computers gparted didn't run... But not on this comp because it also refuses to start.

Every other option I've found includes this and that command prompt switching which I'm not keen to try out.

If there are no alternate solutions to this alternate solution I guess I'll give linux another try when next bigger release of ubuntu comes out.

---

### Post by Pumalite on 2008-03-01
Did you try Gparted with the 'Force Vesa? option?

---

### Post by rustygates on 2008-03-01
I had the same proublem with 7.10 one one pc it works fine on this one I never could get all the way threw the instal. the live cd would not load.. So what I have done is use 6.06.1 it loaded the live cd and instaled without a flaw, what I would suggest in your case is try the 6.06.1 live cd. ubuntu is a great my wireless even worked.. although I did have to disable ipv6 and set the priorty high on firefox to be able to surf the net. let me know if it works.

---

### Post by Toneri on 2008-03-02
thanks for the suggestions guys.

I'll give gparted another go (though I do recall already trying every option with it but was so plastered fri evening that I need to recheck ;)

If that does not work, I'll try 6.06. One n00b question on that though. If it installs, do I miss anything that comes with 7.10 or does the 6.06 update on every part that it is practically same as 7.10?

---

### Post by Toneri on 2008-03-02
Okies...

Writing this now from my fresh instal of 7.10 :)

Observations:
- On my mobo (MSI P35 Neo Platinum) there are two sata controllers. The Marvell controller on which I have my Vista HD on, was found by the Alternate install, but the hd on other controller was not.
- When trying out gparted and partedmagic and both of them also refuse to start, I went to the bios and started fiddling around with some settings.
- After changing the 2nd sata controller mode from IDE to ACHI, even Vista found another SATA RAID controller
 -> then went on trying the alternate install cd again and IT FOUND BOTH DISKS this time.

After installing the OS I tried the gparted disk again and it still does not work but no worries since at least the os install worked.

thanks for everyone for your help.

Now to work on the next problems:
 - Why the boot loader does not work (need to force boot to linux)
 - Why the envy's nvidia control panel does not provide proper resolution...

...and many many more I suppose, but that's normal ain't it ;)

---

