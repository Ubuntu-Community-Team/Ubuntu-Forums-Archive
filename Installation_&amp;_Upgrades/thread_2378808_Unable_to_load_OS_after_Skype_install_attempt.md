---
title: "Unable to load OS after Skype install attempt"
date: 2017-11-27
forum: Installation &amp; Upgrades
---

### Post by carbuncle on 2017-11-27
I was following this [https://www.google.com/amp/s/m.wikihow.com/Install-Skype-Using-Terminal-on-Ubuntu%3famp=1](https://www.google.com/amp/s/m.wikihow.com/Install-Skype-Using-Terminal-on-Ubuntu%3famp=1)

My computer frooze and I had to reboot.
I got the standard menu:
Ubuntu
Advanced
Memory test

Choosing any of those I get errors:
All starting with- error: can't find command

Choosing the 1st 2 gives a long error 
Can't find 'save_env'
Boot/grub/i386-pc/video.mod
'search'
'echo'
Linux
Echo
Lastly-initrd

The 3rd memory test gives can't find-
Search
Knetbsd

This forum seriously needs to let u add screen shots!

---

### Post by ajgreeny on 2017-11-27
The link you show is very out of date and of no use any more; it will not work, even if you can find and install that version of Skype.

You will now need to download Skype from [https://go.skype.com/skypeforlinux-64.deb](https://go.skype.com/skypeforlinux-64.deb) but it is available only as a 64 bit application so for your 32 bit system (I think that's what you have) you will have to use the web-based site at [https://login.live.com/login.srf?wa=wsignin1.0&rpsnv=13&ct=1511821372&rver=6.7.6626.0&wp=MBI_SSL&wreply=https%3A%2F%2Flw.skype.com%2Flogin%2Foauth%2Fproxy%3Fclient_id%3D578134%26redirect_uri%3Dhttps%253A%252F%252Fweb.skype.com%253Fintcmp%253Daccountweb-_-uktrybeta%26site_name%3Dlw.skype.com&lc=1033&id=293290&mkt=en-GB&uaid=2324fd26cc1fad44940e9cf19ffcbcd4&psi=skype&lw=1&cobrandid=90010&client_flight=hsu%2CReservedFlight33%2CReservedFlight67](https://login.live.com/login.srf?wa=wsignin1.0&rpsnv=13&ct=1511821372&rver=6.7.6626.0&wp=MBI_SSL&wreply=https%3A%2F%2Flw.skype.com%2Flogin%2Foauth%2Fproxy%3Fclient_id%3D578134%26redirect_uri%3Dhttps%253A%252F%252Fweb.skype.com%253Fintcmp%253Daccountweb-_-uktrybeta%26site_name%3Dlw.skype.com&lc=1033&id=293290&mkt=en-GB&uaid=2324fd26cc1fad44940e9cf19ffcbcd4&psi=skype&lw=1&cobrandid=90010&client_flight=hsu%2CReservedFlight33%2CReservedFlight67)

If I'm wrong and you do have a 64 bit system you can go ahead and download the file as shown above then install it with command ```
sudo apt install Downloads/Skypeforlinux-64.deb
``` assuming that is the name of the file downloaded and it is in Downloads in your home.

However, there is something very wrong with your system which is difficult to guess at from what you've told us.  If you had to carry out a hard shutdown by holding the power-button there may be filesystem corruption so boot to a live USB or DVD and run command ```
sudo e2fsck /dev/sda1
``` assuming sda1 is the root partition of your install.  

See if that helps, and if not, come back again with as much detail as you can.

---

### Post by carbuncle on 2017-11-27
I think something with the Skype install corrupted it. I'm waiting to see about getting a friend's computer to use, you are meaning a live USB of the OS?[http://www.instructables.com/id/How-to-make-your-own-Ubuntu-LiveUSB/](http://www.instructables.com/id/How-to-make-your-own-Ubuntu-LiveUSB/)

I was thinking of trying this before I read what you wrote [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)

Here are some images of the current screen options 
[https://imagebin.ca/v/3inO72zD3xQa](https://imagebin.ca/v/3inO72zD3xQa)

[https://imagebin.ca/v/3inPCAqw2sXG](https://imagebin.ca/v/3inPCAqw2sXG)

[https://imagebin.ca/v/3inQ3FdBQV30](https://imagebin.ca/v/3inQ3FdBQV30)

---

### Post by carbuncle on 2017-11-28
I just did the repair and that worked! my friend just did the boot repair live usb for me and forgot to make me one of my OS. However I noticed its still slow when I ran the command after finding my root directory with df, it didn't give too much.
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1654056         4   1654052   1% /dev
tmpfs             333044      1292    331752   1% /run
/dev/sda5      409441656 259949320 128670832  67% /
none                   4         0         4   0% /sys/fs/cgroup
none                5120         0      5120   0% /run/lock
none             1665216     65020   1600196   4% /run/shm
none              102400        36    102364   1% /run/user
/dev/sr0         4249808   4249808         0 100% /media/suzanne/SBF_TTT1
suzanne@RedSilver-Latitude-D620:~$ sudo e2fsck /dev/sda5
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda5 is mounted.
e2fsck: Cannot continue, aborting.

---

### Post by strixtux on 2017-11-29
Try Skype 8.11 next time. I installed it on a fresh 17.10 64 bit machine and, well, it works. Mostly.

---

