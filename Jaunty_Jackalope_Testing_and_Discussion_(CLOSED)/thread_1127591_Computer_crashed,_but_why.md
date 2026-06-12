---
title: "Computer crashed, but why?"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thezood on 2009-04-16
I had an (almost) total system lock-up with Jaunty today. I was running Firefox and Update Manager when the mouse froze and the computer accepted no keyboard commands whatsoever. REISUB worked though. I can't really find anything in the logs but then again I'm not really sure of what to look for. I have plenty of Linux experience but haven't really had much luck finding useful things the logs. Does anyone have any tips?

Overall, Jaunty feels unstable and sometimes very slow on my machine, which is alarming since final release isn't many days away. I guess I notice slowdowns much more since my machine is definately low-end (Asus EEE 904HD). Oh well, let's just hope the developers fix it or I guess Intrepid will have to do.

---

### Post by JohnJackson on 2009-04-16
I too have experienced a few freezes where neither the mouse nor keyboard respond, nor can I switch to a tty. However performance has seemed quick. They are quite random and unexpected so I cannot attribute it to any event or action. For me my / partition is ext4 and /home partition is ext3.

---

### Post by thezood on 2009-04-16
I guess it's to be expected with a new release. It would be nice to be able to contribute by reporting the bugs that probably exist somewhere.

---

### Post by go7Ul1ai on 2009-04-16
Are you using an Intel Chipset? If so, this is a problem that has yet to be fixed.

---

### Post by JohnJackson on 2009-04-16
I have an nVidia graphics card

---

### Post by olskar on 2009-04-16
Me to using an aticard :/ seems like it might not be cardrelated

---

### Post by go7Ul1ai on 2009-04-16
Hmm, well it's a similar issue anyway, just not the one I was thinking of :/

---

### Post by thezood on 2009-04-16
I have an Intel chipset. Another lockup occured just now, this time when I pressed the button for importing a key file in Software Sources. And just as I installed 9.04RC on my production partition. I'll just have to cross my fingers crashes aren't going to keep occuring this often.
A good thing is that performance seem to have improved with the last updates.

[quote=lee.jarratt]Are you using an Intel Chipset? If so, this is a problem that has yet to be fixed.[/quote]

Do you have an URL to that bug?

---

### Post by habtool on 2009-04-16
I had a lockup a few minutes ago in jaunty while Downloading the RC iso.

I had left the pc and when I came back the screen-saver had stalled, also keyboard was frozen and also the mouse.
This is the first freeze for me on jaunty I have tracked it from about Alpha 3 onward.

X32, ext4, nvidia, core2 duo on myside

---

### Post by JohnJackson on 2009-04-16
Intel thread: [http://ubuntuforums.org/showthread.php?t=1120684](http://ubuntuforums.org/showthread.php?t=1120684)

A difference for me is that the cursor doesn't move when it freezes

---

### Post by habtool on 2009-04-16
> **thezood said:**
> I have an Intel chipset. Another lockup occured just now, this time when I pressed the button for importing a key file in Software Sources. And just as I installed 9.04RC on my production partition. I'll just have to cross my fingers crashes aren't going to keep occuring this often.
A good thing is that performance seem to have improved with the last updates.



Do you have an URL to that bug?

The Intel issue is in RC release notes too:
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

also bug mentioned in RC notes:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

---

### Post by gotgenes on 2009-04-22
See [Bug #332549]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/332549/") or Launchpad and contribute your information if you think it's the same one you're experiencing.

---

