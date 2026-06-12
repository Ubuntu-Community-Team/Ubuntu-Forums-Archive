---
title: "Firefox broken again"
date: 2017-02-03
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2017-02-03
Did another upgrade to 4.4.0-62, the problem described here came back:

[https://ubuntuforums.org/showthread.php?t=2351167](https://ubuntuforums.org/showthread.php?t=2351167)

Rebooting several times (what seemed to work last time) did not fix it. Pages load slowly, and never finish. E.g. getting googlemaps in Seamonkey is almost instantaneous, while in Firefox it chugs along for about 10 seconds and then just stalls.

---

### Post by &amp;KyT$0P# on 2017-02-03
Try a new, clean Firefox [profile]("http://kb.mozillazine.org/Profile").

If that doesn't solve it, are you running an apparmor profile for Firefox in enforce mode?

---

### Post by PaulBx on 2017-02-03
According to aa-status, the firefox apparmor profile is in enforce mode.

dmesg shows a lot of "DENIED" messages, starting with these...
```

[   42.767632] audit: type=1400 audit(1486152926.871:67): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/proc/4331/net/arp" pid=4337 comm=4C696E6B204D6F6E69746F72 requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   42.941667] audit: type=1400 audit(1486152927.047:68): apparmor="DENIED" operation="file_mprotect" profile="/usr/lib/firefox/firefox{,*[^s][^h]}//lsb_release" name="/usr/bin/python3.5" pid=4352 comm="lsb_release" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   44.216992] audit: type=1400 audit(1486152928.319:69): apparmor="DENIED" operation="open" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/xdg/lubuntu/applications/mimeinfo.cache" pid=4331 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   44.357416] Bluetooth: hci0 command 0x0c25 tx timeout
[   45.486683] audit: type=1400 audit(1486152929.591:70): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4382 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[   46.361476] Bluetooth: hci0 command 0x0c38 tx timeout
[   48.109598] audit: type=1400 audit(1486152932.215:71): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4382 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[   48.111219] audit: type=1400 audit(1486152932.215:72): apparmor="DENIED" operation="unlink" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/paul/.cache/mozilla/firefox/mjgcmg3t.default/safebrowsing-to_delete/test-track-simple.cache" pid=4382 comm=55524C20436C6173736966696572 requested_mask="d" denied_mask="d" fsuid=1000 ouid=0
[   48.365534] Bluetooth: hci0 command 0x0c39 tx timeout
[   50.245613] audit: type=1400 audit(1486152934.347:73): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.SRuin7" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.245769] audit: type=1400 audit(1486152934.351:74): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.uHMKfG" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.245854] audit: type=1400 audit(1486152934.351:75): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.CB2d8e" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.263006] audit: type=1400 audit(1486152934.367:76): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.e7HH3N" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.263126] audit: type=1400 audit(1486152934.367:77): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.aYTcZm" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.263205] audit: type=1400 audit(1486152934.367:78): apparmor="DENIED" operation="mknod" profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/shm/org.chromium.ndZIUV" pid=4418 comm=57656220436F6E74656E74 requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
[   50.369602] Bluetooth: hci0 command 0x0c05 tx timeout



```

Haven't tried messing with the firefox profile yet.

Firefox runs if I put it in "complain" mode.

That's odd. In the log file we have the profile listed as 
profile="/usr/**lib**/firefox/firefox

while the actual profile is called 

/etc/apparmor.d/usr.**bin**.firefox

Though maybe it doesn't matter because /usr/bin/firefox is just a link to /usr/lib/firefox/firefox.sh

Well, I guess I will just run firefox as "complain". Apparently there is a lot of debate about the firefox apparmor profile anyway, and I'm not interested in learning the guts of apparmor enough to restrict it some more. Maybe I should just start trying other browsers!

---

### Post by &amp;KyT$0P# on 2017-02-03
> **PaulBx said:**
> Apparently there is a lot of debate about the firefox apparmor profile anyway, and I'm not interested in learning the guts of apparmor enough to 
Apparmor profiles require a lot of manual tweaking and personal customisation to set up.  If you're looking to restrict Firefox, and don't want to use apparmor for that, I suggest trying [FONT=Courier New]firejail[/FONT] instead.  It's available in the repositories.

> Maybe I should just start trying other browsers!
To solve a problem that actually has nothing to do with Firefox? :-k

---

### Post by gotaproblemwithmything on 2017-02-04
I can confirm that an update recently broke my Firefox, and it's related to apparmor. Pages would not load at all, I just got a white screen. I used apparmor utils to give Firefox some new privileges, and it's working again.

---

### Post by vasa1 on 2017-02-04
> **halogen2 said:**
> ...
If that doesn't solve it, are you running an apparmor profile for Firefox in enforce mode?
That's interesting because a few years ago*, the Firefox profile was provided but not active for fear of confusing new users. Now, I'm seeing reports that make me think that at least some users are having active profiles and running into issues.

* [https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile](https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile)

---

