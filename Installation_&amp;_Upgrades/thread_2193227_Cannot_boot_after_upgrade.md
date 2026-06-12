---
title: "Cannot boot after upgrade"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by zeynel2 on 2013-12-11
I already posted questions to several forums including here [http://ubuntuforums.org/showthread.php?t=2192528](http://ubuntuforums.org/showthread.php?t=2192528) but the issue is still not resolved. Thanks to everyone who tried to help, but can you let me know if there is no hope to fix this, if so I will have to reinstall and lose all data I had (I have no backup). Thanks.

---

### Post by ian-weisser on 2013-12-11
It's probably pretty easy to fix.
There was lots of good advice in that previous thread.

Losing your data is entirely your choice. Backing up is very easy to do.
You already did the hardest part when you booted from a DVD.

---

### Post by zeynel2 on 2013-12-12
Hi ian-weisser: None of the good advice is working for me and all I get is reference to that link. Do you have any specific ideas that I can try. 

The latest thing I tried was to log in through grub without splash (this gets me to a command line) and I logged in and there was a message saying that a new version of ubuntu was available. I started to download that, all went well, but as soon as download ended, the screen went black.

I also tried the advice here: [http://askubuntu.com/questions/288842/general-error-mounting-filesystems-after-upgrade-to-13-04](http://askubuntu.com/questions/288842/general-error-mounting-filesystems-after-upgrade-to-13-04) and it did not work. Can you help?

---

### Post by zeynel2 on 2013-12-12
[COLOR=#000000][FONT=Arial]I tried again and when I run sudo apt-get dist-upgrage I get this error:
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.7+1ubuntu6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.7+1ubuntu6_amd64.deb) Could not resolve 'us.archive.ubuntu.com'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I thought this may be relevant because I was told that this was a video driver issue.[/FONT][/COLOR]

---

### Post by zeynel2 on 2013-12-12
I am able to log in through command line and I was able to print some of the important files. Would it be possible to back up from the command line? How can I do that?

---

### Post by ian-weisser on 2013-12-12
> **zeynel2 said:**
> I started to download that, all went well, but as soon as download ended, the screen went black.

That could mean a lot of things. It could mean that your screen turned off to save power, and you merely needed to jiggle the mouse, and your system is just fine. Or it could mean that you successfully upgraded and rebooted, but didn't fix your video driver. We're not psychic - you must explain *exactly* what happened and what you experienced in a lot more detail.

When you boot, stop the boot cycle at the GRUB screen.
There are instructions on your screen to tell you how to do that.
At the GRUB screen, select an older kernel to boot into.
You still need to fix the newer one, but it's easier if you can successfully boot.

---

### Post by ian-weisser on 2013-12-12
> **zeynel2 said:**
> I am able to log in through command line and I was able to print some of the important files. Would it be possible to back up from the command line? How can I do that?

Insert your USB stick or external hard drive.

Use the **ls** (list) command to find your stick. You might need to look around a bit in the /media directory.
For example, here is how I found my USB stick using the **ls** command:
```
$ ls /media
cdrom  cdrom0  ian                 #  Well, I know it's not a cdrom

$ ls /media/ian/
SHARED_128                          #  There it is!

$ ls /media/ian/SHARED_128/
00063.jpg                              # Look! It's the list of all my stuff on the USB stick!
zoo_stuff.jpg
```

Use the command **cp** (copy) to backup your stuff to the external USB stick or drive.
You can copy one file at a time, or entire directories (if your external drive is big enough)
The format is simple: cp FROM TO, like a sentence. 
For example, if I want to copy the file /home/ian/pudding_recipe onto the external disk, I would use
```
cp /home/ian/pudding_recipe /media/ian/SHARED_128/
```

If I wanted to copy my entire /home/ian directory with all my personal files (and my disk is big enough)
```
cp -r /home/ian /media/ian/SHARED_128/
```

---

### Post by zeynel2 on 2013-12-12
I tried this but it did not work. As soon I insert the USB drive I see this on the command line:

[517.576392] sd 6:0:0:0: [sdb] No Caching mode page found
[517.579669] sd 6:0:0:0: [sdb] Assuming drive cache: write through
&#8230;
and this repeats a few times.

I tried to fix with this answer [http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning) but that did not work either. 

ls /media does not recognize the USB stick. Is there any way to fix this?

---

### Post by zeynel2 on 2013-12-12
ian-weisser: I couldn't use the USB stick to back up but I used the instructions here [http://manpages.ubuntu.com/manpages/oneiric/man1/dropbox.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/dropbox.1.html) to back up to Dropbox with cp -r /home/a/Documents /home/a/Dropbox. Thanks, for the help, I was trying to copy the Documents directory but it wouldn't then I realized that I needed to enter -r, then it worked.

I would still like to fix the other issue if I can. Any ideas?

---

### Post by ian-weisser on 2013-12-12
Black screen smells like a hard-to-configure video card. Or perhaps a couple other issues.
I'm not a guru with video drivers. My last video problem was in 2006 or 2007.

Did you get the "nomodeset" option in Grub working?
Are you able to boot with an older kernel? Does video work with that kernel?

---

### Post by Bucky Ball on 2013-12-12
***Thread closed.***

Please do not duplicate post. You are getting plenty of help on the other thread (and if oldfred can't help with a boot problem few can) and there was no reason to start a new one. Go back to the other thread, re-read carefully.

---

