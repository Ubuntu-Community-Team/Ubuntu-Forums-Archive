---
title: "Wubi doesn't do anythin at all!"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by UnBr34KaBl3 on 2010-04-29
When I run wubi to install 10.4 the process will start and then instantly terminate. I've tried to download the wubi.exe file and also tried running it from the CD (mounted with daemon tools).

Nothin happens! This is strange since I actually installed the beta of 10.4 with wubi a couple of weeks ago. Now nothing happens at all!

At one point Norton blocked pyrun.exe and I thought that was it but after disabling norton and downloading another wubi.exe there's no change.

I'm runnig Windows 7 64 bit and i also have python installed, maybe that can interfere in some way.

Need help since this seems to be the best ubuntu ever! Thanks!

---

### Post by Sijomo on 2010-04-29
If it's doing nothing at all and not even producing the debug log, it might a problem if you have Python already installed; this is a problem on Thinkpads. 

If you stick this in a batch file and run it, if it starts working, this is your problem.

SET PYTHONCASEOK=
wubi.exe

---

### Post by drreed on 2010-04-29
> **UnBr34KaBl3 said:**
> When I run wubi to install 10.4 the process will start and then instantly terminate. I've tried to download the wubi.exe file and also tried running it from the CD (mounted with daemon tools).

Nothin happens! This is strange since I actually installed the beta of 10.4 with wubi a couple of weeks ago. Now nothing happens at all!

At one point Norton blocked pyrun.exe and I thought that was it but after disabling norton and downloading another wubi.exe there's no change.

I'm runnig Windows 7 64 bit and i also have python installed, maybe that can interfere in some way.

Need help since this seems to be the best ubuntu ever! Thanks!

You did verify your iso didn't you? Don't assume that this one will be ok just because your last download was.

Checksum your iso and make sure you have a good burn. My 10.04 "test cd for defects" screen didn't come up and I'm not sure why. If you see that, ALWAYS make sure you run that step. It actually reads all those files and makes sure they're ok.

---

### Post by UnBr34KaBl3 on 2010-04-29
Dont think it's that. The batch file doesn't work.

This is the file i used:
[http://dl.dropbox.com/u/4018313/go.bat](http://dl.dropbox.com/u/4018313/go.bat)

Only outputs: 
[IMG]http://dl.dropbox.com/u/4018313/wubi.png[/IMG]

The wubi.exe file is placed in the same directory.

Other suggestions?

---

### Post by UnBr34KaBl3 on 2010-04-29
> **drreed said:**
> You did verify your iso didn't you? Don't assume that this one will be ok just because your last download was.

Checksum your iso and make sure you have a good burn. My 10.04 "test cd for defects" screen didn't come up and I'm not sure why. If you see that, ALWAYS make sure you run that step. It actually reads all those files and makes sure they're ok.

Downloaded via bit-torrent, bit-torrent auto checks that right?

However I have downloaded the wubi.exe file 10 times and it can't gone wrong every single time!

---

### Post by drreed on 2010-04-29
> **UnBr34KaBl3 said:**
> Downloaded via bit-torrent, bit-torrent auto checks that right?

However I have downloaded the wubi.exe file 10 times and it can't gone wrong every single time!


I don't know about bittorrent checking the download for me, I always check that myself.
10 times? Surely one of them must be good then, just make sure the one your actually using is, that's all, the other 9 don't count.

I don't know what else to tell you, I've never used Wubi. I'll check back to see how your coming along though, and if I think of anything I'll let you know.

---

### Post by Deozaan on 2010-04-29
I'm having a similar issue. Also on Windows 7, 64-bit.

But I get an error message:

> pyrun.exe - Drive Not Ready

The drive is not ready for use; its door may be open. Please check drive B: and make sure that a disk is inserted and that the drive door is closed.

[ Cancel ]  [ Try Again ] [ Continue ]

Drive B: on my machine is actually just a USB 1.44 Floppy drive that's not even plugged in, and hasn't been for weeks.

Clicking any of the three buttons results in the same error message popping up again in a few seconds.

I have to go into process explorer and End Task pyrun.exe to get this error message to stop popping up.

Aside: Where do you find the checksum hash for the disc images? I don't see it anywhere on the download page... Here's mine:

Ubuntu 10.04 LTS Desktop AMD64 MD5: 3e0f72becd63cad79bf784ac2b34b448

EDIT: I found my solution here: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

Basically Wubi didn't like the fact that my computer had a floppy drive, even though there was no media in the drive. By clicking the Continue button enough times it was able to install. I've since gone into my Device Manager and uninstalled the Floppy Drive. Wubi now runs without issue.

---

### Post by UnBr34KaBl3 on 2010-04-30
I guess I'll have too install a dual boot instead. Is there an easy way to make Windows start first now? Because since Grub 2.0 it has been a pain to make it work.

---

