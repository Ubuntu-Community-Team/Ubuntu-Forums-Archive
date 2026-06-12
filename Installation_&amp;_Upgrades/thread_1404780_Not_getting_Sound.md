---
title: "Not getting Sound"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by karumudi7 on 2010-02-11
Hi I am not getting sound in APPS like VLC,Skype etc;
But I am getting sound from Kubuntu default Apps Amarok,Dragon player..

Why it is, getting only from Default Apps?

The same MP3 file is played in Amarok and in VLC latest ver 1.0.5, but sound is from Amarok, same with dragon player.

---

### Post by khelben1979 on 2010-02-12
Applications which uses the KDE sound server give you sound where the other ones might be using other sound settings.

Does your computer have a sound chip on the motherboard + installed sound card? If the sound chip is used as default sound you won't hear any sound from the sound card.

---

### Post by dabl on 2010-02-12
```
sudo apt-get install --reinstall pulseaudio
```

```
sudo apt-get install pavucontrol paman
```

Then Alt-F2 "pavucontrol" and look at the outputs -- look for anything muted.  When everything looks right, KMenu > System Settings > Multimedia, and review the sequence of devices.  Use the "test" button to check.  If the top device does not make a sound when you press "test", try the next device on the list.  If a device down the list plays the tune, then move it up to the top of the list.

If you play around with the devices in the "Multimedia" list, and also pavucontrol, you should get all items playing correctly.

---

### Post by karumudi7 on 2010-02-12
> **khelben1979 said:**
> 
Does your computer have a sound chip on the motherboard + installed sound card? If the sound chip is used as default sound you won't hear any sound from the sound card.


I dont know correctly abt sound card but I am using DELL LAPTOP I generally used Sigmatel Audio Driver to instal Sound driver in Windows. How can we chk?
but in previous i used Ubuntu Jaunty,Hardy. There i got sound in other apps also. But now in kubuntu the prob arised.

---

### Post by karumudi7 on 2010-02-12
> **dabl said:**
> ```
sudo apt-get install --reinstall pulseaudio
```

```
sudo apt-get install pavucontrol paman
```

Then Alt-F2 "pavucontrol" and look at the outputs -- look for anything muted.  When everything looks right, KMenu > System Settings > Multimedia, and review the sequence of devices.  Use the "test" button to check.  If the top device does not make a sound when you press "test", try the next device on the list.  If a device down the list plays the tune, then move it up to the top of the list.

If you play around with the devices in the "Multimedia" list, and also pavucontrol, you should get all items playing correctly.


Thanks man Its working now,Recording device is also working fine!
Thank U!

---

