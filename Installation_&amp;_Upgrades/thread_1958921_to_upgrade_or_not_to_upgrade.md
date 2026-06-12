---
title: "to upgrade or not to upgrade"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2012-04-15
Hello everybody :)

Maverick Meerkat is no longer supported, so no more updates for Maverick.
I have asked several times the same question without getting any answer from anyone. 
If I upgrade to Natty (Ubuntu 11) will Natty immediately take on board my printer and scanner
(Brother DCP 350 C and Canon Lide 25) Or will I once more be faced with the hassles and hurdles of searching for the correct drivers?  If so, then thanks but no thanks I will stay with Meerkat.

Thanks in advance for any piece of information concerning updates and drivers.

C.NAUD

---

### Post by Herman on 2012-04-15
You could create a backup copy of your operating system as it is now with Partimage or Clonezilla. Then give upgrading a try and see if it works as well as you would hope. If you're not happy with the upgrade you could restore the backup.

---

### Post by darkod on 2012-04-15
Since you waited so long using 10.10 without upgrading to 11.04, I think it is wiser to try and use 12.04 when it comes out. Back up all your data and do a clean install of 12.04 LTS, not upgrading 3 times version by version.

Also make an image of your current setup and that way you can go back as already said.

---

### Post by christon74 on 2012-04-15
Thanks a lot Herman. I have downloaded 'Partimage'. Problem is I have not yet found the way to launch it. It should be somewhere in 'System'.  The 'search for files' tools does not give any results, no quick launch icon on the desk....
Baaah, after all, Maverick is still in perfect condition.

---

### Post by Herman on 2012-04-15
To start Partimage in Ubuntu try typing 'sudo partimage' on your command line, (terminal),
```
sudo partimage
```You will of course need to be running partimage from a live CD or from a different Ubuntu installation, say in a USB maybe or in a different partition. I like to use the [Parted Magic Live CD]("http://partedmagic.com/doku.php?id=start") for that kind of work.

It's not too hard to use partimage, you use your tab and/or arrow keys to move the selection box around and use your space bar to make a selection. Mostly it has the instructions in it already. 

Here's a link to a nice illustrated step-by-step tutorial: Free Imaging software - [CloneZilla & PartImage - Tutorial]("http://www.dedoimedo.com/computers/free_imaging_software.html") - Dedoimendo

---

### Post by raymondvillain on 2012-04-15
I just upgraded from 10.10 to 11.04 and ALL my printers, desktop icons, links etc. were just where I wanted them.

But for some reason or other I can't seem to get Ubuntu to remember my wireless network WPA/WPA2 password.  Every time I boot I have to type it in before the network connects.

And how are we supposed to use the keyring?  I've not found a use for it, so when it asks me I just click the cancel box.

Good luck.

---

### Post by czgirb on 2012-04-16
> **darkod said:**
> Since you waited so long using 10.10 without upgrading to 11.04, I think it is wiser to try and use 12.04 when it comes out. Back up all your data and do a clean install of 12.04 LTS, not upgrading 3 times version by version.

Also make an image of your current setup and that way you can go back as already said.

Currently, I'm using Ubuntu 10.04.
Previously I wish to upgrade to 11.04 or 11.10.
But I see there are so many people said there is so much problem within *.04 and *.10.
So I burried my wish deeply. Is it allowed for me to upgrade to 12.04 directly?

I hear you said "CLEAN INSTALL" ... why there should be a clean install? since I hear there are so many people said by using Ubuntu, clean install is not required.
Please explain which one is right?

---

### Post by czgirb on 2012-04-16
Double post ... please delete
Thank you

---

### Post by darkod on 2012-04-16
> **czgirb said:**
> Currently, I'm using Ubuntu 10.04.
Previously I wish to upgrade to 11.04 or 11.10.
But I see there are so many people said there is so much problem within *.04 and *.10.
So I burried my wish deeply. Is it allowed for me to upgrade to 12.04 directly?

I hear you said "CLEAN INSTALL" ... why there should be a clean install? since I hear there are so many people said by using Ubuntu, clean install is not required.
Please explain which one is right?

If you are using 10.04 even better because it is a LTS version. The next 12.04 is also LTS and it is allowed to pugrade directly from LTS to LTS. So, you would need to wait until late April (26th, 27th, not sure exactly), for 12.04 LTS to be officially released and you can upgrade directly.

It's better to have a backup any case since any upgrade can go wrong. And it's better to download the image of 12.04, burn a cd, and check if live mode is working fine. If you have problems in live mode, usually you can expect the same problems after you upgrade.

Just make sure you upgrade to 12.04 and not 10.10. In Software Sources, in the Update tab, at the bottom you can set to be prompted only about Long Term Releases. That will prompt you to upgrade from LTS to LTS only, it will ignore releases in between.

---

