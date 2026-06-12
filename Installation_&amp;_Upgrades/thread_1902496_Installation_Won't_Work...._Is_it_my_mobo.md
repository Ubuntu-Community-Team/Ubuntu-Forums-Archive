---
title: "Installation Won't Work.... Is it my mobo?"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by DeadlyOats on 2011-12-30
I just built a new machine.  It uses the Asrock P67 Extreme 4 Gen3 mobo.  I saw a couple of threads, here, with people trying to install 'buntu via wubi, and they have this mobo.  Their installations stalled AFTER the 'buntu installer completed.

I'm doing, or trying to anyway, a fresh install from a CD.  It stalls when it get's to the firewire thingy...  I disabled the firewire device in the BIOS (UEFI?).  Now it stalls at the USB core thingy....  If I disable the USB (if I could) I'd end up with no mouse or keyboard.  Sometimes it stalls at a point where it says something about something being "killed" and the numeral "9".

I wonder if 'buntu/Linux is not ready for this mobo?  Or is there a work around?  I'm not installing via wubi.  I'm doing a straight install with the intention of doing a dual-boot with Winbloze....

Ironic.  I say, 'Winbloze', but it's Linux that's having trouble installing.  :lolflag:

EDIT:  Forgot to mention.  I'm trying to install Ubuntu 11.10, 64 bit version.

---

### Post by whatthefunk on 2011-12-30
I glanced through this review:
[http://kdubois.net/?p=1336](http://kdubois.net/?p=1336)

Guy says his worked out of the box with Ubuntu.  Try the 32 bit version to see if that works.  Try Ubuntu 10.04.  Try something else from the Ubuntu family like Kubuntu or Xubuntu.

---

### Post by DeadlyOats on 2011-12-30
Thanks for your reply and for that link.  It could be I have a bad copy of Ubuntu on that CD.  I'll re-download the ISO, and try the other flavors of 'buntu as well.

I'll - of course - update with the results.

Thanks again.

---

### Post by 73ckn797 on 2011-12-30
A bad download will cause numerous issues. I assume, by your time on the forums, that you understand the need to verify md5sums and burning slowly.

---

### Post by DeadlyOats on 2012-01-01
Happy New Year, everyone!  I just got back from work, and just finished installing Ubuntu LTS, 64 bit version.

None of the 11.10 Ubuntu's or Kubuntu's worked on my new build....

The first download of 64 bit Ubuntu, and the 64 bit Kubuntu hung before the Installation Menu was even displayed.  All I got was text, and it would hang at [COLOR="Red"]udevd [119]:[/COLOR] ((for Kubuntu)) or [COLOR="Red"][202]:[/COLOR] ((for Ubuntu)) [COLOR="Red"]'/sbin/modprobe -bv pci: (a really long string of numbers and letters)'[/COLOR]

The next line sometimes displayed was: [COLOR="Red"][159][/COLOR] ((for Kubuntu)) or [COLOR="Red"][222][/COLOR] ((for Ubuntu)) [COLOR="Red"]terminated by signal 9 (killed).[/COLOR]

Sometimes I'd get this line: [COLOR="Red"][4.908710] firewire_core: Created device FW0: GUID (a long string of numbers and letters)[/COLOR].

And that one time, when I disabled the firewire device in the BIOS, it hung at USB with the same sort of message as I got for the firewire_core thingy....

The Second download of Ubuntu 64 bit, and both Ubuntu/Kubuntu 32 bit versions, actually had me go through the installation process, but then at the first boot, after install, hung at a blank maroon screen (Ubuntu) or a blank blue screen (Kubuntu).  The reboot would have all versions hang at a black screen with a single blinking cursor at the very top-left of the screen and no text...

I don't understand how this could be.  Ubuntu 10.04 LTS installed fine, and I've booted into it just fine.  I'm typing this from there now...  So, why does a *NEWER* version of Ubuntu Linux *NOT* work?

As to md5sum....  I know of it, but don't know how to use it.  However, I did take steps to be sure I got good downloads and well burned CD's.  The subsequent downloads of 11.10 64 & 32 bit 'buntus were downloaded using Transmission torrent downloader.  I know these do CRC's or md5sums for each piece it downloads.  Next, not only did I set k3b to it's lowest burn speed, I also checked the 'verify written data' box, and as you know k3b does the md5sum check as well, and they were all good.

This is definitely a Linux/'buntu problem.  Could be the Gen 3 SATA/USB features of the mobo is playing havoc with Linux?  Although, the mobo should be using Gen2 SATA/USB since I'm not using an Ivy Bridge CPU.  I'm using a Sandy Bridge CPU....

This calls for a Linux brain surgeon....

Is there a work-around for this?  Or is this something Canonical or Linus have to look at?

---

### Post by whatthefunk on 2012-01-01
Check this thread out:
[http://ubuntuforums.org/showthread.php?t=1758080](http://ubuntuforums.org/showthread.php?t=1758080)

They all seem to be having the same problem as you and a couple solutions are offered.

---

### Post by darkod on 2012-01-01
Yeah, it's weird that a later version would not work. I don't know the specific details of development, but I alwways thought being LTS does carry a lot of weight.
Some people even say all the versions between are just a preparation for the next LTS.
They are more stable and more attention is paid, IMHO.
I know it's not an excuse but you might as well stick with it until the 12.04 LTS comes out in 4 months.

---

### Post by DeadlyOats on 2012-01-02
Thanks, whatthefunk!  Your link pointed me to the answer I needed for the workaround to get the install to work.  DanielBuus is inclined to believe the trouble is in the linux kernel itself, starting with kernel version 2.6.38.  He may be onto something with that.

darkod, I hope you're right.  I hope they fix it in time for 12.04 LTS...

---

