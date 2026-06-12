---
title: "Help me debug boot issue..."
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kenny_Larsen on 2010-03-23
Hi All,

Have been having some unpredictable issues during boot, I came home this evening and booted the computer and it just hung during boot with some red patches at the top of the screen. I then ran the live cd and it booted through, did my urgent tasks, then rebooted, as it was doing so was repeatedly pressing esc for the grub. This didn't seem to bring the grub menu up, however the system did boot? Will there be a log file I can find that might show why it hung previously?

Cheers,

Kenny

---

### Post by cariboo on 2010-03-23
You now have to hold down the shift key to get to the grub menu. All the logs are located in /var/log. I looks like you have a problem with the video driver.

---

### Post by Owen.C93 on 2010-03-23
> **Kenny_Larsen said:**
> Hi All,

Have been having some unpredictable issues during boot, I came home this evening and booted the computer and it just hung during boot with some red patches at the top of the screen. I then ran the live cd and it booted through, did my urgent tasks, then rebooted, as it was doing so was repeatedly pressing esc for the grub. This didn't seem to bring the grub menu up, however the system did boot? Will there be a log file I can find that might show why it hung previously?

Cheers,

Kenny
I had this and had to reconfigure xorg. Is it since you updated to -17 kernel. If so see this thread.
[http://ubuntuforums.org/showthread.php?t=1437167](http://ubuntuforums.org/showthread.php?t=1437167)

---

### Post by Kenny_Larsen on 2010-03-23
No I'm currently still running kernel 16, interestingly if I restart it fails, if I then retsrat with the livecd and then restart again it works, what is the livecd changing that allows it to boot?

EDIT: Will update now to see if it fixes it...

---

### Post by Kenny_Larsen on 2010-03-23
Kernal -17 fixes -> solved (Somehow)

Now to deal with the rest of the boot time errors! :P

---

### Post by Kenny_Larsen on 2010-03-24
Unsolved...

It turns out that restarting the system works, but shutting down, the booting up leads to the same problem as before (for both kernals -16 and -17). As before booting to the livecd and then restarting allows the system to boot normally

Anyone got any ideas? I'm really stumped!

Kenny

---

### Post by Kenny_Larsen on 2010-03-27
Bump

Need to try to get this sorted at some point!

---

### Post by QLee on 2010-03-27
[QUOTE=Kenny_Larsen]Bump

Need to try to get this sorted at some point![/QUOTE]

Kenny, this is beta software, you're not using it for mission critical computing, are you?

I'm sure most of us would like to help you, however, you haven't given us much to troubleshoot with.

Cariboo907, gave you what I think is a good hint and suggestion. I agree that video is where I would start looking if I saw this on a system of mine . Did you find anything in the logs as suggested? 

Did you reconfigure Xorg after the kernel upgrade as suggested by Owen. C93?

Otherwise, all we have to go on is your original post and we don't even know what kind of computer you have or what the video card might be.

---

### Post by Kenny_Larsen on 2010-03-27
Hi Qlee,

Apologies for the lack of info, new-ish to all this! Nothing on here is particularly critical, just for playing on!

I have tried to follow Cariboo's advice, there is no Xorg.conf file so I tried to create one using
```
sudo Xorg -configure
```
However I get an error:
```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
```

The same error on boot also happens in recovery mode on both kernals (-16, -17)

I have builtin graphics, Via S3 Unichrome Pro.

There was nothing in the logs I could find, perhaps the last message in kern.log before it freezes is:

Mar 27 07:58:55 kenny-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.

Thanks,

Kenny

---

### Post by QLee on 2010-03-27
If you do a search of the forum (or just a plain search engine search) you will find that others are having trouble with the VIA chipset.  

There is this launchpad bug recorded, see if your problem fits with it.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623)

I'm a little surprised you didn't find those yourself.

Edit:  An addition, I've never tried reconfiguring X while X was running, judging by the error you got, you would have had to get out of X first too.

---

### Post by Kenny_Larsen on 2010-03-27
Thanks I must have missed those, I'll keep my eye on the launchpad...

Kenny

---

