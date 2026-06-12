---
title: "burning 8.04 iso"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Arch Parsons on 2008-04-26
Hello,
I have been trying this past couple of days to upgrade from Ubuntu 7.1 to Hardy Heron 8.04.  I get errors in doing updates 1-35 in that it hangs on 26 and reports fail on the others. When it gets to setting up the upgrade it has trouble at the same step.  In terminal mode it hangs on 0%.  I tried downloading the cd within Ubuntu yesterday evening, but it ended with the message, "unable to open iso file," or words to that effect.  Now I have the iso downloaded to Windows.  When I try to burn the iso with Nero CD ROM burner it reports an error in block size, "Do I want to fix or leave as is?" Where should I go from here?  Can someone point me to a beginners guide for upgrading Gutsy Gibbon to Hardy Heron with the cd? Thanks in advance for any assistance.

---

### Post by sandysandy on 2008-04-26
see this link for upgrading

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

link for burning iso

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

regards

---

### Post by Arch Parsons on 2008-04-26
Thanks for the reply.  I think I saw those links before.  I am still not having much luck with any of the install options.   I had no luck with Infraburner.  I did burn a copy with Nero. I ignored the option to change the block size.  The disk loads nomally in Windows but Upgrade is not an option and install returns a boot error.  I tried the disk inside Ubuntu and it asks to open inside package manager and then asks for the CD-Volume label. I type Ubuntu 8.04 i386 which is what appears after the drive letter,  but setup returns an error and stops it its tracks. What is the CD-ROM label?  How do I get the CD-ROM label while inside Ubuntu? Why can't the software detect this?

---

### Post by ugm6hr on 2008-04-26
The problem with the bi-annual release cycle is that every user in the world is trying to download at the same time.

I would suggest you just wait a few weeks for things to settle.

If you really want 8.04 now - download the Alternate CD by BitTorrent, and upgrade using that.  Or get a LiveCD to give it a try before a fresh reinstall.

---

### Post by Arch Parsons on 2008-04-26
Thanks.  I do notice that it is beginning to get faster each day, though still hanging a long time trying to fetch certain files, noticeably "en_translation" files, whatever they are.  I am thinking the cd that I have burned is quite probably not a good copy. The normal upgrade goes ok for awhile and then stops dead in its tracks - likely network congestion. You would think that they would include some indication of why things are not working, such as a network congestion warning.  It will hopefully be more likely to succeed in a week or two.

---

### Post by Herman on 2008-04-26
I agree with ugm6hr, BitTorrent is a much more reliable for downloading software that merely downloading it through a browser.

The Linux wget command is another good way to download software, video or any other kind of file.
Ironically for Windows users, you need some sort of Linux operating system already before you can use the wget command.
It might even be able to work from a LiveCD if you mount a hard disk file system to save the file to, but I have never tried that and I'm not sure how to set that up.
The wget command will try hard to download your files intact and uncorrupted. I have not had any problems yet with any files I have downloaded with the wget command, and it can download large files like DVDs too, which browsers can't handle.

In the example below, my connection was broken three times and each time, wget kept trying again and succeeded in downloading the file intact.
I'm impressed!
```
herman@amd64:~$ wget http://ga14.gamearena.com.au:3030/software/linux/ubuntu/hardy-dvd-i386.iso
--13:21:53--  http://ga14.gamearena.com.au:3030/software/linux/ubuntu/hardy-dvd-i386.iso
           => `hardy-dvd-i386.iso'
Resolving ga14.gamearena.com.au... 203.46.104.154
Connecting to ga14.gamearena.com.au|203.46.104.154|:3030... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,012,935,168 (3.7G) [application/octet-stream]

45% [========================================================================>                                                                                         ] 1,823,452,896   --.--K/s  ETA 4:04:10

16:45:14 (145.94 KB/s) - Read error at byte 1823452896/4012935168 (Connection timed out). Retrying.

--16:45:15--  http://ga14.gamearena.com.au:3030/software/linux/ubuntu/hardy-dvd-i386.iso
  (try: 2) => `hardy-dvd-i386.iso'
Connecting to ga14.gamearena.com.au|203.46.104.154|:3030... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4,012,935,168 (3.7G), 2,189,482,272 (2.0G) remaining [application/octet-stream]

51% [+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=========>                                                                               ] 2,066,861,280   --.--K/s  ETA 5:17:33

17:24:59 (99.73 KB/s) - Read error at byte 2066861280/4012935168 (Connection timed out). Retrying.

--17:25:01--  http://ga14.gamearena.com.au:3030/software/linux/ubuntu/hardy-dvd-i386.iso
  (try: 3) => `hardy-dvd-i386.iso'
Connecting to ga14.gamearena.com.au|203.46.104.154|:3030... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4,012,935,168 (3.7G), 1,946,073,888 (1.8G) remaining [application/octet-stream]

59% [+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++============>                                                                  ] 2,397,967,351   --.--K/s  ETA 3:57:06

18:13:38 (110.84 KB/s) - Read error at byte 2397967351/4012935168 (Connection timed out). Retrying.

--18:13:41--  http://ga14.gamearena.com.au:3030/software/linux/ubuntu/hardy-dvd-i386.iso
  (try: 4) => `hardy-dvd-i386.iso'
Connecting to ga14.gamearena.com.au|203.46.104.154|:3030... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4,012,935,168 (3.7G), 1,614,967,817 (1.5G) remaining [application/octet-stream]

100%[++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++=================================================================>] 4,012,935,168  160.89K/s    ETA 00:00

20:59:06 (158.91 KB/s) - `hardy-dvd-i386.iso' saved [4012935168/4012935168]

``````
herman@amd64:~$ md5sum hardy-dvd-i386.iso 
367710528efcd54987f230f4d1cf7dd8  hardy-dvd-i386.iso
```To use the wget command you just need to right-click on the download link and click 'copy link location', to copy the download URL.
Then you open a terminal and type: wget and after a space, paste in your URL for the download.
wget is great! :guitar:
Regards, Herman :)

---

### Post by Arch Parsons on 2008-04-28
Thanks for the info on the WGet command.  I will remember this thread for the next time. I love trying things that are new to me. People say I have a lot of patience.  I guess they mean persistence. I am definitely very, very poor at just sitting or standing and waiting for something. I went ahead and did the automatic upgrade last night (not waiting for the demand to decrease).  At approx. 20 kbps It took most of the overnight hours. Just before dawn I checked it and the packages were ready to install.  The installation complained about insufficient disk space and other errors were reported, but apparently it upgraded successfully.  Thanks again.

---

