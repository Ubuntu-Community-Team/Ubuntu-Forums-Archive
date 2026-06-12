---
title: "Initial boot after installation works, all subsequent boots freeze"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by bent82 on 2016-07-28
So I am having a weird issue, I actually noticed it with Linux Mint, but I decided to try Ubuntu to see if the problem originated there, and it does seem to.  I have a little Dell Inspiron Mini 1012.  Ubuntu 15.04 and older will install and works great.  The trouble starts when I try to install 15.10 or 16.04.  The installer boots fine, and I am able to install.  I remove the USB drive I used and reboot.  The system will fully reboot into the desktop, I am able to use the system if I choose.  But when I shut it down and try to start up again, the system will freeze every time.  I hit escape so I can view the list of what the system is doing, and it doesn't seem to freeze on any particular thing each time, but it does freeze solid every time.  No blinking cursor, no hard drive activity, nothing.  After the first initial boot after installation, the system will never boot again.  I am completely at a loss as for what to do, and would love to get the newer versions working on this system.  If anyone needs more info, just let me know.  Thank you.

---

### Post by oldfred on 2016-07-28
Looking up specs on that system, shows older Pine Trail Atom chip.

Are you installing Ubuntu or Lubuntu? Ubuntu typically needs newer systems particularly Unity needs better video chips or a video card.

And there are specific issues with some newer Bay Trail Atom chips, but those are newer and used 32 bit UEFI. Which requires extra install steps and some boot parameters.

---

### Post by bent82 on 2016-07-28
Well, the ultimate goal was to get Linux Mint 18 working.  When I was having issues with that, I tried Ubuntu since I know Mint is based on it, and I wanted to see if the problem occurred in Ubuntu as well.  I have not tried Lubuntu but I will try it later this evening to se if the problem occurs there as well.  

If support had been dropped somewhere between 15.04 and 15.10, I could understand it, but I don't really think that is the case.  As I said, the initial boot after installation works great, I don't have any issues whatsoever. but as soon as I shut it down, it will never start up again, freezing every time.

I know my problem description is light on the technical details, so if anyone needs me to try anything or post any outputs, I am willing to do so.

---

### Post by bent82 on 2016-07-28
So I had some time to install Lubuntu 16.04, and I get the exact same results as Ubuntu and Mint.  Any boot after the first one results in a hard freeze, the cursor stops flashing and all hard drive activity stops.  I haven't tried Lubuntu 15.04, but I'm guessing the issue started in 15.10 just like Ubuntu.

---

### Post by bent82 on 2016-08-01
So does anyone have any more info for me, or know what I should be doing to try to get this to work?  So far, I have determined that any Ubuntu-based OS freezes this system on the second boot if it is version 15.10 or newer, and works on 15.04 or older.

---

### Post by oldfred on 2016-08-01
This was for the newer bay trail, perhaps yours is similar?
 intel_idle.max_cstate=1 required on baytrail to prevent crashes
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) 

 Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by bent82 on 2016-08-01
Thanks for the reply.  I added the line intel_idle.max_cstate=1 to the file /etc/default/grub, which I believe is what I was supposed to do.  It didn't make a difference, I still get a hard freeze during boot.

EDIT: Rather than double post, I will add this onto the end of this post.  

I realized that I had tried all these Ubuntu variants but I hadn't tried anything NOT based on Ubuntu, since I don't tend to use those distros.  So I decided to quickly download Fedora Core 24 and give it a shot.  Well, I have discovered it isn't an Ubuntu issue after all, I get the same hard freeze during boot (on anything but the first boot, which works great).  I have now ruled out Ubuntu as being the source of this issue, but what's left?  I suppose it could be a kernel issue, but I have no idea where to go for help with that.  I also don't know how to narrow this down any further.  Any advice would be a great help.

---

### Post by oldfred on 2016-08-01
Does 14.04 work, it is supported until 2019.

Or is it now only available with the enablement stack which is  then a newer kernel? 
 Ubuntu 14.04.1 -> kernel 3.13 (from Ubuntu 14.04)
LTS Hardware Enablement Stack
Ubuntu 14.04.2 -> kernel 3.16 (from Ubuntu 14.10)
Ubuntu 14.04.3 -> kernel 3.19 (from Ubuntu 15.04)

---

### Post by bent82 on 2016-08-01
As I mentioned in my last message, I figured we might have a kernel bug.  This information allowed me to finally stumble upon the appropriate google terms to find the problem.

[https://bugzilla.redhat.com/show_bug.cgi?id=1253523](https://bugzilla.redhat.com/show_bug.cgi?id=1253523)
[https://bugs.archlinux.org/task/47509](https://bugs.archlinux.org/task/47509)
[https://bugzilla.kernel.org/show_bug.cgi?id=107651](https://bugzilla.kernel.org/show_bug.cgi?id=107651)

It seems like it could be specific to this Dell mini model.  It appears to be a bug with the laptop driver, system tries to turn on a keyboard backlight which doesn't exist, which freezes the system on any boot after the first.  Apparently, this was introduced in kernel 4.1.3, and hasn't really even been acknowledged by the kernel devs.  There is a workaround listed that I have yet to try, and I'll post when I get a chance.

---

### Post by bent82 on 2016-08-01
Success!  Using the workaround listed on the kernel bug report page:

```
sudo systemctl mask [EMAIL="systemd-backlight@leds\:dell\:\:kbd_backlight.service"]systemd-backlight@leds\:dell\:\:kbd_backlight.service[/EMAIL]
```

The keyboard backlight service is then masked and won't freeze the system when a kernel version greater than 4.0.8 starts.  I am assuming this will be an appropriate workaround that won't cause any other issues.  Hopefully the kernel devs will fix this eventually, but as long as the workaround works, I should be all set.  Thanks oldfred for your help!

---

