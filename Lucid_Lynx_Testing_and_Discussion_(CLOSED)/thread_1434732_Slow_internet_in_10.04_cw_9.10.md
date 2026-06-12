---
title: "Slow internet in 10.04 cw 9.10"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-03-20
Hi

I am getting at best half my speed on 10.04 cw 9.10

I have applied the ipv6.disable=1 fix to grub, and installed and configured pdnsd in both 10.04 and 9.10.

Some evidence:
10.04 speedtest.net
[[IMG]http://www.speedtest.net/result/755503293.png[/IMG]](http://www.speedtest.net) 

9.10 speedtest.net
[[IMG]http://www.speedtest.net/result/755489581.png[/IMG]](http://www.speedtest.net) 

(Note huge ping difference)

from sudo pdnsd-ctl dump (on 10.04 box - to check it's on)
```
www.speedtest.net.
    03/20 01:27:54    A       69.17.117.207
```

10.04 boot commands from grub.cfg:
```
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 4eb04ac8-20af-4c12-935e-c16dc0f34581
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=4eb04ac8-20af-4c12-935e-c16dc0f34581 ro   ipv6.disable=1 splash
	initrd	/boot/initrd.img-2.6.32-16-generic

```
Can anyone give me any clues?

---

### Post by Bochonok on 2010-03-20
You are lucky :)
My network speed has been screwed in 9.10 already and it hasn't been improved yet.

---

### Post by grandtoubab on 2010-03-20
Hello
Have a look on namebench, it could improve to choose better DNS
[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Below my result
[http://www.speedtest.net/result/755537259.png](http://www.speedtest.net/result/755537259.png)

---

### Post by ubername on 2010-03-20
Thanks

I think pdnsd should overcome DNS times, but perhaps it is not working properly

I found this
[http://ubuntuforums.org/showthread.php?t=1395866](http://ubuntuforums.org/showthread.php?t=1395866)

Which is looking promising but not fully convinced it's fixed yet.

---

### Post by grandtoubab on 2010-03-20
one time I used to fix my MTU to 1492

---

### Post by Bochonok on 2010-03-20
> **grandtoubab said:**
> Hello
Have a look on namebench, it could improve to choose better DNS
[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Below my result
[http://www.speedtest.net/result/755537259.png](http://www.speedtest.net/result/755537259.png)
The ping issue is not the dns issue. They are my results with 2.6.32 and 2.6.30 kernel respectively. This is the ppp issue appeared in 2.6.31 and it hasn't been fixed yet.

---

### Post by ubername on 2010-03-20
Loving your speeds, Bochonok!

I did a quick search for 'ppp issues 2.6.31' but couldn't find anything that I could relate to - are you saying that I (and everyone else?) need to wait for a kernel upgrade / fix to see my speeds improve?

---

### Post by Bochonok on 2010-03-20
> **ubername said:**
> Loving your speeds, Bochonok!

I did a quick search for 'ppp issues 2.6.31' but couldn't find anything that I could relate to - are you saying that I (and everyone else?) need to wait for a kernel upgrade / fix to see my speeds improve?
I've downgraded to 2.6.30. But it's a bad solution for some specific hardware. Although mine is widely used (Intel P35, nvidia 8800gts512, etc), so I've no significant problems (need some tweak to get sound working though).

---

### Post by ubername on 2010-03-21
Hmm...

I've just realised that my 9.10 install runs on 2.6.31


> :~$ uname -r
2.6.31-20-generic

So it must (?) be something else - Anyone else having this problem with much slower connection on 10.04 v 9.10??

---

### Post by ubername on 2010-03-22
bump

This is doing my head in a bit.

Downloading updates etc. on karmic goes at +-2M/s wheras it is about 250K/s on Lucid. 
Browing is practically seamless on Karmic, but full of 'waiting for...' messages in Lucid. (and'resolving host...' even though I have pdnsd on – is that a clue?)

Can anyone help at all?

---

### Post by jfernyhough on 2010-03-22
Out of interest have you tried a newer kernel? Or the mainline versions? I've found that sometimes a plain vanilla kernel works better than the Ubuntu-sauce version.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Running 2.6.33 and all is fine, had problems with e.g. Ubuntu's 2.6.32-16 and nvidia (which is likely fixed now, but still).

---

### Post by ubername on 2010-03-22
Thanks, just tried the /daily/current 2.6.34-999 and it still behaves the same.

---

### Post by psycosmyth on 2010-03-24
I've been having this issue since 9.10. The problem with speed is with wireless only though. I'm using my old D-link pcmcia card that has an Atheros chip. Madwifi was awesome with this card but Ath5k caused problems with the dhcp requests. It would work great without a password but somehow forgets to communicate data with one. I would have the first page of a sight load instantly but any links from there would freeze. Not sure how this relates to your problem but there were no other posts on speed loss.
The speed test site shows the same speed for wifi and wired.
I have been using 8.04 instead for some time.

---

### Post by ubername on 2010-03-25
Wow, North Antarctica!

Thanks for the post, I'm on wired only so it's not that.

Anyone got any clues I could use for trouble shooting? I don't know if it's a kernel thing and I'm on pretty standerd kit - Dell E520 
-Processors-
Intel(R) Pentium(R) D CPU 2.80GHz		: 2800.00MHz
Intel(R) Pentium(R) D CPU 2.80GHz		: 2800.00MHz

-PCI Devices-
Ethernet controller		: Intel Corporation 82562V 10/100 Network Connection (rev 02)

VGA compatible controller		: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)

 This is also a clean(ish) install, from Beta 1 (although with a home partition that might be as old as Jaunty or more - anyone know how to check how old the home partition is?)

Bizarre - I just did *sudo apt-get install hardinfo* to get the stuff I pasted above and got: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mesa-utils
The following NEW packages will be installed
  hardinfo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 263kB of archives.
After this operation, 782kB of additional disk space will be used.
Get: 1 http://archive.ubuntu.com/ubuntu/ lucid/universe hardinfo 0.5.1-1.1ubuntu2 [263kB]
Fetched 263kB in 1s (212kB/s)   
Selecting previously deselected package hardinfo.
(Reading database ... 170924 files and directories currently installed.)
Unpacking hardinfo (from .../hardinfo_0.5.1-1.1ubuntu2_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up hardinfo (0.5.1-1.1ubuntu2) ...

Processing triggers for menu ...

```
And look at the speed - - 2128 KB/s.

Yet all my GUI apps trundle along with fluctuating rates of between <5KB/s to > 1MB/s (but never as good as 2128KB/s)

Help please - or even post if you are on similar kit / set-up and NOT having problems!

---

### Post by mentrei on 2010-03-28
im having the same problem...
in 9.10 the connection go at maximum
but in 10.04...

---

### Post by Reiger on 2010-03-29
I'm having trouble with kernel 2.6.32-17 (Internet drops out quickly); but 2.6.32-16 still works `fine'. Fine being a miserable 1.31Mb/s download, 0.21Mb/s upload that is.

---

### Post by mentrei on 2010-03-29
ok, i fixed it.
set my router to bridge mode, run:

> sudo pppoeconf

restarted the pc...
and the speed is back!!

---

### Post by shindou01 on 2010-03-30
you should mark your thread as solved so that others with similar issue may use your solution ontheir problem as well then....
Congratulations...

---

### Post by -siGGi- on 2010-03-31
i also had a simliar problem with wlan, i simply fixed it by changing the radio channel from 1 to 12 in the routerconfiguration. you can change it to whatever number you want i have 13 channels on the whole on my FRITZ!Box Fon WLAN 7050

---

### Post by ubername on 2010-04-07
Marking as solved - I didn't use any of the specific tips, but assorted updates seems to have done the trick.

---

