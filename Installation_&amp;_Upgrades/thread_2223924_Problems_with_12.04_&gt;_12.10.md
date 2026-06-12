---
title: "Problems with 12.04 &gt; 12.10"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Ursus Maritimus on 2014-05-13
Tried to find answers from forums and from google, but didn't get anything helpful. Even I tried some ideas.

Asus x201e kx-179d  Intel celebron 847.

Tried to update 12.04 to 12.10. Was downloading it from the net and then the elec went down.. Went elec came back, I continued download and finished the update.

Since that, nothing hasn't worked, normally. Can't get the sidepanel/software to be seen,  there isn't anything at top corner either. I was able to use terminal, but what I did,  nothing changed. I did find my folders etc, still existing, but pretty hard to get hold anyway.
At software sources>other software, I did got even more confused. Disabled quantal is mentioned 7 times, as well as, medbuntu -ubuntu 12.04 'precise pangolin' disabled on upgrade to quantal.

So, what should I do? Is the upgrade messed up? Any ideas...

Thanks.

---

### Post by sudodus on 2014-05-13
Tough luck :-(

I'm afraid it is messed up. An electric power failure during upgrading to a new version is one of the reasons, why you should always backup your current system or at least your personal files before starting the upgrading.

But 12.10 has passed end of life, so it is a bad choice. Instead you should have waited for the first point release 14.04.1 in August.

In a way you are lucky, that you can use the terminal and read files, so you should be able to backup your personal files :-)

-o-

I suggest that you boot from an Ubuntu install DVD/USB drive and backup the important files to an external drive.

After that you can install/reinstall Ubuntu or consider what version, 12.04 LTS or 14.04 LTS and flavour, standard Ubuntu, Lubuntu, Xubuntu, Kubuntu, Ubuntu Gnome depending on your hardware. So please tell us about your computer, it makes it easier to help.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Ursus Maritimus on 2014-05-13
Asus x201e kx179d 
1.8 G 
Intel celebron (R)cpu 1007u @ 1.5Ghz x 2
32-bit 
Intel HD graphics 
Ieee 802.11b/n

---

### Post by Ursus Maritimus on 2014-05-13
Thanks for the reply and yes, not nice.
I can still see some details : ubuntu 12.10, but fact is, I don't even know why I was doing it.

I can open the folders still, from the desktop (there's 2 folders there), even the wifi goes on automaticly, even I can't get hold on it. Thats why I was wondering, if there's something, which could be done. Or just upgrade the system directly, for some other option.

Backup is good, I agree. But my hd is at Bkk for week or two, until I'll get it.

---

### Post by sudodus on 2014-05-13
It should be possible to run any of the versions and flavours in this computer. But if you play video, a light-weight desktop environment will help, so it is worth trying the medium light Xubuntu and Ubuntu Gnome or the ultra-light Lubuntu. Standard Ubuntu and Kubuntu have more eye-candy.

If you were happy with 12.04 LTS, you can reinstall it and wait until August to upgrade to 14.04 LTS. But you can certainly try 14.04 LTS now, even if it is not fully debugged yet.

---

### Post by Ursus Maritimus on 2014-05-13
I would be happy to be back with 12.04. Is it possible to use the old version (still got that one at usb stick, 9 months old) or do I need new one? Not for sure, how will the www work or how it really should be done command wise, properly..

---

### Post by sudodus on 2014-05-14
All flavours of 12.04 (except Lubuntu) have long time support.

- Xubuntu (and I think Kubuntu) until April 2015

- Standard Ubuntu until April 2017.

---

### Post by Ursus Maritimus on 2014-05-14
Sounds good. Is there any special way, I should make the installation? Any particular commands I should / shouldn't use?

---

### Post by mastablasta on 2014-05-14
you can reinstall (i.e. not format the drive during install). this should just overwrite what you have with fresh 12.04 files and hopefully restore the system keeping the data intact. in theory and often in practice it woks. just in case it is better to create backup0 of personal data files using live session.

you can then add xubuntu-desktop and remove unity -ubuntu desktop (if you wish to have xubuntu). this is done by pasting one long command for example for xubuntu: [http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise)

---

