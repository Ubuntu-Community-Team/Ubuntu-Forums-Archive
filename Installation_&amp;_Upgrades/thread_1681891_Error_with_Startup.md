---
title: "Error with Startup"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by sarmadluvu on 2011-02-04
Hej
I just downloaded Ubuntu installer for windows (wubi). After downloading and installing it as dualboot operating system. I went on configuring it. for my bad luck my laptop died due to low battery (I found it the cause, but may be some system error, well I don't think so) when the system was updating itself. Now I can boot to my old Windows 7 successfully, Ubuntu recover mode also. but when I try to boot with normal Ubuntu, it comes to welcome screen but never takes me to login page. I don't know what went wrong and how can I repair it. But I am really eager to sort it out and enjoy the Ubuntu. I hope there would be someone to help me out.
tnx in anticipation.

---

### Post by bcbc on 2011-02-05
> **sarmadluvu said:**
> Hej
I just downloaded Ubuntu installer for windows (wubi). After downloading and installing it as dualboot operating system. I went on configuring it. for my bad luck my laptop died due to low battery (I found it the cause, but may be some system error, well I don't think so) when the system was updating itself. Now I can boot to my old Windows 7 successfully, Ubuntu recover mode also. but when I try to boot with normal Ubuntu, it comes to welcome screen but never takes me to login page. I don't know what went wrong and how can I repair it. But I am really eager to sort it out and enjoy the Ubuntu. I hope there would be someone to help me out.
tnx in anticipation.

When you boot in recovery mode, have you tried to "repair broken packages"?

---

### Post by sarmadluvu on 2011-02-05
hi,
Thanx for your reply.
I tried different options to no avail:
1- sudo apt-get update
2- sudo apt-get upgrade

both of these options gave the response of going for the dpkg 
so I did
3- sudo dpkg -configure -a
with the response

dpkg: parse error, in file '/var/lib/dpkg/updates/0067' near line 0
newline in field name '#padding'

I have no clue where to go.
otherwise I would go back to Windows which is not so pleasing. :(

---

### Post by bcbc on 2011-02-05
> **sarmadluvu said:**
> hi,
Thanx for your reply.
I tried different options to no avail:
1- sudo apt-get update
2- sudo apt-get upgrade

both of these options gave the response of going for the dpkg 
so I did
3- sudo dpkg -configure -a
with the response

dpkg: parse error, in file '/var/lib/dpkg/updates/0067' near line 0
newline in field name '#padding'

I have no clue where to go.
otherwise I would go back to Windows which is not so pleasing. :(
This thread looks promising: [http://ubuntuforums.org/showthread.php?t=1532208](http://ubuntuforums.org/showthread.php?t=1532208)

Or this one [http://ubuntuforums.org/showthread.php?t=1522210](http://ubuntuforums.org/showthread.php?t=1522210)

---

### Post by sarmadluvu on 2011-02-05
Thanks a lot for your help.
its resolved now.
As directed I deleted the updated dir then went for sudo apt-get upgrade
bingo it worked right then
thank you very much once again.
:)

---

### Post by bcbc on 2011-02-05
Great - glad to hear it's sorted.

PS with wubi installs you want to avoid grub-* package updates. There's a long topic on this in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). It only affects 10.04.1 installs right now (or upgrades to 10.10), but even if you installed 10.10 fresh you could save yourself the trouble by familiarizing yourself with the problem and locking the packages as directed.

---

