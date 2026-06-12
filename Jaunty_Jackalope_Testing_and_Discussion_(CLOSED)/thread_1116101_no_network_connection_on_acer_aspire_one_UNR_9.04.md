---
title: "no network connection on acer aspire one UNR 9.04"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fabianb on 2009-04-04
Hi All,

Could somebody please help me?
Got my Acer Aspire One 4 days ago. It's the AA1 A110-AaGb, 16Gb SSD, 1Gb Ram version.
I immediately installed Ubuntu on there (the netbook remix, UNR Jaunty Daily Image) and got everything to work. A day later I installed Sickboy's kernel ( linux-image-2.6.28sickboy-kuki_0.4_i386.deb), and life was great!
But today suddenly my netbook could not create a new connection, not wired and not via wifi (both were working fine the days before, eth0 out-of-the-box and wifi after some tweaking).
So I tried undo-ing all the changes I made that day: nothing
back to the previous kernel: nothing
re-installing the sickboy kernel: nothing
entire reinstall of the UNR Ubuntu 9.04: nothing
again install of sickboy kernel: nothing
shutting down, removing power cord removing battery and waiting for give minutes, then booting: not... well you get the idea.

I'm quite the noob, but from what I gather everything seems ok
dmesg shows something strange on wifi (dmesg | grep wlan):

[   21.881721] wlan0: direct probe to AP 00:1c:df:8c:0c:6d try 1
[   22.082292] wlan0: direct probe to AP 00:1c:df:8c:0c:6d try 2
[   22.284375] wlan0: direct probe to AP 00:1c:df:8c:0c:6d try 3
[   22.484110] wlan0: direct probe to AP 00:1c:df:8c:0c:6d timed out
[   35.527135] wlan0: authenticate with AP 00:22:6b:8e:64:9f
[   35.555313] wlan0: authenticate with AP 00:22:6b:8e:64:9f
[   35.556906] wlan0: authenticated
[   35.556921] wlan0: associate with AP 00:22:6b:8e:64:9f
[   35.559245] wlan0: RX AssocResp from 00:22:6b:8e:64:9f (capab=0x411 status=0 aid=1)
[   35.559994] wlan0: associated
[   81.295858] wlan0: disassociating by local choice (reason=3)

reason=3???

I'll include the entire dmesg, ifconfig -a and lsmod outputs, and am really hoping someone can help me with this (though I am beginning to fear I'm dealing with malfunctioning hardware).

also, networkmanager shows all the connections (including wifi) and the wifi led is blinking and stuff, just no connection is established.

please does someone know what to do?

---

### Post by fabianb on 2009-04-04
hmm the dmesg output was to much for the previous post, so here it is

---

### Post by ozorba on 2009-04-04
do the following and it will work.

sudo gedit /etc/modprobe.d/blacklist

add the following line

blacklist acer_wmi

save, exit and restart

for more information go to here:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by fabianb on 2009-04-04
Thanks for your reply.
Though it did not do the trick.

I tried almost anything I found on several webpages like [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) to get it to work, but it won't work.
Should have mentioned that though.

Also this solution will only fix wireless trouble right? acer_wmi can't cause my wired connecteion to fail right?

---

### Post by fabianb on 2009-04-07
Oops, nevermind.
The problem seemed to be located in a strangely misbehaving ethernet cable.
Ubuntu was fine all along.
Thanks for the help though.


Move along now people, there is nothing to see here ;)

---

### Post by bobnutfield on 2009-04-07
Glad you got it going.  For what is is worth, I found it to be no longer necessary to use the sickboy kernel with Jaunty.  A simple blacklist and install of the backports, and EVERYTHING works (except, of course, the card readers, which the sickboy kernel has not solved, either).  The boot time with a stock Jaunty install is 11 seconds longer than the sickboy kernel.  I can live with that extra boot time for clean Ubuntu supported kernel on my AAO.

Just a thought...

---

