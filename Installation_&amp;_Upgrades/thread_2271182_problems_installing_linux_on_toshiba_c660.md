---
title: "problems installing linux on toshiba c660"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by kamal5 on 2015-03-28
hello 
I have a toshiba c660 core i3   4 gb ram which used to run windows 7 till i got a virus few months ago and formatted HDD and from that time I ran lubuntu with no trouble at all .
till recently I changed the LED screen due to a crack in it and it still worked afterwards 
but after an update it stopped working. 

now i can't install ubuntu / lubuntu  / open suse  / fedora ...etc  from usb . 
 even trying ubuntu from usb not working . it freezes after like 20 seconds and computer shows no activity at all. 

the only thing i managed to use is puppy linux it worked but it is so basic and I can't get internet with it. 

i have checked the RAM and it is working fine. 
i erased the HDD with dban before trying to install unbuntu  no  luck .


any suggestions where the problem is ?

ps it freezes with the screen saying lubuntu wiht the flashing stars underneath (loading) then everything halts

---

### Post by ubfan1 on 2015-03-28
Try the ESC button at the flashing buttons and try to get the text screen to appear -- there might be an error message you can tell us about.   Did you ever check the hash of the downloaded ISO?
1) Check the md5sum of the downloaded iso:
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

