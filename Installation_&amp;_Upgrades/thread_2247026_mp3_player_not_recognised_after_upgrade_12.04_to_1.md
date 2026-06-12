---
title: "mp3 player not recognised after upgrade 12.04 to 14.04"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by Norman_Price on 2014-10-05
This problem appeared due to an upgrade:

In 12.04 when connecting my mp3 player (Creative Zen X-Fi), it showed up in Rhythmbox (and could be seen in Nautilus), and in 14.04 it can be seen in Nautilus, but does not show up in Rhythmbox (or any other eg Banshee). From scanning forums I am sure that it is a general problem with 14.04, and not specific to my mp3 player.

Here is what I have tried so far with no change whatsoever:
   ```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
sudo apt-get dist-upgrade
``` &#8230; no change.

   
 Have tried getting latest RB:
  ```
 sudo add-apt-repository ppa:fossfreedom/rhythmbox

  sudo apt-get update
  sudo apt-get install rhythmbox
  sudo apt-get dist-upgrade

```  &#8230; no change


Checked:
```
lsusb
Bus 002 Device 005: ID 041e:200a Creative Technology, Ltd 
```
so the device is there...

but checked:
   

```
 sudo mtp-detect

  Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6

  Listing raw device(s)

 No raw devices found.


```

 Tried:
 ```
 sudo apt-get install mtp-tools mtpfs


```  &#8230; no change

Checked:
```
sudo jmtpfs
Unable to open ~/.mtpz-data for reading, MTPZ disabled.No mtp devices found.
```

In case somebody suggests somehow 'putting the device in MTP mode': 1. There is no menu choice for this on the Creative Zen X-Fi and 2. This was not necessary in Ubuntu 12.04.

I think I lack enough understanding to go further. It is an incredibly annoying fault in 14.04 as Nautilus does not list mp3s with their ID3 info - so choosing files (for me masses of legal podcasts from the BBC etc) is a nightmare.

Thanks for any ideas.

PS:
Suggested from: [http://sourceforge.net/p/libmtp/bugs/968/](http://sourceforge.net/p/libmtp/bugs/968/)
I created a ~/.mptz-data and put this into it: [https://raw.githubusercontent.com/kbhomes/libmtp-zune/master/src/.mtpz-data](https://raw.githubusercontent.com/kbhomes/libmtp-zune/master/src/.mtpz-data)
The device still does not appear in RB - so no change there, except now these run without the irritating error message:
```

sudo mtp-detect
libmtp version: 1.1.6

Listing raw device(s)
   No raw devices found.

sudo jmtpfs
No mtp devices found.

```

---

