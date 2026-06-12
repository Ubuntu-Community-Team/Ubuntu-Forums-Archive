---
title: "Is this a bug?"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-07-25
Folks, during Karmic x64 startup, after about 10%  the progress bar stops for like 30 seconds, and then the progress bar goes on.
Does it happen for you too?
Is it a bug or a temporary side effect of some transition to another library or so?

---

### Post by snargfish on 2009-07-25
> **froggyswamp said:**
> Folks, during Karmic x64 startup, after about 10% progress in the progress bar - the progress stops for like 30 seconds, and then the progress bar goes on.
Does it happen for you too?
Is it a bug or a temporary side effect of some transition to another library or so?

No, but I updated & whenever Kubuntu Karmic boots past the splash screen, I just get the oxygen cursor :(

---

### Post by SonnHalter on 2009-07-25
....is this a real question?

---

### Post by deadspider187 on 2009-07-25
> **froggyswamp said:**
> Folks, during Karmic x64 startup, after about 10%  the progress bar stops for like 30 seconds, and then the progress bar goes on.
Does it happen for you too?
Is it a bug or a temporary side effect of some transition to another library or so?

Could be the kernel probing for devices, a service timing out, or something else entirely.  Bootchart should catch it.  Try installing bootchart and posting the image from /var/log/bootchart/.  I wouldn't necessarily say this is even an issue.  How long is the total startup time?

---

### Post by cariboo on 2009-07-25
Dmesg should tell you what is taking so long too. Open a terminal and type:

```
dmesg
```

and look at the time on the left.

---

### Post by MacUntu on 2009-07-26
Don't wanna sound harsh, but if that's the best problem description you can give, you probably shouldn't use an alpha version of Ubuntu.

a. Follow cariboo907's suggestion (at 10% it's unlikely you'll find the problem there).

b. Temporarily remove the parameters "quiet" and "splash" from the "kernel"-line of 
1. GRUB: 
- select the kernel to boot
- press 'e' to edit the entry
- select the "kernel" line and press 'e' to edit
- remove the parameters, press 'Enter' to save
- press 'b' to boot

2. GRUB2:
- select the kernel to boot
- press 'e' to edit the entry
- use cursors to move to the parameters and delete them
- press 'Ctrl+x' to boot

You now should see a lot of messages flying by. Look at what it's doing during the pause and write it down (I usually take a cam to record the whole boot process - it's pathetic we still don't get this output logged to a file...).

c. As mentioned install bootchart.

---

### Post by froggyswamp on 2009-07-26
> **deadspider187 said:**
> Could be the kernel probing for devices, a service timing out, or something else entirely.  Bootchart should catch it.  Try installing bootchart and posting the image from /var/log/bootchart/.  I wouldn't necessarily say this is even an issue.  How long is the total startup time?
Happens every time since I started using Karmic x64 since Alpha 2. And this is an issue because Jaunty x64 boots like twice faster.
I attached the bootchart image.

---

### Post by froggyswamp on 2009-07-26
> **MacUntu said:**
> Don't wanna sound harsh
at least your signature is.

---

### Post by Gina on 2009-07-26
I've always had a pause early in the startup process - I just thought it was normal and haven't investigated.  I don't think it's anything like 30 secs though - more like 10.  So it might be something different in your case.

At times when I have watched the text, I've seen it take various amounts of time doing the various things.  Device detection is probably the longest - I do have quite a lot of extra devices.

---

### Post by ktechkio on 2009-07-26
> **MacUntu said:**
> 

b. Temporarily remove the parameters "quiet" and "splash" from the 


What's that joke for simply use recovery mode then after select resume normal!

---

### Post by MacUntu on 2009-07-26
> **ktechkio said:**
> at least your signature is.
No... click on the link. 

Edit: Maybe connected? [https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

> **ktechkio said:**
> What's that joke for simply use recovery mode then after select resume normal!
I'm so sorry, I always remove recovery mode entries. Didn't know they come without "splash" and "quiet".

---

### Post by froggyswamp on 2009-07-26
And here's my dmesg results.
Again, Jaunty boots like twice faster on same computer same arch.

---

### Post by MacUntu on 2009-07-26
> [   20.008764] end_request: I/O error, dev fd0, sector 0
[   32.168566] end_request: I/O error, dev fd0, sector 0
[   32.168572] Buffer I/O error on device fd0, logical block 0
[   44.352801] end_request: I/O error, dev fd0, sector 0
[   44.352805] Buffer I/O error on device fd0, logical block 0
[   56.516936] end_request: I/O error, dev fd0, sector 0
[   56.516940] Buffer I/O error on device fd0, logical block 0

Yeah, that looks like that bug: [https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

---

### Post by Gina on 2009-07-26
> **MacUntu said:**
> I'm so sorry, I always remove recovery mode entries. Didn't know they come without "splash" and "quiet".I presume then that you've never updated and found the main boot won't work and had to use recovery mode?  This is not a derogatory remark - just curious.

---

### Post by froggyswamp on 2009-07-26
Yep, that seems to be the bug, I've subscribed to it and added a comment, thanks.

---

### Post by MacUntu on 2009-07-26
> **Gina said:**
> I presume then that you've never updated and found the main boot won't work and had to use recovery mode?  This is not a derogatory remark - just curious.

If I need to boot into single user mode (which rarely happens), I edit the kernel line. I just don't like to have more GRUB entries than necessary (editing doesn't worry me).

---

### Post by deadspider187 on 2009-07-26
```

Quote:
[ 20.008764] end_request: I/O error, dev fd0, sector 0
[ 32.168566] end_request: I/O error, dev fd0, sector 0
[ 32.168572] Buffer I/O error on device fd0, logical block 0
[ 44.352801] end_request: I/O error, dev fd0, sector 0
[ 44.352805] Buffer I/O error on device fd0, logical block 0
[ 56.516936] end_request: I/O error, dev fd0, sector 0
[ 56.516940] Buffer I/O error on device fd0, logical block 0

```

Could also be a shotty floppy cable.  I've seen this for a SATA device, a cable replacement fixed it.

---

### Post by dougfractal on 2009-07-26
> **deadspider187 said:**
> ```

Quote:
[ 20.008764] end_request: I/O error, dev fd0, sector 0
[ 32.168566] end_request: I/O error, dev fd0, sector 0
[ 32.168572] Buffer I/O error on device fd0, logical block 0
[ 44.352801] end_request: I/O error, dev fd0, sector 0
[ 44.352805] Buffer I/O error on device fd0, logical block 0
[ 56.516936] end_request: I/O error, dev fd0, sector 0
[ 56.516940] Buffer I/O error on device fd0, logical block 0

```

Could also be a shotty floppy cable.  I've seen this for a SATA device, a cable replacement fixed it.

This fixed it for me.
blacklisting floppy.  Of course don't use if you use a floppy drive

```
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf && sudo rmmod floppy && sudo update-initramfs -u

```

---

### Post by apw on 2009-07-29
You might want to checkout the launchpad bug relating to this issue, where there is a request for help:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579)

---

