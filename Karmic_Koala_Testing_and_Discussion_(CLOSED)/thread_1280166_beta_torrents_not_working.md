---
title: "beta torrents not working?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vkimball on 2009-10-01
I'm trying to download the karmic desktop beta amd64 iso via the torrent.  I keep getting a "not authorized" message.

---

### Post by keplerspeed on 2009-10-01
This file:
[http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-amd64.iso.torrent](http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-amd64.iso.torrent)
Ok I have the same thing "request not authorised for use with this tracker".

Its mentioned here [http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)

So just give it some time, apparently the alternate cd torrent is working fine.

---

### Post by arpanaut on 2009-10-01
[QUOTE=
So just give it some time, apparently the alternate cd torrent is working fine.[/QUOTE]

Yeah Right...
DL torrent file from 5 different mirrors starting from 4:45 PM EST (4hrs. now)
None work... tried DL from utah us site reg. style http and came in corrupted I never have had these kind of problems with DL's for Ubuntu in 5 years... crazy

Unfortunately I am not interested in installing right now just want i-386 desktop live-CD for testing a few dif machines.

Oh Well maybe tomorrow

<biach,piss,whine, moan> LOL

EDIT:  Seems that someone needs to authorize the torrent with the tracker @ ubuntu i.e. [http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)

---

### Post by cariboo on 2009-10-01
I'm currently downloading the desktop torrent. See screenshot.

---

### Post by arpanaut on 2009-10-01
certainly is... 64 bit

got some old machines to see if the lil bear is gonna work on.

not a biggie 

Thanks for the response :-)

---

### Post by nwadams on 2009-10-01
ya, its downloading for me even though it says its not authorized...

---

### Post by cariboo on 2009-10-01
Doesn't everyone use their old 64-bit computers for testing? :)

---

### Post by daas88 on 2009-10-01
I couldn't get the desktop i386 torrent to work... but the alternate i386 is downloading at a nice speed^^

---

### Post by arpanaut on 2009-10-01
> **cariboo907 said:**
> Doesn't everyone use their old 64-bit computers for testing? :)

:lolflag:
Funny Man...

be that as it may
still not working for 386 been sitting like this for hours.
[ATTACH]130444[/ATTACH]

Not important tonite I'm half in the bag and heading for bed soon, Gots one 64 bit lappy, 5 other rigs in various degrees of obsolescence. Alas it's not long before my main home desktop is going to need to be replaced.

Later

---

### Post by jimrz on 2009-10-01
the 386 dvd iso does work, not real speedy yet, though

---

### Post by Druke on 2009-10-01
none of the desktop iso's would DL for me, but the alternative isos worked fine.

I'm installing from those.

---

### Post by ankspo71 on 2009-10-02
Hi,
for those of you in the US trying to get karmic beta desktop 64 or 32, try this link. [http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/) It is my best repo mirror in "software sources". I got mine downloaded at 2 to 2.5mb/s with a direct download. 
Hope it helps.
James

---

### Post by slymi2005 on 2009-10-02
Thanks, this worked for me.

---

### Post by Roger E Critchlow Jr on 2009-10-02
What worked for me was to leave the transmission client sitting with the error from the tracker and go research the problem.  By the time I went back to check, the torrent was 1/3rd downloaded.  It's doing 500 KB/s and should be finished in another 9 minutes.

-- rec --

---

### Post by drumsticks on 2009-10-02
Did anyone compare the MD5SUMs?

The one I downloaded via Torrent is:
```
751d4411029438637f6c6386ac2a6d80 ubuntu-9.10-beta-alternate-amd64.iso
```

While the mirrors claim 
```
faadd7bc9e84ce4790114fafe31aa399 ubuntu-9.10-beta-alternate-amd64.iso
```

Am I the only one seeing such weirdness?

EDIT:
Nevermind. I used the jigdo download based on the Torrent file earlier, and now I'm getting the correct MD5SUM.

---

### Post by kansasnoob on 2009-10-02
This torrent (i386 desktop) is hot:

[http://mirrors.cat.pdx.edu/ubuntu-releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.torrent](http://mirrors.cat.pdx.edu/ubuntu-releases/9.10/ubuntu-9.10-beta-desktop-i386.iso.torrent)

---

### Post by Roger E Critchlow Jr on 2009-10-02
I didn't check the MD5SUMS, but it matches:

root@elf11:~# md5sum ../ISO/ubuntu-9.10-beta-desktop-amd64.iso 
ced0c064235323257015f291fe096bbd  ../ISO/ubuntu-9.10-beta-desktop-amd64.iso[FONT=monospace]
[/FONT]ced0c064235323257015f291fe096bbd *ubuntu-9.10-beta-desktop-amd64.iso

Certainly argues against being in a hurry,

-- rec --

---

