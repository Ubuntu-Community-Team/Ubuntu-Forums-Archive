---
title: "ubuntu won't install"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by tomreynolds93 on 2011-05-26
tried to install 11.04 using wubi and wouldnt work 
so created a boot disk and did it that way:
the boot disk loads but it freezes after the loading dots 

any ideas guys?
Thanks :)

---

### Post by tommcd on 2011-05-27
Do you mean that you burned a copy of the Ubuntu live CD?
If so, then how did you burn the CD? If you are using Windows 7 to burn the CD, just use the iso recording tool that comes with Windows 7. If you are using an earlier version of Windows, try using Iso Recorder or Infra Recorder. Also, be sure to burn the iso at the slowest possible speed. See this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Also, what graphics card does the computer have?

And welcome to the Ubuntu forums!

---

### Post by Hedgehog1 on 2011-05-27
This can be cause by a number of things - but a first guess is all your primary partitions are taken.

The best way to determine the 'usual suspects' is to do this:


Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by shahverdy on 2011-05-27
It might be because of crashed iso image that you have downloaded, This happend to me once. to check that, compare the md5 of the downloaded file with the md5 of the file on the ubuntu servers. you can use md5-sum tool on most linux distros.

if the image was crashed there is no need to download the whole image again. you can use a torrent client to fix it. 
to do so, download the torrent file of your iso image from ubuntu.com/download and start downloading the torrent file using a torrent client like Vuze or bittorent. after downloading started then stop it and quit torrent client, then replace the downloaded file with the crashed one, then reload the info, and start download, this will fix the image .

I hope this would be helpful ; )

---

### Post by Rubi1200 on 2011-05-27
> **tomreynolds93 said:**
> tried to install 11.04 using wubi and wouldnt work 
so created a boot disk and did it that way:
the boot disk loads but it freezes after the loading dots 

any ideas guys?
Thanks :)
Hi and welcome to the forums :-)

What exactly didn't work when you tried to install Wubi?

One of the simplest workarounds for many install issues is to place the downloaded ISO image and wubi.exe file in the same folder and then run Wubi.

Did you try this?

As tommcd mentioned, we need to know what graphics card you have.

Thanks.

---

### Post by tomreynolds93 on 2011-05-27
Thanks guys
Graphics wise its an NVIDIA GeForce 8200M G

Regarding the attempt at installing it using wubi, it appeared to install fine in the windows part, the restarted and selected ubuntu from the boot menu and it did the loading dot things and hung on the background after that. 
Did using the ACPI workarounds option in the grub menu and it got a bit further but still couldnt use it.

I burnt the iso using infrarecorder but it was at maximum speed.

Checked MD5s on downloaded file and is same as hashes on ubuntu website

---

### Post by Rubi1200 on 2011-05-27
Take a look here for possible workarounds:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

